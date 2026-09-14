# OPEN QUESTIONS

Bu dosya proje hafizasinda henuz kesinlesmemis urun sorularini tutar. Bir AI buradaki konuyu kendi varsayimiyla kapatamaz.

## Status Values
- `OPEN`
- `BLOCKED`
- `ANSWERED`
- `CANCELLED`

---

## Aktif Sorular

### Q-0046 — Basic history ile expanded storage arasindaki urun siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q114-Q115, Q144-Q146  
**Question:** Ucretsiz core icinde kalmasi gereken `makul/yeterli gecmis` hangi product value'yu mutlaka korumali; premium expanded media/storage hangi niteliksel farkta baslar?  
**Impact:** Core-free boundary ve monetization trust.  
**Resolution so far:** Temel history, islemi tamamlamak icin gereken evidence ve data export paywall olamaz. Cok buyuk medya arsivi premium adayi olabilir. Sayisal kota/fiyat henuz yok.

### Q-0047 — Basic multi-bike ile advanced garage arasindaki fark
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q062, Q114, Q141, Q146  
**Question:** Birden fazla motosikleti temel olarak ayri tutmak core iken `advanced multi-garage` hangi ek product value ile premium adayi olur?  
**Impact:** User scope ve premium boundary.  
**Resolution so far:** Birkaç motosikleti ayri tutmak core beklentidir; advanced comparative analysis ve kapsamli collaboration premium adayi olabilir.

### Q-0048 — Transfer sonrasi duzeltme uyusmazligi ve coklu devir
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q120, Q135-Q137  
**Question:** Eski sahibin duzeltme onerisi yeni sahip tarafindan reddedilirse veya motosiklet birden fazla kez el degistirirse farkli tarihsel iddialar/provenance nasil anlasilir kalmalidir?  
**Impact:** Ownership-history trust.  
**Resolution so far:** Transfer partial-history olarak isaretlenir; eski kayit sessizce overwrite edilmez; correction proposal attribution/time/prior version/evidence iziyle sunulur.

### Q-0049 — Geri cekilen community contribution'in downstream etkisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q081-Q083, Q105-Q108, Q130  
**Question:** Geri cekilen bir contribution daha once bir official guide, claim veya baska kullanici kararini etkilediyse hangi transparency/re-review ve kullanici uyarisi beklenir?  
**Impact:** Content lifecycle ve community trust.  
**Resolution so far:** Public contribution kaldirilir, personal info silinir; de-identified safety review trace korunabilir. Geri cekilen published correction affected guide icin re-review gerektirir.

### Q-0050 — Shared/collaborative kayitta deletion ownership siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q118-Q121, Q129  
**Question:** Owner kendi motosiklet/kaydini silmek isterken baska bir collaborator'in bagimsiz contribution veya aktarilmis kaydi varsa hangi kaydin kime ait oldugu ve neyin silinebilecegi product-level olarak nasil anlasilmalidir?  
**Impact:** Data ownership ve collaboration trust.  
**Resolution so far:** Owner'in kendi kopyasindaki bagli veriler silinebilir; baska kisilere aktarilmis independent records otomatik etkilenmez.

### Q-0051 — Evidence explanation depth by risk
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q109-Q110, Q132-Q134  
**Question:** Hangi dusuk-risk baglamlarda kisa evidence label yeterli, hangi high-trust/high-risk baglamlarda `neyin hangi kanitla dogrulandigi ve neyin dogrulanmadigi` acik cümleyle zorunlu olmalidir?  
**Impact:** Trust clarity ve information overload dengesi.  
**Resolution so far:** Safety warnings, technical values, ownership transfer ve disputed records'ta label tek basina yeterli degildir.

### Q-0052 — Account-light first-use'tan kalici profile geciste local-data trust
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q123, Q153-Q155  
**Question:** Kullanici ilk real record'u saklamak, cross-device devam etmek veya collaboration baslatmak icin profile gecerken mevcut local history'nin korunmasi/aktarilmasi hakkinda hangi guvenceyi bekler?  
**Impact:** First-use continuity ve user trust.  
**Resolution so far:** Profile isteme nedeni ve mevcut local data'ya ne olacagi onceden aciklanmalidir. Teknik sync/auth cozumleri bu asamada secilmez.

