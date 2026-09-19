# DEBATE-012 — Internal Operations web component-ecosystem tie-break

**Durum:** `HELD` — no-code research closure; winner yok.  
**Tarih/snapshot:** 2026-09-19.  
**Kapsam:** React/Next, Vue/Nuxt, Svelte/SvelteKit ve Angular ailelerinde kritik UI capability/dependency kapanışı, managed-hosting ile portable static/container sınırı ve sahibisiz AI-operated işletme TCO'su.  
**Yetki sınırı:** UI/framework, component, browser cache/service-worker, host console veya generic data API Kavriva API'nin canonical authority'si değildir. API; actor/tenant/scope, security epoch, generation, operation outcome, audit ve object quarantine kararlarının tek ürün otoritesidir.

## 1. Tie-break kararı

Bu belge bir framework seçimi yapmaz. Dört aile de aynı product fixture, aynı API authority, aynı browser/AT kabul standardı, aynı stale-session/lost-outcome oracle'ı, aynı upgrade/rollback/clean-exit ve aynı no-owner handoff sözleşmesiyle `HELD` kalır.

Bir ailenin daha geniş component kataloğuna sahip olması capability kanıtı değildir. Aşağıdakiler ortak veya framework-neutral paketlerle sağlanıyorsa bunlar adaylar arasında sahte ayrıştırma olarak sayılmaz:

- dense table/virtualization için ortak data/virtualization motoru;
- editor/diff veya graph için ortak JavaScript motoru;
- schema validation, `Intl`, Playwright/Cypress, Storybook/visual artifact ve OpenTelemetry/Sentry gibi ortak araçlar;
- hosted auth, error-monitoring, visual-regression veya grid enterprise planı.

Framework-native avantaj yalnızca resmi doküman, exact lockfile ve aynı kabul fixture'ı ile capability'nin gerçekten kapsandığı gösterilirse ayrı yazılabilir. Native kısım da API authz, audit, outcome, quarantine veya clean-room exit'in yerine geçmez.

### 1.1 Kanıt dili

| Etiket | Anlam |
|---|---|
| `ESTABLISHED` | Okunan birincil framework dokümanı veya önceki DEBATE-012 denetimi tarafından açıkça gösterilen sınırlı mekanizma. |
| `PARTIAL` | Framework mekanizması vardır; product contract veya üçüncü taraf closure'ı yoktur. |
| `HELD` | Exact package/version/license/support/hosting/AT/cost kanıtı olmadan kabul edilmeyen capability veya karar. |
| `INFERRED` | Mimari işletme sonucu; framework guarantee'si değildir ve ayrıca test ister. |

Bu nedenle “free”, “production-ready”, “accessible”, “portable”, “supported”, “managed” ve “zero-ops” ifadeleri exact BOM, policy, test ve runbook olmadan sonuç olarak kullanılmaz.

## 2. Okunan bağlam ve değişmeyen sınırlar

Bu tie-break, aşağıdaki mevcut girdilerin bulgularını birleştirir; bunları yeniden puanlamaz:

| Girdi | Bu belgeye taşınan sonuç |
|---|---|
| `DEBATE-012__INTERNAL_WEB_PRIMARY_RESEARCH.md` | Dört framework'ün resmi render/form/accessibility/testing/security/deploy/upgrade sınırları; framework-neutral capability closure'ının açık kalması. |
| `DEBATE-012__INTERNAL_WEB_MANAGER_PROPOSAL.md` | API authority, static/container/managed boundary, equal task fixture, owner-readable cost ve Phase-5 evidence gate. |
| `DEBATE-012__REVIEW_A_ARCHITECTURE_ACCESSIBILITY.md` | Dense workspace, keyboard/AT, responsive behavior, design consistency, component closure ve portability kanıt eksikleri. |
| `DEBATE-012__REVIEW_B_SECURITY_OPERABILITY.md` | Direct API bypass, CSRF/XSS/CSP, session/epoch, response loss, cache/SW, quarantine, supply-chain, outage, quota, clean-room ve TCO hard gate'leri. |
| `DEBATE-012__TASK_SIM_WEB_001.md` | Evidence Review Workspace, Stale Session/Lost Outcome ve Upgrade/Rollback/Clean Exit task'ları; her aday için sonuç `HELD`. |
| `DEBATE-012__FOUR_WAY_EQUIVALENCE_AUDIT.md` | Vue/Nuxt ve Svelte/SvelteKit'in aynı task/context pack ile parity'si; hidden dependency ve adapter closure'ının eşit denetimi. |
| `DEBATE-012__INTERNAL_WEB_FAILURE_TCO_RESEARCH.md` | Frontend failure-mode ve normal/incident/upgrade/exit TCO şekilleri; bu belgede component/hosting bağımlılıklarına uygulanır. |

