# DOCUMENT REGISTRY

Bu dosya kritik belgelerin nerede yasadigini ve otorite seviyesini listeler.

Status degerleri: `EMPTY`, `DRAFT`, `REVIEW`, `APPROVED`, `LOCKED`, `SUPERSEDED`, `ARCHIVED`.

| Alan | Ana belge | Status |
|---|---|---|
| Hafiza / kontrol | `00_CONTROL/*` | APPROVED |
| Calisma sistemi | `01_WORKSPACE/*` | REVIEW |
| Urun kesfi | `02_DISCOVERY/*` | EMPTY |
| Tasarim | `03_DESIGN/*` | EMPTY |
| Teknoloji tartismasi | `04_TECH_STRATEGY/*` | EMPTY |
| ADR | `05_ADR/*` | EMPTY |
| Teslimat planlama | `06_DELIVERY_PLANNING/*` | EMPTY |
| AI-native mimari | `07_AI_ARCHITECTURE/*` | EMPTY |
| Repository bootstrap | `08_REPOSITORY_BOOTSTRAP/*` | EMPTY |

`01_WORKSPACE` Phase-1 delegated synthesis ile dolduruldu ve proje yoneticisi tarafindan siniflandirma kalite kontrolunden gecirildi. Kullanici acik onayi verilmeden `APPROVED` yapilmayacak ve Gate 1 -> 2 gecilmeyecek.

Bu tablo her gate gecisinde guncellenir.
