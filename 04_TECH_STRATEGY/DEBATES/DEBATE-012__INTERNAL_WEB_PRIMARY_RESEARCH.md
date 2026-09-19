# DEBATE-012 — Kavriva Internal Operations web frontend birincil kaynak araştırması

Status: PHASE-4 RESEARCH / NO-CODE / NO ACCOUNT / NO PURCHASE / NO WINNER / ADR PENDING  
Date: 2026-09-19  
Research cut: 2026-09-19, Europe/Istanbul  
Scope: browser Internal Operations surface; React + Next.js, Vue + Nuxt, Svelte + SvelteKit, Angular; Remix/React Router yalnız referans  
Authority boundary: Kavriva API

Bu kayıt yalnızca framework'lerin ve ilgili resmi proje depolarının dokümantasyon, sürüm, destek ve
changelog kanıtlarına dayanır. Hesap açılmadı, ücretli plan incelenmedi, benchmark/prototype/yük testi
yapılmadı, kod yazılmadı ve aday seçilmedi. Maliyet bölümü yalnız maliyet şeklidir; fiyat veya satın alma
kararı değildir.

Evidence etiketleri:

- [CONFIRMED] Resmi belgenin açıkça söylediği davranış, sürüm veya destek durumu.
- [INFERRED] Resmi kanıtlardan Kavriva iş yüküne yapılan sınırlı çıkarım; sağlayıcı garantisi değildir.
- [OPEN] Bu kesitte üretim kararı için yeterli birincil kanıt yok.
- [HELD] Kanıt kapanana kadar bu capability veya mimari varsayım açılmaz.

## 1. Karar sorusu, kapsam ve değişmez authority sınırı

Karar sorusu, hangi JavaScript/TypeScript ailesinin daha popüler olduğu değildir:

> Kavriva Internal Operations'ın yoğun tablo/form/filtre ve approval-review ekranlarını; kullanıcıya
> güvenli, erişilebilir, ölçülebilir ve taşınabilir bir browser yüzeyi olarak hangi framework ailesi,
> Kavriva API'nin tek authority'sini bypass etmeden taşıyabilir?

Bu araştırma “kazanan” çıkarmaz. Dört aile aynı çalışma koşulları altında incelenmiş, hepsi `HELD` bırakılmıştır;
Remix/React Router yalnız sürüm ve mimari referanstır. Framework, hosting veya managed platform şu yetkilerin
yerine geçemez:

1. Kimlik doğrulama bağlamı, issuer/audience/algoritma/kid/JWKS rotation, session/security epoch.
2. Actor, role/grant, scope, competence, independence, resource ve resource version ile commit-time authorization.
3. Server validation, operation ID, payload fingerprint, idempotency, expected version/generation ve status lookup.
4. Canonical state, operation ledger, protected audit, publish/recall/approval kayıtları ve correlation ID.
5. Timeout veya ağ kesintisinde `OUTCOME_UNKNOWN`; kör retry veya UI'daki olumlu varsayım değil.
6. Durable queue/outbox/worker, retry/DLQ, duplicate delivery ve recovery semantiği.

React Server Component/Server Action, Nuxt Nitro endpoint/server middleware, SvelteKit `+page.server` action/hook
veya Angular SSR server output, yalnız browser ile Kavriva API arasındaki uygulama/transport katmanıdır. Bunlar
doğrudan database, provider Data API, local cache, cookie veya framework session'ını Kavriva authority yapmaz.
Browser her mutasyonda Kavriva API'ye gider; API güncel session/security epoch, scope, resource version ve
idempotency'yi tekrar doğrular. Framework içinde optimistic success, yetki/approval sonucu veya audit kaydı
üretilmez. [INFERRED] [HELD]

## 2. Yöntem ve ortak değerlendirme fixture'ı

Resmi kaynaklar aileler için aynı mercekten okunmuştur: release/support, SSR/SPA/SSG/server sınırları,
form ve data loading, accessibility sorumluluğu, test/build/tooling, CSP/CSRF/session, deployment portability,
bundle/performance, upgrade/codemod, ecosystem ve self-host/managed maliyet şekli. Bir ailenin resmi pazarlama
iddiası, diğerinin kanıtıymış gibi genişletilmemiştir.

Ortak Internal Operations fixture'ı:

- Dense table: server-side pagination/filter/sort, saved view, column visibility, keyboard navigation, bulk selection.
- Dense forms: validation, unsaved-change warning, idempotent submit, approval/review, publish/recall and rejection reason.
- Stale tab/multi-operator: aynı resource version üzerinde conflict, timeout, retry, `OUTCOME_UNKNOWN`, audit correlation.
- Browser constraints: slow network, tab restore, refresh, back/forward, screen reader, keyboard-only, reduced motion,
  responsive desktop/tablet, Turkish locale and long labels.
- Security: untrusted text/rendered content, CSP/nonce/Trusted Types, CSRF/XSRF, cookie/session rotation, server-only
  secret, trusted proxy and SSRF boundary.
- Operations: static/CDN, Node/container, serverless/edge and self-hosted exit ayrı ayrı ölçülür; managed host hesabı
  olmadan fiyat/region/SLA iddiası yapılmaz.

Bu fixture “framework kendi başına yapar” demek değildir. Her ailede API contract, domain state, authorization,
server validation, audit and transaction evidence Phase 5'te ayrıca kapanmalıdır.

## 3. 2026-09-19 sürüm ve destek snapshot'ı

| Aile | Bu kesitte kullanılan resmi baseline | Destek/release kanıtı | Bu kesitteki risk/uyarı | Disposition |
|---|---|---|---|---|
| React + Next.js | React 19.3 stable (2026-09-09); Next.js 16.3.3 Active LTS, Next.js 15.5.24 Maintenance LTS snapshot'ı | Next.js support policy: major başına Active LTS ve Maintenance LTS; Next 16 için Node.js >=20.9 | Next App Router React canary'lerini framework ile birlikte kullanır; React Server Functions/RSC bundler API'leri React minor'ları arasında semver garantili değildir | HELD |
| Vue + Nuxt | Vue 3.5.43 stable (2026-09-17); Vue 3.6.0-rc.9 pre-release (2026-09-18); Nuxt 4.5.2 docs snapshot, Nuxt 4.5.1 security patch | Vue minor'ları yaklaşık 3–6 ay aralığında, sabit takvim yok; Nuxt 4.5 resmi blogu Nuxt 3 EOL'u 2026-07-31 olarak bildiriyor | Vue 3.6 RC ve Nuxt modul/version closure production baseline değildir; Nuxt için bu kesitte Next/Angular kadar tek bir LTS tablosu bulunmadı | HELD |
| Svelte + SvelteKit | Svelte 5.56.8 stable; SvelteKit 2 stable documentation baseline | Resmi releases/package registry ve SvelteKit docs | SvelteKit 3.0.0-next.27 pre-release (2026-09-08); SvelteKit 3 production baseline olarak açılmadı, formal LTS matrisi bulunamadı | HELD |
| Angular | Angular 22 Active, released 2026-06-03; Active ~2027-06, LTS ~2028-06; Angular 21 LTS | Angular major yaklaşık 6 ay; 12 ay Active + 12 ay LTS; v2–19 unsupported | Node/TypeScript/RxJS compatibility matrix sürüm kapısını sıkılaştırır; Angular 22 baseline toolchain'e kilitlenmelidir | HELD |
| Remix / React Router (referans) | Remix 3 Release Candidate; stable planı 2026-10-02; React Router v8 duyurusu | Remix 3 RC resmi olarak pre-release ve dokümantasyon/security audit hâlâ kapanmamış olarak duyuruldu | 2026-09-19 tarihinde production finalist olamaz; yalnız React ekosistemi için referans | REFERENCE ONLY / HELD |

`Released`, `Active`, `LTS` ve `pre-release` ifadeleri resmi release/support sayfalarının bu tarihli fotoğrafıdır;
gelecekteki otomatik güncelleme sözü değildir. Exact lockfile, Node/TypeScript/browser matrix, security bulletin
watch ve upgrade prova testleri olmadan “destekli” kelimesi üretim garantisi sayılmaz. [OPEN]

## 4. Eşit capability karşılaştırması

Tablodaki `C` yalnız resmi belgede capability'nin bulunduğunu, `I` Kavriva iş yüküne uygulama çıkarımını,
`O` kapanmamış ayrıntıyı, `H` açılmaması gereken varsayımı gösterir. “Var” satırı domain correctness veya API
authority garantisi değildir.

