# DEBATE-012 — INTERNAL WEB REQUIREMENTS SYNTHESIS

Status: `PHASE-4 WORKING REQUIREMENTS / NO-CODE / TECHNOLOGY-NEUTRAL`
Date: 2026-09-19  
Scope: Browser-based Internal Data & Content Operations frontend and hosting requirements  
Decision level: Requirements and evidence boundary only; not an ADR and not a runtime, provider or framework selection

## 1. Purpose and decision boundary

This document consolidates the repository-approved product, workflow, workspace, security, API-runtime and evaluation
requirements into a browser-based Internal Data & Content Operations technology-requirements boundary. It is intended to
let a later Phase-5 ADR compare frontend and hosting alternatives against the same acceptance evidence.

The Internal Operations client is a **desktop-class, browser-based web application**. It is not an automatically packaged
desktop application, an authoritative offline console, a second consumer application or a provider administration console.
The browser is an operator surface; canonical data, publication eligibility, protected audit and high-consequence effects
remain behind the provider-neutral Kavriva API authority boundary.

This synthesis does **not** select a frontend framework, language, rendering model, browser vendor, hosting provider,
API runtime, database/CMS/search/index, identity provider, queue/worker, object store, analytics stack, AI provider or
paid plan. It also does not authorize code, a prototype, an executable spike, an account, a purchase or a Gate 4 → 5
transition.

### 1.1 Binding repository decisions

| Binding input | What it binds for this synthesis | What it deliberately leaves open |
|---|---|---|
| `DEC-0021` / `OPEN_QUESTIONS.md` `TSQ-002` | Internal Operations starts as a browser-based web application; desktop packaging is outside the current direction. | Framework, route count, responsive breakpoints, hosting and all service technology. |
| `DEC-0024` | Internal Operations approval, publication, recall and role mutations are authoritative online; unknown critical conditions fail closed. | Numeric windows, support matrix and implementation. |
| `DEC-0025` | Immutable approval/release meaning, fenced publication, explicit unknown/partial state, independent negative authority, protected audit and restore quarantine. | Physical topology, role/quorum details, technology and targets. |
| `DEC-0026` | Server-authoritative scoped authorization, privileged step-up, protected audit and quarantine-first ingestion. | Identity/policy/scanner/storage providers and numeric policies. |
| `DEC-0027` | Distinct release authorities, immutable artifact promotion, provenance/SBOM, verifier/trust-root separation and compatibility/revocation graph; no OTA channel is approved. | Exact artifact formats, signing, CI, hosting and deployment providers. |
| `DEC-0028`–`DEC-0030` | AI-native task/evidence graph, nontechnical owner, no-owner-debug operation and staged cost discipline. | Final team/support arrangement and spend plan. |
| `DEC-0034`–`DEC-0038` | API-mediated sensitive access, separate current/history/audit/object meanings, protected floors, account/session epoch, durable long-job semantics, state dictionary and clean-room exit gates. | Runtime/provider/plan/account/queue/worker/identity implementation; all remain held until evidence. |

### 1.2 Source and evidence discipline

The requirements below use the following evidence labels:

| Label | Meaning |
|---|---|
| `MUST` | A product or safety invariant that the chosen implementation must preserve. |
| `SHOULD` | A strong usability/operability requirement; a deviation needs a documented reason and evidence. |
| `OPEN` | Intentionally deferred product/strategy detail; this document must not invent it. |
| `HELD` | A capability is not proven safe/operable yet. `HELD` is not a pass. |
| `HARD FAIL` | A direct violation that rejects an alternative unless the gap is closed with equivalent evidence. |
| `EVIDENCE` | A no-code or later implementation/device/restore/exit artifact needed to claim a pass. |

No score, headline price, login success, HTTP 2xx, green dashboard, empty queue or completed background callback is
evidence of product correctness by itself.

## 2. Repository provenance

### 2.1 Authority chain

```text
Approved product rules and decisions
  ├─ 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md (IDCO-RQ-001..064)
  ├─ 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKFLOW_LIFECYCLE.md (W-01..W-13)
  └─ 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKSPACE_ARCHITECTURE.md (WS-01..WS-12)
          ↓
  04_TECH_STRATEGY/EVALUATION_CRITERIA.md
          ↓
  DEBATE-001 browser-surface boundary and no-code evidence scenarios
          ├─ DEBATE-010 identity/session/recovery/audit requirements
          └─ DEBATE-011 API boundary/long-job/state/restore requirements
          ↓
  DEBATE-012 browser frontend + hosting requirements (this document)
          ↓
  Later Phase-5 ADR and equal-evidence implementation acceptance
```

### 2.2 Requirement provenance map

| This synthesis area | Primary repository evidence | Binding interpretation |
|---|---|---|
| Client form and trust boundary | `00_CONTROL/CURRENT_STATE.md` Internal Data & Content Operations; `00_CONTROL/DECISION_LOG.md` `DEC-0021`; `DEBATE-001` §§6–10 | Browser web is approved; browser is not authority. |
| Dense workspaces and queues | Requirements `IDCO-RQ-004..008`, `IDCO-RQ-052..058`; Workspace `WS-01..WS-12`; Evaluation Criteria Internal Operations weights | Work-object-first, dense review, filterable and drillable surfaces are mandatory. |
| Lifecycle and states | Workflow `W-01..W-13`; Requirements `IDCO-RQ-017..044` | Edit, review, approve, release, publish, correction, rollback and recall are distinct. |
| Provenance and diffs | Requirements `IDCO-RQ-009..016`, `IDCO-RQ-019..024`; Workspace §§3, 6–8 | Current meaning, proposed meaning, evidence and event history remain traversable and separate. |
| Accessibility/responsive operation | Requirements `IDCO-RQ-063..064`; Workspace §10; Evaluation Criteria Internal Operations | Keyboard/assistive use, non-color status, stable focus/context and practical desktop-class responsiveness are required. |
| Authorization and stale sessions | `DEC-0026`, `DEBATE-010` §§3–8, `DEBATE-001` internal scenario 8 | Authentication is not authority; every sensitive commit is current, scoped and epoch-checked. |
| API effects and state dictionary | `DEC-0038`; `DEBATE-011` §§3–4, 4.7–4.10 | Browser requests are operation-bound; unknown/partial/held states are first-class and visible. |
| Files/media and untrusted ingestion | `DEC-0026`; `DEBATE-001` internal scenario 5; `DEBATE-011` §4.8 | Quarantine, lineage, digest, classification and controlled handles precede active use. |
| Browser/hosting/deploy/rollback | `DEBATE-001` §§7–10; `DEC-0027`; `DEBATE-011` §§4.9, 9 | Central updates reduce drift, but immutable artifact and cross-plane compatibility are required. |
| AI operation, cost and exit | `DEC-0028..0030`, `DEC-0037`, `DEC-0038`; `DEBATE-010` §§6–8; `DEBATE-011` §§7–10 | Owner-readable safe stops, bounded AI tasks, normalized BOM and clean-room exit are activation gates. |

## 3. Logical topology and authority boundary

