# DEBATE-012 — Render / Hosting Tie-break: Internal Operations

**Durum:** `PHASE-4 NO-CODE / CONDITIONAL DEFAULT ONLY / 0 PASS / 4 MODES HELD / ADR NOT READY`  
**Tarih:** 2026-09-19 (Europe/Istanbul)  
**Kapsam:** Internal Operations browser surface; React (Vite/static ve gerektiğinde Next), Angular, Vue/Nuxt ve
Svelte/SvelteKit; managed static SPA/CDN + API, same-origin server-assisted shell/BFF, managed serverless/edge SSR ve
portable/managed Node container render/hosting biçimleri  
**Authority:** Kavriva API; browser, framework server, hosting dashboard ve provider console canonical authority değildir

Bu belge bir provider, framework, exact version, account, plan, region, runtime, package, domain veya satın alma kararı
değildir. Kod, prototip, executable spike, deployment veya production proof yapılmaz. Amaç, public SEO gerektirmeyen
desktop-class Internal Operations için en sade güvenli başlangıç render/hosting yönü varsa onu açıkça sınamak ve dört
hosting biçimini eşit evidence kapısında tutmaktır.

## 0. Kısa hüküm

En sade güvenli **varsayılan yön** olarak şu pattern önerilebilir:

> **Authenticated, CSR-first, route-specific static web artifact + managed static/CDN delivery + browser → Kavriva API.**
> **SSR/BFF, edge runtime ve service worker varsayılan değildir.**

Bu bir `PASS`, production seçimi veya provider onayı değildir; `CONDITIONAL DEFAULT / HELD` çalışma yönüdür. Gerekçesi:

- Internal Operations public SEO veya crawler-rendered HTML istemiyor; bu nedenle SSR'nin SEO faydasını almak için
  authenticated HTML/payload ve ikinci runtime eklemek zorunlu değil.
- Static delivery canonical DB/object/publication/recovery authority taşımaz; authority yüzeyi daha küçük ve clean-room'da
  yeniden üretilecek artifact daha nettir.
- Browser, yalnız API operation/status sözleşmesini tüketir; `ACCEPTED` yalnız canonical API effect + protected audit +
  version/generation ile gösterilir.
- Service worker, authenticated HTML/API/status veya privileged mutation taşımaz; varsayılan olarak kapalı tutularak
  old-cache/old-tab authority riskinin bir sınıfı azaltılır.
- Managed static delivery, tek teknik olmayan owner için portable static/container'a göre DNS/TLS, purge, build ve
  incident yükünün bir bölümünü azaltabilir; bu, provider account/quota/support/exit yükünü ortadan kaldırmaz.

Bu default yalnız şu ortak koşullar eşit kanıtla kapanırsa açılabilir: strict session/cookie-or-token boundary,
server-side CSRF/CORS/origin, XSS/CSP/Trusted Types, stale-tab/epoch/outcome, no-store/private cache, quarantine-first
upload, API correlation, outage safe-stop, immutable artifact/deploy compatibility, privacy/log redaction, owner/support,
normalized safe TCO ve source-untouched clean-room exit. Bu koşullar kapanmazsa **BFF/SSR'ye otomatik geçiş yapılmaz**;
capability `HELD` kalır ve gap açıkça gösterilir.

### Dört biçimin tie-break sonucu

| Render/hosting biçimi | İlk tercih sırası | Belgesel hüküm | Ana gerekçe |
|---|---:|---|---|
| Managed static SPA/CDN + browser → Kavriva API | Koşullu default | `HELD` | En küçük web authority/runtime yüzeyi; cross-origin/session/CORS/CSRF ve API partial-outage kanıtı şart |
| Same-origin server-assisted shell/BFF | Koşullu ikinci seçenek | `HELD` | CORS yüzeyini azaltabilir; fakat ikinci runtime, secret, SSRF, timeout, BFF authority/cache ve support yüzeyi ekler |
| Managed serverless/edge SSR | Route-specific istisna | `HELD` | SEO gereksiz; SSR/payload/cache/edge quota/region/rollback coupling ancak somut ihtiyaçla haklı olabilir |
| Portable artifact + managed/portable Node container | Sonraki challenger | `HELD` | Artifact exit yolu güçlü olabilir; fakat reverse proxy, patch, TLS/DNS, logs, capacity, restore ve no-owner-debug yükü büyür |

Bu sıralama framework seçimi değildir ve sayısal skor değildir. Four-way audit sonucu React/Next, Angular, Vue/Nuxt ve
Svelte/SvelteKit için `0 PASS / 0 REJECT / 4 HELD`; mevcut task simulation'da React/Next ve Angular'ın
`WEB-TASK-001..003` sonuçları da `HELD`dir.

## 1. Okunan kanıt ve değişmez karar sınırı

