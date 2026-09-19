# DEBATE-007 — Architect / Judge Synthesis

Status: `PASS_WITH_CHANGES — CORRECTIONS INCORPORATED / USER APPROVED DEC-0034 / ADR NOT READY`
Date: 2026-09-18

## Inputs

- repository-derived data/backbone requirements synthesis;
- official/primary-source mechanism research;
- user-supplied external deep-research report and controlled intake audit;
- manager proposal for data backbone and logical boundaries;
- independent Review A — data safety/offline/domain integrity;
- independent Review B — security/operations/cost/provider exit.

## External Research Disposition

The external report was useful for identifying mechanisms: authoritative-versus-local state, delta/cursor sync, outbox,
idempotency, conflict policy, media separation, backup/PITR and managed-versus-self-hosted trade-offs. It did not satisfy
the requested primary-source standard overall. Unsupported percentages, zero/perfect language, Flutter-Web assumption,
fixed upload thresholds and categorical PostgreSQL/API/NoSQL/VPS/provider conclusions were excluded.

## Reviewer Agreement

Both reviewers accept the high-level provider-neutral shape and reject implementation/provider/ADR readiness. They agree
that the proposal must not collapse authority into one database, treat managed service as safety, use a local cache as
truth, or call backup/export success recovery proof.

Review A exposed restore resurrection, physical-action recall races, incomplete offline packages, classification leakage
and inconsistent cross-boundary snapshots. Review B exposed privileged authorization bypass paths, object capability and
audit custody gaps, incomplete recovery/exit, account/billing/region failures, uncapped cost, AI privilege and premature
PostgreSQL/managed preference.

## Corrections Incorporated

- canonical authority per domain, not an assumed single physical database;
- PostgreSQL and managed relational reduced to later equal-comparison hypotheses;
- protected non-restorable release/security/deletion/operation/migration floor;
- action-bound eligibility checks and machine-verifiable closed offline package manifests;
- classification propagation and deletion/withdrawal behavior across all copies and derivatives;
- explicit cross-plane partial/unknown/reconciliation state machine;
- effect/idempotency/audit/object/outbox binding and protected-audit hold rule;
- coordinated export/restore consistency manifest plus independent clean-room import;
- complete privileged-path and product/workload/provider identity matrix;
- provider/account/billing/region failure states, staged true-cost controls and AI operation runbooks;
- local device loss/non-eviction, cross-plane recovery and provider-exit evidence.

## Judge Determination

The corrected proposal is coherent as a Phase-4 working direction:

> canonical transactional authority per domain; server/API-mediated sensitive access; online-authoritative Internal
> Operations; bounded, closed and versioned mobile offline packages; durable user operations with explicit reconciliation;
> separate current/history/protected-audit and object/media planes; rebuildable non-authoritative projections; and
> cross-plane tested backup, restore, export and exit.

No database engine, BaaS, API runtime, Flutter storage library, object store, cloud/provider, identity service, backup tool,
paid plan or numeric RPO/RTO is selected. Relational/PostgreSQL and managed service are later candidates, not conclusions.

Verdict:

- Phase-4 direction: `PASS_WITH_CHANGES — CHANGES INCORPORATED`;
- user approval: `RECEIVED 2026-09-18 / DEC-0034`;
- engine/provider/physical architecture ADR: `HELD`;
- code/prototype/purchase: `NOT AUTHORIZED`;
- Gate 4 -> 5: `REMAINS CLOSED`.

## Evidence Links

- [[DEBATE-007__DATA_BACKBONE_AND_LOGICAL_BOUNDARIES]]
- [[DEBATE-007__DATA_BACKBONE_REQUIREMENTS_SYNTHESIS]]
- [[DEBATE-007__DATA_BACKBONE_PRIMARY_RESEARCH]]
- [[DEBATE-007__EXTERNAL_RESEARCH_INTAKE_REVIEW]]
- [[DEBATE-007__REVIEW_A_DATA_SAFETY_OFFLINE]]
- [[DEBATE-007__REVIEW_B_SECURITY_OPERATIONS_COST]]