```text
Operator browser
  ├─ authenticated session / step-up / scoped UI state
  ├─ queues, coverage, editor, diff, provenance, review, release, impact, analytics, audit
  └─ no canonical DB/object/publication/recovery authority
             │ HTTPS/API contract; operation ID; request fingerprint
             ▼
Provider-neutral Kavriva API boundary
  ├─ current actor/session/issuer/epoch and policy authorization
  ├─ exact object/scope/classification/version/generation checks
  ├─ protected audit precondition/receipt
  ├─ canonical transition + deterministic effect/outbox intent
  └─ explicit product state and reconciliation owner
             │
             ├─ canonical transactional domain state
             ├─ protected audit and monotonic negative floors
             ├─ quarantined object/media plane
             ├─ durable queue/worker for long jobs
             └─ consumer publication projection / versioned eligibility
```

### 3.1 Surface requirements

| ID | Requirement | Priority | Evidence |
|---|---|---|---|
| `IWEB-SURF-001` | The client must expose the conceptual work surfaces needed for queues, coverage, focused workspaces, detail, diff, review packet, release, impact, timeline and analytics drill-down. These are responsibilities, not a mandated route count. | `MUST` | Workspace §2; `WS-01..WS-12` |
| `IWEB-SURF-002` | The browser must preserve motorcycle/model/year/variant/modification scope, content state, version/freshness, provenance, conflict/uncertainty reason, affected dependents, actor role and last meaningful decision across hand-offs. | `MUST` | Workspace §6; `W-01..W-13` |
| `IWEB-SURF-003` | Opening a new surface must not silently reset scope, filters, selected object, unsaved draft, review context or security epoch. | `MUST` | Workspace §§6, 8; `DEBATE-011` §4.5 |
| `IWEB-SURF-004` | Internal UI may display and request transitions, but it must never directly change mobile application eligibility, release status, audit custody, role authority or recovery floors. | `MUST` | `DEBATE-001` §8; `DEC-0034`, `DEC-0038` |
| `IWEB-SURF-005` | Provider consoles, generic Data APIs/RPCs/views/functions, direct Storage paths and signed URLs must not become alternate operator authority. | `MUST` | `DEBATE-010` §4.7; `DEBATE-011` §4.7 |
| `IWEB-SURF-006` | The browser may provide safe read-only context during an outage only with timestamp/freshness disclosure; it must not infer currentness, approval or success from cached state. | `MUST` | `DEC-0024`; Workflow §7; `DEBATE-011` §4.10 |
| `IWEB-SURF-007` | Critical facts cannot be hidden by experience mode, commercial entitlement, narrow viewport or a generic dashboard summary. | `MUST` | `IDCO-RQ-064`; Workspace §10 |
| `IWEB-SURF-008` | The client must be replaceable without changing domain meaning or API authority contracts; shared UI is optional, shared vocabulary/contracts are not. | `MUST` | `DEBATE-001` §8; `DEC-0034` |

### 3.2 Browser is online-authoritative for internal mutations

The browser is allowed to prepare a draft or request work, but the following are **online-authoritative API operations**:

- review assignment/decision, approval, rejection and changes requested;
- release preparation and controlled publication;
- correction, supersession, rollback, suspension and recall;
- role/grant/policy/access changes and privileged recovery-adjacent actions;
- export/disclosure requests and any action that creates an external effect;
- source/evidence withdrawal when it changes current evaluation;
- canonical data/content mutation and status reconciliation.

If connectivity, authorization, protected audit, current generation, negative floor, account/billing or deployment
compatibility is unknown, the UI must show the corresponding `HELD`, `OUTCOME_UNKNOWN`, `SERVICE_UNAVAILABLE` or other
state from §8. It may preserve a recoverable unsaved/partial draft, but it must not claim that an offline click approved,
published, recalled, exported or changed canonical truth.

## 4. Workspace, queue and information-density requirements

### 4.1 Workspace coverage matrix

| Workspace | Required queue/detail content | Required guarded actions | Required non-success/failure behavior |
|---|---|---|---|
| `WS-01` Coverage & Research Queue | Scope/domain matrix; gap reason; consequence; age; owner; dependencies; next action; not researched/missing/incomplete/stale/conflicting/unreviewed/approved/published/recalled/not applicable. | Open/refine research; assign/claim; split nearby variant; pause/return with reason. | Empty is not complete; priority is not truth; unknown and not-applicable stay distinct. |
| `WS-02` Motorcycle/Variant | Identity hierarchy; distinguishing observations; applicability matrix; duplicate/nearby-scope conflict. | Create/refine scope; link distinction evidence; split/merge only by recorded decision; route dependent re-review. | Nearby variant never substitutes silently; unresolved fit blocks application eligibility. |
| `WS-03` Source & Provenance | Source register; evidence detail; applicability/date/actor; current evaluation vs historical use; graph or equivalent traversal; withdrawal impact. | Link/qualify/withdraw/mark stale or inaccessible; open dependent re-review; set private/shared/community/public scope. | Withdrawal preserves history and independently reevaluates dependents; source access is not trust. |
| `WS-04` Data & Content Editor | Exact target scope; current value/state beside proposal; evidence; validation; dependencies; teaching-only/application-eligible meaning; draft history. | Draft/edit; split claims; link evidence; record unknown/partial/unresolved/not applicable; save incomplete; submit. | Draft is never live; no silent overwrite; unresolved fit/source blocks application eligibility. |
| `WS-05` Missing/Stale/Conflict Review | Grouped issue queue; side-by-side competing sources/claims; missing distinction; stale/withdrawn impact; previous decisions. | Request evidence; narrow/split scope; record bounded decision; return draft/research; route review/recall. | No automatic winner or fabricated confidence; unresolved is a valid outcome. |
| `WS-06` Reviewer & Approval Queue | Review type/risk/age/scope/capability; review packet; diff; evidence; impact; conditions/expiry; prior decisions. | Claim/start review; changes requested; bounded approve/reject/unresolved; delegate/return. | Review is not publication; approval is exact-scope/version only; separation of duties is visible. |
| `WS-07` Release & Publication | Exact included versions; readiness checklist; dependency/impact; excluded/unresolved/recalled scope; progress/status; mobile availability. | Create/inspect candidate; hold/return; request controlled publish; inspect/retry/reconcile; supersede/recall. | Partial/failure/delay remains explicit; mixed versions require an explicit state, not “live”. |
| `WS-08` Version & Release Lineage | Timeline; current/prior diff; scope/evidence/reviewer/release lineage; historical use; superseded/recalled history. | Compare; open correction; select known-good rollback candidate; link historical use. | Rollback is a new event; old version/use is never erased or silently rewritten. |
| `WS-09` Quality & Operations Analytics | Coverage vs completeness vs reviewed/published; freshness/withdrawal; backlog age; publish latency/failure; rollback/recall/re-review; slices. | Filter/drill; open underlying work; create research/correction item; annotate operational context. | Unknown/unresolved/unreviewed counts remain visible; metrics never auto-publish or overwrite. |
| `WS-10` Audit & Change History | Object timeline; actor/action/time/scope; old/new state/version; approval/publish/recall chain; access/export history. | Inspect/compare/trace; open correction/investigation; produce auditable handoff. | Audit is permissioned and protected; ordinary erasure is unavailable. |
| `WS-11` Correction/Rollback/Recall | Severity/reason/owner; impact graph/list; application restriction vs teaching/history; active/completed work; replacement/rollback; reach-back; closure. | Triage; suspend/recall; draft correction; select known-good; re-review; publish replacement; reopen/close with rationale. | Recall is not deletion; started work retains safe closure/recovery; no guessed rollback. |
| `WS-12` Roles/Access/Policy | Capability matrix; scope visibility; propose/review/approve/publish/recall/audit; separation warnings; future vs historical attribution. | Inspect/request/change access through controlled API; inspect effective scope; audit handoff. | Access removal cannot erase history; private/community moderation cannot become official approval. |

