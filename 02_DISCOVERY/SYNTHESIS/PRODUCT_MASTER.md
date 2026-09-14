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

**CONFIRMED — Q006, Q012, Q022, Q090, Q123, Q153-Q155**

Kullanici:
- yapmak istedigi islemi bilerek,
- yalniz bir belirtiyle,
- yalniz history/reminder tutmak icin,
- multi/shared motorcycle baglamiyla gelebilir.

Self-service first-use'ta motosiklet secilip guide value hizla gorulmelidir. Record-only user ilk dakikada motosikletini ekleyip son islemini kaydetmeli ve approaching maintenance value'yu anlayabilmelidir. Shared/multi-bike user motosiklet ayrimini ve contribution attribution'ini erken gorebilmelidir.

Account/profile ilk degerden once zorunlu olmamali. Ilk real record'u kalici saklama, cross-device devam veya collaboration baslatma ihtiyaci profile gecis icin dogal product trigger'dir. Kullaniciya neden profile ihtiyac oldugu ve mevcut local data'ya ne olacagi onceden aciklanmalidir. Teknik auth/sync modeli bu asamada secilmez.

### 3. Motorcycle-guide fit, variant certainty and modification fit

**CONFIRMED — Q008-Q009, Q019, Q026, Q036-Q039, Q066-Q067, Q102-Q104**

Guide, gercek motosikletle yeterli fit kurulmadan motosiklete ozel application instruction gibi sunulamaz. Marka/model/yil, motor hacmi, donanim, relevant features, visible hardware ve fotograflar kullanilabilir. Kullanici technical code/document scavenger hunt'a zorlanmamalidir.

Observable evidence yetersizse eksik ayrim gosterilir ve variant-specific application kapanir. Bu visual identification'in her motosiklette teknik olarak yeterli oldugu feasibility iddiasi degildir.

Modified system'de factory guide otomatik uygun sayilmaz. Common aftermarket degisiklik verified fit varsa adapted guide'a dahil edilebilir. Unique/custom modification'da evidence gap aciklanabilir ve teaching-only bilgi kalabilir; zarar verebilecek application adimlari fit dogrulanana kadar acilmaz.

### 4. Trust, provenance and evidence semantics

**CONFIRMED — Q010-Q011, Q040-Q044, Q073-Q074, Q109-Q110, Q132-Q134**

Verified technical information reliable source + motorcycle/application fit + review/provenance gerektirir. Source version/relevant section, review context ve applicable claim gorulebilmelidir.

Evidence vocabulary'nin temel mantigi tutarlidir:
- `Kullanici beyani`: kisinin girdigi bilgi,
- `Belgeli`: supporting evidence tasir,
- `Incelenmis`: kanit review'dan gecmistir,
- `Dogrulanmis`: belirli claim yeterli source/evidence/review ile teyit edilmistir.

Ancak `verified` claim'i context-specific'tir. Verified maintenance record `islemin yapildigina yeterli evidence var` anlamina gelir; perfect workmanship guarantee degildir. Verified technical guide ise source + motorcycle fit + application-step suitability claim'ini tasir.

Safety value, technical value, ownership transfer ve disputed record gibi high-trust baglamlarda label tek basina yeterli olmayabilir; `neyin hangi kanit/review ile dogrulandigi ve neyin dogrulanmadigi` acikca anlatilmalidir.

### 5. Guide detail and experience adaptation

**CONFIRMED — Q007, Q014-Q015, Q025, Q054**

Beginner icin temel unit `tek hareket + ilgili gorsel + basari kontrolu` seviyesine inebilir. Experienced user ayni verified content'in short checklist/technical-detail gorunumune hizla ulasmak ister. Safety ve critical verification deneyim seviyesine gore azaltilamaz.

Visual model: actual/marked photo, hidden connection icin drawing, sequence/motion kritikse short video, safety/measurement/check icin explicit text. Wrong-bike visual ayniymis gibi kullanilamaz; verified drawing/schema fallback olabilir.

### 6. Readiness, self-remediation, re-validation and re-entry

**CONFIRMED — Q013, Q016-Q017, Q050-Q053, Q096-Q098, Q126-Q128**

Readiness yalniz `deneyimliyim/yapabilirim` beyanina dayanamaz. Eksik kosul varsa:
1. once assessment'in yanlis olup olmadigi kontrol edilebilir,
2. learning/preparation/equipment acquisition/self-remediation yolu sunulur,
3. yeni photo/measurement/alternative check ile re-validation yapilabilir,
4. kosul saglaninca equipment + motorcycle fit + critical checks yeniden dogrulanarak ayni guide'a donulebilir.

Professional recommendation ile mandatory application closure ayni sey degildir. Professional help kullanicinin degerlendirebilecegi option olabilir. Unverified critical condition ise user preference'dan bagimsiz mandatory safety gate'tir. Self-assertion onceki stop kararini kaldiramaz.

### 7. Teaching vs application and high-consequence guidance

**CONFIRMED — Q018-Q021, Q034, Q045-Q053, Q068-Q069, Q099-Q101, Q126-Q128**

High-consequence category adi tek basina content'i kapsam disi yapmaz. Teaching content okunabilir kalabilir. Gercek motorcycle-facing application ise fit/equipment/environment/critical information/result verification gibi zorunlu kosullara baglidir.

First physical intervention'dan once required conditions kontrol edilir; islem sirasinda yeni risk/mismatch ortaya cikarsa application o noktada durur.

Professional help `sen yapamazsin` diliyle sunulmaz. Hangi kosulun dogrulanmadigi, nasil giderilebilecegi ve re-entry yolu aciklanir. Symptom capture, photo, preparation, learning ve result-check destegi external help secilse bile devam eder.

### 8. Diagnosis before repair

**CONFIRMED — Q012, Q022-Q024, Q056-Q058, Q090**

Diagnosis kanit toplayarak belirsizligi azaltir. `En olasi` claim'i icin birden fazla ayirt edici evidence ve alternatives evaluation gerekir. Equal possibilities ayrica tutulur; random parts replacement onerilmez. Makul checks sonunda neden belirlenemezse `Neden dogrulanamadi` sonucu, performed checks ve safe-use uncertainty ile kapanabilir.

### 9. Recovery, interruption and version changes

**CONFIRMED — Q025-Q028, Q042-Q043, Q059-Q060, Q096-Q101**

User stuck/mismatch/error durumunda normal progression gerekirse durur. More detail, safe recovery, evidence capture ve external help yolu sunulur. Interrupted work'te last step, removed parts, measurements, photos/notes ve guide version korunur.

Guide change yarim ise sessizce uygulanmaz. Critical correction varsa old flow durur; current physical motorcycle state new guide ile yeniden fit edilirken progress/notes korunur.

### 10. Content review, correction, recall and community boundary

**CONFIRMED — Q040-Q044, Q080-Q084, Q105-Q108, Q130**

Official guide human review ve source/provenance tasir. Community contribution explicit opt-in ve official guide'dan ayri status/provenance ile sunulur. Correction official guide'a direct yazilmaz; source, motorcycle fit ve safety effect review edilir.

Moderation reason explicit/respectful olmali; correction/re-submit/appeal yolu olabilir. Repeated wrong contribution pre-review'a, intentional/repeated dangerous contribution sharing restriction'a gidebilir. Unverified useful experience `unverified personal experience` olarak kalabilir fakat official step olamaz.

Contribution withdrawal'da public content kaldirilmali ve contributor personal information silinmelidir. Safety review history gerekiyorsa de-identified trace product expectation olarak kabul edilebilir; bu legal/technical implementation karari degildir. Withdrawn published correction affected guide re-review gerektirebilir.

### 11. Maintenance/history and edit trail

**CONFIRMED — Q029-Q033, Q062-Q064, Q073-Q077, Q109-Q110, Q131-Q134**

History rich ve auditable olmalidir: date/km, work/reason, parts/materials, measurements/checks, photos/notes, actor ve guide version gibi context korunur. Wrong record duzeltilebilir fakat old/new value, time ve reason kaybolmaz.

External service/hobby work provenance ile kaydedilir. Paid role otomatik `verified` sayilmaz. Export standard olarak source/provenance, evidence level, significant corrections ve dates'i tasimalidir; data export core right'tir, premium olamaz.

### 12. Maintenance timing and uncertainty

**CONFIRMED — Q031-Q033, Q061, Q064, Q075-Q077**

Manufacturer motorcycle-specific km/time intervals ve verified completion kaydi baseline'dir. Verified exception varsa gerekcesiyle apply edilir. Modified/new part interval unknown ise old interval otomatik kullanilmaz veya new interval uydurulmaz; uncertainty gorunur olur.

Multiple overdue work harm/use impact + delay + verified conditions ile explainable priority alir.

### 13. Notifications and catch-up

**CONFIRMED — Q032-Q033, Q070-Q072, Q111-Q113**

Routine reminders group/disable/postpone edilebilir. Current user important-nonurgent overdue item icin daily spam yerine weekly-at-most summary tercih etmektedir; global locked cadence degildir.

Critical safety routine reminders arasinda kaybolmaz. App acilisinda safety summary, delay consequence ve direct next action gorunur. Multiple critical items harm/urgency ile siralanir. Long absence sonrasi notification storm yerine single catch-up summary beklenir.

### 14. Time/cost estimate trust boundary

**CONFIRMED — Q013, Q078-Q079**

Time exact promise degil range + uncertainty olarak; cost part/consumable/tool/labor components + exclusions + price date + assumptions ile sunulmalidir.

### 15. Commercial neutrality and free-core boundary

**CONFIRMED — Q065, Q085-Q088, Q114-Q115, Q144-Q146**

Commercial/sponsor influence technical fit'i, alternatives visibility'yi veya guide content'i degistiremez.

Free core en az sunlari korumali:
- motorcycle-specific core guide,
- required safety warnings/visuals/checks,
- operation completion icin gereken steps,
- basic/reasonable maintenance history,
- user data export,
- birkaç motosikleti ayri tutabilme.

