# DEBATE-010 — Kimlik, Oturum ve Ayrıcalıklı Erişim Hata/Tehdit Araştırması

Status: `PHASE-4 RESEARCH / NO-CODE / ADR PENDING`
Date: `2026-09-18`
Scope: Tüketici mobil uygulaması + browser tabanlı Internal Data & Content Operations
Research cut: `2026-09-18` resmi kaynak okuması

## 1. Karar sorusu

Kavriva; çalınmış kimlik bilgisi, stale JWT/claim, kayıp cihaz, zayıf kurtarma, yanlış identity merge,
IdP kesintisi, tenant sınırı ihlali veya ayrıcalıklı AI görevi altında hangi erişimi sürdürmeli, hangisini
reddetmeli ve hangi kanıtı korumalıdır? Supabase Auth/Postgres/RLS/Storage mekanizmaları bu davranışın yalnızca
primitive ve savunma katmanlarıdır; ürün yetkisi Kavriva API/policy boundary'sinde yeniden değerlendirilir.

Bu kayıt araştırma ve no-code test matrisi kaydıdır. Kod, prototip, provider hesabı, şema, plan, satın alma,
üretim kanıtı veya Phase-5 ADR kararı içermez.

## 2. Devralınan bağlam ve bağlayıcı sınırlar

- `DEC-0026`: hibrit, kapsamlandırılmış ve bağlamsal yetkilendirme; commit-time re-authorization; ayrıcalıklı
  oturum/kurtarma kontrolü; protected audit; deny-by-default.
- `DEC-0034`: hassas erişim server/API üzerinden; Internal Operations online-authoritative; current state,
  history/provenance ve protected audit ayrı anlamlar; anti-resurrection recovery/exit.
- `DEC-0035`: yönetilen Supabase merkezli yön yalnızca Kavriva API authority boundary arkasında; RLS/Storage
  defense-in-depth; `service_role`/secret yalnız server-side; Studio Internal Operations değildir.
- `DEC-0036`: seçili görev için tam ve sürümlü offline paket; ayrı durable operation ledger; offline işlem
  high-consequence kabul/rol/approval/publish/recall authority'si değildir.
- `REF-HISTORY-001` ve `REF-PROFILE-001`: actor/source/evidence/current claim ayrıdır; role revoke geçmiş
  attribution'ı silmez; profile migration no-silent-loss/no-silent-overwrite ve conflict review ister.
- Teknik olmayan owner'ın SSH, SQL, dashboard repair veya log teşhisi yapması kabul edilen recovery yolu değildir.

## 3. Supabase araştırmasından çıkan güvenlik gerçekleri

1. **JWT canlılık garantisi değildir.** Supabase oturumu access JWT + dönen refresh token ailesiyle temsil eder; access
   token tipik olarak kısa ömürlüdür. Refresh token rotasyonu tekrar kullanım tespiti taşır, fakat resmi reuse interval ve
   parent-token istisnaları nedeniyle "bir kez kullanıldıysa her tekrar kesin saldırıdır" şeklinde basitleştirilemez.
   Access JWT `session_id` içerir. Bir user silindiğinde
   veya banlandığında daha önce verilmiş access JWT, `exp` süresine kadar geçerli kalabilir. Supabase dokümanı,
   hassas işlemlerde `session_id` değerinin `auth.sessions` ile kontrol edilmesini ayrıca önerir. Banned user'ın
   mevcut session'ları da otomatik revoke edilmiş sayılmaz. [User sessions][S1], [User Management][S2]
2. **Rol/claim değişikliği token refresh'e kadar eski kalabilir.** `raw_user_meta_data` kullanıcı tarafından
   değiştirilebilir ve authorization için kullanılmamalıdır. `raw_app_meta_data` authorization için daha uygun
   olsa da JWT, refresh edilene kadar güncel olmayabilir. Bu nedenle claim, yalnızca hızlı sinyal; hassas commit
   için current policy/grant/session epoch kontrolü gerekir. [RLS][S7], [Custom Claims/RBAC][S8]
3. **MFA UI eklemek tek başına koruma değildir.** Supabase `aal1`/`aal2` claim'leri üretir; MFA kuralları
   API, backend ve RLS'de uygulanmalıdır. Factor kaldırıldığında `aal2` düşüşü refresh aralığına bağlı olabilir;
   hassas işlem öncesi yeni session/refresh zorunlu bir güvenli varsayılandır. [MFA][S3]
4. **Anonim kullanıcı `authenticated` PostgreSQL rolünü kullanır.** Ayırmak için `is_anonymous` claim'i
   kontrol edilmelidir. Anonymous user sign-out, browser verisi temizleme veya başka cihaz sonrası hesabına
   erişemez; identity linking ve veri çatışması ürün tarafından açıkça çözülmelidir. Supabase dokümanı merge,
   overwrite veya mevcut hesabı tercih etme seçeneklerini uygulamaya bırakır. [Anonymous Sign-Ins][S4]
