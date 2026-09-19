# DEBATE-010 — Bağımsız Reviewer B: Owner / TCO / Operability / Recovery

Durum: `HELD — A/B eşit belgesel aday; privileged production açılışı yok; provider, plan, hesap ve satın alma yok`
Tarih: 2026-09-18 (Europe/Istanbul)
Reviewer: Bağımsız Reviewer B
Kapsam: `NO-CODE / NO ACCOUNT / NO PURCHASE / ADR NOT READY`

## 0. Hüküm

Bu inceleme; `DEBATE-010__IDENTITY_REQUIREMENTS_SYNTHESIS.md`, `DEBATE-010__IDENTITY_FAILURE_THREAT_RESEARCH.md`,
`DEBATE-010__IDENTITY_PROVIDER_PRIMARY_RESEARCH.md` ve `DEBATE-010__MANAGER_PROPOSAL.md` ile
`DEC-0029/0030/0032/0035` ve ilgili kontrol belgelerini, teknik olmayan tek sahip ve AI-operated işletim modeli
altında adversarial olarak değerlendirir. Kod, prototip, provider hesabı, plan, ödeme veya ADR üretmez.

Yönetici önerisinin ana sınırları doğrudur: authentication ≠ authorization; stable Kavriva principal; server/API
authority; security epoch; account-light migration; online privileged mutation; protected audit; no-owner-debug.
Ancak öneri, bu sınırların gerçek sağlayıcı planı, recovery personeli, outage yolu, gizli bağımlılık maliyeti ve
clean-room çıkışı ile nasıl işletileceğini henüz kanıtlamıyor.

| Ölçüt | A — Tek Supabase Auth | B — Supabase consumer + ayrı privileged IdP |
|---|---|---|
| Privileged üretim | `HELD`: Supabase passkey API’si hâlen experimental; session/recovery planı açık | `HELD`: ikinci issuer, plan, recovery ve mapping seçilmemiş |
| Owner/TCO | Daha az görünen control-plane; ancak üretim Auth e-postası, domain, log/audit ve recovery ekleri açıklanmadı | İkinci sabit abonelik, ikinci support/outage/recovery ve issuer mapping yükü; MAU/MRU karşılaştırması normalize değil |
| Outage blast radius | Auth + consumer + internal aynı sağlayıcı arızasından etkilenebilir | IdP ayrışması fayda sağlayabilir; API/DB/audit ortak arızası ve cross-issuer drift eklenir |
| Last-admin / recovery | Tek plane daha basit görünüyor; fakat bağımsız ikinci insan/yol tanımlı değil | İki plane için iki owner/support/recovery zinciri gerekir; son admin sorunu büyür |
| Exit | Stable principal iyi başlangıç; factor/credential, Auth/Storage ve audit geçişi kanıtlanmadı | İki issuer ID’si, grants, factor’lar, session’lar ve audit mapping’i birlikte taşınmalı |
| Disposition | `HELD` | `HELD` |

`0 PASS / 0 üretim onayı` hükmü korunmalıdır. A ve B’nin aynı kelimeyle `HELD` olması risklerin eşdeğer olduğu
anlamına gelmez; aşağıdaki A/B’ye özgü hard gate’ler kapanmadan yönetici önerisi “koşullu A, hazırlıklı B” olarak
kalabilir, fakat herhangi bir provider seçimi veya privileged activation’a dönüşemez.

## 1. Bağlayıcı kontrol doğrulaması

| Kontrol | Doğrulanan hüküm | Bu review sonucu |
|---|---|---|
| `DEC-0029` / `00_CONTROL/SOURCE_OF_TRUTH.md` / `00_CONTROL/CURRENT_STATE.md` | Sahip teknik olmayan product/decision owner’dır; AI bounded task, bağımsız review ve evidence ile çalışır; owner SQL/SSH/build/debug/repair yapmaz; AI legal/provider/store authority’yi taklit edemez | Yönetici önerisi ilkeyi doğru taşır. Provider DNS, SMTP, billing, recovery ve support adımlarında “owner-readable” kontrol ile gerçek teknik onarım arasındaki sınır henüz task/runbook olarak kapanmamıştır. |
| `DEC-0030` / `00_CONTROL/DECISION_LOG.md` | Ücretler mandatory/deferrable/optional/scale-triggered ayrılır; güncel resmi fiyat, free/cap/overage, vergi/kur, billing period ve exit gösterilir; karşılanamayan zorunlu assurance `HELD` olur | Öneri yalnız “A daha düşük / B daha yüksek” diyor. Auth planı, SMTP/SMS, domain, log, audit, support, recovery ve incident/exit aylarıyla owner-readable BOM yok. |
| `DEC-0032` / `00_CONTROL/DECISION_LOG.md` | Android-first, iOS-later; doğrudan Android cihaz, ödünç iPhone; TRY 2.000–3.000/ay gelecekteki non-store planning ceiling’idir, harcama izni değildir | Kimlik/redirect/recovery kanıtı Android’de başlasa da iOS parity otomatik kazanılmaz. Tavan, ikinci IdP veya Supabase eklerini peşinen onaylamaz. |
| `DEC-0035` / `00_CONTROL/DECISION_LOG.md` | Supabase-centered fiziksel yön yalnız Kavriva API arkasında; RLS/Storage defense-in-depth; Studio Internal Operations değildir; object/audit/floor bağımsız recovery ister; Neon+API+R2 fallback’tir | A için Auth provider seçimi veya paid plan onayı çıkmaz. B, `DEC-0035`’e aykırı değildir; fakat iki issuer yüzeyi API’de açıkça normalize edilmelidir. |
| `04_TECH_STRATEGY/RISK_REGISTER.md` | Özellikle `TSR-026` emergency failure-domain, `TSR-029` stolen privileged session, `TSR-045` no-owner-debug, `TSR-048` hidden/uncapped cost, `TSR-049` budget ile assurance düşürmeme | DEBATE-010 proposal bu riskleri listeliyor, fakat owner/recovery staffing, support SLA ve fiyat/plan gate’iyle kapatmıyor; residual `UNKNOWN/HELD` kalmalıdır. |

