# DEBATE-012 — WEB TASK SIMULATION 001

Status: `PHASE-4 NO-CODE / EQUAL TASK SIMULATION / NO WINNER / ADR NOT READY`  
Date: 2026-09-19  
Scope: `React + TypeScript / Next.js LTS candidate` versus `Angular LTS candidate`  
Tasks: `WEB-TASK-001`, `WEB-TASK-002`, `WEB-TASK-003`

## 1. Purpose and decision boundary

This is an independent, no-code, equal-input task simulation for the two retained Internal Operations web finalists. It
tests whether an AI-operated delivery system can decompose the same high-consequence browser work into bounded,
reviewable task/module contracts with the same product, security, accessibility, recovery, cost and exit obligations.

The simulation produces planning evidence only. It does not create application code, pseudo-implementation, prototype,
executable test, account, subscription, deployment or ADR. Framework documentation capability is not Kavriva product
correctness. The Kavriva API remains the only product authority for authorization, canonical state, audit, publication,
recall, operation acceptance and recovery floors.

No winner is declared. All candidate/task results remain `HELD` until the same real browser, assistive-technology,
security, failure, upgrade, hosting, cost and clean-room evidence closes the required gates.

## 2. Simulation method and equal-output contract

### 2.1 Candidates

| Candidate | Boundary used for this simulation | Explicitly not assumed |
|---|---|---|
| **A — React + TypeScript / Next.js LTS** | React UI plus a declared Next.js LTS composition; route/render mode, server/client boundary and API call placement are task outputs to be reasoned about. | Exact Next version, App Router/Pages Router choice, RSC/server actions, table/grid/editor/state/auth packages, static/SSR/CSR mode, hosting mode or provider. |
| **B — Angular LTS** | Angular LTS application and its declared CLI/SSR/static composition; route/render mode and API call placement are task outputs to be reasoned about. | Exact Angular major, Node/TypeScript/RxJS matrix, standalone/module style, CDK/Aria/Material/grid/editor/state/auth packages, static/SSR/CSR mode, hosting mode or provider. |

The 2026-09-19 primary-research snapshot records React/Next and Angular release/support signals, but a snapshot is not a
production lock. Each candidate must carry its exact lockfile, runtime/compiler/browser matrix, security-watch policy and
upgrade evidence in a later acceptance pack.

### 2.2 Equal input rule

Both candidates receive exactly the same conceptual fixture, requirements, state dictionary, threat cases, owner model,
browser conditions, dependency assumptions and output schema. Candidate-specific decomposition may expose different
mechanism boundaries, but it may not remove an acceptance oracle or add hidden product authority.

The following are fixed for this simulation:

- browser-based, desktop-class Internal Operations surface;
- provider-neutral Kavriva API authority; no direct canonical DB/object/provider-console authority;
- same actor/tenant/scope/resource/version/generation/security-epoch/operation/audit state;
- same source/evidence/claim/diff/provenance/review/release objects;
- same `ACCEPTED`, `QUEUED/SUBMITTED`, `DENIED`, `HELD`, `OUTCOME_UNKNOWN`, `PARTIAL/RECONCILING`, `AUDIT_HELD`,
  `BILLING_HELD`, `ACCOUNT_HELD`, `DEPLOYMENT_HELD`, `OBJECT_QUARANTINE`, `RESTORE_QUARANTINE`, `EXPORT_PARTIAL`,
  `SERVICE_UNAVAILABLE` and `RECOVERY_REQUIRED` meanings;
- same keyboard, screen-reader, zoom, reduced-motion, narrow viewport, slow network, tab restore and back/forward cases;
- same stale-role/epoch race, response-loss, duplicate, cache/service-worker, API N/N-1, deployment, rollback and exit cases;
- same AI task-pack, collision-lock, independent-review, owner-handoff, cost and clean-room requirements.

### 2.3 Equal output schema

Each candidate/task result must contain the same fields, in the same order:

| Output field | Required content |
|---|---|
| `O-01 Context pack` | Minimum references, state/contract inputs, fixture assumptions and explicit omissions. |
| `O-02 Objective and boundary` | User/product outcome, affected surface and exact task stop line. |
| `O-03 Task/module decomposition` | Bounded task units, ownership and completion dependency; conceptual names only. |
| `O-04 Allowed/forbidden scope` | Read/write boundaries, credentials, files/routes/config and prohibited authority. |
| `O-05 Dependencies and collision surfaces` | Upstream contracts, shared files/state, release locks and concurrent-AI hazards. |
| `O-06 Accessibility/security/product oracles` | Observable pass/fail oracles; framework primitive is never the oracle. |
| `O-07 Evidence plan` | No-code evidence now and real implementation evidence later. |
| `O-08 Forward recovery and owner handoff` | Partial/failure/unknown path, resolver, safe stop and plain-language owner decision. |
| `O-09 Unknowns` | Unresolved facts that must stay `OPEN`/`HELD`; no silent assumption. |
| `O-10 Qualitative complexity` | Low/medium/high/very high with reasons, not a numeric framework score. |

## 3. Minimum context pack

### 3.1 Common context pack supplied to every candidate and task

| Pack ID | Minimum content | Source/provenance |
|---|---|---|
| `CP-001` | Phase-4 no-code boundary; browser Internal Operations direction; no framework/provider/hosting decision. | Manager Proposal §§1–3, 15; Primary Research §§1–2, 13; `07_AI_ARCHITECTURE/README.md` |
| `CP-002` | Internal workspace responsibilities: queue, coverage, variant, source/evidence, editor, conflict, review, release, lineage, analytics, audit, recall and access. | `DEBATE-012__INTERNAL_WEB_REQUIREMENTS_SYNTHESIS.md` §§3–4; original `WS-01..WS-12` |
| `CP-003` | Lifecycle distinction: research → evidence → draft → validate/conflict → human review → approval → release → publication → correction/rollback/recall. | Requirements/workflow package; Manager Proposal §4 |
| `CP-004` | Current meaning versus event history; exact scope/applicability; bounded diff; bidirectional provenance and impact traversal. | Requirements `IDCO-RQ-009..044`; Manager Proposal §§4.1, 4.5 |
| `CP-005` | Kavriva API tuple: actor/principal, issuer/session/assurance, security epoch, action/resource/tenant/scope/classification, grant/delegation/competence/independence, policy/version/generation, negative floors, operation fingerprint and audit readiness. | Manager Proposal §§4.2–4.3; Primary Research §§1, 10 |
| `CP-006` | Operation semantics: same-ID same-payload status lookup; changed fingerprint/scope/actor conflict; timeout/response loss = `OUTCOME_UNKNOWN`; no blind retry. | Manager Proposal §4.3; Failure/TCO §§3.4, 4.1 |
| `CP-007` | Protected audit-before-effect, durable long-job gate, quarantine-first object lane, monotonic negative floor and end-to-end epoch revocation. | `DEBATE-011` §§4.1–4.10; Failure/TCO §§3–5 |
| `CP-008` | Browser/render/cache invariant: authenticated HTML/API/status private or no-store as appropriate; static/SSR/CSR/server helpers are transport layers, not authority; service worker is never privileged mutation authority. | Manager Proposal §§8–9; Primary Research §§1, 5–8; Failure/TCO §§3.1, 4.1 |
| `CP-009` | Accessibility baseline: keyboard complete, visible focus, logical focus return, table semantics, graph linear alternative, non-color state, screen-reader status, zoom/large text/reduced motion. | Manager Proposal §4.4; Failure/TCO F10 / WEB-05 |
| `CP-010` | Security baseline: server-side CSRF/XSRF, contextual untrusted-content handling, CSP/Trusted Types policy, secure session/cookie boundary, no browser secrets, direct-path/BOLA/IDOR denial. | Primary Research §10; Failure/TCO F02–F04 / WEB-02 |
| `CP-011` | AI-native task contract: exact objective/scope, read/write list, dependency snapshot, release lock, operation IDs, credential class, dry run, hard stop, evidence, reviewer, forward recovery and owner handoff. | `07_AI_ARCHITECTURE/README.md`; Failure/TCO §§7.2–7.3 |
| `CP-012` | Cost/exit baseline: normalized normal/incident/upgrade/restore/exit BOM, quota/overage stop, source/lockfile/SBOM/artifact/config/header/cache/session/API/object/audit clean-room exit. | Manager Proposal §12; Primary Research §§11–12; Failure/TCO §§6, 8 |

