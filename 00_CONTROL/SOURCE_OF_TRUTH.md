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
Approved working consumer-facing brand name source'u:
- `03_DESIGN/BRAND_NAME.md`
- DEC-0012

Approved working logo-direction source'u:
- `03_DESIGN/LOGO_DIRECTION.md`
- DEC-0013
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-BRAND-001`

Approved working anchor-UX source'u:
- `03_DESIGN/ANCHOR_UX_STRUCTURE.md`
- DEC-0014
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-UX-001`

Approved working anchor visual-direction source'u:
- `03_DESIGN/ANCHOR_VISUAL_STYLE.md`
- DEC-0015
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-VISUAL-001`

Logo evidence / review:
- `03_DESIGN/KAVRIVA_LOGO_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_LOGO_REVIEW.md`

Anchor UX evidence / review:
- `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_REVIEW.md`

Anchor visual evidence / review:
- `03_DESIGN/KAVRIVA_ANCHOR_VISUAL_STYLE_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_ANCHOR_VISUAL_STYLE_REVIEW.md`

L05A approval concept/direction seviyesindedir; generated PNG production vector asset, final font/palette/app-icon geometry veya trademark-cleared mark degildir.

U04 approval anchor calibration hierarchy seviyesindedir; final screen catalog/navigation/state architecture veya universal full-app template degildir.

V10 approval working visual-direction seviyesindedir; exact HEX values, final font/type scale, final icon family, responsive rules, production photography veya universal full-app layout degildir. Selected V10 screenshot'taki shield/check trust/safety iconography canonical component semantics sayilmaz.

Ekran gercegi `SCREEN_CATALOG.md`, `STATE_MATRIX.md`, `NAVIGATION_MAP.md` ile kurulur. Gorsel otorite `REFERENCE_INDEX.md` icindeki APPROVED/LOCKED referanslardir.

Naming evidence / review:
- `BRAND_NAME_01_HANDOFF.md`
- `BRAND_NAME_REVIEW.md`

Naming research legal trademark clearance yerine gecmez.

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
