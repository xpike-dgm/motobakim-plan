# DEBATE-012 — Bağımsız Adversarial Review B: Security / Operability / TCO / Exit

**Durum:** `HELD — NO WINNER / REACT-NEXT = ANGULAR / HOSTING MODES HELD / ADR NOT READY`  
**Tarih:** 2026-09-19 (Europe/Istanbul)  
**Kapsam:** `PHASE-4 / NO-CODE / NO ACCOUNT / NO PURCHASE / GATE 4 -> 5 CLOSED`  
**Reviewer:** Bağımsız Reviewer B — Security, Session, Operability, Owner TCO ve Clean-room Exit  
**Aday A:** React + Next.js  
**Aday B:** Angular  

Bu review yalnızca belge/research düzeyindedir. Kod, prototip, executable spike, hesap, provider hesabı, plan,
abonelik, ödeme, migration, deployment, production proof, ADR veya Gate 4 → 5 geçişi oluşturmaz. React/Next ve
Angular aynı kanıt sınırında tutulur. Bir hosting şeklinin yönetilen olması güvenliği, geri dönüşü veya owner
operability'sini otomatik olarak kanıtlamaz.

## 0. Kısa hüküm

Yönetici önerisinin korunması gereken çekirdeği doğrudur:

- browser/framework server/provider console canonical product authority değildir;
- yüksek sonuçlu işlemler her commit'te Kavriva API tarafından yeniden yetkilendirilir;
- operation identity, immutable payload fingerprint, expected version/generation ve `OUTCOME_UNKNOWN` korunur;
- protected audit, quarantine, long-job, negative floor, restore ve no-owner-debug ürün sözleşmesinin parçasıdır;
- no-code ve provider/plan satın almama sınırı korunmuştur.

Buna rağmen yönetici önerisi, React/Next'i AI aşinalığı ve ekosistem genişliği nedeniyle koşullu lider diye öne
çıkarırken Angular için aynı güvenlik/operability kanıtını sunmuyor. Bu, ölçülmüş bir avantaj değil, kanıtsız bir
önceliklendirmedir. Ayrıca öneri aşağıdaki hard gate'lerin yalnız isimlerini anıyor; framework/hosting birleşimleri
üzerinde gerçek bir adversarial kanıt, owner/support/account zinciri, normalized BOM veya clean-room kabulü yok.

| Yüzey | Belgesel hüküm | Bugünkü sonuç |
|---|---|---|
| React + Next.js | Mekanizma kanıtı var; Kavriva API authority, stale-state, browser security, upload, deploy, exit ve owner operasyonu kanıtlanmamış | `HELD` |
| Angular | Mekanizma kanıtı var; Angular LTS/XSRF/Aria/CLI, Kavriva authority, stale-state, upload, deploy, exit ve owner operasyonu kanıtlamıyor | `HELD` |
| React/Next ↔ Angular eşitliği | Aynı `WEB-AC-001..022` ve `WEB-01..11` evidence pack'i kapanmadan liderlik hükmü yok | `NO WINNER` |
| Hosting/render modları | Her mod farklı session, cache, failure-domain, support, cost ve exit yükü getiriyor | `HELD` |

Bu review'de **9 CRITICAL, 12 MAJOR ve 5 MINOR** bulgu vardır. Belgesel aşamada hiçbir aile topyekûn `REJECT`
değildir; fakat aşağıdaki bir hard-fail gerçek kanıtta görülürse ilgili family/hosting/capability
`REJECT-IF-UNMITIGATED` olur. Diğer aday otomatik kazanan sayılmaz.

### Hosting modları için ayrı hüküm

Araştırmadaki ortak taxonomy kullanılmıştır; manager proposal'daki H1/H2/H3 adlarıyla karıştırılmamalıdır:

| Mod | Operasyonel saldırı yüzeyi | Hüküm |
|---|---|---|
| `H1 Managed framework-native / edge` | Provider build/runtime/cache/edge, account/quota, region, rollback ve adapter semantiği | `HELD`; provider rollback'i data/schema/floor rollback'i değildir |
| `H2 Managed static artifact / CDN` | Authenticated state'in browser → API yolu, CORS/CSRF, headers, cache purge, upload ve API partial outage | `HELD`; static artifact authority değildir |
| `H3 Portable static / CDN` | DNS/TLS, headers, route fallback, purge, monitoring, certificate ve incident işi owner/otomasyona döner | `HELD`; owner repair gerekirse `REJECT-IF-UNMITIGATED` |
| `H4 Portable Node/container` | Reverse proxy, patch/CVE, secret, drain, logs, capacity, backup/restore, DNS/TLS ve failover | `HELD`; SSH/SQL/raw-log owner yolu varsa `REJECT-IF-UNMITIGATED` |
| `H5 Split static frontend + managed API` | İki failure domain'i; cross-origin cookie/CORS/CSRF, correlation, compatibility ve partial outage | `HELD`; "daha ucuz/güvenli" varsayımı yok |

## 1. Okunan bağlayıcı kanıt ve yöntem

Tamamı okunan girdiler:

- `00_CONTROL/AI_START_HERE.md`
- `00_CONTROL/CURRENT_STATE.md`
- `00_CONTROL/SOURCE_OF_TRUTH.md`
- `00_CONTROL/DECISION_LOG.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_PRIMARY_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_FAILURE_TCO_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_MANAGER_PROPOSAL.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__JUDGE_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__JUDGE_SYNTHESIS.md`

Evidence dili:

- `CONFIRMED`: resmi veya repository belgesinde mekanizma/kural açıkça vardır; bu tek başına Kavriva production
  güvenliği değildir.