### 3.2 Candidate-specific context is additive, not hidden

| Candidate | Additive context that may be inspected | Must not be treated as product authority |
|---|---|---|
| React + TypeScript / Next LTS | Official React/Next LTS/support, render boundaries, form/action ergonomics, server/client/DTO boundary, accessibility lint/route announcement, testing/upgrade/self-host evidence. | React state/transition, Next server action/route handler, RSC/cache/prefetch, framework auth helper, build/host dashboard or provider rollback. |
| Angular LTS | Official Angular LTS cadence/compatibility, CSR/SSR/static modes, reactive forms, HttpClient/XSRF client half, Aria/CDK patterns, CLI/Vitest/E2E/build/update evidence. | Angular guard/interceptor/service/signal, SSR/hydration/TransferState, sanitization/XSRF helper, CLI build status, service worker or host dashboard. |

## 4. Shared fixture and state oracles

The same conceptual fixture is used for all three tasks:

- one authorized reviewer operating within one tenant and motorcycle/model/year/variant scope;
- one official evidence item, one community/private evidence item and one withdrawn/inaccessible evidence relation;
- one current claim/content version, one proposed draft diff and one dependent guide step;
- one prior approval/release relation and one affected active/historical-use relation;
- one current policy/access generation and a later revoked role/security epoch;
- one operation identity with payload fingerprint, expected object generation and protected audit readiness;
- one supported wide desktop and one declared narrow/degraded viewport;
- one slow/interrupted network path, one timeout/response-loss path and one stale tab/back-forward path;
- one old asset/service-worker/API N−1 path and one clean-room host/exit path.

### 4.1 Shared product oracles

| Oracle | Pass meaning | Fail/hold meaning |
|---|---|---|
| Scope/applicability | Exact motorcycle/variant/domain remains visible and bounded. | Nearby variant, broad model or missing scope appears applicable by guess. |
| Current/history separation | Current meaning and event/version history are both inspectable. | New value silently rewrites prior value, dispute, withdrawal or use. |
| Provenance | Source/evidence/claim/version/reviewer/release/use and relations are traversable. | Attachment or badge substitutes for provenance. |
| Bounded decision | Reviewer can approve one bounded unit while another remains unresolved. | UI forces false completeness or fabricated winner/confidence. |
| State honesty | `HELD`, unknown, partial, denied, quarantined and unavailable are explicit. | HTTP success, toast, optimistic view or empty queue is shown as canonical success. |
| Publication boundary | Draft/review/approval/release/publication remain distinct. | Edit becomes live or review becomes publication. |
| Correction/recovery | Recall/correction preserves history and safe next action. | Recall deletes history or old state clears a newer negative floor. |

### 4.2 Shared accessibility/security oracles

All candidate-specific sections below must use these same oracles; candidate differences are decomposition/risk surfaces,
not relaxed requirements.

- Keyboard-only traversal reaches queue, scope, evidence, diff, provenance, decision, status, retry/hold and recovery.
- Focus is visible, modal/route focus is predictable, and focus returns to the invoking control after a warning/dialog.
- Tables expose headers/row context/sort/filter/selection/changed values; graph has a linear textual path.
- Pending/held/unknown/conflict/recall/access-denied states are not color/icon/toast/hover-only.
- Screen-reader names, descriptions, errors and live status are available; zoom/large text/reduced motion remain usable.
- Input is contextual-encoded/sanitized, untrusted HTML/rendered evidence remains untrusted, and CSP/Trusted Types policy is
  explicit where applicable.
- Server/API rechecks CSRF/XSRF, session/epoch, actor/scope/resource/version/fingerprint and audit readiness.
- Browser bundle, HTML, logs, source maps and AI task context contain no privileged secret, raw token, private file bytes or
  unrestricted data authority.
- Direct fetch/provider-console/preview/old-tab/cached-route/BOLA/IDOR paths receive the same deny/hold result.

## 5. WEB-TASK-001 — Evidence Review Workspace

### 5.1 Task definition and common output

**Objective:** Produce a bounded plan for a dense evidence-review workspace where an authorized reviewer can inspect
source/evidence, current and proposed claim/content meaning, provenance, dependent guide impact and a decision form without
silently approving or publishing anything.

**Input:** `CP-001..CP-012` plus the shared fixture; no additional hidden product context.  
**Required output for both candidates:** `O-01..O-10`, a traceable task/module map, contract/oracle table, explicit
unknowns and a plain-language owner handoff.  
**Stop line:** Planning ends at reviewable task contracts and evidence design; no route/component code, package selection,
API implementation, schema, auth provider or hosting configuration.

### 5.2 Candidate A — React + TypeScript / Next LTS

#### A-001 context pack

`CP-001..CP-012` plus the React/Next additive pack in §3.2, an explicit route/render boundary decision record, a list of
server/client DTO boundaries and an inventory of any interactive client surface (table, diff, graph, form). RSC/server
actions, framework cache/prefetch and API call placement are `OPEN` task outputs, not pre-approved assumptions.

#### A-002 conceptual task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `R-A1 Scope and review-shell contract` | Preserve scope, current/proposed version, review capability and state dictionary across the workspace. | Context contract and state-to-surface matrix; no authority in route/UI guard. |
| `R-A2 Evidence/source panel` | Show source type/access/date/applicability, evidence status, community/private/official classification and withdrawal history. | Provenance relation checklist and untrusted-content rules. |
| `R-A3 Diff/current-history panel` | Render bounded claim/content/guide-step diff with current meaning beside event/version history. | Diff oracle coverage including explicit absence, unresolved and withdrawn values. |
| `R-A4 Provenance/impact traversal` | Provide a graph or equivalent plus keyboard/linear traversal from source to dependents and back. | Bidirectional path fixture and accessible alternative contract. |
| `R-A5 Decision/operation panel` | Collect bounded decision, rationale, conditions/expiry and operation identity; call only the Kavriva API contract. | Allow/deny/hold/unknown outcome map and protected-audit precondition reference. |
| `R-A6 Client/server boundary review` | Identify interactive client islands versus safe DTO rendering and forbid secret/role/authority leakage through framework data paths. | DTO redaction, cache/no-store and direct-path threat checklist. |
| `R-A7 Browser evidence pack` | Plan keyboard/AT, narrow viewport, untrusted content, stale data and dense-scale evidence. | No-code walkthrough plus Phase-5 browser/AT fixture list. |

