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

## Product Model — Current Working Synthesis

### 1. Core product identity and priority

**CONFIRMED — Phase 1, Q006-Q007, Q089, Q116-Q117, Q138-Q143**

MotoBakim'in birincil hedefi, bireysel motosiklet sahibinin kendi motosikletindeki bakım, mekanik ve elektriksel islemleri neyi/neden/nasil yaptigini anlayarak guvenli bicimde tamamlayabilmesidir.

Ilk product priority:
1. yeni/az deneyimli self-service owner,
2. deneyimli self-service owner,
3. temel record/history tracking ihtiyaci.

Record-only owner, multi-bike owner, shared-family context ve hobby helper anlamli desteklenen baglamlardir. Professional/servis ilk urunun dogrudan ana target'i degildir; owner davetiyle contribution/collaboration participant olabilir. Ayrı professional work-management product ileride dusunulebilir fakat owner-first self-service deneyimini degistirmemelidir.

### 2. Entry modes and segment-specific first value

**CONFIRMED — Q006, Q012, Q022, Q090, Q123, Q153-Q155, Q175-Q177**

Kullanici yapmak istedigi islemi bilerek, yalniz bir belirtiyle, yalniz history/reminder tutmak icin veya multi/shared motorcycle baglamiyla gelebilir.

Self-service first-use'ta motosiklet secilip guide value hizla gorulmelidir. Record-only user motosikletini ekleyip son islemini kaydetmeli ve approaching maintenance value'yu erken anlayabilmelidir. Shared/multi-bike user motorcycle separation ve contribution attribution degerini erken gorebilmelidir.

Account/profile ilk degerden once zorunlu olmamali. Ilk real record'u kalici saklama, cross-device devam veya collaboration baslatma ihtiyaci profile gecis icin dogal product trigger'dir.

Local-to-profile transition trust-preserving olmalidir: aktarilacak local scope onceden gorunmeli, records successful transition teyit edilmeden sessizce kaybolmamali, duplicate/conflicting groups source/date/differences ile review edilebilmeli ve silent overwrite yapilmamalidir. Kullanici profile gecmezse guide reading, motorcycle selection, local history ve interrupted-step continuation gibi local degerler devam edebilmelidir. Teknik auth/sync implementation bu asamada secilmez.

### 3. Motorcycle-guide fit, variant certainty and modification fit

**CONFIRMED — Q008-Q009, Q019, Q026, Q036-Q039, Q066-Q067, Q102-Q104**

Guide, gercek motosikletle yeterli fit kurulmadan motosiklete ozel application instruction gibi sunulamaz. Marka/model/yil, motor hacmi, donanim, relevant features, visible hardware ve fotograflar kullanilabilir. Kullanici technical code/document scavenger hunt'a zorlanmamalidir.

Observable evidence yetersizse eksik ayrim gosterilir ve variant-specific application kapanir. Bu visual identification'in her motosiklette teknik olarak yeterli oldugu feasibility iddiasi degildir.

Modified system'de factory guide otomatik uygun sayilmaz. Common aftermarket degisiklik verified fit varsa adapted guide'a dahil edilebilir. Unique/custom modification'da evidence gap aciklanabilir ve teaching-only bilgi kalabilir; zarar verebilecek application adimlari fit dogrulanana kadar acilmaz.

### 4. Trust, provenance and evidence semantics

**CONFIRMED — Q010-Q011, Q040-Q044, Q073-Q074, Q109-Q110, Q132-Q134, Q162-Q174, Q184-Q185**

Verified technical information reliable source + motorcycle/application fit + review/provenance gerektirir. `Verified` context-specific claim'dir; perfect workmanship veya outcome guarantee degildir.

Evidence vocabulary'nin temel mantigi tutarlidir:
- `Kullanici beyani`: kisinin girdigi bilgi,
- `Belgeli`: supporting evidence tasir,
- `Incelenmis`: evidence review'dan gecmistir,
- `Dogrulanmis`: belirli claim yeterli source/evidence/review ile teyit edilmistir.

Risk-adaptive explanation beklenir. Low-risk rutin note veya simple photo description'da short label yeterli olabilir. Brake/steering/electrical safety, critical technical values ve disputed maintenance/history gibi high-trust context'te claim, motorcycle, evidence, reviewer ve unresolved uncertainty aciklanmalidir.

Ilk bakista result, evidence level, source type, date ve varsa uncertainty gorunmeli; full document, review chain, previous versions ve detailed rationale daha derin detail olabilir. Bu product expectation final UI component karari degildir.

Disputed claims silent winner-takes-all truth modeline zorlanmaz. Service document ile owner observation celisirse iki source ayri claims olarak tutulur ve unresolved completion maintenance counter/future guide decisions'ta verified fact gibi kullanilmaz.

### 5. Guide detail and experience adaptation

**CONFIRMED — Q007, Q014-Q015, Q025, Q054**

Beginner icin temel unit `tek hareket + ilgili gorsel + basari kontrolu` seviyesine inebilir. Experienced user ayni verified content'in short checklist/technical-detail gorunumune hizla ulasmak ister. Safety ve critical verification deneyim seviyesine gore azaltilamaz.

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

### 9. Recovery, interruption, guide change and physical-state remapping

**CONFIRMED — Q025-Q028, Q042-Q043, Q059-Q060, Q096-Q101, Q178-Q183**

User stuck/mismatch/error durumunda normal progression gerekirse durur. More detail, safe recovery, evidence capture ve external help yolu sunulur.

Interrupted work'te motorcycle, guide version, last definitely completed step, in-progress step, photos, safety warnings ve preparation/readiness context korunmalidir. Unsaved step completed varsayilamaz.

Critical interruption sonrasi previous confirmations automatic carry-forward edilmemelidir. Motorcycle stability, energy/temperature state, removed parts, open connections ve last critical step completion yeniden kontrol edilebilir. User nerede kaldigindan emin degilse next step'e otomatik gecilmez; last known safe state'ten photo/symptom/check questions ile current state yeniden establish edilir ve unresolved durumda application durur.

Online/freshness re-check sonrasi guide materially degismisse user once change, safety impact ve immediate-stop requirement'i gormek ister. Old/new guide transition current physical state new guide'a guvenilir bicimde remap edilmeden application continuation'a izin vermemelidir. Existing physical state fit edilemiyorsa teaching acik kalabilir, application kapanir ve external support tek/default exit olmaz.

### 10. Content review, correction, recall and community dependency

**CONFIRMED — Q040-Q044, Q080-Q084, Q105-Q108, Q130, Q166-Q168**

Official guide human review ve source/provenance tasir. Community contribution explicit opt-in ve official guide'dan ayri status/provenance ile sunulur. Correction official guide'a direct yazilmaz.

Contribution withdrawal public content/personal info'yu kaldirmalidir. Safety review history gerekiyorsa de-identified trace kalabilir; bu legal/technical implementation karari degildir.

Withdrawn community evidence daha once official guide/claim'i desteklemisse dependency-aware re-review gerekir. Aynı claim yeterli independent sources + motorcycle-fit evidence + prior review ile hala destekleniyorsa review sonrasi kalabilir. Remaining evidence yetersizse ilgili verification status/application section korunmamalidir.

Withdrawal safety warning, technical value veya applied critical step'i etkiliyorsa ilgili guide users correction/re-review bilgisi almayi bekler. Stylistic/narrative-only change ayni severity'de user reach-back gerektirmez.

### 11. Maintenance/history, correction and disputed claims

**CONFIRMED — Q029-Q033, Q062-Q064, Q073-Q077, Q109-Q110, Q131-Q134, Q156, Q162-Q165, Q184-Q185**

Core history longitudinal trust'i korumalidir. En az motorcycle, operation, date, mileage, actor, outcome, important safety notes, evidence level ve correction history korunmali; old basic records sadece space acmak icin silinmemelidir.

Wrong record duzeltilebilir fakat old/new value, time, actor/reason ve evidence izi kaybolmaz. Important historical claim'de who/when/evidence/correction/dispute context izlenebilir kalmalidir. `Degistirilemez iz` product-level historical integrity beklentisidir; specific immutable-storage architecture karari degildir.

Transfer correction rejected olursa accepted record ile disputed proposal ayri claims olarak kalir. Multiple ownership transfers owner/period/coverage/gaps ile gorunur; partial periods birlestirilip `complete history` diye sunulamaz.

Paid-service document ile owner evidence celisirse unresolved service completion future maintenance veya guide decisions'a verified completion gibi aktarilmaz.

### 12. Maintenance timing and uncertainty

**CONFIRMED — Q031-Q033, Q061, Q064, Q075-Q077, Q184-Q185**

Manufacturer motorcycle-specific km/time intervals ve verified completion baseline'dir. Verified exception varsa gerekcesiyle apply edilir. Modified/new part interval unknown ise old interval automatic kullanilmaz veya new interval uydurulmaz.

Disputed completion maintenance counter'i certainty ile reset etmemelidir.

### 13. Notifications, correction reach-back and catch-up

**CONFIRMED — Q032-Q033, Q070-Q072, Q111-Q113, Q167**

Routine reminders group/disable/postpone edilebilir; critical safety routine reminders arasinda kaybolmaz. Long absence notification storm yerine prioritized catch-up summary beklenir.

Historical content/evidence withdrawal safety warning, technical value veya used critical step'i etkiliyorsa affected users correction/re-review notification almayi bekler. Exact affected-user boundary sonraki discovery gap'idir.

### 14. Time/cost estimate trust boundary

**CONFIRMED — Q013, Q078-Q079**

Time exact promise degil range + uncertainty; cost parts/consumables/tools/labor + exclusions + price date + assumptions ile sunulmalidir.

### 15. Commercial neutrality, core history and expanded storage boundary

**CONFIRMED — Q065, Q085-Q088, Q114-Q115, Q144-Q146, Q156-Q161**

Commercial/sponsor influence technical fit'i veya guide content'i degistiremez.

Free core en az sunlari korumali:
- motorcycle-specific core guide,
- required safety warnings/visuals/checks,
- operation completion icin gereken steps,
- basic/reasonable longitudinal history,
- safety/understanding icin gerekli temel evidence,
- user data export,
- basic multi-bike isolation.

Premium/storage boundary mevcut basic history'yi gizleme/silme yoluyla yaratilmamalidir. Limit doldugunda new large uploads yonetilebilir fakat existing core history/safety evidence erisilebilir ve exportable kalmalidir.

Expanded evidence archive cok sayida high-resolution photo, long video ve genis document archive gibi high-volume media value ile baslar. Advanced garage ise cross-bike analysis, bulk planning, richer collaboration ve large-archive search gibi cross-bike/scale value'da ayrisir.

Exact quota, tier, price ve business viability bu discovery'den cikmaz.

### 16. User segmentation minimum value

**CONFIRMED — Q141-Q143, Q153-Q161**

- Beginner owner: learning + safe detailed application.
- Experienced owner: speed + accuracy + verified concise guidance.
- Record-only owner: history + maintenance schedule/reminder.
- Multi-bike owner: each motorcycle history/mileage/reminder/active work independent.
- Shared-family context: authorized, attributed records.
- Hobby helper: actor-attributed contribution.

Accuracy hicbir segmentte cost reduction'dan dusuk priority olmamalidir.

### 17. Shared motorcycle, contributor evidence and access lifecycle

**CONFIRMED — Q118-Q119, Q138-Q140, Q169-Q171**

Owner access grants collaboration. Actor, timestamp, evidence ve edits visible olmali; private notes automatic share edilmemeli ve permission revocable olmalidir.

Motorcycle-record ownership, contributor-owned evidence ve historical attribution ayni kavram degildir. Owner own motorcycle record lifecycle'ini yonetebilirken collaborator'in independent evidence'i sessizce yok edilmemelidir. Contributor own photo/document evidence'i geri cekebilir; linked history'de evidence-withdrawal trace kalmali ve affected claim trust yeniden degerlendirilmelidir.

Access revoke future viewing/adding'i durdurur fakat prior attributed operation records actor/time ile history'de kalabilir. Contributor evidence visibility'nin independent transferred copies gibi edge case'leri hala aciktir.

### 18. Ownership transfer, repeated transfers and archive