### 4.2 Queue requirements

| ID | Requirement | Priority |
|---|---|---|
| `IWEB-QUEUE-001` | Every queue item must identify object scope, current state, consequence/risk, age, owner/role, evidence/gap reason, dependencies and the next safe action. Assignment is not approval. | `MUST` |
| `IWEB-QUEUE-002` | Queues must filter and sort by motorcycle/model/year/variant, technical/content domain, state, risk/consequence, source type, freshness, owner, age, dependency, interaction depth and time period where permitted. | `MUST` |
| `IWEB-QUEUE-003` | Queue counts must expose unknown, unresolved, not applicable, not-yet-reviewed, blocked, partial and recalled items; no denominator may hide them without explanation. | `MUST` |
| `IWEB-QUEUE-004` | A summary count, KPI or priority score must drill to the exact research item, claim, evidence, decision and audit event that produced it. | `MUST` |
| `IWEB-QUEUE-005` | Bulk operations, if later supported, must be scope-previewed, permission-checked, operation-identified and impact/audit-bound; they must not bypass bounded review or independent approval. | `MUST` |
| `IWEB-QUEUE-006` | Large queues must remain usable through a documented result-window/pagination strategy; no unbounded DOM/render or request behavior may make a critical queue unusable. The strategy must not change ordering or state meaning. | `MUST` |
| `IWEB-QUEUE-007` | Queue refresh, filter changes and back navigation must preserve scope and make freshness/loading/partial failure explicit. | `MUST` |

### 4.3 Dense tables and practical operator layouts

Dense table views must keep the following minimum context visible or one deliberate action away: scope; state and
eligibility; version/release; freshness; risk; owner; evidence/provenance strength; unresolved reason; dependent count;
and next action. Status cannot be communicated by color alone.

Required behaviors:

1. Sticky or otherwise persistent scope/state context when scrolling a large table.
2. Deterministic sorting/filtering with active-filter summary and clear reset.
3. Column visibility/density controls may reduce noise but may not hide critical safety, fit, uncertainty, recall,
   version or permission facts without an explicit warning.
4. Row selection must not confuse a displayed projection with a committed operation; every mutation has operation state.
5. Multi-pane desktop review may show queue + detail + diff/provenance together. On narrower viewports, panes may stack or
   become deliberate tabs, but the system must preserve context and focus.
6. If a viewport cannot safely support a dense write/review action, the UI must say “desktop-class view required” (or
   equivalent plain-language reason) and provide safe read/return behavior; it must not hide a dangerous control or make
   a narrow viewport appear complete.

## 5. Diff, provenance graph and impact requirements

### 5.1 Version/diff contract

| ID | Requirement | Priority |
|---|---|---|
| `IWEB-DIFF-001` | Every proposed change shows exact target scope, current meaning/state, proposed meaning/state, version/generation and change reason. For a new item, prior value is explicit absence, never invented. | `MUST` |
| `IWEB-DIFF-002` | Diffs work at the claim/content and guide-step level where applicable, including prerequisites, warnings, measurements, expected outcomes, applicability and consumer meaning. | `MUST` |
| `IWEB-DIFF-003` | Added, removed, changed, unchanged, unknown, unresolved and not-applicable facts have distinct accessible semantics; whitespace or visual decoration cannot be the only difference signal. | `MUST` |
| `IWEB-DIFF-004` | Current value and event/version history are separate; a newer value never erases prior dispute, correction, withdrawal, approval or use. | `MUST` |
| `IWEB-DIFF-005` | Reviewers can approve a bounded claim/content unit while leaving another conflict or unsupported unit unresolved. The UI must not force false all-or-nothing completeness. | `MUST` |
| `IWEB-DIFF-006` | Any diff affecting a published/active physical-work context exposes affected variants, guides, records, interaction depth and safe stop/recheck/remap implications. | `MUST` |
| `IWEB-DIFF-007` | Concurrent change or stale generation produces a visible conflict/re-review path; last-write-wins is prohibited for trust-critical content. | `MUST` |
| `IWEB-DIFF-008` | Diff export/inspection is permissioned and auditable; exported data is a disclosure event and cannot imply that copied data was retracted. | `MUST` |

### 5.2 Provenance graph contract

```text
Motorcycle scope (make/model/year/variant/modification)
       │ applicability / fit
       ▼
Research item ──reason/priority/owner──► gap / queue item
       │
       ├── source ──contains/observes──► evidence
       │                                  │ supports / disputes / withdraws
       ▼                                  ▼
Claim or content assertion ──depends-on──► guide step / warning / prerequisite / outcome
       │                                     │
       ├── current meaning/state             ├── draft → validated → reviewed → approved version
       └── event history                     └── release → published eligibility → consumer use
                                                   │
                                                   └── correction / supersession / rollback / recall impact

Audit/review/decision events attach to every edge and node; traversal must work in both directions.
```

| ID | Requirement | Priority |
|---|---|---|
| `IWEB-TRACE-001` | A source/evidence view traverses to every dependent claim/content unit and consumer/release impact, subject to authorization. | `MUST` |
| `IWEB-TRACE-002` | A claim/content/version view traverses back to sources, evidence, applicability, collector, reviewers, decisions, releases and affected use. | `MUST` |
| `IWEB-TRACE-003` | A correction/recall/withdrawal view traverses forward to affected variants, guides, records, releases, active/historical work and re-entry path. | `MUST` |
| `IWEB-TRACE-004` | Graph edges carry relation type, scope, current/historical status, date where known, actor and reason. A file attachment without a relation is not provenance. | `MUST` |
| `IWEB-TRACE-005` | Source access, evidence availability, current evaluation visibility and historical trace are independently displayed. | `MUST` |
| `IWEB-TRACE-006` | Evidence may be withdrawn, inaccessible, superseded, disputed or insufficient without deleting the historical link; dependent claims are re-evaluated independently. | `MUST` |
| `IWEB-TRACE-007` | Community/private/public and official/teaching-only/application-eligible classifications remain visible and cannot be inferred from a publication badge. | `MUST` |

## 6. Lifecycle, review and controlled publication

### 6.1 Required lifecycle

```text
Research requested
  → Research active ↔ Evidence pending
  → Draft
  → Validation blocked / Conflict review (as needed)
  → In human review
  → Changes requested ↺ Draft/Research
  → Approved (exact snapshot)
  → Release candidate
  → Published / Publication partial / Publication failed
  → Monitoring
  → Correction / Superseded / Rollback / Suspended-recalled / Withdrawn
  → Re-review → Replacement release
```

`Archived` is historical retention, not current authority. `Teaching-only`, `Historical-only`, `Insufficient evidence`,
`Unresolved` and `Not applicable` are meaningful outcomes, not missing UI values.

### 6.2 Gate requirements