5. **Identity linking hassas bir hesap işlemdir.** Otomatik linking aynı e-posta adresini kullanır; doğrulanmamış
   e-posta ile linkleme pre-account-takeover riski yaratabileceği için Supabase ek koruma uygular. Manual linking
   beta'dır; SAML SSO hesapları linking hedefi değildir. Kavriva'nın profile/data merge kararı yine ayrı bir
   domain işlemidir. [Identity Linking][S5]
6. **Magic link e-posta hesabının güvenine dayanır.** Magic link tek kullanımlıdır; email OTP'nin varsayılan
   süresi 1 saattir ve bu değer üretim politikası değil, platform varsayılanıdır. E-posta hesabı ele geçirilirse
   link veya OTP de ele geçirilmiş kabul edilir. Privileged approval/publish için magic link tek başına yeterli
   güvence değildir. [Passwordless email][S6]
7. **RLS ve grant iki ayrı kapıdır; `service_role` RLS'yi bypass eder.** `authenticated` olmak tek başına
   ownership/tenant yetkisi değildir. Exposed nesnelerde grant + RLS; server API'de de tenant/scope/operation
   kontrolü gerekir. `service_role`/secret browser, Flutter veya AI context'ine giremez. [Securing your API][S9],
   [RLS][S7]
8. **Signed Storage URL Auth revoke ile otomatik kesilmez.** Storage signed URL ayrı bir anahtarla imzalanır
   ve Auth JWT anahtarının dönmesiyle iptal olmaz; süre dolana kadar çalışabilir. Bu nedenle private media için
   kısa süre, object-generation/authorization check ve hassas export için server-mediated handle gerekir.
   [Serving assets from Storage][S10]
9. **Supabase Auth audit log'u ürün audit'i değildir.** Auth event'leri dış log storage'a ve isteğe bağlı
   Postgres tablosuna yazılabilir; bu, Kavriva'nın approval/publish/recall/tenant/AI operation zincirinin
   bağımsız ve tam kanıtı yerine geçmez. [Auth Audit Logs][S11]
10. **Database backup Storage object'lerini taşımaz.** Restore/delete/revoke/identity floor için DB, object,
    session/policy ve protected audit birlikte reconcile edilmelidir. [Database Backups][S12]

## 4. Risk ayrımı: tüketici ve Internal Operations

| Boyut | Tüketici mobil | Internal Operations |
|---|---|---|
| Ana zarar | Özel history/not/photo, yanlış profile/vehicle bağlama, account takeover, güven ve güvenli kullanım kaybı | Yanlış teknik veri/guide değişikliği, approval/publish/recall bypass, cross-tenant veri sızıntısı, bozuk audit ve kitlesel etki |
| Kabul edilebilir varsayılan | Sınırlı public/teaching ve son güvenli offline paket; hesap değişikliği ve yeni sync için yeniden doğrulama | `DENY`/`HELD`, read-only durum veya güvenli negatif suspension; approval, publish, rol ve policy değişikliği offline/IdP belirsizliğinde kapalı |
| Kimlik güvencesi | Düşük riskli keşifte AAL1/magic link düşünülebilir; private history, identity change ve export için step-up | Approval, publication, emergency negative, access administration, audit/export ve quarantine-release için phishing-resistant MFA + işlem bağlı step-up |
| Oturum varsayımı | Mobil cihaz kaybolabilir, ağ ve refresh cevabı kaybolabilir; token/yerel paket kısa ve kapsamlı olmalı | Açık sekme güvenilir değildir; her hassas commit'te current actor, grant, scope, policy, session epoch ve object/version tekrar kontrol edilir |
| Kurtarma | Kullanıcı self-service recovery alabilir, fakat identity/data merge otomatik yapılmaz | Kurtarma normal girişten zayıf olamaz; dual-control veya süreli break-glass; recovery aktörü approval/publish yapamaz |
| Audit | Account/session, identity, data exposure ve merge olayları açıklanabilir kalmalı | Actor/effective grant/delegation/policy version/operation/result zinciri protected ve bağımsız olmalı; kanıt yoksa etki `HELD` |

Tüketici UX'inde sürtünme azaltılabilir; fakat bu, Internal Operations yetki zincirinin gevşetilmesi anlamına gelmez.
Özellikle aynı Supabase Auth projesini paylaşmak, iki yüzeyin aynı yetki veya aynı account-state varsayımını
kullanmasını gerektirmez.

## 5. Kimlik/oturum/ayrıcalık hata tehdit test matrisi