#### A-003 allowed and forbidden scope

| Allowed in this task | Forbidden in this task |
|---|---|
| Conceptual ownership of workspace panels, state displays, DTO shapes, focus/semantic requirements, API operation references and test/evidence artifacts. | Code/pseudo-code, package installation, table/graph/editor choice, React/Next version pin, RSC/server-action commitment, direct DB/Data API/Storage, auth/provider/session policy, publication or hosting changes. |
| Read-only use of canonical design/state/requirements and the shared fixture. | Treating client state, Next cache/prefetch, route guard, server action, server component or framework response as authorization/audit/commit. |
| Task-level dependency and collision documentation. | Editing global design tokens, shared API schema, identity policy, release manifest or another candidate’s files. |

#### A-004 dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| Kavriva API operation/status/audit contract | Read-only contract reference; API changes are a separate task with owner/reviewer. |
| Canonical design/state vocabulary | Consume canonical tokens/semantics; no local badge/state meaning. |
| Interactive client/server boundary | Route ownership and DTO redaction record; no hidden server authority. |
| Shared table/diff/graph/form/accessibility package decision | Remains dependency `OPEN`; package task cannot be silently introduced. |
| React/Next lockfile, render mode and framework cache | Release lock; any change is a separate reviewed upgrade task. |
| Other AI tasks editing layout/route/cache/config | Explicit file/route/config ownership; collision causes `PARTIAL/RECONCILING`, not merge guessing. |

#### A-005 accessibility, security and product oracles

The shared §4 oracles apply. React/Next-specific checks add:

- route transition announces the new context without losing focus, and interactive client boundaries do not create a
  keyboard trap or inaccessible portal;
- RSC/server action/route handler output is treated as a transport/DTO layer; no server action response is called accepted
  without API operation/audit/version evidence;
- framework cache, prefetch, suspense/transition or optimistic state cannot display a stale role/epoch as actionable;
- interactive/virtualized table and graph DOM semantics are audited; lint or ARIA pass-through alone is not a pass;
- user-specific response/data is isolated from shared/CDN cache and secrets/roles/private evidence are not serialized to the
  browser.

#### A-006 evidence plan, forward recovery and owner handoff

**No-code evidence now:** task dependency graph; React/Next server-client/DTO and cache-boundary risk register; state/diff/
provenance contract; equal oracle checklist; AI task ownership/collision map; unresolved package/render/hosting list.

**Later evidence:** real supported-browser keyboard/screen-reader/zoom path; dense table/diff/graph scale; untrusted evidence
rendering and CSP/Trusted Types; direct API/BOLA/IDOR; stale tab/epoch; API response-loss; operation status; route/cache/
service-worker; source-map/log redaction; artifact and clean-room exit.

**Forward recovery:** If the task stops after any panel/decomposition step, preserve the context pack, current task manifest,
open findings and owner. A failed/unknown API call remains `HELD`, `OUTCOME_UNKNOWN` or `PARTIAL/RECONCILING`; never show a
review decision as approved. Reopen the same operation/status path; do not reset the reviewer’s scope or erase draft context.

**Owner handoff:** “The evidence review screen is planned but not approved/published. The unresolved items are [plain-language
list]. No owner action is required beyond approve/hold/stop or request support; an AI reviewer must close the listed evidence
and accessibility/security fixtures.” No raw logs, code repair, SQL, SSH or package debugging is handed to the owner.

#### A-007 unknowns and qualitative complexity

| Dimension | Result |
|---|---|
| Unknowns | Exact Next LTS version; App/Pages Router; RSC/server action use; table/graph/editor package; API call placement; cache/no-store policy; CSP/Trusted Types; supported browser/AT matrix; hosting mode; large-data thresholds. |
| Qualitative complexity | **High.** Dense review semantics are bounded, but React/Next client/server/cache/RSC choices and third-party control accessibility create several independently reviewable closure surfaces. This is not a comparative score. |
| Simulation disposition | `HELD` — no real browser/AT/security/scale evidence; no winner implication. |

### 5.3 Candidate B — Angular LTS

#### B-001 context pack

`CP-001..CP-012` plus the Angular additive pack in §3.2, an explicit CSR/SSR/static route decision record, Node/TypeScript/
RxJS/CLI compatibility snapshot and a list of any CDK/Aria/Material/third-party interactive controls. Hydration,
TransferState, service worker and HttpClient interceptor behavior are `OPEN` task outputs, not authority.

#### B-002 conceptual task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `G-A1 Scope and review-shell contract` | Preserve scope, current/proposed version, review capability and state dictionary across the workspace. | Same context contract and state-to-surface matrix as `R-A1`. |
| `G-A2 Evidence/source feature` | Show source/evidence status, applicability, actor/classification and withdrawal history. | Same provenance relation checklist and untrusted-content rules. |
| `G-A3 Diff/current-history feature` | Render bounded claim/content/guide-step diff and event/version history. | Same diff oracle, including explicit absence and unresolved values. |
| `G-A4 Provenance/impact feature` | Provide graph or equivalent and keyboard/linear traversal in the same fixture. | Same bidirectional path and accessible alternative contract. |
| `G-A5 Decision/operation feature` | Collect bounded decision/rationale/conditions and call the Kavriva API operation contract. | Same allow/deny/hold/unknown and audit-precondition evidence. |
| `G-A6 Transport/render boundary review` | Identify service/HttpClient/SSR/hydration/browser boundaries and forbid secret/role leakage. | DTO redaction, cache/no-store and direct-path threat checklist. |
| `G-A7 Browser evidence pack` | Plan the same keyboard/AT, narrow viewport, untrusted content, stale data and dense-scale evidence. | Same no-code walkthrough and Phase-5 fixture list. |

#### B-003 allowed and forbidden scope

| Allowed in this task | Forbidden in this task |
|---|---|
| Conceptual ownership of feature components/services/facades, state displays, DTO shapes, focus/semantic requirements, API operation references and evidence artifacts. | Code/pseudo-code, package installation, exact Angular major/toolchain, CDK/Aria/Material/grid choice, direct DB/Data API/Storage, auth/provider/session policy, publication or hosting changes. |
| Read-only use of canonical design/state/requirements and the shared fixture. | Treating guards, interceptors, services, signals, TransferState, hydration or framework response as authorization/audit/commit. |
| Task-level dependency and collision documentation. | Editing global design tokens, shared API schema, identity policy, release manifest or React/Next task files. |