| Gate | Required evidence before the next positive transition | Forbidden shortcut |
|---|---|---|
| Research → Draft | Identity/scope, applicability, evidence relation, missing/unknown reason and intended meaning. | Nearby-variant guess or value filled only to complete a form. |
| Draft → Validation | Current/proposed diff, change reason, linked evidence, dependent claims/guides and recoverable draft. | Silent overwrite or direct mobile-live edit. |
| Validation → Review | No suppressed fit/provenance/staleness/conflict/unsupported-assertion findings; unresolved items bounded. | Treating validation as real-world correctness. |
| Review → Approved | Authorized reviewer, exact snapshot/scope, evidence considered, rationale, conditions/expiry and independence as required. | Self-approval or scope expansion by UI convenience. |
| Approved → Release candidate | All included versions approved, dependencies checked, unresolved/excluded/recalled scope explicit. | Mixing draft, conflict or recalled content as eligible. |
| Release → Published | Guarded current authorization, generation/floor checks, protected audit receipt and explicit operation result. | UI confirmation, HTTP 2xx, queue-empty or provider console as proof. |
| Published → Correction/Recall | Reason, severity, scope, source/evidence basis, owner, interaction-depth impact and safe next action. | Delete/rewrite history or guessed rollback. |
| Recall → Re-entry | Supported replacement/known-good candidate, re-review/approval and controlled republish. | Clearing a recall with a stale/old artifact. |

### 6.3 Review packet minimum

Every high-consequence review packet must make one bounded decision possible without hunting across unrelated surfaces:

- exact motorcycle/model/year/variant/modification and content scope;
- current/proposed meaning and version/generation;
- claim/content and guide-step diff;
- sources/evidence, applicability, retrieval/observation date where known, withdrawal/staleness/dispute state;
- validation findings and unresolved gaps;
- prior decisions, review history and separation-of-duties status;
- affected dependencies, release/use and interaction-depth impact;
- conditions, expiry/freshness expectation and next safe action;
- operation identity and API state, including audit receipt/readiness.

## 7. Accessibility, keyboard and responsive practical layout

### 7.1 Accessibility requirements

| ID | Requirement | Priority |
|---|---|---|
| `IWEB-A11Y-001` | No critical operation may require a mouse, hover, color perception or a visual-only graph. Keyboard-only operators must be able to inspect, filter, open, review, submit, cancel and recover. | `MUST` |
| `IWEB-A11Y-002` | Focus order follows the visible task order; focus is visible; opening a dialog/warning/diff moves focus predictably and returns it to the invoking control when closed. | `MUST` |
| `IWEB-A11Y-003` | Tables expose meaningful headers, row/column context, sort/filter state, selection state and changed values to assistive technology. | `MUST` |
| `IWEB-A11Y-004` | Status, warnings, conflict, recall, permission and operation-result semantics are conveyed through text/structure in addition to color, icon or badge. | `MUST` |
| `IWEB-A11Y-005` | Validation and authorization errors identify the affected field/object, reason, blocked action and safe next action; announcements do not steal focus from unrelated work. | `MUST` |
| `IWEB-A11Y-006` | Provenance graphs have a keyboard/linear equivalent with node labels, relation labels, scope, status and a path back to the source/claim. | `MUST` |
| `IWEB-A11Y-007` | Dense content remains readable under zoom, large text, high contrast and reduced-motion settings supported by the chosen browser/platform. | `MUST` |
| `IWEB-A11Y-008` | Step-up authentication, re-authentication, upload progress, cancellation and stale-session recovery are operable with keyboard and assistive technology. | `MUST` |
| `IWEB-A11Y-009` | Language/unit/accessibility preferences must not require a consumer profile or hide critical facts. Turkish-first product context remains supported without changing semantics. | `MUST` |
| `IWEB-A11Y-010` | The Phase-5 acceptance matrix must identify representative keyboard and assistive-technology combinations; simulator or AI assertion alone is not evidence. | `MUST` |

Exact conformance target, browser/assistive-technology pairs and visual tokens remain `OPEN`; the absence of a selected
standard is not permission to ship a keyboard or non-color blocker.

### 7.2 Responsive, desktop-class behavior

| Viewport class | Required behavior | Explicit limit |
|---|---|---|
| Wide desktop | Multi-pane queue + detail + diff/provenance/review; dense tables; bulk context preview; persistent scope header. | Must not imply that all actions are safe merely because space is available. |
| Narrow desktop/tablet | Deliberate pane stacking or tabs; persistent object/scope/version context; no clipped critical columns; keyboard order remains predictable. | Exact breakpoints and layout technology are `OPEN`. |
| Phone/narrow browser | Safe read/triage/status and return-to-desktop path may be supported if declared; critical facts and operation state remain visible. | Dense approval/publish/recall need not be phone-capable; unsupported writes must be explicit, not silently hidden. |
| Degraded network/offline | Preserve view context and recoverable draft if implemented; show last-known time and service state. | No offline authoritative approval, publication, recall, role/policy mutation or export success. |

`IWEB-RESP-001` requires that every supported viewport have a practical layout for its declared actions. A candidate that
requires a desktop wrapper solely to make the approved browser form usable reopens the product direction; it is not an
automatic fallback.

## 8. Security, session, stale tab and privileged operation requirements

### 8.1 Authorization tuple

Authentication proves a session/issuer; it does not grant product authority. Before every sensitive effect, the API must
evaluate a current tuple containing:

```text
actor/workload + provider-qualified principal
issuer + current session + assurance/step-up + security epoch
action + exact resource/object + tenant/owner + scope + classification
role/grant/delegation + competence + independence + policy/access version
object/version/generation + release/schema/config/package/client capability
current recall/suspension/revocation/deletion/accepted-operation floors
operation ID + immutable request fingerprint + intended effect/reason
protected audit readiness/receipt + runtime/dependency compatibility
```

Cached claims, `user_metadata`, an open browser tab, a hidden button, provider role, browser-supplied ID or RLS result is
not sufficient authority.

### 8.2 Security/session requirements

| ID | Requirement | Priority |
|---|---|---|
| `IWEB-SEC-001` | Privileged/high-consequence actions require phishing-resistant, user-verified, transaction/resource-bound step-up with correct origin/RP/redirect/challenge semantics. | `MUST` |
| `IWEB-SEC-002` | Factor enrollment/removal/loss, recovery, downgrade, stolen-token, logout-all, key rotation, browser CSRF/PKCE/origin and accessibility behavior are explicit tested states. | `MUST` |
| `IWEB-SEC-003` | Provider session identity, Kavriva principal, role/grant/delegation, competence/independence and historical audit actor remain separate. | `MUST` |
| `IWEB-SEC-004` | Security-epoch revocation reaches current/pending/in-flight operations, lost-response retries, worker leases, private object handles, browser cache/service worker, open tab, exports and locally retained classified packages. | `MUST` |
| `IWEB-SEC-005` | Downloaded copies cannot be remotely guaranteed to disappear; residual risk and last-known status are represented honestly. Remote wipe is not authority. | `MUST` |
| `IWEB-SEC-006` | Browser bundles, repositories, logs and ordinary AI task contexts never contain service-role, provider-owner, billing-root, unrestricted SQL/SSH, raw SMTP/SMS or equivalent high-consequence credentials. | `MUST` |
| `IWEB-SEC-007` | Cross-tenant/resource/scope checks apply to reads, diffs, status lookup, exports, previews, audit views and mutations; an operation ID cannot disclose another tenant's result or payload. | `MUST` |
| `IWEB-SEC-008` | Private object handles are short-lived and bound to exact audience/scope/object/version/epoch; stale or revoked handles fail closed. | `MUST` |
| `IWEB-SEC-009` | Exact cookie/token storage, TTL, reauthentication windows and numeric access-review/session limits remain provider-neutral `OPEN` values that must be declared and evidenced before activation. | `OPEN`/`MUST` |

