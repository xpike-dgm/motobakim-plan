# ADR-015 — AI-Safe Module, Contract, Repository Topology and Project Graph

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

`DEC-0028` (with `00_CONTROL/PROJECT_SCOPE_ADDENDUM_AI_NATIVE_EXECUTION_SYSTEM.md`) requires the project to be
built as a contract-governed, task-addressable system with an Obsidian-compatible relationship graph, minimum
sufficient task context packs, no-code task simulation, bidirectional closure evidence and multi-AI design
consistency — and Gate 5 -> 6 explicitly demands the module/contract/topology, graph metadata/identity and
dependency-direction decisions as APPROVED/LOCKED ADR scope. This capstone ADR locks that execution architecture
at strategy level on top of ADR-001–ADR-014, whose boundaries it governs. Mechanism design (context router,
validation harness, CI gates, physical vault) belongs to Phase 7–8; this ADR fixes the shape those mechanisms
must implement, so Phase 6 planning cannot silently deform it.

## Decision Drivers

- A fresh AI must complete the next `TASK-xxx` without reading the whole project and without breaking it.
- "All tasks DONE" must never count as product completion; ten closure layers decide instead.
- No AI may plead "I didn't know the project" after violating a safety, design, data or architecture boundary.
- High-impact AI work needs separated implementer/reviewer/validator roles even when the same model fills them.
- Small change surface, explicit ownership, narrow contracts and enforced dependencies beat arbitrary file
  fragmentation.

## Options Considered

### Option A — Conventional file-by-file modularity with informal ownership (rejected)

Small files and folder conventions with ownership "understood" by the team. Rejected: no machine-verifiable
boundaries, no enforced dependency direction, no minimum-context guarantee — a single AI task can silently cross
any line, and review cannot prove it didn't.

### Option B — Monolithic AI context (whole-project reads per task) (rejected)

Every task loads the full repository context. Rejected: context bloat, unpredictable cost, stale-context drift
between tasks, and no least-privilege scoping — the opposite of the approved operating model.

### Option C — Contract-governed task-addressable capsules with a verifiable project graph (chosen)

Every applicable part behaves as a capsule (purpose, public surface, interior, allowed dependencies, tests,
change rules, project links); an Obsidian-compatible graph makes purpose, ownership, dependency, requirement,
task, test, evidence and change-chain relations machine-checkable; every task ships with a minimum sufficient
context pack; closure is proven across ten layers; task plans simulate dependency/conflict/failure/rollback/
closure before development.

## Decision

Kavriva adopts Option C with the following locked architecture:

1. **Capsule rule:** each module owns an explicit purpose, public contract surface, internal scope, allowed/forbidden
   dependencies, tests, change/rollback rules and requirement/design/task/test links. Goal is minimum change
   surface plus enforced boundaries — never file-count fragmentation.
2. **Repository topology:** planning truth (this repository) and implementation truth (later code repository/vault)
   stay linked through stable identities; generated artifacts, evidence registries and task queues live at
   governed addresses; no orphan files or folders — everything resolves to at least one purpose/ownership/module/
   task link (small source files via module manifests, path indexes and task evidence, not per-file bureaucracy).
3. **Graph metadata and identity (binding standard):** Markdown/Obsidian-compatible records with stable identity
   and machine-verifiable metadata supporting at minimum `purpose`, `domain/module/owner`, `depends_on`/`used_by`,
   `implements`, `public_contracts`/`internal_scope`, `tasks`/`tests`/`evidence`, `supersedes`/`superseded_by` and
   `status`/`last_verified`. Orphan records, broken links, forbidden dependencies, cycles, ownerless public
   contracts, untested critical behavior and stale context packs are detectable at quality gates — a hand-drawn
   diagram alone never counts.
4. **Dependency direction:** dependencies point toward stability (product truth → contracts → capsules → tasks);
   private internals never leak upward through public contracts; classification and authority boundaries from
   ADR-001/ADR-004 propagate through every edge; cross-boundary use requires an explicit allowed edge, never
   silent import.