Tamamı okunan girdiler:

- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_PRIMARY_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_FAILURE_TCO_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_MANAGER_PROPOSAL.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__REVIEW_A_ARCHITECTURE_ACCESSIBILITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__REVIEW_B_SECURITY_OPERABILITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__TASK_SIM_WEB_001.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__FOUR_WAY_EQUIVALENCE_AUDIT.md`
- `00_CONTROL/DECISION_LOG.md` — özellikle `DEC-0037` ve `DEC-0038`

Bağlayıcı sınırlar:

1. Internal Operations browser-based ve desktop-class'tır; public SEO, desktop wrapper veya authenticated offline
   console gereksinimi yoktur. Phone/narrow browser yalnız açıkça desteklenen safe read/triage/status yüzeylerini
   sağlayabilir; high-consequence write'ın viewport'ta sessizce gizlenmesi kabul edilemez.
2. `DEC-0037`: authentication authority değildir. Provider identity, Kavriva principal, session, role/grant,
   competence/independence, workload/AI identity, legal/billing owner ve historical audit actor ayrıdır. Step-up,
   session/epoch/revoke, CSRF/PKCE/origin, recovery ve support evidence kapanmadan privileged production `HELD`dir.
3. `DEC-0038`: browser ve provider console doğrudan canonical DB/object/publication/export/recovery authority alamaz;
   tüm hassas yollar provider-neutral Kavriva API arkasındadır. Commit-time tuple, operation fingerprint, protected
   audit-before-effect, durable long-job, monotonic negative floors, state dictionary, owner/support ve clean-room exit
   binding'dir.
4. Static/SSR/CSR/hybrid/serverless/container, framework primitive'i veya host dashboard'u ürün state'i, audit'i,
   authorization'ı, publication/recall'ı veya recovery floor'unu değiştiremez.
5. No-code sınırı nedeniyle aşağıdaki öneri mekanizma/fixture/evidence sırasıdır; implementasyon veya purchase planı
   değildir.

Evidence dili: `CONFIRMED` resmi/repository mekanizması; `INFERRED` sınırlı uygulama çıkarımı; `OPEN` bilinçli
deferred detail; `HELD` olumlu kanıt yok; `REJECT-IF-UNMITIGATED` hard-fail güvenli hold/recovery ile kapatılmamış.

## 2. Default yönün sınırları ve güvenli çalışma şekli

### 2.1 Render ilkesi

- Public SEO yoktur; authenticated workspace route'ları için CSR-first static shell başlangıç hipotezidir.
- Route-specific static artifact yalnız shell ve UI kodunu taşır. User-specific data, operation status, role/grant,
  provenance, private evidence, audit, release/recall veya high-consequence effect artifact'a gömülmez.
- Server-side rendering, BFF veya edge route yalnız ölçülebilir initial-load, secure same-site session, accessibility
  veya proxy ihtiyacı gösterilirse ayrı route/capability için yeniden açılır. Bir route'un SSR olması diğer route'ların
  authority'sini değiştirmez.
- Static build artifact, CDN cache, browser state, framework cache, optimistic UI veya service worker `ACCEPTED`
  anlamı veremez. Accepted sonuç API operation ID, canonical version/generation ve protected audit reference ile gelir.
- Serverless/edge veya container kullanılsa bile runtime replaceable ingress/transport worker'dır; persistent product
  truth, operation ledger, audit/floor, object manifest ve recovery state runtime memory'sinde tutulmaz.

### 2.2 Hosting ilkesi

Managed static/CDN, owner-operability açısından portable static/container'a göre daha sade görünebilir; fakat şu
provider yükleri açık kalır: account/legal ownership, build quota, bandwidth/egress, CDN purge, domain/TLS, support,
provider outage, preview isolation, rollback semantics, logs/subprocessors ve clean-room exit. Bu nedenle “managed”
`PASS` veya “free” güvenli TCO sıfırı değildir.

Portable static/container ise exit ve artifact kontrolü verebilir; fakat owner'ın DNS/TLS, reverse proxy, patch/CVE,
capacity, log redaction, backup/restore, deploy drain veya certificate repair yapması gerekirse `DEC-0029` ihlal edilir.
Bunlar bounded AI automation + external support/recovery zinciriyle kapanmadıkça uygun değildir.

### 2.3 API / degraded operation ilkesi

- Browser API command'i operation ID, immutable payload fingerprint, actor/session/epoch, exact scope/resource/
  version/generation ve expected effect ile gönderir.
- Timeout/abort/response loss `OUTCOME_UNKNOWN` olur; same-ID status lookup dışında blind retry yoktur. Changed payload,
  actor veya scope `CONFLICT/HELD`; status lookup cross-tenant disclosure yapmaz.
- API unavailable iken safe history/read yalnız last-known timestamp/freshness ile sürdürülebilir. Approval, publish,
  recall, role/policy, export, source withdrawal veya canonical mutation `SERVICE_UNAVAILABLE/HELD` olur.
- Long upload/scan/render/OCR/export/import/package/reconciliation/notification browser request'ine sığdırılmaz;
  durable queue/worker, lease, checkpoint, bounded retry, DLQ/quarantine, backpressure, drain ve reconciliation
  sözleşmesine bağlıdır.

## 3. Dört hosting biçiminin eşit adversarial karşılaştırması

| Boyut | Managed static SPA/CDN + API | Same-origin server-assisted shell/BFF | Managed serverless/edge SSR | Portable/managed Node container |
|---|---|---|---|---|
| Canonical authority | Static artifact yalnız UI; API tek authority | BFF yalnız allowlisted transport; API tek authority | SSR/edge yalnız transport/render; API tek authority | Container yalnız replaceable runtime; API/data plane tek authority |
| Session/cookie/token | Browser→API origin, secure cookie/token contract; no browser secret | HttpOnly same-origin session mümkün; BFF session/epoch authority olamaz | Edge header/cookie forwarding, private payload; provider runtime semantics | Reverse proxy/secret rotation/session drain; owner-independent automation gerekir |
| CSRF/CORS/origin | Strict CORS + server CSRF/Origin/Referer; same-site design evidence | Same-origin CORS yüzeyi azalır; CSRF yine server-side zorunlu | Edge proxy/cache CORS/CSRF/redirect trust ayrıca kanıtlanır | Proxy/API origin and CSRF/CORS contract; forwarded header trust sınırı |
| XSS/CSP/Trusted Types | CDN/headers + app encoding; untrusted source/preview API/quarantine'da | BFF/SSR error/HTML/headers yeni XSS/SSRF yüzeyi | SSR payload/nonce/cache/header parity, untrusted HTML izolasyonu | Proxy/header/config/source-map/log redaction owner-independent olmalı |
| Stale tab/cache/SW | Immutable assets; authenticated data/status private/no-store; SW default off | BFF/SSR HTML and server cache actor/scope/epoch-bound; no shared private cache | Edge/SSR cache and payload invalidation; old revision/region race | Reverse proxy/app cache/SW purge/drain/release graph |
| File upload | Browser direct public write yok; API-scoped quarantine handle; long job separate | BFF may proxy but body/timeout/SSRF limits and API quarantine unchanged | Function body/time limits; large upload/scan worker separate | Multipart/body/proxy limits; queue/object/scanner separate |
| API correlation/outcome | Browser status resolver; static host success is not effect | BFF must preserve operation ID and unknown/hold; no hidden retry | Edge timeout/buffering/retry cannot collapse unknown | SIGTERM/health/timeout/retry must preserve same operation ledger |
| Outage | Shell/read-only may load; positive mutation hold; API dependency visible | BFF outage and API outage distinct; stale shell no authority | Edge/provider/region outage; safe read only with freshness | Host/proxy/cert/instance outage; external support/automation required |
| Deploy/rollback | Immutable artifact digest; API N/N−1/schema/floor compatibility; host rollback artifact-only | Shell/BFF/API/config/message compatibility; no DB rollback assumption | Function/edge revision, cache, region, secret, API/schema/message graph | Image/base runtime/worker/config/drain plus API/data forward recovery |
| Logs/privacy | CDN/browser logs no token/cookie/PII/file bytes; CSP report/source-map redaction | BFF request/response/error/header redaction; correlation without payload | Edge logs/headers/payload/subprocessor retention | Host/reverse-proxy/app/worker logs, disk/remote sink and deletion policy |
| Account/support | CDN/domain/build/quota/provider support; API remains separate | Static host + BFF account/runtime + API support | Edge/runtime/account/region/quota + API support | Host/DNS/TLS/patch/restore + API support; largest owner burden |
| Cost shape | Low runtime cash shape, but API/auth/object/audit/log/test/exit remain | Adds server compute, secrets, logs, egress and support | Adds request/CPU/cold-start/region/cache/egress and provider coupling | Adds instance/image/patch/proxy/certs/log/backup/capacity labor |
| Clean-room exit | Source/lock/SBOM/artifact/headers/cache/session/API/object/audit/floor and DNS/TLS | Also BFF config/secret/route/proxy and runtime behavior | Also edge preset/bindings/cache/region/secret/rollback behavior | Also image/base OS/proxy/worker/volumes/DNS/TLS/observability |
| Tie-break | **Conditional default / HELD** | **Secondary / HELD** | **Exception / HELD** | **Challenger / HELD** |

### 3.1 Managed static SPA/CDN + API — koşullu default

**Olumlu sinyal:** Internal app için SEO/SSR zorunluluğu yoktur; artifact merkezi ve versioned olur; web runtime'ın
ephemeral/server-side authority yüzeyi küçülür; React Vite/static, Next static export (server features kullanılmadan),
Angular static/CSR, Nuxt `ssr:false`/prerender ve SvelteKit adapter-static benzer artifact şekline yaklaşabilir.

**Saldırı yüzeyi:** API ayrı origin ise CORS, credentialed requests, cookie domain, CSRF token/Origin, redirect/PKCE,
preflight failure, upload directness, status polling ve correlation; CDN/HTML/API cache ayrımı; preview URL isolation;
large-file body handling; API unavailable iken shell'in stale role/data göstermesi.

**Zorunlu kapı:** Exact same-site/origin/session strategy ve server-side CSRF; no token/service key in bundle/local
storage/logs; authenticated HTML/API/status private/no-store; static assets hashed; no service-worker privileged path;
`SERVICE_UNAVAILABLE` safe read/hold; API N/N−1 and release/negative-floor compatibility; object upload always
quarantine-first; managed host outage/account/support and clean-room evidence.

**Disposition:** `CONDITIONAL DEFAULT / HELD`. CORS/CSRF/session/partial-outage veya owner support kapanmıyorsa bu
pattern `REJECT-IF-UNMITIGATED`; BFF/SSR otomatik bypass değildir.

### 3.2 Same-origin server-assisted shell/BFF — koşullu ikinci seçenek

**Olumlu sinyal:** Browser/API same-origin arrangement ile CORS ve bazı cookie/redirect karmaşıklığı azalabilir; HttpOnly
session ve server-side header/CSP üretimi kolaylaşabilir; API endpoint correlation tek origin'den taşınabilir.

**Saldırı yüzeyi:** BFF'nin provider/API yerine ikinci authority sanılması; user-supplied tenant/resource/version'ın
trusted kabulü; BFF cache'in scope/epoch dışı paylaşılması; SSRF/Host/forwarded header/open redirect; request body/time
limits; secret leakage; BFF timeout'un API `OUTCOME_UNKNOWN` semantiğini bozması; ayrı build/deploy/log/billing/exit.

**Zorunlu kapı:** BFF yalnız allowlisted Kavriva API transport/DTO adapter olmalı; canonical DB/object write, approval,
publication, audit/floor ve recovery yok. Commit-time authz/epoch/version/fingerprint/audit API'de tekrarlanmalı. Trusted
proxy/outbound allowlist, SSRF/body/rate/time bound, private/no-store, error/source-map redaction, same operation ID,
deployment compatibility, owner support ve clean-room BFF import kanıtı gerekir.

**Disposition:** `SECONDARY / HELD`. Static cross-origin path için documented security gap kapanmıyorsa yeniden açılabilir;
"same-origin" tek başına daha güvenli veya daha ucuz kabul edilemez.

### 3.3 Managed serverless/edge SSR — route-specific exception

**Olumlu sinyal:** Bazı route'larda first-load/payload/proxy/secure-origin ergonomisi ve edge latency avantajı olabilir;
frameworklerin SSR/edge mekanizmaları resmi olarak mevcut.

**Saldırı yüzeyi:** SSR HTML/payload/cache'e role/epoch/private evidence sızması; edge region/replica consistency;
function CPU/memory/wall-clock/body/log limits; provider adapter drift; cache invalidation; secret binding/rotation;
old revision/old tab; platform rollback'in API/schema/queue/object/audit/floor'ı geri almaması; managed quota/support.

**Zorunlu kapı:** Her SSR route için private/no-store veya exact actor/scope/epoch cache; API N/N−1, release/config/
message/content/object/package generations; edge timeout/body/retry `OUTCOME_UNKNOWN`; no long jobs in request;
untrusted render isolation; immutable artifact/revision; old revision drain; DNS/TLS/account/support; normalized
incident/restore/exit BOM.

**Disposition:** `EXCEPTION / HELD`. Public SEO yokken SSR için ürün gerekçesi ve eşit cost/security/exit kanıtı yoksa
default olarak açılmaz.

### 3.4 Portable artifact + managed/portable Node container — challenger

**Olumlu sinyal:** Node/container artifact, framework server ihtiyaçlarını ve host replacement'ı görünürleştirebilir;
static artifact ile karşılanamayan server-assisted path'ler taşınabilir olabilir.

**Saldırı yüzeyi:** Reverse proxy/headers/TLS/DNS/cert renewal; image/base runtime CVE; environment/secret layer; health
endpoint'in product truth sanılması; graceful drain/old revision; capacity/instance cost; logs/metrics/backup/restore;
queue/worker coordination; owner veya AI'nın SSH/SQL/raw log/console repair'a itilmesi.

**Zorunlu kapı:** Fully automated bounded deploy/drain/secret rotation/health/readiness/rollback/forward recovery;
managed state (queue, object, audit/floor, identity, DNS, support) clean-room'da yeniden kurulmalı; source untouched,
owner-readable incident, external support/recovery people ve no-owner-debug kanıtı olmalı. Container image rollback
DB/schema/data/audit/negative-floor rollback'i değildir.

**Disposition:** `CHALLENGER / HELD`. Portable/managed container, static default başarısız olunca otomatik fallback
değildir; owner technical repair gerekiyorsa `REJECT-IF-UNMITIGATED`.

## 4. Frontend family × hosting fit — eşit değerlendirme

Bu tablo mechanism fit'i gösterir; hiçbir hücre `PASS` değildir. Dört aile için aynı API authority, state dictionary,
security/a11y/failure/cost/exit oracle'ı kullanılır.

| Family | Managed static SPA/CDN + API | Same-origin shell/BFF | Managed serverless/edge SSR | Portable/managed Node container |
|---|---|---|---|---|
| **React + Vite/static; Next gerektiğinde** | Vite/static artifact veya Next static export ile en düşük runtime surface; Next server features kaybolur. Browser API CORS/CSRF/cache/upload kanıtı şart. `HELD` | Next server shell/Route Handler/Server Action yalnız transport; RSC/cache/secret/timeout/SSR authority riskleri. Vite ayrı BFF seçimi ister. `HELD` | Next SSR/edge/adapter; React/Next RSC/canary/bundler/version closure, payload/cache/region/rollback kanıtı. `HELD` | Next Node/Docker/standalone veya React server composition; reverse proxy, Node/runtime, image, logs, drain, exit. `HELD` |
| **Angular** | `ng build` static/CSR; HttpClient/XSRF client half, static fallback/headers/CSP/API contract external. `HELD` | Angular SSR/server output veya thin proxy; hydration/TransferState/interceptor/guard authority ve cache riskleri. `HELD` | Angular SSR/hybrid/non-Node path; hydration/event replay, Node/TS/RxJS/CLI/CDK and edge parity. `HELD` | Angular SSR Node output or static served by container; CLI/build config, proxy/TLS, patch, logs, restore/exit. `HELD` |
| **Vue + Nuxt** | `ssr:false` SPA/prerender; `useFetch`/payload/cache and CORS/CSRF/upload/status boundaries. `HELD` | Nitro server/middleware as transport only; `useCookie`, header forwarding, routeRules, SSRF/proxy/cache. `HELD` | Nuxt universal/Nitro/edge; routeRules/SWR/ISR/payload, module/support/adapter and region/rollback. `HELD` | Nitro Node `.output`; modules/runtime-config/reverse proxy, long-job/log/support/exit. `HELD` |
| **Svelte + SvelteKit** | adapter-static/prerender; form actions not available as authority; browser API/session/cache/SW evidence. `HELD` | adapter-node or server hooks/actions as transport; cookie/locals/load serialization, CSRF/CSP, body/shutdown. `HELD` | page `ssr`/`csr`/`prerender`, adapter edge; SvelteKit 2/v3, action/load/hook/adapter/cache parity. `HELD` | adapter-node standalone or equivalent; body limit, graceful shutdown, proxy/TLS/log/worker/exit. `HELD` |

### 4.1 Family-neutral interpretation

- React Vite/static, Angular static, Nuxt SPA/prerender ve SvelteKit adapter-static aynı **artifact shape**'e yaklaşabilir;
  bu, bundle/a11y/grid/editor/security/AT/upgrade/exit yüklerinin aynı olduğu anlamına gelmez.
- Next, Angular SSR, Nuxt Nitro veya SvelteKit server/edge output'unun mevcut olması BFF/SSR'yi gerekli kılmaz.
- React/Next AI familiarity, Angular LTS, Nuxt universal rendering veya Svelte compiler a11y warning'i hiçbir mode için
  API authority, CSRF, current session, WCAG, quarantine, owner support veya clean-room PASS vermez.
- Four-way audit'in `WEB-TASK-001..003` çıktıları dört adayda yapısal olarak eşittir: 7 conceptual units/task,
  `High/High/Very high` planning complexity, fakat tümü `HELD`. Bu eşitlik bir framework puanı değil, aynı kabul
  standardının uygulanabildiğine dair no-code parity'dir.

## 5. Ortak security/session/cache/upload sözleşmesi

### 5.1 Session, cookie/token, CSRF/CORS

| Konu | Managed static/API | Same-origin BFF | Edge SSR | Container |
|---|---|---|---|---|
| Secret | Bundle/public env/local storage'da privileged secret yok; API veya exact session boundary | BFF server secret custody olabilir, browser'a leak yok | Edge bindings/headers no bundle; rotation/drain | Env/secret store/image layer/log redaction; rotation/drain |
| Session | Secure/HttpOnly/SameSite veya açıkça gerekçeli token; current API session/epoch | HttpOnly possible; BFF session product authority değil | Forwarded cookie/header allowlist; payload private | Proxy/API cookie/session; old revision invalidation |
| CSRF/CORS | Server CSRF token + Origin/Referer + strict CORS/credential allowlist | Same-origin CORS azalır; CSRF hâlâ zorunlu | Edge preflight/cache/origin; API recheck | Reverse proxy/API origin; forwarded header allowlist |
| Step-up/revoke | API transaction-bound; open tabs/status/handles epoch | BFF cannot bypass API step-up | Edge cannot trust cached claim | Container cannot replace API/recovery |

Next Server Action origin check, Angular HttpClient XSRF interceptor, Nuxt `useCookie`/middleware, SvelteKit action
cookie defaults veya route guard yalnız defense/transport katmanıdır. Hiçbiri `DEC-0037` current API authorization,
phishing-resistant step-up, end-to-end epoch veya protected audit yerine geçmez.

### 5.2 XSS/CSP/untrusted content

Internal Operations source/evidence/preview içeriğini render eder; untrusted HTML, SVG, URL, markdown, office/PDF
preview veya AI/OCR output'u trusted technical truth değildir. Dört mode'da ortak zorunluluk:

- contextual encoding/sanitization; React `dangerouslySetInnerHTML`, Angular bypass APIs, Vue `v-html`/dynamic head,
  Svelte raw HTML/DOM escape hatch'leri ayrı review;
- CSP report-only → enforce, nonce/hash/SRI/Trusted Types kararı ve third-party script allowlist;
- preview/render isolated from operations credential/authority; original/derivative digest/lineage/classification;
- CSP reports, SSR errors, browser logs, source maps ve host logs token/cookie/PII/file bytes taşımaz;
- CSP defense-in-depth'tir; API authz/CSRF/audit/quarantine yerine geçmez.

### 5.3 Stale tab, cache ve service worker

- Authenticated HTML/API/status private/no-store veya exact actor/scope/epoch-bound cache olmalı; public hashed static
  assets ayrı tutulmalı.
- Old tab/back/refresh/second tab, role revoke, security epoch, object/release/schema/config/package generation ve newer
  negative floor her mode'da API commit'te tekrar kontrol edilir.
- Service worker default olarak kapalıdır. Gerekirse yalnız immutable/read-only shell için version/update/kill-switch/
  old-tab drain kanıtı gerekir; privileged mutation, role/status/audit veya recalled data SW cache'ine alınmaz.
- Host/CDN/SSR/routeRules/TransferState/loader cache/reverse proxy `ACCEPTED`, recall clear veya session revoke
  anlamı veremez. Old artifact or restore newer negative floor'ı temizemez.

### 5.4 File upload ve quarantine

Static, BFF, SSR veya container seçiminden bağımsız olarak browser direct public object write yapamaz. Upload:

1. private quarantine + short-lived exact-scope handle;
2. declared/observed type, size, archive nesting/decompression/traversal, malformed/polyglot, digest and duplicate;
3. URL SSRF/private network/redirect/scheme/host/time/resource policy;
4. scan/render/OCR/AI/derivative isolation, lineage and most-restrictive classification;
5. `OBJECT_QUARANTINE`/partial/orphan/reconcile states;
6. manifest/approval/API gate before active/public use;
7. object bytes/metadata/backup/restore/clean-room cross-plane evidence.

Upload success, preview, scan completion veya HTTP 2xx technical correctness/official evidence değildir.

## 6. Operability, outage, deploy, privacy ve cost tie-break

### 6.1 API correlation ve failure semantics

Her mode aynı state dictionary'yi göstermeli:

| Olay | UI/API sonucu | Yasak inference |
|---|---|---|
| Browser/API timeout veya response loss | `OUTCOME_UNKNOWN`; same-ID status lookup, no blind duplicate | Timeout = failed/success |
| API unavailable | `SERVICE_UNAVAILABLE`; safe history/read only with timestamp, positive hold | Cached role/currentness |
| Role/epoch/object/release change | `DENIED`/`HELD`/`DEPLOYMENT_HELD`; draft/evidence preserved, re-review | Old tab/button = authority |
| Object upload/scan incomplete | `OBJECT_QUARANTINE`/`PARTIAL/RECONCILING` | Preview/scan = approved evidence |
| Schema/API/message/client mismatch | `DEPLOYMENT_HELD`; forward recovery | Green health = compatible product |
| Audit/fallback unavailable | `AUDIT_HELD`; no positive high-consequence effect | Platform log/audit intent = protected receipt |
| Host/DNS/TLS/account/quota incident | `SERVICE_UNAVAILABLE`/`ACCOUNT_HELD`/`BILLING_HELD`; external support owner | Owner SQL/SSH/console repair |

### 6.2 Deploy, rollback ve supply chain

Her frontend release exact reviewed source, lockfile, dependency closure/SBOM, build inputs, artifact digest/provenance,
independent verification, approval/signature, client capability and compatibility graph'i bağlar:

```text
web release/artifact
  + API contract / DB schema-migration / config generation
  + queue-worker message generation / drain
  + content-object-package manifest / negative floor
  + session-security epoch / revocation generation
  + DNS/TLS / cache-service-worker / observability / support