## 2. CRITICAL bulgular

### C-01 — Last-admin ve bağımsız recovery yolu tek sahip modeliyle işletilebilir değil

**Kanıt / problem.** Öneri, privileged recovery için dual-control veya süreli break-glass, son admin kaybı için
güvenli hold ve no-owner-debug diyor. Fakat DEC-0029/0030 kapsamında tek teknik olmayan sahip var; ikinci bağımsız
recovery aktörü, legal account owner, provider support yolu, emergency negative authority, notification sahibi,
SLA veya ücretli destek sınıfı tanımlı değil. “Dual-control” burada bir kontrol cümlesi olarak kalıyor. Aynı kişi,
aynı provider hesabı veya aynı recovery factor hem issuer hem approver olursa self-approval ve recovery bypass riski
devam eder. Hiç kimse/hiçbir bağımsız yol tanımlanmazsa son admin kilitlenmesinde recall/suspension gibi negatif
güvenlik etkisi de gecikir.

**Risk.** Pozitif işlem `HELD` olsa bile incident containment, recall, revoke ve account recovery yapılamaz; owner’dan
SQL/SSH, dashboard superuser veya log teşhisi istenmesi DEC-0029 ihlalidir. Bu, A ve B için privileged production
açılışını etkileyen safety/operability hard fail’dir.

**Düzeltme / kapanış kanıtı.**

1. Product approver, recovery verifier, legal/billing owner, provider support contact ve emergency negative operator
   rollerini; insan/kurum, factor custody, scope, süre, notification ve audit sorumluluğuyla ayır.
2. En az iki bağımsız recovery yolu ve iki farklı failure-domain tanımla; break-glass yalnız negative suspension /
   revoke / quarantine üretsin, approve/publish/unsuspend/release üretmesin.
3. Recovery security epoch’i artırmalı; eski session, refresh/recovery artifact ve pending high-consequence authority
   iptal edilmeli; provider/API erişilemiyorsa owner-readable `ACCOUNT_HELD` / `SERVICE_UNAVAILABLE` gösterilmeli.
4. Tabletop ve no-code drill: tüm normal adminler kilitli, IdP down, provider support gecikmeli, audit sink normalde
   yazılamıyor. Owner yalnız anlaşılır `hold / notify / request-support / negative-stop` adımları görmeli; teknik
   repair yapmamalı.

**Yönetici önerisine etkisi.** “Recovery dual-control olabilir” ifadesi yeterli değildir. C-01 kapanana kadar A da B
de privileged production için `REJECT-IF-UNMITIGATED`; consumer low-risk/read-only ve safe-stop modları ayrı tutulur.
Bu bulgu B’yi otomatik kazanan yapmaz; B’de recovery aktör ve support sayısı artar.

### C-02 — Provider outage, protected audit/floor ve negative suspension için bağımsız yetki kanıtı yok

**Kanıt / problem.** A, tek Supabase provider’ının Auth, API/DB, Storage, log ve kontrol yüzeylerinin aynı failure
domain’inde bulunabilmesi nedeniyle consumer + Internal Operations blast radius’unu büyütür. B, Auth issuer’ını
ayırarak bir arızayı izole edebilir; fakat Kavriva API/DB, audit/floor, DNS, billing veya object plane ortak kalabilir.
Her iki aday için öneri “independent negative suspension path ayrıca gerekir” diyor, ancak bu yolun hangi bağımsız
credential, API, datastore, operator, retention, billing ve restore koşuluyla çalıştığı belirtilmiyor.

