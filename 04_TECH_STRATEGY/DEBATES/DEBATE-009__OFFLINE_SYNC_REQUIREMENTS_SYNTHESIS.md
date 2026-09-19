# DEBATE-009 — Offline Sync Requirements Synthesis

Status: `PHASE-4 REPOSITORY-DERIVED REQUIREMENTS / NO-CODE / ADR NOT READY`  
Date: 2026-09-18  
Decision level: Flutter consumer-mobile data, offline, local-work and reconciliation requirements; logical API boundary requirements  
Authority: `DEC-0023`–`DEC-0035` and the repository sources listed in Section 2

## 1. Purpose and decision posture

This document converts the approved product rules and Phase-4 working directions into one requirements framework for
Kavriva's Flutter consumer mobile surface. It covers a data-efficient bounded offline package, local user work,
reconciliation, cache eviction, recall/suspension, wrong-base delta handling, device loss/restore, account-light to
profile migration and the server/API boundary around the managed Supabase-centered working direction.

It is a repository-derived synthesis, not a new user decision. It does not authorize code, a prototype, an executable
technology spike, an account, a purchase, a subscription or a Phase-5 ADR. It does not select a Flutter storage library,
sync library, delta algorithm, API runtime, database schema, identity provider, object-storage transport, queue, cache,
signing mechanism or backup product.

The current decision posture is:

- Flutter is the approved consumer-mobile working direction (`DEC-0033`); Android is the first publication lane and iOS
  follows later (`DEC-0032`). Product/data/safety/provenance truth must remain portable and outside framework-bound
  presentation code.
- Offline use is risk-tiered, bounded and release-bound (`DEC-0024`). Offline availability is never itself application
  authorization, freshness proof or recall truth.
- Internal Operations is a browser product and its approval, publication, recall/suspension, role/policy and protected
  audit mutations are online-authoritative by default.
- The provider-neutral logical shape is canonical authority per domain, server/API mediation, separate current/history/
  protected-audit and object/media meanings, durable user operations, explicit reconciliation, rebuildable projections and
  tested cross-plane restore/export/exit (`DEC-0034`).
- A managed Supabase-centered physical backend is the reversible Phase-4 working direction (`DEC-0035`): managed
  PostgreSQL, Auth and private Storage are initial candidates, with a bounded server/API runtime between all clients and
  sensitive data. The runtime and physical decomposition remain replaceable until the Phase-5 ADR.

### 1.1 North-star acceptance rule

A future design is compatible with this synthesis only if it can demonstrate, with the same fixture and no-code evidence
schema for every retained candidate, that:

1. a selected motorcycle/task receives a complete, bounded, version- and capability-bound package rather than a library
   copy;
2. a wrong-base, partial, mixed, recalled, stale or incompatible package cannot become current application authority;
3. local user work is durable before it is reported as locally saved, and retries/reconnects resolve the same operation
   without silent loss or high-consequence last-write-wins;
4. cache pressure, device restore, clone suspicion and account/profile migration cannot erase required history or resurrect
   revoked, recalled, deleted or already-accepted truth;
5. negative authority (suspension/recall) has precedence over positive eligibility and remains honest during residual
   offline races and outages;
6. Flutter and browser clients cannot obtain general canonical database/object authority, and every sensitive effect is
   checked by the Kavriva server/API boundary; and
7. a nontechnical single owner and bounded AI workflows are not required to debug SQL, SSH, provider consoles, signing,
   build or incident state.

## 2. Repository authority used

The following files are the source set for this synthesis. Their status and boundaries remain authoritative; this document
does not silently promote a draft, external report or implementation suggestion into a product decision.

| Source | Contribution to DEBATE-009 |
|---|---|
| `00_CONTROL/CURRENT_STATE.md` | Current Phase-4 state, no-code boundary, Flutter/Supabase working directions, browser Internal Operations and owner-operability constraints. |
| `00_CONTROL/OPEN_QUESTIONS.md` | Account-light local value, migration conflict/failure, stale content, active-work revalidation and remaining strategy questions. |
| `00_CONTROL/DECISION_LOG.md` — `DEC-0035` | Managed Supabase-centered working direction, mandatory API mediation, independent recovery/audit/floor and reversal triggers. |
| `03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md` | Product invariants, version/publication/recall/audit requirements and explicit deferrals. |
| `DEBATE-002__OFFLINE_SAFETY_RECALL_CLIENT_COMPATIBILITY.md` | Risk-tiered bounded offline eligibility, package layers, recall/freshness, safe closure, compatibility and browser mutation rules. |
| `DEBATE-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md` | Immutable meaning, release/suspension generations, unknown/partial outcomes, anti-resurrection and emergency negative authority. |
| `DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md` | Distinct release authorities, closed release-meaning graph, compatibility, provenance, restore/revocation and AI-operability controls. |
| `DEBATE-006__COMMON_FIXTURE_AND_OPERATING_ASSUMPTIONS.md` | Equal comparison workload, device/network/data fixture, capability boundary, cost fixture and pass/hold/reject rule. |
| `DEBATE-007__DATA_BACKBONE_AND_LOGICAL_BOUNDARIES.md` | Logical data planes, API authority, durable user operations, package closure, cross-plane recovery, classification and AI runbooks. |
| `DEBATE-007__JUDGE_SYNTHESIS.md` | Corrections required for restore resurrection, closed packages, classification, audit custody, provider failure and exit. |
| `DEBATE-008__MANAGER_SYNTHESIS.md` | Reversible Supabase-centered direction and mandatory modular safeguards, including independent object/audit/floor recovery. |

Research mechanisms retained by the Judge (such as delta/cursor sync, outbox, idempotency, conflict policy and media
separation) are treated here only as requirements properties. Unsupported percentages, fixed production thresholds,
Flutter-Web assumptions and categorical provider conclusions remain excluded.

## 3. Product truth and invariants

These are product/architecture requirements, not implementation preferences.

