# DEBATE-010 — Düzeltilmiş Judge Sentezi

Status: `PASS_WITH_CHANGES — CORRECTIONS INCORPORATED / USER APPROVED DEC-0037 / NO PRIVILEGED WINNER / ADR NOT READY`
Date: `2026-09-18`
Scope: `NO-CODE / NO ACCOUNT / NO PURCHASE / GATE 4 -> 5 CLOSED`

## 1. Hüküm

Araştırma ve iki bağımsız Luna Max incelemesi, temel yönü koruyor fakat hiçbir kimlik sağlayıcısını veya privileged
üretim yolunu `PASS` saymıyor:

- **Consumer profile için Supabase Auth**, mevcut Supabase-merkezli backend ve Flutter desteği nedeniyle Phase-4 lider
  çalışma yönü olarak kalabilir.
- **Account-light kullanım**, varsayılan olarak cihazdaki Kavriva local installation principal ile başlar; gereksiz
  server anonymous account oluşturulmaz.
- **Internal Operations privileged kimliği için kazanan yoktur.** Tek Supabase Auth daha sade ve düşük bileşenlidir,
  fakat passkey bugün experimental/beta ve ortak failure-domain riski vardır. Ayrı IdP beta takvimini ayırabilir, fakat
  iki issuer, iki recovery/support ve ek ücret nedeniyle otomatik daha güvenli değildir.
- **High-consequence production activation**, phishing-resistant credential'ın varlığına veya `GA` etiketine değil,
  aşağıdaki bütün capability/recovery/audit/outage/exit fixture paketinin geçmesine bağlıdır.

Bu belge sağlayıcı, plan, factor, oturum süresi veya satın alma seçmez. Belgesel sonuç iki aday için de
`0 PASS / 15 HELD / 0 REJECT`tir. `HELD`, güvenli olduğu anlamına değil, olumlu üretim kanıtı bulunmadığı anlamına gelir.

## 2. Kullanıcıya teknik olmayan karar özeti

Telefon uygulamasında kullanıcı temel değeri hesap açmadan deneyebilir. Kalıcı profil istediğinde hangi verinin
taşınacağını görür; çakışma varsa sistem sessizce birini silmez. Tüketici hesabı için Supabase en sade başlangıç yönüdür.

Şirket içi tarayıcıda ise giriş yapmak tek başına onaylama veya yayımlama yetkisi vermez. Kritik işlem anında kişinin
oturumu, güncel görevi, kapsamı ve ikinci güvenlik doğrulaması yeniden kontrol edilir. Supabase'in geçiş anahtarı özelliği
kararlı ve bütün testlerden geçmişse tek sistem kullanılabilir. Geçmezse yalnız personel için ayrı hizmet değerlendirilebilir.
İkinci hizmet şimdiden satın alınmaz. Güvenli yöntem yoksa kritik personel işlemi açılmaz.

## 3. Bağlanan ortak kimlik ve yetki sözleşmesi

### 3.1 Kimlikler ayrıdır

- local installation/device partition;
- Kavriva product profile/principal;
- provider-qualified `(issuer, subject)` kimliği;
- browser/mobile session ve assurance;
- role/grant/delegation;
- competence ve independence;
- workload/service/AI identity;
- provider/legal/billing/recovery owner;
- immutable historical audit actor.

E-posta, görünen ad veya provider user ID bu sınıfları sessizce birleştirmez.

### 3.2 Authentication yetki değildir

IdP token'ı yalnız kimlik/oturum kanıtıdır. Kavriva API her hassas istekte current actor, issuer/session, security epoch,
action, exact resource/tenant/scope, classification, role/grant, competence, independence, policy version, resource
version/generation ve operation ID ile `ALLOW`, `DENY` veya `HELD` üretir. Cached claim, `user_metadata`, açık browser
sekmesi, gizli düğme, provider admin rolü veya client-supplied ID yetki değildir.

### 3.3 Provider adapter sınırı

Provider-neutral olan Kavriva principal, authorization tuple, security epoch, audit ve product state'tir. Token/session,
factor, redirect/origin, linking, logout, key rotation ve recovery semantiği provider-specific adapter'da açıkça tutulur;
tamamen soyutlanmış sayılmaz.

## 4. Reviewer düzeltmeleri — bağlayıcı ekler

### 4.1 End-to-end revoke

Security epoch yalnız JWT'yi değil, şu uçları da kapsayan karara bağlanır:

- current provider session/account state;
- grant/policy/competence generation;
- pending ve in-flight operation;
- lost-response/status lookup/retry;
- private object handle/signed URL ve object generation;
- browser cache/service worker kapsamı;
- local offline package generation, classification, expiry ve key state.

İndirilmiş kopyanın uzaktan geri alınamayacağı dürüstçe belirtilir. Private object için kısa ömürlü, exact audience/
scope/object/version/epoch bağlı handle veya server mediation gerekir. Revoke sonrası yeni handle verilmez. Remote wipe
yalnız best-effort'tür; authority değildir.

### 4.2 İki ayrı kurtarma yolu

**Privileged account recovery** ve **emergency negative authority** aynı şey değildir:

- Account recovery eski session, refresh/recovery artifact ve pending high-consequence authority'yi iptal eder; fresh
  phishing-resistant giriş ister; recovery aktörü approve/publish/role grant yapamaz.
- Emergency negative authority yalnız suspension/recall/quarantine/access deny üretir; positive truth, publication,
  unsuspension veya competence oluşturamaz. Normal IdP/API/audit failure domain'inden mümkün olduğunca ayrılır ve
  monotonic negative floor artırır.

Tek teknik olmayan sahip bugün gerçek dual-control personel modelini tek başına sağlayamaz. İkinci bağımsız gerçek insan/
kurum, legal/support recovery yolu ve custody daha sonra açık dış bağımlılık olarak çözülene kadar privileged production
`HELD` kalır. AI bu insan/kurum otoritesini taklit edemez.

### 4.3 Protected audit before effect

Auth log ürün audit'i değildir. High-consequence effect'ten önce veya eşdeğer transactional güvenceyle protected event
durmalıdır. Event; actor/workload, effective role/scope, issuer/session assurance, epoch, policy/grant/competence version,
operation ID, object/version, old/new meaning, ordered server time, reason, result ve impact/recovery owner taşır.

Normal custody ve yeterince bağımsız fallback yoksa positive effect `HELD` olur. Gap/fork/replay, audit read/export/
redaction, retention/legal hold, restore ve fallback reconciliation ayrıca sınanır. Başarılı DB cevabı tek başına başarı
kanıtı değildir.

### 4.4 İki issuer için hard gate

Aday B seçilirse her issuer için allowlisted `iss`, exact `aud`, algorithm/key/JWKS rotation, expiry/clock policy,
issuer-qualified immutable subject mapping, current session/account state ve assurance semantics tanımlanır. E-posta/
display-name automatic mapping yasaktır. Collision veya claim disagreement `HELD` olur.

Tek Kavriva security epoch operation'ı iki provider session'ını, pending authority'yi ve product grants'i tutarlı
biçimde kapatmadan global logout/revoke tamam sayılmaz. Bir provider unavailable ise diğer issuer bypass oluşturmaz.

### 4.5 Phishing-resistant etiket yeterli değildir

`GA/stable`, `passkey` veya `aal2` tek başına kabul değildir. Privileged fixture şunları birlikte kanıtlar:

- correct origin/RP-ID, user verification ve challenge freshness;
- factor enrollment/remove/loss, downgrade ve recovery;
- action/resource/version/consequence bağlı fresh step-up;
- logout-all, stolen token ve current session/epoch deny;
- browser CSRF, redirect allowlist, PKCE ve transaction binding;
- accessibility ve supported browser/device davranışı;
- outage, key rotation ve provider support/recovery.

TOTP, SMS veya magic link phishing-resistant fallback olarak kullanılamaz.

### 4.6 Account-light migration ayrı product operation'dır

Provider identity linking, Kavriva history/evidence/motorcycle ownership merge'i değildir. Migration; source possession,
fresh target re-auth, kapsam/classification preview, stable operation ID/fingerprint, merge freeze, immutable source→target
mapping, per-conflict `HELD`, target acceptance/reconciliation ve split/rollback taşır. Target kabul edilmeden local source
silinmez; entitlement/role/grant yeniden hesaplanır.

### 4.7 Direct data yolları

Flutter/browser için generic Data API, RPC, Storage, view/function veya signed URL high-consequence bypass oluşturamaz.
Grants + RLS/Storage defense-in-depth kalır; `USING`/`WITH CHECK`, view/function semantics ve cross-tenant negative tests
Phase-5 sözleşmesinde doğrulanır. `service_role` ve provider owner credential client, repo, log veya AI context'ine girmez.

## 5. Eşit aday hükmü

### Aday A — Tek Supabase Auth

Phase-4'te sadelik lideridir; privileged üretim kazananı değildir. Şu koşulların tümü gerekir:

- passkey API yalnız stable/GA değil, §4.5 fixture'ını geçer;
- seçilen plan session controls, required log/support ve recovery yeteneklerini gerçekten sağlar;
- common provider outage sırasında safe read, positive hold ve bağımsız negative authority kanıtlanır;
- end-to-end revoke, protected audit/floor, object/private-data ve clean-room exit kapanır.

### Aday B — Supabase consumer + ayrı privileged IdP

Yalnız Internal Operations için challenger'dır; automatic fallback değildir. Clerk/Auth0 isimleri kısa listedir, seçim
değildir. §4.4 iki-issuer hard gate, ikinci provider support/recovery, normalized cost ve exit kanıtı olmadan A'dan üstün
sayılamaz. Consumer Flutter kimliği bu adaylara taşınmış değildir.

## 6. Owner-readable güvenli maliyet kapısı

Headline `USD 25` veya `USD 35` toplam maliyet değildir. Satın alma/ADR öncesi A ve B için aynı normalized BOM gerekir:

- Auth planı ve MAU/MRU ölçüsü/overage;
- API runtime/compute;
- custom SMTP, sender domain ve DNS;
- SMS yalnız kullanılıyorsa mesaj/fraud/ülke maliyeti;
- domain/custom domain;
- provider/product audit, fallback custody, log drain ve monitoring;
- object backup, restore, PITR ve clean-room exit;
- support, incident ve last-admin recovery;
- vergi, kur ve normal/incident/restore/exit ayları.

Her satır `mandatory / deferrable / optional / scale-triggered`, güncel resmi tarih, plan, kota, hard cap ve stop action
taşır. TRY 2.000–3.000/ay gelecekteki planlama tavanıdır; satın alma izni değildir. Zorunlu assurance bütçeye sığmıyorsa
TOTP/SMS/magic-link ile düşürülmez; capability `BILLING_HELD/HELD` kalır.

## 7. No-owner-debug ve AI görev sınırı

Provider yapılandırma işleri ayrı task aileleri olur: issuer adapter, SMTP/domain/DNS, passkey origin/RP-ID, redirect/
PKCE, session/epoch, recovery, audit drain/fallback, billing/cost stop, support escalation, export/clean-room migration.
Her task allowed/forbidden scope, credential class, human external action, fixture, rollback/forward recovery, reviewer,
validator ve plain-language handoff taşır.

AI provider owner, billing root, unrestricted SQL, `service_role`, raw SMTP/SMS secret veya high-consequence credential
alamaz. Owner yalnız anlaşılır ürün/ödeme/hukuki/support kararını verir; DNS/secret/log onarımı yapmaz.

## 8. Aktivasyon kapısı

Privileged Internal Operations high-consequence production ancak şu paket birlikte geçerse açılır:

1. stable principal + provider adapter + current authorization tuple;
2. passkey/step-up/factor-loss/stolen-token/logout-all fixtures;
3. role revoke, stale tab, direct API, cross-tenant ve in-flight commit negative tests;
4. privileged recovery + ayrı emergency negative authority tabletop;
5. protected audit/fallback/floor + restore reconciliation;
6. end-to-end object/local-package/queue revoke;
7. last-admin ve provider/SMTP/DNS/billing/outage owner-readable runbook;
8. Android-first real-device identity/recovery/deep-link fixture; iOS-later ayrı parity gate;
9. normalized safe-minimum BOM ve owner cost stop;
10. identity/audit/object/session clean-room exit with factor re-enrollment;
11. independent security ve owner/TCO review.

Critical satır `UNKNOWN` ise `HELD`; mandatory negative/recovery/audit/no-owner-debug ihlali varsa ilgili capability
`REJECT-IF-UNMITIGATED` olur. Diğer aday otomatik kazanan sayılmaz.

## 9. User-approved working direction olarak önerilen kapsam

Kullanıcı onaylarsa yalnız şu Phase-4 yönü bağlanır:

- consumer profile için Supabase Auth lider çalışma yönü;
- account-light local-first ve açık, geri alınabilir profile migration;
- provider-qualified stable Kavriva principal, provider adapter, API authorization ve security epoch;
- privileged üretimde phishing-resistant, transaction-bound ve test edilmiş activation kapısı;
- Aday A kapıyı karşılamazsa yalnız Internal Operations için Aday B'nin eşit kanıtla değerlendirilmesi;
- protected audit-before-effect, end-to-end revoke, ayrı recovery/negative authority, cost/no-owner-debug/exit hard gates.

Onay; provider hesabı, ücretli plan, Clerk/Auth0, passkey implementasyonu, exact factor, session TTL, SMTP/SMS, ikinci
insan/kurum, kod, prototip, ADR veya Gate 4 -> 5 geçişi değildir.

## 10. Açık kalanlar

- exact privileged IdP/provider/plan ve satın alma tarihi;
- session/JWT/refresh/step-up süreleri ve browser cookie/storage biçimi;
- ikinci bağımsız recovery/negative operator insan/kurum modeli ve support SLA;
- protected audit/fallback/floor teknolojisi ve retention;
- SMTP/domain/DNS, notification ve abuse provider'ı;
- local encryption/keystore ve private offline-data policy;
- role/capability/competence/quorum sayıları;
- exact recovery/merge/split UI ve legal consent/retention;
- normalized maliyet BOM'u ve güncel TRY karşılığı;
- gerçek Android/iOS/browser/restore/exit evidence;
- Phase-5 ADR ve implementasyon task'ları.

## 11. Review kayıtları

- `DEBATE-010__REVIEW_A_SECURITY_RECOVERY.md`: `HELD / NO WINNER`, 4 critical, 9 major, 1 minor.
- `DEBATE-010__REVIEW_B_OWNER_TCO_OPERABILITY.md`: `HELD / NO WINNER`, 4 critical, 7 major, 3 minor.

İki review de consumer Supabase Auth çalışma yönünü reddetmez; hiçbir privileged provider veya production activation'ı
onaylamaz. Kullanıcı düzeltilmiş Phase-4 çalışma yönünü `DEC-0037` altında onayladı. Bu onay provider hesabı, plan,
satın alma, implementasyon, privileged activation, ADR veya gate geçişi değildir.