Değişmeyen product oracle'ları:

1. Render edilmiş state, form success, route middleware, SSR payload, cache, service worker, auth helper, host dashboard veya HTTP 2xx canonical commit değildir.
2. Stale role/epoch, changed fingerprint veya API N/N-1 uyumsuzluğu `CONFLICT`/`HELD` yoludur.
3. Response loss/timeout guessed success veya guessed failure değildir; aynı operation ID ile disclosure-safe status lookup yapılır ve sonuç `OUTCOME_UNKNOWN` kalabilir.
4. Dosya upload/preview/download önce type/size/hash/tenant/scope, quarantine, malware/content policy ve restore evidence ister; frontend component'i quarantine authority değildir.
5. Eski bundle, cache veya service worker revoked/recall/deleted/accepted truth'u geri getiremez; browser invalidation tek başına recovery değildir.

## 3. Exact capability/dependency closure matrisi

Kısaltmalar: `F` = framework-owned mekanizma; `F-P` = framework-owned ama partial; `TP` = third-party veya ortak paket; `H` = closure kanıtı tutuldu. “Framework-owned” burada framework'ün resmi API'sini belirtir; package'ın iyi olması veya çok kullanılması anlamına gelmez.

| Kritik capability | React + Next | Vue + Nuxt | Svelte + SvelteKit | Angular | Tie-break sonucu |
|---|---|---|---|---|---|
| **Dense data grid / virtualization**: server pagination/filter/sort, saved view, column visibility, bulk action, row/column keyboard, sticky/frozen cells, large dataset, Turkish/long labels, selection/conflict state | `F-P`: React DOM, Next render/data boundary; grid/virtualization `TP/H` | `F-P`: Vue rendering/Nuxt data boundary; grid/virtualization `TP/H` | `F-P`: compiler/render/load boundary; grid/virtualization `TP/H` | `F-P`: CDK primitives may help; full grid/virtualization still `TP/H` | Hiçbir aile full dense grid closure'ı sunmuş sayılmaz. Shared engine seçilirse ayrıştırma sıfırlanır; semantic virtualization ve AT kanıtı ayrıca gerekir. |
| **Accessible primitives**: dialog/menu/combobox/focus trap/return/live status/table/graph alternative/zoom/reduced motion | `F-P`: ARIA/DOM ve lint; complete primitive `TP/H` | `F-P`: Vue guidance/announcer; complete primitive `TP/H` | `F-P`: compiler warnings, route announcement/focus; complete primitive `TP/H` | `F`: CDK/Aria pattern'leri daha fazla native coverage; WCAG acceptance yine `TP/H` + real AT | Angular'ın native surface'i wrapper işini azaltabilir, fakat product accessibility pass'i veya grid/graph semantiğini kapatmaz. |
| **Forms / validation / mutation**: field state, async validation, dirty/unsaved warning, idempotency, approval/review/publish/recall | `F-P`: React Actions/form status; server validation/authz/audit `API`; schema/form package `TP/H` | `F-P`: `v-model`/reactivity; server validation/authz/audit `API`; form package `TP/H` | `F-P`: form actions/enhance; server validation/authz/audit `API`; form package `TP/H` | `F`: Reactive Forms/validators/form state; server validation/authz/audit still `API` | Angular closes client form mechanics more directly; none closes commit authority. Shared schema and server contract erase most family separation. |
| **Editor / diff**: large text, syntax/highlight, worker/CSP, diff semantics, keyboard, read-only/compare, conflict markers | Framework-owned closure yok; editor/diff engine and wrapper `TP/H` | Yok; engine/wrapper `TP/H` | Yok; engine/wrapper `TP/H` | Yok; engine/wrapper `TP/H` | Common engine (ör. browser editor/diff runtime) kullanılırsa wrapper, worker, CSP, bundle ve AT riskleri her ailede yeniden ölçülür. |
| **Graph**: provenance/impact traversal, zoom/pan, keyboard/linear alternative, large graph, focus and non-color status | Framework-owned closure yok; graph engine `TP/H` | Yok; graph engine `TP/H` | Yok; graph engine `TP/H` | Yok; graph engine `TP/H` | Graph library veya framework wrapper'ı API lineage/audit authority değildir; linear fallback ve screen-reader fixture'sı zorunludur. |
| **i18n / Turkish**: runtime locale, plural/date/number, long labels, validation/error messages, search/sort, RTL/locale fallback | `F-P`: browser `Intl`; runtime message catalog `TP/H` | `F-P`: `Intl`; runtime message catalog `TP/H` | `F-P`: `Intl`; runtime message catalog `TP/H` | `F-P`: Angular i18n ağırlıkla build/compile path; runtime switch/message catalog `TP/H` | `Intl` ortak altyapıdır; Turkish UI message ownership, locale data, extraction, fallback, dates and API error mapping candidate ayrımı değildir. |
| **Testing / E2E**: unit/component/integration, browser/AT, stale/lost outcome, upload/quarantine, API N/N-1, deploy/rollback | Official docs test layers; React-specific test libs `TP/H`; Playwright/Cypress ortak `TP/H` | Vue Test Utils/Nuxt utility + common E2E; exact versions `H` | Vitest/Playwright ecosystem; exact fixture/adapter `H` | `F-P`: TestBed/CLI/Vitest path; common E2E/AT still `TP/H` | Test toolünün varlığı test sonucu değildir. Aynı real-browser, AT, artifact and incident replay fixture'ı olmadan parity `HELD`. |
| **Visual regression / design system**: tokens, states, focus/disabled/error/held, Turkish expansion, responsive/dense, diffable artifacts | Framework-owned full design system yok; Storybook/visual runner/design tokens `TP/H` | Yok; `TP/H` | Yok; `TP/H` | Material/CDK optional native-adjacent surface; product system/visual baseline `TP/H` | Hosted visual service convenience/paid plan olabilir; local artifact ve clean-room export kanıtı olmadan portability `HELD`. |
| **Auth / session adapter**: cookie/token boundary, CSRF/Origin, CSP/XSS/Trusted Types, epoch/revoke, tenant/scope, step-up, status disclosure | React/Next docs auth guidance; provider/session adapter `TP/H`; API authority `F dışı` | Nuxt middleware/`useCookie`/Nitro transport aids; adapter `TP/H`; API authority dışı | hooks/load/actions/cookies aids; adapter `TP/H`; API authority dışı | HttpClient/XSRF client aid; no server auth authority; adapter `TP/H` | Hiçbir aile auth/session contract'ı framework-owned product authority olarak kapatmaz. Browser storage/JWT/cache/SSR data privileged truth değildir. |
| **Error monitoring**: browser/runtime/server correlation, operation ID, privacy/redaction, source maps, retention, alerting, outage mode | No framework-owned monitoring; Sentry/OTel-like `TP/H` | Yok; `TP/H` | Yok; `TP/H` | Yok; `TP/H` | SDK common olduğu için winner kanıtı değildir. Hosted ingestion, retention, residency, quota and account recovery cost'u ayrı BOM'dur. |