### 8.3 Stale-tab and stale-session protocol

1. Every mutating view carries a server-issued policy/access version, security epoch, object/version/generation and release
   context.
2. On commit, the API rechecks the full authorization tuple and current negative floors; client state cannot override it.
3. If the tab is stale, role revoked, policy changed, object changed, release recalled or epoch advanced, the operation is
   `DENIED`, `HELD` or `DEPLOYMENT_HELD` as applicable. It is never silently merged or last-write-wins.
4. The UI preserves the operator's draft and review evidence where safe, explains what changed, identifies the resolver and
   offers refresh/review/rebase/return—not a blind “continue anyway”.
5. If the session/epoch is revoked, all high-consequence controls and handles are invalidated across tabs; re-authentication
   cannot silently reuse a pre-revocation approval.
6. If the response is lost after submission, the UI shows `OUTCOME_UNKNOWN` and resolves by the same operation ID through a
   disclosure-safe status lookup. Retrying a different payload/scope/actor becomes `CONFLICT/HELD`.

## 9. API contract and shared state dictionary

### 9.1 API contract requirements

| ID | Requirement | Priority |
|---|---|---|
| `IWEB-API-001` | All sensitive reads/writes and every high-consequence effect go through the Kavriva API boundary; client/provider-console direct paths are inventoried and negatively tested. | `MUST` |
| `IWEB-API-002` | Operation identity binds actor/tenant/action/resource/scope/classification and immutable payload fingerprint. | `MUST` |
| `IWEB-API-003` | Same operation identity + same semantic request returns the existing result read-only; changed payload/scope/actor/intended effect is `CONFLICT/HELD`; cross-tenant lookup is `DENY`. | `MUST` |
| `IWEB-API-004` | The authoritative core binds operation acceptance, current authorization/generation fence, canonical transition, protected audit receipt reference, deterministic effect intent and reconciliation state. | `MUST` |
| `IWEB-API-005` | Object, queue, notification, scanner, AI/OCR and external effects use deterministic keys, manifest, lease/retry budget, generation/epoch recheck and explicit reconciliation; physical cross-plane atomicity is not claimed. | `MUST` |
| `IWEB-API-006` | Known long jobs use durable queue/worker semantics with lease/heartbeat/checkpoint, bounded retry, DLQ/quarantine, poison/backpressure, cancel, deploy drain, message compatibility and owner-visible backlog. | `MUST` |
| `IWEB-API-007` | Background callbacks, `waitUntil`, an empty queue or worker success are not durable acceptance or exactly-once proof. | `MUST` |
| `IWEB-API-008` | Protected audit receipt/precondition is accepted before positive high-consequence effect; missing primary and sufficiently independent fallback custody yields `AUDIT_HELD`. | `MUST` |
| `IWEB-API-009` | Newer recall/suspension/revoke/delete/object/package/accepted-operation/migration floors beat old runtime, queue, cache, handle, package or restore state; unknown/tie holds. | `MUST` |
| `IWEB-API-010` | API responses expose a state, operation ID where applicable, timestamp/version/generation, retained data, allowed/blocked effects, retry/reconciliation behavior, resolver/support owner and restore/exit implications. | `MUST` |

### 9.2 Single state dictionary

The browser, API, queue/worker status, owner runbook and audit views use one semantic dictionary. The exact visual treatment
is open, but the meaning and next action are not.

| State | Meaning | Allowed effects | UI minimum | Never infer from |
|---|---|---|---|---|
| `ACCEPTED` | Canonical effect and required audit evidence are proven. | Follow-on effects only under their own current checks. | Operation/result, exact version/generation and audit reference. | HTTP 2xx alone. |
| `QUEUED/SUBMITTED` | Request accepted; canonical external effect not yet proven. | Status lookup, cancel where allowed, bounded retry policy. | Queue/operation identity, expected next event and owner-visible progress. | Button click or queue presence alone. |
| `DENIED` | Current policy/authority explicitly rejects effect. | Safe read, escalation or corrected request. | Reason, scope, resolver and non-destructive next action. | Hidden button. |
| `HELD` | Positive action lacks required safe condition/evidence. | Add evidence, re-auth, resolve conflict or await owner/support. | Blocking gate and exact resolver; preserved context. | “No error” or stale green page. |
| `OUTCOME_UNKNOWN` | Response/connection ended before canonical result could be proven. | Same-ID status lookup/reconciliation; no blind duplicate. | Honest uncertainty, operation ID and safe retry rule. | Timeout treated as failure or success. |
| `PARTIAL/RECONCILING` | Some planes/effects differ; closure is in progress. | Reconcile through owner/worker path. | Affected scope, retained data, next action and no false completion. | Partial list or one successful plane. |
| `AUDIT_HELD` | Protected audit receipt/custody is missing or unverifiable. | Hold positive effect; restore/audit recovery. | Audit gate and support/custody owner. | Provider log or `audit_intent` alone. |
| `BILLING_HELD` | Safe required capability cannot run within approved cost/plan/limit. | Stop, approve cost, reduce scope only if safety unchanged. | Cost line, cap/overage, stop action and owner decision. | Headline plan price. |
| `ACCOUNT_HELD` | Provider/account/legal/support/recovery prerequisite is unavailable. | Plain-language escalation; no positive authority. | External dependency and owner action. | Successful login. |
| `DEPLOYMENT_HELD` | Release/client/schema/config/message/negative-floor compatibility is unsafe. | Drain, forward-recover, align releases. | Release IDs, incompatibility and safe action. | Green health endpoint. |
| `OBJECT_QUARANTINE` | Original/derived object is awaiting type, digest, malware/archive/SSRF/render/classification checks. | Isolated inspect/review only. | Quarantine reason, lineage and next scan/review. | Preview or scan completion. |
| `RESTORE_QUARANTINE` | Restore/import is not reconciled against current authority/floors. | Read/compare/reconcile in isolation. | Restore manifest, missing planes and anti-resurrection status. | Successful backup/import job. |
| `EXPORT_PARTIAL` | Export omitted/failed on one or more planes or disclosures. | Resume/reconcile with explicit scope. | Included/excluded data and disclosure audit. | Download completion. |
| `SERVICE_UNAVAILABLE` | Required dependency is unavailable. | Safe read if declared; hold positive mutation. | Dependency, timestamp, retained work and support path. | Cached currentness. |
| `RECOVERY_REQUIRED` | Incident/restore/exit needs controlled recovery. | Runbook/authorized support/reviewer path. | Owner-readable next action and external actor. | Owner SQL/SSH/debugging. |

Lifecycle states from the product workflow (`Research requested`, `Research active`, `Evidence pending`, `Draft`,
`Validation blocked`, `Conflict review`, `In human review`, `Changes requested`, `Approved`, `Release candidate`,
`Published`, `Superseded`, `Suspended/recalled`, `Withdrawn`, `Archived`) remain separately visible. They are not replaced
by transport state.