Belirtilen kabul testleri belge düzeyinde tanımdır; Phase 4'te gerçek sistem testi çalıştırılmaz. Her test,
başarılı görünen UI yerine authoritative API sonucunu, yan etkileri ve protected audit kanıtını kontrol eder.

| ID — senaryo | Tüketici riski | Internal Operations riski | Önleyici kontrol | Tespit ve kanıt | Güvenli varsayılan / kabul testi | Faz sınırı |
|---|---|---|---|---|---|---|
| **ID-01 — Çalınmış access/refresh token veya telefon** | Hesap takeover; private history, photo, note veya bağlı identity açığa çıkar. Telefon/SMS numarasının yeniden atanması da yanlış kullanıcıya erişim sağlayabilir. | Stolen browser/mobile token ile private evidence, export, approval veya rol/policy erişimi; telefon OTP'si privileged güvence sayılırsa geniş etki. | Access JWT kısa tutulur; refresh reuse detection ve session/device listesi; remote revoke; hassas API'de `session_id` + security epoch + current account state; telefon tek başına privileged factor değildir; signed object handle kısa ömürlü ve scope'lu. | Auth sign-in/refresh/sign-out, device/phone/MFA değişikliği, IP/device anomalisi, revoke epoch ve protected operation audit. | **DENY/HELD:** token kopyasıyla revoke sonrası hassas çağrı başarısız; refresh yeni token vermez; telefon kaybı device/session revoke üretir. Offline cihaz yalnız bounded, read-only güvenli paketi kullanır; high-consequence işlem yoktur. | Phase 4: revoke/epoch/step-up/no-offline invariant. Sonra: exact TTL, device binding/attestation, SMS/phone politikası ve local key storage. |
| **ID-02 — Silinmiş veya askıya alınmış kullanıcıda canlı oturum** | Supabase'te user silme veya ban, verilmiş JWT'yi hemen yok etmeyebilir; silinen kullanıcı `exp` süresince API'ye erişebilir. | Ayrılan/revoked operator, açık sekmeden approval/publish/role change sürdürebilir; historical actor attribution yanlışlıkla silinmemeli. | Sensitive route'ta `session_id` → `auth.sessions` kontrolü; kısa JWT; account-state/security epoch; ban/delete sonrası refresh ve new login deny; in-flight operation commit'te tekrar yetkilendirilir. | Account state change, stale-token request, session lookup miss, denied sensitive attempt, revoke impact graph. | **Kabul:** önceden alınmış JWT ile düşük-risk endpoint politikaya göre sınırlanabilir; approval/publish/export/role change anında `DENY/HELD`; refresh başarısız; geçmiş olaylar actor olarak korunur. | Phase 4: immediate sensitive revoke contract. Sonra: exact token/session timeout ve tüm endpoint sınıflandırması. |
| **ID-03 — Eski rol/claim açık sekmede** | Eski entitlement veya profile claim'i private alana erişim denemesi doğurur. | Eski `approver/publisher/admin` claim'i, gizli buton veya doğrudan API çağrısı ile self-approval/bypass denemesi. | `user_metadata` authorization'da kullanılmaz; `app_metadata`/custom claim yalnız hint; current grant/scope/policy version/session epoch server'da okunur; commit-time reauthorization; stale page read-only. | Token claim ile current grant farkı, policy version mismatch, stale epoch, direct route deny ve refresh event'i. | **Kabul:** açık sekmeden eski claim ile direct POST/RPC ve hidden-button bypass reddedilir; sayfa refresh/re-login ister; policy refresh olmadan tek bir material side effect oluşmaz. | Phase 4: claim freshness ve API boundary. Sonra: claim schema, policy cache/TTL ve exact push/refresh UX. |
| **ID-04 — E-posta hesabı ele geçirilmesi / magic link** | Ele geçirilmiş e-posta, magic link/OTP ve password reset ile account takeover; e-postaya bağlı tüm private veriler riskte. | Internal account veya privileged operator takeover; email-only link ile approval, publication, export veya role recovery tehlikeli. | Verified email; exact redirect allowlist + PKCE/deep-link binding; magic link/OTP yalnız düşük riskli giriş; identity/email change için fresh reauth + step-up; privileged yüzeyde phishing-resistant factor; security-change notification; `shouldCreateUser=false` türü açık hesap oluşturma politikası. | Auth audit (sign-in, reset, email change, identity link), yeni cihaz/IP, factor change, recovery ve unusual link replay. | **Kabul:** magic link replay ikinci kez çalışmaz; yanlış redirect kabul edilmez; e-posta ele geçirilse dahi privileged mutation için fresh strong factor/AAL2+ gerekir; hesap değişikliği pending/notification üretir. | Phase 4: magic-link privileged deny, reauth, allowlist, notification invariant. Sonra: SMTP/provider, link/OTP TTL, passkey/WebAuthn ve risk motoru. |
| **ID-05 — MFA cihazı kaybı veya MFA faktörünün kaldırılması** | Kullanıcı hesabına ulaşamaz veya kolay recovery ile saldırgan yeni factor ekler. | MFA'sız veya AAL1 oturumla approval/publish/role change; factor kaldırma sonrası stale `aal2` claim'e güvenme. | Privileged roles phishing-resistant MFA; iki bağımsız recovery seçeneği/backup-code kararı; lost-factor recovery dual-control; unenroll sonrası zorunlu refresh/session reauth; API/RLS'de `aal`/step-up enforcement; factor events audited. | Factor enroll/unenroll, AAL transition, recovery actor, new device, failed challenge; Supabase Auth audit + product audit korelasyonu. | **Kabul:** kayıp factor ile AAL1 session approval yapamaz; factor kaldırma sonrası refresh edilmemiş eski `aal2` claim'i kabul edilmez; recovery tüm eski privileged sessions/pending auth'ları revoke eder ve yeni factor'ı ayrı kanıtla bağlar. | Phase 4: AAL2/strong MFA, factor-loss hold ve dual-control invariant. Sonra: TOTP/passkey/SMS seçimi, backup code ve numeric policy. |
| **ID-06 — Kurtarma suistimali / help-desk sosyal mühendisliği** | Saldırgan support/recovery akışını normal login'den daha kolay bulur; account takeover. | Help-desk veya owner, kendini approver/publisher yapabilir; eski session açık kalır; audit attribution karışır. | Recovery normal privileged auth'tan zayıf olamaz; identity proof + independent reviewer/dual control; recovery increments security epoch; all sessions/refresh/recovery artifacts and pending high-consequence transactions revoked; break-glass time-bound, negative-only, no self-approval. | Recovery request, verifier, evidence, factor add/remove, epoch change, session revocation, notification ve break-glass use protected audit'e yazılır; burst/geo anomaly alert. | **Kabul:** recovery sırasında açık eski session hassas çağrıda reddedilir; tek support actor yeni privileged factor/role veremez; audit eski olayları silmez; kanıt/audit sink yoksa normal positive action `HELD`. | Phase 4: recovery state machine, dual control, epoch/revoke, no-owner-debug. Sonra: proofing vendor, support SLA, break-glass numeric duration. |
| **ID-07 — Anonymous/local kullanıcıyı yanlış profile bağlama veya yanlış hesap birleştirme** | Anonymous user `authenticated` rolü taşıdığı için yanlış RLS ile private veriye erişebilir; sign-out/device değişimi sonrası local history kaybolabilir veya başka hesaba taşınabilir. | Yanlış contributor/owner/tenant attribution; private evidence veya technical history başka profile geçirilir; conflict sessizce overwrite edilir. | `is_anonymous` ayrı restrictive policy; local-install principal ile canonical account ayrı; yalnız verified identity + explicit account confirmation; isim/e-posta/user metadata heuristiği yok; merge conflict ledger; stable record IDs ve no-silent-overwrite. | Anonymous→permanent link, identity link/unlink, reassign/merge, conflict count, orphaned records ve cross-profile reads auditlenir. | **Kabul:** iki account aynı görünen e-posta/display name ile merge edilemez; existing account'a link öncesi açık reauth/confirmation; her record source/target/karar ile korunur; conflict varsa `HELD`, iki taraf da kaybolmaz ve rollback/split yolu vardır. | Phase 4: anonymous isolation, explicit/verified merge, conflict hold. Sonra: merge UI, retention, data ownership/transfer ve split algorithm. |
| **ID-08 — Cihaz kaybı ve offline iptal/revoke gecikmesi** | Kayıp telefonda local private data, token, offline package veya pending operation kalabilir; remote revoke ağ gelene kadar uygulanmayabilir. | Internal Operations authoritative mutation offline değildir; ancak browser cache/cookie veya queued request tekrar oynatılabilir. | Local data minimization/encryption/key custody; remote device/session revoke; package expiry, base/generation/digest; no offline approval/publish/role/recall; pending operations idempotent ve online reauth/epoch check ile submit; remote wipe yalnız best-effort, authority değil. | Device reappearance, old package generation, replayed operation ID, epoch mismatch, failed submission/reconciliation ve cache access signals. | **Kabul:** cihaz offline iken revoke edilir; tekrar online olduğunda old package/operation `DENY/RECONCILING/HELD`, accepted operation duplicate olmaz; recalled/revoked content yeniden authority olmaz. Internal approval hiçbir zaman offline kuyruğa alınmaz. | Phase 4: bounded offline + anti-replay/anti-resurrection contract. Sonra: local encryption, OS keystore, package TTL/grace, remote wipe and exact offline policy. |
| **ID-09 — Yönetici hesabı kilitlenmesi veya son admin kaybı** | Login/support yolu kapanır; tüketici account recovery ve safety correction gecikir. | Role/policy revoke, emergency suspension veya incident response yapılamaz; sole admin compromise veya lockout sistemik olur. | En az iki bağımsız recovery path/persona; provider legal owner ile product admin ayrımı; break-glass yalnız süreli ve negative-only; admin otomatik approver/publisher/auditor değildir; owner-readable self-service status; normal product flow SQL/SSH istemez. | Failed-login/lockout, last-admin invariant, break-glass issuance/use/expiry, unhandled queue ve recovery health signal. | **Kabul:** tüm normal adminler unavailable iken high-consequence positive work `HELD`, mevcut güvenli consumer read devam eder; dual-control recovery yeni admin açar, geçmiş attribution değişmez; owner SQL/SSH istemez. | Phase 4: no-sole-admin, safe hold, dual recovery, no-owner-debug. Sonra: exact staffing, provider support/legal ownership, break-glass SLA. |
| **ID-10 — IdP/Auth kesintisi** | Yeni login/refresh ve account change yapılamaz; kullanıcı yalnızca son güvenli ve açıkça sınırlı içeriğe erişebilir. | Auth/step-up doğrulanamıyorsa approval/publish/export/role change yapılamaz; mevcut JWT'yi IdP liveness veya current role kanıtı sanma riski. | Auth health ve request state machine; API current session epoch/account state; consumer cached safe/read-only; Internal Operations online-only; independent negative suspension path; fallback, MFA'yı bypass etmez. Supabase changelog/Health Advisor Auth error-rate sinyali işletim gözlemidir, authority değildir. | Auth/IdP error rate, refresh failures, health signal, operation `OUTCOME_UNKNOWN/HELD`, incident/audit correlation. | **Kabul:** IdP down iken yeni login ve sensitive step-up reddedilir; cached consumer safe read çalışabilir; Internal positive mutation `HELD`; restore sonrası pending işlemler otomatik başarılı sayılmaz, reconcile gerekir. | Phase 4: outage state, fail-closed high-consequence, read-only safe mode. Sonra: IdP composition, fallback credential/SSO, RTO/RPO ve provider incident contract. |
| **ID-11 — Cross-tenant / BOLA / IDOR** | Bir tüketici başka kullanıcının motorcycle, history, private media veya export nesnesini ID değiştirerek okuyabilir/yazabilir. | Operator doğru role sahip olsa bile yanlış organization/workspace/motorcycle/domain scope'a erişebilir; service key/RPC yolu tüm tenant'ları açabilir. | Client tenant/object ID authority değildir; API target membership + resource scope + classification kontrolü; grants + RLS; `USING` ve `WITH CHECK`; views `security_invoker=true` veya private schema; `service_role` yalnız dar server worker; direct Data API high-consequence için yasak. | Cross-tenant denied probes, abnormal ID enumeration, policy mismatch, export scope, object path mismatch ve security audit. | **Kabul:** A tenant token ile B object id, nested relation, direct REST/RPC, signed URL ve export reddedilir; update ile `user_id/tenant_id` yeniden atanamaz; no row/permission leak; deny event auditlenir. | Phase 4: tenant/resource authorization tuple + negative tests. Sonra: exact tenant lattice, row/view/function schema ve enumeration UX. |
| **ID-12 — Identity merge/split** | İki account/profile'nin history, notes, media, notifications ve consent'i karışabilir; merge sonrası geri ayırma zorlaşır. | Approval author, reviewer, competence, tenant membership ve delegation attribution'ı yanlış kişiye yazılır; incompatible roles birleşebilir. | Auth identity, stable Kavriva principal ve domain ownership ayrı; merge freeze; verified consent + reauth + independent review; immutable source→target mapping/event; no silent FK rewrite; split restores source IDs/attribution and re-evaluates grants; high-consequence objects merge edilmeden `HELD`. | Merge/split event, source/target IDs, reason, approver, conflicts, reassignment count, orphan/dedup report, grant/policy recalculation. | **Kabul:** same email veya matching profile merge tek başına yetmez; collision/tenant/role conflict `HELD`; merge sonrası audit eski actor IDs ile okunur; split sonrası geçmiş event ve current ownership tutarlı kalır. | Phase 4: stable identity/merge/split invariants and freeze. Sonra: exact domain merge grammar, legal retention/consent, UI and reversible job mechanics. |
| **ID-13 — Audit attribution bozulması** | Kullanıcı yaptığı değişikliği inkâr edemez hale gelmeli; support, private exposure ve merge nedeni açıklanabilmeli. | `actor=admin` veya `actor=AI` gibi geniş etiketler high-consequence kararın gerçek insanını gizler; audit silinirse release/recall güvenilmez. | Event minimumu: actor/principal, effective role/scope, session/assurance, auth method, device/client, delegation/grant, policy version, operation ID, resource/version, old/new meaning, server time/order, result/deny/fail/unknown; AI/service identity ayrı; append-only/tamper-evident protected custody. | Missing sequence, gap/fork/replay, log sink divergence, actor/grant mismatch, unusual export, audit read/redaction ve restore reconciliation. | **Kabul:** aynı insan iki role, delegated human ve AI worker ile işlem yaptığında zincir ayrışır; normal + fallback audit yoksa high-consequence `HELD`; başarılı DB response audit kanıtı yoksa success diye raporlanmaz; audit export source evidence'ı değiştiremez. | Phase 4: event contract, protected floor, attribution and hold semantics. Sonra: SIEM/log drain, retention/redaction/legal hold, integrity primitive and exact storage. |
| **ID-14 — AI görevlerinde least privilege ihlali** | AI, private consumer data veya güvenlik/teknik iddiayı gereğinden geniş context ile görür; kullanıcı AI önerisini authority sanabilir. | AI task broad DB/service key/console owner erişimi alırsa cross-tenant okuma, role escalation, approval/publish, audit mutation veya secret exfiltration yapabilir. | Task-scoped kısa ömürlü capability/identity; minimum context ve classification; allowlisted route/action/object; read/write ayrı; `service_role`, project owner token, SQL/SSH ve geniş Storage handle AI prompt/context'ine verilmez; approval/publish/role/recovery yalnız insan/controlled workflow; sandbox, expiry, idempotency. | Tool-call/capability use, context classification, data-volume, denied attempt, secret scanner, AI/service actor, operation ledger ve human decision audit. | **Kabul:** sıradan görev AI'sı başka tenant okuma, export, service key, SQL/SSH veya approval/publish denediğinde `DENY` ve audit; izinli görev yalnız fixture kapsamındaki read/write'ı yapar; timeout/partial sonucu `UNKNOWN/RECONCILING`, otomatik retry side effect üretmez. | Phase 4: least-privilege task contract, no-secret/no-console, human high-consequence gate. Sonra: credential broker, model/provider/data residency, sandbox and per-task quotas. |
| **ID-15 — Teknik olmayan owner için SSH/SQL/debug gerektirmeyen kurtarma** | Kullanıcı hesabı veya güvenli correction yolu kapalı kalır; tüketici güvenli kullanımı ve data export gecikir. | Provider/Auth/worker failure sırasında owner'dan SQL, SSH, dashboard superuser veya log teşhisi istenirse güvenlik ve süreklilik kırılır; yanlış manuel repair yeni yetki bypass'ı yaratır. | Owner-readable state machine (`AUTH_HELD`, `RECOVERY_REQUIRED`, `OUTCOME_UNKNOWN`, `RESTORE_QUARANTINE`); browser'dan bounded revoke/recovery/request-support; dual-control; AI yalnız scoped diagnostics ve evidence pack hazırlayabilir, repair authority'si yoktur; cross-plane backup/export/restore runbook; safe read/negative suspension path. | Health/error signal, operation ledger, provider/account/billing/IdP state, protected incident evidence, next-action and escalation owner. | **Kabul:** simulated key leak, IdP outage, last-admin lockout ve response-loss'ta owner yalnız anlaşılır recovery action/dual approval/support escalation kullanır; sistem SSH/SQL istemez; safe positive effect kapanır; blocked state ve next action görünür. | Phase 4: no-owner-debug invariant, readable failure states and safe hold. Sonra: exact control-plane UI, support/legal process, restore drill, RTO/RPO and vendor SLA. |

