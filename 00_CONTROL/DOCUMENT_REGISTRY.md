# DOCUMENT REGISTRY

Bu dosya kritik belgelerin nerede yasadigini ve otorite seviyesini listeler.

Status degerleri: `EMPTY`, `DRAFT`, `REVIEW`, `APPROVED`, `LOCKED`, `SUPERSEDED`, `ARCHIVED`.

| Alan | Ana belge | Status |
|---|---|---|
| Hafiza / kontrol | `00_CONTROL/*` | APPROVED |
| Calisma sistemi | `01_WORKSPACE/*` | APPROVED |
| Urun kesfi | `02_DISCOVERY/*` | REVIEW |
| Tasarim | `03_DESIGN/*` | EMPTY |
| Teknoloji tartismasi | `04_TECH_STRATEGY/*` | EMPTY |
| ADR | `05_ADR/*` | EMPTY |
| Teslimat planlama | `06_DELIVERY_PLANNING/*` | EMPTY |
| AI-native mimari | `07_AI_ARCHITECTURE/*` | EMPTY |
| Repository bootstrap | `08_REPOSITORY_BOOTSTRAP/*` | EMPTY |

`01_WORKSPACE` Phase-1 sentezi kullanici tarafindan 2026-09-14 tarihinde acikca onaylandi ve Gate 1 -> 2 gecisi tamamlandi.

`02_DISCOVERY` Q006-Q245 raw evidence ve working synthesis ile discovery saturation review seviyesine ulasti. `02_DISCOVERY/GATE_2_REVIEW.md` recommendation'i `READY_FOR_USER_APPROVAL` durumundadir. User approval olmadan discovery `APPROVED` sayilmaz ve Gate 2 -> 3 gecilmez.

Bu tablo her gate gecisinde veya review-state degisiminde guncellenir.
