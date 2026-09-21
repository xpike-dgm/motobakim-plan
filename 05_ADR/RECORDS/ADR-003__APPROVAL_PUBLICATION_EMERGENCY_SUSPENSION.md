# ADR-003 — Approval, Publication, Emergency Suspension and Restore Semantics

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

> **Record integrity note (2026-09-21):** this file briefly held a duplicate of the ADR-004 text after a tooling
> write fault overwrote it (the fault reported success but wrote ADR-004 content to this path). The defect was
> caught by the independent Phase-6 epic-coverage verification before any downstream work consumed it. The genuine
> ADR-003 text below is restored exactly as presented to and approved by the owner; no decision was changed. The
> duplicate content was removed, not merged. See `00_CONTROL/CHANGELOG.md`.

## Context

Phase-4 strategy (DEBATE-003, user-approved under `DEC-0025`) answered how Kavriva guarantees that exactly the
reviewed material becomes consumer-eligible, that edits/retries/failures cannot silently publish another state, that
unsafe material can be stopped even when normal paths are down, and that restore cannot resurrect danger or erase
history. This ADR converts that direction into binding release semantics on top of ADR-001 (logical boundaries) and
ADR-002 (physical platform). It selects no database, cloud, CMS, queue, CDN, identity provider, signing technology,
frontend framework or vendor, and no numeric target.

## Decision Drivers

- Approval-to-consumer integrity: the approved exact meaning must equal the servable meaning, including derived
  artifacts, localization, transforms, media, configuration and scope.
- Honest outcomes: success, failure, partial and unknown must be distinguishable to operators and consumers.
- Independent safety stop: a compromised or unavailable publisher must not block suspension of unsafe content.
- Restore discipline: backups must never move release or suspension authority backward.
- Nontechnical operation: states carry owner-readable reason, owner, next action and effect.

## Options Considered

### Option A — Approved record becomes live directly (rejected)

An approved database/CMS record is also the consumer-live record. Rejected: in-place edits change approved meaning,
review races delivery, partial updates create mixed meaning, direct data access becomes an undeclared publication
path, and rollback/audit lineage turns ambiguous.

### Option B — Controlled immutable release (necessary but insufficient alone)

Approval binds one exact immutable snapshot; a release candidate carries exact approved versions plus dependency
closure; only one authoritative guarded transition changes the consumer-current release. Adopted as the normal path.
Alone it is insufficient: if emergency suspension shares the same identity, database, publisher and delivery path, the
safety control can fail together with the incident it must contain.

### Option C — Controlled release plus independent emergency suspension plane (chosen, as B + C)

Option B plus a narrowly scoped suspension authority and delivery path designed to stay usable when material parts of
normal publishing are unavailable. Cost: extra operational complexity, misuse risk (suspending valid content), and an
independence that must be tested, not merely described. Fully offline devices still cannot learn a new suspension
immediately (accepted DEBATE-002 residual constraint).

### Option D — Manual exports and operator-led updates (rejected as primary model)

Rejected: slow emergency response, weak proof of uniform version delivery, drift through manual copying. Documented
out-of-band communication may remain a contingency only.

## Decision

Kavriva adopts Option B + C with the following locked semantics:

1. **Approval binds exact meaning:** immutable snapshot identity and integrity evidence; exact claims/content/media and
   dependencies; applicability scope; evidence/provenance considered; validation findings and open uncertainty;
   reviewer identity, role/scope, time and rationale; conditions, expiry and consequence class; all derived/rendered
   artifacts and transformation inputs that can change consumer meaning. A later edit creates a new candidate; the
   approved snapshot is never mutated in place.
2. **One authoritative publication transition per consumer scope:** expected-current-version check, idempotent
   operation identity, atomic promotion of a complete manifest (or explicit all-or-partial guarantee), server-derived
   result/timestamp/audit event, and an independent read-after-operation status lookup. Preflight checks are
   re-verified at commit; the browser never decides success locally.
3. **Explicit state model:** `PREPARED → AUTHORIZED → PUBLISHING → AUTHORITATIVE_CURRENT → DELIVERY_OBSERVED →
   CONSUMER_RECONCILED`, with `HELD`, `FAILED`, `OUTCOME_UNKNOWN`, `PARTIAL_PROPAGATION`, `SUPERSEDED`, `SUSPENDED`
   and `RECALL_OPEN` branches. Authoritative-current means the guarded transition completed, not instant delivery;
   consumer-reconciled never implies an offline device received the change.