## 6. Ortak kabul kriterleri

Her kimlik/erişim senaryosu aşağıdaki beş sonucu birlikte üretmeden `PASS` sayılmaz:

1. **Authoritative karar:** İstek current actor, session, grant, scope, tenant, classification, workflow/resource
   version, independence ve security epoch ile server-side `ALLOW`, `DENY` veya `HELD` olur.
2. **Yan etki sınırı:** `DENY`, `HELD`, `OUTCOME_UNKNOWN` veya stale/offline durumda approval, publication, role,
   audit deletion, private export veya irreversible merge oluşmaz.
3. **Attributable evidence:** actor/effective grant/session/operation/object version/policy/result zinciri protected
   audit'e yazılır; kimlik revoke veya merge geçmiş attribution'ı silmez.
4. **Kullanıcıya dürüst durum:** tüketici güvenli read/safe-stop/recovery; Internal Operations read-only/hold/negative
   action; belirsizlik başarı gibi gösterilmez.
5. **İleri recovery:** refresh/re-auth, reconcile, dual-control recovery, split/rollback, export veya support path
   tanımlıdır; retry aynı side effect'i çoğaltmaz.

`PASS` için yalnızca Supabase Auth/RLS hata kodu, gizli buton veya başarılı upload yeterli değildir. Gerçek
uygulama ve restore/device/IdP testleri Phase 5+ kanıtı olarak ayrıca yürütülmelidir.

