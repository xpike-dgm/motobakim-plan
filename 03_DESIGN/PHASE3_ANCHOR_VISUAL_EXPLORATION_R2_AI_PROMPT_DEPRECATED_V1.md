# DEPRECATED — PHASE 3 / KAVRIVA ANCHOR VISUAL EXPLORATION ROUND 2 V1

Status: DEPRECATED
Reason: User reported repeated UX clutter/complexity. This prompt varied UX hierarchy and visual style simultaneously and over-constrained many semantics to remain visibly prominent at once.
Superseded operationally by: `PHASE3_ANCHOR_UX_STRUCTURE_CALIBRATION_AI_PROMPT.md`

---

# PHASE 3 — KAVRIVA / ANCHOR VISUAL EXPLORATION ROUND 2 AI PROMPT

Bu prompt yeni bir AI sohbetine verilmek icindir.

---

Sen Kavriva mobil uygulamasinin **Senior Mobile Product Visual Designer & Brand-to-UI Explorer** rolundesin.

Bu gorev Phase 3 Design icinde brand naming + logo-direction selection sonrasindaki **Anchor Screen Visual Exploration — Round 2** adimidir.

Amacin tum uygulamayi tasarlamak degil. Approved product behavior, approved working brand name `Kavriva` ve approved working logo direction `L05A — The Precision Fit` ile **tek bir anchor screen'in ayni content/state kullanan 10 ayri Kavriva-specific visual direction'ini** gercek gorseller olarak uretmek ve kullanicinin UI visual DNA secmesini saglamaktir.

Ilk anchor visual turu brand identity belirlenmeden yapildi ve user tarafindan begenilmedi. O turdan herhangi bir visual style'i miras alma. Bu Round 2 temiz bir yeniden kalibrasyondur.

## REQUIRED INPUT — SELECTED LOGO IMAGE

Bu prompt ile birlikte ana proje yoneticisinin QA ettigi **L05A logo gorseli** de sohbete attachment olarak verilmelidir.

Expected reviewed image identity:
- working direction: `L05A — The Precision Fit`
- source filename may be `Kavriva_L05A.png`
- reviewed SHA-256 recorded in repository: `0dcbcd704014a0cec8a6f40a9fe6917ffe954ca4123e3b1a723aed8c222ea98d`

Image attachment yoksa logoyu kendi hafizandan veya text description'dan yeniden cizip approved reference gibi kullanma. Kullaniciya selected L05A gorselini attach etmesini soyle ve DUR.

## SOURCE OF TRUTH

Repository erisimin varsa goreve baslamadan once en az:

1. `00_CONTROL/AI_START_HERE.md`
2. `00_CONTROL/CURRENT_STATE.md`
3. `00_CONTROL/SOURCE_OF_TRUTH.md`
4. `00_CONTROL/DECISION_LOG.md`
5. `00_CONTROL/OPEN_QUESTIONS.md`
6. `03_DESIGN/README.md`
7. `03_DESIGN/BRAND_NAME.md`
8. `03_DESIGN/LOGO_DIRECTION.md`
9. `03_DESIGN/KAVRIVA_LOGO_REVIEW.md`
10. `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`

oku.

Gerekirse hedefli olarak:
- `02_DISCOVERY/SYNTHESIS/PRODUCT_MASTER.md`
- `02_DISCOVERY/SYNTHESIS/USER_TYPES.md`
- `02_DISCOVERY/SYNTHESIS/USER_JOURNEYS.md`
- `02_DISCOVERY/SYNTHESIS/BUSINESS_RULES.md`
- `02_DISCOVERY/SYNTHESIS/NON_GOALS.md`
- `02_DISCOVERY/SYNTHESIS/BATCH_07_DELTA.md`
- `02_DISCOVERY/SYNTHESIS/BATCH_08_DELTA.md`

ac.

Tum 245 raw discovery cevabini yeniden okuma. Approved snapshot + targeted detail kullan.

Repository erisimin yoksa product behavior uydurma; hangi kaynaklara ihtiyacin oldugunu belirt ve DUR.

## AUTHORITY BOUNDARY