| ID | Invariant | Required meaning |
|---|---|---|
| `OSR-INV-001` | Account-light first value | The user may obtain core local value before creating a profile. Language/unit preference and accessibility support are not profile prerequisites. A later profile adds controlled continuity; it does not retroactively make local value invalid. |
| `OSR-INV-002` | Fit precedes application | Motorcycle/model/year/variant and relevant modifications must be resolved before motorcycle-facing application guidance is treated as applicable. Nearby variants are never merged by guess. |
| `OSR-INV-003` | Teaching is not application authority | Teaching, history, evidence and provenance may remain readable while current physical application is held. A readable cached item is not thereby current, approved or safe to apply. |
| `OSR-INV-004` | Offline availability is not authorization | A package, local record, signature, encrypted cache or restored backup cannot create positive eligibility, approval, publication, entitlement or recall state. |
| `OSR-INV-005` | Data efficiency cannot remove safety closure | The default package excludes unrelated guides, motorcycles and unused media, but must include the compact warnings, checks, required media, completion states and task-specific safe-stop/recovery needed for every reachable physical state. |
| `OSR-INV-006` | Unknown critical state fails closed | Unknown, stale, disputed, missing, mixed, corrupt or incompatible critical dependencies inherit the highest applicable consequence. They cannot be silently treated as low-risk or not applicable. |
| `OSR-INV-007` | No silent overwrite | Current state, event/history, provenance, protected audit, local operation and object/media meanings remain distinct. High-consequence data never uses silent last-write-wins. |
| `OSR-INV-008` | Durable local work is not server success | A local pending operation can be safely persisted without claiming server acceptance. Server acceptance, conflict, hold, failure and outcome-unknown remain explicit. |
| `OSR-INV-009` | Negative authority wins | Known suspension/recall/revocation overrides an otherwise valid positive eligibility. A suspension is a negative stop authority; it cannot create replacement content or silently clear itself. |
| `OSR-INV-010` | Active work has safe closure | Started physical work retains task-specific guidance needed to stop, close or recover, even when normal application eligibility, entitlement, publication or lifecycle status changes. Safe recovery is not a hidden route into new application steps. |
| `OSR-INV-011` | Saved context is not physical proof | Resume restores context, not current confirmations. Revalidation of current physical/safety state is required at the reviewed boundary; “unchanged” user assertion does not bypass critical checks. |
| `OSR-INV-012` | History is not rewritten | Correction, recall, rollback, withdrawal, transfer, role revocation, deletion of one copy and migration do not silently erase prior use, provenance, attribution, disputes, independent evidence or the version actually used. |
| `OSR-INV-013` | Restore cannot resurrect | Old backups, clones, caches, deployments or provider snapshots cannot restore a lower release/suspension/security/deletion/accepted-operation generation or revive revoked, recalled, deleted or already-accepted state. |
| `OSR-INV-014` | Classification follows copies | Private, shared, community, official, draft, audit/security and derived/projection meanings propagate to packages, media, previews, analytics, exports, backups, AI/OCR results and caches. Derivation never grants official authority. |
| `OSR-INV-015` | API is the authority boundary | Flutter and browser clients do not hold general canonical database/object authority. Sensitive reads and every high-consequence mutation are evaluated by the server/API against current actor, session, action, object, scope, state, classification, consequence, independence and expected version/generation. |
| `OSR-INV-016` | Browser mutations are online-authoritative | Internal Operations cannot claim offline approval, publication, recall, role change or audit success. Lost responses are reconciled by operation identity; blind duplicate mutation is prohibited. |
| `OSR-INV-017` | AI and owner limits are real requirements | AI tasks must be bounded, least-privileged and independently reviewed. The nontechnical owner must not be required to perform SQL/SSH repair, interpret raw logs, repair builds/signing or act as sole high-consequence approver. |

## 4. Logical authority model

The following are logical boundaries. They do not require one server per row, premature microservices or a particular
physical database. A managed Supabase core may host multiple logical planes only if the API boundary, custody and recovery
properties remain independently demonstrable.

| Logical plane | May provide | May not provide |
|---|---|---|
| Canonical current domain authority | Current approved facts, user records, relationships, permissions and domain constraints. | It may not erase event/history/provenance or become a direct client store. |
| Release/eligibility/suspension authority | Exact approved release meaning, capability envelope, freshness/eligibility context, suspension/recall generations and negative precedence. | It may not be inferred from a local cache, push receipt, browser state or an old valid signature. |
| Flutter package/cache boundary | Complete scoped package, optional media, local work context and bounded offline use. | It may not approve, publish, recall, resolve canonical truth or act as a full database copy. |
| Durable local operation ledger | Pending local user operations, attachment dependencies, device/installation generation and reconciliation status. | It may not report server completion before authoritative result or be silently evicted while pending. |
| Domain history/provenance/evidence | Prior versions, sources, claims, disputes, withdrawals, correction lineage, guide version used and user interaction depth. | It may not be replaced by a mutable current row or an opaque KPI. |
| Protected audit and non-restorable floor | Ordered attributable evidence, release/suspension/security/deletion/accepted-operation/migration floors and recovery checkpoints. | It may not be the same unprotected mutable cache/log that a restoring administrator can rewrite. |
| Object/media boundary | Private user photos, evidence, documents, derived assets, package media, exports and release artifacts with digest, generation, classification, lineage and quarantine state. | A database backup alone may not be treated as object-byte backup; client/global storage credentials are prohibited. |
| Projections and convenience copies | Search, analytics, notifications, package-builder inputs and cache views that can be rebuilt or reconciled. | They cannot approve, publish, recall, authorize, silently repair or become the canonical source. |
| Account/profile binding | Association of local records and operations with a selected profile/account after explicit migration review. | It cannot silently merge accounts, change historical meaning, create current eligibility or destroy local-only value on failure. |
| Kavriva server/API boundary | Authentication/session and scoped authorization, package issuance, operation submission/status, reconciliation and high-consequence mutation authority. | It cannot delegate authority to a hidden button, provider console, browser cache, client SDK or provider-native default. |

## 5. Requirements for the bounded offline package

### 5.1 Package scope and layers

| ID | Requirement |
|---|---|
| `OSR-PKG-001` | The default package unit MUST be scoped to the selected motorcycle/model/year/variant, applicable modifications, selected guide/task, exact approved release, client capability contract and current/expected physical-work states. |
| `OSR-PKG-002` | The default package MUST exclude the full guide library, unrelated motorcycles, unrelated tasks and unused media. A client MUST NOT download the fixture's unrelated 2 GB catalog by default. |
| `OSR-PKG-003` | The required compact core MUST contain fit/version/status metadata, applicable text/steps, critical warnings, prerequisites/checks, expected outcomes, completion-state semantics, freshness/eligibility context and complete task-specific safe-stop/recovery closure. |
| `OSR-PKG-004` | Media MUST be layered: essential instructional media is included only when the guide cannot be safely understood without it; high-resolution images, galleries, video and nonessential teaching material are optional/on-demand and visibly sized before download. |
| `OSR-PKG-005` | Personal work context MUST retain selected motorcycle, guide/release version used, definite last step, notes, confirmations, selected evidence references and applicable attachment state without turning those records into current physical proof. |
| `OSR-PKG-006` | Package acceptance MUST be atomic. A partial, corrupt, mixed-release, missing-dependency, capability-incompatible or integrity-failing package MUST NOT enter current-use state. |
| `OSR-PKG-007` | The package manifest MUST bind exact package/release identity, base/target generation where relevant, applicability, dependency closure, client/schema capability, consequence classification, freshness/eligibility state, suspension/revocation generation, required/optional media, language/unit/accessibility meaning, digests and safe-closure coverage. |
| `OSR-PKG-008` | The package MUST close every reachable physical state and negative branch for offline-start eligibility, including stop, mismatch, insufficiency, uncertainty, interruption and recovery paths defined by reviewed guide content. The client MUST NOT invent a safe decision boundary. |
| `OSR-PKG-009` | Capability negotiation MUST occur before download/use. Unknown safety-critical fields, unmet minimum capability, unsupported client semantics or an old/dormant client outside the supported contract MUST fail closed for affected application. |
| `OSR-PKG-010` | A package MUST be accepted only with authenticated/completed integrity evidence and an anti-rollback/replay check against the latest available release/suspension floor. A valid old artifact is not current authority. |
| `OSR-PKG-011` | Downloads MUST support interruption, cancellation, retry and resumability at the transport/workflow level only if final acceptance still requires a complete verified package. An interrupted transfer is never an available package. |
| `OSR-PKG-012` | The user MUST see package size and contents before optional or large download. Cellular consent and network preference are policy inputs; exact commercial thresholds remain open. |
| `OSR-PKG-013` | Package replacement MUST budget temporary space for the existing package, the new package and verification/atomic replacement. The transfer size is not the peak installed/indexed size. |
| `OSR-PKG-014` | Account-light local use MUST remain valid where the bounded eligibility policy permits it. A profile/account MUST NOT be introduced solely as an unannounced prerequisite for package use, history access or safe recovery. |

