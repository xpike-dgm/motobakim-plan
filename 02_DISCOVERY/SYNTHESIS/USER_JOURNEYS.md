# USER JOURNEYS

Status: DRAFT

Kullanicilarin teknik implementasyon detayindan bagimsiz uc uca product journeys.

## J-001 — Known task -> prepare -> execute -> verify -> record
**Evidence:** Q006, Q013-Q021, Q029-Q030, Q050-Q053, Q096-Q099, Q126-Q128
1. User yapmak istedigi islemi bilir.
2. Motorcycle/guide fit ve task-specific readiness degerlendirilir.
3. Risk, duration/cost, tools/parts/equipment ve use impact gorulur.
4. Eksik condition varsa reason + self-remediation + re-validation yolu sunulur.
5. Critical missing condition application'i kapatir; professional help optional support olabilir.
6. Kosul saglanip yeniden verified olunca ayni guide'a geri donulebilir.
7. Guide experience-level'a gore detail/hiz sunar; safety invariants degismez.
8. Critical steps visual/measurement/success checks ile ilerler.
9. New risk/mismatch olusursa progression durur.
10. Verified completion history'ye kaydedilir.

## J-002 — Symptom -> evidence-guided diagnosis -> repair guide
**Evidence:** Q012, Q022-Q024, Q056-Q058
1. Symptom daily language/area/visual ile ifade edilir.
2. Immediate danger check yapilir.
3. Safe distinguishing checks evidence toplar.
4. Possibilities certainty taklidi yapmadan daralir.
5. Yeterli evidence varsa repair guide'a gecilir.
6. Evidence yetersizse `Neden dogrulanamadi` sonucu + handoff summary mumkundur.

## J-003 — Variant/modification mismatch -> resolve or teaching-only fallback
**Evidence:** Q026, Q036-Q039, Q066-Q067, Q102-Q104
1. Guide physical motorcycle ile mismatch verir.
2. Application durur.
3. Observable features/photos ile distinction denenir.
4. Common aftermarket verified ise adapted guide'a gecilir.
5. Unique/custom fit unresolved ise missing evidence gosterilir.
6. Teaching-only general content kalabilir; risky application kapanir.

## J-004 — Readiness stop -> self-remediation -> re-validation -> re-entry
**Evidence:** Q050-Q053, Q096-Q098, Q126-Q128
1. User critical readiness condition'i karsilamaz.
2. False-positive possibility kontrol edilir.
3. Learning/preparation/equipment acquisition yolu sunulur.
4. New photo/measurement/alternative evidence ile re-validation yapilir.
5. User assertion tek basina gate'i acmaz.
6. Equipment + motorcycle fit + critical checks yeniden verified olunca same guide resume edilir.
7. Professional recommendation ile mandatory closure ayrica ifade edilir.

## J-005 — High-consequence learning -> conditional application / professional option
**Evidence:** Q068-Q069, Q099-Q101, Q126-Q128
1. User high-consequence topic'i ogrenmek ister.
2. Risks, prerequisite knowledge, equipment ve critical checks teaching layer'da aciklanir.
3. First physical intervention'dan once mandatory conditions verify edilir.
4. Unverified critical condition application'i kapatir.
5. Professional help option olabilir; tek exit olmak zorunda degildir.
6. Self-remediation/re-validation ve eventual self-service re-entry korunur.

## J-006 — User gets stuck / mistake / unexpected behavior -> recovery
**Evidence:** Q025-Q027
1. Normal progression durur.
2. More detail/visual/motion guidance acilir.
3. Motorcycle safe state'e alinmaya calisilir.
4. Evidence captured olur.
5. Safe return veya professional help yolu sunulur.

## J-007 — Pause work -> version/freshness/material-change check -> physical-state remap -> resume
**Evidence:** Q028, Q042-Q043, Q059-Q060, Q122, Q147-Q149, Q178-Q180
1. Work state, physical context ve guide version korunur.
2. Return'de version/freshness kontrol edilir.
3. Critical change/stale state varsa old application devam etmez.
4. User change'in ne oldugunu, safety impact'i ve immediate stop gerekip gerekmedigini gorur.
5. Motorcycle'in current physical state photo/check questions ile current guide'a yeniden fit edilmeye calisilir.
6. Old completed steps ve new guide entry point verify edilmeden continuation olmaz.
7. Physical state reliably match edilemiyorsa teaching/reference kalir, application kapanir; professional support optional olur.
8. Verified current path ile resume edilir.

## J-008 — Maintenance due -> prioritize -> remind -> perform/record/postpone
**Evidence:** Q031-Q033, Q061, Q064, Q070-Q072, Q075-Q077, Q111-Q113
1. Verified manufacturer plan + completion history kullanilir.
2. Verified exceptions gerekcesiyle plan degistirir.
3. Missing/uncertain interval hidden edilmez.
4. Multiple due items harm/urgency/use impact ile siralanir.
5. Routine reminders group/postpone olabilir.
6. Critical safety ayrı gorunur.
7. Long absence catch-up summary ile toparlanir.
8. Postponement completion sayilmaz.

## J-009 — Review/correct/dispute historical work
**Evidence:** Q029-Q030, Q073-Q074, Q109-Q110, Q132-Q134, Q162-Q165
1. User history record'u acar.
2. Work, actor, date/km, evidence, guide version gorulur.
3. Wrong entry correction old/new/time/reason iziyle yapilir.
4. Transfer sonrasi correction rejected ise original accepted record ile disputed proposal ayri kalir.
5. Who/when/evidence/correction/dispute context important historical claim'de korunur.
6. Evidence explanation risk-adaptive olur.
7. Multiple ownership periods provenance + coverage + gaps ile gorulur.

## J-010 — External service/hobby contribution -> evidence-aware history -> dispute if needed
**Evidence:** Q063, Q109-Q110, Q138-Q140, Q184-Q185
1. Owner baska bir actor tarafindan yapilan isi record eder/davet eder.
2. Hobby helper ve paid service ayrilir.
3. Actor attribution + evidence kaydedilir.
4. Paid service ek service/document context tasir.
5. Role alone verified status yaratmaz.
6. Service document owner observation/evidence ile celisirse claims source-wise separate tutulur.
7. Dispute unresolved ise maintenance counter veya future guide decision verified completion gibi ilerlemez.

## J-011 — Community contribution -> review -> publish/hold -> appeal/withdraw -> downstream re-review
**Evidence:** Q080-Q084, Q105-Q108, Q130, Q166-Q168
1. Personal content default-private kalir.
2. Explicit community contribution yapilir.
3. Provenance/review status official guide'dan ayri tutulur.
4. Problem varsa reason + correction/re-submit/appeal yolu sunulur.
5. Contribution withdrawal public content/personal info'yu kaldirir.
6. De-identified safety review trace gerekirse kalabilir.
7. Withdrawn evidence downstream guide/claim'i desteklediyse re-review tetiklenir.
8. Independent evidence yeterliyse claim review sonrasi kalabilir; yetersizse verification/application hold olur.
9. Safety/technical/applied-critical impact varsa affected users correction/re-review bilgisi alabilir.

## J-012 — Commercial support without technical influence
**Evidence:** Q085-Q088, Q114-Q115, Q144-Q146, Q156-Q161
1. Technical fit first gelir.
2. Commercial/sponsor surface explicit isaretlenir.
3. Core completion/safety/basic history/export/basic motorcycle isolation paywall olmaz.
4. Expanded media/cross-bike advanced analysis/collaboration premium candidate olabilir.
5. Recurring vs one-time value product expectation olarak ayrisabilir.

## J-013 — Multi-motorcycle core isolation -> advanced garage
**Evidence:** Q062, Q141, Q146, Q154, Q159-Q161
1. Her motorcycle history/km/reminder/active-work context independent kalir.
2. One motorcycle change digerini etkilemez.
3. Basic multi-bike separation core value'dur.
4. Advanced garage cross-bike analysis, bulk planning, richer collaboration ve large-archive search gibi ek value'da baslar.

## J-014 — Shared motorcycle collaboration -> access/evidence lifecycle
**Evidence:** Q118-Q119, Q138-Q141, Q154, Q169-Q171
1. Owner access grants contribution.
2. Actor attribution/time/edit trail gorunur.
3. Private notes automatic share edilmez.
4. Access revocable olur; revoke future access/addition'i durdurur.
5. Prior attributed operation records history'de kalabilir.
6. Contributor own evidence withdrawal mumkundur; linked claim trust yeniden degerlendirilir.
7. Owner delete baska kisinin independent evidence'ini sessizce yok etmez.
8. Independent transferred-copy visibility/withdrawal siniri hala discovery gap'idir.

## J-015 — Ownership transfer -> partial-history disclosure -> repeated transfers -> disputed corrections
**Evidence:** Q120, Q135-Q137, Q162-Q165
1. Owner transfer edilecek records/evidence'i secer.
2. Personal notes/private photos default-private kalir.
3. New owner `owner-selected / incomplete history` oldugunu gorur.
4. Covered period ve visible gaps aciklanir.
5. Repeated transfers owner/donem/coverage ile ayri provenance tasir.
6. Partial histories complete chain gibi merge edilmez.
7. Former owner correction proposal accepted/rejected statusuyla original record yaninda kalabilir.
8. Prior version/evidence trail korunur.

## J-016 — Archive -> restore / actual delete -> collaborator-data boundary
**Evidence:** Q121, Q129, Q169-Q171
1. Archive active garage'dan cikarir, history'yi korur, reversible'dir.
2. Actual delete oncesi affected linked data/collaboration scope gosterilir.
3. Confirmation sonrasi owner'in own copy linked data'si silinir.
4. Previously transferred independent records otomatik etkilenmez.
5. Collaborator-owned evidence separate lifecycle gosterebilir; withdrawal trace history trust'i gunceller.

## J-017 — User data export
**Evidence:** Q093, Q131, Q156-Q158
1. User kendi verisini export eder.
2. Export premium olmaz.
3. Record content yaninda source/provenance, evidence level, important corrections ve dates bulunur.
4. Expanded-media limit basic history/export erisimini bozamaz.
5. Technical format bu asamada belirlenmez.

## J-018 — Roadside / offline continuity -> stale critical hold
**Evidence:** Q090-Q091, Q122, Q147-Q149
1. Downloaded guide/visual/safety/progress/history offline acilir.
2. Version/last-check visibility bulunur.
3. Conceptual teaching stale olsa da reference olarak kalabilir.
4. Critical freshness verify edilemiyorsa motorcycle-facing application kapanir.
5. Learning/preparation/local record devam eder.
6. Connection gelince current version check yapilir; material change varsa J-007 recovery path'i uygulanir.

## J-019 — Accessible active repair
**Evidence:** Q124-Q125, Q150-Q152
1. Clear Turkish/familiar units/appropriate detail sunulur.
2. Text/visual/audio/large/easy controls alternative channels saglar.
3. Risk/direction/location/value/stop warning multiple modalities ile iletilebilir.
4. Critical confirmation easy interaction ugruna kaldirilmaz.
5. Energy isolation/stability/critical connection/completion explicit reviewable confirmation ister.

## J-020 — Record-only first use -> later guided repair
**Evidence:** Q117, Q153
1. User motorcycle ekler.
2. Recent work record eder ve upcoming maintenance value'yu gorur.
3. Guide aramak zorunda degildir.
4. Later same motorcycle/history context'ten guided repair'e gecebilir.

## J-021 — Account-light first use -> persistence/profile migration -> conflict review
**Evidence:** Q123, Q153-Q155, Q175-Q177
1. Segment-specific first value account zorunlulugundan once gorulur.
2. User first real record'u kalici saklamak, cross-device devam etmek veya collaborator invite etmek ister.
3. Profile reason + local data scope onceden aciklanir.
4. Local records successful transition confirm edilmeden sessizce kaldirilmaz.
5. Duplicate/conflicting groups source/date/differences ile review edilir.
6. Silent overwrite olmaz; user separate/relate/verified correction options bekler.
7. User profile istemezse local guide/history/interrupted-work value devam edebilir.

## J-022 — Active repair interruption -> resume revalidation
**Evidence:** Q181-Q183
1. Device/app/attention interruption olur.
2. Motorcycle, guide version, last definitely completed step, in-progress step, photos, safety warnings ve preparation context korunur.
3. Unsaved step completed varsayilmaz.
4. Stability, energy/temperature, removed parts, open connections ve last critical step yeniden kontrol edilir.
5. Previous confirmation automatic valid sayilmaz.
6. User state'ten emin degilse last known safe state'ten photo/symptom/check questions ile current state yeniden establish edilir.
7. Unresolved durumda application durur.

## J-023 — Evidence explanation: concise low-risk -> explicit high-risk
**Evidence:** Q172-Q174
1. Low-risk routine content short evidence label ile baslayabilir.
2. User daha derin provenance acabilir.
3. High-risk/disputed context claim + motorcycle + evidence + reviewer + unresolved uncertainty aciklar.
4. First-level result/evidence/source/date/uncertainty; deeper level full docs/review chain/versions/rationale olabilir.

## Open Journey Gaps

- Contributor evidence withdrawal'in previously transferred/independent copies ile product-level iliskisi.
- Disputed historical/service claim'e yeni independent evidence geldiginde resolution states.
- Historical claim states icin minimum semantik set.
- Material guide change'de old guide ile yapilmis artik onerilmeyen physical changes recovery.
- Long interruption'da saved context vs current physical reality trust boundary.
- Profile migration cancel/rollback beklentisi.
- Withdrawn evidence icin `affected user` boundary.
- Evidence detail depth'in beginner/experienced adaptation'i safety explicitness'i azaltmadan nasil olmali.
- Core invited collaboration ile premium extensive collaboration siniri.