5. **Task-pack minimum (binding for Phase 6 schema and Phase 7 protocol):** single measurable objective; user
   outcome linkage; preconditions and completed dependencies; mandatory ADR/contract/rule/screen/module reads;
   allowed paths/modules; forbidden areas and escalation rules; expected artifact changes; acceptance plus
   negative/failure cases; validation/architecture/integration checks to run; migration/rollback/data-protection
   needs; design reference with responsive/accessibility rules; completion evidence and handoff format; graph
   records the task must update. An AI forced outside its pack moves the task to `BLOCKED`/change-request —
   never silently expands scope.
6. **Ten closure layers (all required for completion claims):** task, feature, flow, requirement, design,
   architecture, data/migration, release, product-scenario and gap-audit closure, traced bidirectionally as
   `Requirement/Rule/Screen/State → Epic → Capability → Feature → Flow → Task → Contract/Module → Test/Evidence`
   and back. Orphan tasks and taskless requirements are both rejected.
7. **No-code simulation before development:** execution order over the dependency graph, document-level
   post-task state checks, blocked/failed/partial/retry/rollback/requirement-change scenarios, parallel-AI
   collision analysis, old/new contract compatibility, critical-flow walkthroughs, requirement-to-evidence gap
   scans, task-removal gap tests and all-DONE re-evaluation of product/release gates. Open links stay visible as
   `MISSING`, `UNOWNED`, `BLOCKED`, `CONFLICT` or `UNVERIFIED` — never smoothed over.
8. **Design consistency:** canonical tokens, component/pattern catalog, layout/type/icon/motion rules, responsive
   and Turkish-content rules, screen/state contracts, accessibility semantics, reference screens with variation
   bounds and shell/navigation rules form the single source; new patterns enter only through controlled design
   change, with full-screen, cross-screen, cross-state, responsive, accessibility and regression evidence at
   feature and release level.
9. **Role separation:** implementer, reviewer and (where needed) adversarial/validator roles stay independent in
   role, context and first review even on the same model; shared-blind-spot risk stays visible; AI never
   impersonates legal identity, store ownership or qualified attestation, and unavoidable external dependencies
   surface early in nontechnical language with the exact required user/outside action.

## Rationale

Only verifiable structure (not conventions, not whole-project reads) can guarantee that bounded AI work stays
bounded across hundreds of tasks and multiple models. Locking the shape now — before Phase 6 decomposes work —
prevents delivery pressure from quietly trading away the boundaries, packs, simulation and closure proof that the
entire AI-operated model depends on.

## Consequences

### Positive

- Every future task is plannable, reviewable and provable against the same structural contract.
- Design, safety, data and architecture boundaries become machine-checkable instead of tribal knowledge.
- Completion claims become evidence chains instead of task-count assertions.

### Negative / Trade-offs

- Capsule, contract, graph and simulation discipline is real upfront planning overhead in Phase 6–8.
- Strict pack scoping will block tasks that could "just quickly" cross a boundary — friction by design.
- The graph and gates need building and maintenance (Phase 7–8, then Development) before they pay back.

## Prohibited / Constrained Alternatives

- Informal ownership, unenforced boundaries, whole-project context loads, silent scope expansion.
- `all tasks DONE` presented as product completion without the ten closure layers.
- Self-PASS of high-impact AI output without independent review.
- Design invention outside the canonical system; components/patterns added without controlled change.
- AI impersonation of human/organizational authority.
- Phase 7–8 mechanism choices (router design, harness, CI plumbing, vault layout) pre-decided here — this ADR
  fixes shape and standards; mechanisms follow in their phases.

## Revisit Triggers

- Evidence shows the capsule/graph/pack/closure apparatus costs more than the defects it prevents at Kavriva's
  measured scale, or a strictly stronger verifiable alternative emerges — resolved by superseding ADR with
  measured before/after evidence.
- Exact identity scheme details, metadata serialization, router/harness/CI designs and vault layout remain HELD
  for Phase 7–8 design evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0028`, `DEC-0029` (binding requirements)
- `00_CONTROL/PROJECT_SCOPE_ADDENDUM_AI_NATIVE_EXECUTION_SYSTEM.md`
- `00_CONTROL/PHASE_GATES.md` — Gate 5 -> 6 exit criterion (requires this ADR scope)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md` through ADR-014 (governed
  boundaries this topology enforces)
- Downstream: Phase 6 (epic→task network, closure matrix, simulation), Phase 7 (context routing, packs,
  validation, change control), Phase 8 (vault, manifests, CI gates, bootstrap proof)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