**CONFIRMED — Q120-Q121, Q135-Q137, Q162-Q165**

Selective transfer `owner-selected / incomplete history` olarak represented edilmelidir. Covered period ve visible gaps gosterilir; non-transferred private content acilmaz.

Repeated transfers her owner/donem/coverage ile ayri provenance tasir. Partial histories tek complete chain gibi merge edilmez. `Complete history` iddiasi unknown periods varsa kullanilmaz; trust coverage transferred periods ile sinirli gosterilir.

Transfer sonrasi silent overwrite yoktur. Former owner correction/new-info proposal ile current owner acceptance/rejection ayri historical claims olarak kalabilir; prior version/evidence izi korunur.

Archive delete degildir: active garage'dan cikarir, history'yi korur, reversible'dir.

### 19. Actual deletion and data ownership

**CONFIRMED — Q092-Q095, Q129-Q131, Q169-Q171**

Actual motorcycle deletion oncesi affected history/photos/measurements/reminders ve collaboration-related scope anlasilir olmalidir. User'in own copy linked data removal expectation'i vardir; baska kisinin independent transferred data'si otomatik silinmemelidir.

Contributor kendi kanitini geri cekebilir; bu claim history'yi sessizce ayni verified state'te birakmamalidir. Legal retention/backup/privacy implementation bu product discovery'nin karari degildir.

### 20. Offline/freshness semantics

**CONFIRMED — Q090-Q091, Q122, Q147-Q149, Q178-Q180**

Offline access ile application authorization ayni sey degildir. Freshness especially safety notice, technical value ve changeable procedure-order claims'de application-critical olabilir.

Stale critical content teaching/reference olarak kalabilir; current instruction gibi gorunemez. Critical freshness verify edilemiyorsa motorcycle-facing application re-check'e kadar kapanir. Re-check materially changed guide getirirse physical-state remapping gerekir.

### 21. Localization and active-repair accessibility

**CONFIRMED — Q124-Q125, Q150-Q152, Q181-Q183**

Clear Turkish, familiar units ve experience-appropriate terminology beklenir. Alternative text/visual/audio/large/easy controls useful olabilir.

Convenience safety invariant'i kaldiramaz. Critical confirmation ve resume re-validation korunur; previous state interruption sonrasi automatic valid sayilmaz.

### 22. Trust-breakers / non-goal direction

**CONFIRMED — Q035, Q065, Q088, Q095, Q096-Q110, Q122, Q126-Q185**

Trust-breaking behavior includes:
- fabricated/unverified technical certainty,
- hidden danger veya self-assertion bypass of critical gate,
- false definitive diagnosis,
- dangerous-work success guarantee,
- teaching content masquerading as current application instruction,
- critical safety/core history/core completion behind paywall,
- silent history/provenance overwrite/loss,
- cross-account/cross-motorcycle state mixing,
- partial transferred history presented as complete,
- withdrawn evidence ignored while claim silently stays verified,
- disputed service record used as certain completion,
- stale critical application left open without re-check,
- interruption resume without current-state revalidation,
- accessibility shortcut removing critical confirmation,
- commercial influence on technical recommendation.

## Working Interpretations — INFERRED, NOT DECIDED

- `Teaching vs application` yatay product trust principle olabilir.
- `Evidence-gated re-entry` readiness/recovery modelinin ortak semantigi olabilir.
- Auditability guide version, history, moderation, collaboration, ownership transfer ve export boyunca ortak principle olabilir.
- `Verified` kelimesinden cok `hangi claim verify edildi` product trust acisindan esastir.
- History tek mutable truth row'dan cok attributed claims + evidence + correction/dispute context'i tasiyan product concept olabilir; bu bir database architecture karari degildir.
- `Resume` son gorulen step'e donmek degil, son known-safe state'i current physical reality ile yeniden establish etmek olabilir.
- Basic multi-bike entitlement degil motorcycle-isolation invariant'i olarak ele alinabilir.
- Premium boundary historical trust'i azaltmak yerine expanded media/cross-bike advanced value uzerinden kurulabilir.

Bu yorumlar discovery ilerledikce test edilmeye devam edecektir.
