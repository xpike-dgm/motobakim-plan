# DEBATE-012 — Internal Operations Web Frontend Failure, TCO ve Operability Araştırması

**Durum:** PHASE-4 / NO-CODE / EŞİT KÖTÜ-DURUM FİXTÜRÜ / NO WINNER / ADR NOT READY  
**Tarih:** 2026-09-19 (Europe/Istanbul)  
**Kapsam:** Internal Operations web frontend'i; browser state/rendering, session ve rol görünümü, API çağrısı
kontratı, cache/service worker, veri-ağır ekranlar, dosya yükleme, erişilebilirlik, browser uyumluluğu,
frontend supply-chain, framework upgrade, deployment/hosting, log/privacy, billing/quota ve clean-room exit.  
**Aday aileleri:** React/Next, Vue/Nuxt, Svelte/SvelteKit, Angular.  
**Yetki sınırı:** Bu belge hesap, provider, plan, abonelik, satın alma, kod, prototip, migration, production proof,
Phase-5 ADR veya Gate 4 -> 5 geçişi oluşturmaz. Hiçbir aile veya hosting modu seçilmemiştir.

## 1. Kısa sonuç

Dört frontend ailesi aynı ürün otoritesi, aynı API operation ledger'ı, aynı auth/session/security-epoch sözleşmesi,
aynı object quarantine, aynı audit/floor, aynı browser fixture ve aynı evidence gate'leri altında tutulmalıdır. React/Next,
Vue/Nuxt, Svelte/SvelteKit ve Angular'ın hepsi static artifact üretebilir; bazıları ayrıca Node/edge/serverless sunucu
çıktısı üretir. Bu yetenek farkı browser'ın veya framework state'inin approval, publication, recall, suspension,
tenant, role veya audit authority'si olduğu anlamına gelmez.

İki sınır özellikle ayrılmalıdır:

1. **Managed hosting kolaylığı** build, CDN, preview, TLS, domain ve rollback işinin bir kısmını provider'a taşır;
   provider hesabı, build/runtime semantiği, quota, cache, DNS/TLS ve vendor coupling riskini ortadan kaldırmaz.
2. **Portable static/container** çıkış ve yeniden kurulum kabiliyetini artırabilir; static host'ta auth/API secret saklanmaz,
   container host'ta ise reverse proxy, patch, health, certificate, log, backup, restore ve incident işi proje sahibine
   veya otomasyona geri döner. Teknik olmayan tek owner için etkileşimli SSH/SQL/browser-devtools teşhisi kabul edilemez.

Bütün adaylar şu anda **HELD**'dir. Gerçek browser matrix'i, stale tab/role yarışı, response-loss ve false-success,
cache/service-worker invalidation, quarantine upload, WCAG klavye/focus, schema/API compatibility, supply-chain,
hosting/DNS/TLS, cost cap, clean-room exit ve no-owner runbook kanıtı yoktur. Güvenli hold/reconciliation yolu
kurulamayan veya owner'ın teknik debug yapmasını gerektiren kullanım **REJECT-IF-UNMITIGATED** olur.

## 2. Bağlayıcı karar bağlamı

Bu araştırma aşağıdaki mevcut sınırları browser/frontend düzeyine taşır:

- DEC-0034: Her alanın canonical transactional authority'si server/API mediated'dir; Internal Operations
  online-authoritative'dir; durable identified operation, bounded offline package, protected audit, ayrı object
  boundary, cross-plane restore/export/exit ve non-restorable negative/deletion/accepted-operation floor zorunludur.
- DEC-0035: Managed Supabase PostgreSQL/Auth/private Storage çalışma yönüdür; browser doğrudan genel DB/object
  authority alamaz; yüksek sonuçlu mutation'lar Kavriva API arkasındadır; RLS/Storage defense-in-depth'tir.
- DEC-0036: Her kullanıcı işlemi operation_id, payload fingerprint, expected version/generation ve görünür
  pending/submitted/accepted/conflict/held/failed/outcome-unknown/reconciling durumlarını taşır. HTTP 2xx,
  queue boşluğu, framework action completion veya optimistic state canonical acceptance değildir.
- DEC-0037: Authentication authority değildir. API current actor/session/issuer, security epoch, action, resource,
  tenant/scope, grant, competence, independence, policy, object generation ve operation identity ile karar verir.
  Browser guard, cached JWT claim, route middleware veya hidden UI button bu kontrolün yerine geçmez.
- DEC-0029 ve DEC-0030: Proje AI-operated, tek ve teknik olmayan owner içindir. Owner kod, SQL, SSH, log teşhisi,
  queue surgery veya incident repair yapmaz. Sonuçlar ürün dilinde ve owner-readable durumlarla görünür.
- DEC-0032: TRY 2.000–3.000/ay ilerideki non-store planning ceiling'idir; ödeme yetkisi değildir. Güvenlik,
  recovery, accessibility, monitoring veya exit bütçeye sığmıyorsa zayıflatılmaz; capability HELD kalır.

### 2.1 Frontend neyin sahibi değildir?

Frontend kullanıcı intent'ini toplar, API'ye taşır, server sonucunu gösterir, pending/unknown/held durumunu açıklar,
cache'i sınırlar, erişilebilir etkileşim sağlar ve ekran performansını ölçer. Aşağıdakiler frontend/runtime tarafından
kanıtlanamaz:

- 200 OK, React transition, Vue/Nuxt payload, Svelte action, Angular signal veya service-worker cache ile ürün kabulü;
- client-supplied tenant/resource/role/grant/version/object URL ile yetki;
- HTML/JS bundle içine gömülen public env, route guard veya hidden button ile secret/authorization;
- browser log'u, CDN log'u veya framework telemetry'si ile protected product audit;
- restore edilmiş eski bundle/cache ile güncel revoke, recall, deletion, suspension veya accepted-operation floor;
- preview/branch URL'si, host dashboard'u, green build veya rollback düğmesi ile cross-plane recovery;
- AI task context'i veya provider owner hesabı ile ürün onayı, billing, root/recovery authority.

## 3. Eşit karşılaştırma fikstürü

### 3.1 Ortak sınırlar

Karşılaştırma framework tanıtımı veya benchmark değildir. Dört aile için aynı:

| Fikstür | Bağlayıcı eşitlik kuralı |
|---|---|
| API ve data plane | Aynı Kavriva API endpoint'leri; browser generic DB/Data API/RPC/Storage write göremez. Aynı actor/session/epoch/grant/version ve operation ledger kullanılır. |
| High-consequence akış | Login/session refresh; role revoke; approval/publication/recall/suspension; file upload; large table/diff/graph; failed/timeout/retry; deploy old-tab. Aynı payload, latency, interruption ve network fault script'i kullanılır. |
| Browser | En az güncel Chrome, Edge, Firefox, Safari masaüstü; iOS Safari ve Android Chrome/uygulama WebView'i. MDN Baseline yalnız başlangıç sinyalidir; accessibility, assistive technology, performance ve security testinin yerine geçmez. |
| Security headers | HSTS/TLS, CSP (report-only rollout dahil), frame-ancestors, form-action, base-uri, connect-src, cookie attributes, CORS/CSRF ve no-store politikaları her ailede aynı niyetle doğrulanır. |
| Cache | Hashed immutable static asset ile user/API response ayrılır. Authenticated HTML/data ve operation status cache'lenmez; service worker varsa explicit version, update, kill-switch ve stale-tab testine girer. |
| Object | Upload private quarantine'a gider; client MIME/name/size bilgisi karar değildir. Scan, digest, classification, lineage ve manifest tamamlanmadan active/public handle yoktur. |
| Release | release_id, API/schema compatibility window, frontend asset generation, service-worker version ve rollback target birlikte kayıtlıdır. Code rollback database/schema rollback değildir. |
| Observability | Correlation ID + operation ID vardır; token, cookie, file content, PII ve secret browser/host log'una girmez. Browser telemetry protected audit yerine geçmez. |
| Cost | Normal ay, incident ayı, upgrade/compatibility dönemi ve clean-room exit aynı normalized BOM ile ölçülür. Headline framework veya host fiyatı tek başına TCO değildir. |
| Owner/AI | Owner yalnız anlaşılır onay ve geri dönüşsüz ürün kararını verir. AI task pack exact scope, credential class, stop condition, evidence ve forward recovery olmadan çalışmaz. |

### 3.2 Aday aileleri — mekanizma sinyali, kazanan değil

| Kod | Aile | Resmî mekanizma sinyali | Failure/TCO yüzeyi |
|---|---|---|---|
| **F1** | **React/Next** | Next static export HTML/CSS/JS dosyaları olarak herhangi bir static web server'da yayınlanabilir; API routes, rewrites, redirects, headers, ISR, default image optimization ve SSR gibi runtime özellikleri static export'ta desteklenmez. Self-host edilen Next için reverse proxy, cache koordinasyonu, multi-instance invalidation ve public/runtime env ayrımı gerekir. | React + Next + state/data/cache/SSR/RSC/server-action/third-party paketlerinin birleşik release yüzeyi; static/Node/edge sınırının yanlış anlaşılması; stale cache ve version skew. React escape hatch'leri veya Next server özelliği backend authorization proof değildir. |
| **F2** | **Vue/Nuxt** | Nuxt Node server, pre-rendered static, serverless ve edge ortamlarına deploy edilebilir. Nitro Node preset'i çalıştırılabilir Node entrypoint üretir; static ssr:true prerender veya ssr:false SPA fallback üretir. CDN proxy'lerinin script enjeksiyonu/hydration davranışı ayrıca doğrulanmalıdır. | SSR/SSG/SPA/Nitro preset/module/runtime-config ayrımı; pre-rendered payload ve CDN cache'in current auth/data sanılması; modül ekosistemi ve provider preset coupling. |
| **F3** | **Svelte/SvelteKit** | adapter-static tüm siteyi static dosya olarak prerender eder; adapter-node standalone Node server üretir; adapter-auto hedef provider'a göre adapter seçer ve hedef kesinleşince explicit adapter + lockfile önerilir. SvelteKit service worker build version'ı ile cache isimlendirebilir; eski tab kapanana kadar eski worker yaşayabilir. | Adapter/host semantiği, SvelteKit load/action/store state'i, optional service worker ve old-tab lifetime; Node adapter'da varsayılan 512 KB body limit ve 30 s graceful-shutdown gibi deployment kontratları. |
| **F4** | **Angular** | ng build static çıktı veya hybrid/server çıktı üretebilir; static uygulamada server route'ları index.html'e fallback yapmalıdır. Angular security rehberi template escaping/sanitization, AOT, CSP/Trusted Types ve HttpClient XSRF client yardımını anlatır; XSRF token'ı backend doğrulamazsa client interceptor tek başına koruma değildir. Service worker build'leri application version olarak ele alır. | Büyük CLI/build/configuration yüzeyi, service-worker version/cache, SSR/static ayrımı, AOT/CSP/Trusted Types escape hatch'leri, CLI ve üçüncü taraf component/CDK sürüm uyumu. |

Bu sinyaller resmî capability kanıtıdır; Kavriva üretim kanıtı değildir. Dört aday da aynı failure sonucu ve aynı
evidence gate'i karşılamadıkça HELD kalır.

### 3.3 Hosting modları ve sınırları

| Kod | Hosting modu | Ne taşınır? | Taşınmayan/kanıt gerektiren yüzey |
|---|---|---|---|
| **H1** | Managed framework-native/edge | Build, preview, CDN, TLS/domain, provider rollback ve gerektiğinde SSR/function runtime. | Provider account/DNS/TLS/quota/outage; framework adapter ve cache semantics; env/config'in rollback'de yeniden kurulup kurulmadığı; data/API/audit/object recovery; clean-room exit. |
| **H2** | Managed static artifact/CDN | dist/out/build veya Angular static çıktı; CDN/TLS/domain ve artifact promotion. | Auth/session/API server yoktur; route fallback, headers, cache invalidation, CSP/HSTS, large upload ve API CORS/CSRF ayrı plane'dir. Preview URL'si production security boundary değildir. |
| **H3** | Portable static server/CDN | Static dosya hash'leri, HTML/CSS/JS ve host-konfigürasyon manifesti. | Nginx/CDN route fallback, headers, compression, TLS renewal, DNS, artifact retention, rollback, service-worker kill/update, monitoring ve incident runbook proje işidir. Browser'a secret koyulamaz. |
| **H4** | Portable Node/container | OCI/image veya Node server + runtime dependencies, reverse proxy, health/readiness ve graceful shutdown. | Patch/CVE, image/base runtime, env/secret, persistent cache, uploads, TLS/DNS, logs, backup/restore, capacity, failover, exit ve owner-independent operation proje işidir. |
| **H5** | Split static frontend + managed API | Browser delivery ve API ayrı failure domain'leri; static frontend yalnız API contract'ı tüketir. | Cross-origin cookie/CORS/CSRF, DNS/TLS iki uçta, API compatibility, lost response, object upload, correlation/log privacy ve partial outage. Split daha güvenli veya daha ucuz kabul edilmez; kanıt ister. |

Managed olması operasyondan kurtulma değil, operasyon sorumluluğunun bir kısmını provider boundary'sine taşıma şeklidir.
Portable olması da exit'in otomatik olduğu anlamına gelmez; clean-room bootstrap ve owner-independent runbook yoksa
portable aday REJECT-IF-UNMITIGATED olur.