### 5.2 Wrong-base delta and incremental update requirements

A delta is a data-efficiency optimization, not a second authority. The exact delta format, cursor mechanism and storage
library remain open.

| ID | Requirement |
|---|---|
| `OSR-DLT-001` | Every delta MUST declare the exact base package/release identity and generation it was computed from, the target identity/generation, applicability scope, client capability and complete dependency/closure manifest. |
| `OSR-DLT-002` | A delta MUST be rejected when the local base is absent, has a different identity/generation/digest, is already superseded/withdrawn/recalled, is only partial/mixed, is outside the capability window, or arrives out of order. “Closest” or “latest local” base matching is not valid. |
| `OSR-DLT-003` | Wrong-base, stale, corrupt, incompatible or incomplete delta MUST NOT be applied partially and MUST NOT be merged as if it were a full package. The resulting state is explicit `REJECTED_WRONG_BASE`/`FULL_PACKAGE_REQUIRED` or equivalent. |
| `OSR-DLT-004` | On delta rejection, the system MUST request or make available a complete compact package for the same scope. If no complete package can be established, normal application holds while teaching/history/evidence/safe recovery remain available where representable. |
| `OSR-DLT-005` | A failed delta MUST NOT evict a still-complete valid active-work package or its safe-stop/recovery closure. It also MUST NOT lower risk, freshness or dependency requirements to fit a smaller transfer. |
| `OSR-DLT-006` | Delta acceptance MUST be atomic and subject to the same release, suspension/revocation, capability, dependency, classification, integrity and anti-rollback checks as a full package. |
| `OSR-DLT-007` | A delta MUST NOT clear a recall/suspension, create positive eligibility, rewrite history, change classification or silently replace a disputed/high-consequence value. Those are authoritative reviewed events. |
| `OSR-DLT-008` | The no-code comparison evidence MUST show that the candidate can detect wrong-base, out-of-order, mixed and missing-delta cases and recover to a complete safe state without downloading the unrelated library. |

## 6. Requirements for local user operations and reconciliation

### 6.1 Durable local operation contract

| ID | Requirement |
|---|---|
| `OSR-OPS-001` | A local user operation MUST be durably recorded before the interface reports it as locally persisted. A transient UI state, optimistic widget state or unsent request is not local durability. |
| `OSR-OPS-002` | Each operation MUST have a stable operation identity, actor/account-light or profile context, installation/device generation, object/scope, action, payload fingerprint, schema/release meaning, expected current version/generation, creation/update time and attachment/dependency references. |
| `OSR-OPS-003` | Operations MUST preserve classification and privacy scope for private, shared, community, official, evidence and audit-related data. A later retry MUST NOT widen disclosure. |
| `OSR-OPS-004` | The local ledger MUST distinguish at least `PENDING`, `SUBMITTED`, `ACCEPTED`, `CONFLICT`, `HELD`, `FAILED`, `OUTCOME_UNKNOWN` and `RECONCILING` (or semantically equivalent inspectable states). A local-only accepted-looking row is not server acceptance. |
| `OSR-OPS-005` | Attachments and object dependencies MUST have their own explicit received/quarantined/validated/activated/failed/pending state. A partial upload or missing required object cannot produce a false completed operation. |
| `OSR-OPS-006` | Retrying the same operation identity MUST resolve to the same intended effect. Reusing an identity with a changed payload, scope, generation or meaning MUST be rejected and surfaced as a new operation requirement. |
| `OSR-OPS-007` | A lost response after submission MUST become `OUTCOME_UNKNOWN` until the server/API status lookup reconciles it. The user MUST NOT be asked to blindly repeat a high-consequence operation. |
| `OSR-OPS-008` | The operation ledger MUST survive ordinary cache cleanup while pending, conflicted, held or outcome-unknown. It may be removed only through a separate, inspectable retention/data-loss policy that does not claim server completion. |
| `OSR-OPS-009` | A local completion record MUST preserve whether the work is completed, partial/unresolved or safely stopped. Local persistence cannot coerce an unresolved state into success. |
| `OSR-OPS-010` | High-consequence official content, safety, provenance, ownership, entitlement, deletion, evidence dispute and recall-related operations MUST preserve both sides and use explicit conflict/hold/review. Silent last-write-wins is prohibited. |
| `OSR-OPS-011` | Low-consequence merge rules may be considered later only when their scope, fields, conflict semantics, audit meaning and rollback are explicit. A generic last-write-wins rule is not a baseline. |
| `OSR-OPS-012` | Local device loss may result in a truthful local-only loss/held state. The product MUST NOT invent server completion, uploaded evidence or current safety authority for data that never reached the server. |

### 6.2 Reconciliation boundaries and outcomes

| ID | Requirement |
|---|---|
| `OSR-SYN-001` | Authoritative reconciliation MUST be attempted at the defined product boundaries: app launch/foreground return, network return, before new physical application, before interrupted-work resume where required, at high-consequence decision boundaries, after restore/clone detection and during account/profile migration. Exact numeric timing remains open. |
| `OSR-SYN-002` | Push/background delivery is only a wake-up or re-check hint. A missed push, delayed job or process termination MUST NOT be treated as proof that no recall exists. Background execution is not a correctness requirement. |
| `OSR-SYN-003` | The product MUST distinguish `known_to_server`, `known_to_client` and `last_authoritatively_reconciled` (or equivalent). A successful check does not eliminate the residual race in which a recall commits immediately after it. |
| `OSR-SYN-004` | Reconciliation MUST compare current release, suspension/revocation, eligibility/freshness, client capability, applicability, operation result and relevant domain versions/generations. A client MUST NOT decide these from local wall time or cache age alone. |
| `OSR-SYN-005` | Reconciliation MUST be idempotent and operation-addressable. Lost responses are resolved by the original durable operation identity and server result; retries do not create a second effect. |
| `OSR-SYN-006` | Server-derived time and authoritative generations supply the audit/result meaning. Client wall-clock time is context only and cannot extend offline eligibility across reboot/restore. |
| `OSR-SYN-007` | A reconciliation result MUST expose accepted, rejected, conflict, held, failed, partial or outcome-unknown state with owner/next action where applicable. A network error is not silently labeled a recall, success or failure. |
| `OSR-SYN-008` | Cross-plane effects spanning current state, object bytes, protected audit, release/suspension state or outbox/projection MUST use explicit `PREPARED`, `COMMITTED`, `PARTIAL`, `FAILED`, `OUTCOME_UNKNOWN`, `RECONCILING` and `HELD` semantics (or equivalent). |
| `OSR-SYN-009` | Reconciliation MUST preserve history/provenance/audit and classification while updating current state. Projections, search, analytics, notifications and package builders are retryable consumers, not authority. |
| `OSR-SYN-010` | If the server/API, identity, audit, object or provider boundary is unavailable, the product MUST enter an owner-readable hold/unavailable/unknown state and preserve safe local context. It MUST NOT require owner SQL, SSH or provider-console repair. |