**Risk.** IdP belirsizliği veya outage sırasında yalnız `HELD` demek, daha önce yayımlanmış kritik içeriğin
recall/suspension/revoke edilmesini garanti etmez. Normal ve fallback audit aynı sağlayıcıya bağlıysa effect’in
kanıtı da kaybolabilir. “Provider dashboard yeşil” veya mevcut JWT, current safety state değildir.

**Düzeltme / kapanış kanıtı.** Her iki aday için Auth, API runtime, DB, object, audit, floor, DNS, SMTP, billing ve
support failure matrix’i yazılmalı:

- yeni login / refresh / step-up;
- mevcut düşük riskli read ve safe-stop;
- approval / publish / export / role change;
- emergency suspend / recall / revoke;
- audit-before-effect, fallback evidence, `OUTCOME_UNKNOWN`;
- restore sonrası monotonic negative floor.

Her satırda bağımsız control-plane, credential class, owner action, expected cost, RTO/RPO varsayımı, escalation ve
clean-room evidence bulunmalı. Normal veya fallback protected evidence yoksa yüksek etkili işlem `HELD` kalmalı.

**Yönetici önerisine etkisi.** A’nın “daha sade” iddiası common-mode riskini gizlememeli; B’nin “ayrı IdP daha erken
güvenlik” iddiası da API/DB/floor outage’ını çözmez. C-02 kapanana kadar iki aday eşit documentary `HELD`, fakat
production activation için koşullu değil zorunlu gate’tir.

### C-03 — Privileged session/step-up yeteneği plan bağımlılığıyla birlikte hard-gate yapılmamış