| Kriter | React + Next.js | Vue + Nuxt | Svelte + SvelteKit | Angular |
|---|---|---|---|---|
| UI/component | C: React UI library; Next App Router | C: Vue SFC/Composition API; Nuxt app | C: Svelte compiler; SvelteKit framework | C: Angular component/DI/CLI |
| Form/mutation | C: React 19 Actions/forms; Next Server Actions; API boundary H | C: `v-model`, `useFetch`/`$fetch`; Nitro handlers; API boundary H | C: POST form actions, progressive enhancement; remote form functions experimental/H | C: reactive/template forms and validators; HttpClient; API boundary H |
| Load/data | C: Server Components, `fetch`, streaming, colocated load; DTO discipline H | C: `useFetch`/`useAsyncData` SSR payload; routeRules; header-forwarding H | C: `load`, server-only modules, serialized data; secret leakage H | C: app services/HttpClient, SSR transfer/hydration; cache/auth design H |
| Render boundary | C: SSR/stream/static/client; static export feature-limited | C: universal SSR default, CSR/SSG/hybrid/SWR/ISR | C: SSR/prerender/client per page/layout | C: CSR default, SSR/SSG/client per route, static output |
| Accessibility | C: ARIA pass-through + Next route announcer/lint; app WCAG owner | C: Vue WCAG guidance + Nuxt announcer; app owner | C: compile-time a11y warnings + focus/announcement; app owner | C: Angular Aria/CDK patterns; expertise/manual QA still required |
| Test/tooling | C: Jest/Vitest/Cypress/Playwright; async RSC E2E caveat | C: Vue Test Utils/Vitest/Cypress/Playwright; `@nuxt/test-utils` | C: Vite, Vitest/Playwright ecosystem; exact fixture remains to prove | C: CLI/Vitest + jsdom default, Karma supported, E2E options |
| Security primitives | C: Next data security, Server Action origin check, CSP guide; validation/authz app/API | C: Vue escaping/security guide; Nuxt safe head/cookie; optional module closure | C: server hooks/actions/cookies; CSP/CSRF integration app-owned/H | C: sanitization, AOT, CSP/Trusted Types nonce, XSRF client half |
| Portability | C: Node/Docker all features; static export limited; adapter API | C: Nitro Node/static/serverless/edge presets | C: adapter-node/static/cloud/edge packages | C: static/CDN; Node SSR; Web Request/Response non-Node path |
| Bundle/performance | C: RSC/streaming/code split/Turbopack; measure hydration/client payload | C: compiler/tree-shaking/Vite; hybrid route caching; payload control | C: compiler output, code split/preload/prerender; measure | C: esbuild/Vite, budgets, hydration/event replay; measure |
| Upgrade | C: `@next/codemod`, Next 16 migrations; React RSC pinning | C: Nuxt 4 codemod; Vue minor TS caveat; module matrix | C: Svelte/SvelteKit migration docs; SvelteKit 3 held | C: `ng update` schematics/migrations; old builder deprecation |
| Ecosystem closure | I: React packages plus Next/Vercel/adapter ecosystem | I: Vue Router/Pinia/Nitro/modules | I: adapters, Svelte packages, Vite ecosystem | I: Angular packages/CDK/RxJS/CLI coupling |
| Cost shape | I: static CDN, Node/container, adapter/managed host; no price | I: static CDN, Nitro server/edge; no price | I: static CDN, adapter host/Node/edge; no price | I: static CDN or SSR Node/container; no price |

Bu tablo eşdeğerlik için başlangıç kanıtıdır; hiçbir satır `PASS` anlamına gelmez. Form, session, CSRF veya SSR
capability'si, Kavriva API'nin canonical state/authorization/audit semantiğini devralmaz.

## 5. Aday A — React + Next.js

### 5.1 Kimlik, maturity ve release/support

- React resmi blogu React 19.3'ü 2026-09-09'da yayımlanmış stable sürüm olarak duyurur. View Transitions,
  Fragment Refs ve React DOM `browser` API'si gibi özellikler bu release'te güncellenmiştir. [CONFIRMED] [R1]
- React, UI kütüphanesi olarak routing, CSS, auth, data/cache veya deployment için tek bir platform sözleşmesi
  vermez. Bu boşlukta Next.js uygulama framework'ü olur; React core support için Next'in LTS tablosu ikame
  edilmemelidir. React core için bu araştırmada bağımsız, uzun süreli LTS matrisi bulunmadı. [OPEN] [R2]
- Next.js support policy Next 16.x'i Active LTS ve Next 15.x'i Maintenance LTS olarak tanımlar. Bu kesitte resmi
  release blog snapshot'ı Next 16.3.3'ü Active, Next 15.5.24'ü Maintenance security release çizgisinde gösterir.
  Active yeni feature ve bug fix; Maintenance critical bug/security fix eksenidir. [CONFIRMED] [N1][N2]
- Next 16 installation dokümanı Node.js 20.9 minimumunu, modern browser floor'larını ve create-next-app ile
  TypeScript/ESLint/Tailwind/App Router/Turbopack varsayılanlarını bildirir. App Router React canary release'lerini
  framework'e gömer; Pages Router package React kullanır. Bu, framework/React sürüm closure'ını lockfile ile birlikte
  yönetmeyi gerektirir. [CONFIRMED] [N3]
- React Server Functions React 19'da stable olsa da RSC bundler/framework API'lerinin React 19 minor'ları arasında
  semver garantisi olmadığı, bundler/framework için exact version veya Canary pin'inin önerildiği resmi docs'ta
  yazılıdır. [CONFIRMED] [R3] [HELD]

### 5.2 Render, server/client ve data boundary

- Next App Router layouts, Server Components, streaming ve colocated data fetching sağlar. React server render
  API'leri Node için `renderToPipeableStream`, Web Streams destekleyen browser/Deno/edge için
  `renderToReadableStream`, ayrıca static HTML API'lerini sunar. [CONFIRMED] [N4][R4]
- Next deploy docs Node server ve Docker'da tüm feature'ları, static export'ta ise server feature'larının
  çalışmadığını söyler. Static export CDN/S3/Nginx/Apache gibi statik sunuculara taşınabilir; adapter API farklı
  platformlar için vardır fakat üçüncü taraf adapter uyumluluğu platforma göre değişir. [CONFIRMED] [N5]
- Server Component server-only secret/DB/internal API'ye erişebilir, fakat secret veya güvenilmeyen DTO client
  bundle'ına geçirilmemelidir. Kavriva'da Server Component'in server'a yakın olması onu API authority yapmaz;
  canonical read/mutation Kavriva API'den gelmeli, component sadece güvenli DTO render etmelidir. [INFERRED] [N6]
- Static/SSR/CSR seçimi ekran/route bazında yapılabilir. Dense operasyon tablosu için server pagination ve
  filter request'i browser'dan API'ye veya güvenilir server adapter'a gider; browser cache'si authorization/epoch
  sonucu olarak kabul edilmez. [INFERRED] [HELD]

### 5.3 Forms, mutation ve session

- React 19 `<form action={...}>`, `useActionState`, `useFormStatus` ve Actions ile form submit/pending/error
  ergonomisi sağlar; uncontrolled form başarılı action sonrası reset olabilir. Bu UI lifecycle capability'sidir,
  commit/audit/authorization değildir. [CONFIRMED] [R5]
- Next Server Actions POST-only'dir; resmi data-security docs host/origin karşılaştırmasının CSRF riskini azalttığını,
  proxy için `allowedOrigins` bulunduğunu söyler. Yine de action içinde input validation ve authorization zorunludur;
  Route Handlers public endpoint sayılır. [CONFIRMED] [N7]
- Next resmi rehberi yeni projelerde server-only Data Access Layer, authorization ve safe DTO kullanımını önerir.
  Kavriva action/DAL, API'nin actor/session/role/scope/version/idempotency doğrulamasını tekrar çağırabilir; local
  `useActionState` veya UI optimistic state transaction sonucu değildir. [INFERRED] [N7]
- Auth guide authentication, session ve authorization ayrımını yapar ve auth library kullanımını güvenlik/sadelik
  için önerir; belirli bir identity provider veya Kavriva authority vermez. Session rotation/security epoch,
  replay, reauth ve revoke davranışları API sözleşmesinde kalır. [CONFIRMED] [N8] [HELD]

### 5.4 Accessibility

- React DOM ARIA attribute'larını HTML semantiğine yakın geçirir; input docs label ve accessible name önemini açıklar.
  React tek başına WCAG pass vermez. [CONFIRMED] [R6][R7]