## 7. Phase 4'te bağlanması gereken kararlar

Bu araştırmanın Phase 4 çalışma yönü olarak bağladığı hükümler:

- Supabase Auth, authentication/session primitive'idir; Kavriva approval, publication, recall, competence,
  tenant veya protected audit authority'si değildir.
- Tüm high-consequence mutation, export, role/policy, identity merge ve privileged recovery Kavriva server/API
  boundary'sinde commit-time yeniden yetkilendirilir.
- `user_metadata`, client-supplied tenant/scope ve UI visibility yetki kaynağı değildir; `service_role`/secret
  yalnız server-side dar görev context'inde kalır.
- Sensitive route'lar current `auth.sessions`/session epoch/account state ve gerektiğinde fresh step-up kontrolü
  olmadan başarılı sayılmaz; deleted/banned/revoked/stale claim etkisi açıkça test edilir.
- Internal Operations approval/publish/role/recovery offline kuyruğa alınmaz; consumer offline yalnız versioned,
  digest-bound, task-scoped ve safe-stop/recovery closure içeren paket/işlem sınırında kalır.
- Privileged authentication, recovery ve MFA kaybı phishing-resistant/dual-control yönünde tutulur; exact factor,
  TTL ve backup-code seçimi açık bırakılır.
- Anonymous/local→permanent bağlama, merge/split ve tenant transferi explicit verified workflow + conflict hold +
  non-destructive attribution ile yürür; e-posta veya görünen profile eşleşmesi otomatik karar değildir.