### 3.1 Capability closure'ın gerçek anlamı

Her satırın “kapanması” yalnızca component import edilmesi değildir. Aynı fixture'da şu kanıtların birlikte bulunması gerekir:

- semantik DOM/table headers, keyboard order, visible focus, focus return, screen-reader announcement, zoom/large text/reduced motion ve graph linear alternative;
- server pagination/filter/sort, saved view, virtualization threshold, bulk selection, stale row, changed fingerprint, partial result ve Turkish/long-label behavior;
- editor/diff large-payload, worker/CSP, untrusted text, conflict/unknown state ve read-only fallback;
- API-issued session/epoch/scope, CSRF/Origin/CSP/XSS/Trusted Types policy, direct API negative tests, same-ID outcome resolver, no-store/cache/SW rules;
- upload type/size/hash/quarantine/content-policy, preview sandbox, download scope and restore/incident handoff;
- browser support matrix, AT matrix, test artifact, visual baseline, source-map/privacy policy and owner-readable failure message.

Bunlardan biri package dokümanında yoksa package capability `HELD` kalır. “A11y warning yok” veya “component library'de grid var” tek başına kabul değildir.

## 4. Framework-owned ve common third-party sınırı

### 4.1 React + Next

React resmi yüzeyi UI/DOM, form action ergonomisi ve ARIA passthrough ile sınırlıdır. Next App Router, Server Component/streaming, Server Action, data-security, authentication, testing, CSP, self-hosting, standalone ve codemod dokümanları render/transport/build sınırlarını açıklar; bunlar API authz/audit, session epoch, object quarantine, operation outcome veya business commit değildir. Next support policy React'in policy'si değildir.

