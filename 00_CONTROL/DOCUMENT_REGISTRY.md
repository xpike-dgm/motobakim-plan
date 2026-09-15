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

`03_DESIGN` aktif asamadir. Brand `Kavriva`, L05A working logo direction, U04 working anchor UX ve V10 working visual direction APPROVED reference seviyesindedir. Full screen inventory/navigation/state artifacts main-manager QA'den gecmis ve `REVIEW` durumuna tasinmistir:
- `03_DESIGN/SCREEN_CATALOG.md`
- `03_DESIGN/NAVIGATION_MAP.md`
- `03_DESIGN/STATE_MATRIX.md`
- `03_DESIGN/DESIGN_PRINCIPLES.md`
- `03_DESIGN/SCREEN_COVERAGE_TRACEABILITY.md`
- `03_DESIGN/SCREEN_INVENTORY_REVIEW.md`

Screen architecture explicit user approval beklemektedir. User approval olmadan screen-family/spec asamasina authority gecisi veya Gate 3 -> 4 yapilmaz.

Bu tablo her gate gecisinde veya review-state degisiminde guncellenir.
