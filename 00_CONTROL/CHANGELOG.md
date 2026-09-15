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
- Shared collaboration'da motorcycle record lifecycle, contributor evidence lifecycle ve historical attribution ayrildi. Owner delete baska contributor'in independent data'sini sessizce silemez; contributor evidence withdrawal trust re-evaluation tetikler. Independent transferred-copy edge case OPEN kaldi.
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

### Product Discovery — Batch 07 Complete
- User `PORTABLE DISCOVERY HANDOFF PACKAGE — BATCH 07` icerigini ana yonetici sohbetine getirdi.
- Q186-Q215 raw Q&A ve supplemental user note `02_DISCOVERY/SESSIONS/SESSION-007_BATCH_07_Q186_Q215.md` icine verbatim kaydedildi.
- Delegated `ANSWERED/SUPPORTED` candidates automatic kabul edilmedi; raw user evidence ile QC yapildi.
- Contributor evidence withdrawal semantics netlesti: independent/transferred record automatic silinmez; source access, provenance history, visibility ve current trust ayridir; withdrawn evidence evaluation'dan cikarilir ve remaining independent evidence ile claim yeniden review edilir.
- Disputed claim resolution netlesti: new evidence prior dispute'i silent delete etmez; resolution review + evidence sufficiency gerektirir; prior disagreement ve resolution reason history'de kalir; new information correction/extension olarak prior claim'e baglanabilir.
- Historical claim semantics az sayida current-state meaning + ayrintili claim-event history modeline daraldi. Candidate meanings accepted/disputed/insufficient-evidence/superseded; technical enum/schema karari yapilmadi.
- Material guide change/long interruption recovery current physical state reconstruction ve critical re-validation'a dayandirildi. Automatic reversal, nearest-step guessing veya `user says unchanged` ile critical recheck bypass kabul edilmedi.
- Profile migration cancel/failure/rollback local source preservation, partial-state transparency ve non-destructive conflict review ile netlesti; technical sync/transaction architecture secilmedi.
- Correction reach-back interaction depth + risk ile ayristirildi; exact channel/SLA secilmedi.
- Beginner/experienced trust adaptation explanation depth/speed'e sinirlandi; high-risk source/fit/uncertainty/conflict/safety ve mandatory checks invariant kaldi.
- Basic shared-bike trust attribution/revoke/private-content separation/provenance/history integrity olarak netlesti; advanced collaboration participant/role/task/approval/bulk-coordination scale'inda ayrisabilir.
- Batch 07 supplemental user note yeni PROPOSED entitlement preference getirdi: free `1 active motorcycle + 1 invitee + basic history/warnings + user-selected 1 full guide`; additional motorcycles/guides paid; existing records not locked.
- Bu proposal APPROVED/LOCKED yapilmadi. Q159/Q161 broad free multi-bike interpretation ve Q065/Q087/Q145 core-guide interpretation ile refinement tensions `02_DISCOVERY/CONFLICTS.md` icinde CONF-001/CONF-002 olarak kaydedildi.
- `OPEN_QUESTIONS.md`: Q-0050 ve Q-0056 — Q-0064 ANSWERED; entitlement lifecycle icin Q-0065 — Q-0069 OPEN.
- `ASSUMPTIONS.md`: ASM-031/032/033/035/036 SUPPORTED; ASM-034 OPEN refinement; ASM-037 new OPEN.
- `PRODUCT_MASTER.md` Batch 07 evidence ile guncellendi.
- `02_DISCOVERY/SYNTHESIS/BATCH_07_DELTA.md` business-rule/journey/feature/non-goal/glossary additions'i additive olarak kaydetti.
- `QUESTION_PROGRESS.md` 215/215; Batch 07 complete / Batch 08 ready yapildi.
- `02_DISCOVERY/BATCH_08_AI_PROMPT.md` Q216-Q245 entitlement-lifecycle closure icin hazirlandi.