Kritik closure için React/React DOM/Next/compiler/bundler/TypeScript yanında form/schema, table/virtualization, editor/diff, graph, i18n, auth/session, monitoring, test/visual ve deployment adapter BOM'u gerekir. RSC/code-split avantajı interactive grid/chart/editor/form package'larının client boundary'si, hydration, CSP/worker, source-map ve browser/AT fixture'ı ile yeniden ölçülür. React ecosystem genişliği veya AI familiarity karar kanıtı değildir.

### 4.2 Vue + Nuxt

Vue resmi yüzeyi SFC/reactivity/forms/security/accessibility/testing/tooling/performance rehberidir. Nuxt/Nitro rendering, server routes/middleware, data fetching, cookies, route rules, deployment, testing, security modules ve upgrade/codemod sunar. `v-model`, Pinia/store, `useFetch`/`$fetch`, SSR payload, route middleware, `useCookie` ve routeRules cache transport/UX yardımcılarıdır; canonical authority, server authz, audit veya commit değildir.

Vue/Nuxt closure'ı Vue/Nuxt/Nitro/Vue Router/Pinia/Vite/TypeScript/Node, UI/grid/editor/graph/form/validation/i18n/auth/security/test/monitoring modules, adapter/host ve route-by-route render/cache policy'sini birlikte pinlemelidir. Nuxt release/support horizon, module compatibility, SSR payload/cache/SW, serverless/edge adapter ve clean-room proof kapanmadan “modüler” veya “portable” iddiası `HELD`dir.

### 4.3 Svelte + SvelteKit

Svelte compiler accessibility warnings, SvelteKit load/page options, server hooks, form actions, auth/session, accessibility, performance, adapters and testing package list sağlar. Bu mekanizmalar semantic app behavior'a yardım eder; `locals`, cookie/JWT, load result, action success, serialized data, adapter veya compiler warning API authority değildir.

Closure; Svelte/SvelteKit/Vite/Node/TypeScript/compiler/adapter yanında form/validation, table/grid, editor/diff, graph, i18n, auth/session, test/visual and monitoring packagesını exact lock/SBOM ile doğrulamalıdır. SvelteKit support/LTS matrix, adapter parity, action/load/hooks/serialization, major migration ve remote-form boundary'si açık kaldığı için package listesi eşdeğerlik veya portability kanıtı değildir.

### 4.4 Angular

Angular framework/CLI/compiler, Reactive Forms/validators, HttpClient/XSRF client behavior, CDK/Aria, TestBed/CLI testing, build budgets, SSR/hydration, deployment and `ng update` resmi surface'i diğer üç aileden daha fazla native mekanizma taşır. Bu, Angular'ın dense grid, full editor/diff, graph, runtime i18n catalog, auth/session provider, error monitoring, enterprise license/support veya business API authority sağladığı anlamına gelmez.

Angular closure'ı Angular core/CLI/compiler/CDK/Aria/Material (seçildiyse), RxJS, Node/TypeScript, grid/editor/graph/form/i18n/auth/security/test/visual/monitoring packagesı, SSR adapter ve host BOM'udur. Angular LTS framework/CLI desteği third-party grid/auth/material/monitoring paketlerinin aynı tarihte uyumlu veya destekli olduğunu kanıtlamaz. Native Forms/Aria/TestBed wrapper işini azaltabilir; capability acceptance, AT and clean-room evidence gereksinimi değişmez.

## 5. License, free/paid, support ve release compatibility

Bu çalışmada exact component package/version seçilmediği için package-level license, paid tier, support SLA, data residency, seat/user/row/build/event quota ve current price iddiaları **`HELD`**dir. Core framework dokümanlarının veya npm/GitHub package sayfasının bulunması tek başına ürünün exact lockfile closure'ını kanıtlamaz.

### 5.1 Cost model tablosu

