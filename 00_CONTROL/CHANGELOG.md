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
- Q066-Q095 raw Q&A `SESSION-003_BATCH_03_Q066_Q095.md` icine verbatim kaydedildi.
- Onceki kanitla dogrudan conflict tespit edilmedi.
- Observable feature + fotografla variant ayristirma, high-consequence conditional learning/application, notification grouping/cadence, history edit trail/evidence levels, maintenance uncertainty, time/cost transparency, community/moderation, commercial neutrality, roadside/offline, data ownership/export/delete ve trust-breaker alanlari derinlesti.
- Q070 haftalik ozet global LOCKED policy yapilmadi; Q074 automatic verification taxonomy yapilmadi; Q087 final premium package sayilmadi.
- Open questions, assumptions, glossary ve tum working synthesis dosyalari guncellendi.
- Batch 04 Q096-Q125 promptu hazirlandi.

### Product Discovery — Batch 04 Complete
- Kullanici `PORTABLE DISCOVERY HANDOFF PACKAGE — BATCH 04` icerigini ana yonetici sohbetine getirdi.
- Q096-Q125 raw Q&A `02_DISCOVERY/SESSIONS/SESSION-004_BATCH_04_Q096_Q125.md` icine verbatim kaydedildi.
- Portable paketteki `ANSWERED/RESOLVED` ve assumption status adaylari otomatik kabul edilmedi; ham kullanici cevaplari uzerinden yeniden kalite kontrolu yapildi.
- Readiness false-positive durumunda serbest override yerine fotograf/olcum/alternatif kontrolle evidence-based re-validation ve non-overrideable safety gate beklentileri CONFIRMED edildi.
- Teaching-only content ile belirli motosiklete uygulanabilir application instruction ayrimi guclendi; high-consequence application ilk fiziksel mudahaleden once ve yeni risk/mismatch aninda gate'leniyor.
- Professional escalation'in `sen yapamazsin` diliyle sunulmamasi, eksik kosul/remediation/retry yoluna dayanmasi ve diagnosis/preparation/result-check desteginin devam etmesi kaydedildi; exact escalation trigger OPEN tutuldu.
- Common aftermarket icin verified adapted guide beklentisi; custom/unique durumda evidence gap + teaching-only bilgi + application hold davranisi kaydedildi. Bunun technical coverage feasibility'si varsayim olarak acik kaldi.
- Community moderation removal reason, appeal/re-submit, pre-review, repeated dangerous contribution restriction ve `dogrulanmamis kisisel deneyim` statuleri eklendi.
- Q109-Q110 ile `kullanici beyani / belgeli / incelenmis / dogrulanmis` temel product semantigi netlesti; tum domainlerde zorunlu tek global taxonomy olarak kilitlenmedi.
- Kritik reminder'larda app-ici safety summary, harm/urgency siralamasi ve uzun aradan donuste catch-up summary beklentileri eklendi.
- Premium adaylar analysis/storage/multi-garage/personalization ile genisledi; non-recurring optional value icin one-time payment tercihi kaydedildi; final pricing/package modeli secilmedi.
- Record-only owner, shared-family/hobby helper adjacent user context'leri eklendi; core focus bireysel self-service rider olarak korundu; professional/service target statusu OPEN kaldi.
- Shared motorcycle icin owner permission, contributor attribution, edit trail, revocable access ve private-note isolation beklentileri kaydedildi.
- Ownership transfer'da secili vehicle history transferi, personal content privacy ve preview; archive'da reversible history-preserving state beklentileri kaydedildi. Parsiyel transfer completeness acik kaldi.
- Critical offline guide last-verification ve freshness-limit sonrasi online re-check'e kadar application hold beklentisi kaydedildi; sayisal threshold secilmedi.
- Progressive first-use, Turkiye-first terminology/unit expectation ve accessibility/dirty-hands/voice-easy-touch ihtiyaclari discovery'ye eklendi; teknik auth/voice/UI cozumleri secilmedi.
- `OPEN_QUESTIONS.md`: Q-0030, Q-0031, Q-0032, Q-0033, Q-0034, Q-0037, Q-0038, Q-0039, Q-0040, Q-0041 ANSWERED; Q-0004, Q-0026, Q-0027, Q-0035, Q-0036 ve yeni Q-0042 — Q-0045 OPEN.
- `ASSUMPTIONS.md`: ASM-016 SUPPORTED, ASM-020 RESOLVED, ASM-021 CHALLENGED; ASM-022 — ASM-025 yeni OPEN varsayimlar eklendi.
- `GLOSSARY.md` Batch 04 domain terimleriyle rafine edildi.
- `PRODUCT_MASTER`, `USER_TYPES`, `USER_JOURNEYS`, `BUSINESS_RULES`, `FEATURE_CANDIDATES`, `NON_GOALS` Batch 04 kanitiyla guncellendi.
- `QUESTION_PROGRESS.md` Batch 04 complete / Batch 05 ready yapildi.
- `02_DISCOVERY/BATCH_05_AI_PROMPT.md` Q126-Q155 icin adaptif olarak hazirlandi.

### Current State
Durum `PHASE-2 / PRODUCT DISCOVERY — BATCH 05 READY`. Batch 06, Batch 05 ham kanit ve synthesis kalite kontrolunden gecmeden hazirlanmayacak; Gate 2 -> 3 otomatik gecilmeyecek.
