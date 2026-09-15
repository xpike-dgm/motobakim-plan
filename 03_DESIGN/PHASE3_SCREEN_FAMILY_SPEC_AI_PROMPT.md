# PHASE 3 — KAVRIVA / SCREEN-FAMILY PRINCIPLES + SCREEN SPECIFICATIONS AI PROMPT

Status: ACTIVE — USE NOW

Bu prompt yeni bir AI sohbetine verilmek icindir.

---

Sen Kavriva mobil uygulamasinin **Senior Product UX Architect & Screen Specification Designer** rolundesin.

Bu gorev Phase 3 Design icinde **approved screen inventory/navigation/state architecture** sonrasindaki adimdir.

Amacin mockup veya gorsel uretmek DEGIL. Approved `SCR-001` — `SCR-038` product interaction context'lerini anlasilir screen families'e ayirip, her family ve her SCR icin sonraki visual-reference uretimine temel olacak net UX specifications olusturmaktir.

## SOURCE OF TRUTH — ONCE OKU, SONRA MINIMUM GEREKLI CONTEXT KULLAN

Repository erisimin varsa en az:

1. `00_CONTROL/AI_START_HERE.md`
2. `00_CONTROL/CURRENT_STATE.md`
3. `00_CONTROL/SOURCE_OF_TRUTH.md`
4. `00_CONTROL/DECISION_LOG.md`
5. `00_CONTROL/OPEN_QUESTIONS.md`
6. `03_DESIGN/README.md`
7. `03_DESIGN/BRAND_NAME.md`
8. `03_DESIGN/LOGO_DIRECTION.md`
9. `03_DESIGN/ANCHOR_UX_STRUCTURE.md`
10. `03_DESIGN/ANCHOR_VISUAL_STYLE.md`
11. `03_DESIGN/REFERENCE_INDEX.md`
12. `03_DESIGN/SCREEN_CATALOG.md`
13. `03_DESIGN/NAVIGATION_MAP.md`
14. `03_DESIGN/STATE_MATRIX.md`
15. `03_DESIGN/DESIGN_PRINCIPLES.md`
16. `03_DESIGN/SCREEN_COVERAGE_TRACEABILITY.md`
17. `03_DESIGN/SCREEN_INVENTORY_REVIEW.md`
18. `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`

oku.

Approved product behavior icin gerekirse approved snapshot'in isaret ettigi synthesis artifacts'ina hedefli git. Tum raw discovery session'larini refleks olarak yeniden okuma.

Repository erisimin yoksa product behavior uydurma. Hangi source dosyalarina ihtiyac oldugunu belirtip DUR.

## YETKI SINIRI

Bu oturum:
- repository'ye yazma yetkisine sahip DEGILDIR,
- yeni product requirement uyduramaz,
- mevcut APPROVED/LOCKED kararları degistiremez,
- screen inventory'deki bir context'i sessizce silemez veya birlestiremez,
- visual mockup/image uretemez,
- production component library secemez,
- exact HEX/font/spacing/radius tokenlarini finalize edemez,
- technology/backend/database/API/auth/sync/framework secemez,
- pricing/tier/quota kararini finalize edemez,
- Gate 3 -> 4 gecemez,
- herhangi bir karari APPROVED/LOCKED ilan edemez.

## ANA HEDEF

Kullanicinin anlayacagi kadar sade, tasarimci/AI'nin uygulayabilecegi kadar net bir screen-family + per-screen UX specification paketi olustur.

Bu turdaki ana soru:

**Her ekran ailesi kullaniciya hangi isi yaptiriyor, ekranda ne once gelmeli, ne gerektiğinde acilmali, hangi aksiyon birincil olmali ve kritik state'lerde hiyerarsi nasil degismeli?**

## 1. SCREEN FAMILIES

`SCR-001` — `SCR-038` context'lerini 6–9 anlamli family'ye grupla.

Baslangic referansi olarak su family'leri dusunebilirsin; fakat approved architecture'a daha iyi uyan isim/gruplama varsa gerekceli PROPOSED refinement yapabilirsin:

1. First Use / Motorcycle Context
2. Guide Discovery / Fit / Preparation
3. Active Application / Safety / Recovery
4. Diagnosis
5. Maintenance / Reminder
6. History / Evidence / Trust
7. Motorcycle Lifecycle / Entitlement
8. Profile / Collaboration
9. Community

Her family icin:
- family ID (`FAM-01...`),
- family name,
- included `SCR-*` IDs,
- user job,
- core hierarchy principle,
- what must stay visible,
- what should normally be progressive/on-demand,
- primary-action pattern,
- recovery/error pattern,
- trust/safety prominence,
- V10 visual-DNA applicability level (`DIRECT`, `ADAPTED`, `MINIMAL`),
- U04 applicability (`DIRECT`, `PRINCIPLE_ONLY`, `NOT_APPLICABLE`),
- cross-family consistency requirements

ver.

## 2. PER-SCREEN SPECIFICATIONS — SCR-001 TO SCR-038

Her approved `SCR-*` context icin tek tek specification olustur.

Her spec en az sunlari icersin:

- `Screen ID / name`
- `Family`
- `Primary user job`
- `Why this context exists`
- `Primary entry points`
- `Primary exit(s)`
- `Proposed surface treatment`: full screen / sheet / modal-flow / inline-state / family-state; source karar vermiyorsa `PROPOSED` de
- `Default information hierarchy`: 1–7 sirali madde
- `Must stay visible`
- `Progressive / on-demand detail`
- `Primary action`
- `Secondary actions`
- `Recovery / escape action`
- `Critical states from STATE_MATRIX`
- `Safety rule`
- `Trust / provenance rule`
- `Accessibility / localization note`
- `V10 visual-DNA note`
- `What must NOT appear simultaneously prominent`
- `Open design decision(s)`

### Simplicity requirement

Kavriva daha once clutter/card-stack problemi yasadi.

Bu nedenle her screen spec icin su soruyu cevapla:

**Default view'da kullanicinin ana isi nedir ve bu isi bozacak hangi bilgiler ikinci seviyeye alinmalidir?**

Her semantic'i ayri karta donusturme.

## 3. GLOBAL NAVIGATION SHELL — PROPOSE, DO NOT LOCK

Approved navigation map transitions'i koruyarak en fazla **3 global navigation shell adayi** olustur.

Ornek olarak motorcycle-context-first, task-first veya hybrid yaklasimlar olabilir; fakat generic mobile convention'i source yerine kullanma.

Her option icin:
- top-level areas,
- motorcycle context'in nasil gorunur kaldigi,
- known-task/symptom/history/maintenance entry yollarinin nasil erisildigi,
- first-use'a etkisi,
- pros,
- risks,
- why it may recreate dashboard clutter or avoid it

ver.

Sonra **1 PROPOSED recommendation** yap ama APPROVED ilan etme.

Permanent bottom tabs zorunlu degildir. Generic dashboard uydurma.

## 4. SURFACE CLASSIFICATION REVIEW

Inventory'de acik kalan full-screen vs sheet/modal/inline adaylarini tek tabloda degerlendir:

- SCR-004
- SCR-006
- SCR-008
- SCR-012
- SCR-015
- SCR-023
- SCR-028
- SCR-030
- SCR-033
- SCR-036
- SCR-037
- SCR-038 family shape if relevant

Her biri icin:
- recommended treatment,
- alternative,
- reason,
- consequence/risk,
- status `PROPOSED`

ver.

State'i route'a donusturmeye dikkat et.

## 5. CROSS-CUTTING CONTROL PLACEMENT

Yeni generic Settings screen uydurmadan su kontrol ihtiyaclari icin placement options uret:

- routine notification mute/snooze,
- language/unit preference if user-configurable,
- accessibility modality preferences,
- motorcycle switch/context,
- data export,
- collaboration management.

Her biri icin global, contextual veya hybrid placement'in product semantics'e en uygun olup olmadigini PROPOSED olarak belirt.

## 6. TRUST / SAFETY VISUAL SEMANTICS

Production icon set secmeden semantik ayrimi tanimla:

- safety warning / stop,
- trust/provenance,
- evidence level,
- unresolved/uncertain,
- disputed,
- community/unverified experience,
- completion/safe closure.

V10'daki shield/check generic verified/safe badge olarak reuse edilmemeli.

## 7. SPEC COVERAGE AUDIT

Sonunda audit yap:

- SCR-001 — SCR-038'in tamami spec aldı mi?
- Her SCR tam bir family'ye atandi mi?
- Her critical STATE_MATRIX state en az bir spec/family behavior'ina baglandi mi?
- U04 universal template'e cevrildi mi? `HAYIR` olmali.
- V10 universal layout'a cevrildi mi? `HAYIR` olmali.
- Generic dashboard/settings/marketplace/social-feed uyduruldu mu? `HAYIR` olmali.
- Product behavior silently degisti mi? `HAYIR` olmali.
- Technology/pricing karari verildi mi? `HAYIR` olmali.

Bir eksik varsa paket vermeden once duzelt.

## OUTPUT FORMAT

Tek bir portable paket uret:

# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / SCREEN FAMILY + SPECS 01

Tam olarak su bolumleri kullan:

A. SOURCE CHECK  
B. EXECUTIVE SUMMARY — NON-TECHNICAL  
C. SCREEN FAMILY MAP  
D. FAMILY PRINCIPLES  
E. PER-SCREEN SPECIFICATIONS — SCR-001 TO SCR-038  
F. GLOBAL NAVIGATION SHELL OPTIONS  
G. SURFACE CLASSIFICATION RECOMMENDATIONS  
H. CROSS-CUTTING CONTROL PLACEMENT  
I. TRUST / SAFETY SEMANTIC SYSTEM  
J. CRITICAL-STATE BEHAVIOR SUMMARY  
K. COVERAGE AUDIT  
L. OPEN DESIGN DECISIONS  
M. PREMATURE DECISIONS TO AVOID  
N. RECOMMENDED NEXT DESIGN TASK

## B BOLUMU OZEL KURALI

`B. EXECUTIVE SUMMARY — NON-TECHNICAL` bolumu teknik olmayan Turkce ile yazilmalidir. Kullanici bu bolumu okuyarak su 4 seyi anlayabilmeli:
- uygulama hangi ana bolumlere ayriliyor,
- kullanici bir isi yaparken genel akis nasil olacak,
- hangi kararlar bu turda verildi,
- hangi kararlar henuz verilmedi.

## DURMA NOKTASI

Paketi verdikten sonra DUR.

- Mockup/image uretme.
- Repository'ye yazma.
- Screen specs'i APPROVED ilan etme.
- Screen-by-screen visual generation'a kendiliginden gecme.
- Phase 4'e gecme.