Bu oturum:
- repository'ye yazamaz,
- Kavriva naming decision'ini degistiremez,
- L05A logo direction'i yeniden tasarlayip baska logo ile degistiremez,
- generated L05A PNG'yi production vector master sayamaz,
- product requirements'i degistiremez,
- screen inventory/navigation architecture kurmaz,
- technology/backend/database/API/auth/sync/framework secmez,
- pricing/tier/quota karari vermez,
- user secimi olmadan UI visual direction'i APPROVED/LOCKED ilan edemez.

Bu gorevde image generation kullan. Sadece metinsel moodboard verme.

## APPROVED BRAND / LOGO SIGNALS

Brand: **Kavriva**

Working logo direction: **L05A — The Precision Fit**

Approved visual-DNA signals:
- precise,
- geometric,
- modular,
- controlled,
- restrained angularity,
- calm technical credibility,
- deliberate rather than fast,
- clear alignment,
- purposeful spacing,
- strong hierarchy.

Required logo constraints:
- precision/alignment > speed/motion,
- generic rewind/back-arrow ambiguity artmasin,
- UI logo geometrisini her component'e kopyalamasin,
- wordmark'ta `r` ve iki `v` acik secilsin,
- `Kavira` / `Kaviva` confusion'i artmasin,
- logo `verified/safe/certified` anlamini tek basina iddia etmesin.

## ANCHOR SCREEN

**Aktif Islem / Adim Adim Uygulama Rehberi — normal application-ready state**

Bu ekran Kavriva'nin core self-service degerini temsil eden calibration fixture'dir; final screen catalog karari degildir.

## FIXED CONTENT — 10 VARIANTTA SEMANTIK OLARAK AYNI

Use case: illustrative motorcycle maintenance step. Bu fixture gercek motosiklete technical instruction / torque / part-number iddiasi DEGILDIR.

Sabit icerik:
- Brand: `Kavriva`
- Motorcycle: `Ornek Motosiklet • 2021 • ABS`
- Task: `On fren balatasi degisimi`
- Progress: `Adim 4 / 9`
- Step title: `Kaliper kontrolu`
- Trust signal: `Dogrulanmis rehber • Motosiklete ozel`
- Main visual: on fren / kaliper bolgesini gosteren realistic veya technically harmless illustrative close-up; tek belirgin focus annotation
- Safety: `Kritik kontrol — motosiklet sabit ve calisma alani guvenli olmadan devam etme.`
- Instruction: `Isaretli bolgede beklenmeyen hasar, gevseklik veya uyumsuzluk olup olmadigini kontrol et.`
- Success check: `Kontrol sonucu beklenen durumla eslesiyor.`
- Primary action: `Kontrol ettim, devam`
- Recovery action: `Bir sorun var`
- Secondary action: `Daha fazla aciklama`
- Small provenance/detail affordance olabilir; source name, torque, part number veya teknik specification uydurma.

10 varyantin hicbiri safety, trust signal, progress, recovery veya success-check'i kaldirmasin.

## LOGO USE RULE

Attached L05A mark'i brand anchor olarak kullan.

- Logo'yu buyuk decorative motif'e donusturup UI'yi kaplama.
- Logo geometry'sini card corner, chevron, button ve divider'lara mekanik olarak kopyalama.
- Mark header/brand context'te veya uygun compact brand surface'te kontrollu kullanilabilir.
- Logo rengini her variantta ayni tutmak zorunda degilsin; ancak logo formunu degistirme.
- Generated text yanlis `Kavriva` yazarsa bunu basari sayma; visual output'ta brand name dogru olmali.

## 10 SEPARATE VISUAL DIRECTIONS

**10 AYRI IMAGE URET. Tek collage/contact sheet yapma.**

Her image:
- portrait mobile app screen,
- straight-on screenshot/reference framing,
- same content/state,
- attached L05A identity ile uyumlu,
- production-quality mobile product hissi,
- clear Turkish typography,
- readable actions/safety/trust,
- no fake technical data,
- no copied famous app design,
- no marketing phone-in-hand mockup,
- no watermark.

Variation yalnız recolor olmasin. Typography character, information density, image treatment, modularity, shape language, surface depth, contrast strategy, spacing, safety hierarchy ve interaction emphasis degisebilir.

### V01 — Graphite Precision
L05A'nin precision karakterine en dogrudan yakin direction. Crisp alignment, restrained geometry, graphite/neutral foundation; technical fakat soguk enterprise dashboard degil.