| Closure sınıfı | Tipik model | Ücretsiz/OSS varsayımının sınırı | Exact evidence gate |
|---|---|---|---|
| Framework/runtime/compiler | Genellikle public OSS distribution; support window/version policy ayrı | OSS license, security patch, Node/TS/compiler compatibility ve owner time yine maliyettir | exact version, source license, support matrix, SBOM/advisory |
| Dense grid | Community/open-source veya enterprise feature/tier olabilir | Virtualization, export, grouping, keyboard/AT, support ve upgrade package'ı ayrı olabilir | same fixture benchmark, semantic/AT proof, package license, paid feature map |
| Accessible primitives/design system | Native partial surface + family-specific/headless package veya internal wrapper | “ARIA props” ve storybook component'i WCAG/product acceptance değildir | DOM/AT fixture, wrapper ownership, license/support, visual artifact |
| Forms/validation | Native partial/full forms + common schema veya family package | Client validation server authority değildir; async/locale/error mapping engineering cost'tur | schema BOM, API validation, i18n and replay/duplicate tests |
| Editor/diff/graph | Common engine + framework wrapper; bazı pro features commercial olabilir | Worker/CSP, bundle, large data, graph accessibility, export and security review ayrı | engine/wrapper matrix, license, browser/AT/large fixture, exit rebuild |
| i18n/Turkish | Browser `Intl` + message catalog/runtime package | `Intl` translation ownership, plural/message extraction, date/error consistency sağlamaz | Turkish long-label/locale fixture, catalog ownership, fallback and license |
| Test/E2E/visual | Open-source runner; hosted dashboard/artifact may be paid | CI minutes, browser binaries, AT lab, retention, visual SaaS quota and source-map privacy | reproducible local artifact, quota/price, retention/export, browser matrix |
| Auth/session/monitoring | Provider/SDK veya hosted service; common API contract possible | hosted auth/monitoring account, outage, quota, retention/residency and exit burden | provider-neutral protocol, cost/SLA/data policy, self-host/export rehearsal |
| Hosting/adapter | managed convenience or portable static/container | managed pricing does not include failure/debug/exit; static does not carry private authority | outage/quota/restore/clean-room/rollback evidence |

İki yanlış eşitleme özellikle yasaktır:

1. **“OSS = sıfır maliyet” yanlışlığı:** lisans ücreti yoksa bile lockfile/SBOM, security patch, browser/AT, visual baseline, incident, support ve clean-room emekleri vardır.
2. **“Managed = no-ops” yanlışlığı:** provider console deploy kolaylığı; session/cache/CSP/DNS/TLS, API compatibility, quota, outage, account recovery ve exit sorumluluğunu silmez.

### 5.2 Bakım ve release closure

Framework release policy ile component closure ayrı BOM'dur:

- React core ve Next support policy ayrı izlenir; React/React DOM/Next/compiler/bundler/RSC ve selected packages birlikte upgrade edilir.
- Vue core release cycle ile Nuxt/Nitro/Vite/modules/Pinia/Vue Router compatibility aynı şey değildir.
- Svelte compiler, SvelteKit, Vite, adapter ve pre-release/major migration için tek contract yoksa release `HELD`dir.
- Angular Active/LTS, Angular CLI/CDK/Material/RxJS ve Node/TypeScript compatibility'yi kapsar; third-party grid/editor/auth/monitoring/support window'larını kapsamaz.

Her aile için minimum release manifest:

`framework → renderer/compiler → router/runtime → Node/TypeScript → bundler/adapter → form/schema → grid/virtual → editor/diff → graph → i18n → auth/session/security → test/E2E/visual → monitoring → host/runtime`.

Her node için exact version, release date, support end, license, transitive SBOM, known advisory, migration/codemod, API/schema compatibility, rollback artifact ve exit procedure yoksa version update yapılmaz. Popularity, download count, AI training familiarity veya “çok wrapper var” release evidence'i değildir.

## 6. Managed hosting ve portable static/container sınırı

