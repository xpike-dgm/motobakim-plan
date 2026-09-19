# DEBATE-010 — Bağımsız Reviewer A: Güvenlik, Kurtarma ve Yetkilendirme

Durum: `HELD — bağımsız adversarial no-code inceleme / winner yok / ADR hazır değil`  
Tarih: `2026-09-18 (Europe/Istanbul)`  
İnceleyen: `Reviewer A — security/recovery/authorization`  
Kapsam: Tüketici Flutter uygulaması, browser Internal Operations, Kavriva API sınırı,
kimlik sağlayıcısı A ve B adayları, revoke/recovery/audit/account-light merge.  
Çalışma modu: Kod, prototip, hesap açılışı, satın alma veya üretim testi yoktur.

## 1. Kısa hüküm

Önerinin yönü güvenlik prensipleri bakımından çoğunlukla doğrudur: authentication ile
authorization ayrılıyor, hassas commit server tarafına bırakılıyor, provider admini
ürün approver'ı sayılmıyor, beta passkey ile privileged production açılmıyor ve iki
aday için de `HELD` kapısı korunuyor. Ancak belge, bu prensipleri güvenli bir
uygulama/kanıt sözleşmesine henüz çevirmiyor.

| Aday | İnceleme sonucu | Neden | Bu review sonucu |
|---|---|---|---|
| **A — tek Supabase Auth** | `HELD` | Passkey hâlâ experimental/beta; tek provider outage'ında revoke/negative suspension ve object erişimi için bağımsız kontrol kanıtı yok. | **Winner değil.** Beta gate ve ortak kontroller kapanmadan privileged production açılamaz. |
| **B — consumer Supabase + ayrı privileged IdP** | `HELD` | İki issuer mapping, token/revoke/epoch birleşimi, recovery ve outage zinciri tasarım düzeyinde; ikinci issuer güvenliği otomatik artırmıyor. | **Winner değil.** İki issuer'ın eşdeğer negatif/pozitif testleri kapanmadan A'dan üstün sayılamaz. |
| Ortak Kavriva katmanı | `HELD` | End-to-end revoke, recovery/break-glass, protected audit, merge, local key ve API/RLS sınırı test edilebilir sözleşme değil. | Her iki aday için ortak aktivasyon kapısı. |

Belgesel değerlendirmede `PASS` yoktur; bu durum `REJECT` kararı değil, yüksek
sonuçlu olumlu etkinin kanıt gelene kadar `HELD` kalmasıdır. A ve B aynı tehdit,
recovery, audit, cost/operability ve exit fixture'larında eşit kanıtla
karşılaştırılmalıdır; consumer tarafında Supabase'in daha sade görünmesi, iki
adaylı privileged kararında winner yaratmaz.

### Önem derecesi

- **CRITICAL:** Kontrol kapanmadan privileged/high-consequence üretim açılırsa
  yetki ele geçirme, private evidence disclosure, yanlış publish/recall veya
  kurtarılamayan audit/authority etkisi doğabilir.
- **MAJOR:** Güvenlik standardı gevşemese bile activation/ADR için önemli bir
  sözleşme, sınır veya negatif kanıt eksiktir.
- **MINOR:** Güvenlik kapısını tek başına açmayan; fakat resmi kaynak yorumu,
  terminoloji veya karşılaştırma doğruluğunu bozan düzeltmedir.

## 2. Okunan kanıt tabanı ve doğrulama disiplini

İncelenen dosyalar:

- `DEBATE-010__IDENTITY_REQUIREMENTS_SYNTHESIS.md` — özellikle §5.3–§5.8,
  §6, AC-ID-01–AC-ID-26;
- `DEBATE-010__IDENTITY_FAILURE_THREAT_RESEARCH.md` — özellikle §3, ID-01–ID-15
  ve §6–§9;
- `DEBATE-010__IDENTITY_PROVIDER_PRIMARY_RESEARCH.md` — özellikle §3–§7;
- `DEBATE-010__MANAGER_PROPOSAL.md` — özellikle §3–§8;
- `00_CONTROL/DECISION_LOG.md` içindeki `DEC-0026`, `DEC-0034`, `DEC-0035`,
  `DEC-0036`.

Supabase iddiaları 2026-09-18 tarihinde güncel resmi dokümanlarla tekrar
karşılaştırıldı. Bu review'deki resmi kaynaklar:

- [User sessions](https://supabase.com/docs/guides/auth/sessions) ve
  [User Management](https://supabase.com/docs/guides/auth/managing-user-data):
  access JWT'nin stateless olduğu, silme/ban işleminin verilmiş JWT'yi geriye
  dönük yok etmediği ve hassas işlemlerde `session_id` kontrolünün gerektiği;
- [MFA](https://supabase.com/docs/guides/auth/auth-mfa): `aal1/aal2`, MFA'nın
  API/backend/RLS'de ayrıca uygulanması ve factor kaldırıldığında `aal2`'den
  `aal1`'e düşüşün refresh aralığına bağlı olabildiği;
- [Anonymous sign-ins](https://supabase.com/docs/guides/auth/auth-anonymous) ve
  [Identity Linking](https://supabase.com/docs/guides/auth/auth-identity-linking):
  anonymous kullanıcının `authenticated` PostgreSQL rolünü taşıdığı, `is_anonymous`
  kontrolünün gerektiği, domain veri merge'inin ürün sorumluluğu olduğu ve manual
  linking'in beta olduğu;
- [Passkey authentication](https://supabase.com/docs/guides/auth/passkeys) ve
  [Passkeys beta changelog](https://supabase.com/changelog/46458-passkeys-for-supabase-auth-beta):
  passkey'in WebAuthn tabanlı phishing-resistant credential olarak tanımlanması,
  fakat API'nin hâlâ `Experimental`/opt-in olması;
- [Serving assets from Storage](https://supabase.com/docs/guides/storage/serving/downloads):
  signed URL anahtarının Auth JWT imza anahtarından ayrı olduğu ve URL'nin expiry
  zamanına kadar geçerli kaldığı;
- [Auth Audit Logs](https://supabase.com/docs/guides/auth/audit-logs) ve
  [Database Backups](https://supabase.com/docs/guides/platform/backups): Auth
  audit kapsamının ürün audit'i olmadığı ve database backup'ın Storage object
  bytes'larını içermediği;
- [RLS](https://supabase.com/docs/guides/database/postgres/row-level-security):
  `authenticated` rolünün tek başına ownership/tenant authorization olmadığı.

## 3. Bulgular özeti

| ID | Seviye | Uygulama | Kısa bulgu | Öneriye etkisi |
|---|---|---|---|---|
| C-01 | **CRITICAL** | A+B | Revoke/security epoch object URL, local package, cached token ve in-flight/queued mutation'a end-to-end bağlanmıyor. | Common activation gate; kapanmadan private evidence/high-consequence işlem yok. |
| C-02 | **CRITICAL** | A+B | Recovery/break-glass ve provider/API outage'ında bağımsız negative authority uygulanabilir değil. | Adayların ikisi de privileged production için `HELD`. |
| C-03 | **CRITICAL** | A+B | Protected audit prensip olarak var; effect öncesi zorunlu kanıt, fallback custody ve gap/replay/restore sözleşmesi proposal'da yok. | Approval/publish/recall/recovery success kanıtlanamaz. |
| C-04 | **CRITICAL** | B (A için ortak eşdeğer gate) | İki issuer stable-principal mapping'i token confusion, collision ve global revoke boşluklarını kapatmıyor. | B otomatik güvenli veya winner değildir. |
| M-01 | **MAJOR** | A+B | “Phishing-resistant + fresh step-up” iddiası authn ile işlem-bağlı authorization'ı ayıracak parametreleri tanımlamıyor. | PR etiketi fixture kapanana kadar kullanılmamalı. |
| M-02 | **MAJOR** | A+B | Account-light/profile merge için source possession, target reauth, split/rollback ve ownership/entitlement grammar eksik. | Silent attach/loss/account takeover riski; merge activation `HELD`. |
| M-03 | **MAJOR** | A+B | Role/competence/independence/policy tuple'ının issuer, expiry, SoD ve conflict semantics'i uygulanabilir değil. | Current authorization iddiası test edilemez. |
| M-04 | **MAJOR** | A+B | Kavriva API authority denirken direct Data API/RPC/Storage/RLS/view/function deny sınırı yazılmamış. | UI gizlemek BOLA/IDOR veya service-key bypass'ını önlemez. |
| M-05 | **MAJOR** | A+B | Account-light offline local secret/key custody ve revoke sonrası local disclosure sınırı açık değil. | Kayıp cihaz/private history için consumer safe-mode kanıtı eksik. |
| M-06 | **MAJOR** | A+B | Refresh token “tek kullanımlık” ifadesi resmi reuse interval/parent-token istisnalarını eksik yorumluyor. | Replay fixture ve revoke beklentisi yanlış kurulabilir. |
| M-07 | **MAJOR** | A | Beta/GA kapısı gerekli fakat “GA” tek başına browser/Dart/RP-ID/recovery/revoke kanıtı değildir. | A'nın privileged activation koşulu güçlendirilmeli. |
| M-08 | **MAJOR** | A+B | A/B no-code tablosu her senaryoyu `HELD` yapıyor ama farklı failure-domain ve kanıt gereksinimlerini eşit fixture'a dönüştürmüyor. | Winner uydurulamaz; karşılaştırma yeniden normalize edilmeli. |
| M-09 | **MAJOR** | A+B | Browser session, CSRF, redirect/PKCE ve transaction binding ortak sözleşmede proposal seviyesinde yok. | Stolen browser credential/CSRF yolu açık kalabilir. |
| m-01 | **MINOR** | Kaynak yorumu | Auth0 Flutter SDK resmi olsa da resmi geliştirici merkezi onu `Beta` ve production için önerilmez olarak işaretliyor. | B internal-browser adayını değiştirmez; consumer olgunluğu iddiası düzeltilmeli. |

## 4. Ayrıntılı adversarial bulgular

### C-01 — Revoke/security epoch tüm veri ve yan-etki uçlarına yayılmıyor

**Kanıt.** Manager proposal security epoch'i session, refresh/recovery artifact ve
pending high-consequence authority için tanımlar (`MANAGER_PROPOSAL` §3, satır
33–36); offline revoke senaryosunu ise “safe read/reconcile” olarak bırakır (§6,
satır 100–108). Threat research aynı dosyanın §3.8'inde signed Storage URL'nin
Auth revoke ile otomatik kesilmediğini, kısa süre/object-generation/authorization
handle gerektiğini açıkça söyler (satır 62–65). Requirements de link revoke'un
sonradan online erişimi durdurabileceğini, indirilmiş/kopyalanmış veriyi geri
alamadığını belirtir (`IDENTITY_REQUIREMENTS_SYNTHESIS` §5.8, satır 256–257).

**Kusur.** Proposal'da epoch'in şu uçlarla nasıl bağlandığı yoktur: Supabase
signed URL/object handle, Storage download, browser cache/service worker, local
offline package, pending queue, in-flight request ve lost-response replay. Auth
JWT veya `auth.sessions` revoke edilse bile daha önce çıkarılmış signed URL expiry
olana kadar çalışabilir. “Safe read” de private evidence/photo/history'yi kayıp
cihazda göstermeye devam edebilir; remote wipe authority değil best-effort'tir.
Bu nedenle “revoke tamamlandı” ile “data-plane disclosure durdu” aynı kabul
edilemez.

**Düzeltme / kabul kapısı.**

1. Her hassas okuma ve commit için `principal + issuer/session + security_epoch +
   grant_generation + object_generation + exact scope + operation/version`
   doğrulanan provider-neutral decision tuple oluşturulmalı.
2. Private object için doğrudan URL yerine API-mediation veya kısa ömürlü,
   object/version/actor/epoch/audience ile bağlanmış handle kullanılmalı; revoke
   sonrasında yeni handle verilmiyor, eski handle object-generation/epoch ile
   reddediliyor. Download edilmiş kopyanın geri alınamayacağı açık disclosure
   olarak auditlenmeli.
3. Queue/in-flight commit, status lookup ve retry epoch/version tekrar kontrolü
   yapmalı; eski operation yeni payload ile yeniden kullanılamamalı.
4. Local package sınıflandırılmalı, expiry/generation ve keystore key state'i
   doğrulanmalı; device revoke sonrası güvenli read/private data sınırı ve
   `RECONCILING/HELD` davranışı fixture ile gösterilmeli.

**Öneriye etkisi.** A ve B için `CRITICAL`. İkinci issuer bu boşluğu çözmez;
consumer tarafı Supabase Storage ise B de aynı object revoke sözleşmesine
bağımlıdır. Bu kapanmadan private evidence/export veya privileged positive effect
production'a açılamaz.

### C-02 — Recovery/break-glass ve outage sırasında negative authority uygulanabilir değil

**Kanıt.** Proposal privileged recovery için “dual-control **veya** separately
governed, time-limited break-glass” der; hangi aktörlerin hangi eylemi yapacağı,
quorum, expiry, notification ve post-review tanımlı değildir (`MANAGER_PROPOSAL`
§3.7, satır 41–42). Last-admin senaryosu yalnız “dual/independent recovery”,
IdP outage senaryosu yalnız “negative path independent” sonucunu yazar (§6,
satır 106–108). Oysa `DEC-0026` protected audit fallback ve failure sırasında
hold davranışını bağlar (DECISION_LOG satır 640–665).

**Kusur.** “Or” ifadesi, dual-control olmadan tek bir governed actor'a yol
açabilir. Ayrıca recovery ile emergency negative suspension aynı şey değildir:
recovery hesabı geri alırken, safety recall/suspension yolu aktif hesabı veya
release generation'ı negatif yönde durdurmalıdır. Aday A'da Supabase Auth
kesintisi iki yüzeyi etkileyebilir; aday B'de ikinci IdP bulunması Kavriva API,
audit veya data-plane bağımsızlığını kendiliğinden sağlamaz. Tek teknik olmayan
sahip için iki kişilik positive recovery yoksa bu durum açıkça `HELD` kalmalıdır;
“AI/owner halleder” çözüm değildir.

**Düzeltme / kabul kapısı.** İki ayrı state machine yazılmalı:

- **Privileged account recovery:** iki bağımsız, gerçek insan kimliği; fresh
  phishing-resistant auth; iki taraflı onay; scope/TTL; eski session/refresh/
  recovery artifact/pending authority revoke; bağımsız bildirim; protected
  audit/fallback; recovery actor'ı approve/publish/role grant yapamaz.
- **Emergency negative authority:** IdP/API outage'ından mümkün olduğunca
  bağımsız; yalnız release/domain/object suspension veya access deny üretir;
  positive technical truth, publish, role grant ve competence üretmez; monotonic
  suspension/security floor artırır; iki aktör, expiry, reason ve post-incident
  reconciliation ile çalışır. Kanıt sink'i yoksa action `HELD` veya açıkça
  governed `OUTCOME_UNKNOWN` kalır.

Provider/control-plane owner, legal account owner, product actor ve recovery
contact ayrı tutulmalı; provider hesabı kilitliyken ürünün güvenli negative
durumu ile hesap `ACCOUNT_HELD` durumu birbirine karıştırılmamalıdır.

**Öneriye etkisi.** A ve B için `CRITICAL`. Her iki aday aynı negative/recovery
fixture'ını geçmeden hiçbir aday daha güvenli ilan edilemez.

### C-03 — Protected audit varmış gibi söyleniyor; fakat effect öncesi gating ve custody yok

**Kanıt.** Proposal “Auth log ayrı; Kavriva product audit ayrı ve korunmuş kanıt”
der (`MANAGER_PROPOSAL` §3.8, satır 43–44). Requirements ise minimum protected
evidence'ın effect'ten önce durable olmasını, normal ve protected fallback yoksa
high-consequence action'ın `HELD` kalmasını; bağımsız custody, ordered sequence,
gap/fork/replay ve restore reconciliation'ı ister (§5.8, satır 235–257; AC-ID-12).
Threat research Supabase Auth audit log'unun approval/publish/recall/tenant/AI
operation zinciri olmadığını söyler (§3.9, satır 66–68). Resmi Auth Audit Logs
dokümanı da kayıtları sign-in, reset, refresh ve sign-out olaylarıyla sınırlar;
Storage seçeneği external log veya optional Postgres'tir.

**Kusur.** Proposal protected audit'i isim olarak taşır, fakat “audit yazılmadan
effect yok”, iki custody/fallback, append-only/tamper-evident zincir, sequence
gap/fork/replay alarmı, audit read/redaction'ın auditlenmesi ve restore sonrası
negative floor uzlaştırması için bağlayıcı contract vermez. Auth audit'in plan
retention'ı veya optional Postgres tablosu ürün audit'i yerine konulursa, başarılı
bir DB response'un gerçek insan/rol/policy/scope/old-new etkisini kanıtladığı
yanlış sanılabilir.

**Düzeltme / kabul kapısı.** `product_audit_event` için actor/workload ve
effective role/scope, issuer/session assurance, security epoch, policy/grant/
competence version, operation ID, object/version, old/new meaning, server order,
reason, result ve impact/recovery owner zorunlu olmalı. Event effect'ten önce
veya eşdeğer transactional güvenceyle protected custody'ye yazılmalı; normal
sink ve bağımsız fallback yoksa `ALLOW` yerine `HELD` dönmeli. Audit zinciri
gap/fork/replay, restore, retention/legal-hold, read/export/redaction ve fallback
reconciliation fixture'larında sınanmalı.

**Öneriye etkisi.** A ve B için `CRITICAL`. Audit closure olmadan approval,
publication, recall, role/policy, recovery veya export “başardı” olarak
raporlanamaz.

### C-04 — B'nin iki issuer mapping'i token confusion ve global revoke boşluğunu kapatmıyor

**Kanıt.** B bileşimi “iki issuer stable Kavriva principal'a map eder” ve “global
security epoch” uygular (`MANAGER_PROPOSAL` §5, satır 73–80); zayıf taraflar
yalnız mapping/logout/revoke/actor yükünü söyler (§5, satır 87–92). Provider
research de bu konuları satın alma/ADR öncesi yeniden kontrol listesine koyar
(§7, satır 139–147). Bununla birlikte issuer trust contract'ı yoktur.

**Kusur.** `iss/aud/sub` namespace'i, alg/JWKS/key rotation, issuer-specific
session/revocation, duplicate/ambiguous identity, e-posta ile yanlış eşleşme,
JIT/deprovision, assurance equivalence ve provider outage davranışı belirtilmez.
İki issuer'ı aynı stable principal'a map etmek, yanlış doğrulanmış token veya
yanlış account link'iyle operator scope/role taşıma riskini artırır. Kavriva
epoch'i provider refresh token'larını veya Storage signed URL'lerini kendiliğinden
iptal etmez; bir issuer'da revoke edilip diğerinde açık kalan session da
“global logout” değildir.

**Düzeltme / kabul kapısı.** Her issuer için allowlisted `iss`, exact `aud`,
alg/key/JWKS rotation ve expiry/clock policy; issuer-qualified immutable
`(issuer, sub)` mapping; e-posta/display name ile automatic actor mapping yasağı;
collision/claim disagreement'ta `HELD`; provider session + Kavriva epoch kontrolü;
tek bir revoke/epoch operation'ı ve pending-op invalidation; provider-specific
logout/recovery/audit/outage runbook gerekir. Key retirement, stale token,
cross-issuer confusion, duplicate mapping, lost response ve one-provider outage
fixture'ları A ile aynı kanıt eşiğinde çalıştırılmalı.

**Öneriye etkisi.** B için `CRITICAL`; A için de tek issuer'ın trusted token,
session ve key-rotation contract'ı aynı şekilde kapanmalıdır. B bu bulgu
kapanmadan A'dan üstün değildir; bu review B'yi reddetmez, `HELD` tutar.

### M-01 — “Phishing-resistant + fresh step-up” tanımı işlem sınırını kapatmıyor

**Kanıt.** Proposal privileged browser için fresh phishing-resistant doğrulama ve
işlem-bağlı step-up söyler (`MANAGER_PROPOSAL` §3.6, satır 39–40); provider
research TOTP'nin phishing-resistant olmadığını ve Supabase passkey'in beta
olduğunu belirtir (`IDENTITY_PROVIDER_PRIMARY_RESEARCH` §3.1, satır 41–45).
Requirements exact authenticator, step-up UX ve recovery factor'ı açık karar
olarak bırakır (§6, satır 286–302).

**Kusur.** WebAuthn/passkey bir authentication ceremony'si olarak
phishing-resistant olabilir; bu, tek başına privileged action'ın fresh,
user-verified, origin/RP-ID doğru, transaction-bound veya recovery/enrollment
değişikliğinin güvenli olduğu anlamına gelmez. Supabase `aal2` ise TOTP/phone
gibi faktörlerle de elde edilebilir; `aal2 = phishing-resistant` değildir. Factor
kaldırma sonrası JWT'nin `aal` claim'i refresh'e kadar eski kalabilir.

**Düzeltme.** Capability bazında assurance policy yazılmalı: privileged login,
factor add/remove, recovery ve step-up için WebAuthn/passkey origin/RP-ID,
user-verification ve challenge'ın actor/action/resource/version/consequence ile
bağlanması; step-up freshness penceresi; downgrade/factor-loss'ta immediate
deny; TOTP/SMS/magic-link fallback yasağı; synced passkey/attestation ve
authenticator loss policy'si. Bu alanlar gerçek browser/Dart/native fixture'ı
geçmeden “phishing-resistant” diye etiketlenmemeli.

**Öneriye etkisi.** A ve B için `MAJOR`; B'nin IdP'si de aynı Kavriva
transaction-bound koşullarını kanıtlamak zorundadır.

### M-02 — Account-light/profile merge, provider identity-linking ile karışabilir

**Kanıt.** Proposal local installation principal'i verified re-auth ve conflict
hold ile profile'a bağlar, e-posta benzerliğini reddeder (`MANAGER_PROPOSAL` §3.5,
satır 37–38). Threat research anonymous→permanent akışında `is_anonymous`,
conflict ledger ve no-silent-overwrite ister (ID-07, satır 100). Resmi Supabase
anonymous dokümanı anonymous kullanıcının `authenticated` rolünü taşıdığını ve
conflict çözümünü (overwrite/merge/manual) uygulamaya bıraktığını söyler; manual
identity linking resmi dokümanda beta'dır.

**Kusur.** Proposal'da source installation possession, target account re-auth,
merge freeze, stable record mapping, pending operation handling, private/shared/
official classification, entitlement/ownership transfer, idempotency ve split/
rollback grammar yoktur. Provider identity-linking yalnız auth identity'lerini
bağlar; Kavriva history, evidence, motorcycle ownership veya attribution merge'i
değildir. Aynı görünen e-posta veya cached profile ile yanlış target'a attach,
duplicate veya ownership elevation doğabilir.

**Düzeltme.** Merge'i ayrı bir Kavriva operation olarak tanımlayın: source ve
target'ın aynı kişiye ait olduğuna dair explicit verified proof; source+target
fresh re-auth; kapsam/classification preview; operation ID/fingerprint; merge
freeze; immutable source→target mapping; conflict başına `HELD`; target kabul ve
reconciliation olmadan source deletion yok; split ile original actor/provenance
geri alınabilir; entitlement/role/grant yeniden hesaplanır. Anonymous RLS'de
`is_anonymous` restrictive policy ile kontrol edilmeli; `authenticated` rolü
tek başına ownership sayılmamalıdır.

**Öneriye etkisi.** A ve B için `MAJOR`; account-light migration positive
authority'si bu contract ve rollback/split fixture'ı olmadan açılmaz.

### M-03 — Authorization tuple var, fakat issuer/expiry/SoD/competence yürütme sözleşmesi yok

**Kanıt.** Proposal API'nin action/object/tenant/classification/role/grant/
competence/independence/policy/epoch ile karar vereceğini yazar (§3.2, satır
31–36). Ancak Requirements exact role matrix, competence issuer/recertification,
quorum ve low-risk combinations'ı açık karar olarak bırakır (§6, satır 286–302);
`DEC-0026` de role matrix, competence issuer ve staffing/quorum'un çözülmediğini
belirtir (DECISION_LOG satır 657–665).

**Kusur.** Tuple alanlarını isimlendirmek, bunların canonical source, issuer,
effective time, expiry, revoke generation, conflict accumulation (group/alias/
delegation/service identity), classification boundary ve author/approver/
activator ayrımını tanımlamaz. Provider dashboard role, JWT claim veya admin
superuser'ın ürün yetkisine dönüşmeyeceği yalnız ilke olarak yazılmıştır.

**Düzeltme.** Grant/competence/delegation/policy controlled object'leri
versioned ve attributable olmalı; material change için distinct author,
independent approver, activator, effective time ve pending-work recheck;
self/nested/transitive delegation, scope/classification bypass ve role
accumulation negatif testleri; issuer/expiry/recertification ve independence
quorum açıkça bağlanmalı. Eksik veya stale object `DENY/HELD` üretmeli.

**Öneriye etkisi.** A ve B için `MAJOR`; provider seçimi bu domain authorization
eksikliğini çözmez.

### M-04 — Kavriva API authority iddiası direct Supabase surface'lerini kapatmıyor

**Kanıt.** `DEC-0035` API boundary'sini ve RLS/Storage'ı defense-in-depth olarak
bağlar, `service_role`/secret'ı client dışında tutar (DECISION_LOG satır
975–985). Threat research de grants + RLS'nin iki ayrı kapı olduğunu ve
`authenticated` rolünün tenant authority olmadığını söyler (§3.7, satır 58–61).
Proposal ise “API karar verir” der, fakat direct REST/Data API, RPC, view,
Storage download ve function exposure için allow/deny sözleşmesi vermez (§3.2,
satır 31–32).

**Kusur.** UI'da buton gizlemek veya API endpoint'i yazmak, public/exposed schema,
yanlış grant, permissive RLS, `SECURITY DEFINER` veya doğrudan signed URL yolunu
kapatmaz. Anonymous kullanıcı da `authenticated` PostgreSQL rolünü taşıdığı
için `TO authenticated` tek başına yeterli değildir. Direct path negatif testleri
olmadan BOLA/IDOR, `user_id/tenant_id` reassignment veya service-key leakage
tespit edilemez.

**Düzeltme.** Exposed object/grant inventory; public/exposed tabloların RLS ve
ownership/tenant `USING` + `WITH CHECK` politikaları; client'tan direct
high-consequence write/RPC deny; view'larda `security_invoker` veya private
schema; `SECURITY DEFINER` fonksiyonlarda private schema, explicit auth check ve
minimal grants; service/secret server-only; direct REST/RPC/object-ID/signed URL
cross-tenant fixture'ları zorunlu olmalı.

**Öneriye etkisi.** A ve B için `MAJOR`. RLS, Kavriva API'nin yerine geçmez;
fakat API var diye RLS/grant/Storage yüzeyi ihmal edilemez.

### M-05 — Account-light offline secret/key custody ve revoke sonrası local disclosure açık

**Kanıt.** Proposal local installation principal ve offline safe-read yönünü
tanımlar (§3.5 ve §6, satır 37–38, 100–108), fakat local encryption/key custody
contract'ı taşımaz. `DEC-0036` encryption/key custody'yi ayrı `HELD` karar olarak
bırakır (DECISION_LOG satır 1028–1047). Threat research kayıp cihaz ve offline
revoke için encryption/key custody, package expiry ve remote wipe'ın authority
olmadığını söyler (ID-08, satır 101).

**Kusur.** Account-light'in temel değeri ve pending work cihazda tutuluyorsa,
cihaz kaybı veya restore/reinstall sonrası private history, evidence metadata,
token ve package erişiminin kapsamı belirsizdir. “Safe read” her veri türü için
safe değildir; revoked collaborator veya stolen device'ın local copy'si online
revoke gelene kadar okunabilir. Plaintext fallback, keystore failure, backup
exclusion, key rotation/recovery ve local deletion semantiği proposal'da yoktur.

**Düzeltme.** Per-installation key'i OS keystore ile koruyan, plaintext fallback
olmayan; package/ledger classification, expiry/generation, key loss/revoke ve
device migration quarantine contract'ı yazılmalı. Private evidence için offline
izin daraltılmalı; network dönüşünde epoch/key/object generation recheck yapılmalı;
remote wipe best-effort olarak açıkça disclosure riskiyle auditlenmeli. Key
kanıtı yoksa yalnız düşük riskli/öğretici safe read, private data ise `HELD`.

**Öneriye etkisi.** A ve B için `MAJOR`; bu çoğunlukla ortak consumer
Supabase/local katmanıdır, B'nin ikinci IdP'si çözmez.

### M-06 — Refresh token “tek kullanımlık” ifadesi istisnaları atlıyor

**Kanıt.** Threat research Supabase session özetinde refresh token'ın “tek
kullanımlık” olduğunu söyler (`IDENTITY_FAILURE_THREAT_RESEARCH` §3.1, satır
34–38). Resmi [User sessions](https://supabase.com/docs/guides/auth/sessions)
dokümanı ise token reuse detection için varsayılan 10 saniyelik reuse interval ve
parent-token istisnası olduğunu, ağ yanıtı kaybolduğunda bu istisnaların oturumu
gereksiz yere düşürmemek için kullanıldığını açıklar.

**Kusur.** “Single-use” mutlak anti-replay garantisi gibi test edilirse iki
sonuçtan biri çıkar: meşru concurrent refresh yanlış compromise sayılır veya
reuse interval içindeki çalınmış token gözden kaçar. Proposal sensitive
authorization'ın refresh davranışından bağımsız session/epoch kontrolünü yeterince
ayrıntılandırmıyor.

**Düzeltme.** Dokümantasyon “normalde single-use, belgelenmiş reuse exceptions”
olarak düzeltilmeli. Reuse window içi/dışı stolen refresh, concurrent legitimate
refresh, refresh-family revoke, lost response ve epoch change fixture'ları
koşulmalı. Privileged API için refresh-token sonucuna değil current session,
account state ve Kavriva epoch'e güvenilmeli.

**Öneriye etkisi.** A ve B için `MAJOR` kaynak/fixture düzeltmesi; provider'ın
reuse semantiği değişirse yeniden doğrulama zorunlu.

### M-07 — Aday A'nın beta/GA kapısı gerekli ama yeterli değil

**Kanıt.** Proposal passkey stable/GA, browser akışı ve recovery/revoke
fixture'ları kabul edilene kadar A'nın privileged production'ını `HELD` tutar
(`MANAGER_PROPOSAL` §4, satır 50–71; §7, satır 120–137). Bu temkin doğrudur.
Resmi Supabase passkey dokümanı 2026-09-18 tarihinde de `Experimental`, explicit
opt-in ve API değişebilir durumunu gösterir.

**Kusur.** “GA” bir ürün etiketi; tek başına Dart/native/browser sürüm paritesi,
RP-ID/origin sabitliği, user verification, factor loss, session revoke,
transaction-bound step-up, key rotation, rollback veya outage davranışı kanıtı
değildir. Aday A'nın tek provider failure-domain'i için bağımsız negative path da
aynı activation cümlesine bağlanmamıştır.

**Düzeltme.** A activation gate; pinned client/server versions, stable API
contract ve rollback; browser/Dart/native support matrix; RP-ID/origin/UV policy;
enrollment/removal/recovery/lost-factor; stolen-token/session revoke; step-up
transaction binding; key rotation; IdP/API outage ve independent negative
suspension fixture'larının tamamını ister. TOTP/SMS/magic-link fallback ile gate
geçilemez. Beta devam ettiği sürece A yalnız low-risk/read-only veya `HELD`
operasyon olarak kalır.

**Öneriye etkisi.** A için `MAJOR`; beta'ya güvenme değil, GA'yı tek kanıt gibi
okumayı önleme bulgusudur. B de aynı ortak fixture'ı geçmeden winner değildir.

### M-08 — A/B karşılaştırması “eşit HELD” diyor ama eşit kanıt üretmiyor

**Kanıt.** Proposal §6 tablosunda 15 senaryonun her biri A ve B için aynı
`HELD` sonucunu alır (satır 94–118); §7'de ise consumer için Supabase lider,
privileged için conditional A/B yönü önerilir (satır 120–137). Provider research
de A'yı consumer lider, B'yi internal challenger olarak etiketler (§6, satır
125–137).

**Kusur.** Aynı `HELD` etiketi farklı belirsizlikleri gizler: A'da tek provider
outage/recovery; B'de issuer mapping/revoke/key rotation/recovery; her ikisinde
Kavriva API/audit/object floor. “0 PASS / 15 HELD / 0 REJECT” gerçek bir equal
fixture veya weighted risk sonucu değildir. Ayrıca A/B'nin ortak consumer
katmanı için verilen liderlik, privileged mimari kararı hakkında kanıt değildir.

**Düzeltme.** Ortak fixture her aday için aynı input, aynı saldırı, aynı beklenen
`ALLOW/DENY/HELD`, aynı audit/recovery/exit kanıtı ve aynı owner-operability/cost
formatıyla doldurulmalı. Özellikle stolen token, factor loss, account merge,
signed URL, two-tab revoke, one-provider outage, two-issuer collision, lost
response, restore/anti-resurrection ve emergency negative suspension ayrı
sonuçlandırılmalı. Evidence yoksa her iki aday `HELD`; hiçbirine “leader” veya
“safer” etiketi verilmemeli.

**Öneriye etkisi.** A ve B için `MAJOR` karar-disiplini bulgusu. Bu review
winner seçmez; düzeltme sonrası eşit kanıtla yeniden değerlendirme ister.

### M-09 — Browser session/CSRF/redirect/PKCE/transaction binding ortak contract'ta görünmüyor

**Kanıt.** Requirements browser storage'da reusable long-lived authority
olmamasını, trusted origins, CSRF/cross-site protection ve transaction binding'i
ister (§5.4, satır 162–177). Provider research Android deep-link/PKCE ve browser
origin/RP-ID kontrollerini satın alma öncesi açık bırakır (§7, satır 139–147).
Manager proposal ise browser için yalnız stale/offline mutation'ın çalışmaması ve
step-up'ı söyler (§3.6, satır 39–40).

**Kusur.** Fresh step-up, çalınmış browser credential, CSRF veya yanlış redirect
ile saldırganın doğru API action'ına ulaşmasını tek başına önlemez. Cookie/token
storage, origin/redirect allowlist, PKCE/deep-link binding, CSRF token, CSP ve
transaction nonce/audience contract'ı olmadan “stale page hold” güvenlik
kontrolü eksik kalır.

**Düzeltme.** Internal Operations için browser threat contract'ı; exact token/cookie
storage ve lifetime, HTTPS/origin/redirect allowlist, PKCE/deep-link, CSRF/cross-
site savunması, transaction nonce ve action/resource/version/consequence binding,
tab replay ve lost-response fixture'larıyla bağlanmalı. Browser'da long-lived
reusable authority veya provider dashboard session'ı ürün authority'si olmamalı.

**Öneriye etkisi.** A ve B için `MAJOR`; provider seçimi bu browser boundary'sini
ortadan kaldırmaz.

### m-01 — Auth0 Flutter olgunluğu resmi kaynakta olduğundan daha olumlu okunuyor

**Kanıt.** Provider research Auth0 için “resmi Flutter SDK/quickstart” der ve
matriste yalnız “resmi Flutter SDK” notunu taşır (`IDENTITY_PROVIDER_PRIMARY_RESEARCH`
§3.4 ve §4, satır 75–102). Güncel resmi Auth0 developer merkezi ise [Auth0 SDK
for Flutter](https://developer.auth0.com/resources/get-started/mobile/flutter)
başlığını `Beta` olarak gösterir ve production için henüz önermediğini belirtir.
Auth0'nun browser Universal Login'i ve B adayının internal-browser kapsamı yine
geçerli olabilir; sorun, Flutter olgunluğunun genel “official = production
ready” sinyali gibi okunmasıdır.

**Düzeltme / etki.** A2 kaynağı browser/Universal Login kanıtı olarak ayrılmalı;
Auth0 Flutter SDK consumer değerlendirmesinde beta/production-not-recommended
olarak `HELD` yazılmalıdır. Bu bulgu B'nin yalnız browser internal kapsamını tek
başına değiştirmez ve A/B winner üretmez; fakat provider karşılaştırma matrisi
düzeltilmelidir.

## 5. Doğru olan ve yanlış yorumlanmaması gereken noktalar

Adversarial review, her temkinli ifadeyi kusur saymaz:

1. Supabase passkey'in beta/experimental olduğunu söyleyip A'nın privileged
   production'ını kapalı tutmak **doğru yöndür**. Kusur, GA'yı tek başına yeterli
   kanıt sayma ve ortak negative/recovery/object gate'ini eksik bırakmadır.
2. TOTP, SMS veya magic link'i phishing-resistant privileged auth yerine
   koymamak **doğrudur**. `aal2` veya “MFA açık” etiketi de aynı şey değildir.
3. Silme/ban sonrası verilmiş JWT'nin `exp`'e kadar yaşayabileceği, anonymous
   kullanıcının `authenticated` rolü taşıdığı, signed URL'nin Auth key revoke'dan
   bağımsız olduğu ve database backup'ın Storage bytes'larını taşımadığı
   araştırmada doğru yönde yorumlanmıştır; bunlar C-01/M-06 kapılarının neden
   gerektiğini güçlendirir.
4. A ve B'nin ortak `HELD` sonucu bir güvenlik PASS'i değildir. Bu review hiçbir
   adayı reject etmez veya winner seçmez; eksik kanıtı görünür kılar.

## 6. Karar için zorunlu düzeltme paketi

Privileged activation veya Phase-5 ADR öncesi aşağıdaki no-code sözleşme/fixture
paketi her iki aday için aynı formatta hazırlanmalıdır:

1. Global security epoch, provider session, grant/competence/policy generation,
   object generation ve operation ID'nin tek decision tuple olarak işlendiği
   state machine.
2. Storage object handle/signed URL, browser cache, local package, queue,
   in-flight ve lost-response için revoke/anti-replay/anti-resurrection matrisi.
3. Privileged account recovery ile emergency negative suspension'ın ayrıldığı;
   dual-control, TTL, scope, notification, fallback audit ve no-positive-authority
   kurallarını içeren break-glass sözleşmesi.
4. Product audit event schema, effect-before-audit hold, independent fallback,
   tamper/gap/fork/replay detection, restore/retention/redaction/export kanıtı.
5. Account-light/profile merge/split contract'ı: source/target proof, fresh
   re-auth, explicit consent, classification/ownership/entitlement, conflict
   hold, immutable mapping, idempotency ve no-destructive-source deletion.
6. Provider-neutral authorization matrix: role, scope, competence, independence,
   delegation, issuer, expiry, SoD, policy version ve conflict accumulation.
7. Direct REST/RPC/Storage/view/function yüzeylerinin exposure/grant/RLS/
   `security_invoker`/`SECURITY DEFINER` ve `service_role` sınırlarıyla negatif
   test matrisi.
8. A için passkey GA sonrası bile version/RP-ID/origin/UV/recovery/revoke/
   transaction-bound fixture'ları; B için per-issuer `iss/aud/sub`/JWKS/key
   rotation/mapping/logout/outage/recovery fixture'ları.
9. Browser session/token/cookie, CSRF, PKCE/deep-link, origin ve transaction
   nonce sözleşmesi; Android-first/iOS-later lane'lerinin ayrı kanıtı.
10. Aynı threat/recovery/evidence/cost/owner-operability/exit rubric'iyle A/B
    karşılaştırması. Kanıt eksikliği her iki adayda `HELD`; consumer “liderliği”
    privileged winner'a çevrilmemeli.

## 7. Son disposition

`DEBATE-010__MANAGER_PROPOSAL.md` güvenlik standardını bütçeye göre düşürmeme,
beta passkey ile privileged production'ı açmama ve provider-neutral Kavriva
authorization yönünde **iyi bir çalışma başlangıcıdır**. Fakat C-01, C-02 ve C-03
kapanmadan A veya B için high-consequence production activation güvenli değildir;
C-04 B'nin iki issuer iddiasını ayrıca `HELD` tutar. M-01–M-09 ortak sözleşmeyi,
m-01 provider karşılaştırma doğruluğunu düzeltir.

Bu dosya kod, ADR, hesap, satın alma veya winner kararı oluşturmaz. Güvenli karar:

> **A = HELD, B = HELD; winner yok. Önce ortak revoke/recovery/audit/authorization
> contract ve eşit fixture kanıtı, sonra yeniden değerlendirme.**

