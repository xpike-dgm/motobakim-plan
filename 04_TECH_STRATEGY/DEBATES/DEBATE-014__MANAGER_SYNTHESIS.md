# DEBATE-014 — Analytics and Measurement Strategy Manager Synthesis

Status: `USER-APPROVED PHASE-4 WORKING DIRECTION / DEC-0044 / NO PROVIDER WINNER`

## Nontechnical Decision

Kavriva measurement'ı ürünün gerçeği veya güvenlik otoritesi olarak değil, yalnızca gözlem katmanı olarak kullanmalı.

First release should preserve a split boundary in which Kavriva owns canonical operational metrics and
protected evidence, product analytics stays optional and replaceable, and reliability/observability remains a separate
plane. If a dedicated product-analytics layer cannot meet privacy, cost, offline and clean-exit evidence gates, Kavriva
should fall back to the smaller owned baseline rather than weakening those gates.

## Binding Phase-4 Working Direction

- Internal Operations coverage and data-quality metrics derive from Kavriva canonical records, not consumer telemetry.
- Protected privileged-action audit/security evidence stays outside analytics.
- Product analytics is purpose-limited, minimized, anonymous/account-light by default and non-authoritative.
- Analytics consent denial, SDK/provider outage, quota/billing hold, late upload or deletion request cannot disable the
  safe core path or critical negative-safety/recall behavior.
- Reliability/crash/performance observability remains a separate plane; store/platform vitals are supporting evidence only.
- Product-analytics provider replacement must be possible without moving canonical records, protected audit or owned
  operational metrics.
- Raw export alone is not accepted as proof of clean exit. Identity/deletion fidelity, derived objects, late-arriving
  data and mobile instrumentation portability remain HELD until separately proven.
- The nontechnical owner gets simple health/status and escalation paths; recovery must not require SQL, queue surgery,
  SDK debugging or provider-console expertise.

## First-Release Measurement Capability

Mandatory at direction level:
- plane separation;
- canonical-record-derived Internal Operations coverage/data-quality visibility;
- minimal purpose-limited product usage measurement where allowed and useful;
- crash/ANR/performance supporting signals;
- consent/opt-out enforcement;
- telemetry health for late/drop/duplicate visibility;
- old-client semantic compatibility;
- retention/delete/export path;
- outage independence.

Deferrable:
- identified analytics profiles and anonymous-to-profile history merge;
- cross-device identity;
- advanced funnels/cohorts/retention;
- warehouse streaming and rich segmentation.

Optional:
- session replay, heatmaps, broad autocapture, surveys and detailed device/location enrichment.

Scale-triggered:
- dedicated collector tier, warehouse/lake export, long raw retention, advanced sampling/cardinality controls,
  multi-region analytics, paid SLA/support and automated spend controls.

## Data-Minimization Boundary

Baseline analytics should not collect VIN/chassis identifiers, raw repair evidence/media, free-text repair notes,
email/phone/name, advertising or cross-company tracking identifiers, protected-audit receipts, secrets/tokens or
arbitrary high-cardinality properties merely because an SDK exposes them.

Coarse motorcycle/variant context, app/build version, pseudonymous identifiers and crash/performance diagnostics require
a named purpose and bounded retention/access behavior.

## Architecture Families After Review

- Family A — Kavriva-owned minimal measurement remains the safe fallback and can carry canonical operational metrics.
- Family B — managed dedicated product analytics can reduce infrastructure burden, but provider/SDK/privacy/volume/exit
  dependencies remain evidence gates.
- Family C — self-hostable/open-source analytics increases infrastructure/data control but also shifts upgrades, backups,
  security, support and incident burden onto Kavriva; it is not assumed cheaper.
- Family D — split/hybrid is the manager's conditional architecture-shape proposal because it isolates canonical
  operations, replaceable product analytics and observability failure domains. It is not a provider winner and is only
  acceptable while the clean-room and privacy/TCO gates remain explicit.

## Evidence and Review History

- TASK-002 research package compared four architecture families with two candidate/reference mechanisms per family.
- Source ledger contains 30 official/primary references.
- Failure walkthrough contains 16 mandatory scenarios × four families = 64 family rows with eight required fields.
- REVIEW-003 returned CHANGES_REQUESTED with one Major M-1 limited to S15 clean-room replacement / Family D.
- AI-001 remediated only S15-D; unsupported portability points remained HELD.
- REVIEW-004 returned PASS with no Critical, Major or Minor findings and confirmed no regression in the other 63 rows,
  measurement-plane separation, privacy/minimization boundary, source ledger or conditional direction.
- TASK-002 is DONE after manager readback.

Exact Drive links are registered in `00_CONTROL/DRIVE_ARTIFACT_INDEX.md`.

## What Remains HELD

- Flutter-specific offline queue/process-death/duplicate/clock behavior for a shortlisted client path.
- Anonymous-to-profile merge/split, shared-device, logout/reset and motorcycle-switch identity semantics.
- Exact retention periods and deletion treatment of derived aggregates/backups/exports.
- Finalist DPA/subprocessor/residency evidence.
- Real release-build SDK overhead.
- Owner-facing support/incident runbook.
- Clean-room historical export fidelity including identity/deletion/derived objects.
- Provider-neutral mobile observability sufficiency.
- Jurisdiction-specific legal/privacy applicability and final consent wording.

## User Approval

The user explicitly approved this Phase-4 working direction under `DEC-0044`.

## Boundary

This proposal does not approve a product-analytics provider, observability provider, account, plan, trial, purchase,
event schema, SDK integration, code, final KPI target, legal conclusion, deployment, Phase-5 ADR or Gate 4 -> 5 transition.