| Hosting boundary | Sağlayabileceği operasyon kolaylığı | Sağlayamayacağı / ayrıca kanıtlanması gerekenler | Exit/wrapper riski |
|---|---|---|---|
| **Managed frontend/edge/platform** | build/deploy/preview, CDN/cache, TLS/DNS integration, provider metrics; framework adapter convenience | API authority, session/epoch, CSRF/CSP/XSS, object quarantine, DB/schema compatibility, response-loss resolver, quota/outage/account recovery | provider adapter, route/cache semantics, env/secret/log/source-map coupling; console-only recovery clean-room'a giremez |
| **Portable static artifact** | CDN/object host ile düşük runtime surface; rebuildable HTML/JS/CSS | private authz, server mutation/action, long job, upload/quarantine, secure API proxy, server session, dynamic approval/audit | static export feature loss; API/config/header/asset/SW/cache/session runbook ayrı. “Static” dependency-free veya offline-authoritative değildir |
| **Portable container/server runtime** | Node/container/runtime portability, explicit process and env boundary; managed hosttan çıkış kolaylaşır | TLS/DNS/region, autoscale, queue/worker, cache, secrets, logs/redaction, backups, monitoring, patching, incident/on-call | runtime image, adapter/preset, Node/TS/OS, build artifact, proxy/header/cookie and host config compatibility; ops burden owner/AI'ye taşınır |
| **Self-host / clean-room** | provider account'tan bağımsız tekrar build/cutover; evidence-based exit | source/lock/SBOM/build recipe, artifact provenance, secrets, DNS/TLS, API/object/audit history, cache/SW purge, monitoring and support | framework wrapper'ı kaldırmak yetmez; server/API/identity/observability/data authority import ve anti-resurrection proof gerekir |

Framework-specific boundary hints:

- Next static export, Server Components/Actions, cache and standalone output; Nuxt routeRules/Nitro/presets; SvelteKit `ssr/csr/prerender`, `load/actions/hooks`, adapters; Angular SSR/hydration/CLI output — bunların her biri route-by-route artifact/runtime contract'ı ister.
- Adapter veya host değişikliği UI package değişikliği kadar yüksek olabilir: cookie/header forwarding, CSP nonce, cache key, streaming/hydration, source maps, file/preview proxy, API N/N-1 ve status disclosure aynı anda replay edilmelidir.
- Aynı component engine dört ailede kullanılsa bile wrapper lifecycle, event/focus/slot/directive, SSR/hydration, style isolation, worker loading ve testing adapter maliyeti family-specific olabilir. Bu fark ölçülmeden “common package ile kapanır” da denemez.

## 7. Normal / incident / upgrade / exit TCO şekilleri

Sayısal fiyat verilmemiştir; input yoksa karşılaştırmalı sayı üretmek yanıltıcı olur. Normalize edilen şekil aşağıdadır:

`TCO = normal capability closure + incident reserve + upgrade rehearsal + exit reserve + no-owner escalation`

| Durum | TCO driver'ları | No-owner-debug etkisi | Kanıt/stop line |
|---|---|---|---|
| **Normal operation** | exact BOM/SBOM, license/advisory watch, CI/browser/AT/visual runs, grid/editor/graph payload, build/cache/CDN, monitoring events, quota/egress, runbook upkeep | Framework/package/host owner bulunamazsa küçük version/cache/header sapması bile specialist escalation'a dönüşür | monthly dependency/release/visual/AT evidence; quota, privacy and owner handoff visible |
| **Incident** | stale tab/role, CSRF/XSS/CSP, direct API bypass, lost response, optimistic false success, old cache/SW, upload/quarantine, browser/AT, large table/diff/graph, DNS/TLS/host outage | UI mechanism'i canonical sanan AI guessed success veya blind retry üretebilir; forensic context, operation ID, artifact, scope ve audit missing ise recovery maliyeti katlanır | status `OUTCOME_UNKNOWN`/`HELD`; same-ID resolver, disclosure-safe logs, safe stop/support handoff; no broad debug guess |
| **Upgrade** | framework/runtime/compiler, adapter, grid/editor/graph, auth/session, i18n, monitoring, browser/AT, API N/N-1, schema/config/cache/SW, visual baselines | Version compatibility graph'i owner yoksa release/rollback kararını veremez; migration/codemod başarı mesajı product acceptance değildir | exact lock diff, SBOM/advisory, migration rehearsal, real-browser/AT/visual + incident replay, guarded promote/rollback |
| **Exit / clean-room** | source/lock/SBOM/license, build recipe, artifact/provenance, env/headers/secrets, DNS/TLS, session/auth, API/object/audit/floor history, cache/SW invalidation, monitoring/export, dual-run/cutover | Provider/framework wrapper bilgisi yalnız kişideyse exit “source copy” seviyesinde kalır; anti-resurrection ve authority import kanıtlanamaz | fresh environment rebuild, no account dependency, API/object/audit/history validation, cache/session purge, rollback and handoff artifacts |

Managed ortam normal build time'ını düşürebilir; incident, account recovery, outage, quota ve exit reserve'sini sıfırlamaz. Portable container ops line item'ını büyütebilir; provider lock-in ve clean-room uncertainty'sini azaltabilir. Static artifact deploy cost'u azaltabilir; private mutation/auth/session/quarantine işini API ve supporting runtime'a iter. Bu trade-off'lar dört aday için aynı accounting boundary ile ölçülmeden winner çıkarılamaz.

