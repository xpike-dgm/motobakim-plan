# DEBATE-012 — Internal Operations Web Frontend ve Hosting Yönetici Önerisi

Status: `REVIEWED / SUPERSEDED BY CORRECTED JUDGE SYNTHESIS / NO WINNER / ADR NOT READY`
Date: `2026-09-19`
Scope: `NO-CODE / NO ACCOUNT / NO PURCHASE / GATE 4 -> 5 CLOSED`

> **Correction note:** Independent reviews and equal four-way audits rejected the proposal's React conditional-leader,
> Angular fallback and lower-priority Vue/Svelte language. The authoritative corrected conclusion is
> `DEBATE-012__JUDGE_SYNTHESIS.md`: all four families are equal `HELD`, with no framework winner. The CSR-first static
> artifact/CDN + Kavriva API pattern is only a conditional render/hosting starting direction.

## 1. Teknik olmayan kısa anlatım

Kavriva'nın şirket içi tarayıcı uygulaması basit bir istatistik paneli olmayacak. Araştırma, kaynak ve kanıt, teknik
veri, içerik hazırlama, değişiklik karşılaştırma, inceleme, onay, yayınlama, geri çağırma ve geçmiş takibini aynı kontrollü
üründe yürütecek. Bu nedenle seçilecek web teknolojisinin yalnız güzel ekran yapması değil; büyük ve karmaşık çalışma
ekranlarını, klavye kullanımını, erişilebilirliği, eski sekme güvenliğini ve hata sonrası doğru durumu taşıması gerekir.

Dört teknoloji ailesi incelendi. İlk taslağın React/Next'i AI aşinalığıyla öne çıkarma önerisi sonraki bağımsız
review'ler ve eşit dört-yol denetimi tarafından reddedildi. React/Next, Angular, Vue/Nuxt ve Svelte/SvelteKit eşit
`HELD` adaylardır; bugün framework kazananı yoktur. Tarayıcı uygulamasının statik mi, küçük bir güvenli sunucu kabuğuyla
mı yayımlanacağı framework seçiminden ayrı kanıtlanacaktır.

Hiçbir framework güvenlik yetkisi değildir. Ekrandaki gizli düğme, route guard, server action veya framework cache'i
onay/yayınlama hakkı vermez; bütün kritik kararlar daha önce onaylanan Kavriva API tarafından tekrar kontrol edilir.

## 2. Karar sınırı

Bu öneri:

- web framework ailesi ile hosting/render biçimini ayrı kararlar olarak tutar;
- dört aday için ortak değerlendirme sınırı kurar; ilk shortlist sıralaması Judge tarafından geri çekilmiştir;
- dense workspace, accessibility, security, deployment, TCO ve exit karşılaştırmasını kurar;
- Phase 5 gerçek evidence ve reversal gate'lerini tanımlar.

Bu öneri şunları seçmez:

- exact React/Angular/Next sürümü, component/table/editor/graph/state/form/test kütüphanesi;
- static SPA, Next server shell, SSR, BFF, container, CDN veya hosting provider;
- cookie/token/session biçimi, CSP ayrıntısı, browser support sayıları;
- domain, region, plan, hesap, abonelik veya ödeme;
- route/component kodu, prototip, executable task simulation, deployment veya ADR.

## 3. Devralınan bağlayıcı yönler

- `DEC-0021`: Internal Operations browser-based'dir; desktop wrapper yeniden açılmadı.
- `DEC-0026`: authentication authority değildir; least privilege, separation of duties, protected audit ve
  quarantine-first ingestion zorunludur.
- `DEC-0028/0029`: proje AI-operated, Obsidian-compatible ve task-addressable olacaktır; owner kod/debug yapmaz.
- `DEC-0034/0035`: browser generic DB/Storage authority taşımaz; sensitive yollar Kavriva API arkasındadır.
- `DEC-0037`: privileged işlemler current session/epoch, transaction-bound step-up ve activation gate ister.
- `DEC-0038`: stable operation, `OUTCOME_UNKNOWN`, protected audit receipt, long-job gate, state dictionary ve
  no-owner-debug web istemcisinde de aynen korunur.

## 4. Framework'ten bağımsız zorunlu web sözleşmesi

### 4.1 Ürün çalışma alanları

Seçilecek yapı şu iş yüzeylerini güvenle taşımalıdır:

- coverage/research queue ve motorcycle/variant workspace;
- source/evidence/provenance graph;
- technical data/content editor;
- missing/stale/conflict review;
- reviewer/approval queue ve exact review packet/diff;
- release/publication, version lineage ve impact/recall;
- operations analytics ve audit/change history.

Kritik state, scope, source, evidence, uncertainty, version ve next action farklı sekmelere saklanarak görünmez hale
getirilemez.

### 4.2 Browser yalnız presentation ve work orchestration katmanıdır

- Browser route guard, hidden button, cached role veya framework server action ürün yetkisi değildir.
- Critical mutation Kavriva API'de current authorization + expected version/generation + audit readiness ile yeniden
  değerlendirilir.
- Direct DB/Data API/RPC/Storage/provider console yolu ürün mutation'ı yapamaz.
- File/media önce private quarantine'a gider; browser preview, MIME veya upload success active content authority değildir.

### 4.3 State ve response honesty

Web UI ortak API sözlüğünü kayıpsız gösterir: `ACCEPTED`, `QUEUED/SUBMITTED`, `DENIED`, `HELD`, `OUTCOME_UNKNOWN`,
`PARTIAL/RECONCILING`, `AUDIT_HELD`, `BILLING_HELD`, `ACCOUNT_HELD`, `DEPLOYMENT_HELD`, `OBJECT_QUARANTINE`,
`RESTORE_QUARANTINE`, `EXPORT_PARTIAL`, `SERVICE_UNAVAILABLE`, `RECOVERY_REQUIRED`.

Optimistic görünüm yalnız geçici/pending olarak etiketlenir. HTTP 2xx, toast, framework mutation completion, empty queue
veya cached response canonical success değildir. Response kaybolursa aynı operation ile status lookup yapılır.

### 4.4 Accessibility ve information density

- keyboard-only tamamlanabilir akış, visible focus, logical focus return ve no keyboard trap;
- screen reader name/state, table headers, diff/graph alternative representation ve live status;
- critical state'in yalnız renk, toast, icon veya hover ile anlatılmaması;
- browser zoom, large text, reduced motion ve practical responsive behavior;
- küçük ekranda high-consequence context saklanıyorsa mutation `HELD` veya supported viewport gerekir.

Framework/component library WCAG kanıtı değildir; gerçek browser + assistive technology evidence gerekir.

### 4.5 Dense data ve graph sınırı

Large queue/table/diff/graph için server-side pagination/filter/sort, bounded page, virtualization, stable selection,
off-main-thread parse gerektiğinde worker ve accessible textual alternative gerekir. Ana thread donması duplicate
mutation veya false success üretemez. SSR büyük client-side table maliyetini otomatik çözmez.

## 5. Eşit aday A — React + TypeScript ailesi, Next.js gerektiğinde kontrollü aday

### 5.1 Neden eşit aday?

- React'ın geniş kullanım alanı ve AI modellerindeki yoğun bilgi tabanı araştırma kolaylığı sinyalidir; seçim veya
  capability kanıtı değildir.
- React/Next ekosistemi dense table/editor/graph, accessibility ve testing için geniş seçenek yüzeyi sunar; exact paket
  güvenli/uygun kabul edilmez, ayrıca kanıtlanır.
- Next.js'in Active/Maintenance LTS politikası ve resmi self-host/static/deploy yolları değerlendirme temeli sağlar.
- Server-assisted same-origin shell/BFF gerekirse framework içinde kurulabilir; ancak Kavriva API authority'sini ikame
  etmez.

### 5.2 Riskler ve hard hold'lar

- React + Next + Node + router/cache/RSC/server action + üçüncü taraf paketler geniş dependency/release yüzeyi yaratır.
- Server/client boundary, framework cache/prefetch, old tab ve RSC/server action version skew false-current state
  yaratabilir.
- Next static export ile SSR/server action/image/ISR gibi özellikler birlikte varsayılamaz; hangi route'un hangi mode'da
  olduğu explicit olmalıdır.
- React ecosystem genişliği aynı zamanda ownerless grid/editor/graph paketi ve multi-AI design drift riskidir.
- Next managed-host kolaylığı provider lock-in veya hidden request/build/log cost'u gizleyebilir.

Bu nedenle liderlik geri çekilmiştir; exact React composition ve hosting mode `HELD`dir.

## 6. Eşit aday B — Angular ailesi

### 6.1 Neden eşit aday?

- Düzenli major cadence, Active/LTS takvimi ve resmi update/compatibility rehberi bakım sorumluluğunu daha görünür kılar.
- CLI, routing, forms, HttpClient, security rehberi ve accessibility primitives daha bütünleşik bir çalışma yüzeyi sunar.
- Katı conventions, farklı AI görevlerinin dosya/route/state sınırlarında tutarlı kalmasına yardımcı olabilir.
- Static artifact veya server/hybrid output seçenekleri vardır; Kavriva API external authority olarak kalabilir.

### 6.2 Riskler ve hard hold'lar

- Daha geniş framework/CLI/toolchain surface'i ve sık major cadence upgrade işi yaratır.
- Angular/TypeScript/Node/RxJS ve component/CDK compatibility closure'ı gerekir.
- Built-in XSRF/sanitization/router guard yalnız client/framework primitive'idir; API authorization kanıtı değildir.
- Dense component ecosystem ve AI task familiarity React kadar geniş varsayılamaz; aynı task simulation ile ölçülmelidir.
- Static/server/service-worker build biçimleri old-client/cache/drain ve hosting complexity taşır.

Angular daha disiplinli olduğu için otomatik güvenli veya daha ucuz sayılamaz; `HELD`dir.

## 7. Eşit adaylar C ve D

### Vue + Nuxt

Okunabilir component modeli ve universal/static/server seçenekleri güçlüdür. Nuxt support/LTS görünürlüğü, module
closure, accessibility/dense-control ecosystem ve AI-operated long-term upgrade kanıtı kapanmamıştır. Diğer üç aileyle
aynı fixture ve aynı kanıt kapısında eşit `HELD` kalır.

### Svelte + SvelteKit

Daha az boilerplate, route-level rendering ve form progressive enhancement olumlu sinyaldir. Ancak formal support,
major/adapter closure ve critical dense package/AI maintenance kanıtı açıktır. Diğer üç aileyle aynı fixture ve aynı
kanıt kapısında eşit `HELD` kalır.

### Remix / React Router

Araştırma kesitinde Remix 3 release candidate/reference durumundadır. Stable/support/security closure olmadan primary
finalist değildir. React composition kararı sırasında gelecekte yeniden incelenebilir.

## 8. Hosting/render yönü — framework seçiminden bağımsız

### H1 — Managed static artifact/CDN + browser → Kavriva API

**Artı:** düşük runtime operasyonu, ucuz/taşınabilir artifact ve hızlı rollback potansiyeli.  
**Eksi:** secure session/cookie/CORS/CSRF, same-origin, headers, cache invalidation, file upload ve API correlation ayrıca
çözülür; browser secret tutamaz.

### H2 — Managed server-assisted same-origin shell/BFF

**Artı:** HttpOnly session, same-origin routing, server-side header/CSP ve controlled API proxy için daha uygun olabilir.  
**Eksi:** ikinci server runtime, timeout, secret, cache, deploy, log, bill ve BFF'nin yanlışlıkla authority olma riski.

### H3 — Portable managed container

**Artı:** artifact/runtime/headers üzerinde kontrol ve host değiştirme yolu.  
**Eksi:** reverse proxy, TLS, patch, image, graceful drain, monitoring ve owner-debug riskini artırır.

### Önerilen render ilkesi

Internal Operations için public SEO gerekmez. Varsayılan hipotez authenticated client-rendered workspace + explicit API
calls'dır. SSR/server shell yalnız session/security, initial-load veya operational kanıtla gerekliyse route-by-route
açılır. User-specific HTML/data `private/no-store` olur; CDN/shared cache'e girmez. Service worker varsayılan offline
authority değildir ve privileged mutation'ı cache'lemez.

Bu ilke H1'i otomatik seçmez; cookie/session ve same-origin güvenliği H2 gerektirirse H2 eşit BOM ile değerlendirilir.

## 9. Eşit no-code senaryo sonucu

| Senaryo | React/Next | Angular | Ortak kabul sonucu |
|---|---|---|---|
| Stale tab/role/session | `HELD` | `HELD` | API current epoch/authz; UI read-only/deny/hold |
| CSRF/XSS/CSP | `HELD` | `HELD` | Server validation + encoding/sanitization + CSP fixture |
| Token/session leak | `HELD` | `HELD` | Browser secret yok; secure session/rotation/revoke |
| Direct API/BOLA/IDOR | `HELD` | `HELD` | UI guard authority değil; exact scope deny test |
| Commit sonrası response kaybı | `HELD` | `HELD` | `OUTCOME_UNKNOWN`; same operation status lookup |
| Optimistic false success | `HELD` | `HELD` | Pending etiketi; canonical accepted olmadan green yok |
| Cache/service worker/old asset | `HELD` | `HELD` | Hashed artifact, HTML/data policy, kill switch, old-tab drain |
| Large table/diff/graph | `HELD` | `HELD` | Equal data fixture, browser CPU/memory/a11y evidence |
| Unsafe/incomplete file upload | `HELD` | `HELD` | Private quarantine + manifest; upload success authority değil |
| Keyboard/screen reader/focus | `HELD` | `HELD` | Real browser/AT; component library proof değil |
| Browser incompatibility | `HELD` | `HELD` | Explicit support matrix + fallback/hold |
| Supply-chain compromise | `HELD` | `HELD` | Lock/SBOM/provenance/review; unknown dependency held |
| Framework/Node major upgrade | `HELD` | `HELD` | Staging + contract/security/a11y/browser evidence |
| DNS/TLS/hosting outage | `HELD` | `HELD` | Positive hold, safe read/history, owner-readable recovery |
| Deploy/API/schema mismatch | `HELD` | `HELD` | Release compatibility; `DEPLOYMENT_HELD`; forward recovery |
| Log/telemetry privacy | `HELD` | `HELD` | Redaction/retention/correlation; log audit değil |
| Billing/quota exhaustion | `HELD` | `HELD` | `BILLING_HELD`; accepted/history preserved |
| Clean-room host/framework exit | `HELD` | `HELD` | Source/build/artifact/config/header/cache/session evidence |
| AI task collision/half release | `HELD` | `HELD` | Task ownership/release lock/evidence/reviewer |
| Owner incident recovery | `HELD` | `HELD` | SQL/SSH/raw log/secret/queue repair yok |

Belgesel sonuç iki finalist için de `0 PASS / 20 HELD / 0 REJECT`tir. Aynı `HELD`, risk şekillerinin aynı olduğu
anlamına gelmez ve production uygunluğu göstermez.

## 10. Yönetici önerisi

Phase 4 için önerilen yön:

1. **Framework sıralaması yok:** React/Next, Angular, Vue/Nuxt ve Svelte/SvelteKit eşit `HELD`; kazanan/fallback yoktur.
2. **Composition açık:** Her aile static/client-rendered ve gerektiğinde server-assisted biçimleriyle aynı fixture'da
   karşılaştırılmadan bütün ürün için otomatik seçilmez.
3. **Eşit kanıt korunur:** Bir adayın başarısızlığı diğerini otomatik kazanan yapmaz.
4. **API authority sabit:** browser/framework server/BFF high-consequence product authority değildir.
5. **Render mode route-specific:** public SEO varsayılmaz; user-specific data no-store; privileged service-worker offline
   mutation yok.
6. **Design consistency contract:** approved Phase-3 screen/workspace architecture, shared state vocabulary, design token/
   component contract, accessibility acceptance and visual regression evidence bütün AI görevlerinde canonical olur.
7. **No-owner-debug:** managed hosting tercih edilebilir, fakat account/DNS/quota/rollback/support yolu owner'a teknik
   repair çıkarmayacak şekilde kanıtlanır.

Bu öneri React, Next, Angular veya bir hosting provider'ını user-approved/locked yapmaz.

## 11. Finalist kapanış için eşit no-code task simulation

Kullanıcı kararı öncesi başlayan üç planlama fixture'ı daha sonra dört aday için eşit biçimde tamamlanmıştır:

### WEB-TASK-001 — Evidence Review Workspace

Bir AI'nın, yalnız minimum context pack ile source/evidence/diff/provenance/decision paneli için task breakdown,
contract, component ownership, accessibility oracle, test/evidence ve handoff üretmesi. Kod yoktur.

### WEB-TASK-002 — Stale Session and Lost Outcome

Role/epoch commit sırasında değişirken publish request response'u kaybolur. UI'nın stale tab, transaction-bound step-up,
`OUTCOME_UNKNOWN`, status lookup, deny/hold ve audit reference davranışı tasarlanır.

### WEB-TASK-003 — Upgrade, Rollback and Exit

Framework security/major update, old tab, API N/N-1, cached chunks, service worker, host rollback ve clean-room rebuild
aynı release manifest'inde yürütülür. Owner yalnız plain-language hold/promote/support kararı verir.

Her task aynı input, output, forbidden scope, dependency count, unknown, owner intervention, reviewer ve evidence
formatını kullanır. Task simulation framework popülerliğini değil AI-operated work surface ve hidden dependency'yi ölçer.

## 12. Owner-readable maliyet kapısı

İki finalist aynı BOM'u taşır:

- framework/runtime/Node ve dependency maintenance;
- component/table/editor/graph/accessibility packages;
- build/preview/artifact retention and source-map custody;
- static CDN veya server/edge/container requests/CPU/memory/egress;
- domain/DNS/TLS/CSP headers;
- auth/session adapter ve Kavriva API traffic;
- logs/metrics/traces/error reporting/privacy retention;
- security/dependency scanning, SBOM/provenance;
- browser/assistive-tech matrix, upgrade rehearsal ve incident capacity;
- support/account/billing/quota;
- clean-room build/host exit ve decommission.

Her satır mandatory/deferrable/optional/scale-triggered, official date/plan/unit/quota/overage, tax/FX, stop action ve
normal/incident/upgrade/exit horizon'u taşır. Ücretsiz framework güvenli toplam maliyeti sıfır yapmaz.

## 13. Reversal ve hard-fail tetikleyicileri

Her adayın çalışma uygunluğu şu durumlarda reddedilir veya held kalır:

- server/client/cache/dependency yüzeyi diğer adaylardan daha çok unresolved critical task veya owner repair yaratır;
- dense grid/editor/graph veya accessibility closure yalnız ownerless/unmaintained packages ile mümkün olur;
- AI task simulations design/contract drift, collision veya incomplete release üretir;
- secure portable hosting/clean-room rebuild framework/provider coupling nedeniyle kapanmaz;
- normalized normal + incident + upgrade + exit BOM anlamlı biçimde daha kötü çıkar.

Hiçbir aile aynı gates'i geçmeden otomatik kazanmaz. Framework conventions/toolchain/major upgrade veya component
ecosystem no-owner-debug/AI-operability hedefini karşılamazsa `HELD` kalır.

Her aday için direct API bypass, stale authorization success, optimistic false success, quarantine bypass, critical
accessibility failure, unpinned supply chain, incompatible rollback, owner technical repair veya unsafe exit
`REJECT-IF-UNMITIGATED`tir.

## 14. Phase-5 gerçek evidence kapısı

- real supported browser + keyboard + screen reader + zoom/reduced-motion matrix;
- representative large table/diff/provenance graph performance and accessible alternative;
- stale session/role/epoch, CSRF/XSS/CSP, BOLA/IDOR, status disclosure and token/cookie tests;
- response-loss/duplicate/optimistic/cache/service-worker/old-tab fixtures;
- private file quarantine, upload interruption, malicious preview and object handle tests;
- framework/Node/dependency security upgrade, lock/SBOM/provenance and reproducible build;
- artifact promotion, API compatibility, deploy rollback/forward recovery and host outage;
- owner-readable incident/support/billing/quota runbook;
- normal/incident/upgrade/exit normalized BOM;
- clean-room build/deploy with source untouched until acceptance;
- bounded AI task pack, independent review and design consistency evidence.

## 15. Kullanıcı kararından önce açık kalanlar

- user decision on the corrected Judge synthesis;
- Phase-5 equal real evidence for all four families;
- exact framework, provider and route-specific render composition;
- user working-direction decision.

No framework, hosting provider, account, subscription, code, prototype, deployment, ADR or gate transition is approved.