#### B-004 dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| Kavriva API operation/status/audit contract | Same read-only contract reference; API changes are separate. |
| Canonical design/state vocabulary | Same shared tokens/semantics; no local badge/state meaning. |
| Angular render/transport boundary | Explicit service/SSR/hydration/DTO ownership; no hidden authority. |
| Interactive control package closure | CDK/Aria/Material/third-party grid/graph/form package remains `OPEN` until security/a11y/release evidence. |
| Angular/CLI/Node/TypeScript/RxJS lockfile | Release lock; compatibility change is a separate reviewed upgrade task. |
| Other AI tasks editing routes/interceptors/config/service worker | Explicit file/route/config ownership; collision becomes `PARTIAL/RECONCILING`, not guessed merge. |

#### B-005 accessibility, security and product oracles

The shared §4 oracles apply. Angular-specific checks add:

- Aria/CDK/dialog/overlay focus and screen-reader semantics are inspected in real DOM; use of a primitive is not a WCAG
  pass;
- reactive/template form validity is not server acceptance; HttpClient/XSRF interceptor is only the client half of the API
  security contract;
- SSR/hydration/TransferState/service-worker data cannot preserve a stale role/epoch as an actionable decision;
- change detection/signals/observable retries cannot duplicate a high-consequence operation or turn 2xx into `ACCEPTED`;
- static output and browser API calls preserve user-specific cache isolation and do not serialize secrets, grants or private
  evidence.

#### B-006 evidence plan, forward recovery and owner handoff

**No-code evidence now:** task dependency graph; Angular render/transport/hydration risk register; state/diff/provenance
contract; equal oracle checklist; AI task ownership/collision map; unresolved CDK/Aria/control/toolchain/hosting list.

**Later evidence:** the same real supported-browser keyboard/screen-reader/zoom path; dense table/diff/graph scale; untrusted
evidence rendering and CSP/Trusted Types; direct API/BOLA/IDOR; stale tab/epoch; response-loss; operation status;
SSR/static/hydration/service-worker; source-map/log redaction; artifact and clean-room exit.

**Forward recovery:** If the task stops after any feature/service decomposition, preserve the same context pack, task manifest,
open findings and owner. Failed/unknown API calls remain `HELD`, `OUTCOME_UNKNOWN` or `PARTIAL/RECONCILING`; no form/service
state can display approval. Reopen the same operation/status path and retain reviewer scope/draft context.

**Owner handoff:** Use the same plain-language handoff as Candidate A. The owner approves/holds/stops or requests support;
the owner is never asked to repair Angular/CLI/RxJS/hydration, run SQL/SSH, inspect raw logs or operate provider consoles.

#### B-007 unknowns and qualitative complexity

| Dimension | Result |
|---|---|
| Unknowns | Exact Angular LTS major; Node/TypeScript/RxJS matrix; standalone/module choice; CDK/Aria/Material/grid/graph package; CSR/SSR/static/hydration; service-worker/cache; CSP/Trusted Types; browser/AT matrix; hosting mode; large-data thresholds. |
| Qualitative complexity | **High.** The feature boundaries are explicit, but Angular/CLI/toolchain/observable/hydration/control-package closure and real accessibility evidence remain substantial independent surfaces. This is not a comparative score. |
| Simulation disposition | `HELD` — no real browser/AT/security/scale evidence; no winner implication. |

## 6. WEB-TASK-002 — Stale Session and Lost Outcome

### 6.1 Task definition and common output

**Objective:** Plan a safe browser flow where a reviewer has an open approval/release tab, role or security epoch changes
during commit, and the response is lost after the request may or may not have committed.

**Input:** Same `CP-001..CP-012` and shared fixture, with the following fixed event sequence variants:

1. Tab snapshot is valid; role/policy/object generation changes before commit.
2. API denies/holds before effect and the response reaches the browser.
3. API commits with audit and the response is lost.
4. API outcome is unknown and the browser retries with the same operation.
5. Browser retries with changed payload/scope or from another tenant/actor.
6. Session/security epoch is revoked while tab, back button, second tab, cache or service worker remains.

**Required output for both candidates:** Same `O-01..O-10`; a state transition/evidence matrix for all six variants; no
blind retry, false green, stale approval or cross-tenant status disclosure.  
**Stop line:** No identity-provider choice, session TTL choice, API implementation, code, browser storage decision or
production deployment.

### 6.2 Candidate A — React + TypeScript / Next LTS

#### A-010 context pack

`CP-001..CP-012` plus the Candidate A pack and the six event variants above. Add an inventory of client cache/prefetch,
transition/suspense, route/server-action/handler, session refresh, tab coordination and status-resolver surfaces. Exact
React/Next mechanism is an unknown.

#### A-011 conceptual task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `R-B1 Session/epoch context contract` | Carry server-issued session/epoch/policy/object generation without treating client claims as authority. | Context freshness and redaction matrix. |
| `R-B2 Commit command boundary` | Bind approval/release request to operation ID, fingerprint, expected generation and API authorization/audit result. | Request tuple and duplicate/conflict matrix. |
| `R-B3 Stale-tab invalidation` | Detect/represent stale role/policy/object/epoch and disable/hold positive actions while preserving safe draft context. | Six-variant deny/hold/review fixture. |
| `R-B4 Lost-outcome resolver` | Resolve same operation ID; distinguish accepted, denied, held, unknown and reconciling without blind retry. | Response-loss state matrix and disclosure-safe lookup evidence. |
| `R-B5 Cache/transition/old-tab boundary` | Prevent RSC/client cache/prefetch/service worker/back-forward state from restoring positive authority. | Cache invalidation/epoch/release test plan. |
| `R-B6 Focus and status recovery` | Announce stale/unknown/denied/accepted states and return focus to a safe control. | Keyboard/screen-reader recovery oracle. |
| `R-B7 Failure/owner handoff pack` | Produce incident result, recovery owner and support-ready evidence without raw technical output. | Owner-readable runbook and reviewer sign-off. |

#### A-012 allowed and forbidden scope

| Allowed | Forbidden |
|---|---|
| Plan state transitions, operation/status contracts, cache/route boundary inventory, focus/recovery behavior, negative tests and owner-facing messages. | Code, auth provider/session TTL, token/cookie storage choice, API schema/runtime, direct DB/object paths, role/policy changes, publication effect or hosting rollback. |
| Inspect shared fixture and canonical state dictionary. | Treating `useActionState`, transition completion, route guard, cache revalidation, server action or fetch response as canonical acceptance. |
| Define task ownership and evidence artifacts. | Retrying with a new operation without resolver evidence, clearing stale state silently, or changing shared API contract in this task. |

#### A-013 dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| API status resolver and operation ledger | Contract dependency; same operation ID is the only lost-outcome reconciliation path. |
| Identity/session/security epoch | Read-only security contract; provider and TTL remain separate decision. |
| Object/release/version/negative floors | Commit-time current-generation check; no client cache override. |
| React/Next cache/RSC/transition/service worker | Explicit ownership and stale-data test; no shared cache mutation by unrelated task. |
| Session UI and global error/status components | Release lock and design contract; collision means `PARTIAL/RECONCILING`. |
| Concurrent AI task changing API client/session adapter | Separate task boundary and dependency snapshot; no generated merge guess. |