## 8. No-owner AI task/context/collision closure

Teknik olmayan tek owner ve AI-operated işletmede capability kadar görev adreslenebilirliği önemlidir. Her component/adapter task'ı aşağıdaki pack olmadan başlatılamaz:

- task ID, candidate/family, exact lockfile ve changed package listesi;
- read/write/forbidden scope, API operation ID/status oracle, expected generation/security epoch;
- affected routes/components, render mode, cache/no-store/SW, cookie/header/CSP/CSRF policy;
- table/editor/graph/form/i18n/accessibility fixture, browser/AT target, visual artifact baseline;
- build artifact/provenance, SBOM/license/advisory, deploy/rollback version and API N/N-1 matrix;
- owner-readable success/held/unknown/failed output, next safe action and escalation handoff;
- collision lock: başka AI task'ının package, auth, route, adapter, service worker, schema, host config veya artifact'ına sessizce merge yok.

AI aşağıdaki davranışları yapamaz:

1. form action/transition/SSR payload/route middleware/cache hit'i accepted sayamaz;
2. response loss sonrası blind retry veya yeni operation ID üretemez;
3. stale role/epoch veya changed fingerprint'i optimistic success ile gizleyemez;
4. direct API/provider path, generic Data API/RPC/Storage veya host console'u authority yapamaz;
5. package popularity, framework familiarity, generated test count veya successful build'i accessibility/security/exit kanıtı sayamaz;
6. owner'dan Nitro hook, Svelte adapter, Next cache, Angular DI, service worker, DNS/TLS veya SQL debug'ı varsayamaz.

Handoff dili plain-language olmalıdır: `state = held/unknown/reconciling`, `operation ID`, `known scope`, `artifact/release`, `what was not changed`, `next safe action = status lookup / wait / support / stop`. Bu pack yoksa normal task bile `HELD`; incident ve exit otomatik `HELD`dir.

## 9. Evidence gates — final tie-break için gereken kapanış

| Gate | Required evidence | Failure disposition |
|---|---|---|
| `E-01 BOM/SBOM` | Four exact lockfiles; framework/runtime/compiler/bundler/adapter + capability packages; transitive SBOM; SPDX/license; advisory and provenance | `HELD`; no license/free/support claim |
| `E-02 Dense workspace` | Same large-table/diff/graph/form fixture; pagination/filter/sort/virtualization, selection, focus, Turkish labels and server states measured | `HELD`; no grid/editor/graph winner |
| `E-03 A11y/AT` | Real browser + keyboard + screen reader/AT, zoom/large text/reduced motion, focus/live-region/table/graph linear path, visual artifact | `HELD`; warnings/ARIA props insufficient |
| `E-04 Security/session` | CSRF/Origin/CSP/XSS/Trusted Types, storage/token policy, stale epoch/role, direct API negative, cache/SW, disclosure-safe status | `HELD`; framework/session helper not authority |
| `E-05 Outcome/reliability` | Lost response, timeout, duplicate, optimistic false success, same operation ID resolver, idempotency and audit/generation proof | `OUTCOME_UNKNOWN`/`HELD`; no blind retry |
| `E-06 File/data boundary` | Upload type/size/hash/quarantine/content policy, preview/download scope, large payload and redaction | `OBJECT_QUARANTINE`/`HELD`; component cannot approve object |
| `E-07 Test/visual` | Reproducible local E2E/AT/visual artifacts; hosted service optional and exportable; source-map/privacy policy | `HELD`; hosted account not sole evidence |
| `E-08 Release/rollback` | Framework + all third-party release matrix, migration/codemod rehearsal, API N/N-1/schema/config/SW/cache, immutable artifact promote/rollback | `UPGRADE_HELD`/`DEPLOYMENT_HELD` |
| `E-09 Host/outage` | Managed vs static vs container runbook; DNS/TLS, quota, region/egress, provider outage, session/cache invalidation, restore/support | `SERVICE_UNAVAILABLE`/`HELD` |
| `E-10 Exit` | Clean-room rebuild without provider account; source/lock/SBOM/build/config/headers/secrets/artifact/API/object/audit/floor/cache/session/monitoring import and anti-resurrection | `HELD`; source copy not exit |
| `E-11 Cost/support` | Normal/incident/upgrade/exit BOM; package license/paid tier/SLA/retention/residency/quota; owner and escalation time | No normalized score; `HELD` |
| `E-12 AI collision` | Task graph, scope, lock, artifact, reviewer, collision and no-owner handoff packs; same fixture across four families | `HELD`; generated code/build success irrelevant |