### 3.4 Frontend operation sözleşmesi

Her high-consequence mutation, UI state'inden bağımsız olarak şu alanları taşır:

operation_id, payload_fingerprint, actor/principal, session/issuer, security_epoch, action, tenant/scope,
resource_id, expected_version/generation, policy/grant/competence_generation, created_at/server_time, current_state,
audit_event_id, object_manifest_id, release_id ve recovery_owner.

| UI durumu | Kullanıcıya görünen anlam | İzin verilen frontend davranışı |
|---|---|---|
| PENDING/SUBMITTED | İstek gönderildi; canonical kabul henüz yok. | Aynı operation status'u izle; retry/close açıklaması ver; ikinci logical operation üretme. |
| ACCEPTED | Server canonical state + audit/object/version bağı kuruldu. | Başarı göster; canonical version/generation ve operation ID göster. |
| DENIED | Current actor/policy/scope izin vermedi. | Etki yok kanıtını ve ürün dilindeki nedeni göster; UI'yi zorla açma. |
| HELD | Güvenli positive action yapılmadı veya dependency belirsiz. | Hold nedenini, recovery owner'ını ve tekrar kontrol yolunu göster. |
| CONFLICT | Fingerprint/version/generation current authority ile uyuşmadı. | Eski local state'i başarı sayma; refetch/compare/explicit user choice. |
| OUTCOME_UNKNOWN | Response kayboldu; iş yapılmış veya yapılmamış olabilir. | Blind retry yok; status/reconcile; accepted görünene kadar false success yok. |
| RECONCILING | DB/object/audit/API/browser görünümü arasında uyumsuzluk araştırılıyor. | Positive next step kilitlenir; safe read/history mümkünse açık kalır. |

## 4. Failure-mode matrisi — eşit kötü durum fikstürü

Okuma kuralı: İlk yükümlülük dört aile için ortaktır. Aday hücreleri mekanizma ve ek failure yüzeyini gösterir;
framework primitive'i kabul kanıtı değildir. HELD güvenli hold tasarlanabilir fakat Kavriva kanıtı yok demektir;
REJECT-IF-UNMITIGATED hold/recovery/no-owner-debug yolu tasarlanamıyorsa uygulanır.

### 4.1 Identity, security ve operation sonucu

| ID / kötü durum | Ortak ürün sonucu, hold ve recovery | Aileye özgü risk | Hosting boundary |
|---|---|---|---|
| **F01 — Stale tab / stale role / revoke race** | Current actor/session/issuer/security epoch/grant/version her mutation'da API'de yeniden kontrol edilir. Stale tab DENIED/HELD; logout/revoke event, focus-return ve status refresh güvenli görünümü yeniden kurar. Cached claim/route guard authority değildir. | React/Next client cache/prefetch; Nuxt payload/composable singleton; Svelte store/load/SW; Angular singleton/signal/SW stale grant taşıyabilir. Hepsinde guard yalnız UX katmanıdır. | CDN/SSR cache'de user HTML/data private/no-store; static host auth kararını veremez. Managed edge cache ve portable headers ayrı test edilir. HELD. |
| **F02 — CSRF / XSS / CSP failure** | CSRF server-side Origin/CSRF token ve cookie policy ile; untrusted data context-appropriate encode/sanitize ile; strict CSP önce report-only sonra enforce ile kontrol edilir. CSP tek savunma değildir. | React dangerouslySetInnerHTML/unsafe URL; Vue v-html/useHead; Svelte raw HTML/DOM; Angular bypassSecurityTrust/raw DOM ve yanlış XSRF backend sözleşmesi incelenir. | Header injection managed host/static host/CDN config'e bağlıdır; analytics/third-party script CSP allowlist'ini genişletmez. REJECT-IF-UNMITIGATED. |
| **F03 — Session/token storage leak or mismatch** | Session identifier mümkünse Secure, HttpOnly, SameSite cookie; CSRF defense ayrı. Expiry/rotation/logout/revoke/tab sync ve XSS blast radius belgelenir. Browser bundle/public env'de secret yoktur. | Next public env build'de inline olabilir; Nuxt public runtime config; Svelte public env; Angular environment/build config hepsi browser'a açıktır ve secret değildir. | Static frontend secret tutamaz. Managed env değişikliği eski artifact/cache'e sızabilir; portable .env, image layer ve log riskleri taşır. HELD. |
| **F04 — Direct API bypass / BOLA / IDOR** | UI'de gizlenen route veya disabled button güvenlik değildir. API actor'dan tenant/scope türetir; ownership/grant/policy/version kontrol eder; client ID'leri yalnız input'tur. Direct curl/fetch, preview URL ve stale bundle aynı deny testini görür. | Next Route Handler/server action; Nuxt Nitro route/composable; Svelte form action/remote function; Angular router guard/HttpInterceptor transport'tur, Kavriva policy değildir. | CORS same-origin policy değildir; managed preview/public CDN, static asset ve browser devtools direct API testine tabi. REJECT-IF-UNMITIGATED. |
| **F05 — Lost response / commit-after-timeout** | OUTCOME_UNKNOWN; FAILED tahmini yapılmaz. Aynı operation_id status endpoint'i ve server ledger ile reconcile edilir; blind retry ve duplicate effect yasaktır. | Server action/fetch/streaming; Nitro/serverless timeout; Svelte action/adapter-node shutdown; Angular HttpClient timeout/interceptor sonucu commit değildir. | Edge/function timeout, CDN buffering, container SIGTERM ve browser network loss farklı failure domain'leridir. HELD. |
| **F06 — Optimistic UI false success** | Optimistic görünüm uncommitted etiketi ve rollback/reconcile state'i taşır; yalnız canonical accepted + version/generation/audit bağından sonra green success. | React transition/Suspense/cache mutation; Vue reactive merge; Svelte store/action; Angular signal/store optimistic update server outcome değildir. | Host mode fark etmez; API outcome unknown, offline cache veya stale HTML hiçbirinde başarı sayılmaz. REJECT-IF-UNMITIGATED. |
| **F07 — Browser cache / service worker / stale asset** | Hashed asset, HTML/data cache policy, SW version/update/kill-switch, old-tab drain ve API no-store kanıtlanır. Cached response approval/role/history authority değildir. | Next immutable/ISR/cache tag; Nuxt payload/route rules; SvelteKit old worker; Angular installed application version ayrı invalidation testine girer. | Managed CDN default cache/invalidation provider'a bağlıdır; portable host Cache-Control, ETag, SW headers'ını açıkça yönetir. HELD. |

### 4.2 Data, files, accessibility ve browser