#### A-014 accessibility, security and product oracles

In addition to §4, the candidate must demonstrate in the plan that:

- a stale approval button cannot remain keyboard-available after revoke/epoch change, and the UI explains why and how to
  refresh/review;
- an `OUTCOME_UNKNOWN` status is announced, retains operation ID, does not steal focus from unrelated work and blocks a
  second logical mutation;
- accepted status displays canonical version/generation/audit reference; denied status shows no-effect reason; held status
  names the resolver; conflict requires explicit comparison;
- route guards, client claims, prefetch, transitions, server action responses and cached DTOs are all tested as non-authority;
- status lookup is tenant/scope/actor restricted and cannot reveal private payload or audit detail to another actor;
- logout/revoke invalidates open tabs/handles at the API/security-epoch boundary, with residual downloaded-copy risk honest.

#### A-015 evidence plan, forward recovery and owner handoff

**No-code evidence now:** six-variant sequence diagram/table; React/Next stale-cache and server/client boundary inventory;
operation/status oracle; focus/announcement plan; direct-path and status-disclosure negative cases; AI collision lock.

**Later evidence:** two real tabs plus back/forward/refresh; role/policy/epoch race; network abort/timeout after commit;
same-ID retry and changed-fingerprint conflict; logout-all; cache/service-worker old asset; keyboard/screen-reader status;
API audit and version evidence.

**Forward recovery:** Preserve the draft, operation ID, last server timestamp and known context. For lost response, status
lookup resolves the original operation. If accepted, show canonical result; if denied, retain no-effect reason; if held or
unknown, prevent positive follow-on and route to resolver. Restore/reload cannot clear a newer negative floor.

**Owner handoff:** “The result is not guessed. Operation `<id>` is [accepted/denied/held/unknown/reconciling]; safe history
remains available. The next action is [wait/status lookup/support/hold].” The owner is not asked to inspect the browser network
panel, rerun a command, delete cache or repair a session.

#### A-016 unknowns and qualitative complexity

| Dimension | Result |
|---|---|
| Unknowns | Session/cookie/token protocol; React/Next route/action boundary; cache/prefetch/service-worker policy; cross-tab channel; API resolver shape; exact step-up/re-auth behavior; browser matrix. |
| Qualitative complexity | **High.** The product state machine is fixed, but client/server/cache/transition boundaries can create hidden stale-success paths that require separate negative evidence. |
| Simulation disposition | `HELD` — no real race, browser, security or AT evidence; no winner implication. |

### 6.3 Candidate B — Angular LTS

#### B-010 context pack

`CP-001..CP-012` plus the Candidate B pack and the six event variants above. Add an inventory of HttpClient/interceptors,
services/facades/signals/observables, route guards, SSR/hydration/TransferState, service worker, session refresh, tab
coordination and status-resolver surfaces. Exact Angular mechanism is an unknown.

#### B-011 conceptual task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `G-B1 Session/epoch service contract` | Carry server-issued session/epoch/policy/object generation without treating client claims as authority. | Same freshness/redaction matrix as `R-B1`. |
| `G-B2 Commit command facade` | Bind approval/release request to operation ID, fingerprint, expected generation and API result. | Same request tuple and duplicate/conflict matrix. |
| `G-B3 Stale-tab invalidation` | Represent stale role/policy/object/epoch and prevent positive actions while preserving safe draft context. | Same six-variant deny/hold/review fixture. |
| `G-B4 Lost-outcome resolver` | Resolve same operation ID and expose accepted/denied/held/unknown/reconciling. | Same response-loss and disclosure-safe lookup evidence. |
| `G-B5 Interceptor/hydration/SW boundary` | Prevent interceptor, singleton state, TransferState, hydration or service worker from restoring authority. | Same cache/epoch/release test plan. |
| `G-B6 Focus and status recovery` | Announce stale/unknown/denied/accepted states and return focus safely. | Same keyboard/screen-reader recovery oracle. |
| `G-B7 Failure/owner handoff pack` | Produce incident result, recovery owner and support-ready evidence without raw technical output. | Same owner-readable runbook and reviewer sign-off. |

#### B-012 allowed and forbidden scope

| Allowed | Forbidden |
|---|---|
| Plan state transitions, operation/status contracts, interceptor/service/guard boundary inventory, focus/recovery behavior, negative tests and owner-facing messages. | Code, auth provider/session TTL, token/cookie storage choice, API schema/runtime, direct DB/object paths, role/policy changes, publication effect or hosting rollback. |
| Inspect shared fixture and canonical state dictionary. | Treating guard/interceptor/service/signal/observable/hydration/TransferState/HttpClient response as canonical acceptance. |
| Define task ownership and evidence artifacts. | Retrying with a new operation without resolver evidence, clearing stale state silently, or changing shared API contract in this task. |

#### B-013 dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| API status resolver and operation ledger | Same contract; same operation ID is the only lost-outcome reconciliation path. |
| Identity/session/security epoch | Read-only security contract; provider and TTL remain separate decision. |
| Object/release/version/negative floors | Commit-time current-generation check; no service/store/cache override. |
| Angular interceptor/service/signal/SSR/hydration/service worker | Explicit ownership and stale-data test; no shared state mutation by unrelated task. |
| Global auth/error/status/focus services | Release lock and design contract; collision means `PARTIAL/RECONCILING`. |
| Concurrent AI task changing API client/session adapter | Separate task boundary and dependency snapshot; no generated merge guess. |

#### B-014 accessibility, security and product oracles

In addition to §4, the candidate must demonstrate in the plan that:

- a stale approval control cannot remain actionable through a route guard, signal, service cache or restored tab after revoke;
- `OUTCOME_UNKNOWN` is announced, retains operation ID, does not create a duplicate observable and remains resolvable;
- accepted/denied/held/conflict state includes canonical version/generation/audit, no-effect reason or resolver;
- HttpClient XSRF interceptor, route guard, SSR/hydration, TransferState, service worker and optimistic observable updates are
  all tested as non-authority;
- status lookup is tenant/scope/actor restricted and cannot reveal private payload or audit detail;
- logout/revoke invalidates open tabs/handles at the API/security-epoch boundary, with residual downloaded-copy risk honest.

#### B-015 evidence plan, forward recovery and owner handoff

**No-code evidence now:** six-variant sequence diagram/table; Angular interceptor/service/hydration boundary inventory;
operation/status oracle; focus/announcement plan; direct-path/status-disclosure negative cases; AI collision lock.

**Later evidence:** same two-tab/back-forward/refresh race; role/policy/epoch change; network abort/timeout after commit;
same-ID retry and changed-fingerprint conflict; logout-all; cache/service-worker old asset; keyboard/screen-reader status;
API audit/version evidence.

**Forward recovery:** Preserve draft, operation ID, timestamp and known context. Resolve lost response through the original
operation status path. Accepted shows canonical result; denied retains no-effect reason; held/unknown blocks positive follow-on;
restore/reload cannot clear a newer negative floor.