- `INFERRED`: mekanizma ile ürün sınırından çıkarılan sınırlı risk/olasılık; gerçek fixture gerektirir.
- `OPEN`: bu aşamada bilinçli olarak çözülmemiştir; varsayılanla doldurulamaz.
- `HELD`: gereksinimle açıkça çelişmeyen fakat olumlu evidence kapanmadığı için açılmayan capability.
- `REJECT-IF-UNMITIGATED`: authority, safety, privacy, continuity, owner operability, spend veya exit sınırını
  eşdeğer kanıt olmadan karşılamayan kullanım.

Saldırı merceği, şu varsayımları kabul etmez: gizli düğme yetkidir, route guard güvenliktir, XSRF interceptor tek
başına CSRF kapatır, CSP tek başına XSS kapatır, HTTP 2xx effect'tir, green host dashboard'u recovery kanıtıdır,
static artifact taşınabilirliği clean-room exit'tir, provider log'u protected product audit'tir veya AI/owner
provider hesabını ve bağımsız recovery otoritesini temsil eder.

## 2. Yönetici önerisinde korunması gerekenler

1. Browser, React/Next Server Action, Angular interceptor/guard, SSR shell ve provider console canonical DB/object,
   publication, protected audit veya recovery authority değildir.
2. Her hassas effect için current actor/session/issuer/epoch, action/resource/tenant/scope/classification,
   grant/competence/independence/policy, object/version/generation, negative floors, operation fingerprint ve audit
   readiness commit anında tekrar kontrol edilmelidir.
3. Aynı operation ID + aynı semantic payload mevcut sonucu read-only döndürür; farklı payload/scope/actor
   `CONFLICT/HELD`; response kaybı `OUTCOME_UNKNOWN` olur.
4. Protected audit receipt olmadan high-consequence positive effect `AUDIT_HELD`; audit intent, provider log'u veya
   browser telemetry'si receipt yerine geçmez.
5. Upload/URL/preview/derivative quarantine-first; long job için durable queue/worker; restore/rollback için
   monotonic negative floor ve anti-resurrection korunmalıdır.
6. `ACCEPTED`, `QUEUED/SUBMITTED`, `DENIED`, `HELD`, `OUTCOME_UNKNOWN`, `PARTIAL/RECONCILING`, `AUDIT_HELD`,
   `BILLING_HELD`, `ACCOUNT_HELD`, `DEPLOYMENT_HELD`, `OBJECT_QUARANTINE`, `RESTORE_QUARANTINE`, `EXPORT_PARTIAL`,
   `SERVICE_UNAVAILABLE` ve `RECOVERY_REQUIRED` yalnız renk/toast/HTTP sonucu değildir; retained data, allowed/blocked
   effects, resolver, cost stop, audit ve exit etkisini de taşımalıdır.

## 3. CRITICAL bulgular

### C-01 — Direct API/provider bypass için yalnız niyet var; negative inventory ve proof yok

**Bulgu.** Manager proposal browser'ın generic DB/Storage authority taşımayacağını söylüyor, ancak React/Next Route
Handler/Server Action, Angular `HttpClient`/interceptor/route guard, static preview URL'si, provider Data API/RPC/view/
function, direct Storage/signed URL ve provider console yüzeylerinin tam allow/deny/hold envanterini sunmuyor.
"Button gizli", "route kapalı" veya "RLS var" demek `IWEB-API-001`, `WEB-AC-006` ve `F04` için kanıt değildir.

**Saldırı/arıza yolu.** Bir operator veya saldırgan browser devtools/curl ile client-supplied tenant/resource/version,
Next Server Action, Angular endpoint veya signed URL'yi çağırır; UI'de görünmeyen publish/recall/export/role değişikliği
API'de farklı davranır. Operation ID başka tenant'ın status/payload/audit özetini açarsa BOLA/IDOR ve disclosure oluşur.
Provider console veya generic RPC etkiliyse Kavriva approval/publication/audit/floor sınırı delinmiş olur.

**Zorunlu düzeltme/evidence.** React/Next ve Angular için aynı browser→frontend runtime→Kavriva API→DB/object/provider
console matrisi hazırlanmalı; her yol `ALLOW / DENY / HELD / OUTCOME_UNKNOWN` beklenen sonucuyla negatif test edilmelidir.
Actor/tenant/scope API'den türetilmeli, client ID yalnız input sayılmalı; status lookup disclosure-safe ve cross-tenant
deny olmalıdır. RLS/Storage defense-in-depth olarak test edilir, sole authority sayılmaz.

**Hüküm.** Bypass gerçek kanıtta kapanmazsa ilgili capability `REJECT-IF-UNMITIGATED`; bugün her iki aile ve her mod
`HELD`. React/Next veya Angular lehine fark yoktur.

### C-02 — Session, CSRF/XSRF, XSS ve CSP sözleşmesi hosting şekilleri arasında bağlanmamış

**Bulgu.** Proposal static/client-rendered ve server-assisted shell'i hipotez olarak anıyor; fakat cookie/token storage,
session rotation/revoke, security epoch, origin/redirect/PKCE, resource-bound step-up, CSRF contract, CSP nonce/hash,
Trusted Types, untrusted HTML/SVG/markdown ve secret redaction için uygulanabilir bir boundary seçmiyor. Next Server
Action origin/host check'i yalnız bir CSRF katmanıdır. Angular `HttpClient` XSRF interceptor'ı client half'tır;
backend doğrulaması olmadan güvenlik sağlamaz. React `dangerouslySetInnerHTML` veya Angular bypass/sanitizer escape
hatları internal source/evidence/preview içeriğinde ayrı threat model ister.

**Saldırı/arıza yolu.** H2/H5 cross-origin cookie veya bearer token yolu CORS/CSRF/Origin yanlışlığıyla publish/recall
command'i tetikler. XSS, trusted preview, dynamic HTML veya SVG ile operator session'ını/step-up'ı kullanır. CSP report-
only'de kalır veya nonce/header proxy'de kaybolur; public env, SSR payload, source map veya error response secret/PII
taşır. Login olmuş olmak transaction-bound approval yetkisi değildir.