## 10. File, document and media requirements

| ID | Requirement | Priority |
|---|---|---|
| `IWEB-OBJ-001` | File/URL/material intake is quarantine-first; no original or derived object becomes active/public/technical evidence merely because upload, scan, render or AI/OCR completed. | `MUST` |
| `IWEB-OBJ-002` | Intake preserves original bytes/reference, size/type, digest, version, source identity, retrieval/observation context, classification, lineage and retention/disclosure state. | `MUST` |
| `IWEB-OBJ-003` | Validate declared and observed type, size/resource limits, archive nesting/decompression, traversal, malformed media, malicious payload and duplicate/orphan behavior before active use. Exact limits remain `OPEN` but cannot be unbounded. | `MUST` |
| `IWEB-OBJ-004` | URL fetch requires SSRF/private-network protection, redirect policy, scheme/host controls, timeout/resource bounds and evidence that the fetched material is the claimed source. | `MUST` |
| `IWEB-OBJ-005` | Untrusted preview/rendering is isolated from operations credentials and authority; previews carry untrusted status and exact source/derived lineage. | `MUST` |
| `IWEB-OBJ-006` | Derivatives inherit the most restrictive classification and remain linked to the original; withdrawal/revocation propagates to handles and derivatives. | `MUST` |
| `IWEB-OBJ-007` | Private object access uses short-lived, exact audience/scope/object/version/epoch handles or server mediation; expired/revoked/stale handles fail closed. | `MUST` |
| `IWEB-OBJ-008` | Large upload, scan, render, derivative, OCR/AI, export/import, cleanup and reconciliation work uses the long-job contract; progress, cancel, retry, quarantine, DLQ and reconciliation are visible. | `MUST` |
| `IWEB-OBJ-009` | File/media UI exposes upload/processing/published/withdrawn/quarantined/failed/partial status and does not describe media as technical correctness, fit, diagnosis, maintenance or safety evidence without a separate attributable review. | `MUST` |
| `IWEB-OBJ-010` | Browser-insufficient file/device behavior is recorded as an explicit gap for strategy/user decision; a desktop wrapper is not introduced silently. | `MUST` |

## 11. Browser compatibility and client safety

The exact supported browser/OS/assistive-technology matrix is `OPEN` and must be set by a later evidence-backed decision.
The requirements for that decision are fixed:

| Compatibility area | Required evidence |
|---|---|
| Supported desktop browsers and OS versions | Declared support and tested login, session, navigation, tables, diff, upload, download, step-up, error and stale-tab flows. |
| Keyboard and assistive technology | Representative keyboard-only and screen-reader paths through queue, diff, provenance, decision, upload and recovery. |
| Storage/cookies/redirects | Safe behavior when storage is unavailable/cleared, session expires, origin/redirect is unexpected or an old tab remains open. |
| Network and time | Offline/disconnected, slow/interrupted, reconnect, changed device clock, lost response and duplicate retry behavior. |
| Browser cache/service worker (if used) | Old asset/API contract, revoked session, negative floor and recalled content cannot regain authority. |
| File/media APIs | Type/resource limits, quarantine, large-file progress, cancellation, preview isolation and access revocation. |
| Viewports and zoom | Wide desktop, narrow desktop/tablet, declared narrow-browser behavior, zoom/large text and reflow. |
| Security mechanisms | CSRF/PKCE/origin/redirect, step-up, logout-all, key rotation, stale session and cross-tenant disclosure tests. |

Compatibility unknowns must remain visible as `HELD` or `DEPLOYMENT_HELD`; “works in one browser” is not a support claim.
Unsupported browser behavior must be an explicit safe state with a readable reason and next action, not hidden controls or
partial authority.

## 12. Hosting, deployment, release and rollback requirements

### 12.1 Hosting requirements

| ID | Requirement | Priority |
|---|---|---|
| `IWEB-HOST-001` | Hosting must support central, versioned web release and rapid safe withdrawal/hold without requiring operators to update individual desktop clients. | `MUST` |
| `IWEB-HOST-002` | The hosted client must use a secure origin and a documented boundary for session, origin, redirect, browser cache and asset handling. Exact hosting product is `OPEN`. | `MUST` |
| `IWEB-HOST-003` | Client hosting cannot confer canonical DB/object/publication/recovery authority and cannot require provider-console action for normal product operation. | `MUST` |
| `IWEB-HOST-004` | A deploy exposes release identifier, client capability and compatible API/schema/config/message/content context for safe diagnosis by AI/support; no raw secret or privileged credential is exposed. | `MUST` |
| `IWEB-HOST-005` | Hosting failure has an owner-readable `SERVICE_UNAVAILABLE`/`RECOVERY_REQUIRED` path; the owner is not asked to SSH, edit DNS blindly or repair raw logs. | `MUST` |
| `IWEB-HOST-006` | Web hosting, API, data, object, audit/floor, queue/worker, observability, DNS/TLS, notification, support and recovery costs are evaluated together; a cheap client host cannot hide unsafe adjuncts. | `MUST` |

### 12.2 Artifact and deploy contract

Each web release must bind the reviewed source, declared dependency closure, workflow/build inputs, exact artifact digest,
provenance, SBOM or equivalent dependency evidence, independent verification, approval/signature, compatibility, rollout
and revocation/suspension context. Production promotes the exact verified artifact; it is not silently rebuilt from mutable
source at deploy time.

Deploy compatibility must include at least:

```text
web release_id / artifact digest / client capability
API contract + DB schema/migration/config generation
queue/worker message generation and drain state
content/object/package manifest and current negative floor
session/security epoch and revocation generation
```

Mismatch is `DEPLOYMENT_HELD`; a green health probe does not override it. Data-forward recovery is preferred over binary
rollback when new valid data exists.

### 12.3 Rollback and recall behavior

1. A rollback is a new guarded event to a known-good, compatible, not-recalled predecessor; it preserves the intervening
   artifact, approval, publication window, provenance and affected-use history.
2. An old web artifact, browser cache, service worker, queue message, object handle or offline package cannot clear a newer
   recall, suspension, revoke, delete, accepted-operation or migration floor.
3. If no known-good version exists, the affected operation is suspended/recalled with teaching/history/safe-recovery
   handling; the system must not guess a rollback.
4. Partial deploy, failed asset/API compatibility, old-revision drain failure and delayed cache propagation remain explicit
   `PARTIAL/RECONCILING` or `DEPLOYMENT_HELD` states.
5. Emergency negative authority is independent to the failure-domain level required by later evidence; normal publication
   cannot clear a newer stop.

## 13. AI-operated delivery and no-owner-debug requirements

### 13.1 AI task contract

Every implementation, deployment, migration, incident, restore, cost or exit task must have a machine-readable task pack
containing:

- exact objective, object/scope and allowed/forbidden paths;
- relevant requirements, design references, API/state contracts and negative cases;
- short-lived credential audience/expiry (if any), with no provider-owner or unrestricted authority;
- dry-run/expected operation ID and generation/floor;
- hard stop and rollback/forward-recovery rule;
- evidence digest, independent reviewer and validator;
- required external human/provider action and plain-language owner handoff;
- completion evidence, unresolved `HELD` items and next safe action.