Large media archive, advanced comparative analysis, ongoing advanced analytics ve extensive collaboration premium candidate olabilir. Ongoing service value subscription-like; ongoing service gerektirmeyen optional personalization/print output one-time-like hissedilebilir. Bu product expectation final price/package/business viability karari degildir.

### 16. User segmentation minimum value

**CONFIRMED — Q141-Q143**

- Beginner owner: learning + safe detailed application.
- Experienced owner: speed + accuracy + verified concise guidance.
- Record-only owner: history + maintenance schedule/reminder.
- Multi-bike owner: motorcycle contexts clearly separated.
- Shared-family context: authorized, attributed records.
- Hobby helper: actor-attributed contribution.

Accuracy hicbir segmentte cost reduction'dan dusuk priority olmamalidir.

### 17. Shared motorcycle, hobby helper and paid service

**CONFIRMED — Q118-Q119, Q138-Q140**

Owner access grants collaboration. Actor, timestamp, evidence ve edits visible olmali; private notes automatic share edilmemeli ve permission revocable olmalidir. Hobby help ile paid service same record type gibi gorunmemeli; paid service ek olarak service/document info tasiyabilir. Role itself verification claim yaratmaz.

### 18. Ownership transfer and archive

**CONFIRMED — Q120-Q121, Q135-Q137**

Selective transfer acikca `owner-selected / incomplete history` olarak represented edilmelidir. Covered period ve visible gaps gosterilir; gap `maintenance completed` gibi yorumlanmamalidir. Non-transferred private note/photo content acilmaz.

Transfer sonrasi record silent overwrite edilmez. Former owner correction/new-info proposal sunabilir; current owner attribution/time gorur ve review/accept edebilir; prior version/evidence trail korunur.

Archive delete degildir: active garage'dan cikarir, history'yi korur, reversible'dir.

### 19. Actual deletion and data ownership

**CONFIRMED — Q092-Q095, Q129-Q131**

Actual motorcycle deletion oncesi affected history/photos/measurements/reminders kapsamı gosterilmelidir. Confirmation sonrasi user'in kendi copy'sindeki linked data birlikte silinmesi beklenir. Daha once baskasina transferred independent record otomatik etkilenmemelidir.

Bu product expectation legal retention/backup purge/technical implementation karari degildir.

### 20. Offline/freshness semantics

**CONFIRMED — Q090-Q091, Q122, Q147-Q149**

Offline downloaded content accessible olabilir fakat access ile application authorization ayni sey degildir.

Freshness application-critical ozellikle:
- safety notice,
- technical value,
- changeable procedure order
claim'lerinde anlamlidir.

Old conceptual teaching tek basina application stop nedeni degildir; source/last-check date yine gorunmelidir. Stale critical content teaching/reference olarak kalabilir fakat current instruction gibi gorunemez. Critical freshness verify edilemiyorsa motorcycle-facing application online re-check'e kadar kapanir. Learning/preparation/local records offline devam edebilir. Numeric TTL/threshold secilmemistir.

### 21. Localization and active-repair accessibility

**CONFIRMED — Q124-Q125, Q150-Q152**

Turkiye-first expectation: clear Turkish, familiar units, understandable terms; beginner explanation depth ve experienced concise view.

Accessibility: large readable controls/text, high contrast, warnings not color-only, image descriptions, captions, voice/easy-touch/hands-free support.

Convenience safety invariant'i kaldiramaz. Safety warning, motorcycle fit, technical value, stop condition ve post-operation check atlanamaz. Energy isolation, motorcycle stability, critical connection confirmation ve operation completion gibi critical decisions misheard voice command'a birakilamaz; explicit/reviewable confirmation gerekir. Alternate modality same critical control'u baska yoldan yaptirmali, kontrolu kaldirmamalidir.

### 22. Trust-breakers / non-goal direction

**CONFIRMED — Q035, Q065, Q088, Q095, Q096-Q110, Q122, Q126-Q152**

Trust-breaking behavior includes:
- fabricated/unverified technical certainty,
- hidden danger or self-assertion bypass of critical gate,
- false definitive diagnosis,
- dangerous-work success guarantee,
- teaching content masquerading as current motorcycle application instruction,
- critical safety/core completion behind paywall,
- silent history/provenance overwrite/loss,
- cross-account data mixing,
- community content masquerading as official guidance,
- commercial influence on technical recommendation,
- stale critical application left open without required re-check,
- accessibility shortcut removing critical confirmation.

## Working Interpretations — INFERRED, NOT DECIDED

- `Teaching vs application` yatay product trust principle olabilir.
- `Evidence-gated re-entry` readiness/recovery modelinin ortak semantigi olabilir.
- Auditability guide version, history, moderation, collaboration, ownership transfer ve export boyunca ortak principle olabilir.
- `Verified` kelimesinden cok `hangi claim verify edildi` product trust acisindan esastir.
- Offline continuity safety context preservation'dir; stale application authorization ayri gate'tir.
- Owner-first core ile professional/collaboration support birbirinden ayrilabilir.

Bu yorumlar discovery ilerledikce test edilmeye devam edecektir.