**Zorunlu düzeltme/evidence.** Her iki aile/mod için secure origin, `Secure`/`HttpOnly`/`SameSite` seçimi, server-side
CSRF token + Origin/Referer policy, CORS allowlist, PKCE/redirect allowlist, logout-all/rotation/epoch ve fresh
phishing-resistant transaction-bound step-up açıkça bağlanmalıdır. Untrusted text context-appropriate encode/sanitize
edilmeli; HTML/SVG/URL/preview izolasyonu, CSP report-only→enforce, nonce/Trusted Types kararı ve third-party script
allowlist'i test edilmelidir. `WEB-AC-010`, F02/F03 olumlu/olumsuz browser testleri olmadan positive privileged path
açılmaz.

**Hüküm.** Interceptor, Server Action, guard veya CSP tek savunma olarak kalırsa ilgili path `REJECT-IF-UNMITIGATED`;
şimdilik React/Next ve Angular eşit `HELD`.

### C-03 — Stale tab, security epoch ve lost-outcome protokolü tam kapanmamış

**Bulgu.** Proposal `OUTCOME_UNKNOWN`, status lookup ve stale role/epoch yönünü kabul ediyor; ancak mutating view'da
server-issued policy/access version, security epoch, object/version/generation, release/schema/config/client capability
ve current negative floors'ın birlikte taşınması; response loss sonrası disclosure-safe same-ID lookup; different
fingerprint conflict; browser close/reload/back/second-tab davranışı; draft/review evidence preservation ayrıntılanmış
değil.

**Saldırı/arıza yolu.** Rol revoke veya recall sonrası eski sekme publish/approve/recall gönderir; kullanıcı back-button
ile eski review packet'ini tekrar submit eder; response timeout'tan sonra UI başarısız sanıp yeni payload ile ikinci
operation üretir. Status endpoint mevcut operation'ın başka tenant'a ait olup olmadığını yeterince ayırmaz. Security
epoch yalnız JWT'yi düşürürse pending/in-flight operation, worker lease, handle, browser cache veya open tab hâlâ
positive effect üretebilir.

**Zorunlu düzeltme/evidence.** Commit'te tam authorization tuple ve negative floors tekrar okunmalı. Stale tab/role/
object/release/epoch `DENIED`, `HELD` veya `DEPLOYMENT_HELD` olmalı; blind "continue anyway" olmamalı. Draft/review
evidence kaybolmadan refresh/rebase/resolver gösterilmeli. Same operation + same fingerprint read-only status; changed
payload/scope/actor `CONFLICT/HELD`; cross-tenant lookup `DENY`; canonical status effect + protected audit receipt
ile çözülmelidir. Revoke tab, cache/SW, object handle, export ve local package sınırlarına uzanmalıdır.

**Hüküm.** Eski tab veya lost response positive effect üretebiliyorsa hard fail ve `REJECT-IF-UNMITIGATED`; bugün iki
aday da `HELD`.

### C-04 — Cache/service-worker/old-artifact güvenliği yalnız "varsayılan offline authority yok" cümlesiyle kapanmıyor

**Bulgu.** Proposal service worker'ı privileged mutation için kullanmamayı öneriyor; ancak authenticated HTML/API/status,
Next RSC/prefetch/ISR/cache, Angular TransferState/service worker, CDN `Cache-Control`/`Vary`/ETag, old-tab drain,
update/kill-switch, negative-floor ve recall propagation sözleşmesi yok. "No-store" ifadesi hangi response ve hangi
failure state için geçerli olduğunu söylemiyor.

**Saldırı/arıza yolu.** CDN veya browser/SW eski role/epoch/claim/review packet/operation status'ı başka scope'a verir;
old bundle yeni API/schema ile destructive command gönderir; old SW recalled content'i tekrar gösterir veya cached
positive status'ı accepted sanır. Provider rollback yalnız web artifact'ını döndürür, daha yeni recall/revoke/delete/
accepted-operation floor'ını silerse anti-resurrection bozulur.

**Zorunlu düzeltme/evidence.** Hashed immutable assets ile user/API/operation data ayrılmalı; authenticated HTML/data,
operation status ve privileged mutation response'ları explicit private/no-store veya actor/scope/epoch-bound cache ile
kanıtlanmalıdır. SW kullanılacaksa versioned cache, install/activate/update, old-tab lifetime, kill-switch, revoked
session/negative floor and API N/N-1 compatibility testleri olmalı; privileged mutation ve sensitive status SW cache'ine
girmemelidir. Release graph `release_id + artifact digest + API/schema/config/message/content/object/package generation
+ security epoch/revocation/negative floor` taşımalıdır.

**Hüküm.** Stale cache/SW old negative truth'i temizleyebiliyorsa hard fail; aksi halde evidence kapanana kadar iki aile
ve beş mod `HELD`.

### C-05 — File/URL/preview quarantine ve object custody kritik ayrıntıları eksik

**Bulgu.** Proposal private quarantine'ı doğru yönde anıyor, fakat file/URL intake'in SSRF/private-network/redirect/
scheme/host kontrolü, archive nesting/decompression/traversal, malformed/polyglot media, resource/time/size limits,
duplicate/orphan cleanup, digest/manifest, classification/lineage, preview isolation, derivative inheritance, scoped
short-lived handle, object backup/restore ve interrupted large upload state'lerini bağlamıyor.

**Saldırı/arıza yolu.** Kötü niyetli archive path traversal/decompression bomb veya URL SSRF ile private network'e erişir;
HTML/SVG/office preview operator session'ında XSS çalıştırır; client MIME/extension güvenilir sanılır; incomplete upload
public/signed handle alır; derivative original classification'ı düşürür; revoked handle cache/SW'de çalışır. Scan/render/
AI/OCR tamamlandı diye technical correctness veya official evidence sanılır.