- Next accessibility docs client-side route transitions için route announcer ve descriptive title; default
  `eslint-plugin-jsx-a11y` ile ARIA/role/alt gibi hataları bildirir. Keyboard focus order, table semantics, error
  association, contrast, reduced motion, screen-reader review ve gerçek browser/screen-reader QA uygulamanın
  sorumluluğudur. [CONFIRMED] [N9]
- Dense grid ve approval formunda virtualized/interactive table kütüphanesinin semantik output'u ayrıca audit
  edilmelidir; framework lint uyarısı ürünün WCAG/operational acceptance kriterini kapatmaz. [INFERRED] [HELD]

### 5.5 Test, tooling ve performance

- Next testing docs unit/component/integration/E2E/snapshot katmanlarını; Jest, Vitest, Cypress ve Playwright
  seçeneklerini listeler. Async Server Components bazı unit tool'larla tam desteklenmediğinden resmi rehber E2E'
  yi önerir. [CONFIRMED] [N10]
- Next 16 default Turbopack ve App Router'daki React canary closure'ı build pipeline'a bağlıdır. Production
  checklist streaming, parallel data fetching, caching, `Image`/`Font`/`Script`, Web Vitals, CSP, accessibility
  lint ve Server Action auth konularını birlikte kontrol listesine alır. [CONFIRMED] [N3][N11]
- RSC, streaming ve code-splitting client bundle'ını azaltabilir; fakat interactive grid, chart ve form library
  client component sınırını büyütebilir. TTFB, hydration, JS transfer, API latency ve table interaction gerçek
  fixture ile ölçülmeden bundle/performance üstünlüğü iddia edilmez. [INFERRED] [OPEN]

### 5.6 Security: CSP, CSRF, session ve secret

- Next CSP guide nonce/hash, SRI ve dynamic rendering trade-off'larını dokümante eder. CSP header/nonce üretimi,
  third-party script policy, Trusted Types, report-only ve deploy proxy davranışı uygulama kontratıdır. [CONFIRMED] [N12]
- Server Action origin/host kontrolü CSRF savunmasının bir katıdır. Kavriva API mutating endpoint'lerde anti-CSRF,
  cookie SameSite/Origin/Referer ve session/security epoch doğrulamasını kendi authority'sinde yapmalıdır; Next
  action check'i API authorization yerine geçmez. [INFERRED] [HELD]
- Self-hosting docs reverse proxy'yi malformed request, slow attack, payload size ve rate limiting için önerir;
  Server Action encryption key'in instance'lar arasında sabit olması ve deploymentId/version skew/cache paylaşımı
  dikkat ister. In-memory cache multi-instance canonical state değildir. [CONFIRMED] [N13]
- Next auth guide library önerse de provider/session choice açık bırakılır. Service secret, API token, signing key
  browser bundle'a giremez; Kavriva API yalnız server-side custody veya güvenli user session üzerinden çağrılmalıdır.
  [INFERRED] [HELD]

### 5.7 Deployment portability ve maliyet şekli

- Node server veya Docker, Next feature setinin en geniş biçimidir. Static export CDN/static server'a taşınır fakat
  Server Actions, dynamic headers, server data, auth/session ve API route gibi server feature'ları kaybedilir.
  Adapter API ve Next across-platforms çalışması platform correctness tests/verified adapters yaklaşımını bildirir;
  her adapter'ın cache, streaming, image, headers ve observability parity'si ayrı kanıttır. [CONFIRMED] [N5][N14]
- `output: 'standalone'` output file tracing ile minimum server.js ve gerekli production node_modules'u paketleyebilir;
  monorepo tracing, `public` ve `.next/static` CDN kopyası ayrıca yönetilir. Bu container boyutunu küçültebilir, tam
  exit veya dependency yokluğu anlamına gelmez. [CONFIRMED] [N15]
- Self-host şekli: reverse proxy + Node process/container + shared cache/deployment key + logging/metrics. Managed
  shape: provider build/cache/edge/region/egress özellikleri. Static shape: CDN storage + Kavriva API. Exact price,
  quota, data residency ve SLA bu araştırmada açılmadı. [INFERRED] [OPEN]
- Exit testi Node/Docker ile framework feature setinin yeniden deploy'u, external API endpoint/config export, image/
  font/CDN asset listesi, cache invalidation ve session/key rotation runbook'u ile yapılmalıdır. [HELD]

### 5.8 Upgrade, codemod ve ecosystem closure

- Next codemods docs upgrade migration'larını ve Next 16'da `next lint` kaldırılıp ESLint CLI'ye geçilmesi,
  `middleware`→`proxy` gibi değişiklikleri belgeler. Codemod çalışması review/test olmadan otomatik doğruluk sayılmaz.
  [CONFIRMED] [N16]
- React RSC bundler semver caveat'ı nedeniyle React, React DOM, Next, compiler, bundler, auth/data/grid packagesı
  tek dependency closure olarak lock + renovate/security update policy ile yönetilmelidir. React UI library olduğu için
  routing/form/cache/auth/accessibility grid seçimi ek ecosystem kararlarıdır. [INFERRED] [OPEN]
- `react-aria`/grid/form/query/auth gibi ek kütüphaneler bu belgede aday veya satın alma kararı değildir; resmi
  security/release/maintenance kanıtları olmadan mandatory closure'a alınmaz. [HELD]

**Aday A disposition:** Capability kanıtı güçlü fakat React/Next split release ve App Router/RSC/hosting cache
closure'ı operasyon fixture'ında kanıtlanmadı. `HELD`; winner veya recommendation yoktur.

## 6. Aday B — Vue + Nuxt

### 6.1 Kimlik, maturity ve release/support

- Vue 3 docs Vue'yu declarative, component-based framework olarak; static HTML enhancement, Web Components, SPA,
  SSR/SSG, desktop/mobile ve Composition API/SFC kullanımını kapsayan progressive bir core olarak tanımlar. [CONFIRMED] [V1]
- Vue 2 support'u 2023-12-31'de bitmiştir. Vue'nin fixed release cycle'ı yoktur; minor yaklaşık 3–6 ay aralığında,
  patch gerektiğinde çıkar. TypeScript definition değişimleri minor'da breaking olabilir; compiler/runtime minor
  mismatch library author için önemlidir. [CONFIRMED] [V2]
- Vue core official changelog/release snapshot'ında Vue 3.5.43 stable (2026-09-17), 3.6.0-rc.9 pre-release
  (2026-09-18) görünür. 3.6 RC production baseline değildir. [CONFIRMED] [V3] [HELD]
- Nuxt 4.0 2025-07-15'te stable duyuruldu. İlk v4 duyurusu Nuxt 3 maintenance'ini Ocak 2026 sonuna kadar
  planlarken, daha sonraki Nuxt 4.5 resmi blogu Nuxt 3 EOL'u 2026-07-31 olarak günceller. Nuxt blog snapshot'ında
  Nuxt 4.5 (2026-07-18), security patch 4.5.1/3.21.10 (2026-07-27) ve docs'ta 4.5.2 görünür. Nuxt için bu
  kesitte Angular/Next kadar açık, iki yıllık LTS matrisi bulunmamaktadır. [CONFIRMED] [V4][V5][V12] [OPEN]

### 6.2 Render, server/client ve data boundary

- Nuxt 4 universal rendering'i default yapar: server ilk HTML'yi üretir, browser hydrate eder. Client-side rendering,
  `ssr:false`, prerender/SSG ve routeRules ile hybrid rendering mümkündür; route bazında SWR/ISR/cache ve server
  bundle optimization seçilebilir. `nuxt generate` ile hybrid mod birlikte çalışmaz. [CONFIRMED] [U1]
- Nitro server `server/api`, `server/routes`, `server/middleware` dosyalarını handler olarak üretir; Node, bare metal,
  serverless ve edge preset'leri için deploy yolu sunar. Bu, API proxy/adapter için taşınabilirlik sağlar; Nitro
  endpoint'i Kavriva canonical state veya authz authority olarak kullanılmamalıdır. [CONFIRMED] [U2][U3]
- `useFetch`/`useAsyncData` SSR-safe payload transferiyle hydration'da double fetch'i azaltır; `$fetch` client event/
  POST için kullanılabilir. `useFetch` client'ta cookie/header proxy ederken yalnız gereken header'ları forward etme
  uyarısı vardır; payload `pick`/`transform` ile küçültülmelidir. [CONFIRMED] [U4]
- SSR payload/cache içinde secret, role grant veya gereksiz PII bulunmamalıdır. Internal API ile Kavriva API arasındaki
  response DTO'su explicit allowlist olmalı; browser payload'ı API authority değildir. [INFERRED] [HELD]