- Product audit, Auth audit'ten ayrı protected evidence olarak tutulur; minimum kanıt yoksa high-consequence action
  `HELD` olur.
- AI görevleri task-scoped, minimum context, kısa ömürlü ve ayrı service identity ile çalışır; AI approval/recovery
  authority'si veya provider owner/SQL/SSH erişimi taşımaz.
- Owner recovery, teknik müdahale olmadan anlaşılır state/next action ve dual-control/support path sunar.

## 8. Phase 5 veya daha sonraya bırakılabilecek kararlar

Güvenlik invariant'ları korunmak şartıyla aşağıdaki ayrıntılar bu araştırmada seçilmemiştir:

- Supabase Auth'ın tek başına mı, harici IdP/SSO ile mi kullanılacağı; OAuth/SAML sağlayıcı ve e-posta/SMTP seçimi.
- Exact access JWT/refresh/session inactivity/absolute TTL; concurrent session/device limiti; revocation propagation
  SLA; signed URL/object handle TTL.
- Passkey/WebAuthn, TOTP, SMS, recovery code ve device binding/attestation kombinasyonu; AAL2/AAL3 hedefinin hangi
  capability'lere uygulanacağı.
- Hesap proofing, help-desk, dual-control/break-glass personel modeli, legal owner/support SLA ve exact recovery
  evidence.