### Q-0053 — Mid-repair online re-check sonrasi kritik guide degisikligi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q028, Q059-Q060, Q122, Q147-Q149  
**Question:** Kullanici yarim islemi offline stale guide ile durdurmusken online re-check sonrasi guide materially degismisse mevcut fiziksel motosiklet durumuyla yeni guide arasinda nasil guvenli gecis bekler?  
**Impact:** Interrupted work + freshness safety.  
**Resolution so far:** Kritik degisiklikte eski akis devam etmez; mevcut physical state yeni guide ile yeniden eslestirilir ve ilerleme/notlar korunur. Freshness senaryosundaki user-facing ayrinti aciktir.

### Q-0054 — Active repair interruption ve dikkat kaybi sonrasi geri donus
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q028, Q150-Q152  
**Question:** Telefon kapanir, kullanici uygulamadan ayrilir veya dikkati dagilirsa kritik step state'e geri donmeden once hangi resume/re-confirmation davranisi beklenir?  
**Impact:** Active-repair safety ve recovery.  
**Resolution so far:** Interrupted-work baglami korunur; critical confirmations kolaylik ugruna atlanamaz.

### Q-0055 — Paid service evidence ile owner observation celiskisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q063, Q109-Q110, Q133-Q140  
**Question:** Ucretli servis belgesi belirli bir islemin yapildigini soylerken owner gozlemi/kaniti bununla celisirse iki iddia hangi evidence status ve dispute semantigiyle yan yana tutulmalidir?  
**Impact:** External-service history trust.  
**Resolution so far:** Paid role otomatik verified degildir; yapan kisi, service/document info ve evidence gorunur olmalidir.

---

## Answered Questions — Current Register

Detayli ham kanit `02_DISCOVERY/SESSIONS/` altinda, onceki resolution tarihcesi `00_CONTROL/CHANGELOG.md` icindedir.