### 6.3 Forms, mutation ve session

- Vue forms guide `v-model` ile input/textarea/select state binding'i verir. Bu reactive ergonomi server-side
  validation, idempotency, authorization, expected version veya audit sağlamaz. [CONFIRMED] [V6]
- Nuxt `$fetch`, `useFetch` ve `useAsyncData` read/mutation akışını kolaylaştırır; event POST'ları server API route,
  direct Kavriva API veya server proxy üzerinden tasarlanabilir. Mutation response status'ı UI state'e işlenir fakat
  network timeout'ta `OUTCOME_UNKNOWN` korunur. [INFERRED] [U4]
- Nuxt `server/middleware` request context'e auth bilgisi ekleyebilir; app route middleware navigation/UX guard'ıdır.
  Her ikisi de Kavriva API'nin server-side authorization ve current session/security epoch check'i yerine geçmez. [CONFIRMED] [U3][U5]
- `useCookie` SSR-friendly'dir, fakat varsayılanlarında `httpOnly:false`, `secure:false`, `sameSite` unset olabilir.
  Auth/session cookie güvenli attribute'ları explicit ayarlanmalıdır. `useCookie` auth policy veya revoke mekanizması
  değildir. [CONFIRMED] [U6] [HELD]
- Pinia Vue core-team tarafından büyük SSR app'leri için önerilen state solution'dır; SSR'da singleton store data leak
  riski dokümanda anlatılır. Store cache'i canonical API state yerine konamaz. [CONFIRMED] [V7]

### 6.4 Accessibility

- Vue accessibility docs standard HTML, heading order, landmarks, skip link, labels, focus, keyboard, ARIA ve WCAG
  prensiplerini uygulama sorumluluğu olarak verir; framework otomatik WCAG pass iddiasında değildir. [CONFIRMED] [V8]
- Nuxt 4.4 blogunda accessibility announcer ve typed layout props; Nuxt 4 blogunda first-party accessibility module
  planı gelecek niyet olarak anılır. Planned module'ü shipped capability saymıyoruz. Route announcer varsa bile dense
  table semantics, focus restoration, error/live region, contrast, reduced motion ve screen reader QA uygulamadadır.
  [CONFIRMED] [V5] [OPEN] [HELD]
- Nuxt `useHeadSafe`, user input'tan head metadata üretirken allowlist ile XSS riskini azaltır; bu DOM/component
  semantics veya CMS/untrusted HTML sanitizer ihtiyacını ortadan kaldırmaz. [CONFIRMED] [U7]

### 6.5 Test, tooling ve performance

- Vue testing docs unit/component/E2E ayrımını, official `@vue/test-utils`, Vitest, Cypress ve Playwright'ı listeler.
  E2E staging üzerinde backend/infrastructure ile birlikte çalıştırılmalıdır. [CONFIRMED] [V9]
- Vue tooling docs Vue extension/vue-tsc, Vite, Vitest ve Cypress'i resmi workflow olarak verir. Nuxt test-utils
  first-class utility'dir; Vitest environment ve optional happy-dom/jsdom/Cucumber/Jest/Playwright peer deps vardır.
  Dependency set exact lockfile ile doğrulanmalıdır. [CONFIRMED] [V10][U8]
- Vue production build dev branch'leri temizler; SSR/SSG/CDN deploy guide'ı render modelinin maliyet ve latency'yi
  etkilediğini belirtir. Nuxt 4.5 Vite 8, Rsbuild/Rspack 2 ve experimental SSR streaming duyurur; experimental
  streaming production baseline değildir. [CONFIRMED] [V11][V12] [HELD]
- Compiler/tree-shaking, server payload transfer, routeRules cache ve lazy component'ler bundle/performance için
  fırsattır. Pinia/store, UI library, grid ve module payload'ı; hydration, TTFB ve filter interaction ölçümü
  yapılmadan üstünlük çıkarılamaz. [INFERRED] [OPEN]

### 6.6 Security: template, CSP, CSRF, cookie ve server routes

- Vue security guide untrusted template strings'i compile ederek arbitrary code/SSR server breach yaratabileceğini,
  normal Vue template binding'inin escaped olduğunu söyler. User-authored template, `v-html`, dynamic component ve
  server HTML sanitization ayrı threat modeldir. [CONFIRMED] [V13]
- Aynı guide backend'in CSRF/XSSI gibi riskleri ele alması ve Vue ile backend'in token contract'ında anlaşmasını
  önerir. Vue core CSRF veya auth server sağlamaz. Kavriva API token verification, origin policy ve session epoch
  authority'sini taşır. [CONFIRMED] [V13] [HELD]
- Nuxt cookie composable'ın permissive defaults'ı, `useHeadSafe`'in yalnız head input allowlist'i ve optional
  `nuxt-security` module'ün üçüncü taraf module olması; CSP, security headers, rate-limit veya CSRF'nin “Nuxt core
  garanti” olmadığını gösterir. Module owner/version/security update closure ayrıca kanıtlanır. [CONFIRMED] [U6][U7][U9]
- SSR server/proxy `Host`, forwarded headers, URL fetch ve internal route trust boundary'si SSRF/open redirect
  riskini doğurabilir; trusted proxy allowlist, outbound destination allowlist ve secret redaction API/infra runbook'ta
  kapanmalıdır. [INFERRED] [HELD]

### 6.7 Deployment portability ve maliyet şekli

- Nuxt deployment docs Nitro output ile Node server, prerender/static hosting, `ssr:false` SPA ve serverless/edge
  preset'lerini açıklar. Reverse proxy arkasında çalışma, `.output` artifact ve platform preset'i exit için ölçülebilir
  yüzey sağlar. [CONFIRMED] [U10]
- Static/SSG shape CDN/storage + Kavriva API; Node shape Nitro process/container + reverse proxy + shared/session
  cache; edge/serverless shape provider runtime + adapter/preset + request/response/cache limitsidir. [INFERRED]
- RouteRules/SWR/ISR cache'in multi-operator authorization, current role, version ve recall state'iyle uyumu
  ayrıca kanıtlanmadan response caching açılamaz. Cache key actor/scope/security epoch'i yanlışsa data disclosure
  olur. [INFERRED] [HELD]
- Nuxt/Nitro self-host portability yüksek görünse de exact Node/edge preset parity, streaming, cookie/headers,
  WebSocket/long request, logs/metrics, region/data residency ve managed host egress fiyatı bu kesitte araştırılmadı.
  [OPEN]

### 6.8 Upgrade, codemod ve ecosystem closure

- Nuxt 4 upgrade guide data fetching değişikliklerini ve `npx codemod@latest nuxt/4/default-data-error-value` gibi
  migration codemod örneğini verir. Codemod sonrası SSR payload, routeRules, cookie/header, authz ve E2E regression
  zorunludur. [CONFIRMED] [U11]
- Vue minor release'lerinde TypeScript definition/contract değişebildiği için Vue, vue-router, Pinia, Nuxt/Nitro,
  Vite, TypeScript, UI/grid, auth/security module'leri tek lockfile closure'dır. Vuex maintenance mode'dadır;
  yeni app state kararı ayrıca kanıtlanmalıdır. [CONFIRMED] [V2][V7]
- Nuxt modules katalogda güçlü görünse de module owner, release cadence, transitive dependencies, security advisory,
  Nuxt 4 compatibility ve exit replacement'ı capability closure'ın parçasıdır. [INFERRED] [OPEN]

**Aday B disposition:** Nuxt universal/hybrid/server/static boundary'leri dense browser yüzeyine adaydır; ancak
Nuxt LTS açıklığı, cookie defaults, optional security module ve route cache/session proof'ları kapanmadığı için
`HELD`; winner veya recommendation yoktur.

## 7. Aday C — Svelte + SvelteKit

### 7.1 Kimlik, maturity ve release/support

- SvelteKit resmi introduction sayfasında Svelte compiler üzerine tam web framework olarak; router, Vite code-splitting,
  offline support, preloading, SSR/CSR/prerender ve image optimization sunan framework olarak tanımlanır. [CONFIRMED] [S1]
- Official Svelte releases snapshot'ında Svelte 5.56.8 stable görülür. SvelteKit release snapshot'ında
  `3.0.0-next.27` (2026-09-08) pre-release; production baseline bu nedenle SvelteKit 2 docs/family'dir. [CONFIRMED] [S2][S3] [HELD]
- SvelteKit için Angular gibi resmi 12+12 aylık LTS matrisi bu kaynak kesitinde bulunmadı. Support, adapter ve major
  migration riskleri release page/docs watch ile yönetilmeli; “Svelte stable” SvelteKit app support garantisi değildir.
  [OPEN]