**Zorunlu düzeltme/evidence.** Original bytes/reference, observed/declared type, size, digest, source/retrieval context,
classification, retention/disclosure ve lineage quarantine manifest'ine alınmalı. URL fetch outbound allowlist,
redirect/private-network/timeout/resource bound ile çalışmalı. Preview ayrı process/domain/credential boundary'de
untrusted kalmalı; derivative en restrictive classification'ı taşımalı. Scan/digest/manifest/approval tamamlanmadan
active/public handle yok; handle exact audience/scope/object/version/epoch ve kısa ömürlü olmalı. Large upload/scan/render/
OCR/export queue/worker contract'ına bağlanmalı; orphan/partial/restore state owner-readable olmalı.

**Hüküm.** Quarantine bypass, public direct write veya revoked/stale handle kullanımı gerçek evidence'ta görülürse
`REJECT-IF-UNMITIGATED`; bugün React/Next ve Angular eşit `HELD`.

### C-06 — Immutable artifact, supply-chain ve deploy compatibility proof'u yok

**Bulgu.** Proposal LTS, lockfile ve update/rollback fikrini anıyor; ancak exact dependency closure, transitive SBOM,
provenance/signature, reproducible install/build, trusted builder/registry/verifier, postinstall/script review, source
and workflow inputs, artifact digest, environment manifest ve release approval chain'i göstermiyor. React/Next'te React
minor + Next App Router/RSC/canary/bundler closure'ı; Angular'da Angular/CLI/compiler/Node/TypeScript/RxJS/CDK/grid/auth
closure'ı eşit şekilde kilitlenmelidir.

**Saldırı/arıza yolu.** Compromised package/build plugin, mutable tag veya managed build-image drift'i operator bundle'a
gizli exfiltration/authority ekler. Provider rollback old web artifact'ını döndürürken API/schema/migration/config/
queue-message/object/package/security epoch daha yenidir; old artifact recall/revoke/delete/accepted floor'ını aşar.
Health probe yeşil olsa bile release meaning graph uyumsuzdur.

**Zorunlu düzeltme/evidence.** Exact source/lockfile/toolchain/build inputs, SBOM/license/advisory review, provenance/
attestation/signature, independent verifier/trust-root matrix ve immutable artifact promotion gereklidir. Deploy
compatibility `web release + API contract/schema/migration/config + queue/worker message + content/object/package
manifest + security epoch/revocation/negative floor` ile kontrol edilmeli; old revision drain, secret rotation,
forward recovery ve API N/N-1 testleri yapılmalıdır. Mutable rebuild, provider-console-only promote veya DB rollback
varsayımı yoktur.

**Hüküm.** Artifact provenance/verification veya cross-plane compatibility yoksa release capability `HELD`; mutable
rebuild/negative-floor resurrection hard fail ve `REJECT-IF-UNMITIGATED`. Frameworkler eşittir.

### C-07 — No-owner-debug, support/account ve bağımsız recovery zinciri tanımlı değil

**Bulgu.** Proposal teknik olmayan owner'ın SQL/SSH/debug yapmaması gerektiğini söylüyor; fakat provider account/legal
owner, billing/payment, domain/DNS/TLS, support ticket, incident responder, queue/object/audit/floor custodian, last-admin,
privileged recovery ve emergency-negative bağımsız insan/kurum, escalation target/SLA ve credential boundary açık değil.
Managed hosting bu sorumlulukları kaldırmaz; portable hosting bunları owner'a itebilir.

**Saldırı/arıza yolu.** Host/account lock, quota/billing hold, DNS/TLS expiry, API/DB/object/audit outage veya queue
poison olayında owner raw logs, browser devtools, SQL, SSH, queue surgery, cache purge, secret rotation veya provider
console recovery'ye zorlanır. Tek owner ve AI, bağımsız approval/recovery/negative actor'ı taklit edemez. Positive effect
durur ama accepted history/pending work ve dar negative protection için güvenilir insan yolu bulunmaz.

**Zorunlu düzeltme/evidence.** Her aday/mod için detection, automatic safe-stop, affected scope, retained data,
owner-visible state, external human/provider action, credential class, support target, cost/overage, forward-reconcile,
reviewer ve exit evidence tablosu hazırlanmalı. Outage/account-lock/last-admin tabletop'ta owner yalnız
`approve / hold / stop / payment / legal-support / request-support` seçebilmeli. Recovery account, audit/floor custodian,
provider support ve emergency-negative operator ayrımı; self-approval ve common-mode önlemleri ile bağlanmalıdır.

**Hüküm.** Normal veya incident yolu owner technical repair gerektiriyorsa ilgili capability `REJECT-IF-UNMITIGATED`;
şu an tüm aday/hosting modları `HELD`.

### C-08 — Normalized safe TCO ve bounded spend yalnız kalem listesi olarak kalmış

**Bulgu.** Proposal framework/runtime, host, API, logs, security, support ve exit başlıklarını sayıyor; fakat React ve
Angular için aynı row IDs, resmi tarih/plan/region/unit, usage/MAU/egress, quota/overage, minimum fee, hard-cap kapsamı,
tax/FX/card uncertainty, stop action, incident/restore/exit horizon, external recovery/support ve owner approval yok.
"React daha AI-operable/kolay" veya static/managed host ucuzdur iddiası bu nedenle hesaplanamaz.

**Gizli maliyet saldırısı.** Web host/build/preview/CDN/egress; API/runtime/transaction/pooler; DB/Auth/private Storage;
durable queue/worker/DLQ; protected audit/fallback/floor; scanner/preview/derivative/object backup; logs/metrics/traces;
DNS/TLS/domain/SMTP; browser/AT/security test; support/incident reserve; isolated restore/clean-room; temporary
environment/export/import; secret reissue/DNS cutover; tax/FX/card/account closure aynı güvenli toplamın parçalarıdır.

