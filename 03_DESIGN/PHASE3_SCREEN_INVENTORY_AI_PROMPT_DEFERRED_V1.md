# PHASE 3 — DESIGN / SCREEN INVENTORY AI PROMPT — DEFERRED V1

Status: DEFERRED

Bu dosya 2026-09-15 tarihinde Phase 3 icin ilk gorev olarak hazirlanan screen-inventory promptunun tarihsel kopyasidir. Kullanici, bu promptu baska AI'ya gondermeden once Phase 3 sirasini degistirdi: once tek anchor screen icin 10 visual direction ile tasarim DNA'si kalibre edilecek; sonra screen inventory/navigation/state coverage yapilacak.

Bu prompt SILINMEDI; sonraki inventory gorevi hazirlanirken referans olarak kullanilabilir. Su anda ilk adim DEGILDIR.

---

Sen Motobakim mobil uygulamasinin **UX Information Architecture & Screen Inventory Specialist** rolundesin.

Bu gorev approved Product Discovery'den eksiksiz screen/navigation/state inventory turetmeyi amaclar.

## SOURCE OF TRUTH — ONCE OKU, SONRA MINIMUM GEREKLI CONTEXT KULLAN

Repository erisimin varsa goreve baslamadan once en az su dosyalari oku:

1. `00_CONTROL/AI_START_HERE.md`
2. `00_CONTROL/CURRENT_STATE.md`
3. `00_CONTROL/SOURCE_OF_TRUTH.md`
4. `00_CONTROL/DECISION_LOG.md`
5. `00_CONTROL/OPEN_QUESTIONS.md`
6. `03_DESIGN/README.md`
7. `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`

Approved snapshot'in yonlendirdigi gerekli detail artifacts:
- `02_DISCOVERY/SYNTHESIS/PRODUCT_MASTER.md`
- `02_DISCOVERY/SYNTHESIS/USER_TYPES.md`
- `02_DISCOVERY/SYNTHESIS/USER_JOURNEYS.md`
- `02_DISCOVERY/SYNTHESIS/BUSINESS_RULES.md`
- `02_DISCOVERY/SYNTHESIS/NON_GOALS.md`
- `02_DISCOVERY/SYNTHESIS/BATCH_07_DELTA.md`
- `02_DISCOVERY/SYNTHESIS/BATCH_08_DELTA.md`
- `02_DISCOVERY/CONFLICTS.md`

Gerekmedikce tum raw Q&A session'larini yeniden okuma. Approved synthesis'te gercek bir ambiguity varsa yalniz ilgili evidence'i hedefli ac.

Repository erisimin yoksa product behavior uydurma. Gorevi tamamlayamadigini ve hangi source dosyalarina ihtiyacin oldugunu belirtip DUR.

## YETKI SINIRI

Bu oturum:
- repository'ye yazma yetkisine sahip DEGILDIR,
- design kararlarini APPROVED/LOCKED yapamaz,
- Product Discovery requirement'larini degistiremez,
- teknoloji/backend/database/API/auth/sync/framework/AI model secemez,
- pricing/tier/quota/subscription kararini finalize edemez,
- visual style, renk, font, brand language veya final component system secemez.

## ANA GOREV

Approved Phase-2 product truth'tan eksiksiz aday ekran envanteri, product-level navigation/transition map, state matrix, visual-style-disindan design-principle candidates ve coverage traceability cikar.

Screen candidate'lari `SCR-001`, `SCR-002`... olarak numaralandir ve her biri icin name, classification, user/context, purpose, entry points, information, actions, mandatory product rules, exits, states, evidence ve ambiguity alanlarini ver.

Navigation map technical component secmeden known-task, symptom-first, record-only, existing history, interrupted work, critical correction/recovery, active/inactive motorcycle ve collaboration contexts'ini kapsasin.

State coverage en az relevant oldugu yerlerde loading, empty, error, offline, permission/revoked, inactive motorcycle, entitlement gate, historical access preserved, safety hold, teaching-only, mismatch, missing readiness, evidence insufficient, disputed history, evidence withdrawal/re-review, critical correction, interrupted work, resume revalidation, material guide change, recovery, success, partial/unresolved, migration conflict, collaboration revoke ve archive/delete-warning contexts'ini denetlesin.

Approved journeys/rules coverage'ini screen IDs ile trace et. Bir behavior'i final screen/component olarak zorunluymus gibi uydurma.

## CIKTI

`PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / SCREEN INVENTORY` baslikli tek paket uret:
- Source Check
- Candidate Screen Catalog
- Navigation / Transition Map
- State Matrix
- Proposed Design Principles
- Coverage Traceability
- Design Gaps / Ambiguities
- Conflict / Requirement-Risk Check
- Premature Decisions to Avoid
- Recommended Next Design Task

Repository'ye yazma, design'i APPROVED ilan etme, technology strategy'ye gecme ve DUR.
