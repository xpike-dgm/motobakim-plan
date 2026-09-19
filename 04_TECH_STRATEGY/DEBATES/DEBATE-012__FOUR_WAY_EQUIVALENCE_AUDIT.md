# DEBATE-012 — Internal Operations web dört aday eşdeğerlik denetimi

Status: `PHASE-4 NO-CODE / FOUR-WAY EQUIVALENCE AUDIT / NO WINNER / ADR NOT READY`  
Date: `2026-09-19`  
Scope: `WEB-TASK-001..003` için React + Next.js, Angular, Vue + Nuxt ve Svelte + SvelteKit  
Input contract: `DEBATE-012__TASK_SIM_WEB_001.md` değişmeden  
Authority: Kavriva API; browser/framework server/provider console canonical authority değildir

Bu belge, mevcut `WEB-TASK-001`, `WEB-TASK-002` ve `WEB-TASK-003` no-code fixture'larını değiştirmez. Mevcut
React/Next ve Angular task çıktıları yeniden yazılmamış; bu denetimde kaynak belgeye referans olarak alınmıştır.
Aynı input/output/oracle contract'ı Vue + Nuxt ve Svelte + SvelteKit'e uygulanarak dört adayın eşdeğerlik kapısı
oluşturulmuştur.

Kod, pseudocode, executable test, prototype, account, subscription, provider seçimi, package kurulumu, benchmark,
deployment veya ADR yoktur. Framework aşinalığı, AI modelinin popüler framework'ü daha uzun anlatabilmesi, cevap
uzunluğu veya package sayısı capability kanıtı değildir. Belgesel kanıt eksikse sonuç `HELD` kalır.

Evidence etiketleri:

- `[CONFIRMED]` Kaynak belgede açıkça verilen fixture, kural veya mevcut task sonucu.
- `[INFERRED]` Candidate-specific mekanizmadan çıkarılan risk; gerçek production kanıtı değildir.
- `[OPEN]` Bu denetim kesitinde çözülmemiş bilinçli boşluk.
- `[HELD]` Kanıt kapanana kadar açılmayan capability veya karar.
- `[REJECT-IF-UNMITIGATED]` Gerçek evidence'ta güvenli hold/recovery ile kapatılamayan hard-fail.

## 1. Denetim kararı ve değişmez sınır

Bu dört-way audit'in sorusu şudur:

> Aynı Internal Operations fixture'ı, aynı context pack'i, aynı task output şeması, aynı product/security/a11y
> oracle'ları ve aynı owner-handoff standardı altında dört adayda da adreslenebiliyor mu?

Bu soru “hangi framework daha iyi?” veya “hangisi seçilmeli?” değildir. Denetim sonucu adayları sıralamaz.

Kavriva API'nin authority olduğu invariant'lar korunur:

1. Browser, route guard, framework server action, Nitro endpoint, SvelteKit action/hook, Angular interceptor/guard,
   cache, service worker, provider console, generic Data API/RPC/Storage veya HTTP 2xx canonical product authority değildir.
2. Commit-time actor/session/security epoch, tenant/scope, role/grant, competence/independence, resource version/
   generation, operation fingerprint, idempotency ve protected audit tekrar Kavriva API'de doğrulanır.
3. Response loss veya timeout sonucu guessed success/failure değil `OUTCOME_UNKNOWN`; aynı operation ID ile disclosure-
   safe status lookup yapılır. Değişen payload/scope/actor yeni success değil `CONFLICT`/`HELD` yoludur.
4. `ACCEPTED`, `DENIED`, `HELD`, `QUEUED/SUBMITTED`, `OUTCOME_UNKNOWN`, `PARTIAL/RECONCILING`, `AUDIT_HELD`,
   `DEPLOYMENT_HELD`, `OBJECT_QUARANTINE`, `RESTORE_QUARANTINE`, `EXPORT_PARTIAL`, `SERVICE_UNAVAILABLE` ve
   `RECOVERY_REQUIRED` UI'da renk/toast/empty queue/optimistic state olarak kaybolamaz.
5. Untrusted evidence, HTML/SVG/URL/archive/preview/upload ve derived object quarantine, digest, classification,
   lineage, scoped handle ve protected API gate'i olmadan active/public technical use'a ulaşamaz.
6. Teknik olmayan owner SQL, SSH, raw log/devtools, queue surgery, cache purge, secret/DNS/TLS veya provider console
   repair yapmaz. Hata plain-language hold/stop/support/restore/exit handoff'ına dönüşür.

## 2. Kaynak ve simulation integrity

### 2.1 Okunan ve dokunulmayan girdiler

| Girdi | Bu audit'teki kullanım | Mutation durumu |
|---|---|---|
| `DEBATE-012__TASK_SIM_WEB_001.md` | `CP-001..CP-012`, `O-01..O-10`, shared fixture, state/product/security/a11y oracles, existing React/Angular task decomposition ve mevcut disposition için canonical input | Değiştirilmedi |
| `DEBATE-012__REVIEW_A_ARCHITECTURE_ACCESSIBILITY.md` | Dört aday için eşit context, dense workspace, keyboard/AT, render/hosting, component closure ve AI collision gereksinimi | Değiştirilmedi |
| `DEBATE-012__REVIEW_B_SECURITY_OPERABILITY.md` | H1–H5 hosting taxonomy, security/session/cache/quarantine/supply-chain/owner/TCO/clean-room hard gates | Değiştirilmedi |
| `DEBATE-012__INTERNAL_WEB_MANAGER_PROPOSAL.md` | Product workspaces, browser/API boundary, common state vocabulary, initial three-task intent ve owner no-debug sınırı | Değiştirilmedi |
| `DEBATE-012__INTERNAL_WEB_PRIMARY_RESEARCH.md` | React/Next, Vue/Nuxt, Svelte/SvelteKit, Angular resmi kaynak snapshot'ları ve capability riskleri | Değiştirilmedi |

`TASK_SIM_WEB_001` içindeki input, output ve oracle'lar bu belge içinde yeniden tanımlanmamıştır; aşağıdaki bölümlerde
yalnız traceability için kısa referanslarla gösterilir. Vue/Nuxt ve Svelte/SvelteKit additive context, aynı §3.2 kuralı
uyarınca common pack'e eklenmiştir; hiçbir hidden product context eklenmemiştir.

### 2.2 Eşit uygulama kuralı

Dört adayın her biri:

- aynı `CP-001..CP-012` common context pack'ini;
- aynı `WEB-TASK-001..003` objective, stop line, forbidden scope ve `O-01..O-10` çıktı şemasını;
- aynı source/evidence/claim/diff/provenance/review/release/recall fixture'ını;
- aynı stale role/epoch, lost response, duplicate, old tab/cache/service-worker, API N/N-1, deployment/rollback/exit
  event'lerini;
- aynı keyboard/screen-reader/zoom/large text/reduced-motion/narrow viewport/slow network koşullarını;
- aynı owner-readable handoff, collision lock, reviewer/validator, cost ve clean-room beklentisini

taşır. Candidate-specific capability yalnız transport/render/build/upgrade boundary'sini açıklamak için additive'dir;
product oracle, authority veya kabul standardı gevşetilemez.

### 2.3 Mevcut React/Angular sonuçlarının statüsü

React + Next.js ve Angular için üç task sonucu `TASK_SIM_WEB_001.md` içinde zaten `HELD` olarak tutulmaktadır:

| Aday | Existing source disposition | Bu audit'teki işlem |
|---|---|---|
| React + TypeScript / Next LTS | `WEB-TASK-001..003 = HELD`; complexity `High, High, Very high` | Yeniden yazılmadı; parity baseline olarak referanslandı |
| Angular LTS | `WEB-TASK-001..003 = HELD`; complexity `High, High, Very high` | Yeniden yazılmadı; parity baseline olarak referanslandı |

Bu denetim, React veya Angular'ı yeniden puanlamaz ve mevcut source oracle'ını değiştirmez. Vue/Nuxt ve SvelteKit
çıktıları aynı schema ile eklenir; ardından dört-way parity test edilir.

## 3. Dört aday için context pack eşdeğerliği

### 3.1 Common pack: değişmeyen `CP-001..CP-012`

Common pack'in tam tanımı `TASK_SIM_WEB_001.md §3.1` içindedir. Bu audit için anlamı kısaca:

- browser Internal Operations ve no-code/no-account/no-purchase boundary;
- WS-01..WS-12 queue, variant, source/evidence, editor, conflict, review, release, lineage, analytics, audit, recall ve access;
- research → evidence → draft → validation/conflict → human review → approval → release → publication → correction/rollback/recall lifecycle;
- current meaning/history/version/provenance/applicability ayrımı;
- actor/session/epoch/tenant/scope/grant/competence/independence/policy/version/generation/fingerprint/audit tuple;
- same-ID status lookup, changed-fingerprint conflict, timeout/response-loss `OUTCOME_UNKNOWN`, blind retry yasağı;
- protected audit-before-effect, durable long-job, quarantine-first, monotonic negative floor ve epoch revocation;
- browser/render/cache transport invariant, private/no-store authenticated data ve service worker'ın authority olmaması;
- keyboard/focus/table/graph/live status/zoom/large text/reduced motion/screen-reader a11y baseline;
- CSRF/XSRF, untrusted content, CSP/Trusted Types, cookie/session, no browser secret, BOLA/IDOR negative paths;
- AI task graph, read/write/forbidden scope, collision lock, release lock, evidence, reviewer, recovery ve owner handoff;
- normalized normal/incident/upgrade/restore/exit BOM, quota/overage stop, SBOM/artifact/config/cache/session/API/object/audit clean-room exit.