AI may not receive provider owner, billing root, service-role, unrestricted SQL/SSH, global object keys, approval,
publication, privileged recovery or emergency-negative human/organizational authority. AI/OCR/extraction creates
attributable proposals only; hostile document instructions have no workflow/policy/tool authority.

### 13.2 No-owner-debug contract

| Incident/capability | System must provide without owner debugging |
|---|---|
| Stale session/tab | Plain-language reason, preserved draft/context, re-auth/refresh/review action and operation status. |
| Lost response/duplicate | Operation ID, disclosure-safe status lookup, same-ID retry and different-payload conflict. |
| Publish/recall failure | Affected scope, current state, retained data, resolver/support owner, retry/hold/stop action and audit reference. |
| Queue/worker issue | Backlog/lease/DLQ state, automatic safe stop, bounded retry and external support path; no queue surgery. |
| Object quarantine | Reason, lineage, scan/review action and classification; no manual storage bypass. |
| Billing/quota/account hold | Cost/plan line, cap/overage, safe stop and plain-language approval/support decision. |
| Restore/exit issue | Missing plane/manifest, quarantine state, anti-resurrection result and named recovery owner. |
| Security/recovery incident | Session/epoch deny state, independent recovery/negative actor, evidence custody and escalation. |

The owner can make understandable `approve / hold / stop / payment / legal-support` decisions. The owner is never the
repair mechanism for code, builds, SQL, SSH, raw logs, queue state, secrets, restore cutover or provider-console recovery.

## 14. Cost, hosting lock-in and clean-room exit

### 14.1 Normalized safe-cost requirements

Before any provider/account/plan approval, alternatives must use the same bill-of-materials rows and evidence horizon:

| Cost line | Minimum questions |
|---|---|
| Web hosting/CDN/edge/instance | Free path; build/deploy quota; bandwidth/egress; hard cap; overage stop; incident behavior. |
| API/runtime and transaction/network | Invocation/compute/minimum uptime; concurrency; pooler/TLS/region/egress; support. |
| Database/Auth/private object storage | IO/bytes/ops/MAU/MRU; backup/PITR; object bytes separately; provider lock-in. |
| Durable queue/worker | Retention/retry/DLQ/backpressure/scheduler; long-job cost and stop behavior. |
| Protected audit/fallback/floor | Independent custody, retention/legal hold, restore/reconciliation and incident cost. |
| Scanner/preview/derivative/object backup | Quarantine, temporary storage, scan/render, restore and orphan-cleanup cost. |
| Observability/support/incident | Logs/metrics/traces, export/alerting, support tier, external recovery person/organization. |
| DNS/TLS/domain/SMTP/notifications | Renewal, delivery/abuse, outage and account recovery dependencies. |
| Deploy/schema/message compatibility | Artifact registry, signing/verification, secret/key rotation, drain and forward recovery. |
| Clean-room restore/exit and AI task operation | Isolated drill, replacement environment, evidence custody and AI-run cost. |

Every line is classified `mandatory / deferrable / optional / scale-triggered` with current official date/plan/region,
unit/quota/overage, cap, tax/FX/card uncertainty, stop state, incident/restore/exit effect and owner approval. The later
TRY 2,000–3,000/month amount is a planning ceiling, not spend authorization. If mandatory assurance does not fit, the
capability remains `BILLING_HELD/HELD`; safety, privacy, continuity, accessibility and recovery are not weakened.

### 14.2 Clean-room exit requirements

An export, provider migration or hosting replacement is complete only after isolated, quarantined import and reconciliation
of all relevant planes:

```text
canonical current/history/provenance and applicability
operation ledger/status/conflict/tombstone/outbox
release/package/artifact/schema/config/message generations
principal/policy/grant/competence/session/epoch/recovery state
object bytes + digest/lineage/classification/retention/disclosure
protected audit/fallback/floor and incident/impact graph
queue pending/DLQ/lease + runtime artifact + secret reissue + DNS cutover
```

The source environment remains untouched until independent acceptance. Old revoke/recall/delete/suspension/accepted
operations cannot resurrect; new valid data cannot disappear through silent rollback. Missing or unverified planes remain
`EXPORT_PARTIAL` or `RESTORE_QUARANTINE`. The frontend/hosting choice is rejected if clean-room replacement requires
rewriting product meaning, provider-console-only authority or owner technical repair.

## 15. Phase-5 acceptance criteria and evidence matrix

No `PASS` may be claimed from documentation alone where real browser, accessibility, failure, restore, cost or exit evidence
is required. The following matrix is the minimum comparable evidence package for any frontend/hosting candidate.