## 7. Requirements for cache limits, eviction and storage pressure

Cache policy is a safety/data-lifecycle policy, not merely a storage optimization.

| ID | Requirement |
|---|---|
| `OSR-CCH-001` | The cache MUST distinguish active-work safety/application core, task safe-stop/recovery closure, optional enhanced media, inactive complete packages, package-transfer temporary data, local pending operations, user history/evidence and user photos/private notes. User-created history/photos are not silently counted as disposable package cache. |
| `OSR-CCH-002` | Active-work application core and complete task-specific safe-stop/recovery content MUST be pinned while the work is open. They MUST NOT be evicted merely because the normal cache budget is full. |
| `OSR-CCH-003` | Pending, conflicted, held or outcome-unknown operations and required attachment dependencies MUST be protected from routine cache eviction. |
| `OSR-CCH-004` | When space is constrained, optional enhanced media is the first normal cleanup candidate, followed by unused/re-fetchable inactive package material according to explicit user-visible policy. Required closure MUST never be made incomplete to meet a byte budget. |
| `OSR-CCH-005` | Cache cleanup MUST be user-visible, explain what will be removed, preserve classification and history meaning, and record any package/operation that becomes unavailable or requires re-fetch/reconciliation. Silent destructive cleanup is prohibited. |
| `OSR-CCH-006` | If a complete package cannot be retained or revalidated after storage failure, the package becomes ineligible for normal application. The product presents the safest available stop/preserve-state/support path and never marks work complete. |
| `OSR-CCH-007` | A package MUST NOT be split, down-scoped or evicted into a partial/mixed state and then used as “data efficient.” A small incomplete package is a safety failure, not a successful optimization. |
| `OSR-CCH-008` | The cache MUST retain enough identity/generation/digest and historical version context to explain what was used, what is currently held and why a re-fetch/re-check is required. This metadata is not positive authority. |
| `OSR-CCH-009` | Cache and backup restore MUST not reactivate previously invalidated visibility, entitlement, deletion, withdrawal or suspension. Copy invalidation follows classification and protected deletion/withdrawal floors. |
| `OSR-CCH-010` | The no-code comparison MUST cover storage pressure, process termination, interrupted replacement, old+new temporary-space needs, optional-media cleanup, active-work pinning and recovery from failed cleanup. |

## 8. Recall, suspension, freshness and active-work requirements

| ID | Requirement |
|---|---|
| `OSR-RCL-001` | A known recalled/suspended/invalidated content or dependency MUST block normal new and continuing physical application for its affected scope. Known negative authority overrides local positive eligibility. |
| `OSR-RCL-002` | Suspension is a narrow negative authority: it may restrict future application, identify scope/reason/severity and start a recall case, but it cannot author replacement technical content, grant positive eligibility or silently clear another suspension. |
| `OSR-RCL-003` | Emergency suspension MUST be sufficiently independent from the normal publication/identity/data path to survive the named failure domains; a separate button or UI is not evidence of independence. Exact topology, quorum and numeric objectives remain open. |
| `OSR-RCL-004` | Publication and suspension MUST use a fenced precedence/generation rule. A publish prepared against an older suspension/revocation generation is rejected; an older/in-flight publish cannot clear a newer suspension. Generations MUST NOT move backward through restore/failover. |
| `OSR-RCL-005` | A fully offline device cannot learn a brand-new recall immediately. Bounded validity, re-check boundaries and explicit residual risk limit exposure; the product MUST NOT claim universal instant recall. |
| `OSR-RCL-006` | On connectivity/foreground return, current release, eligibility, recall/suspension, capability and applicability MUST reconcile before further physical progression. Material change routes to remap; mismatch routes to recovery; only successful validation reopens. |
| `OSR-RCL-007` | When freshness expires or authoritative state cannot be established, the next physical progression is held. Teaching, history, evidence capture and task-specific safe stop/recovery remain available where safely representable. Numeric validity windows are not invented here. |
| `OSR-RCL-008` | Resume MUST restore motorcycle, guide/release version, last definite step, notes/photos and context, but saved confirmations MUST not be treated as current physical proof. Required revalidation remains open until the reviewed guide boundary succeeds. |
| `OSR-RCL-009` | A material guide change MUST stop old continuation and require current physical-state capture/remapping. The product MUST NOT reverse or infer a physical action without a verified safe mapping. |
| `OSR-RCL-010` | Task-specific safe-stop/closure/recovery material MUST remain reachable when normal application closes due to recall, entitlement/lifecycle change, stale/unknown state or an outage. Recovery access MUST NOT become a hidden bypass into unrelated/new steps. |
| `OSR-RCL-011` | Affected-user interaction depth MUST remain available for proportional reach-back: view, guide open, active step, evidence submission and completion record are distinct impacts. Reach-back and acknowledgment channels/SLA remain open. |
| `OSR-RCL-012` | A known server release, known client release, last reconciled state, provider unavailable state, suspension authority unknown state and known suspended state MUST remain distinguishable to the user/operator. Infrastructure failure is not silently displayed as a recall, and unknown critical authority is not permission. |

## 9. Device loss, reboot, restore and anti-resurrection requirements

| ID | Requirement |
|---|---|
| `OSR-RST-001` | A wall-clock rollback/forward, reboot, clone suspicion or backup restore MUST NOT extend eligibility by local time alone. Same-boot monotonic duration may support reasoning but is not cross-reboot/restore proof. |
| `OSR-RST-002` | Restored content/cache is treated as derived reference until current release, capability, applicability, freshness and suspension/revocation authority are re-established. Restored history retains the guide/release version historically used. |
| `OSR-RST-003` | A restored installation MUST enter explicit `RESTORE_QUARANTINE` (or equivalent) whenever trust context, device/installation generation, identity binding, time evidence, package integrity or current negative floor is uncertain. |
| `OSR-RST-004` | Exit from restore quarantine MUST reconcile current state, domain history, protected audit checkpoint, identity/policy/configuration, object manifest, package/release graph, pending-operation ledger, deletion/withdrawal tombstones and release/suspension/security/accepted-operation/migration floors. |
| `OSR-RST-005` | The non-restorable floor MUST remain sufficiently independent from the ordinary restored snapshot. If the floor or protected evidence is unavailable, authoritative cutover and high-consequence positive use remain held. |
| `OSR-RST-006` | An operation copied from backup MUST be checked against the accepted-operation ledger and its original installation/device generation. Already accepted effects MUST not replay; changed-payload reuse MUST reject; unresolved effects remain outcome-unknown/held. |
| `OSR-RST-007` | A restored/cloned local profile binding that conflicts with current account/device/profile identity MUST be quarantined for explicit migration/recovery review. No silent merge or wrong-account upload is permitted. |
| `OSR-RST-008` | Device loss/replacement flows MUST distinguish server-accepted records, synchronized history, local-only pending work, local-only media and unrecoverable local state. They MUST not promise recovery of data that never left the lost device. |
| `OSR-RST-009` | Backup/restore MUST cover logical records, object bytes, protected audit/floor, policy/identity mapping, package artifacts and pending operations as separately inventoried planes. Database backup alone is not object or audit recovery proof. |
| `OSR-RST-010` | Every backup/restore/export/exit package MUST carry a coordinated consistency manifest (or explicitly partial status) with schema/config/migration versions, canonical sequences, object generations/digests/classification, audit checkpoint, security/revocation floor, operation/outbox cursor, tombstones and key references without raw secret export. |
| `OSR-RST-011` | Restore/failover MUST preserve newer valid user data through forward recovery when binary/schema rollback would lose it. A safe older artifact is not a license to discard later data or revive revoked truth. |
| `OSR-RST-012` | Clean-room import outside the normal provider account MUST be part of later exit evidence. A successful backup job, PITR action, file export or provider restore alone is not recovery/exit proof. |

## 10. Account-light to profile migration requirements

These requirements carry the approved local-first and migration semantics into the data/sync boundary without deciding an
identity provider or final migration UI.

| ID | Requirement |
|---|---|
| `OSR-MIG-001` | Account-light local records, history, evidence references, notes, preferences and eligible task context MUST remain usable before profile creation, subject to the same bounded safety rules. |
| `OSR-MIG-002` | Migration MUST begin with an inspectable scope preview showing source/local categories, target profile, dates, covered periods, guide/release versions, private/shared/community/official classification, pending operations, attachments, conflicts and exclusions. |
| `OSR-MIG-003` | Migration MUST use stable local identities, installation/device generation and a durable migration operation identity. It MUST be idempotent and must not duplicate operations on retry. |
| `OSR-MIG-004` | Migration MUST preserve source/date/difference/provenance context and MUST NOT silently choose a winner for duplicate, conflicting, disputed, private, shared or community data. Conflicts require visible review/hold. |
| `OSR-MIG-005` | Profile association MUST NOT change the historical meaning of a completed action, the guide/release version used, the evidence attribution or the status of a partial/unresolved/safely-stopped outcome. |
| `OSR-MIG-006` | A migration MUST not grant new technical truth, current eligibility, entitlement or publication authority merely because a profile exists. Profile state and application authority remain separate. |
| `OSR-MIG-007` | Wrong-account, stolen-device, clone, revoked-session and profile-binding conflicts MUST quarantine affected data/operations before upload or merge. Unaffected local data remains usable where safe. |
| `OSR-MIG-008` | Cancellation, network failure, rejected authorization, conflict or partial migration MUST leave the source local data recoverable and usable. A partial target state MUST be labeled partial/incomplete, never success. |
| `OSR-MIG-009` | A successful migration MUST be evidenced per object/operation/classification and must reconcile local pending work with the server operation ledger before local cleanup or duplicate suppression. |
| `OSR-MIG-010` | Local-only private notes/photos and official/community/provenance material MUST retain separate disclosure, retention and deletion semantics during migration. Exported copies cannot be remotely withdrawn by deleting the source. |
| `OSR-MIG-011` | Migration rollback/correction MUST be non-destructive and auditable. It may repair association or remove a mistaken target copy only under explicit policy; it MUST NOT erase independent evidence, audit or required correction history. |
| `OSR-MIG-012` | A later profile migration MUST not become a hidden prerequisite for safe recovery of already-started physical work. If migration is held, task-specific local closure remains available when present and valid. |

## 11. Supabase-centered server/API boundary requirements

The following expresses `DEC-0035` as boundary requirements. It does not select Supabase SDKs, Edge Functions, schema,
RLS policy syntax or a final deployment topology.

| ID | Requirement |
|---|---|
| `OSR-API-001` | Flutter and browser clients MUST use a Kavriva server/API contract for sensitive reads and every mutation that affects canonical state, user ownership, official content, eligibility, publication, recall/suspension, roles, protected audit, migration or deletion. |
| `OSR-API-002` | The API MUST authorize at action time using current actor/session, action, exact object/scope, workflow state, classification, consequence, independence/separation-of-duties and expected version/generation. Client/UI role state, cached permissions and object IDs are not permission. |
| `OSR-API-003` | Package requests MUST return a scoped, versioned, capability-bound manifest for the selected motorcycle/task and must not expose a general database/object query surface to Flutter. |
| `OSR-API-004` | Local operation submission MUST bind operation identity, actor/device/profile context, payload fingerprint, expected versions/generations, classification, attachment dependencies and intended effect. Changed-payload reuse MUST fail. |
| `OSR-API-005` | Each authoritative request MUST have an inspectable server result and independent status lookup: accepted, rejected, conflict, held, failed, partial or outcome-unknown. Server time/result supplies audit meaning; client timeout does not. |
| `OSR-API-006` | RLS and Storage policies are mandatory defense in depth but MUST NOT be the sole approval, publication, recall, provenance, protected-audit or separation-of-duties authority. Provider defaults cannot replace the Kavriva contract. |
| `OSR-API-007` | `service_role` and other privileged secrets MUST remain server-only. They MUST NOT enter Flutter/browser bundles, repositories, logs, exports or ordinary AI task contexts. |
| `OSR-API-008` | Supabase Studio/provider administration MUST remain distinct from the Kavriva browser Internal Operations product. Studio/provider-console access MUST NOT become an undocumented approve/publish/recall/role/audit bypass. |
| `OSR-API-009` | API, database/current state, object bytes, protected audit and non-restorable negative/deletion/accepted-operation floors MUST have explicit custody/recovery relationships. Database backup MUST NOT be represented as Storage-object or audit recovery. |
| `OSR-API-010` | Provider/account/billing/region/identity/DNS/key/support failures MUST produce owner-readable `HELD`, `OUTCOME_UNKNOWN`, `SERVICE_UNAVAILABLE`, `BILLING_HELD` or equivalent states. Normal positive writes/publication stop safely; the owner is not the recovery mechanism. |
| `OSR-API-011` | Direct privileged paths (admin SDK, database functions, migrations, restore, object callbacks, bulk export, support/break-glass and provider-console paths) MUST be included in the authorization and negative-test matrix. Hidden paths are not out of scope. |
| `OSR-API-012` | Object operations MUST use scoped, expiring, digest/generation-bound capabilities or an equivalent server-mediated boundary. Global storage credentials and unbounded object prefixes are prohibited. |
| `OSR-API-013` | API release/configuration/migration changes MUST participate in the closed release-meaning and compatibility graph with Flutter capability, content/package closure, suspension/revocation generation and schema/data state. |
| `OSR-API-014` | Provider-native convenience features MUST not introduce silent last-write-wins, direct content publication, unbounded cache authority, unreviewed recall clearing or a non-exportable canonical dependency. |
| `OSR-API-015` | Supabase-specific coupling MUST remain reversible: stable logical IDs, inspectable logical export, object/audit/floor manifests and clean-room import evidence must be possible before production authority is accepted. |

## 12. Minimum conceptual state contracts

These state names are a requirements vocabulary, not a final schema or UI design.

### 12.1 Package lifecycle

`DISCOVERED → DOWNLOADING → VERIFYING → ACCEPTED_COMPLETE → AVAILABLE_WITHIN_POLICY`

Possible guarded states include `FULL_PACKAGE_REQUIRED`, `REJECTED_WRONG_BASE`, `INCOMPATIBLE`, `EXPIRED`, `SUSPENDED`,
`RECALLED`, `PARTIAL`, `CORRUPT`, `EVICTED`, `HELD` and `RECOVERY_ONLY`. A package in any partial/mixed/corrupt state is
not current application authority.

### 12.2 Local operation lifecycle

`LOCAL_DURABLE → PENDING → SUBMITTED → ACCEPTED | CONFLICT | HELD | FAILED | OUTCOME_UNKNOWN → RECONCILING`

Reconciliation may preserve `PARTIAL` or return to a corrected `PENDING` state. No transition from local persistence to
server acceptance may be implied by a successful local write, optimistic UI or network request dispatch.

### 12.3 Release/suspension precedence

Positive eligibility is conditional on current release, capability, applicability, freshness and the protected
suspension/revocation generation. A newer negative generation dominates an older positive state. Generation rollback is a
fatal authority/recovery error, not a valid rollback path.

### 12.4 Restore lifecycle

`RESTORED → RESTORE_QUARANTINE → RECONCILING → ACTIVE_WITH_CURRENT_AUTHORITY | HELD | RECOVERY_ONLY`

`ACTIVE_WITH_CURRENT_AUTHORITY` is allowed only after current floors, audit continuity, identity/policy, object/package
manifests and pending operations reconcile. A restored snapshot alone cannot enter that state.

### 12.5 Migration lifecycle

`LOCAL_ONLY → SCOPE_PREVIEW → READY | CONFLICT | HELD → SUBMITTED → PARTIAL | OUTCOME_UNKNOWN | ACCEPTED → RECONCILED`

The exact user interaction is open, but source data must remain usable until accepted/reconciled migration evidence exists.

## 13. Frozen workload fixture for equal evaluation

These constants are the approved DEBATE-006 comparison fixture, not final production/commercial limits. A fixture revision
must be recorded once and applied equally to every candidate; no candidate may use easier conditions.

### 13.1 Product, release and scale

| Dimension | Frozen comparison condition |
|---|---|
| Consumer surfaces | Android and iOS phone-focused consumer apps; browser-based Internal Operations. |
| Framework direction | Flutter working direction; data/safety/provenance remains framework-portable. |
| Publication order | Android first, iOS later; simultaneous launch is not assumed. |
| Evaluation horizon | First release plus 24 months maintenance. |
| Planned cadence | Four release windows per year plus safety-critical correction when required; timing remains evidence-gated. |
| MAU tiers | 1,000 launch baseline; 10,000 growth check; 50,000 stress check. |
| Monthly workload per MAU | Two compact task-package transfers; optional-media use by 10% at 100 MB average transfer; 0.5 new user photos at 3 MB average upload. |
| Storage horizon | 24 months for comparison only; not a final legal retention promise. Storage and outbound transfer are shown separately. |

### 13.2 Device and network/interruption profiles

| Dimension | Frozen comparison condition |
|---|---|
| Constrained Android | Android 10/API 29, 64-bit, 4 GB RAM, 64 GB storage, 2 GB free profile. |
| Main Android | Android 13 or newer, 6 GB RAM, 128 GB storage profile. |
| Oldest supported iPhone | iOS 16.4-capable oldest-end profile. |
| Current iPhone | Current generally available iOS on a standard non-Pro device at the release window. |
| Stable Wi-Fi | 50 Mbps download, ordinary latency. |
| Ordinary cellular | 10 Mbps download. |
| Constrained cellular | 1 Mbps, 300 ms latency, 5% packet loss. |
| Interruption | Connection loss during transfer and sync; app background/lock/incoming call/process termination/restart. |
| Offline/time/restore | Fully offline for 72 hours; device clock change; backup restore before reconnection. |
| Evidence bar | Real devices, VoiceOver/TalkBack and qualified safety/content review are required later; simulators/AI claims do not substitute. |

### 13.3 Package and local-data fixture

| Dataset/limit | Normal or stress fixture |
|---|---:|
| Selected package | One selected motorcycle/model year/resolved variant; one active maintenance task. |
| Compact transfer | Required text/warnings/diagrams/complete safe closure target maximum 12 MB. |
| Optional media | Separate high-resolution images/video up to 150 MB; never selected silently. |
| Unrelated catalog | 2 GB present solely to prove it is not downloaded by default. |
| Default content-cache budget | 250 MB, excluding user-created history/photos. |
| Cellular confirmation | Downloads above 25 MB require explicit user choice; safety core cannot be split to evade this. |
| Local records | 3 motorcycles / 250 history-evidence records / 50 user photos at 3 MB / 100 private notes. |
| Stress local records | 10 motorcycles / 2,000 history-evidence records / 500 photos at 3 MB / 1,000 notes. |
| Pending operations | 20 normal / 200 stress. |
| Local/profile conflicts | 3 normal / 30 stress. |
| Seeded failure cases | One duplicate operation, partial upload, corrupt package, interrupted database change, source correction, content withdrawal and safety recall. |

The transfer, cache and media numbers above are comparison constants. They do not approve final package-size classes,
cellular policy, storage quota, freshness window, retention period or commercial limit.

## 14. Equal no-code scenario set

The following scenarios apply the same fixture and evidence schema to every retained mobile/backend candidate. They extend
the DEBATE-002/003/005 acceptance scenarios into the DEBATE-009 data/sync boundary. They are documentary walkthroughs,
not authorization for executable tests or prototypes.

