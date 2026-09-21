# ADR-001 — Canonical Data Authority and Logical Service Boundaries

Status: PROPOSED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-007, user-approved under `DEC-0034`) defined a provider-neutral data shape before any
physical product, provider, schema, package, cloud, paid plan or code is chosen. Kavriva must serve three paths from
one trustworthy core: browser-based Internal Operations (create/review/approve/publish/correct/recall), the Flutter
consumer app (bounded offline motorcycle/task packages), and durable user work (history, evidence, pending operations)
that survives retries, conflict, restore, migration and provider exit — operated for a nontechnical solo owner who
must never administer or repair a database.

## Decision Drivers

- A nontechnical solo owner operates the project; no SQL/SSH/log repair may be required (`DEC-0029`, `DEC-0030`).
- Safety, provenance, approval/publication/recall integrity and protected audit are product requirements
  (`DEC-0024`–`DEC-0027`).
- Offline use is bounded and data-efficient; unknown/stale critical state fails closed (`DEC-0023`, `DEC-0024`).
- Provider choices must stay reversible within the approved cost envelope (`DEC-0030`, `DEC-0032`).
- AI-operated delivery needs explicit boundaries, minimum task context and completion proof (`DEC-0028`).

## Options Considered

### Option A — Canonical authority per domain with server/API mediation and separated planes (chosen)

Each data domain has one canonical transactional authority for current state and cross-record rules, joined through
stable identity, version/generation, operation and manifest contracts — without requiring one physical database.
Flutter and browser clients hold no general database authority; sensitive reads and every mutation pass a server-side
contract. Current state, domain history/provenance and protected audit are distinct meanings. Files/media live behind a
separate logical object boundary with quarantine-first ingestion. Search, analytics, cache, notifications and package
builders are rebuildable non-authoritative copies. Restore/migration uses a protected non-restorable
release/security/deletion/operation floor so old backups cannot resurrect revoked authority.

### Option B — One mutable "current data" bucket

A single store holding whatever is newest, with history and audit as optional add-ons. Rejected: it erases history,
provenance, dispute and release meaning, cannot express recall/suspension generations, and makes restore/exit unsafe.

### Option C — Premature distributed fleet (microservices / event backbone / CRDT / distributed DB now)

Rejected for first release: no concrete load or isolation need justifies it, and it would place unoperable recovery
burden on bounded AI workflows and, in failure, on the nontechnical owner. Deferred until a concrete requirement with
an operable recovery path exists.

## Decision

Kavriva adopts Option A as the binding logical data architecture:

1. **Main truth:** current approved facts, relationships, permissions and user records, one canonical authority per domain.
2. **History and evidence:** who changed what, supporting sources, superseded/disputed states — never silently overwritten.
3. **Publishing control:** exact reviewed versions eligible for consumers; suspended/recalled versions fenced by generation.
4. **Files and media:** dedicated object boundary (identity, version/generation, digest, classification, lineage, owner,
   state, retention); uploads enter quarantine-first and no client holds global storage credentials.
5. **Phone package:** compact, versioned, integrity-bound selected-motorcycle/task material with complete
   safety/recovery closure; partial or mixed packages are unusable.
6. **Convenience copies:** search, analytics, cache, notifications — rebuildable, never authority.

Supporting rules now locked: online-authoritative Internal Operations mutations with durable operation identity
(accepted/rejected/conflict/held/outcome-unknown, reconciled by lookup, no blind repeats); durable pending user-work
operations with stable identity and idempotent retry (no silent last-write-wins for high-consequence data);
classification (private/shared/community/official/security) propagating to every derivative, copy, export and backup;
cross-plane operations (DB/object/audit/outbox) using explicit partial/reconciling states; provider/billing/outage
failure as first-class owner-readable states; minimum-sufficient AI runbooks with least-privilege credentials.

## Rationale

Option A is the only shape that simultaneously satisfies fail-closed offline safety, immutable approval/release
integrity, protected audit, quarantine-first ingestion and clean provider exit without assuming a physical product
first. It keeps first-release complexity minimal (no forced microservices) while making every later physical choice
testable against the 16 acceptance-gate families recorded in DEBATE-007 §7.

## Consequences

### Positive

- Every later ADR (physical backend, runtime, offline, identity, web, CMS, analytics, build, AI) inherits one
  consistent authority/epoch/negative-floor vocabulary instead of re-deciding it.
- Safety, recall and audit behavior stay provable across provider change, restore and exit.
- Owner never needs database skills; AI tasks stay narrowly scoped and reviewable.

### Negative / Trade-offs

- More upfront modeling discipline: identity/version/generation contracts and the consistency manifest must be
  specified before implementation; shortcuts will be rejected by later gates.
- Cross-plane (non-atomic) operations need explicit state machines instead of simple transactions — more states for
  AI workflows to implement and for reviewers to verify.
- Some convenient managed features (direct client DB access, provider-native sync) are permanently off-limits for
  authoritative data.

## Prohibited / Constrained Alternatives

- Direct general client authority over canonical database or object storage.
- Client/UI/cache state as authorization, approval, publication, recall or audit truth.
- Silent last-write-wins for high-consequence data.
- Partial/mixed offline package use; full-library default download.
- Push/background delivery as correctness or recall proof.
- AI/OCR, signature, scan, CDC or provider log as sole technical-correctness evidence.
- Restore/rollback resurrecting revoked authority or discarding newer valid data.
- Microservice/event/CRDT/distributed-database layer without a concrete requirement and operable recovery path.

## Revisit Triggers

- A measured workload proves the single-authority-per-domain shape cannot meet a mandatory product requirement
  within the approved budget and an explicit isolation need exists.
- A later ADR (e.g. physical backend, runtime) demonstrates with evidence that a locked rule here blocks all viable
  candidates; the conflict is then resolved by a superseding ADR, never by silent deviation.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0034` (binding working direction)
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__DATA_BACKBONE_AND_LOGICAL_BOUNDARIES.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__DATA_BACKBONE_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__DATA_BACKBONE_PRIMARY_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__EXTERNAL_RESEARCH_INTAKE_REVIEW.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__REVIEW_A_DATA_SAFETY_OFFLINE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__REVIEW_B_SECURITY_OPERATIONS_COST.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-007__JUDGE_SYNTHESIS.md`
- Downstream: ADR-002 through ADR-015 (all inherit this vocabulary)

## Supersedes

None.

## Superseded By

None (PROPOSED — owner approval pending).
