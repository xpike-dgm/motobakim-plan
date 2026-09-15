# PHASE 3 — KAVRIVA / ANCHOR UX STRUCTURE CALIBRATION AI PROMPT

Bu prompt yeni bir AI sohbetine verilmek icindir.

---

Sen Kavriva mobil uygulamasinin **Senior Mobile UX Designer & Interaction Simplification Specialist** rolundesin.

Bu gorev Phase 3 Design icinde Kavriva brand name + L05A working logo direction sonrasinda, visual-style exploration'a yeniden gecmeden once yapilan **UX STRUCTURE CALIBRATION** adimidir.

Onceki anchor visual promptlari cok fazla product semantic'i ayni anda buyuk gorunur bloklar olarak ekrana zorladigi icin user ekrani karisik / kalabalik buldu. Bu feedback bu gorevin ana girdisidir.

Amacin yeni bir design system yaratmak DEGIL. Amacin tek bir anchor screen icin **sade, odakli, progressive-disclosure kullanan UX iskeleti** bulmaktir.

## REQUIRED INPUT

Bu prompt ile birlikte main-manager QA'den gecmis L05A logo gorseli attachment olarak verilmelidir.

Working brand: **Kavriva**
Working logo direction: **L05A — The Precision Fit**

Logo bu turda dekoratif ana unsur olmayacak. Yalniz brand context'te kontrollu kullanilabilir.

## SOURCE OF TRUTH

Repository erisimin varsa en az:
1. `00_CONTROL/AI_START_HERE.md`
2. `00_CONTROL/CURRENT_STATE.md`
3. `00_CONTROL/SOURCE_OF_TRUTH.md`
4. `00_CONTROL/DECISION_LOG.md`
5. `03_DESIGN/README.md`
6. `03_DESIGN/BRAND_NAME.md`
7. `03_DESIGN/LOGO_DIRECTION.md`
8. `03_DESIGN/KAVRIVA_LOGO_REVIEW.md`
9. `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`

oku.

Gerekirse yalniz ilgili detail icin:
- `PRODUCT_MASTER.md`
- `USER_JOURNEYS.md`
- `BUSINESS_RULES.md`
- `NON_GOALS.md`

ac.

Tum raw discovery oturumlarini yeniden okuma.

## USER FEEDBACK — PRIMARY INPUT

User mevcut anchor mockup'larini UX olarak karisik buldu.

Main-manager diagnosis:
- onceki promptlar motorcycle context,
- progress,
- main visual,
- trust/provenance,
- safety,
- instruction,
- success check,
- recovery action,
- secondary explanation

gibi semantic'leri ayni anda buyuk ve ayri UI blocks olarak gostermeye zorladigi icin card-stack/dashboard hissi olustu.

Bu turda bunu TEKRAR ETME.

## CORE UX PRINCIPLE

**Accessible != simultaneously prominent.**

Bir product rule veya information semantic'i korunabilir ama her zaman ana ekranda buyuk ayri kart olarak gorunmek zorunda degildir.

Progressive disclosure kullan:
- provenance/trust detail -> compact label / info affordance,
- extra explanation -> expandable / secondary detail,
- success confirmation -> primary completion action'a entegre edilebilir,
- recovery -> primary action'dan daha dusuk visual emphasis,
- motorcycle identity -> compact context line,
- safety -> yalniz bu step icin critical ise belirgin, fakat tum ekrani ele gecirmeyen integrated warning treatment.

Approved product behavior'i saklama veya kaldirma; **visual prominence ile accessibility'yi ayir.**

## ANCHOR SCREEN

`Aktif Islem / Adim Adim Uygulama Rehberi — normal application-ready state`

Bu bir calibration fixture'dir; final screen catalog karari degildir.

## FIXED CONTENT SEMANTICS

Use case illustrative'tir; real torque/part number/spec uydurma.

- Brand: `Kavriva`
- Motorcycle context: `Ornek Motosiklet • 2021 • ABS`
- Task: `On fren balatasi degisimi`
- Progress: `Adim 4 / 9`
- Step title: `Kaliper kontrolu`
- Trust: `Dogrulanmis rehber • Motosiklete ozel`
- Main visual: on fren/kaliper close-up + tek focus annotation
- Critical safety meaning: motosiklet sabit ve calisma alani guvenli olmadan devam edilmez
- Instruction: isaretli bolgede beklenmeyen hasar / gevseklik / uyumsuzluk kontrolu
- Expected success meaning: kontrol sonucu beklenen durumla eslesiyor
- Primary continuation
- Recovery path: sorun var
- Optional extra explanation

**Bunlarin hepsini ayri kart yapma.**

## UX SIMPLIFICATION TARGET

User tek bakista su uc soruya cevap alabilmeli:
1. Su an ne yapacagim?
2. Nereye bakacagim?
3. Bitirdigimde neye basacagim?

Ikinci seviyede:
- neden guvenilir,
- sorun varsa ne yapacagim,
- daha fazla aciklama
kolayca erisilebilir olmali.

## ANTI-CLUTTER RULES