Bu common pack dört adayda tamamen aynıdır; adayların “built-in” primitive'leri bu pack'in herhangi bir maddesini
çıkaramaz.

### 3.2 Additive pack: yalnız candidate mechanism context'i

| Aday | Additive context | Açıkça authority sayılmayan mekanizmalar |
|---|---|---|
| React + Next.js | Existing source'daki React/Next support/render/form/action/server-client/DTO/cache/accessibility/test/upgrade/self-host snapshot'ı | RSC, Server Action, Route Handler, cache/prefetch, transition, auth helper, host dashboard |
| Angular | Existing source'daki Angular LTS/compatibility, CSR/SSR/static, reactive forms, HttpClient/XSRF, Aria/CDK, CLI/Vitest/E2E/build/update snapshot'ı | Guard, interceptor, service/signal/observable, SSR/hydration/TransferState, sanitizer/XSRF helper, CLI/host status |
| Vue + Nuxt | Vue 3.5 stable snapshot; Nuxt 4.5.x universal/CSR/SSG/hybrid routeRules; Nitro server/api/middleware; `useFetch`/`useAsyncData`/`$fetch`; `useCookie`; Vue/Nuxt testing/tooling/upgrade/security evidence | `v-model`, route middleware, Pinia/store, Nitro endpoint, server middleware, SSR payload, routeRules cache, optional security module |
| Svelte + SvelteKit | Svelte 5 stable snapshot; SvelteKit 2 baseline; page/layout `ssr`/`csr`/`prerender`; `load`, `+page.server` actions, `hooks.server`, cookies/auth, adapter-node/static/cloud/edge, compiler a11y warning/focus/announcement | form action success, `locals`, hook, load result, cookie/JWT, remote form function, adapter/host, compiler warning |

Vue/Nuxt veya Svelte/SvelteKit context'i yalnız resmi birincil araştırmanın belgelenmiş family boundary'sidir. Exact
version pin, table/grid/editor/auth/i18n package, host, region, cost, session protocol veya production support
garantisi bu additive pack'te varsayılmaz; bunlar `OPEN`/`HELD` unknown'lardır.

## 4. WEB-TASK-001 — Evidence Review Workspace

### 4.1 Değişmeyen task ve oracle

`WEB-TASK-001` objective, input, stop line ve `O-01..O-10` output schema `TASK_SIM_WEB_001.md §§5.1–5.3` içindeki
mevcut fixture'dır; bu dosyada değiştirilmemiştir. Shared product oracles:

- exact scope/applicability, current/history ayrımı, provenance traversal, bounded decision, honest state;
- draft/review/approval/release/publication separation, correction/recall/recovery;
- keyboard-only traversal, visible/predictable focus, semantic table/diff, graph linear alternative, non-color state,
  screen-reader/live status, zoom/large text/reduced motion;
- contextual untrusted-content handling, CSP/Trusted Types, CSRF/XSRF, secure session/cookie, no browser secret,
  direct-path/BOLA/IDOR denial;
- server/API actor/scope/version/fingerprint/audit recheck; browser/runtime response canonical acceptance değildir.

### 4.2 Vue + Nuxt no-code simulation output

#### V-A-001 — O-01 Context pack

`CP-001..CP-012` + Vue/Nuxt additive pack + explicit route/render boundary record + `useFetch`/`useAsyncData`/`$fetch`
read/mutation placement inventory + Nitro `server/api`/middleware transport inventory + SSR payload/cookie/header
redaction list + interactive table/diff/graph/form and accessible linear traversal surface list.

Omitted and still `OPEN`: exact Nuxt/Vue/Node/TypeScript/Vite lock, UI/grid/editor/graph/validation/i18n/auth/security
modules, route-by-route static/CSR/SSR/hybrid mode, cache key/no-store policy, CSP/CSRF policy, supported browser/AT
matrix, hosting/adapter, large-data threshold and owner/support contract.

#### V-A-002 — O-02 Objective and boundary

Source/evidence, current/proposed claim/content, diff/history, provenance/impact, dependent guide and decision formu
tek bir bounded review packet içinde görünür kalır. Vue reactive UI ve Nuxt server/data helpers yalnız allowlisted DTO
transportudur. Nitro handler veya route middleware doğrudan canonical state, role, audit, approval veya publication
authority değildir. Stop line: task contract, state/flow/oracle/evidence/handoff; route/component/package/API implementation yok.

#### V-A-003 — O-03 Task/module decomposition

| Task unit | Conceptual responsibility | Completion evidence |
|---|---|---|
| `V-A1 Scope and review-shell contract` | Scope, current/proposed version, capability ve state dictionary'nin bütün pane/route geçişlerinde korunması | Common context/state-to-surface matrix; UI guard authority değil |
| `V-A2 Evidence/source panel` | Official/community/private/withdrawn evidence, applicability, access/date ve untrusted-content görünümü | Provenance relation, classification ve safe render checklist |
| `V-A3 Diff/current-history panel` | Bounded claim/content/guide-step diff ile current meaning ve event/version history'nin ayrılması | Explicit absence, unresolved, withdrawn ve prior-value fixture |
| `V-A4 Provenance/impact traversal` | Source→evidence→claim→release/use ve reverse impact graph; keyboard/linear fallback | Relation type/status/date/actor ve accessible path fixture |
| `V-A5 Decision/operation panel` | Bounded decision, rationale, condition/expiry, operation ID ve API status reference | Allow/deny/hold/unknown + audit/version precondition map |
| `V-A6 Vue/Nuxt render-data boundary review` | Universal/CSR/SSG/hybrid route, Nitro handler, `useFetch` payload, `$fetch` command, cookie/header ve DTO redaction sınırı | SSR payload/cache/no-store/direct-path threat inventory |
| `V-A7 Browser evidence pack` | Keyboard/AT/focus, narrow/zoom/Turkish labels, untrusted content, stale data ve dense-scale evidence planı | No-code walkthrough ve Phase-5 browser/AT fixture list |

**Module count:** 7 bounded conceptual units; count bir productivity score veya framework preference değildir. Existing
React/Angular task'larında da 7 units vardır; names differ only at transport/render boundary.

#### V-A-004 — O-04 Allowed/forbidden scope

Allowed: workspace pane/state/DTO/focus/semantic/API operation reference/evidence artifact ownership; read-only use of
canonical design/requirements/fixture; Vue/Nuxt boundary and collision map.

Forbidden: code/pseudocode, package installation, exact version, Nuxt module selection, direct DB/Data API/Storage,
auth/provider/session policy, publication/hosting mutation, local Nitro canonical write, treating `v-model`, Pinia,
route middleware, SSR payload, routeRules cache or `$fetch` response as authorization/audit/commit.

#### V-A-005 — O-05 Dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| Kavriva API operation/status/audit contract | Read-only reference; API changes separate owner/reviewer task |
| Canonical design/state dictionary | Shared token/state meaning; no local badge/status synonym |
| Vue/Nuxt/Vite/TypeScript/Node lock and generated `.nuxt` output | Release lock; generated output is not source/audit; version change separate |
| Nitro server routes/middleware and browser `useFetch`/`$fetch` | Explicit transport/DTO boundary; no hidden second authority |
| Universal/hybrid routeRules, SWR/ISR/cache and SSR payload | Actor/scope/epoch-bound cache or private/no-store evidence; no shared sensitive cache |
| Table/diff/graph/editor/form/a11y/i18n/security module closure | Package BOM remains `OPEN`; semantics/SSR/hydration/security/exit evidence required |
| Concurrent AI editing app routes, `nuxt.config`, server routes, state modules, design tokens or lockfile | Explicit route/config/release ownership; collision becomes `PARTIAL/RECONCILING`, not guessed merge |

#### V-A-006 — O-06 Accessibility/security/product oracles

Shared §4 oracles apply. Nuxt-specific negative checks:

- route middleware and server middleware may preserve UX/auth context but never replace API actor/scope/epoch recheck;
- `useFetch` SSR payload and routeRules cache cannot carry stale role, private evidence or positive approval to another
  actor/scope; only necessary headers are forwarded;
- `v-model` valid state, `$fetch`/Nitro response or optimistic Pinia state cannot become `ACCEPTED` without API
  operation/audit/version proof;
- Vue/Nuxt accessibility guidance/announcer and `useHeadSafe` are foundations, not dense grid/graph WCAG evidence;
  virtualized controls, focus restoration, table headers and linear graph path require real DOM/AT review;
- `useCookie` attributes, CORS/CSRF, CSP/Trusted Types, untrusted HTML/SVG/URL/preview and source-map/log redaction are
  tested as security boundary; optional security module does not replace Kavriva API;
- direct Nitro endpoint, browser API, preview URL, cached route or status lookup is tenant/scope/actor restricted and
  disclosure-safe.

#### V-A-007 — O-07 Evidence plan

**No-code now:** V-A task graph; Nuxt render/data/cache/DTO risk register; source→evidence→claim→diff→decision→lineage
state contract; equal oracle checklist; app route/config/lock/module collision map; unresolved package/host list.

**Later:** real browser and screen reader; dense table/diff/graph scale; focus/keyboard/zoom/reduced motion/Turkish
labels; untrusted evidence and CSP/Trusted Types; direct API/BOLA/IDOR; stale epoch/cache/routeRules/SW; status/operation
response loss; private/no-store payload; artifact and clean-room exit.

