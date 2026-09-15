# SOURCE OF TRUTH

Bu belge hangi bilginin hangi otorite seviyesinde oldugunu tanimlar.

## Genel Otorite Sirasi

1. Kullanicinin en yeni ve acik talimati
2. `LOCKED` kararlar / ADR'ler / onayli referanslar
3. `APPROVED` source-of-truth belgeleri
4. `00_CONTROL/CURRENT_STATE.md`
5. Diger aktif repository belgeleri
6. Ham kanit / tartisma kayitlari
7. Gecmis sohbetler
8. AI'nin kendi hatirladigi, varsaydigi veya cikarsadigi bilgi

## Global Kontrol Kaynaklari

- `AI_START_HERE.md` — oturum bootstrap protokolu
- `CURRENT_STATE.md` — guncel durum
- `DECISION_LOG.md` — surec ve proje yonetim kararlari
- `OPEN_QUESTIONS.md` — cozulmemis celiski/belirsizlikler
- `WORKFLOW_MAP.md` — 8 asamanin sirasi
- `PHASE_GATES.md` — asamalar arasi gecis kosullari
- `DOCUMENT_REGISTRY.md` — ana belgelerin status kaydi
- `CHANGELOG.md` — hafiza/source-of-truth degisiklik izi
- `HANDOFF.md` — yeni AI icin kisa devir ozeti

## Asama Bazli Otorite

### 01 Workspace
`PROJECT_VISION.md`, `CONSTRAINTS.md`, `ASSUMPTIONS.md`, `GLOSSARY.md`. Varsayimlar gercek sayilmaz.

### 02 Discovery
`SESSIONS/` ham kanittir. Phase-2 approved product truth entry point'i `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md` dosyasidir. Bu belge onaylanan synthesis snapshot'ini ve hangi blob'larin birlikte okunacagini tanimlar. Working synthesis dosyalarinin sonraki degisiklikleri, controlled approval/supersession olmadan approved snapshot'i otomatik degistirmez.

### 03 Design
Ekran gercegi `SCREEN_CATALOG.md`, `STATE_MATRIX.md`, `NAVIGATION_MAP.md`; gorsel otorite `REFERENCE_INDEX.md` icindeki APPROVED/LOCKED referanslardir.

### 04 Tech Strategy
Tartisma ve oneridir. Tek basina kesin teknoloji karari olamaz.

### 05 ADR
Teknoloji/mimari kararlarinin gerekceli otoritesidir. APPROVED/LOCKED ADR'ler sonraki teknik planlamayi baglar.

### 06 Delivery Planning
Onayli epic/capability/feature/flow/task ve dependency haritalarinin otoritesidir.

### 07 AI Architecture
Kodlama sirasinda AI davranisi, context routing, module boundary, contract, validation, migration ve rollback kurallarinin otoritesidir.

### 08 Repository Bootstrap
Kesinlesen mimarinin fiziksel kurulum plani ve completion kanitlarinin otoritesidir.

## No Silent Rewrite

Kabul edilmis bilgi degisiyorsa eski karar iz birakmadan silinmez. Yeni kayit eskisini SUPERSEDED yapar ve degisiklik changelog'a islenir.
