# CURRENT STATE

## Current Phase

`PHASE-3 / DESIGN — MAINTENANCE + REMINDER VISUAL REFERENCES READY`

## Current Objective

Phase-2 Product Discovery APPROVED ve Gate 2 -> 3 PASSED.

Approved working design references:
- Brand: **Kavriva** — APPROVED.
- Logo direction: **L05A — The Precision Fit** — APPROVED working direction with QA constraints.
- Anchor UX: **U04 — Progressive Detail** — APPROVED working anchor hierarchy.
- Anchor visual direction: **V10 — Signature Kavriva** — APPROVED working visual direction with QA constraints.
- Full-app working screen/state architecture: **REF-ARCH-001** — APPROVED.
- Global navigation: **REF-NAV-001** — APPROVED.
- Screen-family / UX specifications: **REF-SPEC-001** — APPROVED working specs.
- AI Usta root UX: **REF-AIUSTA-001 / A1 — Guided Split** — APPROVED.
- Five-tab root visuals: **REF-SHELL-001 / R01–R05** — APPROVED.
- Guide Discovery / Fit / Preparation: **REF-GUIDE-001 / D01–D05** — APPROVED with constraints.
- Active Application / Safety / Recovery: **REF-ACTIVE-001 / E01–E05** — APPROVED with constraints.
- Diagnosis: **REF-DIAG-001 / G01–G04** — APPROVED with constraints.

## What Just Changed

### Diagnosis family

User supplied G01–G04 and portable handoff with acceptance:
> genel set iyi

Main-manager QA: `PASS_WITH_CONSTRAINTS`.

Approved diagnosis meaning:
- G01 plain-language symptom capture + danger-first gate,
- G02 one discriminating check at a time,
- G03 supported direction without certain-fault claim,
- G04 explicit unresolved outcome / useful handoff.

Required constraints:
- unsafe/uncertain G01 state cannot continue normal diagnosis,
- no random part replacement or fabricated probability,
- `Emin degilim` and unresolved remain valid,
- photo is contextual evidence, not default/automatic diagnosis authority,
- G03 supported result still goes through guide fit/readiness before application,
- reduced/hidden bottom bar remains PROPOSED ONLY.

Canonical:
- `03_DESIGN/DIAGNOSIS_VISUAL_REFERENCES.md`
- `03_DESIGN/KAVRIVA_DIAGNOSIS_VISUALS_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_DIAGNOSIS_VISUALS_REVIEW.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-DIAG-001`
- DEC-0021

### New project-scope requirement — Internal Data & Content Operations

User identified the need for an internal operational product/capability for motorcycle/technical data research, missing-data visibility, controlled updates, publishing and data-quality/coverage analytics, then explicitly confirmed:
> bu kesin yapılacak

This is now an APPROVED project requirement via DEC-0020 and:
`00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`.

Exact form remains open: web app vs desktop vs hybrid, database/CMS/API/sync architecture, roles implementation, analytics stack and AI/provider choices are NOT decided.

Current mobile visual work continues. Before final Gate 3 -> 4 readiness, a targeted Internal Data/Content Operations requirements + workflow/screen-architecture addendum must be completed so Phase 4 evaluates the whole product system, not only mobile.

## Current Phase 3 Sequence

1. Brand / logo / anchor UX / visual — DONE.
2. Screen architecture + screen-family specs — DONE / APPROVED.
3. Five-tab navigation + AI Usta A1 — DONE / APPROVED.
4. Five-tab root visuals — DONE / APPROVED.
5. Guide Discovery / Fit / Preparation — DONE / APPROVED WITH CONSTRAINTS.
6. Active Application / Safety / Recovery — DONE / APPROVED WITH CONSTRAINTS.
7. Diagnosis — **DONE / G01–G04 APPROVED WITH CONSTRAINTS.**
8. **FAM-05 Maintenance / Reminder visual references — READY / CURRENT.**
9. Remaining critical mobile screen/state visual references.
10. Targeted Internal Data & Content Operations requirements/workflow/screen-architecture addendum — REQUIRED BEFORE GATE 3 REVIEW.
11. Gate 3 -> 4 readiness review.

## Current Prompt

**USE NOW:**
`03_DESIGN/PHASE3_MAINTENANCE_REMINDER_VISUAL_REFERENCES_AI_PROMPT.md`

Existing approved R02 Bakim root is H01 and must NOT be redesigned.
Generate exactly 3 new visuals:
- H02 — `SCR-023 Maintenance Item / Reminder Detail`
- H03 — `SCR-024 Catch-Up & Critical Priorities`
- H04 — `SCR-022/023 Maintenance Timing Uncertain`

Required attachments:
- `Kavriva_L05A.png`
- selected V10 screenshot
- `R02-Bakim.png`
- `D02-SCR-010-Guide-Scope-Fit.png`

Maintenance protections:
- no invented km/time/date/interval,
- postpone/snooze != completion,
- maintenance item must have explicit `Bakimi yap / Rehberi ac` connection to trusted guide flow,
- uncertain timing remains uncertain rather than guessed,
- catch-up prioritizes safety/use impact before mere lateness,
- no notification flood or dashboard/KPI treatment.

## Still Open — Not Errors

Mobile/design:
- active physical-work exact bottom-bar visibility,
- first post-onboarding landing tab,
- ambiguous screen/sheet/modal mappings,
- final icons/tokens/components/dark mode,
- exact claim/evidence visual vocabulary,
- optional AI Usta conversational capabilities beyond A1 root,
- exact community contribution CTA weight.

Internal operations / later strategy:
- web vs desktop vs hybrid internal surface,
- exact data-management architecture and schema,
- CMS/database/search/API/sync choices,
- content/reviewer role implementation,
- publishing/versioning/rollback mechanics,
- operational analytics stack,
- AI/model/provider use for research or content operations.

Technology/backend/AI architecture and pricing/tier/quota remain outside Phase 3.

## Gate Status

Gate 3 -> 4 HENUZ GECILMEDI.

Remaining critical mobile visual coverage AND the newly approved Internal Data/Content Operations requirements/workflow addendum must be sufficiently covered before Gate 3 readiness review.

## Last Refreshed

2026-09-16