- Official package directory adapter-node, adapter-static, Cloudflare/Netlify/Vercel adapters, Vitest/Playwright ve
  auth/data packagesını gösterir. Directory snapshot dependency selection veya provider recommendation değildir. [CONFIRMED] [S4]

### 7.2 Render, server/client ve data boundary

- SvelteKit default olarak server render/prerender sonrası hydrate eder. Page/layout options `prerender`, `ssr` ve
  `csr` ile marketing/static, dynamic SSR ve admin CSR aynı app içinde route bazında karıştırılabilir. [CONFIRMED] [S5]
- `+page.server` load server-only data/secrets için; `+page` browser'da da çalışabileceği için secret transferi
  önlenmelidir. Load data serialization ve invalidation, UI data flow'dur; canonical role/resource/version Kavriva
  API'den alınır. [CONFIRMED] [S6] [INFERRED]
- `hooks.server` `handle` her request'te auth/header/response policy uygulayabilir; static asset ve prerendered page'ler
  hook'u bypass edebilir. Bu bypass, browser static artifact'ının session/authz authority olmadığına dair önemli
  operasyon kuralıdır. [CONFIRMED] [S7]
- Adapter-node standalone Node server, adapter-static static output, cloud/edge adapters farklı deploy shapes sağlar.
  Adapter/runtime parity (cookies, streaming, headers, cache, background work) route bazında kanıtlanmalıdır. [CONFIRMED] [S8][S4]

### 7.3 Forms, mutation ve session

- SvelteKit form actions `+page.server` içindeki POST action'ları native `<form>` ile çalıştırır; JS olmadan da çalışır,
  `use:enhance` progressive enhancement sağlar. Form actions feature-complete olarak belgelenir. [CONFIRMED] [S9]
- Actions yalnız POST'tur; form data validate edilmeli ve action authz re-check yapmalıdır. Kavriva approval/publish/
  recall action'ı operation ID/idempotency/expected version/audit için API command çağrısıdır; action success UI sonucu
  transaction outcome değildir. [INFERRED] [HELD]
- SvelteKit docs session ID'nin immediate revoke ve DB lookup trade-off'unu; JWT'nin generally immediate revoke
  edilememesini anlatır. Auth check server hooks'ta yapılır, user `locals` içine konur; identity provider veya
  authorization authority framework tarafından seçilmez. [CONFIRMED] [S10]
- SvelteKit form/action cookies'te httpOnly ve secure default'ları (localhost istisnası) ile SameSite lax görünür;
  production domain/proxy ve API session contract'ı yine explicit test edilmelidir. [CONFIRMED] [S9]
- Docs'taki experimental remote `form` functions type-safe/single-flight mutation yönünde ilerler fakat API değişebilir;
  bu Phase 4 baseline'ında açılmaz. [CONFIRMED] [S9] [HELD]

### 7.4 Accessibility

- Svelte compiler birçok `a11y_*` warning'i verir: label, role, keyboard, alt, caption ve benzeri semantik/interaction
  hataları build sırasında görünür. [CONFIRMED] [S11]
- SvelteKit accessibility docs route announcement live region ve focus management sağlar; platform foundation'dır,
  uygulamanın WCAG geçişi değildir. Dense grid keyboard model, focus trap, error summary, visible focus, contrast,
  reduced motion ve screen-reader/device matrix uygulama sorumluluğudur. [CONFIRMED] [S12] [HELD]
- Warning'i susturmak/`{@html}` kullanmak untrusted content, sanitizer ve CSP riskini yeniden açabilir. Warning policy
  CI'da error veya reviewed exception olarak yönetilmelidir. [INFERRED]

### 7.5 Test, tooling ve performance

- SvelteKit Vite üzerinde HMR, route-level code splitting ve preloading kullanır; official performance docs asset
  preloading, request coalescing, parallel loads, inlining, invalidation, prerender ve link preload mekanizmalarını
  açıklar. [CONFIRMED] [S13]
- Svelte/SvelteKit ecosystem package listesinde Vitest ve Playwright entegrasyonları görülür; component/unit/E2E
  fixture'ı app-level auth/session/API contract ile kurulmalıdır. [CONFIRMED] [S4] [INFERRED]
- Compiler-generated minimal client JavaScript ve page-level CSR/SSR seçimleri bundle fırsatı yaratır; interactive
  tables, editor, chart, grid and localization package'ları gerçek JS transferi/hydration ile ölçülmelidir. [INFERRED] [OPEN]
- SSR ve prerender bir request'in Kavriva API'den fresh permission/resource data alacağı anlamına gelmez; cache,
  invalidation, stale tab ve current security epoch senaryoları Playwright/real browser testinde zorunludur. [HELD]

### 7.6 Security: cookies, hooks, CSP/CSRF ve secret

- SvelteKit `hooks.server` server response headers/auth için geniş uygulama noktasıdır; `+page.server`/actions server-only
  boundary sağlar. Static/prerender output'ta hook çalışmadığı için protected operations dynamic/server path'te kalır.
  [CONFIRMED] [S7]
- Cookie secure/httpOnly/SameSite defaults yardımcıdır, fakat cookie'nin içindeki user/role/epoch iddiası API tarafından
  doğrulanmadan authority değildir. Session ID immediate revoke veya JWT trade-off'u Kavriva session contract'ına göre
  seçilmelidir. [INFERRED] [S9][S10]
- SvelteKit'te framework guide'larında Next/Angular kadar tek bir CSP/CSRF policy sözleşmesi bu kesitte kapanmadı.
  CSP nonce/hash, Trusted Types, Origin/Referer, SameSite ve anti-CSRF token'ın uygulama/API ile explicit kurulması
  gerekir. Exact adapter/header behavior [OPEN] [HELD].
- Action POST ve SameSite lax browser davranışı bir risk azaltma katmanıdır; API commit endpoint'i kendi CSRF/authz/
  replay/epoch check'ini yapmalıdır. CORS veya hook guard'ı server authority yerine konamaz. [INFERRED] [HELD]

### 7.7 Deployment portability ve maliyet şekli

- Adapter-node standalone server container/VM/bare-metal Node şeklidir; adapter-static CDN/static server şeklidir.
  Official cloud adapters managed/edge shape verir. Reverse proxy SSL/compression'ı çoğunlukla dışarıda tutar.
  [CONFIRMED] [S8]
- Static shape low-ops fakat dynamic authz, personalized data, form actions, live approval state için Kavriva API'ye
  browser call gerekir. Node/edge shape SSR/Actions sağlar fakat runtime limit, cache/session, cold start, egress ve
  provider-specific adapter behavior maliyeti doğurur. [INFERRED]
- SvelteKit package/adapters portability için başlangıç sağlar; adapter exit, background work, logs/traces, CSP/headers,
  WebSocket, streaming, region/data residency ve cost/sla ayrıntısı official generic docs'ta tek contract olarak
  kapanmadı. [OPEN]

### 7.8 Upgrade, codemod ve ecosystem closure

- SvelteKit migration docs major upgrade guide'ları sunar; official releases 3.0.0-next.27'nin pre-release olduğunu
  gösterir. Svelte 5 runes/compiler changes, SvelteKit 2 baseline ve gelecekte v3 migration ayrı regression proof
  ister. [CONFIRMED] [S2][S14] [HELD]
- Adapter, form/remote function, auth/session, component library, table/grid, validation, i18n and observability
  packagesı core'dan bağımsız release/security closure getirir. Official package listesinde adının bulunması bakım,
  security veya SLA garantisi değildir. [INFERRED] [OPEN]
- SvelteKit server hooks/adapter API'leri business logic için uzun ömürlü boundary yapılmadan önce API integration,
  CSP/CSRF, cookie, rollback ve artifact portability proof'ları zorunludur. [HELD]

**Aday C disposition:** SvelteKit route-level render boundary ve native form progressive enhancement'i fixture'a
uygun bir capability olarak kanıtlar; ancak SvelteKit 3 pre-release, formal LTS/CSP-CSRF closure ve adapter parity
kanıtı eksik olduğundan `HELD`; winner veya recommendation yoktur.

## 8. Aday D — Angular

### 8.1 Kimlik, maturity ve release/support

- Angular releases resmi sayfası major release'leri yaklaşık 6 ayda; Active 12 ay, LTS 12 ay olarak tanımlar.
  Angular 22 2026-06-03 release, Active yaklaşık 2027-06 ve LTS yaklaşık 2028-06; Angular 21 LTS, Angular 20 LTS
  tablosundadır. Angular v2–19 unsupported snapshot'tadır. [CONFIRMED] [A1]