| ID / kötü durum | Ortak ürün sonucu, hold ve recovery | Aileye özgü risk | Hosting boundary |
|---|---|---|---|
| **F08 — Large table / diff / graph** | Server pagination/filter/sort, bounded page size, virtualization/windowing, worker/off-main-thread parse, digest/selection preservation ve export fallback gerekir. Untrusted diff/HTML render edilmez; main-thread freeze duplicate mutation üretmez. | React concurrent/Suspense; Vue deep reactivity; Svelte DOM/SVG; Angular change detection/grid maliyeti ölçülür. Framework iddiası yerine gerçek fixture kullanılır. | Static/CDN yalnız bytes/latency etkiler; CPU/memory browser'dadır. SSR client table maliyetini yok etmez. HELD. |
| **F09 — File upload incomplete / unsafe / orphan** | Direct public write yok; private quarantine, scoped short-lived handle, size/type/content validation, malware/AV or CDR, digest/lineage/scan manifest ve orphan cleanup gerekir. Client filename/MIME/extension güvenilir değildir. | Next API/proxy body; Nuxt Nitro body; Svelte adapter-node default 512 KB body; Angular multipart/progress transport'tur, quarantine değildir. | Managed function timeout/body limit ve object integration; static/portable body limit; scan worker/quarantine/restore ayrı plane'dir. REJECT-IF-UNMITIGATED. |
| **F10 — Accessibility / keyboard / focus / status** | WCAG 2.2 AA hedefi: keyboard operable, no keyboard trap, visible focus, logical focus after route/modal/error, status/live region, reduced motion, contrast, table headers and screen-reader names. Pending/held/unknown yalnız renk/toast ile iletilmez. | Suspense/portal; Nuxt route transition/teleport; Svelte action lifecycle; Angular overlay/focus trap; component library kullanımı proof değildir. | CDN/SSR/static fark etmez; browser + assistive technology matrix'si release gate'idir. REJECT-IF-UNMITIGATED. |
| **F11 — Browser incompatibility / WebView drift** | Support matrix gerçek owner cihazlarıyla tanımlanır; feature detection/polyfill/fallback, upload/crypto/SW/streaming/keyboard paths ayrı test edilir. MDN Baseline eski cihaz, WebView ve screen reader kapsamı değildir. | React/Next hydration; Nuxt Nitro/client bundle; Svelte adapter/SW module-classic; Angular CLI targets/polyfills/SSR-static davranışı ayrıca test edilir. | Managed platform browser support garantisi vermez; portable server header/TLS/streaming uyumluluğu ek yüzeydir. HELD. |

### 4.3 Release, supply-chain, hosting ve observability

| ID / kötü durum | Ortak ürün sonucu, hold ve recovery | Aileye özgü risk | Hosting boundary |
|---|---|---|---|
| **F12 — Dependency / supply-chain compromise** | Manifest + lockfile, reproducible install, npm ci/eşdeğeri, audit/dependency review, SBOM, provenance/signature, postinstall review, Node/package pin ve vulnerability response gerekir. Unknown source SUPPLY_CHAIN_HELD. | React/Next RSC/router/grid; Vue/Nuxt/Nitro modules; SvelteKit/Vite/adapters; Angular CLI/Material/CDK/builders transitive tree ve plugin hook'ları incelenir. | Managed build image/plugin supply chain provider'a bağlıdır; portable image/base OS locklanır. Lockfile tree'yi sabitler, paketin güvenli olduğunu tek başına kanıtlamaz. HELD. |
| **F13 — Framework/runtime upgrade** | Patch/security upgrade ile major/adapter/runtime migration ayrılır. Staging/preview, contract/e2e, auth/security/CSP, WCAG, browser, large-data, upload, cost and rollback evidence olmadan auto-major production yok. | React/Next codemod; Nuxt migration/Nitro/Vue/Vite module; Svelte adapter/SW; Angular Update Guide/AOT/Material/CDK/SW migration. | Managed automatic build-image/framework update data/API/schema rollback'u değildir; portable runtime/image update release graph'ına bağlanır. HELD. |
| **F14 — Hosting outage / DNS / TLS / certificate** | Owner-readable SERVICE_UNAVAILABLE/read-only history/safe-stop; positive mutation ve approval durur. External probe, DNS/TLS expiry, HSTS/mixed-content, provider status, fallback page ve recovery owner kanıtlanır. | Next SSR/edge/static; Nuxt Nitro/CDN; Svelte adapter/SW stale shell; Angular static/server/SW partial health yanlış başarı göstermemeli. | Managed renewal/edge işi azaltır, account/DNS/provider outage kalır; portable certificate/reverse proxy/DNS renewal automation yoksa hard fail. HELD. |
| **F15 — Deploy rollback / schema/API incompatibility** | Frontend release_id, API N/N-1 compatibility, schema generation, asset hash, SW version, queue/object contract ve rollback target explicit'tir. Old bundle destructive new API'yi blind çağırmaz; rollback DB rollback değildir. | Next RSC/server action/cache; Nuxt payload/Nitro output; Svelte generated chunks/SW; Angular lazy chunks/SW asset group old tab compatibility ister. | Managed rollback artifact repoint edip env/API/schema/cache/DNS'i geri almayabilir; portable image/symlink rollback migration fence ister. REJECT-IF-UNMITIGATED. |
| **F16 — Logs / telemetry / privacy gap** | Correlation/operation/release IDs; token/cookie/PII/file bytes yok. Browser/CSP/server/CDN logs, source maps, analytics ve support export retention/redaction/deletion policy taşır. Log protected audit değildir. | React flight/dev overlay; Nuxt SSR payload/error; Svelte SW/cache trace; Angular dev mode/source map/interceptor context redaction gerektirir. | Managed log retention/subprocessor; portable disk/logrotate/remote sink/deletion. Missing correlation veya unbounded PII AUDIT/PRIVACY_HELD. |
| **F17 — Billing / quota / rate / build minute exhaustion** | Alert hard cap değildir. Limit yaklaşınca BILLING_HELD: positive mutation durur, history/pending operations okunur, overage/account restriction owner-readable olur. | Next SSR/ISR/image/edge/build; Nuxt Nitro/function/egress; Svelte adapter/egress/log; Angular build/artifact/SSR/SW/component package kullanımını BOM'a yaz. | Managed bundles hidden overage taşıyabilir; portable base host ucuz görünse de backup, monitoring, TLS, patch ve incident işi gerçektir. HELD. |

### 4.4 Exit, AI context ve no-owner operation

| ID / kötü durum | Ortak ürün sonucu, hold ve recovery | Aileye özgü risk | Hosting boundary |
|---|---|---|---|
| **F18 — Clean-room exit incomplete** | Source + lockfile + SBOM + build recipe; static/server artifact; API contract; auth/cookie/CSP/cache headers; object quarantine contract; telemetry; DNS/TLS/domain; SW/cache invalidation; release/rollback manifest birlikte export edilir. Clean host build/import, negative auth, deletion/revoke, upload/quarantine, stale asset ve rollback geçmeden EXPORT_PARTIAL kalır. | Next static output dışında RSC/server action/image/cache/env; Nuxt output/presets/modules; Svelte adapter/lockfile/SW; Angular dist/server/angular.json/builders/polyfills/SW config temiz ortamda yeniden kurulur. | Managed project clone/domain alias değildir. Portable host clean bootstrap kanıtı yoksa “taşınabilir” iddia sayılmaz; source silinmez. HELD. |
| **F19 — AI task context / collision / half-complete release** | Task pack exact scope, file/route ownership, operation IDs, release lock, dependency snapshot, forbidden actions, dry-run, stop condition, evidence, rollback/forward recovery ve reviewer taşır. Concurrent task aynı route/config/lockfile/provider environment'ına yazmaz. Yarım iş PARTIAL/RECONCILING. | React app/page/layout; Nuxt pages/app/server/.nuxt; Svelte routes/hooks/config/adapters/SW; Angular angular.json/env/routes/SW/dist collision yüzeyleridir. | Managed preview/promotion; portable image/tag/DNS değişiklikleri environment lock ister. Owner/billing/root token task context'ine girmez. REJECT-IF-UNMITIGATED. |
| **F20 — No-owner-debug / incident repair impossible** | Owner'a etki, durdurulan işler, güvenilir history, unknown/held operasyon, release, host/DNS/TLS/quota, güvenli next step ve tek onay verilir; stack trace/SSH/raw token verilmez. AI bounded health okuyup known artifact promote, safe-stop, scoped secret rotation ve support escalation yapabilir. | Next cache/proxy/Node; Nuxt Nitro/preset/hydration; Svelte adapter body/shutdown/origin/SW; Angular CLI/server/SW complexity runbook'la kapsanır. | Managed host işini azaltır ama account lock/quota/DNS/provider support kalır; portable interactive host debug bu owner modeliyle hard fail'dir. REJECT-IF-UNMITIGATED. |

## 5. Ortak acceptance, incident, restore ve exit sonucu

| Durum | Owner/kullanıcı görünümü | Frontend/hosting kanıtı |
|---|---|---|
| ACCEPTED | Operation ID, canonical version/generation, current role/scope ve güvenilir sonuç görünür. | API ledger + protected audit + object manifest + release/schema generation; UI bunu yalnız okur. |
| DENIED | Ürün dilinde neden; retry yeni yetki veya side-effect üretmez. | Current actor/session/epoch/scope/policy, no-effect proof, correlation ID. |
| HELD | Positive action yapılmadı; dependency, recovery owner ve tekrar kontrol yolu görünür. | Missing cache/auth/audit/object/API/host/cost evidence; hold monotonic ve restore'da korunur. |
| OUTCOME_UNKNOWN | Request tahmin edilmez; aynı operation ile status/reconcile beklenir. | Response loss/abort/timeout sonrası duplicate guard, canonical effect inspection ve audit/object status. |
| SERVICE_UNAVAILABLE | Safe history/read-only/safe-stop varsa sürer; mutation, approval, publication ve nonessential upload durur. | Independent health/DNS/TLS/provider/quota evidence; pending operation korunur. |
| BILLING_HELD | Limit/overage/account restriction anlaşılır; accepted history ve recovery kapanmaz. | Usage/cost/alert/stop evidence; composite cap ve hidden provider kalemi görünür. |
| OBJECT_QUARANTINE | Dosya güvenilir değil; preview/active/public handle yok. | Upload digest/size/type/scan/classification/lineage/manifests ve orphan cleanup. |
| RESTORE_QUARANTINE | Restore edilen UI/cache/data authority değildir; eski negative state yeniden açılmaz. | API/DB/object/audit/identity/config/SW/release import, protected floor karşılaştırması, no-cutover proof. |
| EXPORT_PARTIAL | Exit bitmedi; source hesap/authority silinmez veya yeni host production sayılmaz. | Plane-by-plane export, missing manifest, clean-room import/test, DNS/TLS cutover planı. |

### 5.1 Runtime/framework'ten bağımsız hard-fail cues

1. Browser UI, hidden route, cached role, client JWT claim, optimistic state veya service worker canonical authority sayılır.
2. Browser'a privileged DB/object/service key, long-lived bearer token veya unrestricted API credential bundle edilir.
3. Timeout/response loss sonrası blind retry, guessed success veya duplicate mutation yapılır.
4. CSRF yalnız framework interceptor'ına, XSS yalnız CSP'ye, authorization yalnız route guard'a bırakılır.
5. Quarantine/scan/digest/lineage tamamlanmadan active/public file handle veya public preview açılır.
6. Authenticated HTML/API/operation sonucu CDN, browser cache veya SW ile stale sunulur ve current epoch test edilmez.
7. Accessibility, browser matrix, data-heavy, upload, CSP/security veya privacy testleri “framework zaten yapıyor” diye atlanır.
8. Managed rollback schema/API/cache/SW/secret state'ini geri alıyor varsayılır; portable rollback yalnız image tag'a indirilir.
9. Billing/quota/overage/account closure ölçülmeden safety plane kapatılır veya sınırsız harcama kabul edilir.
10. Clean-room exit yalnız static dist/out/build, Docker image veya provider clone kopyası sayılır.
11. AI task owner/billing/root/service-role/unrestricted SQL/SSH/approval/publication/recovery authority taşır.
12. Teknik olmayan owner'ın SQL, SSH, browser devtools, raw logs, manual migration, cache surgery veya incident repair yapması gerekir.

## 6. TCO: normal, incident, upgrade ve exit cost shape

### 6.1 Maliyeti okuma kuralı

Bu araştırma satın alma teklifi veya fiyat sıralaması değildir. USD/TRY headline fiyatı Türkiye KDV/VAT, kur,
kart/banka, domain/e-mail/SMS, browser test cihazı, support/SLA, API/data/object shared plane, security tooling ve
AI-operability emeğini kapsamaz. Free, preview, quota alert, provider rollback veya static hosting'in “dosya serve
ediyor” olması güvenli production TCO'sunu sıfır yapmaz.

Normalized TCO:

mandatory host + build/deploy + CDN/egress + SSR/edge/request/CPU + API/data/object shared + auth/session
+ audit/log/monitoring + browser/a11y/security test + backup/restore + support + incident reserve + exit amortization
+ tax/FX/card/account uncertainty.

### 6.2 Cost class

- **Mandatory:** API boundary ve operation status; session/epoch; CSP/CSRF/XSS; asset/data cache policy; upload quarantine;
  protected audit/floor; monitoring/redaction; browser/accessibility evidence; dependency/upgrade controls; rollback;
  billing stop; restore/exit; AI task packs and no-owner runbook.
- **Deferrable only with explicit hold:** extra regions/read replicas, broad retention, premium support, advanced graph
  rendering, optional SSR/edge optimization, analytics and nonessential third-party widgets. Deferral safety/floor/exit'i
  bozamaz.
- **Forbidden saving:** direct API/object authority, public uploads, no-store'ı kaldırma, CSP/CSRF weakening, ignored
  dependency alerts, untested major upgrade, owner SSH/SQL, unbounded provider overage, missing clean-room export.

### 6.3 Horizon matrix

| Horizon | Dahil edilmesi gereken kalemler | Managed static/framework host | Portable static | Managed SSR/edge | Portable Node/container | Kabul/hold |
|---|---|---|---|---|---|---|
| **Normal ay** | Frontend artifact/build; CDN/egress; SSR/edge/requests; API/data/object shared; auth; logs/monitoring; CSP/telemetry; domain/DNS/TLS; browser/a11y/security smoke; backup/exit evidence. | Base ve convenience görünür olabilir; preview/build minutes, bandwidth, log retention, provider add-on, account/user/quota ayrıca yazılır. | Cash tabanı düşük olabilir; TLS/DNS, headers/cache, artifact retention, monitoring, invalidation ve API ayrı kalemlerdir. | Request/CPU/edge and cache cost + shared API/object; dynamic user pages no-store ve origin load; managed coupling. | Host cash cost + image/base runtime, reverse proxy, patch/CVE, certificates, backup, logs, capacity, owner-independent automation. | Exact BOM yoksa HELD; shared planes gizlenirse REJECT. |
| **Incident ayı** | Duplicate capacity; stale cache purge; rollback/forward fix; logs/export/forensics; provider support; emergency DNS/TLS; upload quarantine; user communication; overage. | Dashboard rollback hızlı olsa da API/schema/SW/cache/secret mismatch ve provider account failure ayrı maliyet. | Alternate artifact host, DNS propagation, header parity, cache purge ve support işi gerekir. | Partial provider health, function cold start/timeouts, egress/log spike ve API outage ayrıştırılır. | Failover/alternate host, manual capacity and cert/backup recovery; no-owner automation yoksa labour/human risk ağırdır. | Owner-readable stop/cap ve recovery kanıtı yoksa REJECT-IF-UNMITIGATED. |
| **Upgrade/compatibility** | Codemod/manual review; lockfile/SBOM; staging/dual-run; API N/N-1; browser/WebView/AT; large data/upload; CSP/privacy; SW/cache drain; rollback window; docs. | Auto build image/framework upgrade hidden work; preview/production promotion and provider preset changes. | Build artifact diff + header/cache/TLS/SW smoke; server-runtime migration az, browser compatibility cost aynıdır. | Adapter/provider semantics, streaming, env, cache and rollback; runtime bill during dual-run. | New image/Node/security patch, host test, drain/health, cert and state migration. | Rehearsal/evidence yoksa UPGRADE_HELD; major auto-promote forbidden. |
| **Restore drill** | Isolated host; frontend source/lockfile/artifact; API contract; auth/config; object/audit/floor; cache/SW revocation; DNS/TLS; negative tests; reviewer; egress/time. | Provider project clone/rollback tek başına yeterli değildir; build env, env vars, API/schema and SW tested. | Clean static host + API endpoint and headers; domain remains source until cutover proof. | Function/edge artifact, bindings, cache and provider configuration + API/data planes. | Image registry, base runtime, secrets reissue, volumes, reverse proxy, logs and DNS/TLS independent restore. | Anti-resurrection/old-role/old-cache tests fail ise RESTORE_QUARANTINE. |
| **Clean-room exit** | Source + lockfile + SBOM; artifact recipe; API/auth/object/audit contract; headers; cache/SW; telemetry; domain/DNS/TLS; support; dual-run/cutover; decommission/retention. | Provider-specific adapters, preview, rollback, build image and account artifacts; export fees/egress. | Artifact portable only if clean host and header/cache/security behavior reproduced. | Runtime adapter/edge semantics and cache invalidation contract; provider-specific functions replaced. | Operating knowledge, host/cert/backup/runbooks and portable image/import; operator burden highest. | Missing plane EXPORT_PARTIAL; source deletion prohibited. |

### 6.4 Ailelerin cost shape'i — sıralama yok

| Aile | Static path cost shape | SSR/edge/container path cost shape | Upgrade/exit/owner note |
|---|---|---|---|
| React/Next | Artifact/CDN path runtime açısından sınırlı; Next server özellikleri kullanıldıkça static boundary'den çıkılır. | Node/edge/managed framework path; cache coordination, server/client boundary, image/ISR/RSC and preview surfaces add work. | React/Next/Node/RSC ecosystem and provider coupling; static portability unsupported runtime özellikleri dışlandığında ve API external kaldığında değerlendirilebilir. |
| Vue/Nuxt | Nuxt generate/SSG/SPA output static host'a gidebilir; payload and route fallback correctness cost. | Nitro Node/serverless/edge preset, modules and runtime config; cross-provider adapter tests. | Generated output/modules/presets and Vue/Nuxt major migration; clean-room hidden provider state'i kopyalamaz. |
| Svelte/SvelteKit | adapter-static low runtime path; SW optional but cache/update/old-tab evidence cost ekler. | adapter-node/edge adapters, body/shutdown/origin limits and adapter-specific deploy behavior. | Explicit adapter/lockfile/SW invalidation; small artifact API, browser, a11y veya owner runbook costunu kaldırmaz. |
| Angular | Static dist path SSR runtime'ını azaltır ama route fallback, headers, SW ve browser/AT evidence ister. | Angular server/hybrid output, build/server configuration, SW and CLI/runtime compatibility. | CLI/Angular/Material/CDK/update guide and generated config work; sanitizer/XSRF helper server/supply-chain/no-owner proofunu azaltmaz. |

### 6.5 Budget-hold

Cost evidence base, usage, quota/overage, logs, build/preview, egress, API/data/object shared cost, monitoring,
support, restore drill and exit amortization göstermelidir. Aile normal ayda ucuz olup incident/upgrade/exit'te pahalı
olabilir; hiçbir horizon security/data-continuity hard fail'ini offset etmez. Unknown, unbounded veya owner-paid manual
repair BILLING_HELD kalır.

## 7. Operability: tek teknik olmayan owner ve bounded AI

### 7.1 Owner'ın yapacağı / yapmayacağı

**Owner'ın yapabileceği:** ürün dilinde approve/deny/hold; maintenance window onayı; safe stop/read-only tercihi;
harcama/overage kararının anlaşılır onayı; provider support escalation; geri dönüşsüz legal/product kararları.

**Owner'ın yapmayacağı:** SQL/SSH; raw browser devtools; manual cache/service-worker surgery; log grep/redaction;
dependency resolution; secret extraction; queue/object repair; migration/rollback command; certificate/DNS record surgery;
framework upgrade conflict çözümü; approval/publication/recovery authority'yi AI'ya devretme.

### 7.2 AI task-pack minimumu

Her AI görevi task_id, objective, exact route/file/config scope, read/write list, release lock, operation IDs,
actor/tenant scope, credential class (owner/billing/root/service-role yasak), dry-run, expected precondition,
forbidden actions, stop conditions, cost/quota ceiling, browser/security/a11y test list, evidence artifact,
rollback/forward recovery, independent reviewer ve owner-readable handoff taşır.

AI UI'yi green göstermek için API response'u tahmin edemez; task yarım kaldığında PARTIAL/RECONCILING bırakır.
Concurrent AI tasks aynı route/config/lockfile/release/domain environment'ına yazamaz. Generated .next, .nuxt,
.svelte-kit ve dist canonical source veya audit yerine geçmez.

### 7.3 Incident çıktısı

Incident runbook owner'a etki, durdurulan işler, güvenilir kalan history, unknown/held operation sayısı, release_id,
host/DNS/TLS/quota durumu, güvenli sonraki adım, owner'dan beklenen tek onay, recovery owner ve kanıt bağlantılarını
verir. Stack trace, secret, raw token, PII veya “terminalde şu komutu çalıştır” owner çıktısı değildir.

## 8. No-code evidence gates

Aşağıdaki gate'ler tüm dört aile ve seçilen hosting modunda aynı fixture ile kapanmadan Phase-5 ADR'ye giriş yoktur.

| Gate | Minimum evidence | Reject/hold cue |
|---|---|---|
| **WEB-01 Identity/stale** | Revoke/role/epoch yarışında stale tab, old route, back button, second tab ve SW old version aynı server deny/hold sonucunu alır; accepted effect only current generation. | UI guard veya JWT claim authority sayılıyorsa REJECT. |
| **WEB-02 Web security** | CSRF positive/negative; XSS contexts/escape hatches; CSP report-only → enforce; Trusted Types decision; cookie attributes; CORS/direct fetch/BOLA tests; no secret bundle. | CSP tek savunma, interceptor tek CSRF veya browser route guard authorization ise REJECT. |
| **WEB-03 Outcome/optimism** | Lost response, abort, timeout, duplicate retry, reload and offline transition; same operation status; no false green; OUTCOME_UNKNOWN visible. | HTTP success/optimistic cache guessed acceptance ise REJECT. |
| **WEB-04 Cache/release** | Asset hash, HTML/API no-store, CDN/host headers, SW install/update/kill, old tab, rollback and API N/N-1 schema compatibility. | Stale authenticated content or rollback that ignores API/schema/cache/SW is REJECT. |
| **WEB-05 Data/a11y/browser** | Large table/diff/graph fixture; memory/frame/input latency; keyboard-only and screen-reader path; focus/status/error; support browsers/WebViews; graceful feature fallback. | Framework handles it iddiası, keyboard trap veya hidden status REJECT. |
| **WEB-06 Upload quarantine** | Incomplete/resume/retry/duplicate/large/malicious/type-confusion upload; scoped handle; digest/scan/classification/lineage; orphan cleanup; no active/public before manifest. | Client validation veya public object write REJECT. |
| **WEB-07 Supply-chain/upgrade** | Lockfile/reproducible build/SBOM/audit/provenance; dependency review; staged patch/major upgrade; codemod/manual diff; old client/API; rollback. | Unpinned build, unreviewed postinstall/package, auto-major production HELD/REJECT. |
| **WEB-08 Hosting/continuity** | Managed and portable failure model; provider/DNS/TLS/cert outage; safe-stop/read-only; health/probe; known-good promotion; clean deploy rollback; no owner SSH. | Account/DNS/TLS/provider outage or cert renewal manual debug gerektiriyorsa REJECT. |
| **WEB-09 Logs/privacy/cost** | Correlation IDs; no token/cookie/PII/file bytes; retention/deletion; CSP/telemetry redaction; normal+incident+upgrade cost BOM; quota/overage hard stop. | Logs audit sanılır, hidden PII/third party, unbounded spend veya no billing hold varsa REJECT. |
| **WEB-10 Clean-room exit** | Build/import source+lockfile+SBOM ile başka host'ta; API/auth/object/audit/floor; CSP/cache/SW/headers; DNS/TLS; negative auth/deletion/revoke; dual-run/cutover. | DB/image/provider clone alone veya artifact/config/identity/observability eksikse REJECT. |
| **WEB-11 AI/no-owner** | Exact task packs; secret/authority boundary; collision/release lock; bounded diagnostics; owner-readable incident; forward recovery and reviewer. | Owner SQL/SSH/devtools/log surgery veya AI owner/root/approval authority ise REJECT. |

## 9. Phase-4 disposition ve Phase-5 giriş koşulu

### 9.1 Bu araştırmanın disposition'ı

- React/Next, Vue/Nuxt, Svelte/SvelteKit ve Angular eşit aday aileleri olarak tutulur; winner yoktur.
- Managed framework host, managed static/CDN, portable static, portable container ve split frontend/API eşit hosting
  modları olarak tutulur; provider veya plan onaylanmamıştır.
- Browser cache/service worker, optimistic UI, route guard, framework security helper, provider rollback, CDN green status,
  static artifact, container image ve host dashboard kendi başına product acceptance/recovery/audit/exit kanıtı değildir.
- Her aile/mod için unresolved critical gate HELD; güvenli hold/recovery/no-owner path kurulamayan kombinasyon
  REJECT-IF-UNMITIGATED'dir.
- Kod, prototype, provider hesabı, purchase, migration, deploy veya production experiment yapılmamıştır.

### 9.2 Phase-5 ADR'den önce istenecek ortak pack

1. Browser-to-API authorization matrix: browser, static host, SSR/edge, API, RLS/policy, object handle, preview, support,
   provider console ve billing paths; her biri allow/deny/hold/unknown sonucu.
2. WEB-01..11 walkthrough; stale tab/role, CSRF/XSS/CSP, token, direct bypass, lost response, optimistic false success,
   cache/SW, data-heavy, upload, accessibility, browser, supply-chain, upgrade, outage, rollback, log/privacy, billing,
   exit, AI collision ve no-owner incident fixture'ları.
3. Operation ledger/state machine: same ID retry, duplicate, conflict, network loss, browser close, old tab, cache hit,
   restore and provider outage; API effect/audit/object/generation reconciliation.
4. Framework/hosting release graph: source, lockfile, SBOM, Node/browser targets, build artifact, env schema, API/schema
   compatibility, cache/SW generation, DNS/TLS, monitoring and rollback.
5. Quarantine-first upload and protected audit/floor recovery; frontend only scoped object handle görür.
6. Clean-room build/import/cutover outside source host; negative authorization, deletion, revoke/recall/suspension,
   accepted-operation and old-cache anti-resurrection tests.
7. Current staged cost sheet with normal/incident/upgrade/restore/exit horizons; usage, overage, quota, egress,
   build/preview, logs, test devices, support and tax/FX uncertainty; no unapproved purchase assumption.
8. AI task packs, secret/authority boundary, collision lock, owner-readable incident outputs and independent review.

## 10. Primary source ledger and repository evidence

### Framework/runtime primary sources

- [Next.js Static Exports](https://nextjs.org/docs/pages/guides/static-exports) — static output and unsupported runtime features.
- [Next.js Self-Hosting](https://nextjs.org/docs/app/guides/self-hosting) — reverse proxy, env, cache, multi-instance and streaming considerations.
- [Next.js Deploying to Platforms](https://nextjs.org/docs/app/guides/deploying-to-platforms) — Node runtime and platform capability boundary.
- [Next.js Codemods/Upgrade](https://nextjs.org/docs/app/guides/upgrading/codemods) — automated upgrade is not release evidence.
- [React Versions](https://react.dev/versions) and [React 19 Upgrade Guide](https://react.dev/blog/2024/04/25/react-19-upgrade-guide) — version/support and migration signals.
- [Nuxt Deployment](https://nuxt.com/docs/3.x/getting-started/deployment) — Node, static, serverless and edge output modes.
- [Nuxt Upgrade Guide](https://nuxt.com/docs/4.x/getting-started/upgrade) — migration and compatibility signals.
- [SvelteKit Static Site Generation](https://svelte.dev/docs/kit/adapter-static) — prerender/static boundary, fallback and strict output check.
- [SvelteKit Node Server](https://svelte.dev/docs/kit/adapter-node) — standalone Node, body-size, proxy and shutdown contract.
- [SvelteKit Zero-Config Deployments](https://svelte.dev/docs/kit/adapter-auto) — provider adapters and explicit lockfile recommendation.
- [SvelteKit Service Workers](https://svelte.dev/docs/kit/service-workers) — versioned cache, old-tab update and stale-data warning.
- [Angular Deployment](https://angular.dev/tools/cli/deployment) and [ng build output modes](https://angular.dev/cli/build) — static/server artifact and route fallback.
- [Angular Security](https://angular.dev/best-practices/security) — XSS, CSP/Trusted Types, AOT and client-half XSRF limitations.
- [Angular Service Worker DevOps](https://angular.dev/ecosystem/service-workers/devops) — installed application version/cache behavior.
- [Angular Update Guide](https://angular.dev/update-guide) — versioned migration procedure.

### Browser, security, accessibility and supply-chain primary sources

- [MDN secure cookies](https://developer.mozilla.org/en-US/docs/Web/Security/Practical_implementation_guides/Cookies) and [HTTP cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cookies) — Secure, HttpOnly, SameSite, scope and storage considerations.
- [MDN fetch](https://developer.mozilla.org/en-US/docs/Web/API/Window/fetch) — network rejection versus HTTP error response; UI must inspect status and operation state.
- [MDN CSP header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy) and [CSP implementation](https://developer.mozilla.org/en-US/docs/Web/Security/Practical_implementation_guides/CSP) — header, report-only and defense-in-depth boundaries.
- [MDN Service Worker API](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) and [Using Service Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers) — cache interception, install/activate/update and old-cache behavior.
- [MDN Baseline compatibility](https://developer.mozilla.org/en-US/docs/Glossary/Baseline/Compatibility) — browser support summary and its explicit limits.
- [MDN TLS](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Transport_Layer_Security) and [HSTS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Strict-Transport-Security) — certificate, HTTPS, mixed-content and no-bypass behavior.
- [OWASP XSS Prevention](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html) — contextual encoding, framework escape hatches and CSP limits.
- [OWASP CSRF Prevention](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Request_Forgery_Prevention_Cheat_Sheet.html) — server-side CSRF defense and token/origin controls.
- [OWASP Session Management](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html) — session identifier and lifecycle controls.
- [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html) — deny-by-default and server-side per-request authorization.
- [OWASP File Upload](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html) — allowlists, isolation/quarantine, AV/CDR and public retrieval risk.
- [OWASP Logging](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html) — security logging, sensitive-data handling and retention considerations.
- [W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/) — keyboard operability, no keyboard trap and accessible interaction requirements.
- [npm package-lock](https://docs.npmjs.com/files/package-lock.json) and [npm audit](https://docs.npmjs.com/auditing-package-dependencies-for-security-vulnerabilities) — reproducible dependency tree and vulnerability review.
- [npm package provenance/signatures](https://docs.npmjs.com/viewing-package-provenance/) — source/build/publisher evidence and its limitations.
- [GitHub dependency review](https://docs.github.com/en/code-security/concepts/supply-chain-security/dependency-review) — manifest/lockfile change review and vulnerability signal.

### Managed/portable hosting representative and repository evidence

- [Vercel rollback](https://vercel.com/docs/cli/rollback) and [promotion/rollback behavior](https://vercel.com/docs/deployments/promoting-a-deployment) — representative managed-host artifact promotion; env/data/schema/cache rollback must still be evidenced separately.
- [DEBATE-011 — API Runtime Failure, TCO ve Operability](DEBATE-011__API_RUNTIME_FAILURE_TCO_RESEARCH.md) — shared operation, runtime, audit, object, billing, restore, exit and owner boundaries.
- [DEBATE-010 — Identity Failure/Threat Research](DEBATE-010__IDENTITY_FAILURE_THREAT_RESEARCH.md) — session, issuer, epoch, role/grant and revocation boundaries.
- [DEBATE-008 — Stack Architecture Fit Research](DEBATE-008__STACK_ARCHITECTURE_FIT_RESEARCH.md) — candidate equivalence, portability, exit and AI-operated owner fixture.
- DEC-0029..0037, 04_TECH_STRATEGY/EVALUATION_CRITERIA.md, 04_TECH_STRATEGY/EVALUATION_PROTOCOL.md — repository decision and gate context.

## 11. Handoff

Bu belge yalnız Phase-4 no-code adversarial research'tür. Dört frontend ailesi ve beş hosting modu eşit kötü-durum
fikstüründe tutulmuştur. Hiçbir winner, framework, provider, plan, domain, runtime, payment veya production deployment
onaylanmamıştır. WEB-01..11 evidence pack bağımsız review ile kapanmadan Gate 4 -> 5 geçişi kapalıdır.

