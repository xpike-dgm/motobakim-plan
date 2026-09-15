# 03 — DESIGN

Amac: Discovery source-of-truth'undan Kavriva'nin marka kimligini, user-approved UX/visual direction'larini, ekran/state envanterini ve reference sistemini kontrollu sirayla olusturmaktir.

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
10. Full screen inventory + navigation + critical state coverage — **MAIN-MANAGER QA DONE / USER REVIEW REQUIRED**
11. Screen-family principles + screen specifications — **BLOCKED pending inventory approval**
12. Screen-by-screen visual references + user approval
13. Gate 3 -> 4 readiness review

## Approved Working References

### Brand
**Kavriva** — APPROVED working consumer-facing brand.

Canonical:
- `BRAND_NAME.md`
- DEC-0012

### Logo
**L05A — The Precision Fit** — APPROVED working direction.

Canonical:
- `LOGO_DIRECTION.md`
- DEC-0013
- `REFERENCE_INDEX.md` -> `REF-BRAND-001`

### Anchor UX
**U04 — Progressive Detail** — APPROVED working anchor UX.

Canonical:
- `ANCHOR_UX_STRUCTURE.md`
- DEC-0014
- `REFERENCE_INDEX.md` -> `REF-UX-001`

Core principle:
**Accessible does not mean simultaneously prominent.**

### Anchor Visual
**V10 — Signature Kavriva** — APPROVED working visual direction.

Canonical:
- `ANCHOR_VISUAL_STYLE.md`
- DEC-0015
- `REFERENCE_INDEX.md` -> `REF-VISUAL-001`

Important V10 constraints:
- exact HEX values final production tokens degil,
- shield/check canonical trust/safety badge degil,
- generated mechanical image verified motorcycle-specific evidence degil,
- exact font/spacing/radii/responsive/dark-theme behavior final degil,
- V10 universal full-app layout degil.

## Screen Inventory — Current Review Set

Main-manager review:
- `SCREEN_INVENTORY_REVIEW.md`
- result: `PASS_WITH_REFINEMENTS — USER APPROVAL REQUIRED`

Canonical review artifacts:
- `SCREEN_CATALOG.md` — REVIEW
- `NAVIGATION_MAP.md` — REVIEW
- `STATE_MATRIX.md` — REVIEW
- `DESIGN_PRINCIPLES.md` — REVIEW
- `SCREEN_COVERAGE_TRACEABILITY.md` — REVIEW

Current candidate inventory:
- delegated baseline: `SCR-001` — `SCR-037`,
- main-manager coverage addition: `SCR-038 — Community Experiences / Q&A`.

`SCR-*` IDs product interaction contexts'tir; permanent route sayisi degildir.

## Main-Manager Screen Inventory QA Notes

Passed:
- known-task, symptom-first, record-only, interruption/recovery, maintenance, history/dispute, inactive motorcycle, transfer/archive/delete, collaboration, migration ve entitlement-preserved-access coverage,
- critical states including teaching-only, safety hold, mismatch, insufficient evidence, material guide change, partial/unresolved, re-review, downgrade,
- U04/V10'un universal template'e donusturulmemesi,
- global navigation / technical routing / technology / pricing finalization yapilmamasi.

Refinement:
- community contribution/moderation vardi fakat published community Q&A/experience consumption context'i allocation almamisti; `SCR-038` eklendi.

Explicitly still open design mappings:
- global nav shell,
- full-screen vs sheet/modal/inline,
- notification control placement,
- accessibility modality preference placement,
- language/unit preference placement if user-configurable,
- historical claim-state visual vocabulary.

Generic Settings screen source olmadan uydurulmaz.

## Design Reference Authority

`REFERENCE_INDEX.md` icindeki APPROVED/LOCKED references gorsel/UX authority'dir.

Current approved references:
- `REF-BRAND-001` -> L05A,
- `REF-UX-001` -> U04 anchor hierarchy,
- `REF-VISUAL-001` -> V10 working visual direction.

Screen architecture artifacts henuz `REVIEW`; user approval sonrasi source-of-truth authority seviyesine tasinabilir.

## Scope Restrictions

Design asamasi:
- Product Discovery requirement'larini sessizce degistiremez.
- U04'u universal layout yapamaz.
- V10'u exact final component/token system yapamaz.
- `SCR-*` count'u route count gibi yorumlayamaz.
- Technology/backend/database/API/auth/sync/framework secemez.
- Final pricing/tier/quota karari veremez.
- Screen inventory user approval olmadan APPROVED/LOCKED ilan edilemez.

Gate 3 -> 4 icin approved screen catalog, navigation map, important state coverage ve yeterli approved visual references gerekir.

## Current Next Action

User main-manager QA'den gecmis Screen Inventory architecture'i approve eder veya degisiklik ister.

Approval gelmeden screen-family/spec delegation promptu ACTIVE yapilmaz.