4. **Fenced precedence:** publication is conditional on the exact current suspension/revocation generation; a newer
   suspension can never be cleared by an older or in-flight publish; any backward move of release or suspension
   generation is a fatal authority error, never a valid rollback.
5. **Independent emergency plane:** negative-only authority (restrict future application, never create positive truth
   or replacement content); narrower action set than the publisher; operational independence from the normal
   publisher/data-plane/session path, tested by drills; strongly authenticated, minimal-membership, time-bounded use
   with two-person confirmation where delay does not increase harm and one documented single-actor path where waiting
   is more dangerous; every attempt recorded in protected audit; durable operation identity with the same
   outcome-unknown honesty; suspension generation never moves backward across restore/failover.
6. **Rollback as a new event:** only to an exact previously approved, still applicable/compatible/non-recalled release
   through the same controlled path; otherwise suspend and prepare a corrected release. Rollback never erases the
   intervening release's record or cancels reach-back.
7. **Restore quarantine:** a restored system serves no positive eligibility and accepts no normal publication until
   current-release identity, latest suspension/revocation floor, audit continuity and content integrity reconcile.
8. **Consequence-proportionate separation of duties:** author, domain reviewer, safety approver and publisher remain
   distinct for high-consequence packets (per-change independence, not just role membership); audit/security oversight
   inspects without becoming the ordinary publisher; unavailable independent competence yields visible `HELD`, never
   self-approval.
9. **Consumer contract:** exact release identity/integrity, scope, dependency closure, current/superseded/suspended/
   recall meaning, capability envelope, monotonic ordering and last reconciliation context must be evaluable client-side;
   push is advisory only; stale cache is never treated as current.

## Rationale

Direct-live (A) and manual (D) models fail the core integrity question by construction. Controlled release (B) closes
the approval-to-consumer chain, and only an independent negative plane (C) keeps the stop capability alive during the
incidents that most require it. The 18 acceptance scenarios (editor race, split-brain tabs, lost responses, recalled
dependencies, IdP outage, old-restore, compromised credentials, missing rollback candidate, claim-level suspension and
others) are the binding test suite for any implementation of this ADR.

## Consequences

### Positive

- Bit-exact traceability from review decision to served bytes; deterministic diff, lineage and rollback candidates.
- Safe retries everywhere through operation identity; no duplicate-effect or silent-mixed-state classes.
- Safety stop survives publisher compromise and defined infrastructure outages.
- Operators and consumers always see an honest state, including unknown.

### Negative / Trade-offs

- Release machinery is heavier than "approve = live": manifests, generations, preflight, reconciliation lookups.
- Emergency independence (separate credentials, paths, drills, retrospectives) is permanent operating cost.
- Genuinely offline devices keep an explicit residual recall race; no online architecture removes it.
- Unknown/partial states require owner-readable escalation ownership, otherwise they become silent holds.

## Prohibited / Constrained Alternatives

- Any second uncontrolled path (operator UI shortcut, API bypass, direct data access, cache/CDN state, provider
  restore) to consumer-current state.
- Retry creating a second different publication effect; stale tab/role/approval gaining authority from browser state.
- Timeout reported as success or failure before authoritative reconciliation.
- Suspension cleared by older/in-flight publication; generation moving backward for any reason.
- Rollback by binary restore discarding newer valid data or reviving revoked truth.
- Emergency authority authoring content, granting positive eligibility, or silently re-entering suspended scope.
- Publisher able to erase or rewrite evidence of its own actions.

## Revisit Triggers

- Measured evidence shows the single authoritative transition cannot meet a mandatory product requirement and an
  explicit, tested alternative preserves all fenced-precedence and audit properties; resolved by superseding ADR.
- Numeric targets (suspension latency, propagation/acknowledgment objectives, RTO/RPO, emergency credential bounds,
  operator staffing, unknown-resolution ownership, dormant-client reach-back), the exact scope lattice/publishable
  unit, quorum/staffing rules and implementation technology are intentionally HELD for later ADR/design work — their
  absence does not weaken the semantics above.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0025` (binding working direction)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-002__PHYSICAL_BACKEND_PLATFORM_AND_API_AUTHORITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-003__REVIEW_A_PROCESS_SAFETY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-003__REVIEW_B_SECURITY_RESILIENCE.md`
- Downstream: ADR-005 (audit custody), ADR-007 (supply chain/release), ADR-009 (offline recall propagation),
  ADR-011 (CMS publishing mechanics)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
