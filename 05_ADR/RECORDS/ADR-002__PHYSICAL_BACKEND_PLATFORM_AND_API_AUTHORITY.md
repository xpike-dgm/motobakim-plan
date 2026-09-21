# ADR-002 — Physical Backend Platform and API Authority Boundary

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

ADR-001 locked the provider-neutral logical shape: canonical authority per domain, mandatory server/API mediation,
separated history/audit/object planes, bounded offline packages and a non-restorable authority floor. Phase-4 strategy
(DEBATE-008, user-approved under `DEC-0035`) compared physical candidates with current official cost/capability
research, equal architecture/failure walkthroughs, two deliberately divergent independent reviews and manager
synthesis. The owner approved a managed Supabase-centered working direction behind the mandatory Kavriva API boundary,
with Neon + independent API + R2 as first fallback. This ADR converts that direction into a binding, reversible
platform decision. It authorizes no account, region, plan, subscription, purchase, code or production proof.

## Decision Drivers

- Nontechnical solo owner: fewer routine provider surfaces, bills, keys and failure lines (`DEC-0029`, `DEC-0030`).
- ADR-001 authority vocabulary must be physically enforceable, including the anti-resurrection floor and clean-room exit.
- Independent reviewers split honestly: owner/TCO/operability favored Supabase-centered; security/recovery/exit
  favored the modular composition. Both kept every scenario HELD (no-code phase forbids real restore/exit tests).
- Later TRY 2,000–3,000/month non-store planning ceiling is context, not spend authority (`DEC-0032`).

## Options Considered

### Option A — Managed Supabase-centered behind the Kavriva API boundary (chosen)

Managed Supabase PostgreSQL, Auth and private Storage as the initial physical core. Flutter and browser Internal
Operations receive no general database/object authority; sensitive reads and every high-consequence mutation pass the
Kavriva server/API boundary (Supabase Edge Functions or an equivalently bounded runtime as the initial
low-operations candidate, replaceable until proven). RLS/Storage policies are mandatory defense in depth, never sole
authority. `service_role`/secret keys are server-only. Supabase Studio is provider administration, not the Kavriva
Internal Operations surface. Database backup is acknowledged not to cover object bytes, audit or floor custody.

### Option B — Modular managed composition: Neon + independent API + R2 (first fallback)

Managed PostgreSQL (Neon) + independent API/runtime + Cloudflare R2 object storage. Physically explicit API/database/
object boundaries make clean-room exit map more directly to standard primitives — the security/recovery/exit
reviewer's reason to prefer it. Rejected as the starting direction because three providers from day one mean three
billing/outage/credential/support surfaces, converting a security advantage into operating risk for the solo owner.
Retained as the documented first fallback, not an automatic parallel implementation.

### Challenger / reference paths (not selected)

Firebase/Firestore, Appwrite, Cloudflare Workers/D1/R2-as-primary, raw self-host baseline and edge-SQLite paths were
researched as challengers/references. None is approved; self-hosting stays eligible only with automated, observable,
independently reviewable maintenance/recovery plus reproducible clean-room bootstrap — otherwise it is a future
option, not an exit fallback.

## Decision

Kavriva adopts Option A as the reversible physical backend direction, **only together with** the safeguards imported
from the modular review:

1. Server/API mediation for sensitive reads and all high-consequence mutations; no direct-client authority.
2. Private quarantine before object activation.
3. Database, object bytes, protected audit and negative floor treated as separate recovery planes with sufficiently
   independent custody from the ordinary project.
4. Stable IDs and logical export suitable for clean-room import outside the normal provider account.
5. Provider/account/billing outage represented by owner-readable held/unknown/unavailable states that safely stop
   positive writes and publication.
6. Task-scoped AI access without owner, billing, `service_role`, unrestricted SQL or global object credentials.
7. Dated provider changelog and compatibility hold before changed defaults reach production.

Phase-4 cost reading is carried forward as planning context only: Supabase Pro headline (~USD 25/month before
tax/FX/extras) is not the safe total; PITR (~USD 100/month) is not assumed for the early budget; API compute,
independent object backup, protected audit/floor, monitoring, scanning, notifications, restore/exit drills, support
and incident usage remain unresolved. Before any paid account decision, one normalized bill of materials must cover
minimum-safe closed test, minimum-safe Android production, later scale bands, incident month, restore drill and exit
drill. Free tiers may support later exploration but never stand in for production backup, audit, support or recovery.

## Rationale

Option A minimizes day-one operating surfaces for the solo-owner constraint while Option B's explicit-boundary
advantages are imported as mandatory controls rather than ignored. The disagreement between the two independent
reviews is preserved as a trade-off with a defined fallback, not papered over. Direction stays reversible through
explicit reversal triggers instead of provider commitment.

## Consequences

### Positive

- Fewest mandatory paid surfaces at the start; optional capabilities stay off until evidence requires them.
- One consistent enforcement point (Kavriva API) for ADR-001 authorization, epoch and floor semantics.
- Clean-room exit stays testable via stable IDs and logical export from the beginning.

### Negative / Trade-offs

- Single-provider concentration: Supabase-specific Auth/Storage/Functions coupling is the main exit risk, watched by
  trigger 8 below.
- Database backup ≠ full recovery: object/audit/floor custody must be built and paid for separately — the "simple"
  headline price understates the safe total, and this ADR forbids pretending otherwise.
- Three-provider coordination burden is avoided at the cost of keeping the fallback's exit-explicitness as
  requirements-to-prove rather than present-day structure.

## Prohibited / Constrained Alternatives

- Direct client authority over the database or object storage; RLS/Storage policy as sole authority.
- `service_role`/secret keys in clients, repositories, logs or ordinary AI task contexts.
- Supabase Studio as the Internal Operations product surface or as approval/publication/recall/audit authority.
- Database backup presented as covering object bytes, audit or floor recovery.
- Any provider account, region, plan, subscription, purchase or PITR add-on — none is authorized by this ADR.

## Revisit Triggers

Option A is withdrawn and Option B reopened through the same evidence gate if any occurs (binding, from `DEC-0035`):

1. Sensitive/high-consequence flows cannot stay behind the API boundary.
2. Minimum-safe recurring total (API + independent audit/floor + object backup + monitoring + recovery) exceeds the
   owner-approved envelope.
3. Service-role/RLS/Storage/console bypass cannot be bounded and negatively tested.
4. Old restore can resurrect recall, revoke, deletion, suspension or accepted operations.
5. Cross-plane (DB + objects + audit + identity/policy/config/package) restore manifest cannot pass.
6. Stable logical export + clean-room import outside the normal account cannot preserve required negative behavior.
7. Outage/billing/incident recovery requires owner SQL/SSH/debugging.
8. Supabase-specific coupling makes exit materially less safe than the modular fallback.

Option B does not win automatically on reversal; it must still prove three-provider billing/outage/credential/support
coordination through bounded AI workflows without owner debugging.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0035` (binding working direction), `DEC-0034` (logical boundaries)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__STACK_CANDIDATES_COST_PRIMARY_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__STACK_ARCHITECTURE_FIT_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__FINALIST_A_SUPABASE.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__FINALIST_B_MODULAR_MANAGED.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__EQUIVALENCE_AUDIT.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__EXTERNAL_REPORT_AUDIT.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__REVIEW_OWNER_TCO_OPERABILITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__REVIEW_SECURITY_RECOVERY_EXIT.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-008__MANAGER_SYNTHESIS.md`
- Downstream: ADR-003 through ADR-015 (runtime, offline, identity, web, CMS, analytics, build, AI inherit this platform)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
