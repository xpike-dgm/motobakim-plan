# DEBATE-012 — Bağımsız Reviewer A: Mimari, Dense Workspace, Erişilebilirlik ve Eşdeğerlik

Durum: `HELD — adversarial no-code review / winner yok / ADR hazır değil`  
Tarih: `2026-09-19 (Europe/Istanbul)`  
İnceleyen: `Reviewer A — architecture, dense operations, accessibility, framework/render equivalence, AI-operability`  
Çalışma modu: Kod, prototip, executable spike, hesap, satın alma veya production testi yoktur.

## 1. Kısa hüküm

Yönetici önerisi doğru sınırları kuruyor: Internal Operations browser-based kalıyor, browser/framework server ürün
otoritesi sayılmıyor, yüksek sonuçlu işlemler Kavriva API arkasında tutuluyor, `OUTCOME_UNKNOWN` ve no-owner-debug
ilkeleri korunuyor, React/Next ile Angular otomatik seçilmiş ilan edilmiyor. Buna rağmen öneri henüz kendi eşdeğerlik
iddiasını kanıtlamıyor.

En önemli sorun, React/Next'in “AI'ların iyi bildiği geniş ekosistem” gerekçesiyle koşullu lider yapılırken Angular ile
eşit olmayan üç no-code görevinin, Vue/Nuxt ve Svelte/SvelteKit'in ise ancak finalistlerden biri hard-fail verirse
yeniden açılacak challenger'lar olarak bırakılmasıdır. Bu, framework capability'sini değil, önceden seçilmiş AI
alışkanlığını ölçer. Dense workspace ve accessibility maddeleri de doğru isimlerle anılıyor; fakat 12 workspace'in
context/handoff sözleşmesi, erişilebilir yoğun grid/graph davranışı, route-by-route render eşdeğerliği, component
ekosistemi closure'ı, AI task graph'ı, migration ve clean-room exit henüz kabul edilebilir kanıta dönüşmemiştir.

| Aday / yüzey | Bu review hükmü | Gerekçe |
|---|---|---|
| React + Next.js | `HELD / koşullu lider değil` | AI bilgisi ve ekosistem genişliği kanıt değildir; RSC/Next/render/cache/dependency closure kapanmamıştır. |
| Angular | `HELD / React ile eşit finalist` | LTS ve entegre araçlar lifecycle sinyalidir; dense/a11y/AI/upgrade/exit kanıtı yoktur. |
| Vue + Nuxt | `HELD / adil challenger` | LTS/module closure açıkları var; fakat aynı fixture çalıştırılmadan erken elenemez. |
| Svelte + SvelteKit | `HELD / adil challenger` | SvelteKit major/support/adapter closure açıkları var; fakat aynı fixture çalıştırılmadan erken elenemez. |
| Render/hosting biçimleri | `HELD / winner yok` | Static, CSR, SSR, hybrid, edge/container ve split API aynı route/ güvenlik/exit fixture'ında karşılaştırılmamış. |

Belge düzeyinde sonuç `REJECT` değildir; düzeltilebilir bir manager proposal incelenmektedir. Ancak gerçek adayda aşağıdaki
hard-fail davranışlarından biri görülürse ilgili framework/render/hosting bileşimi `REJECT-IF-UNMITIGATED` olur:
critical işlemin mouse-only veya color-only kalması, stale/old artifact ile pozitif authority, doğrudan provider/API
bypass'ı, false success, quarantine'siz object activation, uyumsuz rollback/exit veya teknik olmayan owner'ın debug/SQL/
SSH/queue surgery yapması. `HELD`, güvenli veya production-ready demek değildir.

### Önem dereceleri

- **CRITICAL:** Phase-5 ADR/eşdeğerlik kararı veya high-consequence UI güvenliği bu açık kapanmadan güvenilir biçimde kurulamaz.
- **MAJOR:** Gerekli sözleşme, fixture veya işletim kanıtı eksiktir; aday seçilmeden önce kapanmalıdır.
- **MINOR:** Tek başına capability'yi açmaz; terminoloji, authority veya karşılaştırma okunabilirliğini bozar.

## 2. Okunan kanıt tabanı ve kapsam notu

Bu review aşağıdaki belgelerin tamamı okunarak hazırlanmıştır:

- `00_CONTROL/AI_START_HERE.md`
- `00_CONTROL/CURRENT_STATE.md`
- `00_CONTROL/SOURCE_OF_TRUTH.md`
- `00_CONTROL/DECISION_LOG.md` — özellikle `DEC-0021`, `DEC-0028`–`DEC-0038`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md`
- `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKSPACE_ARCHITECTURE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_PRIMARY_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_FAILURE_TCO_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_MANAGER_PROPOSAL.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__JUDGE_SYNTHESIS.md`

Kullanıcı tarafından anılan `03_DESIGN/WORKSPACE_ARCHITECTURE.md` dosyası repository'de bulunmamaktadır; mevcut,
konuya doğrudan karşılık gelen `INTERNAL_DATA_CONTENT_OPERATIONS_WORKSPACE_ARCHITECTURE.md` canonical çalışma kaynağı
olarak kullanılmıştır. Bu review başka dosyaya dokunmaz.

Bağlayıcı karşılaştırma sınırı; `IDCO-RQ-001..064`, `WS-01..WS-12`, `IWEB-SURF-001..008`, `IWEB-QUEUE-001..007`,
`IWEB-DIFF-001..008`, `IWEB-TRACE-001..007`, `IWEB-A11Y-001..010`, `IWEB-RESP-001`, `WEB-AC-001..022`,
`DEC-0028` AI-native task graph, `DEC-0029` no-owner-debug ve `DEBATE-011` runtime-independent state/authority
sözleşmesidir. Framework dokümanındaki capability, bu product acceptance kanıtlarının yerine geçmez.

## 3. Bulgular özeti

| ID | Seviye | Uygulama | Kısa bulgu | Hükme etkisi |
|---|---|---|---|---|
| C-01 | **CRITICAL** | A+B+challenger'lar | React liderliği AI familiarity/ekosistem varsayımına dayanıyor; simülasyon yalnız React/Angular için planlanıyor. | Eşdeğer framework kararı kurulamaz; tüm adaylar `HELD`, winner yok. |
| C-02 | **CRITICAL** | A+B+challenger'lar | Render/hosting biçimleri route ve threat model düzeyinde eşitlenmemiş; authenticated CSR varsayılanı kanıtsız biçimde öne geçiyor. | Static/SSR/CSR/hybrid karşılaştırması kapanmadan ADR yok. |
| C-03 | **CRITICAL** | A+B+challenger'lar | Dense workspace için yalnız capability listesi var; scope/context, stable selection, pagination, diff/provenance/recall handoff ve graph fallback acceptance'ı yok. | Context kaybı güvenli approval/review/recall'ı bozabilir; `HELD`. |
| C-04 | **CRITICAL** | A+B+challenger'lar | Keyboard/AT, focus, status announcement ve yoğun grid/graph erişilebilirliği ölçülebilir oracle'a bağlanmamış. | Gerçek mouse-only/focus/color-only yol hard-fail; documentary `HELD`. |
| C-05 | **CRITICAL** | AI task/design graph | `DEC-0028` task-addressability, minimum context pack, collision/closure ve canonical design consistency manager önerisinde uygulanabilir task contract'ına dönüşmemiş. | No-code task gate kapanmadan Phase-5 implementation hazırlığı yok. |
| M-01 | **MAJOR** | A+B+challenger'lar | Component/table/editor/graph/upload/i18n/a11y ekosistemi varsayım olarak kalıyor; dependency closure ve escape hatch riski ölçülmüyor. | Package BOM, semantics, bakım, güvenlik ve exit kanıtı olmadan `HELD`. |
| M-02 | **MAJOR** | A+B+challenger'lar | React/Angular için üç görev; dense/a11y, component/design ve AI collision/exit görevleri eksik. Challenger'lar aynı görevleri almıyor. | Simulation sonucu seçim kanıtı sayılmaz; ortak fixture genişletilmeli. |
| M-03 | **MAJOR** | A+B+challenger'lar | Design consistency contract'ı adıyla var, fakat owner/version/change-control/state-token ve internal-web sınırı tanımlı değil. | Multi-AI drift ve consumer/internal semantik karışması `HELD`. |
| M-04 | **MAJOR** | A+B+challenger'lar | Upgrade/migration closure; exact lockfile, Node/TS/browser/AT matrix, API N/N-1, cache/SW, SBOM ve rollback prova zinciri eksik. | Codemod veya LTS iddiası upgrade PASS değildir. |
| M-05 | **MAJOR** | A+B+challenger'lar | Static/SSR/edge/container/split hosting için clean-room exit ve plane manifesti tamam değil; “portable managed container” de belirsizdir. | Provider clone, `dist`, image veya build artifact tek başına exit değildir; `HELD`. |
| M-06 | **MAJOR** | A+B+challenger'lar | BFF/server shell'in Kavriva API'ye yalnız replaceable transport olması ve direct-path negatif envanteri yeterince işletimsel değil. | BFF'nin yanlışlıkla authority olması veya cross-tenant/status disclosure riski. |
| M-07 | **MAJOR** | A+B+challenger'lar | Narrow viewport, zoom/large text, Turkish long labels, saved views, bulk selection ve “desktop-class required” davranışı acceptance'a bağlanmamış. | Kritik state gizlenebilir veya keyboard sırası bozulabilir. |
| m-01 | **MINOR** | A+B | “Koşullu lider / fallback” dili `NO WINNER` ve `HELD` sonucu ile gerilim yaratıyor. | Proposal seçime yönlendiriyor; terminology düzeltilmeli. |
| m-02 | **MINOR** | A | React core ile Next LTS aynı support iddiası gibi okunuyor; React'in bağımsız LTS matrisi yok. | React/Next/Node/RSC lock closure açık yazılmalı. |
| m-03 | **MINOR** | Hosting | H3 “portable managed container” ifadesi iki farklı operasyon modelini birleştiriyor. | Managed container ile portable container ayrı fixture olmalı. |
| m-04 | **MINOR** | Evidence | Requirements belgesinin üst status'ü `APPROVED WORKING ADDENDUM`, son handoff notu ise `DRAFT` diyor. | Authority okunurluğu için sonraki kontrollü doküman düzeltmesinde giderilmeli; bu review bunu değiştirmez. |

## 4. Ayrıntılı adversarial bulgular

### C-01 — React/Next liderliği ve shortlist süreci eşdeğer değil

**Kanıt.** Manager Proposal §5.1 React'i “AI'ların iyi bildiği geniş ekosistem” nedeniyle başlangıç lideri yapıyor;
§6 Angular'ı ilk alternatif/fallback, §7 Vue/Nuxt ile Svelte/SvelteKit'i finalist hard-fail verirse açılacak challenger olarak
konumluyor. §11 no-code task simulation yalnız React ve Angular için üç görev tanımlıyor. Oysa primary research dört
ailenin tümünü `HELD`, failure/TCO araştırması da aynı browser fixture'ını ve aynı evidence gate'lerini öngörüyor.

**Saldırı.** React hakkında modelin daha fazla ön bilgisi olması; React/Next'e daha kısa, Angular'a daha uzun, Vue/Svelte'e
daha eksik context verilmesini capability kanıtına dönüştürür. Angular'ın LTS takvimi lifecycle sinyalidir, dense
workspace veya accessibility PASS değildir. Nuxt/SvelteKit'in açıkları gerçek risk olabilir; fakat aynı task, package
closure ve exit fixture'ı çalıştırılmadan bu riskler ölçülmüş değil varsayılır. “Finalist hard-fail olursa challenger açılır”
önceki seçimin kendisini doğrulayan bir kapı üretir.

**Düzeltme.**

1. “React lideri” ve “Angular fallback” ifadeleri yalnız `conditional hypothesis` olarak etiketlenmeli; karar öncesi
   liderlik iddiası kaldırılmalı.
2. Dört aileye aynı input, aynı minimum context-pack şekli, aynı task output schema, aynı no-code model/rol, aynı
   dependency-discovery izni ve aynı reviewer rubric'i uygulanmalı. Framework-specific dokümana erişim kullanılacaksa
   dört adaya da aynı kuralla açılmalı.
3. Her adayın çıktısı; WS coverage, hidden dependency, task boundary, unresolved unknown, owner intervention, a11y
   oracle, migration/exit closure ve evidence quality üzerinden karşılaştırılmalı. AI popularity veya cevabın uzunluğu
   puan olmamalı.
4. Challenger'lar en az finalistlerle aynı screening fixture'ını almalı; bir aile ancak aynı hard-fail kuralı altında
   kapanmayan bir gap gösterirse `REJECT-IF-UNMITIGATED` olabilir.

**Öneriye etkisi.** Dört aile için `HELD / NO WINNER`. Bu review React, Angular, Vue veya Svelte seçmez.

### C-02 — Framework/render/hosting equivalence route bazında kurulmamış

**Kanıt.** Proposal §8 H1 managed static/CDN, H2 server-assisted same-origin shell/BFF ve H3 portable managed container
listeliyor; “authenticated client-rendered workspace”ı varsayılan hipotez yapıyor. Ancak hiçbir route/iş akışı için
static, CSR, SSR, hybrid/edge/container seçiminin aynı API, session, cache, CSP/CSRF, response-loss, cost ve exit fixture'ı
ile karşılaştırıldığı gösterilmiyor. Primary research her ailede route-level render sınırlarının farklı olduğunu, failure
research ise static/SSR/cache/SW/old-tab davranışının ortak hard gate olduğunu söylüyor.

**Saldırı.** React/Next App Router + RSC/Server Actions kullanılan, Angular ise yalnız CSR/HttpClient ile değerlendirilen
bir karşılaştırma eşit değildir. Static artifact'ta browser→API CORS/CSRF/cookie/redirect ve upload yükü artar; same-origin
shell bunu azaltabilir ama ikinci runtime, secret, timeout, cache ve BFF coupling getirir. SSR ilk görünümü hızlandırabilir,
fakat cached HTML/payload stale role, version veya negative floor taşıyabilir. CSR stale HTML riskini azaltırken büyük review
screen'inde initial load, main-thread freeze ve recovery UI riskini büyütebilir. Service worker, CDN veya prefetched route
hiçbir modda current authorization değildir.

**Düzeltme.** Her aday için, aynı route/capability matrix'i yazılmalı:

- WS-01/04/06/07/11/12 gibi high-consequence yüzeylerde browser-direct API, same-origin shell ve server-assisted/BFF
  çağrısının sınırı;
- static, CSR, SSR, hybrid/edge ve portable Node/container artifact'ının session, no-store, cache key, CSP/CSRF,
  stale-tab, response-loss, old-client/API N/N-1, upload ve operation status davranışı;
- initial-load/keyboard/screen-reader, large-table CPU/memory, latency, quota/egress, support ve clean-room exit;
- route başına `ALLOW/DENY/HELD/OUTCOME_UNKNOWN/PARTIAL/DEPLOYMENT_HELD` beklenen semantik durum.

Hiçbir mod kanıtlanmadan “CSR default” seçilmiş sayılmamalı; bu yalnız araştırılacak başlangıç hipotezi olarak kalmalı.
BFF/server shell varsa bütün yüksek sonuçlu command/read/status yolları Kavriva API'de kalmalı; BFF authority, audit veya
canonical cache olamaz.

**Öneriye etkisi.** Render/hosting tüm adaylar için `HELD`. Old cache/old tab/direct BFF path pozitif authority verirse
ilgili bileşim `REJECT-IF-UNMITIGATED`.

### C-03 — Dense workspace mimarisi sorumluluk listesi olarak kalıyor

**Kanıt.** Proposal §4.1 gerekli workspaces'i sayıyor ve §4.5 server pagination/filter/sort, bounded page,
virtualization, worker ve textual alternative istiyor. Fakat `WS-01..WS-12` için sorumluluk→route/surface→API contract→
state→handoff→focus context traceability matrix'i; workspace architecture §6'daki cross-workspace context contract'ın
gerçek bir acceptance fixture'ı yok. `IWEB-QUEUE-001..007`, `IWEB-DIFF-001..008` ve `IWEB-TRACE-001..007` yalnız niyet
olarak kalırsa dense UI güvenli review yüzeyi sayılmaz.

**Saldırı.** Coverage queue'dan variant detail'e gidince make/model/year/variant/modification scope, active filters veya
unresolved reason resetlenir. Bir source withdrawal'dan dependent claim/release/active-work impact'e gidince graph yalnız
görsel düğüm gösterir, relation type/status/date/actor kaybolur. Server pagination altında sıralama kararsızsa sayfalar
arasında duplicate/missing item oluşur. Virtualized grid yalnız görünür satırları AT'ye sunarsa keyboard/selection ve
bulk operation yanlış nesnede çalışabilir. Current value ile event/history aynı tabloda flatten edilirse silent overwrite
veya false “current” izlenimi doğar. Recall center aktif physical work ve safe recovery bağlantısını kaybederse yanlış
pozitif uygulama açılabilir.

**Düzeltme.** No-code pack'e aşağıdaki sözleşme eklenmeli:

- Her surface için WS ID, bounded object/scope, current state, version/generation, freshness, provenance/uncertainty,
  dependency/interaction depth, actor role, allowed/blocked next action ve operation/status ID.
- Scroll/pane/tab/back/filter/refresh/page change boyunca scope, active filter, selected object, draft, security epoch,
  review packet, sort order ve freshness korunmalı; reset varsa açık confirmation ve safe return olmalı.
- Server-side filter/sort/pagination deterministik olmalı; saved view, column visibility/density, pinned critical fields,
  cross-page selection, bulk preview/operation ID ve partial result semantiği aynı fixture ile sınanmalı.
- Current meaning, proposed meaning, prior/event history, provenance relation ve impact graph ayrı fakat bir adımda
  traversable kalmalı. Graph'in keyboard/linear equivalent'i ve table/diff fallback'i zorunlu olmalı.
- Narrow viewport'ta kritik write/review güvenli değilse `desktop-class view required` metni, safe read/return ve retained
  context gösterilmeli; kontrol sessizce gizlenmemeli.

**Öneriye etkisi.** Context veya state kaybı high-consequence review/publish/recall'a izin verirse ilgili bileşim hard-fail;
documentary aşamada `CRITICAL / HELD`.

### C-04 — Accessibility/keyboard sözleşmesi ölçülebilir acceptance'a dönüşmemiş

**Kanıt.** Proposal §4.4 keyboard-only, visible focus, screen reader, focus return, live status, reduced motion ve zoom'u
listeliyor; fakat conformance target, browser/AT matrix, keyboard sequence, representative component fixture'ı veya
non-visual graph oracle vermiyor. Primary research dört ailede de framework lint/Aria/compiler yardımının uygulama WCAG
kanıtı olmadığını; `IWEB-A11Y-001..010` ve `WEB-AC-014` gerçek browser/AT kanıtı istediğini açıkça ayırıyor.

**Saldırı.** Dense grid virtualization, portal/dialog, route transition, focus trap veya hydration; row/column header,
changed/unknown state, error association ve selection bilgisini screen reader'dan düşürebilir. `HELD` veya `OUTCOME_UNKNOWN`
yalnız renk, icon, toast veya disappearing alert ile anlatılabilir. Turkish uzun label/validation text 200–400% zoom'da
critical column'u veya focus target'ı örtebilir. Provenance graph canvas/SVG ise keyboard linear path olmayabilir. Step-up,
upload cancellation, stale-session re-auth ve lost-response status lookup mouse/visual flow'a sıkışabilir.

**Düzeltme.** ADR öncesi aynı erişilebilirlik oracle'ı tanımlanmalı:

- En az keyboard-only path: queue filter/sort/open, multi-pane traversal, row/bulk selection, diff/provenance traversal,
  review decision, cancel/retry/status lookup, upload/quarantine, step-up ve stale-session recovery.
- Focus visible/order/return, skip/landmark, dialog/alert/live-region, error-to-field/object association, table headers,
  sort/filter/selection/change semantics, non-color state ve graph linear alternative.
- Declared browser/OS/AT matrix, Turkish locale and long labels, 200%/400% zoom or chosen large-text target, high contrast,
  reduced motion and narrow desktop/tablet behavior. Exact support matrix is open, fakat “bir browser'da çalışıyor” kabul
  değildir.
- Automated lint/type warnings yalnız başlangıç sinyali; representative real-browser + screen-reader evidence zorunlu.

Bir framework veya component library “a11y built-in” olduğu için bu gate'i kapatamaz. Kritik yol mouse-only, focus-lost,
color-only veya assistive interpretation'sız kalırsa `REJECT-IF-UNMITIGATED`.

**Öneriye etkisi.** Dört aday ve tüm render biçimleri `HELD`; gerçek failure hard-fail.

### C-05 — AI task-addressability ve design consistency bağlayıcı bir çalışma sistemine dönüşmemiş

**Kanıt.** Proposal §10 ve §14 design token/component contract, visual regression, independent review ve bounded AI task
gereğini anıyor. Fakat `DEC-0028`'in minimum sufficient context pack, allowed/forbidden scope, Obsidian-compatible graph,
bidirectional requirement→task→test closure, collision lock, generated artifact ayrımı, reviewer/validator ve completion
evidence koşulları task şemasına çevrilmemiş. “React AI'lar tarafından iyi bilinir” bu boşluğu kapatmaz; Angular
convention'ları da otomatik task-addressability kanıtı değildir.

**Saldırı.** Yeni AI, tüm repo'yu okumadan yalnız bir WS-06 review panelini ele alır; canonical state dictionary,
focus oracle, API status envelope, approved design token veya recall semantics context pack'te yoksa lokal olarak makul
ama sistemle çelişkili bir surface planlar. İki AI aynı `ReviewPacket`, route config, design token, i18n, generated route
manifest veya service-worker/release file'ına dokunur. `.next`, `.nuxt`, `.svelte-kit`, `dist` veya generated Angular output
source/audit sanılır. Task “DONE” görünür ama WS-06→WS-07→WS-08/11 closure, negative cases veya independent evidence orphan
kalır.

**Düzeltme.** Her framework/render bileşimi için aynı machine-readable task pack minimumu zorunlu olmalı:

- objective, exact object/scope, allowed/forbidden paths, dependency graph links, context pack, API/state/design refs;
- expected preconditions, operation/generation, negative cases, hard stop, rollback/forward-recovery ve unresolved `HELD`;
- conceptual component ownership, canonical token/state version, generated/config surfaces, release lock ve collision rule;
- credential class/audience/expiry (kod aşamasında), reviewer/validator, evidence digest, owner-readable handoff ve next action;
- requirement→workspace→task→acceptance→test/evidence ile reverse orphan/gap detection.

Task simulation'da task sınırı, unknown sayısı, hidden dependency, touched conceptual surfaces, owner technical intervention,
design consistency finding ve reviewer rework ölçülmeli. Framework familiarity, output uzunluğu veya ekosistem popülerliği
puanlanmamalı. Yeni AI'nin işi için no-code simülasyonun amacı kod üretmek değil, bu closure'ın gerçekten adreslenebilir
olduğunu kanıtlamaktır.

**Öneriye etkisi.** `CRITICAL / HELD`; task graph ve design oracle kapanmadan implementation/ADR hazırlığı yok.

### M-01 — Component ecosystem “geniş seçenek” varsayımı closure değildir

**Kanıt.** Proposal React/Next için dense table/editor/graph/a11y/testing ekosisteminin genişliğini, Angular için
CLI/CDK/Aria/forms bütünlüğünü avantaj sinyali yapıyor; fakat exact package seçimi bilinçli olarak açık bırakılıyor.
Primary research her iki ailede de grid/editor/auth/query/i18n/observability paketlerinin core support'tan bağımsız
release/security/SSR/hydration/exit closure'ı olduğunu; Nuxt modules, Svelte adapters/packages için de aynı sınırın geçerli
olduğunu söylüyor.

**Saldırı.** React'in “geniş ekosistemi” daha fazla paket, farklı focus/state semantics ve unowned escape hatch getirir;
Angular CDK/Aria ise dense table veya graph'in gerçek AT davranışını garanti etmez. Vue/Nuxt module veya Svelte package
adı katalogda görünse bile maintenance, security advisory, license, Nuxt/SvelteKit/adapter compatibility ve replacement
kanıtı yoktur. Virtualized table, editor, diff, graph, upload, focus, i18n ve chart paketleri farklı event/DOM modeline
bağlanırsa canonical design system ve API state semantics bozulur.

**Düzeltme.** A/B/challenger için aynı capability BOM'u hazırlanmalı: table/grid + virtualization, editor/diff,
provenance graph + linear alternative, form/validation, state/data, i18n/Turkish, focus/ARIA, upload/progress,
auth/session adapter, test/AT, telemetry/CSP ve build/adapter. Her package için version/support owner, license, SBOM,
security watch, SSR/hydration/render parity, keyboard semantics, bundle/large-data behavior, API escape hatch,
fallback/replacement ve clean-room exit yazılmalı. “Built-in” veya package count tek başına puan değildir.

**Öneriye etkisi.** Tüm adaylar `MAJOR / HELD`; kritik capability yalnız unsafe/unmaintained package ile kapanıyorsa
`REJECT-IF-UNMITIGATED`.

### M-02 — No-code simulation kapsamı ve rubriği dar

Manager Proposal §11'in üç görevi gerekli ama yeterli değildir: `WEB-TASK-001` Evidence Review, `WEB-TASK-002` Stale
Session/Lost Outcome ve `WEB-TASK-003` Upgrade/Rollback/Exit. Dense queue/keyboard/AT, component ecosystem/design drift
ve parallel AI collision ayrı ölçülmediği için React/Angular sonucu framework karşılaştırması sayılmaz.

**Düzeltme:** Aşağıdaki paket dört aileye ve seçilen render/hosting modlarına aynı input/output formatıyla uygulanmalı:

| Task | No-code saldırı | Zorunlu çıktı |
|---|---|---|
| `WEB-TASK-001` Evidence Review Workspace | WS-03/04/05/06/08/10; source→evidence→claim→diff→decision→lineage traversal | Context pack, object/API contract, component ownership, focus/AT oracle, negative cases, handoff graph, reviewer evidence. |
| `WEB-TASK-002` Dense Queue + Keyboard | WS-01/02/05/06/09/11; deterministic pagination/filter/sort, saved view, column density, bulk selection, scope retention, long Turkish labels | Wire/state map, table semantics, selection/operation contract, virtualization/text fallback, zoom/narrow behavior, performance and a11y acceptance. |
| `WEB-TASK-003` Stale Session + Lost Outcome | Role/epoch changes at commit; publish/recall response loss; old tab/back/SW; same-ID status lookup | State machine, API envelopes, `DENY/HELD/OUTCOME_UNKNOWN`, audit reference, focus return, safe retry and owner next action. |
| `WEB-TASK-004` Component Ecosystem + Design Consistency | Same capability BOM, token/state mapping, grid/editor/graph/upload/a11y package alternatives | Package/lock/SBOM assumptions, license/security/maintenance, semantic wrapper boundary, fallback/exit, visual/state consistency oracle. |
| `WEB-TASK-005` Upgrade + Rollback + Clean Exit | Patch/major migration; old client/API N/N-1; cache/SW; schema/message/config/release mismatch; clean host rebuild | Lockfile/SBOM/provenance, codemod/manual review, compatibility graph, forward recovery, rollback fence, plane manifest and `EXPORT_PARTIAL` conditions. |
| `WEB-TASK-006` AI Context + Collision | Two bounded AI tasks touch adjacent workspace/design/config surfaces; one task stops half-complete | Machine-readable task packs, graph links, allowed/forbidden scope, locks, reviewer/validator, evidence digest, `PARTIAL/RECONCILING`, no-owner handoff. |

No-code simülasyon; kod, prototype, executable spike veya provider hesabı değildir. Yalnız task pack, state/flow/contract
haritası, dependency/ownership graph'i, acceptance/negative cases, evidence planı ve review çıktısı üretilir. Aynı model,
aynı reviewer rubric'i, aynı fixture, aynı output şablonu ve adaylar için aynı doküman erişim politikası kullanılmalıdır.

**Minimum karşılaştırma ölçüleri:** WS/handoff coverage; context-pack sufficiency; hidden dependency ve unknown sayısı;
conceptual surfaces ve generated/config boundary sayısı; package closure; keyboard/focus/AT coverage; design drift;
migration/exit missing plane; owner technical intervention (hedef sıfır); reviewer rework ve unresolved hard gate. `PASS`
yalnız no-code simülasyonuyla ilan edilmez; bu simülasyon Phase-5 gerçek evidence hazırlığıdır.

### M-03 — Design consistency contract'ı owner/version/state semantics taşımıyor

Proposal §10 canonical design system sözü veriyor, fakat bunun hangi belge/owner/version ile değiştirileceğini, consumer
mobile görsel otoritesinden hangi noktada ayrılacağını ve Internal Operations dense/keyboard ihtiyaçlarının nasıl temsil
edileceğini tanımlamıyor. Phase-3 consumer visual references, internal web route/component/token kararı değildir; platform-
independent workspace architecture da production visual design'ı açıkça erteliyor.

**Saldırı.** Bir AI mobil görsel DNA'sını internal review grid'ine zorlar; diğeri framework component library defaults'una
kaçar. `HELD`, `AUDIT_HELD`, `OUTCOME_UNKNOWN`, `PARTIAL`, `OBJECT_QUARANTINE` farklı renk/icon/copy ile anlatılır. Aynı
object bir queue'da “reviewed”, detail'de “approved”, release'te “published” gibi görünür. Visual regression yalnız pixel
farkını ölçüp yanlış state semantics'ini kaçırabilir.

**Düzeltme.** Framework-neutral internal web design contract'ı kurulmalı: semantic state dictionary, typography/spacing/
density/contrast/focus tokens, table/diff/graph/alert/dialog patterns, Turkish copy rules, keyboard order, responsive
degradation, provenance/history distinction ve component ownership. Contract versioned olmalı; task graph her surface'i
bu contract'a bağlamalı; visual + semantic + AT review birlikte yapılmalı. Consumer visual DNA ile internal web density
arasında controlled relationship kurulmalı, sessizce yeni authority yaratılmamalı.

**Öneriye etkisi.** `MAJOR / HELD`; tekrar eden design/state drift gerçek implementation'da hard-fail seviyesine çıkar.

### M-04 — Upgrade/migration iddiası yalnız LTS/codemod ile kapanmıyor

**Kanıt.** Manager Proposal React/Next Active/Maintenance LTS ve Angular Active/LTS takvimini olumlu sinyal yapıyor.
Primary research React core için bağımsız LTS matrisi olmadığını, Next App Router'ın React canary/RSC closure'ı getirdiğini;
Angular'ın Node/TypeScript/RxJS/CLI/CDK compatibility matrix'inin sıkı olduğunu; Vue/Nuxt ve Svelte/SvelteKit'te de
major/module/adapter closure'larının ayrıca kanıtlanacağını yazıyor.

**Saldırı.** `ng update` veya Next codemod çalışır, fakat table/editor/graph semantics, CSP/CSRF, auth/session epoch,
hydration, browser/AT, large-data, upload, cache/SW, API schema/message and cost behavior bozulur. Managed build image
framework'ü sessizce yükseltir; old client yeni API veya new client eski schema ile pozitif işlemi yanlış yapar. Code/image
rollback database/data, audit/floor, queue message, object, negative state veya browser cache'i geri almaz.

**Düzeltme.** Her aday için exact lockfile ve transitive SBOM/provenance; framework/runtime/compiler/bundler/table/editor/
auth/i18n/test/observability/adapter version matrix; supported browser/AT and patch SLA; pre-release/deprecated package
block policy; clean clone install/build; codemod + human diff; API N/N-1 and schema/message/config/release compatibility;
stale tab/SW/cache; all WEB-TASK outputs; rollback/forward-recovery and clean-room rebuild runbook zorunlu. Major auto-
promote yasak; mismatch `DEPLOYMENT_HELD`.

**Öneriye etkisi.** Dört aile için `MAJOR / HELD`; codemod veya LTS tek başına PASS değildir.

### M-05 — Portability/hosting ve clean-room exit sınırı eksik

**Kanıt.** Proposal H1/H2/H3'ü artı/eksi olarak listeliyor; fakat “portable managed container” ifadesi managed ve
portable sorumluluğunu karıştırıyor, source untouched/isolated import/plane-by-plane manifest/dual-run/cutover sırasını
bağlamıyor. Failure research; static artifact, container image veya provider clone'un API/auth/object/audit/floor/queue/
identity/cache/SW/observability/DNS/TLS state'ini taşımadığını açıkça ayırıyor.

**Saldırı.** `dist`/`.next`/`.output`/adapter-node image başka host'a kopyalanır; fakat CSP/headers, route fallback,
secret/session rotation, API/schema/config/message compatibility, upload quarantine, operation status, protected audit,
negative floor, object lineage veya SW kill-switch yoktur. Managed host rollback yalnız artifact pointer'ını değiştirir;
provider account/DNS/quota/outage ve API/data plane aynı kalabilir. Static host “taşınabilir” görünür ama cross-origin cookie/
CSRF/CORS/correlation ve no-store riskini artırır.

**Düzeltme.** H1/H2/H3'e ek olarak managed static, portable static, managed SSR/edge, portable Node/container ve split
frontend/API şekilleri ayrı fixture olarak tutulmalı. Clean-room pack en az source+lockfile+SBOM/build recipe/artifact
digest; API/schema/config/message/release generations; identity/session/epoch/policy; current/history/provenance;
operation/tombstone/outbox; object bytes/digest/lineage/classification; audit/floor; queue/DLQ/lease; cache/SW/headers;
DNS/TLS/secret reissue; logs/metrics/support/runbook içermeli. Isolated import/reconciliation ve negative anti-resurrection
testi bağımsız kabul edilmeden source host cutover/decommission edilmemeli; eksik plane `EXPORT_PARTIAL`/`RESTORE_QUARANTINE`.

**Öneriye etkisi.** Tüm aday/hosting kombinasyonları `MAJOR / HELD`; eski cache/restore/host authority diriltirse hard-fail.

### M-06 — BFF/server shell ile Kavriva API boundary'si daha işletimsel yazılmalı

Proposal §8 H2 same-origin shell/BFF'yi session/CSP/CORS için uygun aday olarak sunuyor; §4.2 browser/framework server'ın
authority olmadığını söylüyor. Fakat route handler/Nitro/server action/+page.server/Angular SSR server'ın hangi okuma/yazma/
status yollarında yalnız transport olduğunu; direct client/provider path envanterini ve correlation/operation disclosure
kurallarını açıkça göstermiyor.

**Saldırı.** BFF convenience için canonical status'ı cache'ler, client-supplied tenant/resource/version'ı güvenilir sayar,
provider Data API/RPC/Storage/signed URL'yi bypass eder veya başka tenant'ın operation ID sonucunu döner. Same-origin, CORS
ve hidden route ürün authorization'ı değildir. SSR payload/route cache stale role/epoch/version taşıyabilir.

**Düzeltme.** BFF yalnız allowlisted DTO/command transport adapter olarak tanımlanmalı; current authz tuple, generation,
protected audit, operation idempotency ve state resolver her high-consequence çağrıda Kavriva API'de kalmalı. Browser,
framework server, provider console, generic Data API/RPC/view/function, Storage/signed URL ve preview yolları için
allow/deny/hold/unknown matrix ve negative direct-path tests yazılmalı. Status lookup exact actor/tenant/scope/operation
authorization ve disclosure-safe response taşımalı; private/authenticated HTML/data default cache dışı olmalı.

**Öneriye etkisi.** `MAJOR / HELD`; direct BFF/provider authority gerçeklenirse hard-fail.

### M-07 — Responsive/dense fallback ve operator declaration eksik

Proposal küçük ekranda high-consequence context saklanıyorsa `HELD` veya supported viewport diyor; fakat hangi viewport'ta
hangi action'ın desteklendiği, unsupported write'ın nasıl açıkça bildirileceği, safe read/return ve focus/context retention
tanımlı değil. `IWEB-RESP-001` her declared viewport için practical layout ister; dense action'ı sessizce gizlemeyi reddeder.

**Düzeltme.** Wide desktop, narrow desktop/tablet ve phone/narrow browser için capability declaration matrix yazılmalı.
Her unsupported action; “desktop-class view required” veya eşdeğer plain-language reason, retained scope/version/state,
safe read/status/return ve next action göstermeli. Zoom/large text/reduced motion/high contrast ve Turkish long labels aynı
fixture'da test edilmeli; critical column veya status clip/hide olursa `DEPLOYMENT_HELD`/`HELD`, kullanıcıdan tahmin
istenmemeli.

**Öneriye etkisi.** `MAJOR / HELD`.

## 5. Zorunlu düzeltme ve no-code kanıt sırası

1. **Shortlist dilini düzeltin:** React/Next ve Angular'ı eşit aday, Vue/Nuxt ve Svelte/SvelteKit'i aynı baseline'da adil
   challenger olarak tutun; `winner`, `fallback` ve “AI daha iyi bilir” iddiasını kanıt gelene kadar kullanmayın.
2. **Framework-neutral web contract'ı task-addressable yapın:** WS-01..12 context/handoff, IWEB queue/diff/trace/a11y/
   responsive, API state dictionary, BFF sınırı, operation/status ve negative cases tek graph'ta bağlansın.
3. **Dört aday için aynı no-code task pack'i çalıştırın:** manager'ın üç görevi + dense/a11y + component/design + AI
   collision/clean-exit görevleri; aynı input/output/rubric ve bağımsız reviewer.
4. **Render/hosting route matrix'ini eşitleyin:** static/CSR/SSR/hybrid/edge/container/split şekilleri; aynı auth/cache/
   CSP/CSRF/stale-tab/response-loss/large-data/upload/AT/cost/exit fixture'ı.
5. **Component BOM ve design contract'ı kapatın:** package/version/license/security/maintenance/SSR/AT/exit; framework-
   neutral tokens, state/copy/focus/density, owner/version/change-control ve visual+semantic regression.
6. **Upgrade/portability gates'i bağlayın:** lockfile/SBOM/provenance, codemod/manual diff, API N/N-1, schema/message/SW/
   cache/negative-floor compatibility, clean-room import, source untouched, forward recovery ve owner-readable runbook.
7. **Hard-fail ve hold okumasını normalize edin:** evidence yoksa `HELD`; direct bypass, inaccessible critical path, stale
   positive authority, false success, unsafe exit veya owner technical repair varsa `REJECT-IF-UNMITIGATED`; bir ailedeki
   başarısızlık diğerini otomatik kazanan yapmaz.

## 6. Nihai hüküm

### Framework ve render hükmü

- **React + Next.js:** `HELD / koşullu liderlik kanıtlanmadı / ADR not ready`.
- **Angular:** `HELD / React ile eşit finalist / ADR not ready`.
- **Vue + Nuxt:** `HELD / adil challenger / aynı task ve evidence paketi bekleniyor`.
- **Svelte + SvelteKit:** `HELD / adil challenger / aynı task ve evidence paketi bekleniyor`.
- **Tüm render/hosting modları:** `HELD / route-specific equivalence ve clean-room kanıtı yok`.

### Overall PASS/HELD/REJECT

**Overall: `HELD — REQUIRED CHANGES / NO WINNER / ADR NOT READY`.**

Manager proposal belge olarak şu anda `REJECT` değildir; doğru yönleri koruyarak düzeltilebilir. Ancak bu review ile:

- `PASS` verilen aday veya render biçimi yoktur (`0 PASS`);
- documentary hard-fail gözlemi olmadığı için aday düzeyinde `REJECT` verilmemiştir (`0 REJECT`);
- dört framework ailesi ve hosting/render alternatifleri `HELD`'dir;
- `WEB-TASK-001..006`, WS context/traceability, real browser/AT acceptance, component/upgrade/exit evidence kapanmadan
  Phase-5 ADR, framework/hosting seçimi veya Gate 4 → 5 ilerlemesi yapılmamalıdır;
- gerçek uygulamada yukarıdaki hard-fail'lerden biri güvenli hold/recovery ile kapatılamazsa ilgili bileşim
  `REJECT-IF-UNMITIGATED` olur; diğer framework otomatik winner sayılmaz.

Bu review teknoloji, provider, hesap, satın alma, kod, prototip veya uygulama kararı vermez.
