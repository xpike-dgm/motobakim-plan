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
11. **Screen-family principles + screen specifications — CURRENT / READY**
12. Screen-by-screen visual references + user approval
13. Gate 3 -> 4 readiness review

## Approved Working References

- Brand: **Kavriva** — `BRAND_NAME.md`, DEC-0012.
- Logo: **L05A — The Precision Fit** — `REF-BRAND-001`, DEC-0013.
- Anchor UX: **U04 — Progressive Detail** — `REF-UX-001`, DEC-0014.
- Anchor visual: **V10 — Signature Kavriva** — `REF-VISUAL-001`, DEC-0015.
- Screen/state architecture: **Screen Inventory 01 + refinement** — `REF-ARCH-001`, DEC-0016.

## Approved Working Screen Architecture

Canonical:
- `SCREEN_CATALOG.md`
- `NAVIGATION_MAP.md`
- `STATE_MATRIX.md`
- `DESIGN_PRINCIPLES.md`
- `SCREEN_COVERAGE_TRACEABILITY.md`
- `SCREEN_INVENTORY_REVIEW.md`

Current catalog:
`SCR-001` — `SCR-038`.

These are product interaction contexts, not guaranteed permanent routes.

Still open for screen-family/spec work:
- global navigation shell,
- exact full-screen vs sheet/modal/inline mapping,
- routine notification control placement,
- language/unit preference placement if user-configurable,
- accessibility modality preference placement,
- exact historical trust/claim visual vocabulary,
- exact correction reach-back channel/cadence.

Generic Settings megascreen, dashboard/KPI home, marketplace home veya social feed convention ile uydurulmaz.

## Current Task

**USE NOW:**
`PHASE3_SCREEN_FAMILY_SPEC_AI_PROMPT.md`

Bu tur:
- `SCR-*` context'lerini 6–9 anlamli family'ye ayirir,
- family-level UX principles cikarir,
- SCR-001 — SCR-038 icin tek tek screen specification yazar,
- global navigation shell icin en fazla 3 PROPOSED option sunar,
- ambiguous surface treatments'i PROPOSED olarak degerlendirir,
- cross-cutting control placement ve trust/safety semantics'i rafine eder,
- mockup/image URETMEZ.

## Core Design Protections

- **Accessible does not mean simultaneously prominent.**
- U04 active-guide anchor authority'dir; universal full-app layout degildir.
- V10 visual-DNA reference'tir; universal layout/exact token system degildir.
- Shield/check generic trust/safety/certification badge degildir.
- Product semantics visual simplicity ugruna kaldirilamaz.
- Safety, provenance, uncertainty, recovery ve historical truth gereken context'te korunur.
- Screen/state architecture user approval olmadan degistirilemez; refinement controlled change ister.

## Scope Restrictions

Phase 3:
- technology/backend/database/API/auth/sync/framework secemez,
- pricing/tier/quota finalize edemez,
- final production component library secemez,
- mockup/reference user + main-manager review olmadan authority yapamaz,
- Gate 3 -> 4 kosullari tamamlanmadan Phase 4'e gecemez.

## Gate 3 -> 4

Gate 3 icin approved screen catalog/navigation/important states ve approved visual references gerekir. Bunlarin buyuk kismi mevcut olsa da screen specifications ve yeterli screen-by-screen visual references tamamlanmadan Gate 3 readiness review yapilmayacak.
