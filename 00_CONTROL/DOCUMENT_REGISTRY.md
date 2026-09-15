# DOCUMENT REGISTRY

Bu dosya kritik belgelerin nerede yasadigini ve otorite seviyesini listeler.

Status degerleri: `EMPTY`, `DRAFT`, `REVIEW`, `APPROVED`, `LOCKED`, `SUPERSEDED`, `ARCHIVED`.

| Alan | Ana belge | Status |
|---|---|---|
| Hafiza / kontrol | `00_CONTROL/*` | APPROVED |
| Calisma sistemi | `01_WORKSPACE/*` | APPROVED |
| Urun kesfi | `02_DISCOVERY/*` | APPROVED |
| Tasarim | `03_DESIGN/*` | DRAFT |
| Teknoloji tartismasi | `04_TECH_STRATEGY/*` | EMPTY |
| ADR | `05_ADR/*` | EMPTY |
| Teslimat planlama | `06_DELIVERY_PLANNING/*` | EMPTY |
| AI-native mimari | `07_AI_ARCHITECTURE/*` | EMPTY |
| Repository bootstrap | `08_REPOSITORY_BOOTSTRAP/*` | EMPTY |

`01_WORKSPACE` Phase-1 sentezi kullanici tarafindan 2026-09-14 tarihinde acikca onaylandi ve Gate 1 -> 2 gecisi tamamlandi.

`02_DISCOVERY` Q006-Q245 raw evidence + approved synthesis snapshot ile 2026-09-15 tarihinde kullanici tarafindan APPROVED edildi. Canonical entry point: `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`. Gate 2 -> 3 PASSED.

`03_DESIGN` aktif asamadir. Ana screen/navigation/state artifacts henuz doldurulmamistir; ilk kontrollu screen-inventory promptu hazirlanarak Design DRAFT baslatilir. Phase 4'e Gate 3 saglanmadan gecilmez.

Bu tablo her gate gecisinde veya review-state degisiminde guncellenir.
