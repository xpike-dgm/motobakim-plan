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
- DEC-0006 user-facing discovery oturumlarinin diger AI'lara kontrollu promptlarla delegasyonu LOCKED.
- DEC-0007 proje capi ortak chat talimatlari LOCKED.

### Phase 1 / Gate 1 -> 2
- Ilk 5 teknik olmayan discovery sorusu diger AI oturumunda yurutuldu.
- Phase-1 synthesis kalite kontrolunden gecirildi ve user tarafindan onaylandi.
- Workspace source-of-truth belgeleri APPROVED yapildi.
- Gate 1 -> 2 tamamlandi.

### Product Discovery — Batch 01 Complete
- Q006-Q035 raw Q&A `SESSION-001_BATCH_01_Q006_Q035.md` icine verbatim kaydedildi.
- DRAFT synthesis katmani baslatildi.
- Assumptions, glossary ve open questions kanitla rafine edildi.

### Product Discovery — Batch 02 Complete
- Q036-Q065 raw Q&A `SESSION-002_BATCH_02_Q036_Q065.md` icine verbatim kaydedildi.
- AI resolution adaylari automatic kabul edilmedi; raw evidence ile QC yapildi.
- Variant/modification, content lifecycle, high-consequence, readiness, safe equivalent, diagnosis evidence, guide versioning, multi-bike, external work, maintenance priority ve monetization baseline derinlesti.

### Product Discovery — Batch 03 Complete
- Q066-Q095 raw Q&A `SESSION-003_BATCH_03_Q066_Q095.md` icine verbatim kaydedildi.
- Observable variant evidence, high-consequence conditional learning/application, notification grouping, history evidence, maintenance uncertainty, time/cost transparency, community/moderation, commercial neutrality, roadside/offline, data ownership/export/delete ve trust-breakers derinlesti.

### Product Discovery — Batch 04 Complete
- Q096-Q125 raw Q&A `SESSION-004_BATCH_04_Q096_Q125.md` icine verbatim kaydedildi.
- Readiness false-positive icin evidence-based re-validation ve non-overrideable safety gates CONFIRMED.
- Teaching-only vs application instruction ayrimi guclendi.
- Professional escalation language/remediation support, aftermarket/custom modification fallback, community appeal/enforcement, evidence-label semantics, critical catch-up, recurring/one-time premium hints, record-only/shared contexts, collaboration, transfer/archive, offline freshness gate, progressive first-use ve accessibility baseline eklendi.
- Q-0030, Q-0031, Q-0032, Q-0033, Q-0034, Q-0037, Q-0038, Q-0039, Q-0040, Q-0041 ANSWERED.
- Batch 05 Q126-Q155 promptu hazirlandi.

### Product Discovery — Batch 05 Complete
- User `PORTABLE DISCOVERY HANDOFF PACKAGE — BATCH 05` icerigini ana yonetici sohbetine getirdi.
- Q126-Q155 raw Q&A `02_DISCOVERY/SESSIONS/SESSION-005_BATCH_05_Q126_Q155.md` icine verbatim kaydedildi.
- Portable package'teki `ANSWERED/RESOLVED/SUPPORTED/CHALLENGED` candidates automatic kabul edilmedi; raw user evidence ile QC yapildi.
- Professional escalation semantics netlesti: assessment error check -> self-remediation -> re-validation; professional help optional support, unverified critical condition mandatory application closure; condition yeniden saglanip relevant checks verify edilince self-service re-entry mumkun.
- Actual motorcycle deletion expectation netlesti: delete-oncesi linked data scope preview; user's own copy linked data removal; previously transferred independent records automatic etkilenmez. Bu legal/technical deletion architecture karari yapilmadi.
- Community contribution withdrawal: public content/personal information removal, de-identified safety review trace expectation ve withdrawn published correction'da affected-guide re-review kaydedildi; privacy/legal feasibility acik kaldi.
- Export provenance zenginlesti: source/provenance, evidence level, important corrections ve dates standard export expectation oldu.
- Evidence semantics common vocabulary + context-specific claim olarak rafine edildi. Verified maintenance record `islem yapildi` evidence claim'i olup perfect workmanship guarantee degil; verified technical guide source + motorcycle fit + application-step suitability claim'ini tasir. High-trust context'te label-only yeterli olmayabilir.
- Selective transfer explicit partial/incomplete history olarak tanimlandi; covered period/gaps visible, private non-transferred content protected, transfer-sonrasi correction silent overwrite degil attributed/reviewable proposal modelinde.
- Professional/service scope kapandi: initial direct target owner; professional/service/hobby helper owner-invited collaboration participant olabilir; professional complexity owner-first experience'i domine etmemeli; paid role automatic verified status yaratmaz.
- Segment priority netlesti: beginner + experienced self-service owner first priority; basic record tracking first-version value; advanced shared/work-management later deepen edilebilir.
- Premium boundary rafine edildi: basic multi-bike separation ve reasonable history core; large media archive, advanced comparative analysis ve extensive collaboration premium candidate. `Multi-garage premium` eski genis yorumu daraltildi. Final price/tier/business viability secilmedi.
- Freshness semantics claim/risk-sensitive hale geldi: safety notices, technical values ve changeable procedure order application-critical; stale teaching/reference kalabilir fakat current instruction gibi gorunemez; critical application online re-check'e kadar kapanabilir. Numeric TTL yok.
- Active-repair accessibility safety invariants netlesti: voice/easy-touch/hands-free convenience safety warning, motorcycle fit, technical value, stop/post-check veya critical confirmation'i kaldiramaz. Energy isolation, stability, critical connection ve completion explicit/reviewable confirmation ister.
- Record-only/shared/multi-bike first-use ve profile transition triggers netlesti; persistent record, cross-device continuation veya collaboration profile istemeyi gerekcelendirebilir. Technical auth/sync modeli secilmedi.
- `OPEN_QUESTIONS.md`: Q-0004, Q-0026, Q-0027, Q-0035, Q-0036, Q-0042, Q-0043, Q-0044, Q-0045 ANSWERED; yeni narrow gaps Q-0046 — Q-0055 acildi.
- `ASSUMPTIONS.md`: ASM-022 RESOLVED; ASM-019/023/024/025 SUPPORTED; ASM-021 CHALLENGED korundu; ASM-026 — ASM-030 yeni OPEN assumptions.
- `GLOSSARY.md`, `PRODUCT_MASTER`, `USER_TYPES`, `USER_JOURNEYS`, `BUSINESS_RULES`, `FEATURE_CANDIDATES`, `NON_GOALS` Batch 05 kanitiyla guncellendi.
- `QUESTION_PROGRESS.md` Batch 05 complete / Batch 06 ready yapildi.
- `02_DISCOVERY/BATCH_06_AI_PROMPT.md` Q156-Q185 icin adaptif olarak hazirlandi.

### Current State
Durum `PHASE-2 / PRODUCT DISCOVERY — BATCH 06 READY`. Batch 07, Batch 06 raw evidence ve synthesis QC tamamlanmadan hazirlanmayacak; Gate 2 -> 3 otomatik gecilmeyecek.