- Angular 22 compatibility tablosu Node `^22.22.3 || ^24.15.0 || ^26.0.0`, TypeScript `>=6.0.0 <6.1.0`, RxJS
  `^6.5.3 || ^7.4.0` aralığını; Angular 21 daha farklı Node/TypeScript aralığını gösterir. Runtime/CI image ve
  upgrade matrix lock edilmelidir. [CONFIRMED] [A2]
- Angular framework, Angular CLI, CDK/Aria, RxJS, compiler ve TypeScript birlikte release/compatibility closure'dır.
  LTS, uygulama dependencies veya third-party grid/auth library'nin aynı desteği anlamına gelmez. [INFERRED] [OPEN]

### 8.2 Render, server/client ve data boundary

- Angular CSR default'tur. Angular SSR rehberi hybrid rendering'de route bazlı `RenderMode.Server`, `Client` ve
  `Prerender`; fully static için `outputMode: static` kullanımını açıklar. SSR server compute, SSG build-time;
  static CDN/HTML en kolay deploy shape'dir. [CONFIRMED] [A3]
- Angular hydration DOM'u server HTML ile eşler, transfer data ve event replay sağlayabilir. Direct DOM manipulation,
  browser-only third-party script ve custom/noop Zone.js hydration mismatch/unsupported behavior riski taşır. [CONFIRMED] [A4]
- `@angular/ssr` Web Request/Response API ile Node dışı server yolu açar; non-Node adapter/runtime parity ayrıca
  kanıtlanmalıdır. Static output'ta session/SSR guard çalışmadığından protected data browser→Kavriva API path'inde
  explicit reauth ister. [CONFIRMED] [A3] [INFERRED]
- TransferState/cache, SSR HTML veya browser service store'unda actor/role/epoch/resource version stale kalabilir.
  Canonical read ve command result Kavriva API'den gelir; Angular service yalnız transport/UI state'tir. [HELD]

### 8.3 Forms, mutation ve session

- Angular forms docs reactive forms'i scalable, reusable, testable; template-driven forms'i simpler path olarak verir.
  Validators, form state ve error presentation framework capability'sidir. [CONFIRMED] [A5]
- Reactive form value browser tarafında valid görünse dahi Kavriva API server validation, authorization,
  expected version, idempotency and audit'i tekrar yapar. `HttpClient` response success UI'da kesin commit değildir;
  timeout `OUTCOME_UNKNOWN` status resolver'a gider. [INFERRED] [HELD]
- Angular docs auth/session provider veya server authorization authority sunmaz. Interceptor/cookie/header handling
  yalnız transport helper olabilir; authz grant/competence/independence and security epoch API'de kalır. [INFERRED]
- `HttpClient` built-in XSRF interceptor cookie'den token okuyup header'a ekler; resmi security docs backend'in token
  cookie'yi set ve header/cookie'yi verify etmesi gerektiğini, client half'ın tek başına yetmediğini açıkça söyler.
  [CONFIRMED] [A6]

### 8.4 Accessibility

- Angular Aria headless directives ARIA pattern, keyboard interaction, focus management ve screen-reader behavior için
  yapı taşları sağlar. Docs significant effort/expertise ve uygulama testi gerektiğini belirtir. [CONFIRMED] [A7]
- Angular CDK/Aria ile dense table, dialog, menu, combobox ve focus model kurulabilir; kullanılmış pattern'in DOM,
  labels, error association, live region, contrast, reduced motion, touch/keyboard ve screen-reader acceptance'ı
  ayrıca ölçülür. Angular Aria kullanımı otomatik WCAG conformance değildir. [INFERRED] [HELD]

### 8.5 Test, tooling ve performance

- Angular testing docs yeni CLI app'lerinde Vitest + jsdom default; Karma hâlâ supported. TestBed component/injection
  testleri için; CLI `ng test` CI command'dır. E2E docs Cypress gibi seçenekleri bırakır. [CONFIRMED] [A8][A9]
- Angular application builder esbuild/Vite ile client bundle, Node server ve prerendered routes üretebilir; bundle
  size budgets, ESM tercihi ve CommonJS larger bundle warning'i resmi build docs'tadır. [CONFIRMED] [A10]
- Incremental hydration/defer/event replay non-visible veya deferred UI için performance fırsatı sunar. Angular server
  render ve hydration constraints'i nedeniyle direct DOM/third-party script compatibility fixture'la test edilmelidir.
  [CONFIRMED] [A4][A11]
- CLI budgets, source-map policy, lazy routes, preloading, RxJS operator usage, grid/editor dependency and hydration
  ölçülmeden Angular'ın bundle/performance sonucu çıkarılmaz. [INFERRED] [OPEN]

### 8.6 Security: sanitization, CSP/Trusted Types, XSRF ve SSRF

- Angular security docs template value'larını sanitize eder, AOT compiler'ı önerir; CSP ve Trusted Types'i nonce ile
  birlikte önerir (`CSP_NONCE`). Dynamic HTML bypass security APIs ve untrusted URL/resource ayrıca review ister.
  [CONFIRMED] [A6]
- XSRF interceptor client half'tır; backend token cookie/header validation yapmalıdır. Kavriva API origin/session/
  epoch/operation authorization'ı kendi authority'sinde yapar. [CONFIRMED] [A6] [HELD]
- SSR security docs server-side request, proxy/Host header, external resource ve SSRF trust boundary'si için
  allowlist/validation gerektirir. Angular authz veya identity provider değildir. [CONFIRMED] [A6]
- CSP nonce/Trusted Types policy, response headers, report-only/violation reporting, cookie SameSite/secure/httpOnly,
  session rotation and API replay protection deployment reverse proxy + Kavriva API sözleşmesinde kapanmalıdır. [INFERRED] [OPEN]

### 8.7 Deployment portability ve maliyet şekli

- `ng build` dist artifact üretir. CSR static HTML server/CDN'de çalışır; SPA fallback `index.html` gerekir. SSR
  output Node/server path'i ister; `outputMode: static` fully static artifact'tır. [CONFIRMED] [A12]
- Static shape CDN/storage + Kavriva API; SSR shape Node/container/managed app runtime + reverse proxy; non-Node
  Web Request/Response shape provider/adapter contract'ına bağlıdır. [INFERRED]
- Angular CLI/build/CI static deployment için ek managed framework hesabı gerektirmez; SSR server compute, build runner,
  logs, egress, cache and region cost variables getirir. Exact prices, SLA, data residency and rollback topology
  hesaplanmadı. [OPEN]
- Angular full platform/CDK/CLI self-host çıkışı build artifact ve API endpoint ile mümkün görünür; SSR runtime,
  hydration, Node/TS version and third-party package replacement migration planı exit fixture'ında kanıtlanmalıdır.
  [INFERRED] [HELD]

### 8.8 Upgrade, codemod ve ecosystem closure

- `ng update` Angular CLI migrations/schematics çalıştırır; official update guide major/minor update akışını ve
  migration/compatibility kontrolünü açıklar. Old webpack/browser builder yerine yeni esbuild/Vite application builder
  migration'ı resmi olarak belgelenmiştir; eski builder deprecated. [CONFIRMED] [A13][A14]
- Angular 22 upgrade Node/TS/RxJS matrix'ini taşıdığı için CI image, compiler, CLI, CDK, Material, RxJS and third-party
  grid/auth packagesı aynı compatibility BOM'da olmalıdır. [INFERRED] [OPEN]
- Integrated forms/DI/testing/Aria/CDK operasyon yüzeyini tek framework ailesinde toplar; bunun karşılığında Angular
  compiler metadata, RxJS and CLI conventions'e coupling getirir. “Daha az package” veya “daha ucuz” hükmü yalnız
  fixture ve normalized BOM sonrası verilebilir. [INFERRED]

**Aday D disposition:** Angular'ın release/LTS, form, XSRF client-half, Aria ve build/deployment dokümantasyonu
kanıtlıdır; yine de API authority, SSR hydration, toolchain coupling, exact cost ve third-party closure kapanmadığı
için `HELD`; winner veya recommendation yoktur.

## 9. Remix / React Router — referans sınırı

Remix bu debate'te beşinci finalist değildir.

- Resmi Remix blogu Remix 3 Release Candidate'ı 2026-08-31'de; planned stable tarihi 2026-10-02'yi duyurur.
  Release Candidate production baseline değildir; aynı duyuru docs/security audit işlerinin kapanması gerektiğini
  açıklar. [CONFIRMED] [M1]