Bu gates kapanmadan dört satırın disposition'ı aynıdır:

| Aday | Disposition | Neden winner değil |
|---|---|---|
| React + Next | `HELD` | Core/Next surface güçlü olsa da grid/editor/graph/auth/monitoring/visual closure, wrapper support, license/price, adapter/exit ve no-owner evidence yok. |
| Vue + Nuxt | `HELD` | Reactive/Nitro/module surface capability değildir; routeRules/SSR/cache/module/support/adapter closure ve third-party package BOM açık. |
| Svelte + SvelteKit | `HELD` | Compiler/action/hooks/adapter surface faydalıdır; package/support/LTS/adapter/major/remote-form/exit closure açık. |
| Angular | `HELD` | Forms/CDK/Aria/TestBed native coverage bazı wrapper maliyetini azaltır; full grid/editor/graph/runtime i18n/auth/monitoring/license/support/exit ve API authority kapanmaz. |

## 10. Evidence ledger — mevcut birincil kaynaklar

Bu tie-break yeni package/account sonucu icat etmez; aşağıdaki mevcut resmi source ledger'larını kullanır:

- [React forms/actions and ARIA references](https://react.dev/blog/2024/12/05/react-19), [React common components/ARIA](https://react.dev/reference/react-dom/components/common)
- [Next support policy](https://nextjs.org/support-policy), [data security](https://nextjs.org/docs/app/guides/data-security), [authentication](https://nextjs.org/docs/app/guides/authentication), [accessibility](https://nextjs.org/docs/architecture/accessibility), [testing](https://nextjs.org/docs/app/guides/testing), [self-hosting](https://nextjs.org/docs/app/guides/self-hosting), [CSP](https://nextjs.org/docs/app/guides/content-security-policy), [codemods](https://nextjs.org/docs/app/guides/upgrading/codemods)
- [Vue forms](https://vuejs.org/guide/essentials/forms.html), [Vue accessibility](https://vuejs.org/guide/best-practices/accessibility), [Vue testing](https://vuejs.org/guide/scaling-up/testing), [Vue security](https://vuejs.org/guide/best-practices/security)
- [Nuxt rendering](https://nuxt.com/docs/4.x/guide/concepts/rendering), [server/Nitro](https://nuxt.com/docs/4.x/getting-started/server), [testing](https://nuxt.com/docs/4.x/getting-started/testing), [deployment](https://nuxt.com/docs/4.x/getting-started/deployment), [upgrade/codemods](https://nuxt.com/docs/4.x/getting-started/upgrade)
- [Svelte package/adapters index](https://svelte.dev/packages), [compiler accessibility warnings](https://svelte.dev/docs/svelte/compiler-warnings), [SvelteKit accessibility](https://svelte.dev/docs/kit/accessibility), [form actions](https://svelte.dev/docs/kit/form-actions), [auth/session](https://svelte.dev/docs/kit/auth), [adapter-node](https://svelte.dev/docs/kit/adapter-node)
- [Angular releases/support](https://angular.dev/reference/releases), [version compatibility](https://angular.dev/reference/versions), [forms](https://angular.dev/guide/forms), [security](https://angular.dev/best-practices/security), [Aria](https://angular.dev/guide/aria/overview), [testing](https://angular.dev/guide/testing), [end-to-end](https://angular.dev/tools/cli/end-to-end), [`ng update`](https://angular.dev/cli/update)

Package-level dense grid/editor/graph/i18n/auth/monitoring/visual choices, exact licenses/prices, release/support promises, managed-provider SLA/quota and current clean-room effort are **not closed by these framework sources**. They remain `HELD` until E-01–E-12 evidence is produced. Therefore this document records a tie-break boundary, not a recommendation or winner.

## 11. Final disposition

**Karar:** `DEBATE-012 component ecosystem tie-break = HELD / NO WINNER`.  
**Permitted next step:** Phase-5 may prepare the same no-code evidence packs and normalized cost template for all four families; it may not silently substitute a popular component catalog, hosted account, framework-native helper or generated test count for the gates above.  
**No code/account/winner:** This document creates no code, no account, no provider commitment and no candidate selection.
