# MEMORY CHANGELOG

Bu dosya proje hafizasi, source-of-truth ve planlama sistemindeki anlamli degisikliklerin kronolojik kaydidir.

## 2026-09-14

### Memory System
- GitHub repository kalici proje hafizasi olarak belirlendi.
- `AI_START_HERE`, `CURRENT_STATE`, `SOURCE_OF_TRUTH`, `DECISION_LOG`, `OPEN_QUESTIONS`, `HANDOFF`, `MEMORY_PROTOCOL` kuruldu.

### Planning Workspace Scaffold
- Sekiz asamali workflow `WORKFLOW_MAP.md` ile kayda alindi.
- Asama gecisleri icin `PHASE_GATES.md` eklendi.
- Kritik belge durumlari icin `DOCUMENT_REGISTRY.md` eklendi.
- `01_WORKSPACE` ortak bilgi calisma alani olusturuldu.
- `02_DISCOVERY` soru batch, conflict ve synthesis yapisi olusturuldu.
- `03_DESIGN` screen catalog, navigation, state matrix ve reference index yapisi olusturuldu.
- `04_TECH_STRATEGY` uzman rolleri, evaluation, debate, judge ve risk yapisi olusturuldu.
- `05_ADR` karar kaydi alani olusturuldu.
- `06_DELIVERY_PLANNING` Epic -> Capability -> Feature -> User Flow -> Task yapisi olusturuldu.
- `07_AI_ARCHITECTURE` AI guvenli gelistirme mimarisi calisma belgeleri olusturuldu.
- `08_REPOSITORY_BOOTSTRAP` fiziksel kurulum/CI/quality gate yapisi olusturuldu.
- `90_TEMPLATES` standardize belge sablonlari ve `99_ARCHIVE` tarihsel kayit alani eklendi.

### Scalability Structure
- Ekranlar icin `03_DESIGN/SCREEN_SPECS/` tekil kayit alani eklendi.
- Teknik tartismalar icin `04_TECH_STRATEGY/DEBATES/` eklendi.
- ADR'ler icin `05_ADR/RECORDS/` eklendi.
- Planlama kayitlari `EPICS/`, `CAPABILITIES/`, `FEATURES/`, `FLOWS/`, `TASKS/` olarak ayrildi; kataloglar index olarak konumlandirildi.
- AI mimarisi icin `CONTRACTS/`, `CONTEXT_PACKS/`, `RULES/` tekil kayit alanlari eklendi.
- Bootstrap completion kanitlari icin `08_REPOSITORY_BOOTSTRAP/EVIDENCE/` eklendi.
- Capability, context pack, decision entry ve review checklist sablonlari eklendi.

### Decision Changes
- DEC-0003 SUPERSEDED yapildi.
- DEC-0004 ile sekiz asamali workflow LOCKED hale getirildi.
- DEC-0005 ile kanit/sentez/karar ayrimi LOCKED hale getirildi.
- DEC-0006 ile kullanici-facing discovery soru oturumlarinin diger AI'lara kontrollu promptlarla delege edilmesi LOCKED hale getirildi.

### Phase 1 Delegation
- `01_WORKSPACE/PHASE1_WORKSPACE_AI_PROMPT.md` olusturuldu.
- Prompt ilk 5 genel, teknik olmayan soruyu kapsayacak sekilde sinirlandi.
- Diger AI'nin cevaplardan PROJECT_VISION, CONSTRAINTS, ASSUMPTIONS, GLOSSARY ve OPEN QUESTIONS adaylari cikarmasi tanimlandi.
- Diger AI'nin kendiliginden 30 soruluk discovery turuna gecmesi yasaklandi; kontrol proje yoneticisinde tutuldu.

### Current State
Durum `PHASE-1 / WORKSPACE DISCOVERY DELEGATED` olarak guncellendi. Kullanici diger AI oturumundan ilk workspace discovery ciktisini getirecek; ChatGPT bunu kalite kontrolunden gecirip source-of-truth belgelerine isleyecek.