#### V-A-008 — O-08 Forward recovery and owner handoff

Partial stop preserves common context, task manifest, scope, draft, open findings and owner. Unknown/failed request
remains `HELD`, `OUTCOME_UNKNOWN` or `PARTIAL/RECONCILING`; Nuxt payload/cache or UI reset cannot display approval.
Same operation/status resolver is reopened; no new guessed operation or broad status disclosure.

Owner handoff: “Evidence review planı tamamlanmadı/onaylanmadı/yayınlanmadı. Açık maddeler [plain-language list].
Güvenli next action [hold/status lookup/request support/stop].” Owner is not asked to debug Nitro, clear cache, run SQL,
inspect logs or operate a provider console.

#### V-A-009 — O-09 Unknowns

Exact Vue/Nuxt/Node/TypeScript/Vite lock; Nuxt 4 support horizon; route-by-route render choice; Nitro/serverless/edge
adapter; routeRules/SWR/ISR cache; header/cookie forwarding; CSP/CSRF/Trusted Types; auth/session/epoch; table/grid/
editor/graph and a11y modules; browser/AT; large data; service worker; hosting/region/egress/cost; clean-room exit.

#### V-A-010 — O-10 Qualitative complexity

`High`. Product review semantics are bounded and module count equals the other candidates, but Vue/Nuxt universal/hybrid
payload, Nitro server boundary, routeRules cache, module closure and dense control accessibility require independent
review. This is not a comparative score. Disposition: `HELD`.

### 4.3 Svelte + SvelteKit no-code simulation output

#### S-A-001 — O-01 Context pack

`CP-001..CP-012` + Svelte/SvelteKit additive pack + route/layout `ssr`/`csr`/`prerender` decision record + `load`/
`+page.server`/form action/`hooks.server`/cookie/`locals` data boundary inventory + adapter/runtime list + interactive
table/diff/graph/form and accessible linear traversal surface list.

Omitted and still `OPEN`: exact Svelte 5/SvelteKit 2/Node/Vite lock, SvelteKit 3 migration, UI/grid/editor/graph/
validation/i18n/auth/security packages, route-by-route mode, cache/no-store, CSP/CSRF policy, browser/AT matrix,
adapter/host, large-data threshold, background/queue and owner/support contract.

#### S-A-002 — O-02 Objective and boundary

The same bounded evidence-review packet preserves scope, current/proposed meaning, history, provenance, impact and
decision state. SvelteKit `load`, server actions and hooks are server/transport/UI boundaries only. A form action,
`locals`, cookie, adapter or serialized load result cannot authorize, commit, audit, publish or recall. Stop line is the
same: conceptual task contract and evidence design only; implementation/package/API/host changes are forbidden.

#### S-A-003 — O-03 Task/module decomposition

| Task unit | Conceptual responsibility | Completion evidence |
|---|---|---|
| `S-A1 Scope and review-shell contract` | Scope, current/proposed version, capability ve state dictionary'nin route/layout/pane geçişlerinde korunması | Common context/state-to-surface matrix; UI state non-authority |
| `S-A2 Evidence/source panel` | Evidence type/access/date/applicability/withdrawal ve untrusted source görünümü | Provenance/classification/safe render checklist |
| `S-A3 Diff/current-history panel` | Bounded diff ile current meaning ve event/version history ayrımı | Explicit absence, unresolved, withdrawn ve prior-value fixture |
| `S-A4 Provenance/impact traversal` | Bidirectional relation graph ve keyboard/linear alternative | Relation path/status/date/actor ve accessible fallback fixture |
| `S-A5 Decision/operation panel` | Bounded decision/rationale/condition, operation ID ve Kavriva status reference | Allow/deny/hold/unknown + audit/version precondition map |
| `S-A6 SvelteKit render-data boundary review` | `load`, `+page.server`, form action, hook, cookie/locals, adapter ve serialized DTO sınırı | Server-only secret, cache/no-store/direct-path inventory |
| `S-A7 Browser evidence pack` | Keyboard/AT/focus, narrow/zoom/Turkish labels, untrusted content, stale data ve dense-scale evidence planı | No-code walkthrough ve Phase-5 browser/AT fixture list |

**Module count:** 7 bounded conceptual units; count productivity score değildir. Existing React/Angular and Vue/Nuxt
simulation structures are equivalent; only SvelteKit boundary names differ.

#### S-A-004 — O-04 Allowed/forbidden scope

Allowed: workspace surface/state/DTO/focus/semantic/API reference/evidence ownership; read-only common fixture/design;
SvelteKit server/client/adapter boundary and collision map.

Forbidden: code/pseudocode, package installation, exact version or adapter choice, direct DB/Data API/Storage,
auth/provider/session policy, host publication, treating form action success, `load` data, `locals`, cookie/JWT, hook,
store, remote form function or adapter response as authorization/audit/commit.

#### S-A-005 — O-05 Dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| Kavriva API operation/status/audit contract | Read-only reference; API changes separate owner/reviewer task |
| Canonical design/state dictionary | Shared semantic tokens/copy/focus/density; no local status meaning |
| Svelte 5/SvelteKit 2/Vite/Node lock and generated `.svelte-kit` output | Release lock; generated output is not source/audit; exact version separate |
| `load`, `+page.server`, form actions, `hooks.server`, cookies/locals | Explicit transport/session boundary; no hidden authority or secret serialization |
| `ssr/csr/prerender`, page data serialization, cache and service-worker paths | Route-specific private/no-store/epoch evidence; static pages cannot be privileged authority |
| adapter-node/static/cloud/edge and reverse proxy | Adapter parity for headers/cookies/streaming/logs/limits/rollback; no host assumption |
| Table/diff/graph/editor/form/a11y/i18n/security/test module closure | Package BOM remains `OPEN`; compiler warning is not a package or WCAG closure |
| Concurrent AI editing routes, `hooks`, `svelte.config`, adapter, service worker, design tokens or lockfile | Explicit file/config/release ownership; collision becomes `PARTIAL/RECONCILING` |

#### S-A-006 — O-06 Accessibility/security/product oracles

Shared §4 oracles apply. SvelteKit-specific negative checks:

- `+page.server`/action/hooks/locals can gate transport and retain context but cannot replace API actor/scope/epoch/
  generation/audit check;
- load serialization, `data` invalidation, page options, old tab or service worker cannot restore a stale positive role,
  private evidence or accepted operation;
- form action response, `use:enhance`, remote form function or pending UI cannot become `ACCEPTED` without Kavriva
  operation/status/audit evidence; experimental remote form functions remain `HELD`;
- Svelte compiler `a11y_*` warnings, route announcement and focus management are useful foundations, not full WCAG;
  semantic table/grid, virtualized rows, graph linear path, dialog/focus return, zoom and screen-reader behavior need
  real browser/AT evidence;
- cookie security defaults, hooks, CSP headers, Origin/CSRF contract, untrusted HTML/URL/SVG/preview and log/source-map
  redaction are explicit app/API/adapter tests; no framework single security policy is assumed;
- adapter/direct API/preview/status path is tenant/scope/actor restricted and disclosure-safe.

#### S-A-007 — O-07 Evidence plan

**No-code now:** S-A task graph; SvelteKit load/action/hook/cookie/adapter/cache risk register; state/diff/provenance
contract; equal oracle checklist; route/config/lock/service-worker collision map; unresolved package/host list.

**Later:** real browser/AT; dense table/diff/graph scale; keyboard/focus/zoom/reduced motion/Turkish labels; compiler
warning policy; untrusted evidence and CSP/Trusted Types; direct API/BOLA/IDOR; stale epoch/cache/SW; response-loss/status;
private/no-store payload; artifact/adapter and clean-room exit.

#### S-A-008 — O-08 Forward recovery and owner handoff

Partial stop preserves common context, operation/draft/review evidence, task manifest and unresolved owner. Failed/unknown
action remains `HELD`, `OUTCOME_UNKNOWN` or `PARTIAL/RECONCILING`; load invalidation, page navigation or cookie refresh
cannot erase a newer negative floor. Same operation/status resolver is reopened; no blind duplicate.

Owner handoff: “Review planı [held/unknown/reconciling]; canonical approval yok. Açık maddeler [plain-language list].
Next safe action [status lookup/hold/support/stop].” Owner is not asked to repair hooks, stores, adapters, service worker,
raw logs or provider configuration.

#### S-A-009 — O-09 Unknowns

Exact Svelte/SvelteKit/Node/Vite lock; SvelteKit 2 support horizon and 3 pre-release migration; route mode; adapter
parity; load/action/remote-function boundary; session ID versus JWT/revoke; cookie/Origin/CSRF/CSP/Trusted Types;
table/grid/editor/graph/a11y modules; browser/AT; large-data; service worker; hosting/region/egress/cost; clean-room exit.

#### S-A-010 — O-10 Qualitative complexity

`High`. Product review semantics and seven-module shape are bounded, but SvelteKit server-only/data serialization,
form/action semantics, adapter parity, pre-release major boundary and dense control/a11y package closure require
independent review. This is not a comparative score. Disposition: `HELD`.

### 4.4 WEB-TASK-001 parity result

