# 03 — DESIGN

Amac: Discovery source-of-truth'undan Kavriva'nin marka kimligini, user-approved UX/visual direction'larini, ekran/state mimarisini ve screen specifications'i kontrollu sirayla olusturmaktir.

## Current Phase 3 Sequence

1. Brand naming exploration — **DONE**
2. Brand-name selection + second-pass validation — **DONE**
3. Kavriva explicit brand-name approval — **DONE**
4. Logo exploration Round 01 + Round 02 — **DONE**
5. Logo selection / main-manager QA — **DONE: L05A working direction**
6. Anchor visual R2 attempt — **NOT ACCEPTED / DEPRECATED: UX clutter feedback**
7. Anchor UX Structure Calibration — **DONE**
8. U04 selection + main-manager QA — **DONE: U04 working anchor hierarchy**
9. Visual-style exploration with U04 fixed — **DONE: V10 working visual direction**
10. Full screen inventory + navigation + critical state coverage — **DONE / USER APPROVED**
11. Screen-family principles + screen specifications — **MAIN-MANAGER QA DONE / USER NAVIGATION DECISION REQUIRED**
12. Screen-by-screen visual references + user approval — **BLOCKED pending current decision**
13. Gate 3 -> 4 readiness review

## Approved Working References

- Brand: **Kavriva** — `BRAND_NAME.md`, DEC-0012.
- Logo: **L05A — The Precision Fit** — `REF-BRAND-001`, DEC-0013.
- Anchor UX: **U04 — Progressive Detail** — `REF-UX-001`, DEC-0014.
- Anchor visual: **V10 — Signature Kavriva** — `REF-VISUAL-001`, DEC-0015.
- Screen/state architecture: **Screen Inventory 01 + refinement** — `REF-ARCH-001`, DEC-0016.

## Screen Family + Specifications Review

Delegated package:
`PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / SCREEN FAMILY + SPECS 01`

Main-manager review:
- `SCREEN_FAMILY_SPEC_REVIEW.md`
- result: `PASS_WITH_REFINEMENTS — USER NAVIGATION DECISION REQUIRED`

Package 9 working family oneriyor:
- FAM-01 First Use / Motorcycle Context
- FAM-02 Guide Discovery / Fit / Preparation
- FAM-03 Active Application / Safety / Recovery
- FAM-04 Diagnosis
- FAM-05 Maintenance / Reminder
- FAM-06 History / Evidence / Trust
- FAM-07 Motorcycle Lifecycle / Entitlement
- FAM-08 Profile / Collaboration
- FAM-09 Community

Tum `SCR-001` — `SCR-038` coverage aliyor.

Main-manager refinement:
- language/unit ve accessibility davranislari profile/account prerequisite olamaz; account-light/local use'da da calismalidir.

## Global Navigation — Current Decision

Three PROPOSED options:
1. Motorcycle-Context-First
2. Task-First Launcher
3. Focused Hybrid

Working recommendation:
**Option 3 — Focused Hybrid**

Option 3 concept:
- compact active motorcycle context,
- ana alanlar: `Yap / Coz`, `Bakim`, `Gecmis`,
- motorcycle switch contextual control,
- lifecycle/profile/collaboration/community contextual / lower-prominence entry,
- generic dashboard yok.

This is NOT approved until explicit user selection.

## Core Design Protections

- **Accessible does not mean simultaneously prominent.**
- U04 active-guide anchor authority'dir; universal full-app layout degildir.
- V10 visual-DNA reference'tir; universal layout/exact token system degildir.
- Shield/check generic trust/safety/certification badge degildir.
- Product semantics visual simplicity ugruna kaldirilamaz.
- Safety, provenance, uncertainty, recovery ve historical truth gereken context'te korunur.
- Language/unit/accessibility presentation profile requirement'a baglanamaz.
- Generic Settings megascreen, dashboard/KPI home, marketplace home veya social feed convention ile uydurulmaz.

## Scope Restrictions

Phase 3:
- technology/backend/database/API/auth/sync/framework secemez,
- pricing/tier/quota finalize edemez,
- final production component library secemez,
- mockup/reference user + main-manager review olmadan authority yapamaz,
- Gate 3 -> 4 kosullari tamamlanmadan Phase 4'e gecemez.

## Next Action

User global navigation shell icin 1 / 2 / 3 secimi yapar.

Main-manager recommendation: **3 — Focused Hybrid**.

Selection sonrasi screen-family/spec package controlled approval'a alinabilir ve family-based screen-by-screen visual reference planlama promptu hazirlanabilir.