**Owner handoff:** Use the same plain-language handoff as Candidate A. The owner is not asked to inspect devtools, clear
browser storage, rerun a command, repair an interceptor/service or operate provider consoles.

#### B-016 unknowns and qualitative complexity

| Dimension | Result |
|---|---|
| Unknowns | Session/cookie/token protocol; Angular interceptor/service/guard boundary; signals/observable retry behavior; SSR/hydration/TransferState/service-worker policy; cross-tab channel; API resolver shape; step-up/re-auth; browser matrix. |
| Qualitative complexity | **High.** The product state machine is fixed, but singleton state, interceptors, hydration and observable retries can create hidden stale-success paths requiring separate negative evidence. |
| Simulation disposition | `HELD` — no real race, browser, security or AT evidence; no winner implication. |

## 7. WEB-TASK-003 — Upgrade, Rollback and Exit

### 7.1 Task definition and common output

**Objective:** Plan a controlled framework/runtime/security upgrade, old-tab/API N−1 compatibility window, cached asset/service-
worker behavior, failed deployment, known-good rollback and clean-room host rebuild without resurrecting revoked/ recalled/
deleted/accepted-operation truth.

**Input:** Same `CP-001..CP-012` and shared fixture, with these fixed release events:

1. Dependency/security patch and a later major/adapter/runtime migration are proposed.
2. An old tab holds a previous frontend artifact while API is N/N−1 during rollout.
3. Browser cache/service worker retains old chunks or old HTML.
4. New artifact fails accessibility/security/API compatibility or deploy health.
5. A known-good web artifact is promoted while API/data/schema are forward-recovered, not blindly rolled back.
6. A clean-room host rebuild/import is attempted with source untouched until independent acceptance.

**Required output for both candidates:** Same `O-01..O-10`; release/compatibility graph; upgrade/rollback/exit evidence plan;
owner-readable runbook and explicit `DEPLOYMENT_HELD`, `RESTORE_QUARANTINE`, `EXPORT_PARTIAL` behavior.  
**Stop line:** No version pin, package upgrade, deploy, host/provider choice, migration, account or purchase.

### 7.2 Candidate A — React + TypeScript / Next LTS

#### A-020 context pack

`CP-001..CP-012` plus Candidate A pack, exact current lockfile/SBOM placeholder, render-mode inventory, API N/N−1 contract,
artifact/asset/cache/service-worker policy, environment/config schema, DNS/TLS/header policy, operation/audit/object/floor
export manifests and independent reviewer/owner runbook roles. Exact versions and hosting are `OPEN`.

#### A-021 conceptual task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `R-C1 Dependency/release inventory` | Bind React, React DOM, Next, compiler/bundler, UI/data/grid/editor/auth/observability and transitive packages into one reviewed closure. | Lockfile/SBOM/provenance and vulnerability-review manifest. |
| `R-C2 Render/API compatibility graph` | Record static/CSR/SSR/server boundary, API N/N−1, DTO, session/epoch, schema/config and client capability compatibility. | Compatibility matrix; no mixed authority. |
| `R-C3 Artifact/cache/service-worker contract` | Define asset digest, HTML/data cache policy, old-tab drain, service-worker update/kill and rollback target. | Old-cache/old-tab negative fixture and header policy. |
| `R-C4 Upgrade rehearsal` | Separate patch/security upgrade from major/adapter/runtime migration; require reviewed diff, contract/a11y/security/browser evidence. | Staged rehearsal record and independent review. |
| `R-C5 Deploy/rollback/forward recovery` | Promote exact verified artifact; hold incompatible deploy; rollback web artifact only through guarded event while preserving API/data floors. | `DEPLOYMENT_HELD`/rollback/forward-recovery scenario. |
| `R-C6 Clean-room exit` | Rebuild/import from source, lockfile, SBOM, artifact recipe, config/header/cache/session/API/object/audit/floor contracts on another host. | Isolated import, negative tests, dual-run/cutover and source-preservation evidence. |
| `R-C7 Owner/AI release runbook` | Bound AI credentials/locks and give owner plain-language promote/hold/stop/support choices. | Task pack, collision map, incident/exit handoff. |

#### A-022 allowed and forbidden scope

| Allowed | Forbidden |
|---|---|
| Plan dependency/release graph, upgrade rehearsal, artifact/cache/header contract, rollback/forward-recovery and clean-room evidence. | Changing lockfile/package, version pin, API/schema/identity policy, hosting provider, DNS/TLS, production deploy, data rollback, source deletion or owner technical repair. |
| Read-only inspection of source/lockfile/SBOM/config contract and prior release evidence. | Auto-major promotion, unreviewed codemod, mutable rebuild, treating Next host rollback as API/data/audit rollback, or clearing negative floors. |
| Define route/config/release ownership and AI locks. | Concurrent mutation of shared release/lockfile/cache/config or another candidate’s environment. |

#### A-023 dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| React/Next/compiler/bundler/Node/browser closure | Exact lockfile and supported matrix; upgrade is staged and independently reviewed. |
| API N/N−1/schema/config/message/content/object/package generations | Compatibility graph and `DEPLOYMENT_HELD`; no frontend-only rollback claim. |
| Hashed assets/HTML/cache/service worker/old tab | Release lock, explicit version/kill-switch/drain and stale-negative tests. |
| Auth/session/epoch/secrets/CSP/headers/DNS/TLS | Separate ownership and secret reissue; no values in bundles/logs. |
| Shared lockfile, build config, env schema, artifact manifest and host runbook | One release lock; collision yields `PARTIAL/RECONCILING`, not guessed merge. |
| API/data/object/audit/floor/queue/worker recovery | Cross-plane restore/exit dependency; image or host clone is insufficient. |

#### A-024 accessibility, security and product oracles

In addition to §4, the candidate must demonstrate in the plan that:

- a patch/major/adapter change cannot ship without the same dense table/diff/provenance keyboard/AT and browser evidence;
- RSC/server-action/client-bundle/cache/asset generation changes do not leak secrets or turn old authority into current;
- CSP/nonce/Trusted Types/CSRF/session/epoch/redirect/origin behavior is tested after upgrade and during rollback;
- an old tab/cache/service worker receives safe hold/reload/compatibility behavior, never approval/publication/recall;
- verified artifact digest, release ID, API/schema/config/message generation and current negative floor are visible to support;
- clean-room rebuild reproduces headers/cache/session/authorization/error-state behavior, not merely visual HTML.

#### A-025 evidence plan, forward recovery and owner handoff

**No-code evidence now:** dependency/compatibility graph; React/Next render/cache/service-worker risk register; upgrade-to-
rollback state map; clean-room plane manifest; AI release-lock/collision map; normalized cost/exit unknowns.

**Later evidence:** clean clone/build from lockfile/SBOM; security advisories and codemod diff; API N/N−1 and browser/AT/
large-data/upload tests; CSP/CSRF/session/epoch; old tab/cache/service worker; artifact promotion; deploy failure/rollback;
DNS/TLS/hosting outage; isolated restore/anti-resurrection; alternate-host dual run and cutover.

