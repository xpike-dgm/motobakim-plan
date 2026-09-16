# KAVRIVA MAINTENANCE / REMINDER VISUALS — MAIN-MANAGER REVIEW

Status: PASS_WITH_CONSTRAINTS
Date: 2026-09-16
Scope: H01–H04 / FAM-05 Maintenance / Reminder
User acceptance evidence: `genel set iyi`

## QA Result

H01–H04 form a coherent working visual family and may be used as downstream Phase-3 reference authority within the constraints below.

## Screen Review

### H01 — Maintenance Plan
Existing approved R02 remains valid. Scannable list, no KPI/dashboard drift.

### H02 — Maintenance Item / Reminder Detail
PASS WITH CONSTRAINTS.

Strengths:
- clear item focus,
- `Rehberi ac` is dominant,
- actual-work recording is separate,
- snooze is visibly lower-emphasis and explicitly not completion,
- source/timing detail is progressively available.

Constraints:
- `Yaklasiyor` can appear only when an applicable verified maintenance source and usable history/completion evidence support that state,
- `Yapilan bakimi kaydet` must not silently upgrade a user-entered record to verified truth,
- generated brake imagery is illustrative only.

### H03 — Catch-Up & Critical Priorities
PASS WITH CONSTRAINTS.

Strengths:
- calm ordering rather than alarm wall,
- primary next action obvious,
- remaining plan preserved.

Constraints:
- the fixture must not become a universal rule that brake work is always first,
- prioritization requires supported current safety/use impact and relevant applicable conditions,
- text such as `Bir suredir bakim kayitlarini gozden gecirmediniz` is fixture-dependent and cannot be asserted without supporting product data.

### H04 — Maintenance Timing Uncertain
PASS.

Strengths:
- refuses fabricated due/overdue timing,
- clearly separates what is missing,
- gives useful resolution paths,
- guide reading is explicitly not a due-state decision.

Constraint:
- adding missing information must preserve provenance/evidence state; user input alone cannot convert unsupported timing into verified timing.

## Cross-Family Protections

- no invented intervals/dates/mileage/thresholds,
- postpone != completion,
- maintenance item -> guide preview -> fit/readiness -> application,
- uncertain remains uncertain,
- critical historical correction is not routine reminder UI,
- exact deep-flow bottom-bar visibility remains PROPOSED ONLY,
- exact production copy/tokens/components/icons/accessibility/routing remain non-final.

## Decision

Result: `PASS_WITH_CONSTRAINTS`.

The user-accepted H01–H04 set is suitable for `REF-MAINT-001` APPROVED working-reference status.

Next controlled visual family: FAM-06 History / Evidence / Trust.