| Dimension | React + Next.js | Angular | Vue + Nuxt | Svelte + SvelteKit | Equivalence result |
|---|---|---|---|---|---|
| Common context | Existing source `CP-001..CP-012` | Existing source `CP-001..CP-012` | Same `CP-001..CP-012` | Same `CP-001..CP-012` | Equal |
| Additive context | Existing React/Next pack | Existing Angular pack | Vue/Nuxt pack above | Svelte/SvelteKit pack above | Additive only; no hidden product authority |
| Conceptual modules | Existing source: 7 | Existing source: 7 | 7 | 7 | Equal structural count |
| Objective/stop line | Existing source | Existing source | Same evidence-review objective; no implementation | Same evidence-review objective; no implementation | Equal |
| Product/a11y/security oracle | Existing §4 + candidate checks | Existing §4 + candidate checks | Same §4 + candidate checks | Same §4 + candidate checks | Equal acceptance bar |
| Hidden dependencies | Existing source risk surface | Existing source risk surface | Nitro/routeRules/payload/module closure | load/action/hooks/adapter/serialization closure | Candidate-specific, not hidden from pack |
| Qualitative complexity | Existing `High` | Existing `High` | `High` | `High` | Equal label; not a score |
| Disposition | Existing `HELD` | Existing `HELD` | `HELD` | `HELD` | No winner |

## 5. WEB-TASK-002 — Stale Session and Lost Outcome

### 5.1 Değişmeyen task ve oracle

`WEB-TASK-002`'nin six-variant event sequence'i ve `O-01..O-10` output contract'ı `TASK_SIM_WEB_001.md §§6.1–6.3`
içindedir ve değiştirilmemiştir:

1. Object/policy/role generation commit'ten önce değişir.
2. API effect öncesi deny/hold döner.
3. API audit ile commit eder, response kaybolur.
4. Outcome unknown olur; browser aynı operation ile resolver'a gider.
5. Changed fingerprint/scope/actor ile tekrar denenir.
6. Security epoch revoke olur; tab/back/second-tab/cache/SW kalır.

Oracle: stale approval action keyboard ile erişilebilir kalamaz; `OUTCOME_UNKNOWN` operation ID ile duyurulur; accepted
canonical generation/audit reference taşır; denied reason/held resolver/conflict comparison görünür; cross-tenant status
disclosure yoktur; logout/revoke open tab/handle'ı API epoch sınırında geçersiz kılar; draft/review context korunur.

### 5.2 Vue + Nuxt no-code simulation output

#### V-B-001 — O-01/O-02 Context, objective and boundary

`CP-001..CP-012` + V additive pack + six event variants + `useCookie`, route middleware/server middleware, `useFetch`/
`$fetch`, Nitro handler, routeRules/SWR/ISR cache, SSR payload, tab coordination and status-resolver surfaces.

Objective: stale role/policy/object/epoch veya lost response karşısında review packet'i ve draft'ı koruyarak Kavriva
API'nin same-ID status resolver'ını kullanmak; Nuxt navigation/route guard/server middleware/Pinia/fetch response'ını
canonical acceptance saymamak. Stop: state transition/evidence matrix and owner handoff; identity provider, TTL, token
storage, API implementation, browser storage or deployment choice yok.

#### V-B-003 — O-03 Task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `V-B1 Session/epoch context contract` | Server-issued session/epoch/policy/object generation'i DTO redaction ile taşımak | Freshness, cookie/header and disclosure matrix |
| `V-B2 Commit command boundary` | Operation ID, fingerprint, expected generation ve API auth/audit binding | Duplicate/conflict request tuple |
| `V-B3 Stale-tab invalidation` | Route middleware, Pinia/store, routeRules/payload ve tab state'nin stale positive action üretmesini durdurmak | Six-variant deny/hold/review fixture |
| `V-B4 Lost-outcome resolver` | Same-ID status ile accepted/denied/held/unknown/reconciling ayrımı | Disclosure-safe status and response-loss matrix |
| `V-B5 Nitro/fetch/cache/SW boundary` | `$fetch`/`useFetch`, SSR payload, routeRules/cache, server route ve SW'nin authority olmadığını kanıtlamak | Cache/no-store/epoch/old-tab release plan |
| `V-B6 Focus and status recovery` | Stale/unknown/denied/accepted/conflict state announcement and safe focus return | Keyboard/AT recovery oracle |
| `V-B7 Failure/owner handoff pack` | Plain-language result, resolver, recovery owner, no raw technical intervention | Owner runbook and reviewer sign-off |

Module count: 7; existing React/Angular task count ve source result değişmez. `High` complexity, çünkü stale state
routeRules/cache, SSR payload, Pinia, Nuxt middleware ve `$fetch` header/cookie forwarding yüzeylerinde gizlenebilir.

#### V-B-004 — O-04 Allowed/forbidden scope

Allowed: six-variant state transitions, operation/status tuple, route/cache boundary, focus/recovery, negative cases,
owner message and task ownership.

Forbidden: code/pseudocode, session TTL/provider, token/cookie storage choice, API schema/runtime, direct DB/object/
provider path, role/policy edit, publication, host rollback, treating Nuxt route guard/middleware/`useFetch`/Pinia/
routeRules/SWR/ISR/Nitro 2xx as effect.

#### V-B-005 — O-05 Dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| API operation ledger/status resolver | Same operation ID is only lost-outcome reconciliation path |
| Session/security epoch and cookie/header contract | Read-only contract; `useCookie` values are not authority |
| Resource/version/release/schema/config/negative floors | Commit-time current-generation check; no route cache override |
| Nuxt SSR payload, `useFetch` transfer, `$fetch`, routeRules/SWR/ISR, Pinia and service worker | Explicit stale-data tests; no shared cache mutation by unrelated task |
| Nitro server route/middleware and API proxy | Transport-only; exact actor/tenant/scope/status disclosure check |
| Global focus/status/session composables and `nuxt.config` | Release/design ownership; collision `PARTIAL/RECONCILING` |
| Concurrent AI changing API client, auth module, route rules, cookie defaults or adapter | Separate task/dependency snapshot; no guessed merge |

#### V-B-006 — O-06 Oracles

- Stale approval cannot stay keyboard-actionable through Nuxt route middleware, server middleware, Pinia, SSR payload,
  routeRules cache, old tab or service worker.
- `OUTCOME_UNKNOWN` announcement retains operation ID, does not create duplicate `$fetch`, and routes to resolver.
- Accepted shows API generation/audit; denied no-effect reason; held resolver; conflict comparison; no cross-tenant
  operation detail.
- `useFetch` cookie/header proxy forwards only allowlisted headers; public/stale cache cannot carry private role/epoch.
- Logout/revoke crosses API epoch; cookie deletion/navigation does not falsely claim already-running operation cancelled.

#### V-B-007 — O-07 Evidence, O-08 Recovery/handoff, O-09 Unknowns

**No-code evidence:** six-variant sequence/evidence table; Nuxt payload/cache/middleware/adapter risk register; operation
oracle; focus/live-status plan; direct-path/status-disclosure negatives; AI collision lock.

**Later evidence:** two tabs + back/forward/refresh; policy/role/epoch race; timeout before/after commit; same-ID retry
and changed-fingerprint conflict; logout-all; old asset/SW/routeRules cache; keyboard/AT status; API audit/version.

**Recovery/handoff:** Keep draft, operation ID, server timestamp and known scope. Resolver decides accepted/denied/held/
unknown; route navigation or SSR refresh cannot erase negative floor. Owner sees “result guessed değil; [state], next
action [lookup/wait/hold/support]”; no Nitro/cache/session debug.

**Unknowns:** Session protocol/step-up; Nuxt middleware trust; cookie flags/forwarding; routeRules/cache key; SSR payload
invalidation; cross-tab channel; service worker; API status disclosure; browser/AT; adapter/host.

#### V-B-008 — O-10 Qualitative complexity

`High`; no numeric ranking. Nuxt-specific hidden stale-success paths are independently reviewable. Disposition `HELD`.

### 5.3 Svelte + SvelteKit no-code simulation output

#### S-B-001 — O-01/O-02 Context, objective and boundary

`CP-001..CP-012` + S additive pack + six event variants + `load`, `+page.server`, form action, `use:enhance`,
`hooks.server`, `locals`, cookie/session, adapter, page `ssr/csr/prerender`, service-worker and status-resolver surface
inventory.

Objective: security epoch/role/object race and response loss produce an honest stale/unknown/denied/held/resolving
state; form action, `load`, hook, cookie, `locals`, adapter and browser cache remain transport/UI layers. Stop: state
transition/evidence matrix and owner handoff; identity/session TTL, API implementation, browser storage and deployment
choice yok.

#### S-B-003 — O-03 Task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `S-B1 Session/epoch context contract` | Server-issued session/epoch/policy/object generation'i server-only/DTO-safe sınırda taşımak | Freshness/redaction/cookie matrix |
| `S-B2 Commit command action boundary` | Form action/API request'i operation ID, fingerprint, generation ve audit tuple'ına bağlamak | Duplicate/conflict matrix |
| `S-B3 Stale-tab invalidation` | `load` invalidation, page options, locals, old tab/cache/SW'nin positive action restore etmesini engellemek | Six-variant deny/hold/review fixture |
| `S-B4 Lost-outcome resolver` | Same-ID status ile accepted/denied/held/unknown/reconciling ayrımını yapmak | Response-loss and disclosure-safe lookup |
| `S-B5 Server-hook/action/cache boundary` | `hooks.server`, `+page.server`, form action, serialized data, adapter ve SW'nin non-authority olduğunu test etmek | Cache/epoch/release plan |
| `S-B6 Focus and status recovery` | Stale/unknown/denied/accepted announcement and focus return | Keyboard/AT recovery oracle |
| `S-B7 Failure/owner handoff pack` | Plain-language result, next action, support/recovery context and reviewer sign-off | Owner runbook |

Module count: 7; same structural output. `High` complexity; session/local boundary, action/enhance, server hooks,
serialization, adapter and pre-release closure create independent negative paths.

#### S-B-004 — O-04 Allowed/forbidden scope

Allowed: six-variant state transitions, operation/status contract, server/client/adapter/cache boundary, focus/recovery,
negative cases, ownership and owner message.

Forbidden: code/pseudocode, auth provider/TTL/token storage, API schema, direct DB/object/provider path, role/policy
change, host rollback, treating form action/`use:enhance` result, `load` invalidation, `locals`, hook, cookie, store,
remote form function, adapter or HTTP response as canonical acceptance.

#### S-B-005 — O-05 Dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| API operation ledger/status resolver | Same operation ID only; cross-tenant disclosure deny |
| Session/security epoch/cookie/locals | Server-issued context; browser claims non-authority |
| Resource/version/release/schema/config/negative floors | Commit-time API generation check; load data cannot override |
| `load` invalidation, `+page.server`, actions, hooks, adapter, page options, SW | Explicit stale/old-tab tests; no unrelated task mutation |
| Global focus/status/session utilities and design state | Release/design lock; collision `PARTIAL/RECONCILING` |
| Concurrent AI changing `hooks.server`, `svelte.config`, adapter, auth/session, service worker or lockfile | Separate task snapshot and reviewer; no generated merge guess |

#### S-B-006 — O-06 Oracles

- Stale approval is not actionable through action enhancement, route/page navigation, locals, store, hook, old cache or SW.
- `OUTCOME_UNKNOWN` is announced with operation ID and resolver; pending/enhanced action cannot produce duplicate mutation.
- Accepted contains canonical API version/generation/audit; denied/held/conflict contain reason/resolver; status lookup
  scope is actor/tenant restricted.
- Server-only load/action data cannot serialize secret, role grant, private evidence or stale authority to the browser.
- Cookie/session revoke and epoch invalidate open tabs at API boundary; browser navigation does not claim cancellation.

#### S-B-007 — O-07 Evidence, O-08 Recovery/handoff, O-09 Unknowns

**No-code evidence:** six-variant sequence/evidence table; SvelteKit load/action/hook/cookie/adapter/cache risk register;
operation oracle; focus/live-status plan; direct-path/status negatives; collision lock.

**Later evidence:** two tabs/back/forward/refresh; epoch race; abort/timeout after commit; same-ID and changed-payload
retry; logout-all; old asset/SW; keyboard/AT; API audit/version and disclosure.

**Recovery/handoff:** Preserve draft, operation ID, last server timestamp and scope. Resolve via original operation;
navigation/invalidation cannot clear negative floor. Owner sees state and next safe action, never asks to repair action,
hook, adapter, storage or raw log.

**Unknowns:** Session ID/JWT/revoke; action/enhance/remote form policy; cross-tab channel; cookie/Origin/CSRF/CSP;
adapter/cache/SW; API resolver; step-up; browser/AT; host/region/egress.

#### S-B-008 — O-10 Qualitative complexity

`High`; no numeric ranking. Disposition `HELD`.

### 5.4 WEB-TASK-002 parity result

| Dimension | React + Next.js | Angular | Vue + Nuxt | Svelte + SvelteKit | Equivalence result |
|---|---|---|---|---|---|
| Event variants | Existing source six variants | Existing source six variants | Same six | Same six | Equal |
| Conceptual modules | Existing source: 7 | Existing source: 7 | 7 | 7 | Equal structural count |
| Status/epoch/oracle | Existing source shared §4 + candidate checks | Existing source shared §4 + candidate checks | Same; Nuxt cache/middleware additions | Same; SvelteKit action/hook additions | Equal acceptance bar |
| Hidden dependency surface | Existing source | Existing source | RouteRules/payload/fetch/cookie/Nitro | Load/action/hook/locals/adapter/cookie | Candidate-specific, explicit |
| Qualitative complexity | Existing `High` | Existing `High` | `High` | `High` | Equal label; not a score |
| Disposition | Existing `HELD` | Existing `HELD` | `HELD` | `HELD` | No winner |

## 6. WEB-TASK-003 — Upgrade, Rollback and Clean Exit

### 6.1 Değişmeyen task ve oracle

`WEB-TASK-003` release events, output schema and stop line `TASK_SIM_WEB_001.md §§7.1–7.3` içindedir ve burada
değiştirilmemiştir:

1. Security patch ve later major/adapter/runtime migration.
2. Old tab/frontend artifact + API N/N-1 window.
3. Old HTML/chunks/service-worker/cache.
4. Accessibility/security/API compatibility or deploy-health failure.
5. Known-good web artifact promotion while API/data/schema forward-recover edilir.
6. Source untouched clean-room host rebuild/import.

Oracle: exact lock/SBOM/provenance, reviewed migration, API N/N-1/schema/message/config/release compatibility,
artifact/cache/SW/old-tab safety, CSP/CSRF/session/epoch, a11y/browser/large-data/upload evidence, immutable promote,
guarded rollback/forward recovery, owner no-debug and plane-complete clean-room exit. Artifact/host rollback API/data/
audit/negative-floor rollback değildir.

### 6.2 Vue + Nuxt no-code simulation output

#### V-C-001 — O-01/O-02 Context, objective and boundary

`CP-001..CP-012` + V additive pack + current Nuxt/Vue/Node/TypeScript/Vite/Rspack/Nitro lockfile/SBOM placeholders,
routeRules/render inventory, API N/N-1, `.output`/static artifact, cache/SW/old-tab, environment/config/header,
cookie/session/epoch, DNS/TLS, operation/audit/object/floor and clean-room plane manifests.

Objective: Nuxt/Vue patch/major/module/adapter upgrade, old client/API window, failed deployment, guarded rollback and
clean-room exit without resurrecting revoked/recall/deleted/accepted truth. Nuxt upgrade/codemod, `nuxt.config`, Nitro
output, routeRules and module changes are review surfaces; exact version/host/deploy are not selected.

#### V-C-003 — O-03 Task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `V-C1 Dependency/release inventory` | Vue, Nuxt, Nitro, Vue Router, Vite/Rspack/Rsbuild, Node/TS, modules and transitive closure | Lock/SBOM/provenance/advisory manifest |
| `V-C2 Render/API compatibility graph` | Universal/CSR/prerender/hybrid/routeRules, API N/N-1, DTO/session/epoch/schema/config generations | Route/release compatibility matrix |
| `V-C3 Artifact/cache/service-worker contract` | `.output`/static artifact, HTML/data cache, routeRules/SWR/ISR, old tab, SW, kill/drain | Old-cache/old-tab negative fixture and headers |
| `V-C4 Upgrade rehearsal` | Security patch, Nuxt/Vue major, codemod, Vite/Rspack/Nitro/module changes with manual review | Staged diff + a11y/security/browser/API evidence |
| `V-C5 Deploy/rollback/forward recovery` | Exact verified artifact promotion and guarded web rollback without data/floor rollback | `DEPLOYMENT_HELD`, forward recovery and outage case |
| `V-C6 Clean-room exit` | Source/lock/SBOM/build recipe/output/config/headers/cache/session/API/object/audit/floor import on new host | Isolated import, dual run/cutover, anti-resurrection evidence |
| `V-C7 Owner/AI release runbook` | Release/collision lock, credentials, reviewer and owner plain-language promote/hold/stop/support | Task pack and handoff |

Module count: 7; existing source React/Angular task results untouched. Complexity `Very high`; Nuxt 4.5 dependency
changes, Nuxt 3 EOL boundary, Vite 8/Rspack 2, experimental streaming, routeRules cache and module/Nitro adapter
closure cross-plane upgrade/exit work yaratır.

#### V-C-004 — O-04 Allowed/forbidden scope

Allowed: dependency/release graph, migration rehearsal, artifact/cache/header/session contract, forward-recovery,
rollback fence, clean-room evidence, task/owner/reviewer lock.

Forbidden: changing lock/package/version, running codemod, selecting host/region, deploy/DNS/TLS, API/schema/identity
policy, data rollback, source deletion, provider console or owner technical repair; treating `.output`, static artifact,
Nuxt host rollback, routeRules cache or provider dashboard as full-plane recovery.

#### V-C-005 — O-05 Dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| Vue/Nuxt/Nitro/Vite/Rspack/Node/TS and module closure | Exact lock/SBOM/provenance; pre-release/deprecated block; independent reviewer |
| API N/N-1/schema/config/message/content/object/package generation | Compatibility graph; mismatch `DEPLOYMENT_HELD` |
| `.output`, static assets, routeRules/SWR/ISR, HTML/data cache, SW and old tab | Release lock; version/kill/drain and negative-floor tests |
| Auth/session/epoch/cookies/CSP/headers/DNS/TLS | Separate ownership and secret reissue; no bundle/log secret |
| `nuxt.config`, `nitro.config`, server routes/middleware, module config, lockfile and adapter | Single release/config lock; collision `PARTIAL/RECONCILING` |
| API/data/object/audit/floor/queue/worker and clean-room plane | Cross-plane manifest; image/output clone is insufficient |

#### V-C-006 — O-06 Oracles

- Nuxt/Vue security patch or major cannot ship without same dense/a11y/AT, API authority, stale/unknown and untrusted
  preview evidence.
- Nuxt routeRules/SSR payload/cache/SW/old tab cannot resurrect recall/revoke/delete/negative floor or leak scope/epoch.
- `nuxt upgrade`/codemod/module/Vite/Rspack/Nitro migration must retain CSP/CSRF/cookie/session/epoch, route status,
  table semantics, API N/N-1 and operation outcome behavior.
- Provider/Nitro rollback only changes web artifact; API/data/schema/queue/object/audit/floor forward recovery remains
  explicit. Clean-room `.output`/static rebuild reproduces headers/cache/session/error semantics, not just HTML.

#### V-C-007 — O-07 Evidence, O-08 Recovery/handoff, O-09 Unknowns

**No-code evidence:** Vue/Nuxt dependency graph; routeRules/Nitro/SSR/cache/SW risk register; upgrade/rollback state map;
plane manifest; lock/collision map; normalized cost/exit unknowns.

**Later:** clean clone/build; advisory/codemod/manual diff; API N/N-1, browser/AT, large-data/upload; CSP/CSRF/session/
epoch; old tab/cache/SW; immutable artifact promotion; deploy failure/rollback; DNS/TLS/host outage; isolated restore,
dual-run and cutover.

**Recovery/handoff:** Keep known-good source/artifact/config. Failed upgrade `UPGRADE_HELD`/`DEPLOYMENT_HELD`; rollback
is a guarded web release. Missing plane `EXPORT_PARTIAL`/`RESTORE_QUARANTINE`; source remains untouched. Owner sees
“current release [id], new change [held/failed/promoted], API/data/history [safe/unknown/reconciling], next [hold/
support/stop]”; no provider/debug repair.

**Unknowns:** Exact Nuxt/Vue/Nitro/Vite/Rspack/Node/TS/module lock; Nuxt support horizon; pre-release policy; adapter/
host/region; routeRules/cache/SW; API N/N-1; artifact signing; DNS/TLS; observability; clean-room; cost/exit horizon.

#### V-C-008 — O-10 Qualitative complexity

`Very high`; no numeric rank. Nuxt's server/build/module/route-rule closure is not reduced by a codemod or security patch
headline. Disposition `HELD`.

### 6.3 Svelte + SvelteKit no-code simulation output

#### S-C-001 — O-01/O-02 Context, objective and boundary

`CP-001..CP-012` + S additive pack + Svelte 5/SvelteKit 2/Vite/Node lock/SBOM placeholders, `ssr/csr/prerender` route
inventory, API N/N-1, adapter-node/static/cloud/edge, build output, cache/SW/old-tab, config/header/session/epoch,
DNS/TLS, operation/audit/object/floor and clean-room plane manifests.

Objective: Svelte/SvelteKit patch/major/adapter/toolchain migration, old client/API window, failed deploy, guarded web
rollback and clean-room rebuild while preserving Kavriva current/history/negative truth. SvelteKit 3 pre-release,
remote form functions, adapters and Svelte 5 compiler migration remain reviewed dependencies, not chosen assumptions.

#### S-C-003 — O-03 Task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `S-C1 Dependency/release inventory` | Svelte, SvelteKit, Vite, Node/TS, adapter, form/data/a11y/test and transitive packages | Lock/SBOM/provenance/advisory manifest |
| `S-C2 Render/API compatibility graph` | SSR/CSR/prerender/page options, API N/N-1, DTO/session/epoch/schema/config generations | Route/release compatibility matrix |
| `S-C3 Artifact/cache/service-worker contract` | Build output, HTML/data cache, adapter headers, old tab, SW/update/kill/drain | Old-cache/old-tab negative fixture |
| `S-C4 Upgrade rehearsal` | Security patch, Svelte/SvelteKit major, migration, Vite/adapter/remote-function changes | Reviewed diff + browser/AT/security/API evidence |
| `S-C5 Deploy/rollback/forward recovery` | Exact artifact promote and guarded web rollback without API/data/audit/floor rollback | `DEPLOYMENT_HELD` and forward recovery case |
| `S-C6 Clean-room exit` | Source/lock/SBOM/build recipe/adapter/config/header/cache/session/API/object/audit/floor import | Isolated rebuild, dual-run/cutover, anti-resurrection |
| `S-C7 Owner/AI release runbook` | Task/release/collision lock, reviewer, credential boundary and owner promote/hold/stop/support | Handoff and reviewer evidence |

Module count: 7; complexity `Very high`. SvelteKit 3 pre-release, Svelte 5 compiler/SvelteKit migration, adapter
parity, action/load/hooks/remote function closure, and sparse one-contract LTS evidence make upgrade/exit cross-plane.

#### S-C-004 — O-04 Allowed/forbidden scope

Allowed: dependency/release graph, migration rehearsal, artifact/cache/header/session contract, rollback/forward recovery,
clean-room evidence, release lock and owner handoff.

Forbidden: changing versions/package/adapter, running migration, host/provider/DNS/TLS/deploy, API/schema/identity
policy, data rollback, source deletion, provider console or owner technical repair; treating build output, adapter
rollback, static artifact or framework release as full authority/recovery.

#### S-C-005 — O-05 Dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| Svelte/SvelteKit/Vite/Node/TS/adapter and package closure | Exact lock/SBOM/provenance; SvelteKit 3 pre-release block; review |
| API N/N-1/schema/config/message/content/object/package generation | Compatibility graph; mismatch `DEPLOYMENT_HELD` |
| Build output, page options, headers, cache, SW and old tab | Release lock, version/kill/drain and negative-floor test |
| Auth/session/epoch/cookies/CSP/CSRF/Origin/DNS/TLS | Separate policy/secret ownership; no bundle/log secret |
| `svelte.config`, `hooks.server`, `+page.server`, adapter, service worker, lockfile and generated `.svelte-kit` | One release/config lock; collision `PARTIAL/RECONCILING` |
| API/data/object/audit/floor/queue/worker and clean-room planes | Plane manifest and anti-resurrection; artifact clone insufficient |

#### S-C-006 — O-06 Oracles

- Svelte/SvelteKit/adapter/remote-form/toolchain change cannot ship without dense keyboard/AT, API authority, stale/
  unknown, untrusted content and browser evidence.
- Page `ssr/csr/prerender`, `load` serialization, hooks/cookies, adapter cache or SW cannot restore old authority,
  leaked secret, recalled content or newer negative floor.
- Migration must preserve action/form status, CSRF/Origin/cookie/session/epoch, CSP/header, route announcement/focus,
  API N/N-1 and operation outcome semantics; compiler `a11y_*` warning absence is not enough.
- Adapter/host rollback is web-plane only; API/data/schema/message/object/audit/floor/queue are forward recovered and
  clean-room import is independently accepted.

#### S-C-007 — O-07 Evidence, O-08 Recovery/handoff, O-09 Unknowns

**No-code evidence:** Svelte/SvelteKit dependency graph; page-mode/action/load/hooks/adapter/cache/SW risk register;
upgrade/rollback state map; clean-room plane manifest; collision lock; normalized cost/exit unknowns.

**Later:** clean clone/build; migration diff; API N/N-1/browser/AT/large-data/upload; CSP/CSRF/session/epoch; old
tab/cache/SW; artifact promotion; deploy failure/rollback; DNS/TLS outage; isolated restore/dual-run/cutover.

**Recovery/handoff:** Keep known-good artifact/source/environment. Failed change `UPGRADE_HELD`/`DEPLOYMENT_HELD`;
rollback cannot undo API/data/negative floors. Missing export plane `EXPORT_PARTIAL`/`RESTORE_QUARANTINE`. Owner sees
known-good release and plain-language next action; no adapter, service-worker, DNS, secret or host repair.

**Unknowns:** Exact Svelte/SvelteKit/Vite/Node/TS/adapter/package lock; SvelteKit 2 support and v3 release; remote form
function status; route mode/cache/SW; API N/N-1; artifact signing; browser/AT; DNS/TLS; observability; clean-room;
cost/exit horizon.

#### S-C-008 — O-10 Qualitative complexity

`Very high`; no numeric rank. Pre-release/support/adapter and server data/action closure remains open. Disposition `HELD`.

### 6.4 WEB-TASK-003 parity result

| Dimension | React + Next.js | Angular | Vue + Nuxt | Svelte + SvelteKit | Equivalence result |
|---|---|---|---|---|---|
| Release events | Existing source six events | Existing source six events | Same six | Same six | Equal |
| Conceptual modules | Existing source: 7 | Existing source: 7 | 7 | 7 | Equal structural count |
| Upgrade/exit risk | Existing source | Existing source | Nuxt/Vue/Nitro/Vite/module/routeRules | SvelteKit major/adapter/action/load/hooks | Candidate-specific; all same evidence gate |
| A11y/security/API oracles | Existing source | Existing source | Same plus Nuxt payload/cache/module checks | Same plus Svelte action/adapter checks | Equal |
| Owner intervention target | Existing no-owner-debug | Existing no-owner-debug | Zero technical owner intervention | Zero technical owner intervention | Equal target; evidence absent |
| Qualitative complexity | Existing `Very high` | Existing `Very high` | `Very high` | `Very high` | Equal label; not a score |
| Disposition | Existing `HELD` | Existing `HELD` | `HELD` | `HELD` | No winner |

## 7. Four-way equivalence audit

### 7.1 Context pack sufficiency

| Dimension | React + Next.js | Angular | Vue + Nuxt | Svelte + SvelteKit | Finding |
|---|---|---|---|---|---|
| Common context | Existing `CP-001..CP-012` | Existing `CP-001..CP-012` | Same | Same | Equal input |
| Candidate additive context | Existing official React/Next pack | Existing official Angular pack | Vue/Nuxt render/data/security/upgrade pack | Svelte/SvelteKit render/data/security/upgrade pack | Additive only |
| Explicit omissions | Exact packages, versions, host, session, CSP, route modes, browser/AT, cost | Same | Same plus Nuxt module/routeRules/Nitro closure | Same plus adapter/remote-form/SvelteKit major closure | Equal no hidden decision |
| Product authority | Kavriva API | Kavriva API | Kavriva API | Kavriva API | Equal |
| Context sufficiency result | `HELD` | `HELD` | `HELD` | `HELD` | Documentary pack sufficient to plan, not to pass |

No candidate is penalized for an explicit unknown. Hidden dependency becomes a finding only if the task fails to name it,
not merely because the dependency exists. All four candidate outputs name their principal closure surfaces; no winner
or numeric context score is valid.

### 7.2 Task/module count and qualitative complexity

| Task | React + Next | Angular | Vue + Nuxt | Svelte + SvelteKit | Structural result |
|---|---:|---:|---:|---:|---|
| `WEB-TASK-001` Evidence Review | Existing 7 / `High` | Existing 7 / `High` | 7 / `High` | 7 / `High` | Equal bounded decomposition |
| `WEB-TASK-002` Stale/Lost Outcome | Existing 7 / `High` | Existing 7 / `High` | 7 / `High` | 7 / `High` | Equal six-variant coverage |
| `WEB-TASK-003` Upgrade/Rollback/Exit | Existing 7 / `Very high` | Existing 7 / `Very high` | 7 / `Very high` | 7 / `Very high` | Equal cross-plane gate |

The module count is a qualitative planning shape, not an estimate, velocity measure, defect count or framework score.
“High” and “Very high” mean independently reviewable closure surfaces remain; they do not rank candidates.

### 7.3 Hidden dependencies and dependency closure

| Candidate | Hidden dependency risks made explicit by this audit | Current result |
|---|---|---|
| React + Next.js | React/Next split release, RSC/Server Action/client boundary, cache/prefetch/transition, Node/compiler/bundler, third-party table/editor/graph/auth/a11y, adapter/host | `HELD` existing source |
| Angular | Angular/CLI/compiler/Node/TS/RxJS, SSR/hydration/TransferState, interceptor/guard/signal/observable, CDK/Aria/Material/grid/editor/auth, service worker/host | `HELD` existing source |
| Vue + Nuxt | Vue/Nuxt/Nitro/Vue Router/Vite/Rspack, Nuxt modules, routeRules/SWR/ISR, SSR payload/header forwarding, Pinia, cookies, optional security module, adapter/host | `HELD` |
| Svelte + SvelteKit | Svelte compiler/SvelteKit/Vite, SvelteKit 2→3, adapter, `load`/actions/hooks/locals/cookies, remote forms, page serialization, table/editor/a11y, CSP/CSRF integration | `HELD` |

All four require exact lockfile, SBOM, license/security/advisory watch, supported runtime/browser/AT matrix, package
owner and replacement/exit plan. Core framework documentation does not close third-party dense control or auth/session
dependencies.

### 7.4 Dense workspace and accessibility equivalence

| Acceptance surface | Four-way shared requirement | Candidate-specific risk surface | Result |
|---|---|---|---|
| Scope/selection/pagination/filter/sort | Stable scope, filters, version, selection and bounded page across pane/route/back/refresh | Virtualization, hydration/SSR payload, route state, store/service differences | Same oracle; `HELD` |
| Current/history/diff/provenance | Current meaning never silently replaces history; source→claim→release and reverse traversal | Different component/DOM/serialization/graph packages | Same oracle; `HELD` |
| Keyboard/focus/status | Queue→detail→diff→decision→status/recovery keyboard path; visible focus/return; live non-color state | React portals/RSC transitions; Angular CDK/hydration; Nuxt route announcer/`useHeadSafe`; Svelte compiler warnings/focus/actions | Real browser/AT required; `HELD` |
| Dense table/graph | Table headers/row context/selection; graph textual/keyboard alternative; no main-thread freeze | Third-party grid/graph semantics, package maintenance and bundle | No framework primitive is PASS |
| Zoom/long Turkish labels/narrow | Supported viewport declaration; unsupported write explicit `desktop-class view required`/safe read | CSS/component library, SSR/CSR/layout and focus behavior | Same failure gate |
| Untrusted source/evidence/preview | Contextual encoding/sanitization, CSP/Trusted Types, quarantine and no secret | `v-html`/HTML/SVG; `{@html}`; Vue head; Next/Angular escape/bypass paths | Same security oracle |

The existence of React lint, Angular Aria, Vue guidance/Nuxt announcer or Svelte compiler warnings is not real-browser
accessibility evidence. A mouse-only, color-only, focus-lost or assistive-technology-incomprehensible high-consequence
path is `REJECT-IF-UNMITIGATED`; otherwise all remain `HELD`.

### 7.5 Render and hosting mode equivalence

The same H1–H5 taxonomy from `REVIEW_B §0` applies to each candidate independently:

| Mode | Common acceptance question | React + Next | Angular | Vue + Nuxt | Svelte + SvelteKit |
|---|---|---|---|---|---|
| H1 Managed framework-native/edge | Provider build/runtime/cache/edge, session, quota, region, rollback and adapter semantics | Node/Docker/adapter/edge capability | SSR/static/non-Node output capability | Nitro serverless/edge preset, routeRules | Cloud/edge adapter |
| H2 Managed static artifact/CDN | Browser→API origin/CORS/CSRF/cookie/header/upload/status/partial outage | Static export limited server features | CSR/static `dist` | `nuxt generate`/SPA `ssr:false` | adapter-static/prerender |
| H3 Portable static/CDN | DNS/TLS/headers/fallback/purge/monitoring and owner-safe incident | Static export | `outputMode: static`/SPA fallback | Prerender output | adapter-static |
| H4 Portable Node/container | Reverse proxy, patch/CVE, secret, drain, logs, capacity, backup/restore, DNS/TLS | Node/Docker/standalone | Node SSR output | Nitro `.output` Node | adapter-node |
| H5 Split static frontend + managed API | Two failure domains, CORS/CSRF/correlation, API N/N-1 and partial outage | Browser → Kavriva API | Same | Same; Nitro optional proxy | Same |

No candidate/mode receives a pass from the rendering capability alone. Each route requires `ALLOW/DENY/HELD/
OUTCOME_UNKNOWN/PARTIAL/DEPLOYMENT_HELD` matrix for session, cache/no-store, CSP/CSRF, stale tab, response loss,
large data/upload, cost and clean-room exit. BFF/Nitro/server action/+page.server/SSR is replaceable transport only.

### 7.6 Collision and AI-operability equivalence

| Collision plane | React + Next | Angular | Vue + Nuxt | Svelte + SvelteKit | Equal control |
|---|---|---|---|---|---|
| Shared API/state/design contract | Route/component/client task vs canonical API/state/design | Feature/service vs same | Page/composable/Nitro module vs same | Page/load/action/hook vs same | Read-only contract; owner/reviewer lock |
| Dependency/release config | `package`/lock/Next config/generated output | `angular.json`/lock/build output | `nuxt.config`/Nitro/module/lock/`.nuxt`/`.output` | `svelte.config`/hooks/adapter/lock/`.svelte-kit` | One release lock |
| Render/cache/service worker | RSC/cache/prefetch/service worker | hydration/TransferState/service worker | payload/routeRules/SWR/ISR/service worker | load serialization/page options/service worker | Explicit owner + negative stale fixture |
| Design/AT component surface | grid/editor/graph/a11y packages | CDK/Aria/Material/grid/editor | Vue/Nuxt modules/grid/editor | Svelte packages/grid/editor | BOM and semantic wrapper owner |
| Partial AI task | Incomplete route/cache/release | Incomplete service/interceptor/build | Incomplete composable/Nitro/routeRules | Incomplete load/action/hook/adapter | `PARTIAL/RECONCILING`; no guessed merge |

Task addressability target is zero owner technical intervention. Collision evidence must include task pack, dependency
snapshot, allowed/forbidden scope, credential class, release lock, reviewer/validator, evidence digest, unresolved
`HELD` list and plain-language handoff. AI familiarity/popularity is not a collision metric.

### 7.7 Upgrade, rollback and clean-exit equivalence

| Gate | React + Next | Angular | Vue + Nuxt | Svelte + SvelteKit | Four-way result |
|---|---|---|---|---|---|
| Exact lock/SBOM/provenance | Existing source required | Existing source required | Vue/Nuxt/Nitro/Vite/Rspack/module closure required | Svelte/SvelteKit/Vite/adapter/remote package closure required | All `OPEN` |
| Migration | Next codemod + React/Next/RSC/bundler review | `ng update`/builder migration + TS/Node/RxJS review | Nuxt 4 codemod + Vue TS caveat + Vite/Rspack/Nitro/module review | SvelteKit v2 baseline + v3 pre-release/Svelte compiler/adapter review | Codemod ≠ pass |
| Runtime/route parity | App/Pages/RSC/static/Node/adapter | CSR/SSR/SSG/hydration/static/non-Node | universal/CSR/prerender/hybrid/routeRules/Nitro | SSR/CSR/prerender/page options/adapter | Route-specific proof |
| Old asset/API N−1 | Existing source required | Existing source required | `.output`/static/routeRules/SW and API N−1 | build output/page/cache/SW and API N−1 | `DEPLOYMENT_HELD` on mismatch |
| Rollback | Web artifact only; API/data/floor forward recovery | Same | Nitro/static artifact only; route cache/module/config forward recovery | adapter/build artifact only; action/load/config forward recovery | No cross-plane rollback claim |
| Clean room | Source/lock/SBOM/config/header/cache/session/API/object/audit/floor | Same | Include `.output`, Nitro/routeRules/module and cookie/header behavior | Include adapter/hooks/actions/load/page options and cookie/header behavior | Missing plane `EXPORT_PARTIAL`/`RESTORE_QUARANTINE` |

Nuxt 3 EOL, SvelteKit 3 pre-release and React/Next RSC release coupling are time-sensitive watch items; Angular's LTS
matrix does not remove dependent-package or hydration/SSR closure. No family gets a lifecycle advantage without the same
migration, browser/AT, security, API N/N−1, rollback, owner and clean-room evidence.

### 7.8 Owner intervention equivalence

| Candidate | Documentary owner path | Forbidden owner intervention | Current result |
|---|---|---|---|
| React + Next | Existing source plain-language hold/promote/stop/support | SQL/SSH/raw logs/devtools/cache/SW/secret/DNS/host repair | `HELD` |
| Angular | Existing source same | Same | `HELD` |
| Vue + Nuxt | State/resolver/release ID, safe history, next action and support escalation | Nitro/routeRules/Pinia/cookie/raw log/provider/SQL/SSH repair | `HELD` |
| Svelte + SvelteKit | State/resolver/release ID, safe history, next action and support escalation | action/hook/store/adapter/SW/raw log/provider/SQL/SSH repair | `HELD` |

“Managed” host does not prove owner operability; “portable” host does not permit owner technical repair. Account/legal/
billing/domain/DNS/TLS/support/recovery/audit/floor/negative actor roles and incident tabletop remain common evidence.

### 7.9 Unknowns equivalence

| Unknown family | React + Next | Angular | Vue + Nuxt | Svelte + SvelteKit | Finding |
|---|---|---|---|---|---|
| Version/support | React core vs Next LTS/RSC | Angular LTS vs dependent packages | Nuxt support horizon, Vue minor TS, Nuxt 3 EOL | SvelteKit 2 support, v3 pre-release | All require release watch |
| Runtime/toolchain | React/Next/Node/compiler/bundler | Angular/CLI/Node/TS/RxJS | Vue/Nuxt/Nitro/Vite/Rspack/Node/TS/modules | Svelte/SvelteKit/Vite/Node/adapter | Exact lock `OPEN` |
| Render/cache | RSC/SSR/CSR/static/adapter/cache/SW | hydration/TransferState/CSR/SSR/static/SW | universal/CSR/SSG/hybrid/routeRules/Nitro/cache | page options/load/adapter/cache/SW | Route evidence `OPEN` |
| Session/security | cookie/token/epoch/CSP/CSRF/host | same + XSRF interceptor | `useCookie`, header forwarding, optional security module | action cookies/hooks/Origin/CSP | API authority remains fixed |
| Dense/a11y | controls/virtualization/AT | CDK/Aria/controls/AT | modules/grid/announcer/AT | compiler warnings/grid/AT | Real browser evidence missing |
| Upgrade/exit/hosting | adapter/host/clean room | builder/SSR/host/clean room | Nitro/output/module/routeRules/host | adapter/output/hooks/action/host | All `HELD` |

Naming an unknown is not a failure; silently filling it with default framework behavior would be a failure.

## 8. Four-way disposition and hard-fail reading

### 8.1 Result matrix

| Candidate | WEB-TASK-001 | WEB-TASK-002 | WEB-TASK-003 | Context equivalence | Overall |
|---|---|---|---|---|---|
| React + TypeScript / Next LTS | Existing `HELD` | Existing `HELD` | Existing `HELD` | Equal common pack; additive known | `HELD / NO WINNER` |
| Angular LTS | Existing `HELD` | Existing `HELD` | Existing `HELD` | Equal common pack; additive known | `HELD / NO WINNER` |
| Vue + Nuxt | `HELD` | `HELD` | `HELD` | Equal common pack; additive known | `HELD / NO WINNER` |
| Svelte + SvelteKit | `HELD` | `HELD` | `HELD` | Equal common pack; additive known | `HELD / NO WINNER` |

Documentary audit: `0 PASS / 0 REJECT / 4 HELD`. `HELD` means real evidence is absent; it is not a safety or production
approval.

### 8.2 Shared hard fails

Any candidate or render/hosting combination is `REJECT-IF-UNMITIGATED` if real evidence shows:

1. Framework route/server/cache/store/action/interceptor/adapter/provider path produces effect outside Kavriva API authority.
2. Stale role/epoch/object/version, old tab/cache/service worker or old artifact can produce positive authority.
3. Response loss creates blind duplicate, guessed green status or cross-tenant operation disclosure.
4. CSRF/XSRF is delegated only to a client helper, XSS only to CSP, or authorization only to route/server framework.
5. Untrusted object/preview/HTML/SVG/URL/archive reaches active/public use without quarantine/lineage/digest/scoped handle.
6. Critical path is mouse-only, color-only, focus-lost, non-semantic, screen-reader-incomprehensible or lacks safe narrow/zoom behavior.
7. Mutable/unverified dependency/build/artifact or incompatible API/schema/message/cache rollback is promoted.
8. Owner must perform SQL/SSH/raw log/devtools/queue/cache/secret/DNS/provider technical repair.
9. Mandatory safety/privacy/a11y/audit/continuity/exit cost is unbounded or safety is weakened to fit cost.
10. Clean-room exit loses identity/policy/epoch, current/history/provenance, object lineage, operation/audit/negative floor,
    queue/message or anti-resurrection semantics.

Failure of one candidate does not make another candidate winner. The same fixture and gates must be passed independently.

## 9. Evidence still required before ADR or recommendation

Four-way qualitative equivalence is now documented, but no candidate is selected. The next common evidence pack must retain
the same intent for all four:

1. Exact framework/runtime/compiler/bundler/adapter/package lock, SBOM, license/advisory watch, owner and pre-release policy.
2. Traceability from `WEB-TASK-001..003` and future dense/component/AI-collision tasks to WS-01..12, contract, oracle,
   negative case, reviewer and evidence digest.
3. Real browser/OS/AT matrix: keyboard/focus/live status/table/graph, screen reader, zoom/large text, Turkish labels,
   reduced motion, narrow/degraded view, browser storage/cookie and network failure.
4. Route × mode matrix across H1–H5: session/CORS/CSRF/CSP/cache/no-store, stale/unknown, upload/large data, status,
   owner/support, quota/egress, rollback and exit.
5. Direct-path/BOLA/IDOR, session/epoch/revoke/logout-all, CSP/Trusted Types/XSS, status disclosure, response-loss and
   same-ID/conflict evidence.
6. Dense queue/diff/provenance/graph scale, virtualization/selection, main-thread/input behavior and linear AT fallback.
7. Quarantine-first interrupted/duplicate/malicious upload, preview/SSRF/archive/derivative/handle/restore evidence.
8. Patch/major/adapter/toolchain upgrade, migration review, API N/N−1, old tab/cache/SW, artifact promotion and guarded
   rollback/forward recovery.
9. Owner/support/account/legal/billing/domain/DNS/TLS/recovery/negative actor tabletop and identical normal/incident/
   upgrade/restore/exit normalized BOM.
10. Source-untouched clean-room import, plane-by-plane digest/reconciliation, anti-resurrection, dual-run, cutover and
    independent acceptance.

No item may be replaced by popularity, AI familiarity, package count, documentation-only security assertions, one-browser
simulation, green host dashboard or headline price.

## 10. Final hüküm

- Existing React/Next and Angular simulation records remain unchanged and `HELD`.
- Vue + Nuxt and Svelte + SvelteKit receive the same three no-code tasks, seven conceptual modules per task, common
  context pack, `O-01..O-10` output shape, shared product/security/a11y oracle and owner no-debug boundary.
- All four candidates expose different hidden dependency shapes, but each shape is explicit and requires the same closure;
  no family receives a popularity or familiarity credit.
- Dense workspace, accessibility, render/hosting, collision, upgrade/exit, owner intervention and unknowns are equivalent
  acceptance dimensions, not weighted scores.
- Result: `0 PASS / 0 REJECT / 4 HELD / NO WINNER / ADR NOT READY`.
- No framework, exact version, render/hosting mode, account, provider, package, code, deployment or Phase 5 transition is
  approved by this audit.

## 11. Traceability references

- `04_TECH_STRATEGY/DEBATES/DEBATE-012__TASK_SIM_WEB_001.md` — unchanged common input/output/oracle and existing React/Angular simulation.
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__REVIEW_A_ARCHITECTURE_ACCESSIBILITY.md` — four-way equal context, dense/a11y, render/hosting, AI collision and exit corrections.
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__REVIEW_B_SECURITY_OPERABILITY.md` — H1–H5 modes, security/operability/TCO/clean-room hard gates.
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_MANAGER_PROPOSAL.md` — product workspace, authority, state honesty, no-owner-debug and initial task intent.
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__INTERNAL_WEB_PRIMARY_RESEARCH.md` — official-primary candidate capability and release snapshots, §§5–9.