**Zorunlu düzeltme/evidence.** A ve B, H1–H5 için aynı normalized BOM'u `mandatory / deferrable / optional /
scale-triggered` sınıflarıyla dört ufukta (normal ay, incident ayı, upgrade/compatibility, restore/exit) doldurmalı.
Her satır current official price/plan/region/unit/quota/overage, cap/stop, tax/FX/card, support/incident/restore/exit
etkisi ve owner approval taşımalı. Mandatory assurance bütçeye sığmazsa security, privacy, accessibility, audit,
continuity veya exit düşürülmez; capability `BILLING_HELD/HELD` kalır.

**Hüküm.** Bounded spend veya hidden adjunct kapanmadan her aile/mod `HELD`; unbounded overage veya safety assurance'ı
bütçeye uydurmak için zayıflatma `REJECT-IF-UNMITIGATED`.

### C-09 — Clean-room exit ve anti-resurrection kabul sınırı yazılmamış

**Bulgu.** Proposal taşınabilir static/container ve clean-room rebuild fikrini olumlu anıyor; fakat source untouched
önkoşulu, isolated quarantine import, plane-by-plane manifest/digest, independent acceptance, dual-run/cutover,
decommission ve provider/account closure kanıtı yok.

**Saldırı/arıza yolu.** `pg_dump`, object copy, provider clone, Docker image veya static `dist` taşınır; fakat current/
history/provenance/applicability, operation ledger/status/conflict/tombstone/outbox, release/package/artifact/schema/
config/message generation, principal/policy/grant/competence/session/epoch/recovery, object bytes/digest/lineage/
classification/retention/disclosure, protected audit/fallback/floor, queue pending/DLQ/lease, runtime config/secret,
DNS/TLS ve incident graph eksik kalır. Eski revoke/recall/delete/suspension/accepted-operation veya yeni valid data
dirilemez/dengeye alınamaz.

**Zorunlu düzeltme/evidence.** Source ortamı acceptance'a kadar değişmeden, yeni host isolated/quarantined import
almalı; tüm yukarıdaki plane'ler cross-plane manifest/digest ile uzlaştırılmalı. Negative auth, revoke, recall,
suspension, deletion, accepted-operation, old-cache/SW, stale handle ve queue replay testleri geçmeli; new valid data
silent rollback ile kaybolmamalı. Eksik plane `EXPORT_PARTIAL`/`RESTORE_QUARANTINE`; source silme/decommission yalnız
independent acceptance sonrası; secret reissue, DNS cutover, dual-run ve owner-readable fallback kanıtlanmalı.

**Hüküm.** Clean-room anlam korumuyorsa exit capability `REJECT-IF-UNMITIGATED`; evidence yokken React/Next, Angular
ve tüm hosting modları `HELD`.

## 4. MAJOR bulgular

### M-01 — React/Next koşullu liderliği ölçülmemiş AI aşinalığına dayanıyor

Manager proposal React'i AI modellerinin geniş bilgisi ve ekosistem nedeniyle koşullu lider tutuyor. `WEB-TASK-001`
(evidence review workspace), `WEB-TASK-002` (stale session/lost outcome) ve `WEB-TASK-003` (upgrade/rollback/exit)
aynı input/output/forbidden scope/reviewer/evidence formatıyla React ve Angular üzerinde uygulanmış değil. AI aşinalığı
security, a11y, no-owner-debug, task collision veya clean-room exit kanıtı değildir. Angular'ın LTS/CLI'si de otomatik
güvenli değildir; iki aday **aynı 0 PASS / mandatory gates HELD** statüsündedir.

**Düzeltme:** React/Next ve Angular için aynı no-code task simulation, context-pack boyutu/çakışma yüzeyi/unknown/
owner intervention/reviewer/evidence ölçümü yapılmadan liderlik dili kaldırılmalı; sonuç framework değil gate evidence'ı
olmalıdır.

### M-02 — Hosting/render alternatifleri ayrı karar kapıları olarak yeterince ayrılmamış

Proposal H1 managed static, H2 server-assisted shell/BFF ve H3 portable container diyor; research ise managed framework/
edge, managed static/CDN, portable static, portable Node/container ve split frontend/API olmak üzere beş farklı failure
shape tanımlıyor. Static host'ta auth/API/session/header/large upload; SSR/BFF'de secret/SSRF/timeout/second authority;
container'da patch/DNS/TLS/log/restore; split'te cross-origin/partial outage maliyeti birbirine indirgenemez.

**Düzeltme:** H1–H5 taxonomy'si tablo ve acceptance matrix'e aynen taşınmalı; her framework × hosting mode için aynı
`WEB-01..11`, owner/support, cost, restore ve exit kanıtı istenmeli. Mode seçimi framework seçimiyle otomatik
bağlanmamalı.

### M-03 — Static frontend + API yolunda session/CORS/CSRF ve partial outage varsayımı açık değil

Authenticated client-rendered workspace + explicit API calls düşük runtime gibi görünür; ancak H2/H5'te browser origin,
API origin, cookie domain, CORS preflight, CSRF token/origin, token storage, redirect/PKCE, upload directness,
status-polling ve correlation ayrı plane'lerdir. HttpOnly cookie kullanımı cross-origin policy'yi ortadan kaldırmaz;
bearer token kullanımı da browser bundle/storage sızıntısını çözmez. API unavailable iken static shell stale role/data
göstermemeli; accepted/history ve safe read ayrılmalıdır.

**Düzeltme:** Origin/session matrix, no-store/private response policy, CORS/CSRF negative tests, safe shell/read-only
degraded state, upload/status correlation ve DNS/TLS iki-uç runbook'u yazılmadan H2/H5 `HELD`.

### M-04 — SSR/server-assisted BFF authority creep, trusted proxy ve SSRF sınırı açık değil

Next server shell veya Angular SSR; secret custody, header forwarding, host/proxy trust, outbound URL fetch, request
body/timeout, error redaction, cache key ve correlation için ek runtime'dır. Server Action/SSR route "API'ye yakın"
olduğu için canonical mutation, role veya audit authority olamaz. Yanlış forwarded header veya user-controlled URL
SSRF/open redirect; server cache yanlış scope ile data disclosure yaratır.

**Düzeltme:** BFF/SSR seçilirse yalnız allowlisted Kavriva API DTO/proxy, trusted-proxy allowlist, outbound destination
allowlist, SSRF/body/time/rate bounds, no canonical DB/object writes, secret/error redaction ve route-by-route
compatibility graph kanıtlanmalı. SSR gerekçesi olmayan route'lar static/CSR'e zorlanmamalı; fakat static yol da auth
kanıtı olmadan açılmamalı.

### M-05 — State dictionary isimleri var; state-to-action/retained-data/resolver matrix yok

Proposal state adlarını kaybedilmeden göstereceğini söylüyor; ancak her state'te hangi read/mutation/upload/queue/
approval/recall/export işinin allowed/blocked olduğu, retained data, retry/cancel/status lookup, resolver/support,
audit reference, cost stop ve restore/exit etkisi görünür değil. `OUTCOME_UNKNOWN`'ı timeout, `HELD`'i error toast veya
`PARTIAL`'ı başarılı liste gibi göstermek kritik yanlış karar üretir.

**Düzeltme:** Tek state dictionary, UI/API/runbook/audit/queue için tam matris ve owner-readable next action oluşturulmalı;
life-cycle state (Draft/Review/Approved/Published/Recall) transport state'ten ayrı kalmalı. HTTP 2xx, green health,
queue-empty veya framework action completion hiçbir state'i override etmemeli.

### M-06 — Privacy/logs/telemetry için field-level redaction ve retention closure yok

Proposal correlation ID ve logs/metrics/traces kalemini sayıyor; fakat browser console, network error, Next RSC/Flight,
server action input, Angular interceptor/error, SSR payload, source map, CDN/host log, CSP report, analytics/third-party
telemetry ve upload filename/MIME/URL'lerinde token/cookie/PII/file bytes/technical private data redaction kuralları yok.
Operational log protected product audit değildir; audit immutability/legal hold ile ordinary telemetry deletion ayrıdır.

**Düzeltme:** Allowlist log schema (operation/release/correlation ID, state, scope sınırlı hash/reference), secret/cookie/
token/PII/file-content suppression, source-map policy, CSP report redaction, browser/host/provider retention, deletion/
export/legal hold, subprocessor/telemetry opt-out ve audit-vs-debug separation matrix'i hazırlanmalı. Log gap effect'i
`AUDIT_HELD`/`UNKNOWN` yapıyorsa bu state UI'da görünmeli.

### M-07 — Long-job ve queue/worker semantiği frontend selection'dan kopuk tutuluyor

Object scan/preview/derivative, large export/import, package/reconciliation, AI/OCR ve notification işlerinin "sonra
queue eklenir" diye ertelenmesi; frontend state, operation ledger ve deploy compatibility'yi bugünden etkiler. Browser
tab, `waitUntil`, callback, empty queue veya green worker canonical completion değildir.

**Düzeltme:** Her long-job ailesi için `QUEUED/SUBMITTED`, deterministic effect key, lease/heartbeat/checkpoint,
bounded retry, DLQ/quarantine, poison/backpressure, cancel, deploy drain, old/new message compatibility, owner backlog,
reconcile owner ve cost/restore/exit satırı no-code contract'ta şimdiden tanımlanmalı.

### M-08 — Dense table/diff/provenance graph performans ve erişilebilirlik kanıtı yok

Framework capability'si veya component library, large queue/windowing/virtualization, stable selection, keyboard table
semantics, graph linear equivalent, off-main-thread parse, focus recovery ve main-thread freeze riskini kanıtlamaz.
React concurrent/Suspense veya Angular change detection/event replay performans avantajı olarak varsayılamaz.

**Düzeltme:** Aynı representative scale ile filter/sort/pagination, diff, graph, bulk selection, memory/frame/input
latency, main-thread interruption, screen-reader and keyboard walkthrough yapılmalı. Virtualized row/column semantics,
focus return, non-color status, zoom/large text/reduced-motion ve export fallback `WEB-AC-002/003/004/014/015` ile
bağlanmalı.

### M-09 — Browser/OS/AT support matrix ve degraded behavior net değil

Proposal "gerçek browser + assistive technology" diyor fakat Chrome/Edge/Firefox/Safari, owner OS, iOS Safari/Android
Chrome/WebView, storage/cookie disabled, clock skew, slow/offline/network loss, zoom/large text, screen reader ve
reduced-motion matrix'i belirlemiyor. Browser compatibility veya WebView drift, privileged path'te sessizce partial
authority üretemez.

**Düzeltme:** Supported/unsupported matrix, feature detection/fallback, safe read/return-to-desktop, storage unavailable,
clock/time, upload/crypto/SW/streaming ve stale-session behavior her candidate/mode için evidence-gated olmalı. "Works in
one browser" support claim değildir; unsupported browser explicit `HELD/DEPLOYMENT_HELD` göstermeli.

### M-10 — AI task-pack, collision lock ve external human action örneği yok

Manager proposal AI-native design consistency ve task simulation'i doğru yönde anıyor; ancak route/file/config ownership,
credential audience/expiry, release lock, forbidden provider-owner/billing-root/service-role/SQL/SSH/approval scope,
dry-run, operation/generation precondition, reviewer/validator, forward recovery ve owner-readable handoff örneklenmiyor.
Generated `.next`, Angular `dist`, lockfile, environment/DNS/hosting config veya provider preview üzerinde iki AI'nın
yarım işi birleşebilir.

**Düzeltme:** React ve Angular için aynı machine-readable no-code task pack şablonu; exact scope, read/write/forbidden
paths, dependency snapshot, collision lock, dry-run, hard stop, evidence digest, independent reviewer/validator,
external provider/human action ve completion `HELD` listesi olmadan AI-operability PASS sayılmamalı.

### M-11 — Release cadence/LTS, dependent packages ve upgrade regression eşit kapatılmamış

React core'un Next LTS'sine denk bağımsız LTS tablosu yok; Next App Router RSC/bundler API'leri React minor'ları arasında
semver garantisi taşımıyor. Angular'ın 12+12 ay policy'si Angular/CLI/TS/Node/RxJS/CDK/grid/auth package'larına garanti
değil. Manager "LTS" diyerek bu closure'ı kısaltmamalı.

**Düzeltme:** Exact lockfile/SBOM, Node/TS/browser matrix, advisory watch, pre-release/deprecated package block,
staged codemod/manual diff, API N/N-1, CSP/CSRF/session/epoch, a11y/large data/upload/rollback ve independent reviewer
kanıtı olmadan major auto-promote yasaklanmalı. React/Next ve Angular aynı upgrade horizon'unda ölçülmeli.

### M-12 — Preview, source-map, environment ve deploy failure semantics'i production boundary'den ayrılmamış

Managed preview/branch URL'si production secure-origin, session audience veya data isolation kanıtı değildir. Preview
build'inin production credential/environment alması; source map/error overlay'nin private data çıkarması; CDN/asset
propagation'ın API/schema/negative floor'dan geri kalması; host rollback'in DNS/TLS/cache/SW'yi geri almaması olasıdır.

**Düzeltme:** Preview no-production-data/no-privileged-token policy, environment audience/secret separation, source-map
access policy, immutable artifact digest, release promotion approval, cache/SW purge, DNS/TLS certificate state,
old-revision drain, API/schema/message/object compatibility ve explicit `PARTIAL/RECONCILING`/`DEPLOYMENT_HELD`
runbook'u her host modunda kanıtlanmalı.

## 5. MINOR bulgular

### m-01 — H1/H2/H3 adları araştırma taxonomy'siyle çakışıyor

Manager proposal'daki H1/H2/H3, research'teki beş hosting shape ile aynı değil. Karar ve BOM tablolarında `managed
framework/edge`, `managed static`, `portable static`, `portable container`, `split static/API` adları kullanılmalı; aksi
halde bir hosting şeklinin evidence'ı diğerine yanlış taşınır.

### m-02 — React "LTS" ifadesi React core ile Next support policy'sini ayırmalı

Next Active/Maintenance LTS, React core için bağımsız Kavriva support guarantee'si değildir. Angular LTS de dependent
packages'ın LTS'si değildir. Tarihli snapshot, exact lockfile ve release-watch sahibi açıkça yazılmalı.

### m-03 — "No-store" ifadesi response sınıflarıyla bağlanmalı

Authenticated HTML, API data, operation status, public static asset, untrusted preview ve safe history için farklı
cache/retention davranışı gerekir. Genel `no-store` önerisi kabul edilmeden önce hangi sınıfı kapsadığı ve safe-read
degraded state'i netleştirilmelidir.

### m-04 — Public SEO gerekmez hükmü internal secure-origin ihtiyacını azaltmıyor

SEO olmaması public indexed content, preview secrecy, HSTS/TLS, CSP, frame-ancestors, `form-action`, CORS/CSRF veya
authenticated cache politikasını gevşetmez. Bu varsayım yalnız render optimizasyonu kararında kullanılmalı.

### m-05 — Exact numeric limitsin açık olması “şimdi değer seç” anlamına gelmez

Body/resource limit, session TTL, cache lifetime, queue retry, upload size, retention ve support target henüz `OPEN`
kalabilir; fakat seçilene kadar capability `HELD` olmalı ve unbounded/default değer production varsayımı yapılamaz.

## 6. Zorunlu düzeltme ve eşit evidence pack'i

Manager proposal'ın Phase-4 handoff'u aşağıdaki düzeltmeleri eklemeden tamamlanmamalıdır:

1. **Eşit finalist kuralı:** React/Next ve Angular için `WEB-TASK-001..003` aynı no-code fixture, aynı minimum context
   pack, forbidden scope, reviewer/validator ve evidence çıktısıyla yürütülmeli. AI familiarity veya ecosystem size
   yalnız ölçülmüş task/repair/operability sonucu olarak kullanılmalı.
2. **Browser-to-API authority matrix:** Browser, static artifact/CDN, SSR/BFF, Next Server Action, Angular HttpClient/
   guard/interceptor, Kavriva API, RLS/policy, object handle, preview, provider console ve billing/support yollarının
   her biri için allow/deny/hold/unknown, disclosure ve audit sonucu yazılmalı.
3. **Session/security pack:** Secure origin, cookie/token storage, rotation/revoke, one Kavriva security epoch, logout-all,
   factor-loss, transaction-bound step-up, origin/PKCE/redirect, CSRF/XSRF, CORS, XSS contexts, sanitizer, CSP/nonce/
   Trusted Types, source-map/secret redaction ve accessibility'de re-auth testleri.
4. **Stale/outcome pack:** policy/access version, role/grant, object/version/release/schema/config/client capability,
   negative floors ve operation fingerprint'i her mutating view/commit'te; stale tab/back/refresh/second tab/SW; timeout
   before/after commit; same-ID lookup; different payload conflict; cross-tenant status deny; draft preservation.
5. **Cache/release pack:** Hashed artifact, HTML/API/status no-store/private keys, Cache-Control/Vary/ETag, RSC/TransferState/
   prefetch behavior, SW update/kill/drain, old-tab, API N/N-1, recall/revoke/delete/accepted-operation floor ve
   forward recovery.
6. **Quarantine pack:** Interrupted/resumed/duplicate/large/malicious upload; MIME/type confusion; archive/SSRF/redirect/
   traversal/resource limits; digest/lineage/classification; isolated untrusted preview; short-lived exact-scope handle;
   derivative/backup/orphan/restore; no active/public handle before manifest.
7. **Artifact/supply-chain pack:** Exact lockfile, SBOM/license/advisory, provenance/attestation/signature, reproducible
   install/build, independent verifier/trust roots, postinstall review, immutable promotion, secret/build-image pin,
   old/new runtime drain and schema/message compatibility.
8. **Hosting/continuity pack:** H1–H5 each separately; secure headers/TLS/DNS/domain, account/quota/support outage,
   health/readiness versus product state, safe read/positive hold, emergency negative boundary, deploy rollback/forward
   recovery, cache/SW purge and no-owner incident path.
9. **Privacy/log pack:** Field-level allowlist, correlation/operation/release ID, no token/cookie/PII/file bytes, browser/
   SSR/CDN/provider/source-map/CSP report redaction, retention/legal hold/export/deletion, audit-vs-debug separation,
   third-party telemetry and subprocessor review.
10. **Long-job pack:** Operation/effect key, queue acceptance, lease/heartbeat/checkpoint, retry/DLQ/poison/backpressure,
    cancel, deploy drain, message version, owner backlog and reconciliation for scan/render/OCR/export/import/notification/
    package/research jobs.
11. **Owner/support/TCO pack:** Account/legal/billing/domain/DNS/TLS/support/recovery/audit/floor/negative actor roles;
    owner-readable tabletop; identical BOM rows and normal/incident/upgrade/restore/exit horizons with cap/overage/stop,
    tax/FX/card and external human/support dependencies.
12. **Clean-room pack:** Source untouched; isolated cross-plane import of current/history/provenance, ledger/tombstones,
    release/package/schema/config/message, identity/policy/session/epoch, object bytes/lineage, audit/floor, queue,
    runtime/artifact/secret/DNS; anti-resurrection, dual-run, cutover, independent acceptance and `EXPORT_PARTIAL`.

## 7. Hard-fail koşulları

Aşağıdaki koşullardan biri gerçek evidence'ta kapanmadan ilgili capability/hosting mode açılmaz:

1. Browser, hidden route, cached role/JWT, Next Server Action, Angular guard/interceptor, provider console, Data API/RPC/
   Storage/signed URL veya static preview canonical authority/effect üretebiliyor.
2. Login, TOTP/SMS/magic-link fallback, route guard veya framework XSRF helper; current API authorization, transaction-bound
   step-up, epoch/revoke veya audit-before-effect yerine geçiyor.
3. Untrusted HTML/SVG/URL/archive/preview/AI/OCR active/public technical use'a quarantine, lineage, digest, classification
   ve exact scoped handle olmadan giriyor.
4. Old tab/cache/SW/artifact/queue message/object handle/restore snapshot daha yeni recall/revoke/delete/suspension/
   accepted-operation/migration floor'ını kaldırabiliyor.
5. Timeout sonrası blind duplicate, guessed success/failure veya cross-tenant status disclosure oluşuyor.
6. High-consequence positive effect protected audit receipt/fallback custody yokken açılıyor.
7. Mutable/unverified build, compromised dependency, unsigned artifact, provider-console-only promotion veya incompatible
   rollback üretime alınabiliyor.
8. Normal/incident/restore/exit yolu owner'ın SQL/SSH/raw-log/devtools/queue surgery/secret/DNS/provider-console repair
   yapmasını gerektiriyor veya bağımsız support/recovery/negative actor bulunmuyor.
9. Mandatory safety/privacy/a11y/audit/continuity/exit maliyeti cap/stop olmadan veya gizli adjunctlarla taşınıyor;
   budget pressure güvenlik standardını düşürüyor.
10. Clean-room replacement product meaning, identity/policy/epoch, object lineage, audit/floor, queue/tombstone veya
    negative truth'i koruyamıyor; source acceptance öncesi değiştiriliyor.

## 8. Nihai disposition

**Manager proposal:** `HELD_WITH_REQUIRED_CHANGES / NO WINNER / ADR NOT READY`  
**React + Next.js:** `HELD — equal evidence boundary; no conditional leadership accepted`  
**Angular:** `HELD — equal evidence boundary; no automatic fallback/winner`  
**Hosting H1–H5:** `HELD — mode-specific security, cost, owner and exit evidence missing`  
**Capability-level result:** Direct bypass, stale positive authority, quarantine bypass, weak privileged path,
effect-before-audit, unbounded spend, owner repair or unsafe exit appears → `REJECT-IF-UNMITIGATED`; otherwise safe hold
and evidence completion remain mandatory.

Bu review `DEC-0037` consumer identity çalışma yönünü, `DEC-0038` API runtime çalışma hipotezini veya `DEC-0021`
browser/no-code kararını değiştirmez. Supabase-centered backend, Supabase Auth veya Supabase Edge hiçbir hosting veya
frontend için üretim seçimi değildir. Hiçbir hesap/plan/provider/purchase/code/prototype/deployment/ADR/Gate 4 → 5
geçişi onaylanmamıştır.

**Karar:** `HELD / NO WINNER / REACT-NEXT VE ANGULAR'A EŞİT KANIT KAPISI / HOSTING MODLARI AYRI HELD / ADR NOT READY`.