- Tenant/workspace/resource scope şeması; RLS view/function policy ayrıntısı; authorization policy engine ve cache
  invalidation yöntemi.
- Anonymous/local principal veri retention'ı; domain bazlı merge/split grammar'ı; consent, transfer ve legal delete
  kuralları.
- Local encryption/keystore, remote wipe, offline package grace/expiry ve background revoke davranışı.
- Protected audit custody, log drain/SIEM, retention/redaction/legal hold, integrity/checkpoint yöntemi ve exact
  alert eşikleri.
- AI credential broker, model/provider/data-boundary, sandbox, quota ve human-review UX'i.
- IdP/provider outage fallback, restore/exit cross-plane drill, RTO/RPO ve no-owner-debug support runbook ayrıntıları.

Bu ayrıntıların hiçbiri, Phase 4'te tanımlanan `DENY/HELD`, no-offline-privilege, no-silent-merge,
anti-resurrection, protected-attribution veya no-owner-debug invariants'ını gevşetmek için kullanılamaz.

## 9. Genel sentez

En tehlikeli yanlış varsayım, "Auth başarılıysa kullanıcı hâlâ yetkilidir" önermesidir. Supabase'in stateless JWT,
refresh, role claim, anonymous role, MFA assurance ve signed URL davranışları; kimlik olayının veri-plane ve
workflow-plane etkisinden ayrı zamanlarda ilerleyebileceğini gösterir. Kavriva'nın güvenli çalışma yönü şu zincirdir:

`authentication claim → current session/account state → scoped contextual authorization → fresh step-up →
version/generation/independence check → protected audit → bounded effect`

Zincirin herhangi bir parçası stale, unavailable, conflicting veya unattributable ise tüketici için güvenli read/
safe-stop; Internal Operations için `DENY`/`HELD`/negative suspension uygulanır. Eski token, açık sekme, IdP
kesintisi, offline cihaz veya AI retry hiçbir zaman bu zinciri sessizce kısaltamaz.

## 10. Araştırma kaynakları (resmi/birincil)

Okuma tarihi: `2026-09-18`.

- [S1 — Supabase User sessions](https://supabase.com/docs/guides/auth/sessions): session/JWT/refresh/session_id,
  timeout, refresh-token reuse ve sensitive session validation.
- [S2 — Supabase User Management](https://supabase.com/docs/guides/auth/managing-user-data): delete/ban sonrası
  canlı JWT sınırı ve `auth.sessions` kontrolü.
- [S3 — Supabase Multi-Factor Authentication](https://supabase.com/docs/guides/auth/auth-mfa): `aal1`/`aal2`,
  factor lifecycle ve API/RLS enforcement.
- [S4 — Supabase Anonymous Sign-Ins](https://supabase.com/docs/guides/auth/auth-anonymous): anonymous vs `anon`,
  `authenticated` rolü, `is_anonymous`, linking/conflict ve abuse controls.
- [S5 — Supabase Identity Linking](https://supabase.com/docs/guides/auth/auth-identity-linking): automatic/manual
  linking, verified e-posta ve SSO sınırları.
- [S6 — Supabase Passwordless email sign-in](https://supabase.com/docs/guides/auth/auth-email-passwordless):
  one-time Magic Link, OTP ve expiry varsayımları.
- [S7 — Supabase Row Level Security](https://supabase.com/docs/guides/database/postgres/row-level-security):
  `user_metadata`/`app_metadata`, claim freshness, RLS ve `service_role` bypass.
- [S8 — Supabase Custom Claims & RBAC](https://supabase.com/docs/guides/api/custom-claims-and-role-based-access-control-rbac):
  token claim üretimi ve policy/RLS bağlamı.
- [S9 — Supabase Securing your API](https://supabase.com/docs/guides/api/securing-your-api): grants + RLS,
  exposed objects ve function/role sınırları.
- [S10 — Supabase Serving assets from Storage](https://supabase.com/docs/guides/storage/serving/downloads):
  signed URL anahtarı, expiry ve Auth key rotation'dan bağımsızlık.
- [S11 — Supabase Auth Audit Logs](https://supabase.com/docs/guides/auth/audit-logs): Auth event kapsamı ve
  external/Postgres storage seçenekleri.
- [S12 — Supabase Database Backups](https://supabase.com/docs/guides/platform/backups): DB backup'ın Storage
  object bytes'ını içermemesi ve PITR sınırı.
- [S13 — Supabase Changelog](https://supabase.com/changelog): 2026 Data API exposure, Auth/health/logging,
  backup ve breaking-change izleme kaynağı.
- [S14 — NIST SP 800-63B-4](https://pages.nist.gov/800-63-4/sp800-63b.html): güncel AAL, phishing/replay
  resistance, reauthentication ve authenticator loss/theft lifecycle rehberi.
- [S15 — CISA Implementing Phishing-Resistant MFA](https://www.cisa.gov/sites/default/files/2023-01/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf):
  privileged/high-value erişimler için phishing-resistant MFA yönlendirmesi.

[S1]: https://supabase.com/docs/guides/auth/sessions
[S2]: https://supabase.com/docs/guides/auth/managing-user-data
[S3]: https://supabase.com/docs/guides/auth/auth-mfa
[S4]: https://supabase.com/docs/guides/auth/auth-anonymous
[S5]: https://supabase.com/docs/guides/auth/auth-identity-linking
[S6]: https://supabase.com/docs/guides/auth/auth-email-passwordless
[S7]: https://supabase.com/docs/guides/database/postgres/row-level-security
[S8]: https://supabase.com/docs/guides/api/custom-claims-and-role-based-access-control-rbac
[S9]: https://supabase.com/docs/guides/api/securing-your-api
[S10]: https://supabase.com/docs/guides/storage/serving/downloads
[S11]: https://supabase.com/docs/guides/auth/audit-logs
[S12]: https://supabase.com/docs/guides/platform/backups
[S13]: https://supabase.com/changelog
[S14]: https://pages.nist.gov/800-63-4/sp800-63b.html
[S15]: https://www.cisa.gov/sites/default/files/2023-01/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf
