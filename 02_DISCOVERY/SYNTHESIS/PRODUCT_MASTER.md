# PRODUCT MASTER

Status: DRAFT

Bu belge discovery boyunca rafine edilen teknik olmayan ana urun sentezidir. Ham Q&A yerine gecmez; kanit `02_DISCOVERY/SESSIONS/` altindadir.

## Current Evidence Base
- Phase-1 approved workspace baseline
- `SESSION-001_BATCH_01_Q006_Q035.md`
- `SESSION-002_BATCH_02_Q036_Q065.md`
- `SESSION-003_BATCH_03_Q066_Q095.md`
- `SESSION-004_BATCH_04_Q096_Q125.md`
- `SESSION-005_BATCH_05_Q126_Q155.md`
- `SESSION-006_BATCH_06_Q156_Q185.md`
- `SESSION-007_BATCH_07_Q186_Q215.md`

## Product Model — Current Working Synthesis

### 1. Core product identity and priority

**CONFIRMED — Phase 1, Q006-Q007, Q089, Q116-Q117, Q138-Q143**

MotoBakim'in birincil hedefi, bireysel motosiklet sahibinin kendi motosikletindeki bakım, mekanik ve elektriksel islemleri neyi/neden/nasil yaptigini anlayarak guvenli bicimde tamamlayabilmesidir.

Ilk product priority:
1. yeni/az deneyimli self-service owner,
2. deneyimli self-service owner,
3. temel record/history tracking ihtiyaci.

Record-only owner, multi-bike owner, shared-family context ve hobby helper anlamli desteklenen baglamlardir. Professional/servis ilk urunun dogrudan ana target'i degildir; owner davetiyle contribution/collaboration participant olabilir. Ayrı professional work-management product ileride dusunulebilir fakat owner-first self-service deneyimini degistirmemelidir.

### 2. Entry modes, first value and profile transition

**CONFIRMED — Q006, Q012, Q022, Q090, Q123, Q153-Q155, Q175-Q177, Q201-Q203**

Kullanici yapmak istedigi islemi bilerek, yalniz bir belirtiyle, yalniz history/reminder tutmak icin veya multi/shared motorcycle baglamiyla gelebilir.

Self-service first-use'ta motosiklet secilip guide value hizla gorulmelidir. Record-only user motosikletini ekleyip son islemini kaydetmeli ve approaching maintenance value'yu erken anlayabilmelidir. Shared/multi-bike user motorcycle separation ve contribution attribution degerini erken gorebilmelidir.

Account/profile ilk degerden once zorunlu olmamali. Ilk real record'u kalici saklama, cross-device devam veya collaboration baslatma ihtiyaci profile gecis icin dogal product trigger'dir.

Local-to-profile transition trust-preserving olmalidir: aktarilacak local scope onceden gorunmeli, source/local records successful transition teyit edilmeden sessizce kaybolmamali, duplicate/conflicting groups source/date/differences ile review edilebilmeli ve silent overwrite yapilmamalidir. Cancel/failure durumunda local history kullanilabilir kalmali; profile tarafinda olusan partial records completed migration gibi sunulmamalidir. User hangi records'in local kaldigini ve hangilerinin profile dogrulanarak gectigini anlayabilmelidir. Rollback/correction historical data'yi sessizce silmemelidir.

Kullanici profile gecmezse guide reading, motorcycle selection, local history ve interrupted-step continuation gibi local degerler devam edebilmelidir. Teknik auth/sync/transaction implementation bu asamada secilmez.

### 3. Motorcycle-guide fit, variant certainty and modification fit

**CONFIRMED — Q008-Q009, Q019, Q026, Q036-Q039, Q066-Q067, Q102-Q104**

Guide, gercek motosikletle yeterli fit kurulmadan motosiklete ozel application instruction gibi sunulamaz. Marka/model/yil, motor hacmi, donanim, relevant features, visible hardware ve fotograflar kullanilabilir. Kullanici technical code/document scavenger hunt'a zorlanmamalidir.

Observable evidence yetersizse eksik ayrim gosterilir ve variant-specific application kapanir. Bu visual identification'in her motosiklette teknik olarak yeterli oldugu feasibility iddiasi degildir.

Modified system'de factory guide otomatik uygun sayilmaz. Common aftermarket degisiklik verified fit varsa adapted guide'a dahil edilebilir. Unique/custom modification'da evidence gap aciklanabilir ve teaching-only bilgi kalabilir; zarar verebilecek application adimlari fit dogrulanana kadar acilmaz.

### 4. Trust, provenance, claim states and evidence semantics

**CONFIRMED — Q010-Q011, Q040-Q044, Q073-Q074, Q109-Q110, Q132-Q134, Q162-Q174, Q184-Q194, Q207-Q209**

Verified technical information reliable source + motorcycle/application fit + review/provenance gerektirir. `Verified` context-specific claim'dir; perfect workmanship veya outcome guarantee degildir.

Evidence vocabulary'nin temel mantigi tutarlidir:
- `Kullanici beyani`: kisinin girdigi bilgi,
- `Belgeli`: supporting evidence tasir,
- `Incelenmis`: evidence review'dan gecmistir,
- `Dogrulanmis`: belirli claim yeterli source/evidence/review ile teyit edilmistir.

Risk-adaptive explanation beklenir. Low-risk rutin note veya simple photo description'da short label yeterli olabilir. Brake/steering/electrical safety, critical technical values ve disputed maintenance/history gibi high-trust context'te claim, motorcycle, evidence, reviewer ve unresolved uncertainty aciklanmalidir.

Beginner icin evidence level/source type daha acik sade dille anlatilabilir; experienced user same evidence details/date bilgisine daha hizli ulasabilir. Ancak source, motorcycle applicability, uncertainty, conflict, critical change, safety warning ve mandatory checks high-risk/disputed context'te deneyim seviyesine gore gizlenemez veya kaldirilamaz.

Historical claim semantics iki katmanli olabilir:
1. **Current claim state:** bugun hangi bilgiye dayanilabilecegini anlatan az sayida kullanici anlamli durum,
2. **Claim event history:** dispute, evidence withdrawal, correction, resolution ve supersession gibi bugunku duruma nasil gelindigini gosteren tarihce.

Batch 07 evidence'ina gore minimum current-state anlamlari `accepted`, `disputed`, `insufficient evidence` ve `superseded` olabilir. `Evidence withdrawn` veya `resolved` her durumda ayri top-level current state olmak zorunda degildir; neden/transition event history'de kalabilir. Bu product semantics'tir, database enum/schema karari degildir.

New independent evidence disputed claim'i yeniden degerlendirebilir. Dispute ancak evidence review edilip yeterli bulunursa resolved sayilir; prior disagreement, prior decision ve resolution reason history'de kalir. New information previous claim'i tamamen silmek yerine correction/extension olarak baglanabilir.

Ilk bakista result, evidence level, source type, date ve varsa uncertainty gorunmeli; full document, review chain, previous versions ve detailed rationale daha derin detail olabilir. Bu product expectation final UI component karari degildir.

Disputed service document ve owner observation silent winner-takes-all truth modeline zorlanmaz; unresolved completion maintenance counter/future guide decisions'ta verified fact gibi kullanilmaz.

### 5. Guide detail and experience adaptation

**CONFIRMED — Q007, Q014-Q015, Q025, Q054, Q207-Q209**

Beginner icin temel unit `tek hareket + ilgili gorsel + basari kontrolu` seviyesine inebilir. Experienced user ayni verified content'in short checklist/technical-detail gorunumune hizla ulasmak ister. Low-risk context'te explanation depth degisebilir; safety, critical verification ve dispute/uncertainty high-risk context'te azaltilamaz.

Visual model: actual/marked photo, hidden connection icin drawing, sequence/motion kritikse short video, safety/measurement/check icin explicit text. Wrong-bike visual ayniymis gibi kullanilamaz; verified drawing/schema fallback olabilir.

### 6. Readiness, self-remediation, re-validation and re-entry

**CONFIRMED — Q013, Q016-Q017, Q050-Q053, Q096-Q098, Q126-Q128**

Readiness yalniz `deneyimliyim/yapabilirim` beyanina dayanamaz. Eksik kosulda assessment error check, learning/preparation/equipment acquisition/self-remediation ve new evidence ile re-validation yolu sunulur.

Professional recommendation ile mandatory application closure farklidir. External help optional support olabilir; unverified critical condition mandatory safety gate'tir. Condition yeniden saglanip equipment + motorcycle fit + critical checks yeniden verify edilince same guide'a donulebilir.

### 7. Teaching vs application and high-consequence guidance

**CONFIRMED — Q018-Q021, Q034, Q045-Q053, Q068-Q069, Q099-Q101, Q126-Q128**

High-consequence category adi tek basina content'i kapsam disi yapmaz. Teaching content okunabilir kalabilir; real motorcycle-facing application fit/equipment/environment/critical information/result verification gibi zorunlu kosullara baglidir.

First physical intervention'dan once required conditions kontrol edilir; new risk/mismatch ortaya cikarsa application o noktada durur. Professional help `sen yapamazsin` diliyle sunulmaz; missing condition, remediation ve re-entry yolu aciklanir.

### 8. Diagnosis before repair

**CONFIRMED — Q012, Q022-Q024, Q056-Q058, Q090**

Diagnosis kanit toplayarak belirsizligi azaltir. `En olasi` claim'i icin birden fazla ayirt edici evidence ve alternatives evaluation gerekir. Equal possibilities ayrica tutulur; random parts replacement onerilmez. Makul checks sonunda neden belirlenemezse `Neden dogrulanamadi` sonucu ve safe-use uncertainty ile kapanabilir.

### 9. Recovery, interruption, guide change and physical-state reconstruction

**CONFIRMED — Q025-Q028, Q042-Q043, Q059-Q060, Q096-Q101, Q178-Q183, Q195-Q200**

User stuck/mismatch/error durumunda normal progression gerekirse durur. More detail, safe recovery, evidence capture ve external help yolu sunulur.

Interrupted work'te motorcycle, guide version, last definitely completed step, in-progress step, photos, safety warnings ve preparation/readiness context korunmalidir. Unsaved step completed varsayilamaz.

Critical interruption sonrasi previous confirmations automatic carry-forward edilmemelidir. Last-step completion, removed parts, open connections, motorcycle stability, energy/pressure/temperature state ve relevant safety conditions current reality olarak yeniden kontrol edilmelidir. Motorcycle'in tasinmasi, baskasinin mudahalesi, parts movement/loss veya energy/pressure change state-drift signal'idir. User `hicbir sey degismedi` dese bile stabilization, open connections, parts location, energy state ve last critical result gibi checks salt beyanla atlanamaz.

Material guide change old physical action'i otomatik reverse ettirmez. Once progression durur, degisen step ve current physical risk aciklanir; current motorcycle state evidence ile capture edilir. Ne sokuldu/degisti ve safety condition bilinmeden reversal instruction verilmez. New guide ile safe starting point guvenilir bicimde fit edilemiyorsa application physical step tahmin etmez; teaching/state capture devam edebilir.

Bu behavior photo/check-question gibi evidence kullanabilir fakat belirli computer-vision veya recognition feasibility'si bu discovery'de kanitlanmis degildir.

### 10. Content review, correction, recall and evidence withdrawal dependency

**CONFIRMED — Q040-Q044, Q080-Q084, Q105-Q108, Q130, Q166-Q168, Q186-Q188**

Official guide human review ve source/provenance tasir. Community contribution explicit opt-in ve official guide'dan ayri status/provenance ile sunulur. Correction official guide'a direct yazilmaz.

Contribution withdrawal public content/personal info'yu kaldirmalidir. Safety review history gerekiyorsa de-identified trace kalabilir; bu legal/technical implementation karari degildir.

Evidence withdrawal source access, provenance history, current trust ve visibility'nin ayni sey olmadigini ortaya koyar. Contributor source copy'yi artik paylasmasa bile evidence'in gecmiste bir claim'de kullanilmis olmasi sessizce yok edilmez. Independent/transferred record automatic silinmez.

Withdrawn evidence evaluation'dan cikarilir ve dependent claim/guide remaining evidence ile yeniden review edilir. Yeterli independent evidence kalirsa claim review sonrasi kullanilabilir kalabilir; yetersizse verification/application korunmamalidir. Withdrawal global automatic invalidation degildir.

### 11. Maintenance/history, corrections, disputes and transfer provenance

**CONFIRMED — Q029-Q033, Q062-Q064, Q073-Q077, Q109-Q110, Q131-Q134, Q156, Q162-Q165, Q184-Q194**

Core history longitudinal trust'i korumalidir. En az motorcycle, operation, date, mileage, actor, outcome, important safety notes, evidence level ve correction history korunmali; old basic records sadece space acmak icin silinmemelidir.

Wrong record duzeltilebilir fakat old/new value, time, actor/reason ve evidence izi kaybolmaz. Important historical claim'de who/when/evidence/correction/dispute context izlenebilir kalmalidir. `Degistirilemez iz` product-level historical integrity beklentisidir; specific immutable-storage architecture karari degildir.

Transfer correction rejected olursa accepted record ile disputed proposal ayri claims olarak kalir. Multiple ownership transfers owner/period/coverage/gaps ile gorunur; partial periods birlestirilip `complete history` diye sunulamaz.

New independent evidence eski dispute'i silent delete etmez. Evidence hangi claim'i destekledigi, current decision'i degistirip degistirmedigi ve remaining uncertainty ile birlikte review edilir. New explanation previous claim'e correction/extension olarak baglanabilir.

Paid-service document ile owner evidence celisirse unresolved service completion future maintenance veya guide decisions'a verified completion gibi aktarilmaz.

### 12. Maintenance timing and uncertainty

**CONFIRMED — Q031-Q033, Q061, Q064, Q075-Q077, Q184-Q185**

Manufacturer motorcycle-specific km/time intervals ve verified completion baseline'dir. Verified exception varsa gerekcesiyle apply edilir. Modified/new part interval unknown ise old interval automatic kullanilmaz veya new interval uydurulmaz.

Disputed completion maintenance counter'i certainty ile reset etmemelidir.

### 13. Notifications, correction reach-back and affected-user depth

**CONFIRMED — Q032-Q033, Q070-Q072, Q111-Q113, Q167, Q204-Q206**

Routine reminders group/disable/postpone edilebilir; critical safety routine reminders arasinda kaybolmaz. Long absence notification storm yerine prioritized catch-up summary beklenir.

Correction/withdrawal reach-back user'in interaction depth'i ve change risk'i ile degisebilir. Guide'i yalniz gormek zayif signal; relevant step'i acmak, uyguladigini onaylamak, evidence eklemek ve completion record olusturmak daha guclu affected-user signals'dir.

Ongoing work affected ise relevant flow durabilir ve continue oncesi required re-check gosterilir. Completed work affected ise user'a completed work'un etkilenip etkilenmedigi ve hangi sonucu yeniden kontrol edecegi anlatilmalidir. Exact notification channel/SLA bu discovery'nin karari degildir.

### 14. Time/cost estimate trust boundary

**CONFIRMED — Q013, Q078-Q079**

Time exact promise degil range + uncertainty; cost parts/consumables/tools/labor + exclusions + price date + assumptions ile sunulmalidir.

### 15. Commercial neutrality, free-core trust and premium scale/coordination

**CONFIRMED — Q065, Q085-Q088, Q114-Q115, Q144-Q146, Q156-Q161, Q210-Q215**

Commercial/sponsor influence technical fit'i veya guide content'i degistiremez.

Payment status trust invariants'i zayiflatamaz. Bir record erisilebilirse attribution/provenance, source/evidence status, withdrawal/correction impact, safety warnings ve existing-history integrity de erisilebilir olmalidir.

Core/free trust boundary en az sunlari korur:
- required safety warnings/visuals/checks,
- kullaniciya acik olan bir operation/guide'i guvenli tamamlama icin gereken steps,
- basic/reasonable longitudinal history,
- safety/understanding icin gerekli temel evidence,
- user data export,
- motorcycle contexts arasinda data/state karismamasi,
- basic shared-bike trust sunuldugunda invitation/limited permission/attribution/revoke/private-content separation/history integrity.

Premium/storage boundary mevcut basic history'yi gizleme/silme yoluyla yaratilmamalidir. Limit doldugunda new large uploads yonetilebilir fakat existing core history/safety evidence erisilebilir ve exportable kalmalidir.

Expanded evidence archive cok sayida high-resolution photo, long video ve genis document archive gibi high-volume media value ile baslar. Advanced garage/collaboration cross-bike analysis, bulk planning, advanced archive search, more participants, richer roles, task assignment, approval flows ve detailed permission coordination gibi scale/coordination value'da ayrisir.

**PROPOSED — Batch 07 supplemental user note, NOT APPROVED/LOCKED:** Guncel free-tier adayi `1 aktif motosiklet + 1 davetli + temel history/uyarilar + user'in sectigi 1 tam rehber`; additional motorcycles ve guides paid olabilir; existing records sonradan kilitlenmemeli. Bu proposal Q159/Q161'deki daha genis free multi-bike yorumunu daraltiyor ve Q065/Q087/Q145 core-guide yorumuyla entitlement lifecycle acisindan netlestirme gerektiriyor. `02_DISCOVERY/CONFLICTS.md` icinde izlenir. Active/inactive motorcycle, guide switching, active-repair continuation ve `existing records unlocked` semantigi Q-0065—Q-0069'da OPEN'dir.

Exact quota, tier, price, subscription model ve business viability bu discovery'de kesinlesmis degildir.

### 16. User segmentation minimum value

**CONFIRMED — Q141-Q143, Q153-Q161, Q210-Q215**

- Beginner owner: learning + safe detailed application.
- Experienced owner: speed + accuracy + verified concise guidance.
- Record-only owner: history + maintenance schedule/reminder.
- Multi-bike context: motorcycle states birbirini etkilemez; simultaneous free entitlement ayrica OPEN monetization konusudur.
- Shared-family context: authorized, attributed records; basic trust payment statusuna gore kaybolmaz.
- Hobby helper: actor-attributed contribution.

Accuracy hicbir segmentte cost reduction'dan dusuk priority olmamalidir.

### 17. Shared motorcycle, contributor evidence and access lifecycle

**CONFIRMED — Q118-Q119, Q138-Q140, Q169-Q171, Q186-Q188, Q210-Q215**

Owner access grants collaboration. Actor, timestamp, evidence ve edits visible olmali; private notes automatic share edilmemeli ve permission revocable olmalidir.

Motorcycle-record ownership, contributor-owned evidence ve historical attribution ayni kavram degildir. Owner own motorcycle record lifecycle'ini yonetebilirken collaborator'in independent evidence'i sessizce yok edilmemelidir. Contributor own photo/document evidence'i geri cekebilir; linked history'de evidence-withdrawal trace kalmali ve affected claim trust remaining evidence ile yeniden degerlendirilmelidir.

Access revoke future viewing/adding'i durdurur fakat prior attributed operation records actor/time ile history'de kalabilir. Independent/transferred record source withdrawal nedeniyle otomatik silinmez.

Basic shared-bike trust'ta invitation, limited permission, attribution, revoke, provenance, private-content separation ve historical integrity core trust requirements'dir. Premium collaboration daha fazla participants, richer roles/tasks/approvals ve coordination scale'i uzerinden ayrisabilir.

Exact free invitee entitlement Batch 07 supplemental proposalunda `1 invitee` olarak onerilmistir; APPROVED/LOCKED degildir ve downgrade/inactive lifecycle Q-0069'da aciktir.

### 18. Ownership transfer, repeated transfers and archive

**CONFIRMED — Q120-Q121, Q135-Q137, Q162-Q165, Q189-Q194**

Selective transfer `owner-selected / incomplete history` olarak represented edilmelidir. Covered period ve visible gaps gosterilir; non-transferred private content acilmaz.

Repeated transfers her owner/donem/coverage ile ayri provenance tasir. Partial histories tek complete chain gibi merge edilmez. `Complete history` iddiasi unknown periods varsa kullanilmaz; trust coverage transferred periods ile sinirli gosterilir.

Transfer sonrasi silent overwrite yoktur. Former owner correction/new-info proposal ile current owner acceptance/rejection ayri historical claims olarak kalabilir; prior version/evidence izi korunur. Later independent evidence current state'i degistirse bile prior dispute ve resolution reason history'de gorunur kalir.

Archive delete degildir: active garage'dan cikarir, history'yi korur, reversible'dir.

### 19. Actual deletion and data ownership

**CONFIRMED — Q092-Q095, Q129-Q131, Q169-Q171, Q186-Q188**

Actual motorcycle deletion oncesi affected history/photos/measurements/reminders ve collaboration-related scope anlasilir olmalidir. User'in own copy linked data removal expectation'i vardir; baska kisinin independent transferred data'si automatic silinmemelidir.

Contributor kendi kanitini geri cekebilir; source access ve visibility degisebilir fakat past provenance/history automatic yok olmaz. Withdrawal affected claim'i remaining evidence ile yeniden degerlendirmelidir. Legal retention/backup/privacy implementation bu product discovery'nin karari degildir.

### 20. Offline/freshness semantics

**CONFIRMED — Q090-Q091, Q122, Q147-Q149, Q178-Q180, Q195-Q200**

Offline access ile application authorization ayni sey degildir. Freshness especially safety notice, technical value ve changeable procedure-order claims'de application-critical olabilir.

Stale critical content teaching/reference olarak kalabilir; current instruction gibi gorunemez. Critical freshness verify edilemiyorsa motorcycle-facing application re-check'e kadar kapanir. Re-check materially changed guide getirirse physical-state reconstruction/remapping gerekir; old physical action control edilmeden reverse/continue edilmez.

### 21. Localization and active-repair accessibility

**CONFIRMED — Q124-Q125, Q150-Q152, Q181-Q183, Q198-Q200, Q207-Q209**

Clear Turkish, familiar units ve experience-appropriate terminology beklenir. Alternative text/visual/audio/large/easy controls useful olabilir.

Convenience safety invariant'i kaldiramaz. Critical confirmation ve resume re-validation korunur; previous state interruption sonrasi automatic valid sayilmaz. Explanation depth experience'e gore degisebilir fakat high-risk source/fit/uncertainty/conflict/safety facts korunur.

### 22. Trust-breakers / non-goal direction

**CONFIRMED — Q035, Q065, Q088, Q095, Q096-Q110, Q122, Q126-Q215**

Trust-breaking behavior includes:
- fabricated/unverified technical certainty,
- hidden danger veya self-assertion bypass of critical gate,
- false definitive diagnosis,
- dangerous-work success guarantee,
- teaching content masquerading as current application instruction,
- critical safety/core completion behind paywall,
- existing history/provenance/trust metadata'nin payment change ile retroactive kilitlenmesi,
- silent history/provenance overwrite/loss,
- cross-account/cross-motorcycle state mixing,
- partial transferred history presented as complete,
- withdrawn evidence ignored while claim silently stays verified,
- historical dispute silently erased after new evidence,
- disputed service record used as certain completion,
- stale critical application left open without re-check,
- interruption resume without current-state revalidation,
- old physical change'in new guide'a unsafe/guessed reversal'i,
- accessibility shortcut removing critical confirmation,
- commercial influence on technical recommendation.

## Working Interpretations — INFERRED, NOT DECIDED

- `Teaching vs application` yatay product trust principle olabilir.
- `Evidence-gated re-entry` readiness/recovery modelinin ortak semantigi olabilir.
- Auditability guide version, history, moderation, collaboration, ownership transfer ve export boyunca ortak principle olabilir.
- `Verified` kelimesinden cok `hangi claim verify edildi` product trust acisindan esastir.
- History tek mutable truth row'dan cok attributed claims + evidence + correction/dispute context'i tasiyan product concept olabilir; bu bir database architecture karari degildir.
- Historical trust az sayida **current claim states** + daha ayrintili **claim event history** ile anlatilabilir.
- `Resume` son gorulen step'e donmek degil, son known-safe state'i current physical reality ile yeniden establish etmek olabilir.
- Correction reach-back interaction depth + risk ile agirliklandirilabilir.
- Experience adaptation truth/safety content'ini degil explanation depth/speed'i degistirebilir.
- Premium collaboration trust controls'dan degil participant/motorcycle scale ve coordination complexity'den deger uretebilir.
- Motorcycle isolation bir correctness/trust invariant'i olabilir; simultaneous free-active motorcycle entitlement ayrica monetization kararidir.
- Batch 07 free-tier proposal explicit user preference candidate'dir; Gate 2 oncesi entitlement lifecycle'i netlesmeden final product policy sayilmamalidir.

Bu yorumlar discovery ilerledikce test edilmeye devam edecektir.
