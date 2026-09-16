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

Approved working consumer-facing brand name:
- `03_DESIGN/BRAND_NAME.md`
- DEC-0012

Approved working logo direction:
- `03_DESIGN/LOGO_DIRECTION.md`
- DEC-0013
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-BRAND-001`

Approved working anchor UX:
- `03_DESIGN/ANCHOR_UX_STRUCTURE.md`
- DEC-0014
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-UX-001`

Approved working anchor visual direction:
- `03_DESIGN/ANCHOR_VISUAL_STYLE.md`
- DEC-0015
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-VISUAL-001`

Approved working screen/state architecture:
- `03_DESIGN/SCREEN_CATALOG.md`
- `03_DESIGN/NAVIGATION_MAP.md`
- `03_DESIGN/STATE_MATRIX.md`
- `03_DESIGN/DESIGN_PRINCIPLES.md`
- `03_DESIGN/SCREEN_COVERAGE_TRACEABILITY.md`
- DEC-0016
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-ARCH-001`

Approved global navigation shell:
- `03_DESIGN/GLOBAL_NAVIGATION.md`
- DEC-0017
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-NAV-001`

Approved working screen-family / UX specifications:
- `03_DESIGN/SCREEN_FAMILY_SPECS.md`
- `03_DESIGN/SCREEN_FAMILY_SPEC_REVIEW.md`
- DEC-0017
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-SPEC-001`

Approved working AI Usta root UX structure:
- `03_DESIGN/AI_USTA_UX_STRUCTURE.md`
- DEC-0018
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-AIUSTA-001`

Approved working five-tab root visual family:
- `03_DESIGN/MAIN_SHELL_VISUAL_REFERENCES.md`
- `03_DESIGN/KAVRIVA_MAIN_SHELL_VISUALS_REVIEW.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-SHELL-001`
- approval evidence: explicit user feedback `hepsi iyi`

Approved working Guide Discovery / Fit / Preparation visual family:
- `03_DESIGN/GUIDE_DISCOVERY_FIT_PREPARATION_VISUAL_REFERENCES.md`
- `03_DESIGN/KAVRIVA_GUIDE_DISCOVERY_FIT_PREPARATION_VISUALS_REVIEW.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-GUIDE-001`
- acceptance evidence: user feedback `geneol olarak iyi`

AI Usta evidence / review:
- `03_DESIGN/KAVRIVA_AI_USTA_UX_STRUCTURE_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_AI_USTA_UX_STRUCTURE_REVIEW.md`

Main-shell evidence / review:
- `03_DESIGN/KAVRIVA_MAIN_SHELL_VISUALS_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_MAIN_SHELL_VISUALS_REVIEW.md`

Guide-family evidence / review:
- `03_DESIGN/KAVRIVA_GUIDE_DISCOVERY_FIT_PREPARATION_VISUALS_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_GUIDE_DISCOVERY_FIT_PREPARATION_VISUALS_REVIEW.md`

Review-stage candidate evidence — not approved authority:
- `03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-ACTIVE-CANDIDATE-001` (`REVIEW`)
- E01 preserves approved V10; E02-E05 require explicit user acceptance before approval integration.

Other evidence / review artifacts:
- `KAVRIVA_LOGO_01_HANDOFF.md`
- `KAVRIVA_LOGO_REVIEW.md`
- `KAVRIVA_ANCHOR_UX_STRUCTURE_01_HANDOFF.md`
- `KAVRIVA_ANCHOR_UX_STRUCTURE_REVIEW.md`
- `KAVRIVA_ANCHOR_VISUAL_STYLE_01_HANDOFF.md`
- `KAVRIVA_ANCHOR_VISUAL_STYLE_REVIEW.md`
- `SCREEN_INVENTORY_REVIEW.md`
- `SCREEN_FAMILY_SPEC_REVIEW.md`

Authority boundaries:
- L05A concept/direction authority'dir; production vector/font/palette/trademark clearance degildir.
- U04 active-guide anchor hierarchy authority'dir; universal full-app template degildir.
- V10 visual-DNA authority'dir; exact HEX/font/icon/spacing veya universal layout degildir.
- Screen architecture `SCR-001` — `SCR-038` product interaction contexts'ini tanimlar; permanent route count degildir.
- Five-tab navigation approved: **Garaj · Bakim · AI Usta · Gecmis · Topluluk**.
- `AI Usta` UX role/entry label'idir; LLM/provider/backend/AI architecture karari degildir ve product trust/safety gates'i bypass edemez.
- AI Usta root structure approved: **A1 — Guided Split**; compact motorcycle context + `Nasil yardimci olayim?` + `Bir is yapmak istiyorum` / `Motorda bir sorun var`. Known-task `SCR-009`, symptom-first `SCR-019` flow'una controlled handoff yapar.
- A1 root free-form technical-answer/chat-home authority'si vermez; unsupported diagnosis/value/specification uretimi veya fit/readiness/safety bypass'i yasaktir.
- `REF-SHELL-001` R01–R05 root visual family'yi working reference yapar; exact icon glyphs, production tokens, exact header geometry, R03 decorative image requirement'i ve R05 contribution CTA prominence'i final yapmaz.
- `REF-GUIDE-001` D01–D05 Guide Discovery / Fit / Preparation visual family'yi working reference yapar.
- D03 `Uygulamaya hazir` statusu yalniz mandatory/critical readiness gercekten dogrulanmissa kullanilabilir; pending/unknown/stale/failed critical condition ready sayilamaz.
- D01–D05'te image generation tarafindan uretilen blue K-like mark yeni logo authority DEGILDIR; L05A `REF-BRAND-001` gecerlidir.
- D03 generated tools/materials/optional examples technical truth DEGILDIR; production requirement classification task-specific validated source'tan gelmelidir.
- D02 fit/trust fixture copy real evidence olmadan kullanilamaz.
- D01/D02 visible bottom bar ve D03–D05 reduced navigation exact routing/navigation karari degildir.
- Generated motorcycle imagery identity/fit/diagnosis evidence degildir.
- Community wording gercekte desteklenmeyen authenticity/verification iddiasi yaratamaz.
- Screen-family specs default hierarchy/action/trust/safety behavior'ini authorize eder; ambiguous sheet/modal/full-screen treatments'in bir kismi hala PROPOSED kalir.
- Language/unit/accessibility support profile/account prerequisite olamaz.

Ekran/gorsel otorite `REFERENCE_INDEX.md` icindeki APPROVED/LOCKED references ile kurulur.

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

Kabul edilmis bilgi degisiyorsa eski karar iz birakmadan silinmez. Yeni kayit eskisini SUPERSEDED/refined eder ve degisiklik changelog'a islenir.
