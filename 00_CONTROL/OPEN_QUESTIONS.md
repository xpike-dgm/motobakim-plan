# OPEN QUESTIONS

Bu dosya proje hafizasinda henuz kesinlesmemis urun sorularini tutar. Bir AI buradaki konuyu kendi varsayimiyla kapatamaz.

## Status Values
- `OPEN`
- `BLOCKED`
- `ANSWERED`
- `CANCELLED`

---

## Aktif Sorular

### Q-0050 — Shared/collaborative evidence withdrawal ve independent copies
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q118-Q121, Q129, Q169-Q171  
**Question:** Bir collaborator kendi evidence'ini geri cektiginde bu evidence daha once baska owner'a independent/transferred record olarak aktarilmissa kaynak withdrawal ile aktarilmis kopyanin gorunurlugu, provenance'i ve trust state'i product-level olarak nasil iliskilenmelidir?  
**Impact:** Data ownership, transfer trust ve collaborator rights.  
**Resolution so far:** Owner deletion baska kisinin independent data'sini sessizce silmez. Contributor own evidence'i geri cekebilir; linked history'de withdrawal trace kalir ve claim trust yeniden degerlendirilir. Access revoke prior attributed operation record'u otomatik silmez. Cross-transfer independent-copy behavior hala aciktir.

### Q-0056 — Disputed claim'e yeni independent evidence geldiginde resolution
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q162-Q165, Q184-Q185  
**Question:** Disputed historical veya service claim'e sonradan yeni independent evidence geldiginde claim hangi product-level durumlara gecebilir; disagreement ne zaman resolved sayilabilir, ne zaman iki claim tarihsel olarak birlikte kalmalidir?  
**Impact:** History trust, maintenance calculation ve future guide decisions.  
**Resolution:**

### Q-0057 — Historical claim states icin minimum semantik set
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q162-Q165, Q170, Q184-Q185  
**Question:** Kullanici acisindan history claim'lerinde `accepted`, `disputed`, `evidence withdrawn`, `superseded/resolved`, `unknown` gibi hangi minimum durum ayrimlari gercekten gerekli ve anlasilir?  
**Impact:** Trust language ve design-oncesi state inventory.  
**Resolution:**

### Q-0058 — Material guide change sonrasi eski fiziksel degisiklik recovery
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q178-Q180  
**Question:** Eski guide ile motosiklette yapilmis bir sokme/ayar/baglanti yeni guide'da artik onerilmiyorsa kullanici hangi recovery, geri-alma veya yeniden-dogrulama davranisini bekler?  
**Impact:** Mid-repair safety ve physical-state transition.  
**Resolution:**

### Q-0059 — Long interruption: saved context vs current physical reality
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q181-Q183  
**Question:** Islem saatler/gunler sonra devam ettirildiginde saved state ile gercek fiziksel durumun hala ayni oldugu ne kadar varsayilabilir; hangi tur kosullar yeniden kontrol edilmeden application'a donulmamali?  
**Impact:** Resume safety ve stale work-context trust.  
**Resolution:**

### Q-0060 — Profile migration cancel/rollback expectation
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q175-Q177  
**Question:** Local-to-profile transition baslatilip yarida iptal edilir, hata verir veya user vazgecerse local records ve yeni profile-associated records icin hangi product-level continuity/rollback expectation'i vardir?  
**Impact:** First-use trust ve data continuity.  
**Resolution:**

### Q-0061 — Withdrawn evidence icin affected-user boundary
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q166-Q168  
**Question:** Withdrawn evidence hangi durumda bir kullaniciyi `affected user` yapar: guide'i sadece gormek, ilgili step'i acmak, uygulamak veya completion kaydi olusturmak arasinda correction reach-back beklentisi nasil degisir?  
**Impact:** Safety communication ve over/under-notification dengesi.  
**Resolution:**

### Q-0062 — Evidence detail: beginner vs experienced adaptation
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q007, Q172-Q174  
**Question:** Evidence/provenance aciklama derinligi beginner ve experienced user icin nasil farklasabilir; high-risk explicit trust bilgisi deneyim/hiz ugruna hangi noktada kisaltilamaz?  
**Impact:** Trust clarity, usability ve design requirements.  
**Resolution:**

### Q-0063 — Core invited collaboration vs premium extensive collaboration
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q118-Q119, Q146, Q160-Q161  
**Question:** Basic owner-invited collaboration core'da hangi minimum degeri korumali; premium `extensive collaboration` hangi ek koordinasyon/scale ihtiyacinda baslamali?  
**Impact:** Core/premium boundary ve shared-bike experience.  
**Resolution:**

### Q-0064 — Advanced garage/core collaboration overlap
**Status:** OPEN  
**Opened:** 2026-09-15  
**Context:** Q159-Q161, Q169-Q171  
**Question:** Advanced garage icindeki bulk planning/archive search/cross-bike permissions gibi degerlerden hangileri basic shared-bike trust icin zorunlu degildir; premium siniri basic attribution/revoke/history integrity'yi asla zayiflatmadan nasil product-level ayrilmalidir?  
**Impact:** Monetization trust ve multi-bike/shared-bike scope.  
**Resolution:**

---

## Answered Questions — Current Register

Detayli ham kanit `02_DISCOVERY/SESSIONS/` altinda, onceki resolution tarihcesi `00_CONTROL/CHANGELOG.md` icindedir.