| ID | Scenario | Required allow/deny/hold result and evidence |
|---|---|---|
| `EQ-01` | Scoped package against the 2 GB unrelated catalog | Only selected motorcycle/task compact package is requested/accepted; required closure is present; unrelated catalog is not downloaded. Manifest, size and dependency evidence are shown. |
| `EQ-02` | Interrupted/partial/corrupt package | Transfer may resume, but partial/corrupt data never enters use; atomic verification either accepts one complete package or leaves the prior safe state/hold. |
| `EQ-03` | Wrong-base, out-of-order or missing delta | Delta is rejected with explicit wrong-base/full-package-required state; no closest-base merge, partial application or silent downgrade; complete compact fallback is attempted. |
| `EQ-04` | 72-hour fully offline use | Only the task/risk policy permits bounded use; version/freshness/eligibility context is visible; no new recall knowledge is invented; high-consequence/unknown boundaries hold as governed. |
| `EQ-05` | Recall issued while device is offline and push is missed | Device retains explicit residual risk; on foreground/network return, authoritative suspension wins before further progression; history/safe recovery remain available. Push is not proof. |
| `EQ-06` | Foreground/network return during sync | Current release, capability, suspension/revocation and operation status reconcile; duplicate retry resolves to the original operation identity; server result/time are authoritative. |
| `EQ-07` | Freshness expires during active physical work | Ordinary next progression holds at the reviewed safe boundary; task-specific stop/closure/recovery remains reachable; outcome is partial/unresolved/safely stopped when applicable. |
| `EQ-08` | Material guide change during active work | Old continuation stops; current physical state is captured and remapped only through a safe reviewed mapping; no client-invented reversal or step. |
| `EQ-09` | Device-time rollback, reboot and backup restore | Local clock/restore cannot extend authority; restored package enters quarantine/recheck; history keeps the version used; old backup cannot reduce negative generations. |
| `EQ-10` | Old client receives a new safety-critical semantic | Capability mismatch fails closed for affected application; teaching/history/safe recovery remain only if the client can represent them without hiding meaning; store prompt is not enforcement proof. |
| `EQ-11` | Duplicate operation and lost response | Stable operation identity produces one effect; timeout shows outcome unknown and status lookup path; blind duplicate approval/publication/recall is denied. |
| `EQ-12` | High-consequence conflict vs low-consequence merge | High-consequence data preserves both sides and enters visible conflict/hold/review; any low-risk merge is bounded, attributable and reversible; no universal last-write-wins. |
| `EQ-13` | Cache pressure while active work and pending operations exist | Optional media/unused re-fetchable material is eligible first; active closure, pending operations and required attachments remain; cleanup is visible and non-success cannot be hidden. |
| `EQ-14` | Device loss/replacement with local-only and server-accepted work | Recovery distinguishes server-accepted, synchronized, pending/local-only, media and lost state; it never invents upload/completion or current eligibility. |
| `EQ-15` | Account-light to profile migration with duplicate, private and conflicting records | Scope preview, stable IDs, explicit conflicts, classification and idempotent operation are evidenced; failure/cancel leaves local value usable; partial target is not success. |
| `EQ-16` | Server/API/provider outage or billing hold | Sensitive mutations hold or become outcome-unknown with owner-readable next action; no provider-console or owner-SQL repair path; safe local/reference/recovery behavior remains bounded. |
| `EQ-17` | Publication vs overlapping emergency suspension | Publish is conditional on current suspension generation; newer suspension wins; old/in-flight publish cannot clear it; operation identity/status and protected audit evidence are present. |
| `EQ-18` | Cross-plane restore/export/clean-room import | Current records, object bytes, protected audit, identity/policy, package graph, operations and negative floor reconcile under one consistency manifest; partial import is labeled; exit is not claimed from a successful export alone. |

Each scenario must state: authoritative state transition; user/operator explanation; generated evidence; affected offline,
installed and active-work populations; recovery/reconciliation owner; residual risk; and explicit `PASS`, `HELD` or `REJECT`
result. A green build, valid signature, provider backup, API response, push receipt or stopped rollout is not by itself a
scenario pass.

## 15. Equal pass / hold / reject rules

The DEBATE-006 rule applies without weighted-score escape:

- `PASS` requires credible official/product evidence, a complete Kavriva walkthrough against the frozen fixture, explicit
  visible states and a later acceptance plan for real-device, accessibility, safety, restore and exit evidence.
- `HELD` is required when critical evidence, owner capacity, real-device access, numeric cost, recovery/exit proof,
  compatibility evidence, independent audit/floor, provider-failure behavior or qualified safety/content review is missing.
- `REJECT` applies when the candidate requires an unsafe bypass, unbounded cost/dependency, lost user truth, unsupported
  critical path with no owned fallback, or one of the hard-fail properties below.

### 15.1 Mandatory hold rules

The affected capability remains visibly `HELD` when any of the following is unresolved:

1. a compact package does not close every reachable physical state and safe-stop/recovery branch;
2. wrong-base delta cannot fall back to a complete package without silent merge, replay or downgrade;
3. active-work closure or pending operations can be evicted by routine cache cleanup;
4. local writes lack stable operation identity, idempotent retry, conflict state or outcome-unknown reconciliation;
5. old restore/clone can enter authority before current release/suspension/deletion/accepted-operation floors reconcile;
6. account-light migration can silently lose, duplicate, merge or wrong-account-upload local data;
7. old clients cannot fail closed on unknown safety semantics;
8. recall/suspension relies solely on push, background execution, local time or a shared unexamined failure domain;
9. protected audit/fallback evidence is unavailable for a high-consequence effect;
10. direct provider-console, database, object or privileged service paths bypass the Kavriva API contract;
11. cross-plane object/audit/identity/package recovery is described only by database backup/export success;
12. provider/account/billing/region failure requires the nontechnical owner to debug or repair infrastructure;
13. exact cost, overage/cap behavior or exit path is not owner-readable and bounded;
14. AI cannot perform routine operations through minimum-sufficient, least-privileged, dry-run/idempotent runbooks with
    independent validation.

### 15.2 Hard rejection conditions

Reject a design or affected capability if it requires:

- full-library default download or partial/mixed package application;
- local cache, browser state, push receipt, client clock, provider log or signature as current authority;
- silent high-consequence last-write-wins;
- a direct general client connection to canonical database/object storage;
- restore/rollback that resurrects revoked/recalled/deleted/accepted state or discards newer valid data;
- migration that silently overwrites source, profile, private/shared/community classification or provenance;
- an API boundary that leaks service-role/global object credentials or leaves privileged bypass paths untested;
- a provider-specific feature that is the only canonical, non-exportable source of truth;
- uncapped/unexplained recurring cost, non-portable dependency or owner repair obligation;
- AI as sole approver, unrestricted superuser, legal/billing owner or recovery authority for irreversible/high-consequence work.

No convenience, popularity, framework familiarity, managed-service headline or AI speed claim can cancel a safety,
continuity, accessibility, release-integrity, recovery or operability hold.

## 16. AI-operability and ownership conditions