```

Rollback yalnız current, compatible, not-recalled predecessor'a yeni guarded web event'tir. API/data/schema/audit/
queue/object/negative-floor rollback'i değildir. Managed provider rollback, image tag, static symlink veya host dashboard
bu graph'i atlayamaz. Mismatch `DEPLOYMENT_HELD`; source untouched clean-room acceptance öncesi cutover yok.

### 6.3 Logs/privacy/account/support

- Browser, CDN, SSR/edge, BFF/container, worker, CSP report, source map ve analytics log'ları allowlist correlation /
  operation / release / state / bounded scope-reference taşır; token, cookie, PII, private file bytes, raw headers,
  secret ve raw audit payload taşımaz.
- Operational log protected product audit değildir. Audit retention/legal hold, debug-log deletion/export, support
  access and disclosure event separately authorized/auditedir.
- Managed static bile account/legal owner, billing/quota, domain/DNS/TLS, provider support, build and CDN incident
  dependency taşır. BFF/edge/container bunlara runtime/region/secret/worker/support zinciri ekler.
- Owner yalnız plain-language `approve / hold / stop / payment / legal-support / request-support` kararı verir.
  Account owner, provider support, audit/floor custodian, recovery verifier ve emergency-negative actor rollerinin
  bağımsızlığı/last-admin yolu ayrıca kanıtlanır.

### 6.4 Normalized safe TCO

Dört mode ve dört family aynı BOM row'larını ve horizon'ları kullanır:

| BOM grubu | Managed static | BFF/SSR/edge | Container | Zorunlu sorular |
|---|---|---|---|---|
| Web/build/CDN/runtime | Artifact/build/preview/CDN/egress | Server/edge CPU/request/cold start/egress | Instance/image/registry/proxy/capacity | Free path, unit/quota, overage, hard cap, stop |
| Shared API/data/object/auth | Ayrı fakat zorunlu | Aynı + server traffic | Aynı + network/pooler | IO/bytes/ops/region/backup/object ayrı mı? |
| Audit/floor/queue/object safety | Fallback/log/scan/backup/restore | Runtime/worker/cache adjunctları | Queue/worker/storage/ops | Protected custody, long-job, quarantine, DLQ |
| Security/a11y/privacy | Browser/AT/CSP/CORS test | SSR/headers/secret/SSRF test | Proxy/patch/log/secret test | Mandatory evidence, retention, subprocessors |
| Support/account/incident | CDN/domain/API support | BFF/edge/API/provider support | Host/DNS/TLS/API/recovery support | Owner action, SLA, external people |
| Restore/exit | Clean static host + API | BFF/edge bindings/config | Image/base/runtime/queue/host | Isolated import, source untouched, dual-run |

Her satır `mandatory / deferrable / optional / scale-triggered`, current official date/plan/region/unit/quota/overage,
tax/FX/card uncertainty, stop state ve normal/incident/upgrade/restore/exit etkisi taşımalıdır. TRY 2,000–3,000/ay
planning ceiling'dir; purchase authority değildir. Mandatory assurance bu tavana sığmıyorsa `BILLING_HELD/HELD`,
security/continuity/a11y/exit standardını düşürmek yoktur.

## 7. Clean-room exit tie-break

Default static artifact'in exit'i en kolay görünebilir; bu yalnız UI bytes'ını taşımaktır. Her mode/family için isolated,
quarantined, source-untouched acceptance aşağıdaki plane'leri import/reconcile etmelidir:

1. current/history/provenance/applicability and claim/content meaning;
2. operation ledger/status/conflict/tombstone/outbox and accepted-operation floor;
3. release/package/artifact/schema/config/message/client capability generations;
4. provider-qualified principal, policy/grant/competence, session/security epoch/recovery state;
5. object bytes + digest/lineage/classification/retention/disclosure + quarantine/handle state;
6. protected audit/fallback/floor and incident/impact graph;
7. queue pending/DLQ/lease, runtime artifact, secret reissue and DNS/TLS cutover;
8. cache/SW/headers/CSP/CSRF/session behavior, logs/metrics/correlation and owner/support runbook.

Old revoke/recall/delete/suspension/accepted operation veya newer negative floor dirilemez; new valid data silent
rollback ile kaybolamaz. Missing plane `EXPORT_PARTIAL`/`RESTORE_QUARANTINE`; provider clone, `dist`, image, static
artifact veya DNS alias tek başına clean-room başarı değildir.

## 8. No-code tie-break evidence sırası

Bir sonraki ADR öncesi tüm family × mode kombinasyonları için aynı intent/fixture ile:

1. `WEB-TASK-001..003` ve dört-way audit'in common context/oracle'ları; dense/component/AI-collision görevleri aynı
   output schema ile;
2. route × mode matrix: static/CSR/SSR/hybrid/edge/container; session/cookie/token, CSRF/CORS/origin, XSS/CSP/Trusted
   Types, API correlation, no-store/cache/SW, stale tab/epoch and response loss;
3. direct API/BOLA/IDOR/provider-console/signed-handle negative paths;
4. keyboard/AT/zoom/Turkish/narrow/browser storage/network/dense table/diff/provenance graph;
5. interrupted/duplicate/malicious upload, SSRF/archive/preview/derivative/handle/restore quarantine;
6. API N/N−1/schema/message/config/release/negative-floor, immutable artifact/SBOM/provenance and guarded rollback;
7. DNS/TLS/host/account/quota/support outage, owner-readable safe stop, external recovery/negative authority;
8. privacy/redaction/retention/legal hold/subprocessor and correlation IDs;
9. normalized normal/incident/upgrade/restore/exit BOM with cap/overage/stop;
10. source-untouched clean-room import, anti-resurrection, dual-run/cutover and independent acceptance.

Framework popularity, React AI familiarity, Angular LTS label, Nuxt/Svelte rendering capability, one-browser simulation,
component-library claim, provider dashboard, green health or headline price bu evidence'ların yerine geçemez.

## 9. Final disposition

### Render/hosting

- **Managed static SPA/CDN + API:** `CONDITIONAL DEFAULT / HELD` — Internal app SEO'suz olduğu için en düşük authority/
  runtime yüzeyi; strict session/CORS/CSRF/cache/upload/outage/exit kanıtı olmadan açılmaz.
- **Same-origin server-assisted shell/BFF:** `HELD / SECONDARY` — static split security contract'ı kapanmazsa yeniden
  açılabilir; BFF hiçbir zaman second authority veya canonical cache değildir.
- **Managed serverless/edge SSR:** `HELD / ROUTE-SPECIFIC EXCEPTION` — SEO yok; somut initial-load/proxy/a11y gerekçesi,
  private payload/cache, edge limits, support/cost/exit kanıtı olmadan default değildir.
- **Portable/managed Node container:** `HELD / CHALLENGER` — exit sinyali vardır; owner-debug, proxy/TLS/patch/log/
  restore/queue/support yükü kapanmadan static default'a otomatik fallback değildir.

### Frontend family

- React Vite/static, Next where needed, Angular, Vue/Nuxt ve Svelte/SvelteKit: **eşit `HELD`; winner yok**.
- Artifact shape benzerliği framework/library/AT/security/upgrade/owner/exit kanıtını birleştirmez.
- React/Next AI familiarity ve Angular LTS, Vue/Nuxt universal veya SvelteKit adapter capability'si tie-break sonucu
  değildir.

### Overall hüküm

**`HELD — CONDITIONAL SIMPLEST DEFAULT IDENTIFIED / NO FRAMEWORK OR PROVIDER WINNER / ADR NOT READY`.**

Önerilen default yalnız şu şekilde kayıt altına alınabilir: “Public SEO gerektirmeyen authenticated Internal Operations
web için CSR-first static artifact/CDN + Kavriva API ilk araştırma yönüdür; SSR/BFF/edge/container route-specific
kanıt yoksa açılmaz; service worker privileged/offline authority değildir.” Bu cümle React, Angular, Vue/Nuxt veya
Svelte/SvelteKit seçmez; exact host, session protocol, domain, provider veya plan seçmez.

Static default'un ortak gate'lerinden biri kapanmazsa olumlu standardı düşürmek veya otomatik BFF/SSR/container seçmek
yoktur. İlgili capability `HELD`; doğrudan authority bypass, stale positive authority, unsafe upload/quarantine,
effect-before-audit, incompatible rollback, owner technical repair, unbounded spend veya unsafe clean-room exit gerçek
kanıtta görülürse ilgili family × mode `REJECT-IF-UNMITIGATED` olur. Diğer mode veya framework otomatik winner değildir.

**No account, purchase, provider, exact framework/version, code, prototype, deployment, Phase-5 ADR veya Gate 4 → 5
transition is approved by this tie-break.**
