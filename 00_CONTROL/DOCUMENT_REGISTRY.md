# DOCUMENT REGISTRY

Bu dosya kritik belgelerin nerede yasadigini ve otorite seviyesini listeler.

Status degerleri: `EMPTY`, `DRAFT`, `REVIEW`, `APPROVED`, `LOCKED`, `SUPERSEDED`, `ARCHIVED`.

| Alan | Ana belge | Status |
|---|---|---|
| Hafiza / kontrol | `00_CONTROL/*` | APPROVED |
| Calisma sistemi | `01_WORKSPACE/*` | APPROVED |
| Urun kesfi | `02_DISCOVERY/*` | APPROVED |
| Tasarim | `03_DESIGN/*` | REVIEW |
| Teknoloji tartismasi | `04_TECH_STRATEGY/*` | EMPTY |
| ADR | `05_ADR/*` | EMPTY |
| Teslimat planlama | `06_DELIVERY_PLANNING/*` | EMPTY |
| AI-native mimari | `07_AI_ARCHITECTURE/*` | EMPTY |
| Repository bootstrap | `08_REPOSITORY_BOOTSTRAP/*` | EMPTY |

`01_WORKSPACE` approved; Gate 1 -> 2 tamamlandi.

`02_DISCOVERY` Q006-Q245 raw evidence + approved synthesis snapshot ile APPROVED. Canonical entry point: `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`. Gate 2 -> 3 PASSED.

## Approved Project-Scope Addendum

- `00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md` — **APPROVED REQUIREMENT**
  - Internal motorcycle/technical Data & Content Operations capability is required.
  - Exact web/desktop/hybrid and technology architecture remain open.
  - Targeted requirements/workflow/screen-architecture addendum required before final Gate 3 review.

## Phase-3 Design

`03_DESIGN` aktif asamadir ve Phase-3 butunu tamamlanmadigi icin registry seviyesi `REVIEW` kalir.

Approved working design authorities:
- `BRAND_NAME.md` — Kavriva
- `LOGO_DIRECTION.md` — L05A
- `ANCHOR_UX_STRUCTURE.md` — U04
- `ANCHOR_VISUAL_STYLE.md` — V10
- `SCREEN_CATALOG.md`
- `NAVIGATION_MAP.md`
- `STATE_MATRIX.md`
- `DESIGN_PRINCIPLES.md`
- `SCREEN_COVERAGE_TRACEABILITY.md`
- `GLOBAL_NAVIGATION.md` — 5-tab bottom bar
- `SCREEN_FAMILY_SPECS.md`
- `SCREEN_FAMILY_SPEC_REVIEW.md`
- `AI_USTA_UX_STRUCTURE.md`
- `KAVRIVA_AI_USTA_UX_STRUCTURE_REVIEW.md`
- `MAIN_SHELL_VISUAL_REFERENCES.md`
- `KAVRIVA_MAIN_SHELL_VISUALS_REVIEW.md`
- `GUIDE_DISCOVERY_FIT_PREPARATION_VISUAL_REFERENCES.md`
- `KAVRIVA_GUIDE_DISCOVERY_FIT_PREPARATION_VISUALS_REVIEW.md`
- `ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md`
- `KAVRIVA_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUALS_REVIEW.md`
- `DIAGNOSIS_VISUAL_REFERENCES.md`
- `KAVRIVA_DIAGNOSIS_VISUALS_REVIEW.md`
- `MAINTENANCE_REMINDER_VISUAL_REFERENCES.md`
- `KAVRIVA_MAINTENANCE_REMINDER_VISUALS_REVIEW.md`

`REFERENCE_INDEX.md` approved references:
`REF-BRAND-001`, `REF-UX-001`, `REF-VISUAL-001`, `REF-ARCH-001`, `REF-NAV-001`, `REF-SPEC-001`, `REF-AIUSTA-001`, `REF-SHELL-001`, `REF-GUIDE-001`, `REF-ACTIVE-001`, `REF-DIAG-001`, `REF-MAINT-001`.

## Current Phase-3 Task

**FAM-06 History / Evidence / Trust visual references**.

Active prompt:
`03_DESIGN/PHASE3_HISTORY_EVIDENCE_TRUST_VISUAL_REFERENCES_AI_PROMPT.md`.

Existing R04 Gecmis root is I01; generate I02–I06 only.

Phase 4'e Gate 3 saglanmadan gecilmez. Remaining critical mobile visual references and the Internal Data/Content Operations requirements/workflow addendum must be covered before Gate 3 readiness review.

Bu tablo her gate gecisinde veya review-state degisiminde guncellenir.