The project is AI-operated by a nontechnical product/decision owner (`DEC-0028`–`DEC-0030`). The following are acceptance
conditions for later implementation planning, not permission to implement now.

| ID | Condition |
|---|---|
| `OSR-AI-001` | Each task must have a bounded context pack naming allowed/forbidden scope, relevant contract/fixture, dependencies, expected states, evidence outputs, stop conditions and rollback/forward-recovery path. A fresh implementation AI must not read the whole repository to discover the boundary. |
| `OSR-AI-002` | Product truth, package manifests, operation ledgers, migration states, release/suspension generations and recovery manifests MUST use portable, inspectable formats with stable IDs and explicit relationships. |
| `OSR-AI-003` | Implementation, independent review and validation are separate evidence-producing tasks. AI-generated code, a green check or a manager assertion cannot self-prove offline safety, recovery, accessibility or content correctness. |
| `OSR-AI-004` | Every routine operation needs a minimum-sufficient runbook: allowed action, forbidden action, least-privilege credential class, dry run, idempotent identity, stop condition, evidence capture, forward recovery and plain-language owner output. |
| `OSR-AI-005` | AI MUST NOT receive owner/billing authority, unrestricted superuser/SQL/SSH, `service_role`, global object credentials, signing/root recovery keys or a sole high-consequence approval/recall/migration/restore role. |
| `OSR-AI-006` | AI operations must expose provider/account/billing/region/key/identity failures as `HELD`, `UNKNOWN`, `UNAVAILABLE` or equivalent, with a safe next action. “Try a manual fix” is not a recovery plan for the owner. |
| `OSR-AI-007` | Flutter platform exceptions, generated registrants, Android/iOS build/signing effects and provider coupling must be attributable, reproducible, reviewable and exportable through the project task/evidence graph. |
| `OSR-AI-008` | Dependency/toolchain changes must identify affected package, native/platform, API, schema, release-meaning, restore, offline and accessibility contracts, plus required revalidation. |
| `OSR-AI-009` | If trustworthy AI evidence, independent review, real device/accessibility access, qualified safety/content review or owner-readable cost/recovery evidence is unavailable, the result is `HELD`, not assumed correct. |
| `OSR-AI-010` | The owner must not be required to debug Flutter/native builds, sign artifacts, administer a database, read raw logs, repair a provider outage or infer architecture from an AI failure. |

## 17. Non-goals and deliberately open decisions

### 17.1 Explicit non-goals

This synthesis does not:

- create application code, a prototype, a proof-of-concept, a benchmark or an executable sync spike;
- select a Flutter local database/package library, delta format, CRDT, queue, broker, API framework, schema or endpoint;
- select Supabase Edge Functions versus another server runtime, or turn Supabase Studio into the product admin surface;
- assert a final database, object-storage, identity, backup, audit, monitoring, CDN, notification or AI provider;
- approve a Supabase account, region, plan, Pro/PITR purchase, subscription, adjunct provider or production claim;
- set final package-size, cache, cellular, freshness, retention, RTO/RPO, support-window or reach-back numbers;
- treat 12 MB/150 MB/250 MB/25 MB, 72 hours, MAU tiers or 24 months as commercial/product promises;
- make browser Internal Operations offline mutations a baseline requirement;
- enable OTA/native runtime updates or background execution as a correctness dependency;
- make profile creation a prerequisite for account-light local value or safe recovery;
- authorize automatic AI publication, recall, role, migration, delete, restore or safety authority;
- advance Gate 4 → 5 or create the Phase-5 ADR.

### 17.2 Narrow decisions still open

Later strategy/ADR work must close, with evidence rather than assumption:

1. consequence/risk taxonomy and which categories are always-online versus bounded offline;
2. numeric freshness/eligibility windows, device-time/restore policy and minimum client/capability window;
3. exact package/cache/media limits, eviction retention and active-work closure policy;
4. exact delta/cursor protocol and server package issuance semantics;
5. operation conflict classes, low-risk merge boundaries and high-consequence resolution roles;
6. account-light/profile identity, wrong-account recovery, migration consent and private/shared/community transfer policy;
7. recall/suspension scope lattice, independence/failure domains, reach-back channels and acknowledgment objectives;
8. API runtime, identity/authorization implementation, RLS/Storage policy details and privileged-path custody;
9. protected audit/floor physical custody, object backup/export, restore/exit drills and clean-room cutover;
10. region/legal/data-transfer, retention/deletion/export and provider billing/overage controls;
11. actual Android/iOS device, accessibility, store, signing, build and qualified safety/content evidence;
12. framework-exit criteria if Flutter cannot close a mandatory requirement safely.

## 18. Traceability summary and handoff

| Concern requested for DEBATE-009 | Primary requirement sections | Repository authority |
|---|---|---|
| Data-efficient bounded offline package | Sections 5 and 13 | `DEC-0023`, `DEBATE-002`, `DEBATE-006`, `DEBATE-007`, `DEC-0034` |
| Local user operations | Section 6.1 | `DEBATE-007` D7-05, `DEBATE-006`, `OPEN_QUESTIONS` migration/restore answers |
| Sync/reconcile | Section 6.2 | `DEBATE-002`, `DEBATE-003`, `DEBATE-007` D7-03/D7-05/D7-14 |
| Cache eviction | Section 7 | `DEBATE-002` data controls, `DEBATE-006` cache fixture, `DEBATE-007` D7-12/Judge corrections |
| Recall/suspension | Section 8 | `DEBATE-002`, `DEBATE-003`, `DEBATE-005`, `DEC-0024`/`DEC-0025` |
| Wrong-base delta | Section 5.2 and `EQ-03` | `DEBATE-007` D7-12, Judge correction, `DEBATE-006` package/interruption fixture |
| Device loss/restore | Section 9 | `DEBATE-002`, `DEBATE-003`, `DEBATE-007` D7-10/D7-11/D7-15, `DEBATE-008` safeguards |
| Account-light → profile migration | Section 10 | `DEBATE-002`, `DEBATE-007` local-work/identity boundaries, `OPEN_QUESTIONS` Q-0052/Q-0060, `DEBATE-006` conflict fixture |
| Supabase API boundary | Section 11 | `DEC-0035`, `DEBATE-008`, `DEBATE-007` D7-02/D7-16/D7-17 |
| Product truth and invariants | Section 3 | `INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS`, `DEBATE-002`, `OPEN_QUESTIONS` |
| Equal workload/scenarios | Sections 13–15 | `DEBATE-006`, `DEBATE-002`/`003`/`005` no-code scenarios |
| AI-operability | Section 16 | `DEC-0028`/`0029`, `DEBATE-006`, `DEBATE-007`, `DEBATE-008` |

The next authorized work is documentary Phase-4/Phase-5 preparation: convert these requirements into candidate-neutral
contracts, traceability and evidence plans, then evaluate the physical/API/storage/recovery candidates against the same
fixture. No implementation, purchase or gate transition follows from this synthesis alone.