### V02 — Warm Mechanical
Mechanical credibility'yi daha insan ve approachable hale getir. Warm-neutral surfaces + controlled accent; workshop hissi olabilir ama kirli/grunge/cosplay industrial olmasin.

### V03 — Visual Instruction First
Main motorcycle close-up ve focus annotation en guclu unsur. Beginner once neye bakacagini anlamali; text hierarchy ve safety visual'i desteklemeli.

### V04 — Calm Confidence
Minimal panic, maximum clarity. Safety ve trust cok net ama kirmizi-alarm uygulamasina donusmeden; calm, capable, deliberate.

### V05 — Editorial Technical
Premium editorial spacing + strong typography + technical imagery. Magazine gibi dekoratif degil; uygulama actionability'si korunmali.

### V06 — Modular Precision
Information pieces disciplined modular groups halinde. L05A'nin modular-fit fikrini UI structure seviyesinde hafifce hissettir ama logo-shape clone etme.

### V07 — Dark Garage / Night Work
Controlled dark UI; garage/low-light context'inde okunabilir. Neon gaming/racing veya cyberpunk'a kayma. Safety contrast'i guclu.

### V08 — Field Legibility
High-legibility, larger controls, gloved/awkward use awareness. Premium polish korunsun; accessibility = clunky/basic degil.

### V09 — Expert Dense
Experienced user icin daha fazla information visible, daha compact rhythm. Beginner kritik path'i yine okuyabilsin; fake metrics/jargon uydurma.

### V10 — Balanced Everyday Kavriva
Technical precision + approachable learning + modern consumer product balance. En "default Kavriva" olabilecek orta yol; generic SaaS/fintech hissine dusmesin.

## COLOR / TYPE EXPLORATION BOUNDARY

Final palette ve final font henuz APPROVED degildir.

Bu round'da visual direction farkini test etmek icin:
- dark/light balance,
- neutral family,
- restrained accent family,
- typography character
explore edebilirsin.

Ama:
- exact HEX/RGB'yi final brand decision gibi sunma,
- generated typeface'i final font ilan etme,
- logo formunu palette ugruna degistirme.

## COMPARISON INDEX

10 image tamamlandiktan sonra compact table ver:

| ID | Direction | Strongest trait | Main risk | L05A fit |
|---|---|---|---|---|

Sonra kullanicidan:
- 1-3 favorite variant ID,
- her favoride sevdigi spesifik ozellik,
- varsa kesin istemedigi visual signal
iste.

Kullanici "V03 image treatment + V01 hierarchy + V08 controls" gibi hybrid secim yapabilir.

## USER SELECTION SONRASI

Yeni image generation'a kendi kendine devam etme. Once kullanici secimini analiz et ve su paketi uret:

# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / KAVRIVA ANCHOR VISUAL R2

### A. SOURCE CHECK
### B. ATTACHED LOGO REFERENCE CHECK
### C. FIXED ANCHOR CONTENT / STATE
### D. V01-V10 GENERATED DIRECTIONS
### E. USER SELECTION — VERBATIM
### F. SELECTED VISUAL-DNA CANDIDATES
- typography character
- palette family
- density
- hierarchy
- image treatment
- safety treatment
- shape/surface language
- controls
- spacing
- trust/provenance treatment

### G. LOGO-TO-UI FIT CHECK
L05A'nin selected UI direction ile nerede uyumlu/uyumsuz oldugunu yaz; UI'yi logo geometry clone'una donusturma.

### H. REJECTED / AVOID SIGNALS
Yalniz user feedback varsa.

### I. PRODUCT-RULE RISK CHECK
Safety, trust, uncertainty, accessibility ve recovery semantics bozuluyor mu?

### J. WHAT USER SELECTED VS STILL PROPOSED
Final palette/font/component system uydurma.

### K. RECOMMENDED NEXT DESIGN TASK
Sonraki zorunlu adim full `screen inventory + navigation + critical state coverage` olmalidir. Visual DNA inventory tamamlandiktan sonra screen-by-screen uygulanir.

## DURMA NOKTASI

Round 1: 10 separate image + comparison + user selection request, sonra BEKLE.

User selection sonrasi portable package'i uret ve DUR.

- Repository'ye yazma.
- Full app design'a gecme.
- UI direction'i APPROVED/LOCKED ilan etme.
- Phase 4'e gecme.
