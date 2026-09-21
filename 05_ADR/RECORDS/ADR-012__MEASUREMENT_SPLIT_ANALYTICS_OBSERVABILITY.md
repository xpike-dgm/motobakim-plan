# ADR-012 — Measurement Split: Canonical Metrics, Product Analytics, Observability

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-014, user-approved under `DEC-0044`) compared four measurement families (Kavriva-owned
minimal, managed product analytics, self-hostable/open-source analytics, split/hybrid) through official research,
a 64-row failure matrix, REVIEW-003 remediation and independent REVIEW-004 PASS. Conclusion: measurement is an
observation layer only; canonical operational metrics and protected evidence stay Kavriva-owned; product analytics
stays optional, minimized and replaceable; observability stays a separate, provider-neutral-where-feasible plane;
split/hybrid is the reversible shape with a smaller owned baseline as fallback. This ADR locks that split. It
selects no analytics or observability provider, account, plan, SDK or event schema, and authorizes no integration,
code, KPI target, legal conclusion or deployment.

## Decision Drivers

- Telemetry must never become technical truth, human approval, repair/safety proof, entitlement, recall authority,
  canonical state or protected audit.
- Operational visibility (coverage, data quality, workflow health) must derive from canonical records, not from
  consumer devices that may be offline, opted out or compromised.
- Privacy by default for a consumer app handling motorcycle, location-adjacent and repair data: minimize, anonymize
  and bound retention before collecting.
- Analytics failure (outage, quota, consent denial, deletion) must never degrade the safe core path.
- The owner needs plain health/status signals, never SDK debugging or console expertise.

## Options Considered

### Option A — Kavriva-owned minimal measurement only (safe fallback, kept)

Canonical-record-derived operational metrics plus crash/ANR/performance signals, no dedicated product-analytics
layer. Smallest cost, privacy and exit surface; thinnest product-usage insight. Retained as the automatic fallback
if a dedicated layer fails its evidence gates.

### Option B — Managed dedicated product analytics (held candidate)

Reduces infrastructure burden but imports provider/SDK/privacy/volume/exit dependencies — each an evidence gate,
not an assumption.

### Option C — Self-hostable/open-source analytics (held candidate)

More data control, but upgrades, backups, security, support and incident burden shift onto the project; not
assumed cheaper.

### Option D — Split/hybrid: owned metrics + replaceable analytics + separable observability (chosen shape)

Isolates canonical operations, replaceable product analytics and observability failure domains. Chosen as the
reversible architecture shape — not a provider winner — acceptable only while clean-room, privacy, TCO, offline,
owner-operability and exit gates stay explicit.

## Decision

Kavriva adopts Option D with Option A as the bound fallback:

1. **Plane separation (binding):** canonical operational coverage/data-quality metrics derive from Kavriva records;
   protected privileged-action audit/security evidence stays entirely outside analytics; reliability/crash/
   performance observability is a separate plane, provider-neutral where feasible; store/platform vitals are
   supporting signals only.
2. **Product analytics discipline:** purpose-limited, minimized, anonymous/account-light by default,
   non-authoritative and replaceable. Consent denial, SDK/provider outage, quota/billing hold, late upload or
   deletion request cannot disable the safe core path or critical negative-safety/recall behavior. Provider
   replacement must not move canonical records, protected audit or owned metrics.
3. **Data minimization (binding):** baseline collection excludes VIN/chassis identifiers, raw repair
   evidence/media, free-text repair notes, email/phone/name, advertising and cross-company tracking identifiers,
   protected-audit receipts, secrets/tokens and arbitrary high-cardinality properties merely because an SDK
   exposes them. Coarse motorcycle/variant context, app/build version, pseudonymous identifiers and
   crash/performance diagnostics each require a named purpose with bounded retention and access.
4. **First-release capability:** mandatory at direction level — plane separation; canonical-derived Internal
   Operations coverage/quality visibility; minimal purpose-limited usage measurement where permitted and useful;
   crash/ANR/performance signals; consent/opt-out enforcement; telemetry health (late/drop/duplicate visibility);
   old-client semantic compatibility; retention/delete/export path; outage independence. Deferrable: identified
   profiles, anonymous-to-profile merge, cross-device identity, advanced funnels/cohorts, warehouse streaming,
   rich segmentation. Optional (each needs separate purpose/privacy justification): session replay, heatmaps,
   broad autocapture, surveys, detailed device/location enrichment. Scale-triggered: collector tiers,
   warehouse/lake export, long raw retention, sampling/cardinality controls, multi-region analytics, paid
   SLA/support, automated spend controls.
5. **Fallback rule:** if dedicated product analytics cannot pass the privacy, owner-operability, safe-TCO, offline
   and clean-exit gates, first release ships the smaller Kavriva-owned baseline instead of weakening the gates.
6. **Exit honesty:** raw export alone is not clean-exit proof; cross-provider identity/deletion-state fidelity,
   derived-object fidelity, late-arrival handling and mobile-instrumentation portability stay HELD until separately
   proven.

## Rationale

The split gives each measurement job exactly one home with matching guarantees: operations get record-derived
truth, product questions get consented minimal signals, reliability gets its own plane — so no single provider
outage, deletion request or billing hold can take down safety behavior, and no analytics vendor can quietly become
the system's memory.

## Consequences

### Positive

- Safety and recall behavior provably independent of telemetry fate.
- Privacy posture reviewable line by line (purpose, retention, access per data class).
- Analytics vendor stays replaceable by construction; fallback keeps first release shippable without it.

### Negative / Trade-offs

- Thinner product insight at launch than a full analytics suite would give; funnels, cohorts and attribution wait.
- Three-plane discipline (owned metrics, analytics, observability) is permanent instrumentation and governance work.
- Held portability/exit proofs (identity/deletion fidelity, derived objects, late arrivals) must still be earned
  before any provider switch counts as clean.

## Prohibited / Constrained Alternatives

- Telemetry as technical truth, approval, entitlement, recall or audit evidence.
- Identified tracking, cross-company identifiers, raw evidence/media or secret collection by SDK default.
- Analytics consent/outage/deletion degrading safe core or negative-safety behavior.
- Raw export presented as clean-exit proof.
- Any analytics/observability provider, account, plan, SDK integration, event schema, final KPI, legal
  conclusion, deployment or purchase — none authorized by this ADR.

## Revisit Triggers

- A concrete product question provably needs deferred/optional capability (e.g. funnels, replay) with
  purpose/privacy justification — resolved by superseding ADR scoping exactly that capability.
- Provider choice, retention periods, derived-aggregate deletion treatment, DPA/subprocessor/residency evidence,
  SDK overhead, jurisdiction-specific consent wording and exit proofs remain HELD for later evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0044` (binding working direction)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-002__PHYSICAL_BACKEND_PLATFORM_AND_API_AUTHORITY.md`
- `05_ADR/RECORDS/ADR-005__PROTECTED_AUDIT_CUSTODY_RETENTION_AND_INVESTIGATION.md`
- `05_ADR/RECORDS/ADR-006__KAVRIVA_API_RUNTIME_AND_DURABLE_LONG_JOBS.md`
- `05_ADR/RECORDS/ADR-008__CONSUMER_MOBILE_FRAMEWORK.md`
- `05_ADR/RECORDS/ADR-010__INTERNAL_WEB_FRAMEWORK_RENDER_AND_HOSTING.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-014__MANAGER_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-014__ANALYTICS_MEASUREMENT_REQUIREMENTS_SYNTHESIS.md`
- `00_CONTROL/DRIVE_ARTIFACT_INDEX.md` (TASK-002 / REVIEW-003 / REVIEW-004 links)
- Downstream: ADR-015 (instrumentation module boundaries)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