### Product Discovery — Batch 08 Complete / Gate 2 Review
- User `PORTABLE DISCOVERY HANDOFF PACKAGE — BATCH 08` icerigini ana yonetici sohbetine getirdi.
- Q216-Q245 raw Q&A `02_DISCOVERY/SESSIONS/SESSION-008_BATCH_08_Q216_Q245.md` icine verbatim kaydedildi. User cevaplarindaki Google Play/RevenueCat links raw evidence olarak korundu; external verification veya billing/business implementation karari yapilmadi.
- Delegated `ANSWERED/PARTIALLY_ANSWERED/READY CANDIDATE` adaylari automatic gate karari olarak kabul edilmedi; raw user evidence ile QC yapildi.
- One-active-motorcycle lifecycle netlesti: inactive history/evidence/export/correction/trust access'i korunur; routine reminders susabilir; historical critical safety reach-back ve required recheck/safe-recovery entitlement'tan bagimsiz devam eder; reactivation current km/use ve physical state revalidation ister.
- One-selected-full-guide lifecycle netlesti: account-level current working proposal; bike switch/completion automatic new free right yaratmaz; reuse/history/corrections korunur; user-fault olmayan invalidation replacement selection hakki acabilir. Exact wrong-selection correction window validation topic olarak kaldi.
- Started physical work entitlement change nedeniyle paywall'a takilamaz; safe completion/stop/recovery icin required relevant guidance korunur ve new paid activity entitlement'i yaratmaz.
- `Existing records stay unlocked` read/basic-search/export/provenance/evidence/correction/dispute/error-flag/own-evidence-withdrawal ve existing-claim trust-maintenance behavior'larini kapsayacak sekilde netlesti. Unrelated new routine activity ayri monetizable new activity olabilir.
- Collaboration downgrade historical attribution/evidence/approvals/correction trail'i korur; new routine/advanced activity durabilir; owner revoke authority devam eder.
- Retroactive historical lock, trust-metadata hiding, critical safety correction paywall ve mid-repair paywall explicit trust-breakers olarak guclendi.
- `CONFLICTS.md` CONF-001/CONF-002 `RESOLVED_REFINEMENT` yapildi; final commercial tier approval verilmedi.
- `SYNTHESIS/BATCH_08_DELTA.md` additive product rules/journeys/features/non-goals/glossary'i kaydetti.
- `OPEN_QUESTIONS.md`: Q-0065 — Q-0069 ANSWERED; active product-definition questions kalmadi. Kalan konular non-blocking validation/strategy topics olarak ayrildi.
- `ASSUMPTIONS.md`: ASM-037 SUPPORTED; ASM-038/ASM-039 new OPEN validation assumptions; commercial sustainability assumptions unresolved kaldi.
- `QUESTION_PROGRESS.md`: 245/245; Batch 08 `COMPLETED_QC_PASSED`; automatic Batch 09 hazirlanmadi.
- `02_DISCOVERY/GATE_2_REVIEW.md` olusturuldu; recommendation `READY_FOR_USER_APPROVAL`.
- `DOCUMENT_REGISTRY.md`: Product Discovery `REVIEW` durumuna tasindi.
- `CURRENT_STATE.md`: `PHASE-2 / PRODUCT DISCOVERY — GATE 2 REVIEW REQUIRED`.

### Phase 2 Approval / Gate 2 -> 3
- User Phase-2 Product Discovery synthesis'ini acikca onayladi ve Gate 2 -> 3 gecisini kabul etti.
- `02_DISCOVERY/GATE_2_REVIEW.md` APPROVED / PASSED yapildi.
- `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md` canonical approved Phase-2 snapshot olarak olusturuldu; component blob SHA'lariyla approval snapshot'i freeze edildi.
- `00_CONTROL/SOURCE_OF_TRUTH.md` Phase-2 product truth entry point'i olarak approved snapshot'a yonlendirildi.
- DEC-0009 `Phase 2 Product Discovery Approved and Gate 2 Passed` APPROVED olarak kaydedildi.
- `DOCUMENT_REGISTRY.md`: Product Discovery APPROVED, Design DRAFT.
- `QUESTION_PROGRESS.md`: `DISCOVERY_APPROVED_GATE_2_PASSED`, 245/245.
- Phase-2 approval PROPOSED monetization direction'i final pricing/tier policy'ye donusturmedi; validation/feasibility assumptions acik kaldi.

### Phase 3 Design Start
- `CURRENT_STATE.md`: `PHASE-3 / DESIGN — SCREEN INVENTORY READY`.
- `03_DESIGN/PHASE3_SCREEN_INVENTORY_AI_PROMPT.md` olusturuldu.
- Phase 3 ilk adimi screen catalog + navigation + state coverage olarak belirlendi; mockup/visual reference generation sonraki adima birakildi.
- Delegated Design AI repository'ye yazmayacak, approved product behavior'i degistirmeyecek, technology/backend architecture veya final pricing karari vermeyecek.
- Gate 3 -> 4 screen catalog/navigation/important states ve user-approved visual references yeterli olmadan degerlendirilmeyecek.

### Current State
Durum `PHASE-3 / DESIGN — SCREEN INVENTORY READY`. Siradaki adim `03_DESIGN/PHASE3_SCREEN_INVENTORY_AI_PROMPT.md` promptunu yeni AI sohbetine verip `PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / SCREEN INVENTORY 01` ciktisini ana proje yoneticisine geri getirmektir.
