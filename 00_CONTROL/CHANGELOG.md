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
- `03_DESIGN`, `04_TECH_STRATEGY`, `05_ADR`, `06_DELIVERY_PLANNING`, `07_AI_ARCHITECTURE`, `08_REPOSITORY_BOOTSTRAP` iskeletleri kuruldu.
- Tekil kayit alanlari, template'ler ve archive alani eklendi.

### Process Decisions
- DEC-0004 ile sekiz asamali workflow LOCKED hale getirildi.
- DEC-0005 ile kanit/sentez/karar ayrimi LOCKED hale getirildi.
- DEC-0006 ile kullanici-facing discovery oturumlarinin diger AI'lara kontrollu promptlarla delege edilmesi LOCKED hale getirildi.
- DEC-0007 ile proje capi ortak chat talimatlari LOCKED hale getirildi.

### Phase 1 Delegation and Review
- `01_WORKSPACE/PHASE1_WORKSPACE_AI_PROMPT.md` olusturuldu.
- Ilk 5 genel, teknik olmayan soru baska AI oturumunda soruldu.
- Kullanici yapilandirilmis Phase-1 sentezini ana yonetici sohbetine getirdi.
- `PROJECT_VISION`, `CONSTRAINTS`, `ASSUMPTIONS`, `GLOSSARY` kalite kontrolunden gecirildi.
- Feature gereksinimleri constraint katmanindan ayrildi.
- Tehlikeli/uzmanlik gerektiren islemler kullanici niyeti olarak korundu; kosulsuz urun politikasi yapilmadi.
- 12 acik urun sorusu `OPEN_QUESTIONS.md` icine kaydedildi.

### Phase 1 Approval / Gate 1 -> 2
- Kullanici duzeltilmis Phase-1 workspace sentezini acikca onayladi.
- DEC-0008 eklendi.
- `01_WORKSPACE/PROJECT_VISION.md` `APPROVED` yapildi.
- `01_WORKSPACE/CONSTRAINTS.md` `APPROVED` yapildi.
- `01_WORKSPACE/ASSUMPTIONS.md` registry `APPROVED` yapildi; tekil varsayimlar ayrica izlenir.
- `01_WORKSPACE/GLOSSARY.md` registry `APPROVED` yapildi; `PROPOSED` terimler nihai sayilmadi.
- `DOCUMENT_REGISTRY.md` icinde `01_WORKSPACE/*` = `APPROVED` oldu.
- Gate 1 -> 2 tamamlandi.

### Phase 2 Product Discovery Start
- `02_DISCOVERY/SESSIONS/SESSION-000_GENERAL_BASELINE.md` olusturuldu.
- Q001-Q005 ham transkriptinin repository'de bulunmadigi provenance limitation olarak kaydedildi.
- Sonraki batch'lerde `RAW Q&A — VERBATIM` portable handoff paketinin zorunlu parcasi yapildi.
- `02_DISCOVERY/BATCH_01_AI_PROMPT.md` olusturuldu; soru araligi Q006-Q035 olarak belirlendi.

### Product Discovery — Batch 01 Complete
- Q006-Q035 raw Q&A `SESSION-001_BATCH_01_Q006_Q035.md` icine verbatim kaydedildi.
- Phase-1 baseline ile dogrudan celiski tespit edilmedi.
- Delegated AI'nin siniflandirma ve resolution adaylari ana proje yoneticisi tarafindan yeniden degerlendirildi.
- `PRODUCT_MASTER`, `USER_TYPES`, `USER_JOURNEYS`, `BUSINESS_RULES`, `FEATURE_CANDIDATES`, `NON_GOALS` DRAFT sentezleri olusturuldu.
- `ASSUMPTIONS` ve `GLOSSARY` Batch 01 kanitiyla rafine edildi.
- Open questions yeniden duzenlendi ve `BATCH_02_AI_PROMPT.md` Q036-Q065 icin adaptif olarak hazirlandi.

### Product Discovery — Batch 02 Complete
- Kullanici `PORTABLE DISCOVERY HANDOFF PACKAGE — BATCH 02` dosyasini ana yonetici sohbetine getirdi.
- Q036-Q065 raw Q&A `02_DISCOVERY/SESSIONS/SESSION-002_BATCH_02_Q036_Q065.md` icine verbatim kaydedildi.
- Phase-1 ve Batch-01 kanitiyla dogrudan celiski tespit edilmedi.
- Portable paketteki `ANSWERED/RESOLVED` adaylari otomatik kabul edilmedi; ham kanit uzerinden yeniden degerlendirildi.
- Q036'daki kimlik alanlari evrensel sabit set olarak kilitlenmedi; islem/malzeme/guvenlik farki yaratan ilgili versiyonun kesinlesmesi ust ilke olarak korundu.
- Q040'taki bagimsiz ikinci inceleme `guven sinyali` olarak kaydedildi; tum kritik rehberlerde zorunlu iki-reviewer politikasi yapilmadi.
- Q045 tum sistemleri ogrenme istegi kosulsuz self-service iznine genisletilmedi.
- Q056 sabit nicel teshis kanit esigine donusturulmedi.
- Q063'te fatura tek basina otomatik dogrulanmis dis islem kaniti sayilmadi.
- Q065 ucretli/ucretsiz deger sinirini netlestirdi fakat fiyatlandirma/paketleme modeli secilmedi.
- `PRODUCT_MASTER`, `USER_TYPES`, `USER_JOURNEYS`, `BUSINESS_RULES`, `FEATURE_CANDIDATES`, `NON_GOALS` Batch 02 ile guncellendi.
- `ASSUMPTIONS.md`: ASM-006, ASM-009, ASM-010, ASM-011, ASM-012 RESOLVED; ASM-013 — ASM-018 yeni acik varsayimlar olarak eklendi.
- `GLOSSARY.md` content lifecycle, readiness, dis islem, bakim onceligi ve benzeri terimlerle rafine edildi.
- `OPEN_QUESTIONS.md`: Q-0003, Q-0013 — Q-0019 ve Q-0020 ANSWERED yapildi; kismi ve yeni bosluklar dar acik sorularla korundu.
- `QUESTION_PROGRESS.md` Batch 02 tamamlandi / Batch 03 hazir durumuna getirildi.
- `02_DISCOVERY/BATCH_03_AI_PROMPT.md` Q066-Q095 icin adaptif olarak hazirlandi.

### Current State
Durum `PHASE-2 / PRODUCT DISCOVERY — BATCH 03 READY` olarak guncellendi. Batch 04, Batch 03 ham kanit ve sentezi kalite kontrolunden gecmeden hazirlanmayacak; Phase 3'e gecilmeyecek.