**Kanıt / problem.** Supabase’in güncel session dokümanı varsayılan oturumların kullanıcı çıkış yapana kadar devam
edebildiğini ve inactivity/time-box/single-session kontrollerinin Pro ve üstü planlarda bulunduğunu söyler
([Supabase User sessions](https://supabase.com/docs/guides/auth/sessions)). Güncel passkey dokümanı API’yi
`Experimental` olarak işaretler ve API’nin uyarısız değişebileceğini belirtir
([Supabase Passkey authentication](https://supabase.com/docs/guides/auth/passkeys)); 28 Mayıs 2026 duyurusu da
ürün aşamasını `Beta` olarak verir ([Supabase passkey beta changelog](https://supabase.com/changelog/46458-passkeys-for-supabase-auth-beta)).
Supabase Free karşılaştırmasında session timeouts, single-session, leaked-password protection, automatic backup,
email support ve SLA bulunmaz ([Supabase pricing](https://supabase.com/pricing)).

B’de Clerk için passkey/MFA üretim yolu Pro plana, 50K MRU üstü kullanıma ve sağlayıcı semantiğine bağlıdır; resmi
fiyat sayfası Pro’yu yıllık faturalamada $20/ay, 50K MRU dahil ve MFA özellikli gösterir ([Clerk pricing](https://clerk.com/pricing)).
Auth0’da resmi fiyat sayfası Essentials’ı $35/ay, 500 MAU, Pro MFA, audit-log streaming ve standard support ile;
Professional’ı $240/ay olarak gösterir ([Auth0 pricing](https://auth0.com/pricing)).

**Risk.** “Stable/GA olursa A” veya “passkey destekli IdP ile B” plan/özellik/limit bağımlılığını kapatmaz. Budget
seçimi Free/Hobby’ye kayarsa privileged step-up, session bounds, log/support veya recovery assurance eksik kalabilir;
güvenlik standardı sessizce düşmemeli.

**Düzeltme / kapanış kanıtı.** Provider-plan-capability matrisi zorunlu olsun: privileged login, registration,
transaction-bound step-up, factor loss, re-auth, logout-all, session bound, role revoke, session epoch, audit/fallback,
support and export. Her aday için seçilecek minimum plan, free path, hard cap, overage, billing hold, tax/FX ve stop
state açıkça yazılmalı. Plan karşılanamıyorsa privileged capability `HELD`; TOTP, SMS veya magic link passkey yerine
konmamalı.

**Yönetici önerisine etkisi.** A’nın düşük maliyet avantajı yalnız consumer Auth/low-risk kullanım için conditional
kalır; Pro/ek hizmet gerektiren Internal Operations maliyeti BOM’a girmeden A “ucuz” değildir. B’nin ikinci IdP’si de
yalnız seçilen planın recovery/outage/export kanıtı geçerse aday kalır.

### C-04 — B’de iki issuer için tek global revoke/epoch ve actor mapping kanıtı yok

**Kanıt / problem.** B; Supabase consumer ve ayrı privileged IdP’yi stable Kavriva principal’a map etmeyi öneriyor,
fakat iki issuer’dan gelen session, refresh, factor, role/grant, logout-all, recovery ve support olaylarının tek
security epoch’e nasıl bağlanacağı tanımlı değil. Provider-revoke bir issuer’da gerçekleşip diğer issuer’da eski
oturum canlı kalabilir. Aynı kişinin iki provider hesabı, yanlış e-posta eşleşmesi veya duplicate mapping’i stable
principal’a sessizce bağlanabilir.

**Risk.** Eski privileged issuer token’ı, diğer provider’daki güncel recovery/revoke kararından habersiz şekilde API’ye
ulaşabilir. Audit’te `provider user id → Kavriva principal → effective grant → session epoch` zinciri koparsa
attribution ve negative floor güvenilmez olur. Bu bir iki-provider wiring ayrıntısı değil, high-consequence authorization
hard fail’idir.

**Düzeltme / kapanış kanıtı.**

- Her issuer için current session lookup/revoke, token freshness, `iss/aud/sub`, factor assurance, account-state ve
  provider incident state’i ayrı kaydet; API tek global security epoch ve immutable provider-subject mapping uygulasın.
- Provider A/B’den biri unavailable ise privileged positive action `HELD`; diğer issuer tek başına bypass olmasın.
- logout-all, role revoke, recovery, factor loss, merge/split, duplicate-subject, support lockout ve lost-response
  için same-operation-id ve protected audit fixture’ı çalıştır.
- Provider değişimi veya B→A dönüşünde credential re-enrollment, source/target mapping, historical attribution ve
  pending authority için explicit migration freeze/rollback contract’i göster.

**Yönetici önerisine etkisi.** B “hazırlıklı” bir seçenek olarak ancak bu matrix ve drill ile tutulabilir. A/B’nin
eşit `HELD` tablosu C-04’ün yalnız B’ye özgü maliyet/karmaşıklık ve güvenlik riskini saklamamalıdır.

## 3. MAJOR bulgular

### M-01 — Gizli Auth/TCO kalemleri owner tavanıyla karşılaştırılmamış

`DEC-0030`/`DEC-0032` gereği yalnız headline abonelik değil, güvenli minimum BOM karşılaştırılmalıdır. 2026-09-18
resmi sayfalarda görünen sinyaller şöyledir; bunlar USD liste fiyatıdır, TRY karşılığı değildir ve satın alma öncesi
yeniden doğrulanmalıdır:

| Kalem | Resmi güncel sinyal | Owner/TCO anlamı |
|---|---|---|
| Supabase Free | $0; 50K MAU; 5 GB egress; 1 GB file storage; 1 saat Auth audit log; 1 gün platform log; pause; session timeout/single-session yok; backup/PITR/SLA/email support yok | Prototype/closed test için kullanılabilir; production privileged assurance ve recovery kanıtı değildir |
| Supabase Pro | $25/ay; 100K MAU; 7 gün Auth/platform log; daily backup 7 gün; 250 GB egress; quota üstü MAU $0.00325; spend cap varsayılan açık | Headline tek başına API, protected audit/floor, object backup, monitoring, incident veya exit’i kapsamaz |
| Supabase ekleri | Custom domain $10/domain/project/ay; PITR $100/7 gün retention/ay başlangıcı; phone MFA $75 ilk project + $10 ek project/ay; log drain $60/drain/ay + event/egress; compute/egress/storage ayrıca | Domain, SMTP/SMS, log retention, backup/restore ve incident ayı hidden recurring/scale cost yaratır |
| Supabase Auth e-posta | Default SMTP yalnız pre-authorized adresler, değişebilir rate limit (dokümanda 2 mesaj/saat) ve no-SLA best-effort; production için custom SMTP önerilir ([Custom SMTP](https://supabase.com/docs/guides/auth/auth-smtp)) | Auth e-postası “Supabase içinde ücretsiz” varsayılamaz; SMTP sağlayıcısı, sender domain, DNS/DKIM/DMARC/SPF ve abuse/standby planı ayrı kalemdir |
| Supabase phone/SMS | Phone OTP için dış SMS sağlayıcısı gerekir; MessageBird, Twilio, Vonage vb. ve ülke düzenlemeleri/rate limitleri vardır ([Phone sign-in](https://supabase.com/docs/guides/auth/phone-login)) | SMS privileged factor değildir; consumer/recovery seçilirse mesaj, fraud/abuse ve ülke maliyeti scale-triggered olur |
| Clerk | Hobby 50K MRU; Pro MFA, 50K MRU dahil, $0.02/MRU overage; Pro $20/ay annual billing; MFA/passkey üretim özellikleri plan bağımlı; log/support katmanları ayrışır ([Clerk pricing](https://clerk.com/pricing)) | B’de Supabase consumer + ikinci IdP sabit ücret/overage birlikte hesaplanmalı; MAU ile MRU aynı ölçü değildir |
| Auth0 | Free 25K MAU; Essentials $35/ay ve 500 MAU; Professional $240/ay; MFA, audit stream, environment ve support plan bağımlıdır ([Auth0 pricing](https://auth0.com/pricing)) | B’nin “ayrı IdP” seçimi TRY tavanını, support ve privileged feature gereksinimini hızla etkileyebilir |

Fiyatlar, limitler, plan adları, beta/GA, vergi/kur/region, card fee ve provider terms değişebilir. Bu tablo satın alma
onayı değildir. `TRY 2.000–3.000/ay` gelecekteki planning ceiling’idir; her senaryoda USD→TRY, vergi/kur aralığı,
mandatory/deferrable/optional/scale-triggered, 1K/10K/50K MAU/MRU, normal ay, incident ayı, restore ve exit ayı
gösterilmelidir.

**Düzeltme.** A/B için tek normalized BOM ve owner stop/hold kuralı üret: Auth planı + API runtime + SMTP + domain/DNS
+ SMS (kullanılıyorsa) + protected audit/fallback + log/monitoring + object backup + support + restore/exit. Unknown
satır `UNVERIFIED`, tavan aşımı `BILLING_HELD` veya capability `HELD` olmalı.

**Yönetici etkisi.** M-01 kapanana kadar “A daha düşük”, “B daha yüksek” yalnız nitel hipotezdir; A/B TCO kazananı
değildir. Manager Proposal §6/§7’deki owner monthly cost satırı genişletilmelidir.

### M-02 — No-owner-debug ve AI task operability provider yüzeylerinde henüz kanıtlanmamış

Öneri task-scoped AI identity ve plain-language state’leri doğru koyuyor; fakat gerçek kimlik işletimi için gereken
provider/configuration işleri task grafiğine ayrılmamış: SMTP credential ve sender domain; DNS TXT/CNAME/DKIM/DMARC/SPF;
passkey RP-ID/origin ve Android app-link; factor enrollment/lost-factor; issuer mapping; billing/spend-cap;
log/audit drain; provider support ticket; account lockout ve export. Bunlar SQL/SSH gerektirmese bile legal/billing/
provider owner yetkisi ve insan/kurum doğrulaması gerektirir. B’de aynı task aileleri iki issuer ve iki support yolu için
tekrarlanır. Clerk resmi belgeleri Flutter’ı güncel SDK referansında community-maintained olarak listeler ve 2025
duyurusu Flutter SDK’yı beta olarak tanımlar ([Clerk SDK reference](https://clerk.com/docs/reference/overview),
[Flutter SDK public beta](https://clerk.com/changelog/2025-03-26-flutter-sdk-beta)); bu, B’nin internal browser-only
sınırını netleştirmeyi gerektirir.

**Düzeltme.** Her provider task’ı için `task_id`, allowed/forbidden paths, credential class, human external action,
expected evidence, rollback/forward recovery, incident owner, reviewer, validator ve plain-language handoff yaz.
AI hiçbir task’ta provider owner, billing root, unrestricted SQL, service key, raw SMTP/SMS secret veya high-consequence
approval credential alamamalı. Owner yalnız nontechnical approval/payment/legal/support escalation seçmeli; DNS/secret/
console diagnosis işi owner’a dönmemeli.

**Yönetici etkisi.** “AI-operable” ifadesi task simulation ve support handoff kanıtı olmadan PASS sayılamaz. A’da görev
sayısı daha az olabilir; B’de issuer mapping/revoke/recovery/support görevleri artar. B bu nedenle otomatik fallback değildir.

### M-03 — Exit, credential/factor continuity ve two-provider migration yüzeyini kapsamıyor

Stable Kavriva principal ve app-owned audit doğru başlangıçtır; fakat “provider değiştirme” satırı yalnız export/
clean-room düzeyinde kalıyor. Identity export’un password hash, passkey credential, factor, recovery code, linked
identity, email/phone verification, session/refresh/revoke history, provider role/claim, signed object handle ve
provider-specific audit semantics’i nasıl taşıyacağı yazılmamış. Passkey private key provider’da değildir; Supabase
duyurusu public key’in Auth’ta, private key materyalinin kullanıcının authenticator/credential provider’ında kaldığını
belirtir ([Supabase passkey beta changelog](https://supabase.com/changelog/46458-passkeys-for-supabase-auth-beta)). Bu nedenle
provider/RP-ID değişiminde re-enrollment, factor loss ve support recovery kaçınılmaz bir ürün state’idir; otomatik
credential taşıma varsayılmaz.

**Düzeltme.** A ve B için clean-room exit fixture’ı: stable principal ve historical actor; provider-subject mapping;
role/grant/competence/policy version; pending operations; audit/fallback; object bytes/handles; email/phone; factor
re-enrollment; old session/refresh revocation; deletion/recall/security floor; partial/rollback. Yeni provider’da
credential re-enrollment tamamlanmadan privileged positive action `HELD`; historical attribution korunmalı.

**Yönetici etkisi.** Provider-neutral core korunmalı, ancak “provider değişimi mümkündür” iddiası evidence gelene kadar
`OPEN/HELD` kalmalı. A’nın tek issuer olması migration’ı otomatik kolaylaştırmaz; B’nin iki issuer’ı mapping yükünü
artırır.

### M-04 — Android-first, iOS-later kimlik/redirect/recovery parity kapısı eksik

DEC-0032’nin Android-first kararı owner kaynakları ve yayın sırasıdır; Android kanıtı iOS identity/session/recovery
kanıtı değildir. Flutter consumer flow’unda deep-link/PKCE, Android app-link, reinstall/keystore, iOS universal-link/
keychain, passkey RP/origin, borrowed-iPhone erişilebilirliği ve factor-loss recovery ayrı failure yüzeyleridir.
Internal browser passkey kanıtı consumer mobile hesabına veya iOS’a otomatik taşınamaz. Manager Proposal §8’de gerçek
fixture listelenmiş olsa da provider activation kapısına Android/iOS parity şartı bağlanmamıştır.

**Düzeltme.** Android gerçek cihazı ilk lane olarak kullan; fakat account-light→profile, logout-all/revoke, lost device,
deep-link/PKCE, factor loss, reinstall/restore ve accessibility fixture’ını Android’de kapatmadan provider contract
olumlu sayılmasın. iOS-later lane için aynı provider-neutral contract’ın borrowed-iPhone üzerinde minimum parity ve
kalıcı test erişimi planı olsun. Borrowed iPhone hiçbir kritik release dependency’si olmasın.

**Yönetici etkisi.** Android-first korunur; ancak “A/B provider seçimi Android’de çalıştı” iOS release gate’ini
kaldırmaz. Eksik parity `HELD`, güvenlik standardı düşürme değildir.

### M-05 — Auth audit ile product protected audit/floor ayrımı doğru, fakat custody/retention/restore TCO’su açık

Araştırma ve sentez, provider Auth log’unun Kavriva approval/publish/recall/AI operation audit’i olmadığını doğru
söylüyor. Fakat manager proposal normal + fallback custody, append-only/tamper-evident, restore continuity ve
monotonic negative floor’ın hangi failure domain/cost/support ile sağlanacağını seçmiyor. Supabase resmi fiyatında Free
platform log’u 1 gün, Pro 7 gün; Pro’da log drain ayrıca $60/drain/ay ve event/egress ücretleri görünür; Auth audit
retention planlara göre ayrışır ([Supabase pricing](https://supabase.com/pricing)). Clerk’te Hobby 1 gün, Pro 7 gün app log;
Business’te 30 gün ve priority support vardır ([Clerk pricing](https://clerk.com/pricing)). Provider log retention’ı
protected product audit veya negative floor yerine konamaz.

**Düzeltme.** Minimum protected event schema, independent custody, fallback write-before-effect, retention/redaction/
legal hold, restore manifest, floor checkpoint, gap/fork detection, export ve owner-readable `AUDIT_HELD` state’i için
candidate-neutral BOM ve drill yaz. Auth/API/object/audit/floor birlikte clean-room restore edilmeden positive action
başlamasın.

**Yönetici etkisi.** A’nın tek control-plane basitliği audit/floor bağımlılığını silmez; B’nin ikinci IdP’si de product
audit/floor’ı otomatik bağımsız yapmaz. Her ikisi için `HELD`.

### M-06 — Account-light ve provider anonymous primitive’leri arasındaki fark migration/recovery sözleşmesine bağlanmamış

Proposal doğru olarak local installation principal’ı varsayılan yapıyor ve server anonymous user’ı zorunlu kılmıyor.
Bu karar korunmalı; çünkü Supabase anonymous user `authenticated` PostgreSQL rolüyle görünür, `is_anonymous` ayrımı
ister ve sign-out/başka cihaz sonrasında aynı anonim hesaba geri dönülemeyebilir ([Supabase anonymous sign-ins](https://supabase.com/docs/guides/auth/auth-anonymous)).
Firebase’in anonymous-link primitive’i veya B’deki privileged IdP’nin account flow’u bu domain migration’ını otomatik
çözmez.

**Düzeltme.** Local-only, anonymous provider user, verified profile, device loss, reinstall, unlink, duplicate,
merge/split, partial upload ve server-accepted state için ayrı identity/object state’leri yaz. E-posta/display-name
eşleşmesi karar olmasın; target accepted/reconciled olmadan local source silinmesin. “Local-only loss/held” kullanıcıya
dürüstçe gösterilsin; recovery provider hesabı teknik geçmişi veya authority’yi sessizce miras almasın.

**Yönetici etkisi.** Account-light önerisi korunabilir; fakat provider comparison’daki “anonymous + link primitive”
tek başına A veya B avantajı sayılmamalıdır.

### M-07 — Eşit `0 PASS / 15 HELD / 0 REJECT` tablosu aday-spesifik riskleri görünmez kılıyor

Belgedeki ortak senaryo sonucu iyi bir no-code disiplinidir, fakat aynı `HELD` etiketi A’nın tek-provider blast-radius’u,
B’nin two-issuer revoke/mapping yükü, Clerk/Auth0 plan/support farkı, Supabase custom SMTP zorunluluğu ve last-admin
staffing açığını ayırt etmiyor. Ayrıca `HELD`, “güvenli” değil, “belgesel olumlu kanıt yok” demektir.

**Düzeltme.** Her ortak senaryo için A ve B sütunlarına `CRITICAL/MAJOR/MINOR`, dependency count, failure domain,
owner action, price/plan dependency, exit dependency ve `REJECT-IF-UNMITIGATED` koşulu ekle. En az B-specific iki issuer
revoke, A-specific common outage, both-specific last-admin, SMTP outage ve floor/audit-loss satırları ayrı olsun.

**Yönetici etkisi.** Yönetici önerisi “A sade / B güçlü” anlatısını ancak bu weighted değil evidence-based matrix ile
sürdürebilir. A/B eşit değerlendirilecekse eşit fixture ve eşit hard gate korunmalı; `HELD` sayısı eşit diye winner
çıkarılmamalı.

## 4. MINOR bulgular

### m-01 — Headline fiyatların yanına tarih, plan, ölçü birimi ve kapsam etiketi eklenmeli

Provider research fiyatları tarihli ve değişken olduğunu söylüyor; manager proposal’ın kısa anlatımında bu bağlam
okuyucuya taşınmıyor. Supabase `MAU`, Clerk `MRU`, Auth0 `MAU` aynı metrik değildir; “$25” veya “$35” toplam güvenli
aylık maliyet değildir. Çözüm: her rakamda `official list / USD / tarih / annual-vs-monthly / tax-FX excluded / quota /
overage / support / exit` etiketi.

### m-02 — “Stable passkey” kabul ifadesi capability değil, fixture paketi olarak yazılmalı

GA/stable etiketi; browser origin/RP-ID, Android/iOS deep-link, re-auth/transaction binding, lost factor, recovery,
logout-all, accessibility, audit ve provider outage kanıtını tek başına göstermez. Düzeltme: stable/GA yalnız ilk
önkoşul; gerçek acceptance fixture ve independent review olmadan `PASS` yok.

### m-03 — Provider-neutral abstraction sınırı açıkça provider-adapter olarak adlandırılmalı

Stable Kavriva principal ve authorization tuple taşınabilir; ancak issuer `sub`, token/session semantics, factor,
linking, domain/origin, audit export ve recovery davranışı provider-specific adapter gerektirir. “Provider-neutral”
ifadesi credential/factor semantiğini tamamen soyutlayabildiği izlenimi vermemeli.

## 5. A/B’ye eşit uygulanan zorunlu kabul paketi

Her iki aday aynı paketi sunmadan biri diğerine göre seçilmemeli:

1. Actor/session/issuer/principal/grant/competence/independence/security-epoch mapping; old-token, claim drift ve
   two-tab/in-flight commit negative testleri.
2. Privileged passkey/factor registration, step-up, factor loss, recovery, logout-all, role revoke, pending authority
   cancellation, cross-tenant and provider outage fixture’ları.
3. Last-admin, independent negative suspension, protected audit fallback, `OUTCOME_UNKNOWN` ve restore quarantine
   tabletop; owner SQL/SSH/debug yapmadan tamamlanmalı.
4. Auth plan/capability matrix; SMTP/SMS/domain/DNS/log/audit/support/monitoring/object/floor/backup/restore/exit BOM;
   1K/10K/50K MAU/MRU, normal/incident/restore/exit ayı; USD + tax/FX ranges; hard cap/overage/stop action.
5. Android-first gerçek cihaz identity/recovery/deep-link/PKCE/key-store evidence; iOS-later parity plan and borrowed
   device boundary; no automatic Android→iOS proof.
6. Account-light local→profile, anonymous/link, merge/split, device loss, reinstall, deleted/ban, email takeover and
   clean-room provider migration; historical attribution and negative floor preserved.
7. AI task simulation: provider setup/config, bounded diagnostic, owner-facing handoff, secret/credential class,
   allowed/forbidden scope, reviewer/validator, rollback and support escalation. AI cannot use provider owner,
   billing root, service role, SQL/SSH or high-consequence credentials.

Bu paketin herhangi bir kritik satırı `UNKNOWN` ise sonuç `HELD`; mandatory negative/recovery/audit/owner-debug ihlali
kanıtlanırsa ilgili capability `REJECT-IF-UNMITIGATED` olur. Adayın diğeri otomatik kazanan sayılmaz.

## 6. Yönetici önerisine düzeltilmiş etkisi

1. **Phase-4 consumer working direction:** Supabase Auth, account-light local-first ve provider-neutral Kavriva
   principal olarak koşullu tutulabilir; bu bir hesap/plan/satın alma onayı değildir.
2. **Privileged Internal Operations:** A, yalnız passkey API’si stable/GA olduktan sonra değil, plan capability,
   transaction-bound step-up, factor-loss recovery, global revoke, outage, protected audit/floor, support ve exit
   fixture’ları geçerse açılabilir.
3. **B’nin rolü:** B yalnız internal browser challenger olarak tutulabilir; iki issuer global epoch/mapping, second
   provider cost/support/recovery ve clean-room exit kanıtı gelmeden “hazırlıklı fallback” değil `HELD` adaydır.
4. **No-owner-debug:** Last-admin, provider outage, SMTP/DNS, billing hold ve audit/floor kaybında owner’a teknik
   repair görevi çıkarsa A ve B privileged production için reddedilir; plain-language hold ve external support/recovery
   yolu gerekir.
5. **Budget:** TRY 2.000–3.000/ay yalnız gelecekteki non-store planning ceiling’idir. Tavanı aşan mandatory assurance
   saklanamaz veya TOTP/SMS/magic-link ile düşürülemez; ilgili capability `HELD` kalır.
6. **Android/iOS:** Android-first sürer; iOS-later identity/recovery parity ayrı gate’tir. Ödünç iPhone erişimi
   kalıcı release/support dependency’si yapılamaz.
7. **Exit:** Stable principal iyi sınırdır, fakat factor/credential re-enrollment, provider-subject mapping,
   protected audit/floor, objects, session revoke ve negative behavior clean-room kanıtı olmadan exit iddiası kapatılmaz.

## 7. Final disposition

`HELD — NO WINNER — 0 PASS / 14 bulgu (4 CRITICAL, 7 MAJOR, 3 MINOR) / privileged production yok`

Bu inceleme A’yı veya B’yi seçmez; `DEC-0035` ile uyumlu Supabase-centered Phase-4 çalışma yönünü, API authority ve
fallback sınırlarını değiştirmez. Sadece yönetici proposal’ının owner/TCO/operability iddialarını evidence gate’e bağlar.
Bir sonraki karar; aynı fixture, aynı hard gate, resmi güncel fiyat/capability tekrar kontrolü, owner-readable
recovery/outage runbook, gerçek Android/iOS/restore/exit kanıtı ve bağımsız review tamamlanmadan verilemez.

### Birincil güncel kaynaklar

- [Supabase pricing](https://supabase.com/pricing) — plan, MAU, egress, storage, log, custom domain, PITR, phone MFA,
  log drain, support ve SLA karşılaştırması.
- [Supabase User sessions](https://supabase.com/docs/guides/auth/sessions) — session default’u, session bounds ve
  `session_id` kontrolü.
- [Supabase Passkey authentication](https://supabase.com/docs/guides/auth/passkeys) — experimental/API-change uyarısı.
- [Supabase passkey beta changelog](https://supabase.com/changelog/46458-passkeys-for-supabase-auth-beta) — 2026-05-28
  beta statüsü ve public/private key custody açıklaması.
- [Supabase User Management](https://supabase.com/docs/guides/auth/managing-user-data) — delete/ban ve canlı JWT sınırı.
- [Supabase Custom SMTP](https://supabase.com/docs/guides/auth/auth-smtp) — production SMTP gereksinimi, rate limit ve
  no-SLA default servis.
- [Supabase Phone sign-in](https://supabase.com/docs/guides/auth/phone-login) — SMS provider ve ülke/rate-limit yükü.
- [Supabase anonymous sign-ins](https://supabase.com/docs/guides/auth/auth-anonymous) — anonymous/authenticated ayrımı ve
  device/sign-out geri dönüş sınırı.
- [Clerk pricing](https://clerk.com/pricing) — MRU, plan, MFA, overage, log/support ve annual billing.
- [Clerk SDK reference](https://clerk.com/docs/reference/overview) — Flutter’ın community-maintained sınıflandırması.
- [Clerk Flutter SDK public beta](https://clerk.com/changelog/2025-03-26-flutter-sdk-beta) — Flutter SDK beta duyurusu.
- [Auth0 pricing](https://auth0.com/pricing) — MAU, Essentials/Professional, MFA, audit streaming ve support.

Fiyat, kota, plan, beta/GA, support, tax/FX ve provider terms değişkendir; yukarıdaki resmi sayfalar satın alma veya
güvenlik onayı değildir. Phase-5 ADR / ödeme öncesi yeniden doğrulama zorunludur.