- Remix docs current version'ı React Router v7 olarak açıklar; React Router modes docs Framework Mode'da Vite plugin,
  type-safe href/route modules, code splitting, SPA/SSR/static rendering, loaders/actions ve pending UI capability
  verir. Bu referans React + Next.js adayının dışında aynı render/data sorularını gösterir. [CONFIRMED] [M2][M3]
- React Router security docs inline script için CSP nonce gereğini açıklar. Loader/action, CSP veya framework mode
  Kavriva authorization/audit/transaction authority değildir. [CONFIRMED] [M4]

**Disposition:** `REFERENCE ONLY / HELD`. 2026-09-19 itibarıyla Remix 3 stable release, support matrix, security
audit ve upgrade closure kapanmadan Phase 5 primary candidate setine alınmaz.

## 10. Cross-candidate security ve authority matrisi

| Boundary | React + Next.js | Vue + Nuxt | Svelte + SvelteKit | Angular | Kavriva invariant |
|---|---|---|---|---|---|
| XSS/template | React escaped/ARIA primitives; untrusted HTML app-owned; Next CSP guide | Vue template auto-escape; untrusted template strings forbidden; `useHeadSafe` head allowlist | compiler warnings; `{@html}`/user HTML review; hooks headers | sanitization/AOT; bypass APIs risk | Untrusted content never becomes trusted domain markup without allowlist/sanitizer |
| CSP/nonce/TT | Next CSP nonce/hash/SRI docs; headers/app config | Nuxt header/module choice; core single policy not closed | hook/adapter/header path; exact policy [OPEN] | CSP/Trusted Types nonce explicit | CSP is defense-in-depth; API secret/authz still server-side |
| CSRF/XSRF | Server Action origin/host check + `allowedOrigins`; API recheck | Vue docs assign backend/token contract; Nuxt module optional | POST action/SameSite reduces risk; exact integration [OPEN] | HttpClient XSRF cookie/header is client half; backend verify | Mutating Kavriva endpoint verifies Origin/CSRF/session/epoch/idempotency |
| Cookie/session | Next auth guide/library choice; Server Action key consistency | `useCookie` defaults must be hardened | action cookie secure/httpOnly/SameSite defaults; session/JWT tradeoff | interceptor/cookie transport; no provider | Session ID, rotation/revoke, epoch and current authorization from API |
| Authz | DAL/action/route handler must reauthorize | route/server middleware UX/transport only | hooks/locals/action check only adapter layer | guards/interceptors not server authority | actor, role/grant, scope, competence, independence, resource version at commit |
| Server secret | Server Components/server-only DAL; safe DTO | Nitro server; header/payload forwarding caution | `+page.server`/hooks; static bypass | SSR server/services; browser bundle boundary | API secrets never in bundle, HTML, logs or cache |
| SSRF/trusted proxy | reverse proxy/self-host guidance | Nitro/forwarded header/outbound destination review | adapter/proxy/header review | SSRF/Host allowlist docs | outbound allowlist, trusted proxy and correlation at API/edge |
| Audit/outcome | action response is not audit/commit | `$fetch`/Nitro response is not commit | action success is not commit | HttpClient 2xx is not commit | operation ledger/status resolver, `OUTCOME_UNKNOWN`, protected audit |

Security matrix conclusion: Every family supplies useful browser/server primitives, but no framework can be
accepted as Kavriva security authority. CSRF client token, route guard, SSR middleware, cookie, local state and
Server Action all remain defense/transport layers. [CONFIRMED] [INFERRED] [HELD]

## 11. Deployment, portability ve cost-shape matrix

Exact price/account/region/SLA araştırması yapılmamıştır. Aşağıdaki “cost shape” satın alma teklifi değil,
runtime topology'nin hangi değişkenleri doğurduğudur.

| Shape | React + Next | Vue + Nuxt | Svelte + SvelteKit | Angular | Ortak Kavriva kontrolü |
|---|---|---|---|---|---|
| Static/CDN | Next static export; server feature yok | Nuxt prerender / SPA `ssr:false` | adapter-static | `outputMode: static`, CSR | CDN artifact + Kavriva API; session/CSP/CORS/CSRF browser path |
| Node/container self-host | Node/Docker all features; reverse proxy/shared cache/key | Nitro `.output` Node server; reverse proxy | adapter-node standalone; reverse proxy | SSR Node output | immutable artifact, health gate, logs/traces, rotation, rollback, rate limits |
| Serverless/edge | Next adapter API; platform parity proof | Nitro serverless/edge presets | cloud/edge adapters | non-Node `@angular/ssr` path | timeout, cold start, request/body/cache limits, region, outcome resolver |
| Managed host | build/cache/edge/image/adapter contract | Nitro preset/module/platform contract | adapter/platform contract | managed Node/static service | no account in Phase 4; provider authority not substituted for API |
| Exit | Docker/Node + static path; adapter features may differ | Nitro/Node/static path; routeRules/cache parity | adapter-node/static; adapter-specific features | `dist` static/SSR output; Node/TS coupling | clean-room rebuild from repo, config/secrets/schema/export and session rotation |

Top cost variables across all families:

- Build/CI minutes, server/edge compute, cold start or minimum instances, request/egress, CDN/cache and image/font
  transfer, logs/traces retention, database/API calls, region/data residency, backup/restore and incident capacity.
- SSR/hybrid adds server compute and cache invalidation. Static adds API/browser round trips and public surface
  hardening. Edge adds adapter/runtime and data locality/consistency evidence.
- “Self-hostable” does not mean operations-free; reverse proxy, TLS, WAF/rate-limit, secret rotation, deploy/rollback,
  logs/metrics/traces, alerting and vulnerability patching become Kavriva owner work. [INFERRED]
- Exact normalized BOM, price, quota, egress, SLA, retention and exit-month cost are `[OPEN]`; no plan or provider
  is selected here.

## 12. Upgrade, observability ve Phase 5 evidence gates

Her aday için aynı change/runbook fixture'ı kapanmadan ADR yazılmamalıdır:

1. Exact lockfile: framework, runtime, compiler, bundler, form/grid/editor, validation, auth/session, i18n, test,
   observability and adapter packagesı; transitive SBOM and license/security advisory.
2. Release watch: React/Next, Vue/Nuxt, Svelte/SvelteKit, Angular security advisories; supported Node/TS/browser
   matrix; patch SLA; pre-release veya deprecated package block policy.
3. Codemod proof: clean clone, migration command, human diff review, SSR/static output, form/action, CSP/CSRF,
   session/epoch, table keyboard/screen-reader and E2E replay.
4. API contract test: current session/security epoch, role/scope/competence/independence, expected version,
   idempotency duplicate, conflict, timeout/unknown, retry, recall/approval/publish, audit and status resolver.
5. Render matrix: static, SSR, CSR, hybrid route; browser refresh/back/forward; stale tab; cache key; personalized
   response isolation; server-only secret and DTO redaction.
6. Accessibility gate: semantic table/forms, label/error/description, focus/announcement, keyboard, screen reader,
   contrast, reduced motion, zoom/responsive; automated lint is necessary but not sufficient.
7. Security gate: CSP report-only→enforce, nonce/Trusted Types where used, XSS/untrusted HTML, CSRF/XSRF, SameSite,
   cookie flags, CORS, SSRF/trusted proxy, header forwarding, secret/log redaction and dependency advisories.
8. Operational gate: artifact digest, immutable revision, deploymentId/version skew, cache invalidation, health/readiness,
   rollback/roll-forward, queue/outbox ownership, rate limits, logs/metrics/traces and incident `OUTCOME_UNKNOWN` UI.
9. Portability/exit gate: static and Node/container artifact rebuilt without managed provider, API URL/config export,
   secret re-issuance, data/cache purge, DNS/TLS, runbook and a restore/exit rehearsal.
10. Cost gate: exact region and residency, traffic/request/egress assumptions, normal/incident/restore/exit month,
    quotas/spend stops and owner hours. This research deliberately does not do that purchase analysis.

Framework boundary questions to keep open:

| Question | Why it remains open |
|---|---|
| Which render shape is needed per route? | SSR freshness vs static/CDN vs CSR API calls changes security, latency and cost. |
| Where is API call made? | Browser-direct, server proxy or edge adapter changes CORS, CSRF, secret, timeout and audit correlation. |
| Which session protocol? | Cookie/session ID vs token/JWT, revoke and security epoch need Kavriva authority contract. |
| Which table/grid/editor packages? | A family’s core docs do not prove semantics, bundle, virtualization or maintenance of a third-party control. |
| Which CSP/Trusted Types policy? | Framework guides expose primitives, but exact nonce/hash, scripts, reports and deploy headers are app/infra. |
| Which adapter/host? | Official adapters differ in streaming, cache, headers, logs, region, cost and rollback; no account was opened. |
| Which release cadence? | React/Next split, Vue/Nuxt support, SvelteKit pre-release and Angular LTS all require watch ownership. |
| What is the failure UI? | No framework default can define Kavriva `OUTCOME_UNKNOWN`, retry, status polling or safe recovery. |

