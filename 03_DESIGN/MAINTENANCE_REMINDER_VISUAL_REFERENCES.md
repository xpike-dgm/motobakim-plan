# KAVRIVA MAINTENANCE / REMINDER VISUAL REFERENCES

Status: APPROVED WORKING VISUAL REFERENCE SET
Approved: 2026-09-16
Reference: `REF-MAINT-001`
Evidence: `KAVRIVA_MAINTENANCE_REMINDER_VISUALS_01_HANDOFF.md`
Review: `KAVRIVA_MAINTENANCE_REMINDER_VISUALS_REVIEW.md`

## Approval Boundary

H01–H04 are approved as working Phase-3 visual references for FAM-05 Maintenance / Reminder.

Approval covers:
- hierarchy,
- reminder/completion separation,
- maintenance-to-guide continuity,
- catch-up prioritization meaning,
- explicit uncertain-timing behavior,
- visual continuity with approved Kavriva references.

It does NOT finalize production copy, exact maintenance content, intervals, components/tokens, notification cadence, routing, exact surface modality, accessibility implementation, backend/data architecture or Gate 3 -> 4.

## Approved Working Set

- **H01 — SCR-022 Maintenance Plan**
  - authority remains existing approved `R02-Bakim.png`,
  - scannable maintenance-plan root,
  - no dashboard/KPI treatment.

- **H02 — SCR-023 Maintenance Item / Reminder Detail**
  - explains why an item is shown,
  - keeps source/timing detail progressively accessible,
  - dominant `Rehberi ac` connects to guide preview / fit / readiness,
  - `Yapilan bakimi kaydet` is a separate path,
  - `Daha sonra hatirlat` does not imply completion.

- **H03 — SCR-024 Catch-Up & Critical Priorities**
  - calm ordered catch-up rather than notification flood,
  - first priority is based on supported safety/use impact, not mere lateness,
  - remaining plan stays accessible.

- **H04 — SCR-022/023 Maintenance Timing Uncertain**
  - explicitly states when maintenance timing cannot be supported,
  - does not invent due/overdue state,
  - offers history/evidence/source resolution paths,
  - reading a guide does not imply maintenance is currently due.

## Required Constraints

1. No fabricated date, mileage, interval, threshold or model-specific maintenance value.
2. H02 `Yaklasiyor`-type states are valid only when supported by applicable verified maintenance information and usable completion/history evidence.
3. A user-entered work record is not automatically a verified maintenance fact; provenance/evidence semantics remain separate.
4. Snooze/postpone changes reminder behavior only; it never marks maintenance complete.
5. `Yapilan bakimi kaydet` records actual work and must preserve actor/source/evidence meaning rather than silently upgrading trust.
6. H03 is not a universal `brakes always first` rule. Priority must come from current supported safety/use impact and relevant applicable conditions.
7. H04 must preserve uncertainty when source applicability or completion history is insufficient.
8. Critical historical correction / safety reach-back is not represented as an ordinary routine reminder.
9. Generated motorcycle/mechanical imagery is illustrative and is not evidence of fit, condition or maintenance truth.
10. H02 bottom-bar visibility and H03/H04 focused navigation remain PROPOSED visual treatments only.
11. Exact notification cadence/control placement, copy, icons, components, tokens, dark mode and responsive behavior remain non-final.

## Image Provenance

H01 remains the previously approved `R02-Bakim.png` authority under `REF-SHELL-001`.

| ID | File | Size | SHA-256 |
|---|---|---:|---|
| H02 | `H02-SCR-023-Maintenance-Item-Reminder-Detail.png` | 887x1774 | `affe6f5277f9b6c0b0e3f22b75de2ae7e54f25b9c3f45f2635eb9f793d0b63aa` |
| H03 | `H03-SCR-024-Catch-Up-Critical-Priorities.png` | 887x1774 | `a4772c29e541819822d67f8a1548f0461d48c7893b1bf091fe795a0b727d6359` |
| H04 | `H04-SCR-022-023-Maintenance-Timing-Uncertain.png` | 941x1672 | `0b3f4c180c27dade4be9b8c965d048a9fcad0652f3a2016bf07a16b2c5e0d72c` |

PNG binaries were supplied in the manager conversation; this document records identity/provenance for the approved working reference set.

## Next Visual Family

FAM-06 — History / Evidence / Trust (`SCR-025`–`SCR-030`).