- **Q-0001 ANSWERED — Q010-Q011:** Dogrulanmis teknik bilgi motosiklet/varyantla uyumlu kaynak + provenance + insan incelemesine dayanir; kritik source conflict cozulmeden tek deger secilmez.
- **Q-0002 ANSWERED — Q036-Q039, Q066-Q067:** Kullanici teknik kod avina zorlanmaz; observable evidence denenir, yetersizse variant-specific application kapanir.
- **Q-0003 ANSWERED — Q020, Q034, Q045-Q052:** Kapsam kategori yasagindan cok dogrulanmis kosullar ve stop-gates ile sinirlanir.
- **Q-0004 ANSWERED — Q126-Q128:** Blocked readiness'ta once re-evaluation + self-remediation + re-validation; professional help destek secenegidir, kritik unverified condition ise mandatory application closure'dur. Kosul yeniden saglanip dogrulaninca self-service'e donulebilir.
- **Q-0005 ANSWERED — Q007, Q014:** Beginner detailed, experienced fast view; safety ayni kalir.
- **Q-0006 ANSWERED — Q017-Q021, Q034:** Guvenli application icin match, kaynak, arac/ekipman, risk anlayisi ve sonucu dogrulayabilme gerekir.
- **Q-0007 ANSWERED — Q014-Q015, Q025:** Fotograf/cizim/video/metin ve basari kontrolu gorsel rehber modelini tanimlar.
- **Q-0008 ANSWERED — Q031, Q033:** Manufacturer km/sure + verified completion; uydurma interval yok.
- **Q-0009 ANSWERED — Q029-Q030:** Zengin history ve provenance korunur.
- **Q-0010 ANSWERED — Q032-Q033, Q064, Q070-Q072:** Routine cadence/grouping/user control; critical safety app icinde kalir.
- **Q-0011 ANSWERED — Q012, Q022-Q024:** Evidence-guided diagnosis repair guide'dan ayridir.
- **Q-0012 ANSWERED — Q025-Q028:** Unexpected state recovery/stop/evidence/handoff gerektirir.
- **Q-0013 ANSWERED — Q040-Q044:** Human review ve content lifecycle/review/recall modeli.
- **Q-0014 ANSWERED — Q038-Q039:** Modified system fabrika rehberine otomatik eslesmez.
- **Q-0015 ANSWERED — Q054:** Verified visual fallback; wrong-bike visual yok.
- **Q-0016 ANSWERED — Q053-Q055:** Safe equivalent ancak islev/safety gereklilikleri dogrulanirsa.
- **Q-0017 ANSWERED — Q056-Q058:** Diagnosis evidence threshold sabit sayi degil; unresolved result mumkun.
- **Q-0018 ANSWERED — Q050-Q052:** Task-specific readiness oz-beyandan fazlasini gerektirir.
- **Q-0019 ANSWERED — Q059-Q060:** Guide version change yarim/gecmis isi sessizce yeniden yazmaz.
- **Q-0020 ANSWERED — Q065:** Core safety/guide/history/reminders free baseline.
- **Q-0021 ANSWERED — Q080-Q084:** Community opt-in, provenance/review statuslu ve official guide'dan ayridir.
- **Q-0022 ANSWERED — Q073-Q074:** History edit trail + evidence levels korunur.
- **Q-0023 ANSWERED — Q084-Q088:** Social/commercial support core'u golgelemez; technical neutrality korunur.
- **Q-0024 ANSWERED — Q061, Q075-Q077:** Maintenance exceptions verified olmalidir; uncertainty gizlenmez.
- **Q-0025 ANSWERED — Q078-Q079:** Time/cost estimate uncertainty/assumptions ile sunulur.
- **Q-0026 ANSWERED — Q144-Q146:** Recurring service value ile one-time optional value ayrisabilir; core guide/safety/reasonable history/export/basic multi-bike paywall olamaz. Final price/package secilmedi.
- **Q-0027 ANSWERED — Q141-Q143, Q153-Q155:** Priority beginner+experienced self-service owner; basic record tracking first-version value; adjacent segment values ve first-use farklari tanimli.
- **Q-0028 ANSWERED — Q092-Q094:** User data control/export/delete baseline.
- **Q-0029 ANSWERED — Q090-Q091:** Offline/roadside continuity baseline.
- **Q-0030 ANSWERED — Q096-Q098:** Readiness challenge = evidence-based re-validation, serbest override degil.
- **Q-0031 ANSWERED — Q102-Q104:** Common aftermarket adapted guide; custom durumda teaching-only + evidence gap fallback.
- **Q-0032 ANSWERED — Q105-Q108:** Moderation reason/appeal/re-submit/pre-review/restriction ve unverified personal-experience statusu.
- **Q-0033 ANSWERED — Q109-Q110:** Evidence labels temel semantigi ve `verified != guarantee`.
- **Q-0034 ANSWERED — Q111-Q113:** Critical reminder escalation/catch-up summary.
- **Q-0035 ANSWERED — Q129-Q131:** Delete kendi bagli kopyasini kapsar; independent transferred records etkilenmez; community withdrawal public/personal data'yi kaldirir, de-identified safety trace kalabilir; export provenance/evidence/edit history tasir.
- **Q-0036 ANSWERED — Q138-Q140:** Initial direct target owner; professional/service/hobby helper invited collaboration context; separate work-management product later olabilir.
- **Q-0037 ANSWERED — Q118-Q119:** Shared motorcycle permission/attribution/edit trail/private-note isolation.
- **Q-0038 ANSWERED — Q124-Q125:** Turkiye-first language/units + accessibility baseline.
- **Q-0039 ANSWERED — Q120-Q121:** Selective transfer + archive lifecycle baseline.
- **Q-0040 ANSWERED — Q122:** Offline stale critical guide application re-check'e kadar kapanabilir.
- **Q-0041 ANSWERED — Q123:** First value account/permission zorunlulugundan once gorulebilir.
- **Q-0042 ANSWERED — Q132-Q134:** Common evidence vocabulary + context-specific verified claim; high-trust durumda explicit claim/evidence/unverified explanation gerekir.
- **Q-0043 ANSWERED — Q135-Q137:** Selective transfer partial/incomplete olarak isaretlenir; covered period/gaps gorunur; private content korunur; post-transfer correction proposal attributed/reviewable olur.
- **Q-0044 ANSWERED — Q147-Q149:** Freshness application-critical claim'lerde gate'tir; stale teaching/reference kalabilir; long-offline durumda critical application re-check'e kadar kapali kalir. Numeric threshold yok.
- **Q-0045 ANSWERED — Q150-Q152:** Active-repair accessibility alternate modalities kullanabilir fakat match/value/stop/post-check/critical confirmation safety invariants'i kaldiramaz.

---

## Kullanim Kurali
Yeni belirsizlik ayni formatta eklenir. Soru yalniz kullanici kaniti veya yetkili karar sureciyle `ANSWERED` yapilir. Genis bir soru kapaninca daha dar edge-case sorusu acilabilir; eski cevap sessizce silinmez.