**Forward recovery:** Keep the current known-good artifact/source/environment until the new artifact passes all gates. A failed
upgrade becomes `UPGRADE_HELD`/`DEPLOYMENT_HELD`; a failed migration does not delete valid data. A rollback is a new guarded
web release event, not database/schema/negative-floor rollback. Exit gaps remain `EXPORT_PARTIAL` or `RESTORE_QUARANTINE` and
source remains untouched.

**Owner handoff:** “The upgrade is [held/promoted/rolled back/exit incomplete]. Current known-good release is `<id>`; affected
operations/history remain [safe/unknown/reconciling]. Owner decision: [hold/promote/stop/support].” The owner is not asked to
change DNS, clear service workers, run builds, rotate raw secrets or repair a host.

#### A-026 unknowns and qualitative complexity

| Dimension | Result |
|---|---|
| Unknowns | Exact React/Next LTS/Node/compiler/bundler lock; RSC/server action use; adapter/host; API N/N−1 window; service-worker/cache; artifact signing/verification; DNS/TLS; observability; clean-room host; cost/exit horizon. |
| Qualitative complexity | **Very high.** React/Next split release surface, server/client/render/cache choices, framework/bundler coupling and host parity make upgrade and exit a cross-plane task even when the web artifact itself is portable. |
| Simulation disposition | `HELD` — no upgrade/rollback/clean-room evidence; no winner implication. |

### 7.3 Candidate B — Angular LTS

#### B-020 context pack

`CP-001..CP-012` plus Candidate B pack, exact current lockfile/SBOM placeholder, render-mode inventory, API N/N−1 contract,
artifact/asset/cache/service-worker policy, environment/config schema, DNS/TLS/header policy, operation/audit/object/floor
export manifests and independent reviewer/owner runbook roles. Exact Angular LTS/toolchain and hosting are `OPEN`.

#### B-021 conceptual task/module decomposition

| Task unit | Responsibility | Completion evidence |
|---|---|---|
| `G-C1 Dependency/release inventory` | Bind Angular, CLI, compiler, Node, TypeScript, RxJS, CDK/Aria/Material/grid/editor/auth/observability and transitive packages into one reviewed closure. | Lockfile/SBOM/provenance and vulnerability-review manifest. |
| `G-C2 Render/API compatibility graph` | Record CSR/SSR/static/hydration, API N/N−1, DTO, session/epoch, schema/config and client capability compatibility. | Same compatibility matrix; no mixed authority. |
| `G-C3 Artifact/cache/service-worker contract` | Define dist artifact, route fallback, HTML/data cache, installed application version, old-tab drain and rollback target. | Same old-cache/old-tab negative fixture and header policy. |
| `G-C4 Upgrade rehearsal` | Separate patch/security upgrade from major/CLI/builder/runtime migration; require reviewed diff and contract/a11y/security/browser evidence. | Staged `ng update`/migration review record, without auto-approval. |
| `G-C5 Deploy/rollback/forward recovery` | Promote exact verified artifact; hold incompatible deploy; rollback web artifact only through guarded event while preserving API/data floors. | Same `DEPLOYMENT_HELD`/rollback/forward-recovery scenario. |
| `G-C6 Clean-room exit` | Rebuild/import from source, lockfile, SBOM, dist/server recipe, config/header/cache/session/API/object/audit/floor contracts on another host. | Same isolated import, negative tests, dual-run/cutover and source-preservation evidence. |
| `G-C7 Owner/AI release runbook` | Bound AI credentials/locks and give owner plain-language promote/hold/stop/support choices. | Same task pack, collision map and incident/exit handoff. |

#### B-022 allowed and forbidden scope

| Allowed | Forbidden |
|---|---|
| Plan dependency/release graph, upgrade rehearsal, artifact/cache/header contract, rollback/forward-recovery and clean-room evidence. | Changing lockfile/package, version pin, API/schema/identity policy, hosting provider, DNS/TLS, production deploy, data rollback, source deletion or owner technical repair. |
| Read-only inspection of source/lockfile/SBOM/config contract and prior release evidence. | Auto-major promotion, unreviewed `ng update`/schematic, mutable rebuild, treating CLI/host rollback as API/data/audit rollback, or clearing negative floors. |
| Define route/config/release ownership and AI locks. | Concurrent mutation of shared release/lockfile/cache/config or React/Next candidate environment. |

#### B-023 dependencies and collision surfaces

| Dependency/collision | Required control |
|---|---|
| Angular/CLI/compiler/Node/TypeScript/RxJS/browser closure | Exact lockfile and supported matrix; upgrade staged and independently reviewed. |
| API N/N−1/schema/config/message/content/object/package generations | Same compatibility graph and `DEPLOYMENT_HELD`; no frontend-only rollback claim. |
| Dist assets/HTML/route fallback/service worker/old tab | Release lock, explicit version/kill-switch/drain and stale-negative tests. |
| Auth/session/epoch/secrets/CSP/headers/DNS/TLS | Separate ownership and secret reissue; no values in bundles/logs. |
| Shared `angular.json`, environments/routes, build config, artifact manifest and host runbook | One release lock; collision yields `PARTIAL/RECONCILING`, not guessed merge. |
| API/data/object/audit/floor/queue/worker recovery | Same cross-plane restore/exit dependency; image/host clone is insufficient. |

#### B-024 accessibility, security and product oracles

In addition to §4, the candidate must demonstrate in the plan that:

- a patch/major/CLI/builder change cannot ship without the same dense table/diff/provenance keyboard/AT and browser evidence;
- hydration/TransferState/service-worker/HttpClient/interceptor/guard/signal state cannot leak secrets or restore old authority;
- CSP/nonce/Trusted Types/XSRF/session/epoch/redirect/origin behavior is tested after upgrade and during rollback;
- an old tab/cache/service worker receives safe hold/reload/compatibility behavior, never approval/publication/recall;
- verified artifact digest, release ID, API/schema/config/message generation and current negative floor are visible to support;
- clean-room rebuild reproduces headers/cache/session/authorization/error-state behavior, not merely visual HTML.

#### B-025 evidence plan, forward recovery and owner handoff

**No-code evidence now:** dependency/compatibility graph; Angular render/hydration/cache/service-worker risk register;
upgrade-to-rollback state map; clean-room plane manifest; AI release-lock/collision map; normalized cost/exit unknowns.

**Later evidence:** clean clone/build from lockfile/SBOM; Angular update/build migration diff; API N/N−1 and browser/AT/
large-data/upload tests; CSP/CSRF/session/epoch; old tab/cache/service worker; artifact promotion; deploy failure/rollback;
DNS/TLS/hosting outage; isolated restore/anti-resurrection; alternate-host dual run and cutover.

**Forward recovery:** Keep current known-good artifact/source/environment until the new artifact passes all gates. A failed
upgrade becomes `UPGRADE_HELD`/`DEPLOYMENT_HELD`; failed migration does not delete valid data. Rollback is a new guarded web
release event, not database/schema/negative-floor rollback. Exit gaps remain `EXPORT_PARTIAL` or `RESTORE_QUARANTINE` and
source remains untouched.

**Owner handoff:** Use the same plain-language handoff as Candidate A. The owner is not asked to change DNS, clear service
workers, run builds, rotate raw secrets, repair CLI/Node/RxJS/hydration or operate a host console.