## 13. Sonuç ve disposition

Bu belge için sonuç:

- `0 PASS` / `4 primary candidate HELD` / `1 reference only HELD`.
- React + Next.js, Vue + Nuxt, Svelte + SvelteKit ve Angular'ın her biri SSR/SPA/static/server, forms/data,
  accessibility, testing, security primitives, portability ve upgrade kanıtlarıyla eşit mercekte incelendi.
- Hiçbir aile Kavriva API authority'sinin yerine yazılmadı; framework server runtime'ı direct DB/provider authority
  olarak kabul edilmedi.
- No-code, no-account, no-purchase, no-winner kısıtları korunmuştur. Phase 5 fixture, exact dependency/BOM,
  security/a11y/API/rollback/exit/cost evidence olmadan ADR veya recommendation yazılmamalıdır.

## 14. Resmi birincil kaynak envanteri

### React ve Next.js

- [R1] [React 19.3 release](https://react.dev/blog/2026/09/09/react-19-3)
- [R2] [React introduction](https://react.dev/learn)
- [R3] [React Server Functions](https://react.dev/reference/rsc/server-functions)
- [R4] [React DOM server APIs](https://react.dev/reference/react-dom/server)
- [R5] [React 19 Actions and forms](https://react.dev/blog/2024/12/05/react-19)
- [R6] [React DOM common components and ARIA](https://react.dev/reference/react-dom/components/common)
- [R7] [React input accessibility](https://react.dev/reference/react-dom/components/input)
- [N1] [Next.js support policy](https://nextjs.org/support-policy)
- [N2] [Next.js release blog/changelog](https://nextjs.org/blog)
- [N3] [Next.js installation](https://nextjs.org/docs/app/getting-started/installation)
- [N4] [Next.js App Router](https://nextjs.org/docs/app/api-reference/config/next-config-js/appDir)
- [N5] [Next.js deployment](https://nextjs.org/docs/app/getting-started/deploying)
- [N6] [Next.js data security](https://nextjs.org/docs/app/guides/data-security)
- [N7] [Next.js Server Actions/data security](https://nextjs.org/docs/app/guides/data-security)
- [N8] [Next.js authentication](https://nextjs.org/docs/app/guides/authentication)
- [N9] [Next.js accessibility](https://nextjs.org/docs/architecture/accessibility)
- [N10] [Next.js testing](https://nextjs.org/docs/app/guides/testing)
- [N11] [Next.js production checklist](https://nextjs.org/docs/app/guides/production-checklist)
- [N12] [Next.js Content Security Policy](https://nextjs.org/docs/app/guides/content-security-policy)
- [N13] [Next.js self-hosting](https://nextjs.org/docs/app/guides/self-hosting)
- [N14] [Next.js across platforms / adapters](https://nextjs.org/blog/nextjs-across-platforms)
- [N15] [Next.js output file tracing / standalone](https://nextjs.org/docs/app/api-reference/config/next-config-js/output)
- [N16] [Next.js codemods and upgrades](https://nextjs.org/docs/app/guides/upgrading/codemods)

### Vue ve Nuxt

- [V1] [Vue introduction](https://vuejs.org/guide/introduction)
- [V2] [Vue release cycle and support](https://vuejs.org/about/releases)
- [V3] [Vue core changelog](https://github.com/vuejs/core/blob/main/CHANGELOG.md)
- [V4] [Nuxt 4 release](https://nuxt.com/blog/v4)
- [V5] [Nuxt official blog/changelog](https://nuxt.com/blog)
- [V6] [Vue forms](https://vuejs.org/guide/essentials/forms.html)
- [V7] [Vue state management / Pinia](https://vuejs.org/guide/scaling-up/state-management)
- [V8] [Vue accessibility](https://vuejs.org/guide/best-practices/accessibility)
- [V9] [Vue testing](https://vuejs.org/guide/scaling-up/testing)
- [V10] [Vue tooling](https://vuejs.org/guide/scaling-up/tooling)
- [V11] [Vue production performance](https://vuejs.org/guide/best-practices/performance)
- [V12] [Nuxt 4.5 release](https://nuxt.com/blog/v4-5)
- [V13] [Vue security](https://vuejs.org/guide/best-practices/security)
- [U1] [Nuxt rendering modes](https://nuxt.com/docs/4.x/guide/concepts/rendering)
- [U2] [Nuxt server directory](https://nuxt.com/docs/4.x/directory-structure/server)
- [U3] [Nuxt server/Nitro](https://nuxt.com/docs/4.x/getting-started/server)
- [U4] [Nuxt data fetching](https://nuxt.com/docs/4.x/getting-started/data-fetching)
- [U5] [Nuxt route middleware](https://nuxt.com/docs/4.x/directory-structure/app/middleware)
- [U6] [Nuxt `useCookie`](https://nuxt.com/docs/4.x/api/composables/use-cookie)
- [U7] [Nuxt `useHeadSafe`](https://nuxt.com/docs/4.x/api/composables/use-head-safe)
- [U8] [Nuxt testing](https://nuxt.com/docs/4.x/getting-started/testing)
- [U9] [Nuxt Security module registry entry](https://nuxt.com/modules/security)
- [U10] [Nuxt deployment](https://nuxt.com/docs/4.x/getting-started/deployment)
- [U11] [Nuxt upgrade and codemods](https://nuxt.com/docs/4.x/getting-started/upgrade)

### Svelte ve SvelteKit

- [S1] [SvelteKit introduction](https://svelte.dev/docs/kit/introduction)
- [S2] [Svelte releases](https://github.com/sveltejs/svelte/releases)
- [S3] [SvelteKit releases](https://github.com/sveltejs/kit/releases)
- [S4] [Svelte official packages/adapters](https://svelte.dev/packages)
- [S5] [SvelteKit page options](https://svelte.dev/docs/kit/page-options)
- [S6] [SvelteKit load functions](https://svelte.dev/docs/kit/load)
- [S7] [SvelteKit server hooks](https://svelte.dev/docs/kit/hooks)
- [S8] [SvelteKit adapter-node](https://svelte.dev/docs/kit/adapter-node)
- [S9] [SvelteKit form actions](https://svelte.dev/docs/kit/form-actions)
- [S10] [SvelteKit auth/session](https://svelte.dev/docs/kit/auth)
- [S11] [Svelte compiler accessibility warnings](https://svelte.dev/docs/svelte/compiler-warnings)
- [S12] [SvelteKit accessibility](https://svelte.dev/docs/kit/accessibility)
- [S13] [SvelteKit performance](https://svelte.dev/docs/kit/performance)
- [S14] [SvelteKit migration to v2](https://svelte.dev/docs/kit/migrating-to-sveltekit-v2)

### Angular

- [A1] [Angular releases and support](https://angular.dev/reference/releases)
- [A2] [Angular version compatibility](https://angular.dev/reference/versions)
- [A3] [Angular SSR and hybrid rendering](https://angular.dev/best-practices/performance/ssr)
- [A4] [Angular hydration](https://angular.dev/guide/hydration)
- [A5] [Angular forms](https://angular.dev/guide/forms)
- [A6] [Angular security](https://angular.dev/best-practices/security)
- [A7] [Angular Aria accessibility](https://angular.dev/guide/aria/overview)
- [A8] [Angular testing](https://angular.dev/guide/testing)
- [A9] [Angular end-to-end testing](https://angular.dev/tools/cli/end-to-end)
- [A10] [Angular application build](https://angular.dev/tools/cli/build)
- [A11] [Angular incremental hydration](https://angular.dev/guide/incremental-hydration)
- [A12] [Angular deployment](https://angular.dev/tools/cli/deployment)
- [A13] [`ng update`](https://angular.dev/cli/update)
- [A14] [Angular build system migration](https://angular.dev/tools/cli/build-system-migration)

### Remix / React Router referansı

- [M1] [Remix 3 Release Candidate](https://remix.run/blog/remix-3-release-candidate)
- [M2] [Remix docs](https://remix.run/docs/en/main)
- [M3] [React Router rendering and framework modes](https://reactrouter.com/start/modes)
- [M4] [React Router security](https://reactrouter.com/how-to/security)