- **Q-0001 ANSWERED — Q010-Q011:** Dogrulanmis teknik bilgi motosiklet/varyantla uyumlu kaynak + provenance + insan incelemesine dayanir; kritik source conflict cozulmeden tek deger secilmez.
- **Q-0002 ANSWERED — Q036-Q039, Q066-Q067:** Kullanici teknik kod avina zorlanmaz; observable evidence denenir, yetersizse variant-specific application kapanir.
- **Q-0003 ANSWERED — Q020, Q034, Q045-Q052:** Kapsam kategori yasagindan cok dogrulanmis kosullar ve stop-gates ile sinirlanir.
- **Q-0004 ANSWERED — Q126-Q128:** Blocked readiness'ta re-evaluation + self-remediation + re-validation; professional help destek secenegidir, kritik unverified condition mandatory application closure'dur.
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
- **Q-0026 ANSWERED — Q144-Q146:** Core guide/safety/reasonable history/export/basic multi-bike paywall olamaz; advanced service values premium adayi olabilir. Final price/package yok.
- **Q-0027 ANSWERED — Q141-Q143, Q153-Q155:** Priority beginner+experienced self-service owner; basic record tracking first-version value; adjacent segment values tanimli.
- **Q-0028 ANSWERED — Q092-Q094:** User data control/export/delete baseline.
- **Q-0029 ANSWERED — Q090-Q091:** Offline/roadside continuity baseline.
- **Q-0030 ANSWERED — Q096-Q098:** Readiness challenge = evidence-based re-validation, serbest override degil.
- **Q-0031 ANSWERED — Q102-Q104:** Common aftermarket adapted guide; custom durumda teaching-only + evidence gap fallback.
- **Q-0032 ANSWERED — Q105-Q108:** Moderation reason/appeal/re-submit/pre-review/restriction ve unverified personal-experience statusu.
- **Q-0033 ANSWERED — Q109-Q110:** Evidence labels temel semantigi ve `verified != guarantee`.
- **Q-0034 ANSWERED — Q111-Q113:** Critical reminder escalation/catch-up summary.
- **Q-0035 ANSWERED — Q129-Q131:** Delete/withdrawal/export provenance edge cases baseline.
- **Q-0036 ANSWERED — Q138-Q140:** Initial direct target owner; professional/service/hobby helper invited collaboration context.
- **Q-0037 ANSWERED — Q118-Q119:** Shared motorcycle permission/attribution/edit trail/private-note isolation.
- **Q-0038 ANSWERED — Q124-Q125:** Turkiye-first language/units + accessibility baseline.
- **Q-0039 ANSWERED — Q120-Q121:** Selective transfer + archive lifecycle baseline.
- **Q-0040 ANSWERED — Q122:** Offline stale critical guide application re-check'e kadar kapanabilir.
- **Q-0041 ANSWERED — Q123:** First value account/permission zorunlulugundan once gorulebilir.
- **Q-0042 ANSWERED — Q132-Q134:** Common evidence vocabulary + context-specific verified claim; high-trust explicit explanation.
- **Q-0043 ANSWERED — Q135-Q137:** Selective transfer partial/incomplete, covered period/gaps visible; correction proposal attributed/reviewable.
- **Q-0044 ANSWERED — Q147-Q149:** Freshness application-critical claim'lerde gate; stale teaching/reference kalabilir; numeric threshold yok.
- **Q-0045 ANSWERED — Q150-Q152:** Active-repair accessibility safety invariants'i kaldiramaz.
- **Q-0046 ANSWERED — Q156-Q158:** Core history motorcycle/work/date/km/actor/outcome/safety/evidence/correction continuity'yi korur; expanded storage high-volume media'da baslar; premium basic history/safety evidence'i silemez/gizleyemez.
- **Q-0047 ANSWERED — Q159-Q161:** Basic multi-bike motorcycle isolation core'dur; advanced garage cross-bike analysis/bulk planning/richer collaboration/archive-search value'da baslar.
- **Q-0048 ANSWERED — Q162-Q165:** Rejected correction/disputed claim silent overwrite yapmaz; repeated transfers owner/period/coverage/gaps ile ayrilir ve partial history complete diye sunulmaz.
- **Q-0049 ANSWERED — Q166-Q168:** Withdrawn community evidence dependent guide/claim'i re-review eder; remaining independent evidence yeterliyse claim kalabilir, yetersizse verification/application korunmaz; safety/technical impact correction reach-back gerektirebilir.
- **Q-0051 ANSWERED — Q172-Q174:** Low-risk short label, high-risk explicit claim/evidence/reviewer/uncertainty; first-level ve deeper detail ayrimi tanimli.
- **Q-0052 ANSWERED — Q175-Q177:** Local-to-profile transition scope preview/no-silent-loss/conflict review gerektirir; profile olmadan local core value devam edebilir.
- **Q-0053 ANSWERED — Q178-Q180:** Material guide change change/safety/stop impact'i gosterir; current physical state new guide'a remap edilmeden continuation olmaz.
- **Q-0054 ANSWERED — Q181-Q183:** Active repair resume preserved context + current safety/physical-state revalidation gerektirir; uncertain state'te next step automatic acilmaz.
- **Q-0055 ANSWERED — Q184-Q185:** Service document-owner evidence conflict separate disputed claims olarak kalir; unresolved completion maintenance/future decisions'a verified fact olarak aktarilmaz.

---

## Kullanim Kurali
Yeni belirsizlik ayni formatta eklenir. Soru yalniz kullanici kaniti veya yetkili karar sureciyle `ANSWERED` yapilir. Genis bir soru kapaninca daha dar edge-case sorusu acilabilir; eski cevap sessizce silinmez.
