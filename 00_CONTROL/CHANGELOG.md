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
- Q126-Q155 raw Q&A `SESSION-005_BATCH_05_Q126_Q155.md` icine verbatim kaydedildi.
- Portable package'teki status candidates automatic kabul edilmedi; raw evidence ile QC yapildi.
- Professional escalation semantics: assessment error check -> self-remediation -> re-validation; optional professional support vs mandatory critical closure ayrildi.
- Actual deletion, community withdrawal, provenance-rich export, context-specific evidence semantics, selective-transfer transparency, owner-first professional collaboration, segment priority, free-core/premium boundary, freshness, active-repair accessibility ve profile triggers rafine edildi.
- Basic multi-bike separation + reasonable history core olarak netlesti; old broad `multi-garage premium` yorumu daraltildi.
- Q-0004, Q-0026, Q-0027, Q-0035, Q-0036, Q-0042, Q-0043, Q-0044, Q-0045 ANSWERED; Q-0046 — Q-0055 acildi.
- `ASSUMPTIONS.md`, `GLOSSARY.md` ve tum working synthesis dosyalari guncellendi.
- Batch 06 Q156-Q185 promptu hazirlandi.

## 2026-09-15

### Product Discovery — Batch 06 Complete
- User `PORTABLE DISCOVERY HANDOFF PACKAGE — BATCH 06` icerigini ana yonetici sohbetine getirdi.
- Q156-Q185 raw Q&A `02_DISCOVERY/SESSIONS/SESSION-006_BATCH_06_Q156_Q185.md` icine verbatim kaydedildi.
- Portable package'teki `ANSWERED/SUPPORTED` candidates automatic kabul edilmedi; raw user evidence ile QC yapildi.
- Portable Batch 06 package assumption candidates `ASM-026 — ASM-030` numaralarini repository canonical registry'den farkli anlamlarda kullaniyordu. Canonical IDs sessizce yeniden yazilmadi; evidence mevcut assumptions'a dogru baglandi ve new assumptions ASM-031'den devam ettirildi.
- Core history product boundary netlesti: motorcycle, operation, date, mileage, actor, outcome, important safety notes, evidence level ve correction continuity core'da korunur; old basic records storage pressure nedeniyle silinmez.
- Expanded storage high-volume/high-resolution photos, long videos ve broad document archive degerine ayrildi; premium boundary existing basic history/safety evidence access veya export'u bozamaz.
- Basic multi-bike separation motorcycle-isolation invariant'i olarak netlesti; advanced garage cross-bike analysis, bulk planning, richer collaboration ve large-archive search degerinde baslar.
- Ownership transfer/history trust derinlesti: rejected correction accepted record'u overwrite etmez; disputed claim provenance ile kalir; repeated transfers owner/period/coverage/gaps ile ayrilir; partial periods complete history diye sunulamaz.
- Q163'teki `degistirilemez iz` product historical-integrity expectation'i olarak korundu; immutable ledger/event sourcing/database architecture karari yapilmadi.
- Withdrawn community evidence dependent official guide/claim icin dependency-aware re-review tetikler. Independent evidence yeterliyse claim review sonrasi kalabilir; yetersizse verification/application korunmaz. Safety/technical/applied-critical impact correction reach-back gerektirebilir.
- Shared collaboration'da motorcycle record lifecycle, contributor evidence lifecycle ve historical attribution ayrildi. Owner delete baska contributor'in independent data'sini sessizce silemez; contributor evidence withdrawal trust re-evaluation tetikler. Independent transferred-copy edge case OPEN kaldı.
- Evidence explanation risk-adaptive hale geldi: low-risk concise label; high-risk/disputed context explicit claim/motorcycle/evidence/reviewer/uncertainty. Q174'teki UI wording final component karari yapilmadi.
- Account-light -> profile transition trust-preserving migration olarak rafine edildi: scope preview, no silent loss, conflict review, no silent overwrite. Technical sync/transaction architecture secilmedi.
- Material guide change mid-repair current physical motorcycle state ile new guide arasinda physical-state remapping gerektirir; photo-based expectation computer-vision guarantee veya vendor karari yapilmadi.
- Active-repair interruption resume semantics last-viewed-step degil last-known-safe state + current physical/safety re-validation olarak netlesti.
- Paid-service document vs owner evidence dispute iki source claim olarak korunur; unresolved completion maintenance counter veya future guide decisions'a verified fact olarak aktarilmaz.
- `OPEN_QUESTIONS.md`: Q-0046, Q-0047, Q-0048, Q-0049, Q-0051, Q-0052, Q-0053, Q-0054, Q-0055 ANSWERED; Q-0050 narrowed OPEN; Q-0056 — Q-0064 yeni OPEN gaps.
- `ASSUMPTIONS.md`: ASM-026/027/028/029 SUPPORTED; ASM-030 OPEN; ASM-031 — ASM-035 new OPEN.
- `GLOSSARY.md`, `PRODUCT_MASTER`, `USER_TYPES`, `USER_JOURNEYS`, `BUSINESS_RULES`, `FEATURE_CANDIDATES`, `NON_GOALS` Batch 06 kanitiyla guncellendi.
- `QUESTION_PROGRESS.md` Batch 06 complete / Batch 07 ready yapildi.
- `02_DISCOVERY/BATCH_07_AI_PROMPT.md` Q186-Q215 icin adaptif olarak hazirlandi.

### Current State
Durum `PHASE-2 / PRODUCT DISCOVERY — BATCH 07 READY`. Batch 08, Batch 07 raw evidence ve synthesis QC tamamlanmadan hazirlanmayacak; Gate 2 -> 3 otomatik gecilmeyecek.