#### B-026 unknowns and qualitative complexity

| Dimension | Result |
|---|---|
| Unknowns | Exact Angular LTS/CLI/Node/TypeScript/RxJS/CDK/Aria/Material lock; SSR/static/hydration; service-worker/cache; API N/N−1 window; artifact signing/verification; DNS/TLS; observability; clean-room host; cost/exit horizon. |
| Qualitative complexity | **Very high.** Angular’s integrated CLI/compiler/toolchain has visible conventions, but compatibility closure, hydration/service-worker behavior, control packages and host parity still make upgrade and exit cross-plane work. |
| Simulation disposition | `HELD` — no upgrade/rollback/clean-room evidence; no winner implication. |

## 8. Cross-candidate equivalence audit

| Equivalence dimension | React + TypeScript / Next LTS | Angular LTS | Result |
|---|---|---|---|
| Context pack | `CP-001..CP-012` + candidate additive pack | `CP-001..CP-012` + candidate additive pack | Equal input; candidate version/closure is the only additive difference. |
| Task objectives | Same three product outcomes and stop lines | Same three product outcomes and stop lines | Equal. |
| API/state/security authority | Kavriva API, same operation/audit/epoch/floor contract | Same | Equal; framework never authority. |
| Accessibility/security oracles | Same §4 oracles plus React/Next boundary checks | Same §4 oracles plus Angular boundary checks | Equal acceptance bar. |
| Allowed/forbidden scope | Same read-only/no-code/no-provider/no-authority boundary | Same | Equal. |
| Failure/recovery | Same stale, response-loss, cache/SW, deploy, rollback, restore and exit paths | Same | Equal. |
| Owner/AI model | Same bounded task pack, collision lock, reviewer and no-owner-debug handoff | Same | Equal. |
| Cost/exit | Same normalized BOM and clean-room plane list | Same | Equal. |
| Current evidence | Official mechanism/support signals only; no real task/browser/AT/exit proof | Same | Both `HELD`; no winner. |

### 8.1 Candidate-specific risk surfaces (not scores)

| Candidate | Risk surfaces exposed by the simulations | Required closure before any recommendation |
|---|---|---|
| React + TypeScript / Next LTS | React/Next split release; RSC/server-action/client boundary; cache/prefetch/transition; third-party dense controls; render/host mode parity; lockfile and adapter coupling. | Real browser/AT, stale/unknown, API authority, cache/SW, upgrade, artifact, hosting, cost and clean-room evidence. |
| Angular LTS | Angular/CLI/compiler/Node/TypeScript/RxJS closure; hydration/TransferState; interceptor/guard/signal retry; CDK/Aria/third-party dense controls; service-worker and server/static parity. | Same evidence package with Angular-specific compatibility/hydration/control checks. |

Qualitative complexity results are `High` for WEB-TASK-001/002 and `Very high` for WEB-TASK-003 for both candidates. This
is a planning signal, not a preference or weighted framework score.

## 9. Shared hard fails and reversal triggers

Any candidate/task/hosting composition is `REJECT-IF-UNMITIGATED` if it:

1. treats UI guard, framework server action, interceptor, cache, service worker, optimistic state, provider dashboard,
   HTTP 2xx or build green as canonical authorization, audit, publication, recall or acceptance;
2. bundles privileged DB/object/service credentials, long-lived unrestricted bearer tokens, raw secrets or private evidence;
3. performs blind retry/duplicate mutation or guessed success after timeout/response loss;
4. leaves CSRF solely to a client interceptor, XSS solely to CSP, or authorization solely to a route guard/framework helper;
5. exposes active/public object handles before quarantine, digest, scan/classification/lineage and manifest closure;
6. serves stale authenticated HTML/API/status or old tab/cache/service-worker state without current epoch/generation checks;
7. skips real browser/keyboard/screen-reader/data-heavy/upload/security evidence because the framework claims capability;
8. rolls back only an image/artifact while ignoring API/schema/config/cache/service-worker/negative-floor compatibility;
9. requires auto-major or unreviewed dependency/codemod/package promotion;
10. makes the owner perform SQL, SSH, raw-log/devtools, queue, cache/service-worker, secret, DNS/TLS or incident repair;
11. cannot export/rebuild source, lockfile, SBOM, artifact recipe, config/headers/cache/session/API/object/audit/floor and
    negative behavior in a clean room;
12. silently expands task scope, edits a shared contract without owner/reviewer lock, or leaves a half-complete AI task as a
    green release.

Reversal is evidence-driven. A failure in one candidate does not make the other a winner; the other must pass the same
fixture and normalized evidence. If neither passes, capability remains `HELD` and the standard is not weakened.

## 10. Evidence plan before any ADR or winner

The next evidence pack must be identical in intent and coverage for both candidates:

1. Exact lockfile/runtime/compiler/browser/AT matrix, transitive SBOM, license/security review and patch-watch owner.
2. No-code task traceability from `WEB-TASK-001..003` to modules, contracts, acceptance and negative cases.
3. Real dense table/diff/provenance/graph fixture with keyboard, screen reader, focus, zoom, reduced motion and narrow view.
4. Stale session/role/epoch, cross-tenant/BOLA/IDOR, CSRF/XSS/CSP/Trusted Types, cookie/session and status-disclosure tests.
5. Response-loss/duplicate/optimistic/cache/service-worker/old-tab and API N/N−1 compatibility fixtures.
6. Quarantine-first upload, malicious preview, scoped handle, digest/lineage/classification and orphan-recovery fixtures.
7. Patch/major/adapter/toolchain upgrade rehearsal with reviewed migration diff and independent reviewer.
8. Immutable artifact promotion, deploy incompatibility, rollback/forward recovery, host/DNS/TLS outage and owner runbook.
9. Normal/incident/upgrade/restore/exit normalized cost BOM with caps, overage, stop state, support and owner approval.
10. Clean-room build/import/dual-run/cutover and anti-resurrection tests with source untouched until acceptance.
11. AI task-pack, collision lock, forbidden-credential audit, independent validation and plain-language owner handoff.

No item above can be replaced by framework popularity, component-library claims, documentation-only security assertions,
simulator-only accessibility claims, host dashboard status or headline price.

## 11. Disposition

| Candidate | WEB-TASK-001 | WEB-TASK-002 | WEB-TASK-003 | Overall |
|---|---|---|---|---|
| React + TypeScript / Next LTS | `HELD` | `HELD` | `HELD` | `NO WINNER / ADR NOT READY` |
| Angular LTS | `HELD` | `HELD` | `HELD` | `NO WINNER / ADR NOT READY` |

The simulation confirms that both candidates can be expressed as bounded AI task/module plans under the same product and
security contracts. It does **not** prove that either candidate can satisfy Kavriva’s real dense-workspace accessibility,
stale-session, API outcome, upload quarantine, upgrade/rollback, no-owner-debug, cost or clean-room gates.

No framework, exact version, hosting mode/provider, account, plan, runtime, package, code, prototype, deployment, ADR or
Gate 4 → 5 transition is approved by this document.