| ID | Acceptance criterion | Minimum evidence | Hard-fail if |
|---|---|---|---|
| `WEB-AC-001` | All `WS-01..WS-12` responsibilities and required hand-offs are covered. | Traceability matrix + no-code task simulation + browser walkthrough. | A queue/detail/review/release/recall/audit responsibility is absent or loses context. |
| `WEB-AC-002` | Dense queue/table remains usable and drillable at representative scale. | Keyboard/AT walkthrough, load/resource evidence, filter/sort/pagination behavior. | Critical state/context is clipped, hidden, color-only or untraceable. |
| `WEB-AC-003` | Diff supports bounded claim/content/guide-step decisions. | Current/proposed/absence diff fixtures, concurrent change and conflict evidence. | Edit overwrites history, all-or-nothing false completeness or silent LWW occurs. |
| `WEB-AC-004` | Provenance graph is bidirectionally traversable. | Source→evidence→claim→version→release→use and reverse/impact walkthrough. | Withdrawal/recall cannot identify dependents or historical use. |
| `WEB-AC-005` | Lifecycle gates keep edit/review/approval/release/publication distinct. | State transition matrix and positive/negative API/UI walkthroughs. | `edit → instantly live`, self-approval or unbounded publish exists. |
| `WEB-AC-006` | Online authority is enforced by API, not UI visibility. | Direct-path and cross-tenant negative tests; provider-console bypass inventory. | Browser/direct provider path can mutate canonical truth or eligibility. |
| `WEB-AC-007` | Stale tab/session fails safely. | Changed policy/role/object/epoch/release tab race; preserved draft and re-review evidence. | Stale approval/publish/recall succeeds or old tab clears a newer negative floor. |
| `WEB-AC-008` | Operation idempotency and unknown outcomes are honest. | Timeout-before/after-commit, same-ID retry, changed fingerprint, disclosure-safe lookup. | Blind duplicate, false success/failure or cross-tenant status disclosure. |
| `WEB-AC-009` | Protected audit precedes high-consequence effects. | Primary/fallback outage, effect-before-audit, gap/fork/replay and restore evidence. | Provider log/`audit_intent` alone authorizes effect or audit outage still publishes. |
| `WEB-AC-010` | Privileged step-up/recovery/negative authority boundaries hold. | Origin/PKCE/CSRF/step-up/factor-loss/stolen-token/logout-all/outage/accessibility fixture. | Login or weak fallback grants publish/role/recovery authority; recovery creates positive truth. |
| `WEB-AC-011` | Object/media ingestion is quarantine-first. | Hostile archive/URL/SSRF/redirect/traversal/type/digest/derivative/handle-revoke fixture. | Upload/preview/scan/AI output becomes authority or private object bypasses scope/epoch. |
| `WEB-AC-012` | Long jobs are durable and reconcilable. | Kill/lease/retry/DLQ/poison/backpressure/deploy-drain/message-compatibility evidence. | Callback/empty queue/worker health is treated as exactly-once canonical effect. |
| `WEB-AC-013` | Full API state dictionary is visible and actionable. | State-to-UI/runbook/retry/retained-data/resolver matrix. | HTTP 2xx/green dashboard masks `HELD`, partial, unknown, quarantine or unavailable. |
| `WEB-AC-014` | Keyboard/assistive workflows are complete. | Keyboard-only + representative screen-reader/zoom/high-contrast/reduced-motion walkthrough. | Any critical queue/diff/review/step-up/recovery path is mouse-only, focus-lost or color-only. |
| `WEB-AC-015` | Responsive layouts are practical for declared viewports. | Wide/narrow desktop/tablet/narrow-browser test with scope/focus/state retention. | Dense write is silently clipped/hidden or browser form needs an unapproved desktop wrapper. |
| `WEB-AC-016` | Browser compatibility is explicit and safe. | Declared matrix; storage/cookie/cache/service-worker/time/network/file/security tests. | “Works in one browser” is used as production support; unsupported browser can exercise authority. |
| `WEB-AC-017` | Web artifact/deploy is immutable and compatibility-bound. | Artifact digest/provenance/SBOM/verification/signature/release graph and deploy-drain evidence. | Mutable rebuild, mixed incompatible client/API/schema/message or provider-console-only deployment. |
| `WEB-AC-018` | Rollback/recall cannot resurrect negative truth. | Bad release, known-good guarded rollback, cache/old-tab/queue/object/package race and restore fixture. | Old artifact/cache/restore clears recall, revoke, delete, suspension or accepted-operation floor. |
| `WEB-AC-019` | Owner-readable operations work without debugging. | Incident/outage/billing/account/restore/queue/object runbooks and tabletop. | Owner must use SQL/SSH/raw logs/queue surgery/secrets/provider-console repair. |
| `WEB-AC-020` | AI tasks are bounded and independently validated. | No-code task simulation, credential/scope audit, forbidden-operation tests and reviewer evidence. | AI can obtain provider owner, billing root, unrestricted data, approval, publication or recovery authority. |
| `WEB-AC-021` | Safe cost is normalized and stoppable. | BOM with current price/quota/overage/cap/stop/tax/FX/incident/restore/exit and approval states. | Headline price hides mandatory adjuncts, uncapped spend or unsafe cost reduction. |
| `WEB-AC-022` | Clean-room exit preserves product meaning. | Isolated cross-plane import, digest/manifests, anti-resurrection and dual-run/cutover evidence. | Missing plane is treated as success or migration requires silent semantic rewrite/owner repair. |

## 16. Hard-fail register

The following are non-negotiable rejection conditions for a frontend/hosting alternative unless the exact gap is closed by
equal or stronger evidence without weakening an approved invariant:

1. **Direct authority bypass:** browser, provider console, generic Data API/RPC/view/function/Storage/signed URL or client
   cache can mutate canonical technical truth, publication eligibility, protected audit, recovery or negative floors.
2. **Uncontrolled live edit:** a draft/edit path makes consumer technical content live without bounded validation, human
   review, approval, exact release and protected publication transition.
3. **False state:** UI treats HTTP 2xx, green health, worker success, empty queue, upload/scan/render completion or timeout
   as canonical acceptance/freshness/recall resolution without product-state evidence.
4. **Stale positive authority:** old tab, cached claim, old artifact, old queue message, old handle or restored backup can
   approve, publish, un-recall, re-grant, undelete or resurrect an older truth.
5. **Audit-before-effect failure:** high-consequence positive effect can occur without protected audit receipt or adequate
   independent fallback custody.
6. **Weak privileged path:** login, TOTP/SMS/magic-link fallback, cached role or provider admin status substitutes for
   phishing-resistant, user-verified, transaction-bound step-up and current API authorization.
7. **Recovery conflation:** account recovery can approve/publish/grant roles, or emergency negative authority can create
   positive truth/unsuspend/approve.
8. **Unquarantined ingestion:** hostile/unknown file, URL, archive, preview, derivative or AI/OCR result can enter active
   technical/public use without quarantine, lineage, classification, digest and controlled access.
9. **Non-durable long job:** package/scan/render/OCR/export/import/notification/reconciliation relies on a request callback,
   `waitUntil`, browser tab or empty queue as its durable completion mechanism.
10. **History/provenance loss:** withdrawal, role revoke, correction, transfer, rollback, recall, restore or delete silently
    erases attribution, evidence, dispute, prior version, use relation or independent data.
11. **Accessibility blocker:** critical queue/diff/provenance/review/step-up/recovery operation is mouse-only, focus-unsafe,
    color-only or unavailable to assistive interpretation.
12. **Unusable responsive contract:** a declared browser viewport clips/hides critical state or requires an unapproved
    desktop wrapper to perform the approved browser direction.
13. **No-owner-debug violation:** normal incident recovery requires the nontechnical owner to code, debug, SSH, run SQL,
    inspect raw logs, repair queues, rotate raw secrets or perform provider-console recovery.
14. **Unbounded/hidden cost:** mandatory assurance depends on uncapped or undisclosed spend, or cost pressure weakens safety,
    privacy, accessibility, audit, continuity, recovery or exit evidence.
15. **Unsafe exit:** provider/host replacement cannot preserve current/history/provenance, operation/tombstone, release,
    principal/policy/epoch, object lineage, audit/floor, queue and negative state in a clean-room test.
16. **Scope violation:** the strategy work creates code/prototype/spike, silently selects a runtime/provider/framework, or
    presents a held hypothesis as a production decision/ADR.

## 17. Explicitly deferred decisions for later ADR work

- frontend language/framework/rendering/state/library composition;
- exact browser/OS/assistive-technology support matrix and conformance target;
- navigation route count, breakpoint values, visual tokens and production copy;
- API runtime/language/framework, database/CMS/search/index, queue/worker and object/media provider;
- identity provider, cookie/token storage, numeric session/step-up/recovery windows and role/quorum matrix;
- publication batching/scheduling/transport, CDN/cache/service-worker policy and notification/reach-back channels;
- exact file/media limits, legal/privacy/retention/export policy and analytics/event pipeline;
- hosting provider, region/plan, support/recovery actors, paid adjuncts and final 12–24 month budget;
- whether any later desktop packaging is justified by browser-insufficient evidence (requires a new explicit user decision).

## 18. Phase-4 conclusion

The browser requirement is now sufficiently specific for no-code comparison: choose only among alternatives that can
preserve dense, traversable, keyboard-accessible, responsive desktop-class operations while keeping all high-consequence
authority online and API-mediated. The client must make lifecycle, provenance, diffs, queues, audit, object quarantine,
stale-tab behavior, partial/unknown states, deploy compatibility, owner-readable recovery, cost stop and clean-room exit
observable.

No frontend framework, hosting provider, API runtime or other technology is selected by this synthesis. Any candidate that
cannot close the acceptance matrix or triggers a hard fail remains `HELD`/rejected until the gap is resolved with equivalent
evidence; the standard is not lowered to make a technology fit.
