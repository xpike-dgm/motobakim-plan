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

`01_WORKSPACE` Phase-1 sentezi kullanici tarafindan 2026-09-14 tarihinde acikca onaylandi ve Gate 1 -> 2 gecisi tamamlandi.

`02_DISCOVERY` Q006-Q245 raw evidence + approved synthesis snapshot ile 2026-09-15 tarihinde kullanici tarafindan APPROVED edildi. Canonical entry point: `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`. Gate 2 -> 3 PASSED.

`03_DESIGN` aktif asamadir ve Phase-3 butunu tamamlanmadigi icin registry seviyesi `REVIEW` kalir. Bununla birlikte asagidaki design artifacts tekil olarak APPROVED working authority'dir:
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
- `SCREEN_FAMILY_SPECS.md` — working UX specs
- `SCREEN_FAMILY_SPEC_REVIEW.md` — approved QA record
- `AI_USTA_UX_STRUCTURE.md` — A1 Guided Split working AI Usta root UX
- `KAVRIVA_AI_USTA_UX_STRUCTURE_REVIEW.md` — approved QA record
- `MAIN_SHELL_VISUAL_REFERENCES.md` — R01–R05 approved working root visual family
- `KAVRIVA_MAIN_SHELL_VISUALS_REVIEW.md` — root-set main-manager QA
- `GUIDE_DISCOVERY_FIT_PREPARATION_VISUAL_REFERENCES.md` — D01–D05 approved working visual family
- `KAVRIVA_GUIDE_DISCOVERY_FIT_PREPARATION_VISUALS_REVIEW.md` — guide-family main-manager QA
- `REFERENCE_INDEX.md` -> `REF-BRAND-001`, `REF-UX-001`, `REF-VISUAL-001`, `REF-ARCH-001`, `REF-NAV-001`, `REF-SPEC-001`, `REF-AIUSTA-001`, `REF-SHELL-001`, `REF-GUIDE-001`

Current Phase-3 task:
**Active Application / Safety / Recovery visual references — E01–E05 candidate set generated; user review required**.

Active prompt:
`03_DESIGN/PHASE3_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES_AI_PROMPT.md`.

Review-stage artifact — not yet approved authority:
- `03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-ACTIVE-CANDIDATE-001` (`REVIEW`)
- candidate PNGs: `03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/`

Phase 4'e Gate 3 saglanmadan gecilmez.

Bu tablo her gate gecisinde veya review-state degisiminde guncellenir.
