# MEMORY CHANGELOG

Bu dosya proje hafizasi, source-of-truth ve planlama sistemindeki anlamli degisikliklerin kronolojik kaydidir.

## 2026-09-14

### Memory System
- GitHub repository kalici proje hafizasi olarak belirlendi.
- `AI_START_HERE`, `CURRENT_STATE`, `SOURCE_OF_TRUTH`, `DECISION_LOG`, `OPEN_QUESTIONS`, `HANDOFF`, `MEMORY_PROTOCOL` kuruldu.

### Planning Workspace Scaffold
- Sekiz asamali workflow ve phase gate sistemi kuruldu.
- `01_WORKSPACE` — `08_REPOSITORY_BOOTSTRAP`, template ve archive iskeletleri olusturuldu.

### Process Decisions
- DEC-0004 sekiz asamali workflow LOCKED.
- DEC-0005 kanit/sentez/karar ayrimi LOCKED.
- DEC-0006 kullanici-facing discovery oturumlarinin diger AI'lara kontrollu promptlarla delegasyonu LOCKED.
- DEC-0007 proje capi ortak chat talimatlari LOCKED.

### Phase 1 / Gate 1 -> 2
- Ilk 5 teknik olmayan discovery sorusu diger AI oturumunda yurutuldu.
- Phase-1 synthesis kalite kontrolunden gecirildi ve kullanici tarafindan onaylandi.
- Workspace source-of-truth belgeleri APPROVED yapildi.
- Gate 1 -> 2 tamamlandi.

### Product Discovery — Batch 01 Complete
- Q006-Q035 raw Q&A `SESSION-001_BATCH_01_Q006_Q035.md` icine verbatim kaydedildi.
- DRAFT synthesis katmani baslatildi.
- Assumptions, glossary ve open questions kanitla rafine edildi.
- Batch 02 adaptif promptu hazirlandi.

### Product Discovery — Batch 02 Complete
- Q036-Q065 raw Q&A `SESSION-002_BATCH_02_Q036_Q065.md` icine verbatim kaydedildi.
- Portable paketteki AI resolution adaylari otomatik kabul edilmedi; ham kanitla yeniden degerlendirildi.
- Variant/modification, content lifecycle, high-consequence kosullar, readiness, safe equivalent, diagnosis evidence, guide versioning, multi-motorcycle, external work, bakım priority ve monetization baseline derinlesti.
- Q040 ikinci review `guven sinyali` olarak korundu; global zorunluluk yapilmadi.
- Q063 fatura otomatik verified sayilmadi; Q065 fiyat/paket modeli secmedi.
- Synthesis/assumption/glossary/open-question dosyalari guncellendi.
- Batch 03 Q066-Q095 promptu hazirlandi.

### Product Discovery — Batch 03 Complete
- Kullanici `PORTABLE DISCOVERY HANDOFF PACKAGE — BATCH 03` dosyasini ana yonetici sohbetine getirdi.
- Q066-Q095 raw Q&A `02_DISCOVERY/SESSIONS/SESSION-003_BATCH_03_Q066_Q095.md` icine verbatim kaydedildi.
- Phase-1 ve Batch 01-02 kanitiyla dogrudan celiski tespit edilmedi.
- Q066-Q067, kullanicinin teknik kimlik/belge aramak istemedigi ve observable ozellik/fotograf yetersizse variant-specific uygulamali adimlarin acilmamasi beklentisini CONFIRMED etti; fotografin her gercek motosiklette teknik olarak yeterli olacagi feasibility gercegi yapilmadi.
- Q068-Q069 yuksek gerilim/basincli/yuksek-sicaklik gibi high-consequence alanlarin kategori olarak dislanmamasini fakat motosiklete ozel safety kosullari dogrulanmadan uygulamali progression olmamasini CONFIRMED etti.
- Notification grouping/cadence/user control, history edit trail/evidence levels, maintenance uncertainty/istisnalar, sure-maliyet transparency, community/moderation, commercial neutrality, roadside/offline, data ownership/export/delete ve trust-breaker'lar derinlesti.
- Q070 haftalik ozet tercihinin tek kullanici kaniti oldugu korundu; global LOCKED notification policy yapilmadi.
- Q074 evidence ornekleri global automatic verification taxonomy yapilmadi.
- Q087 premium deger ornekleri final premium package/model karari yapilmadi.
- `OPEN_QUESTIONS.md`: Q-0002, Q-0010, Q-0021 — Q-0025, Q-0028 ve Q-0029 ANSWERED; high-consequence professional escalation, premium packaging, broader segmentation ve yeni edge case'ler OPEN olarak korundu.
- `ASSUMPTIONS.md`: ASM-008 ve ASM-017 RESOLVED; ASM-018 SUPPORTED; ASM-013 OPEN; ASM-019 — ASM-021 yeni OPEN varsayimlar eklendi.
- `GLOSSARY.md` evidence level, belirsiz bakım takvimi, bakım istisnasi, degisiklik izi, community contribution, resmi rehber, ticari tarafsizlik, roadside/offline, data portability ve trust-breaker terimleriyle rafine edildi.
- `PRODUCT_MASTER`, `USER_TYPES`, `USER_JOURNEYS`, `BUSINESS_RULES`, `FEATURE_CANDIDATES`, `NON_GOALS` Batch 03 kanitiyla guncellendi.
- `QUESTION_PROGRESS.md` Batch 03 complete / Batch 04 ready yapildi.
- `02_DISCOVERY/BATCH_04_AI_PROMPT.md` Q096-Q125 icin adaptif olarak hazirlandi.

### Current State
Durum `PHASE-2 / PRODUCT DISCOVERY — BATCH 04 READY` olarak guncellenecek. Batch 05, Batch 04 ham kanit ve synthesis kalite kontrolunden gecmeden hazirlanmayacak; Phase 3'e gecilmeyecek.