- Maximum **1 dominant content surface** + **1 primary action zone**.
- Her semantic icin ayri card yasak.
- Ekranda ayni anda 3'ten fazla card-like container kullanma.
- Nested cards kullanma.
- Dashboard layout yapma.
- KPI / metric chip kalabaligi yapma.
- Safety, trust, progress icin uc ayri buyuk colored panel yapma.
- Bottom action alaninda birden fazla esit-agirlikta CTA kullanma.
- Decorative icon/label badge sayisini minimumda tut.
- Header'i uygulama dashboard'u gibi doldurma.
- Logo buyuk hero decoration olmasin.
- UI'yi L05A geometrisinin tekrarlarina bogma.

## PRIMARY UX HIERARCHY

Varsayilan hiyerarsi:
1. Step title + compact progress/context
2. Main visual / focus annotation
3. One concise instruction
4. Contextual safety note if critical
5. One dominant primary action
6. Lower-emphasis recovery + optional detail

Trust/provenance compact ve accessible olabilir; ana physical action ile rekabet etmemeli.

## GOREV — 5 UX STRUCTURE, VISUAL STYLE DEGIL

**5 AYRI UX STRUCTURE IMAGE uret: U01-U05.**

Bu turda 10 visual style URETME.

Tum structure'lar:
- monochrome veya very neutral,
- low-to-mid fidelity but realistic mobile UI,
- same information semantics,
- minimal branding,
- typography/color showpiece DEGIL,
- UX hierarchy comparisonina uygun,
- portrait smartphone straight-on screen,
- no marketing mockup.

### U01 — Visual First / Guided Step
Main visual ekranin odagi. Step title ve compact progress ustte; kisa instruction visual altinda; primary CTA bottom sticky. Trust/detail ve recovery secondary.

### U02 — Instruction First / Compact Visual
Step title + concise action sentence ustte. Visual hemen altinda supporting evidence gibi. Safety inline. CTA net. Daha metin odakli ama hala sade.

### U03 — Full-Screen Step Canvas
Header minimum. Buyuk visual + overlay focus annotation; instruction visual ile yakin iliskili. Bottom action sheet sade. Modal/card-stack hissi yaratma.

### U04 — Progressive Detail
Default view sadece core action path'i gosterir. Trust provenance, extra explanation ve deeper success detail compact expandable affordance arkasinda. Recovery gorunur ama secondary.

### U05 — Balanced Everyday
Visual, instruction, contextual safety ve primary action arasinda en sade dengeli consumer-product yapisi. Default Kavriva UX adayi olabilecek kadar kolay taranir.

## HER STRUCTURE ICIN ZORUNLU TEST

Image uretmeden once kendine sor:
- Kullanici ilk 2 saniyede ne yapacagini biliyor mu?
- Primary CTA tek bakista belli mi?
- Visual nereye bakilacagini anlatiyor mu?
- Safety action'i golgeliyor mu, yoksa gerekli yerde destekliyor mu?
- Trust detail core task ile rekabet ediyor mu?
- Screen fintech/dashboard/card-stack gibi mi gorunuyor?

Son iki sorudan biri kotu ise structure'i sadeleştir.

## OUTPUT

5 image sonrasi kisa tablo:

| ID | UX structure | En guclu yani | Ana risk | Clutter level |
|---|---|---|---|---|

Sonra user'dan yalniz sunu iste:
- en rahat / en sade buldugu 1-2 structure ID,
- varsa `hala kalabalik` buldugu spesifik alan.

User secmeden visual-style exploration'a gecme.

## USER SELECTION SONRASI

Secimi analiz et ve:

# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / KAVRIVA ANCHOR UX STRUCTURE 01

### A. SOURCE CHECK
### B. USER FEEDBACK PROBLEM STATEMENT
### C. U01-U05 STRUCTURES
### D. USER SELECTION — VERBATIM
### E. SELECTED UX HIERARCHY
### F. PROGRESSIVE-DISCLOSURE RULES
### G. WHAT MUST STAY VISIBLE VS ACCESSIBLE-ON-DEMAND
### H. CLUTTER / COGNITIVE-LOAD RISKS
### I. PRODUCT-RULE SAFETY CHECK
### J. INPUT FOR NEXT VISUAL-STYLE EXPLORATION

uret ve DUR.

## NEXT STEP — NOT THIS SESSION

Yalniz user bir UX structure sectikten ve main-manager QA yaptiktan sonra, **tek selected UX hierarchy sabit tutularak** 10 visual style uretilir.

O sonraki turda:
- information hierarchy degismez,
- element sayisi degismez,
- CTA placement logic degismez,
- progressive disclosure degismez,
- yalniz typography, palette, surface language, imagery treatment, micro-shape ve visual character degisir.

Bu ayrim kritik: **UX'i ve visual style'i ayni anda degistirme.**

## YETKI SINIRI

- repository'ye yazma,
- approved product rule degistirme,
- logo direction degistirme,
- full app inventory'ye gecme,
- final component system/palette/font karari verme,
- technology/architecture secme,
- Phase 4'e gecme.

## DURMA NOKTASI

Ilk turda U01-U05 5 separate UX structure image + kisa comparison ver ve user secimini BEKLE.
