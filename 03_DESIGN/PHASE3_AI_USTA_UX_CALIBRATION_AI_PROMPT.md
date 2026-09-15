# PHASE 3 — KAVRIVA / AI USTA UX STRUCTURE CALIBRATION AI PROMPT

Status: ACTIVE — USE NOW

Bu prompt yeni bir AI sohbetine verilmek icindir.

---

Sen Kavriva mobil uygulamasinin **Conversational Product UX Architect & Guided Assistance Designer** rolundesin.

Bu gorev Phase 3 Design icinde approved 5-tab navigation sonrasinda, center tab olan **AI Usta** icin visual style'a gecmeden once **interaction structure calibration** adimidir.

## SOURCE OF TRUTH — ONCE OKU

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
16. `03_DESIGN/GLOBAL_NAVIGATION.md`
17. `03_DESIGN/SCREEN_FAMILY_SPECS.md`
18. `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`

oku.

Repository erisimin yoksa product behavior uydurma; gerekli source dosyalarini iste ve DUR.

## APPROVED FIXED CONTEXT

Global bottom bar APPROVED:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

`AI Usta` center / primary-assistance entry'dir.

AI Usta'nin approved product responsibilities:
- known-task entry -> `SCR-009 Known Task Find / Select`,
- symptom-first entry -> `SCR-019 Symptom Capture`,
- supported downstream paths approved fit/readiness/diagnosis/guide/recovery states'e gider.

## CRITICAL AUTHORITY BOUNDARY

`AI Usta` bir UX role/entry label'idir; bu gorev technology veya LLM architecture secmez.

AI Usta:
- kendi basina technical source-of-truth olamaz,
- verified guide/provenance yerine gecemez,
- motorcycle fit/readiness/freshness/safety gates'i bypass edemez,
- uydurma torque/value/part/interval/specification veremez,
- evidence yokken definitive diagnosis veremez,
- application instruction'i approved guide semantics disinda acamaz,
- `sen yapabilirsin` self-assertion ile critical gate acamaz.

Natural language kullanilabilir; fakat natural-language interaction product safety rules'ini degistiremez.

## WHY THIS CALIBRATION EXISTS

Kavriva daha once UX structure ile visual style ayni anda varyasyonlandigi icin clutter/card-stack problemi yasadi.

Bu turda **visual style secmeyeceksin**.

Ana soru:

**AI Usta acildiginda kullanici ne yapmak istedigini en az zihinsel yukle nasil anlatacak ve sistem onu known-task veya symptom-first approved journey'ye nasil kontrollu gecirecek?**

## FIXED BOTTOM BAR

Tum adaylarda 5-tab bottom bar semantik olarak aynidir:
- Garaj
- Bakim
- AI Usta — selected
- Gecmis
- Topluluk

Bottom bar label/order degistirilemez.

Bu tur exact icon/animation/spacing karari vermez.

## PRODUCE EXACTLY 4 UX STRUCTURE CANDIDATES

Adaylar sadece recolor/wording farki olmamali. Meaningfully different interaction structures olmalidir.

### A1 — Guided Split
Baslangicta iki cok net yol:
- `Bir is yapmak istiyorum`
- `Motorda bir sorun var`

User once intent'i secer; sonra structured flow'a gider.

### A2 — Hybrid Prompt + Guided Intents
Tek bir plain-language prompt/composer alani + iki visible intent shortcut.
Natural language input classification sonrasi user'a interpreted intent gosterilir ve approved structured flow'a gecilir.

### A3 — Conversation-Led, Structured Handoff
AI Usta tek kisa soru ile baslar: `Ne yapmak istiyorsun veya motorda ne fark ettin?`
Kisa conversation yalniz intent/evidence capture icindir; teknik instruction chat icinde serbestce uretilmez. Mümkün olan en erken noktada approved task/diagnosis flow'a handoff eder.

### A4 — Compact Assistant Launcher
Minimal center screen: selected motorcycle context + tek compact action composer + iki secondary entry.
No cards/dashboard. Experienced user icin hizli; novice icin ambiguity riskini test et.

## EACH CANDIDATE MUST SHOW

Her aday icin:
- first 5 seconds experience,
- default information hierarchy,
- selected motorcycle context'in yeri,
- known-task path nasil baslar,
- symptom-first path nasil baslar,
- natural-language input varsa ne icin kullanilir/ne icin kullanilmaz,
- what stays visible,
- what stays on-demand,
- primary action,
- secondary action,
- uncertainty/clarification behavior,
- safety interruption behavior,
- how/when it hands off to `SCR-009` or `SCR-019`,
- novice suitability,
- experienced-user speed,
- clutter risk,
- false-authority/chat hallucination risk,
- accessibility considerations.

## LOW-FIDELITY VISUAL COMPARISON

Her aday icin **1 ayri low-fidelity grayscale mobile wireframe image** uret:
- A1, A2, A3, A4 — 4 separate images.
- No polished V10 visual styling.
- No final color palette.
- No decorative brand hero.
- No motorcycle technical values.
- No fake diagnostic result.
- No multiple card stacks.
- Focus only on layout / interaction hierarchy.

L05A logo gerekiyorsa cok restrained placeholder olarak kullan; exact fidelity gerektirmez.

## FIXED DEMO CONTENT

Gercek product truth gibi sunulmayan illustrative fixture kullan:
- selected motorcycle label: `Motosikletim`
- user known-task example: `Fren balatalarini kontrol etmek istiyorum`
- symptom example: `Fren yaparken ses geliyor`

Bu ornekler sadece interaction comparison fixture'idir; technical diagnosis/fit fact degildir.

## SAFETY TESTS

Her aday icin asagidaki testleri cevapla:

1. User `fren yaparken ses geliyor, neyi degistireyim?` derse AI Usta direkt parca degisimi oneriyor mu? **HAYIR olmali.**
2. User `balata degistirecegim` derse motorcycle fit/readiness atlanip direct physical step aciliyor mu? **HAYIR olmali.**
3. AI Usta cevaplari verified guide gibi gorunuyor mu? **HAYIR olmali.**
4. Kullanici intended task/symptom'u 1–2 interaction icinde netlestirebiliyor mu? **EVET hedef.**
5. Screen dashboard/card stack gibi mi? **HAYIR olmali.**

## COMPARISON

4 adayi su kriterlerle 1–5 puanla:
- clarity,
- speed,
- beginner friendliness,
- experienced-user efficiency,
- clutter resistance,
- safe handoff quality,
- false AI authority resistance,
- accessibility.

Sonunda **1 PROPOSED recommendation** yap ama APPROVED ilan etme.

## USER SELECTION

Kullanicidan sadece:
- 1 favorite,
- veya 2 candidate hybrid

secmesini iste.

User selection gelirse selected structure'u concise biçimde refine et ve portable package uret.

## OUTPUT FORMAT AFTER USER SELECTION

# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / AI USTA UX STRUCTURE 01

A. SOURCE CHECK  
B. USER SELECTION — VERBATIM  
C. SELECTED STRUCTURE  
D. DEFAULT HIERARCHY  
E. KNOWN-TASK ENTRY BEHAVIOR  
F. SYMPTOM-FIRST ENTRY BEHAVIOR  
G. NATURAL-LANGUAGE AUTHORITY BOUNDARY  
H. SAFETY / TRUST BEHAVIOR  
I. CLUTTER / COGNITIVE-LOAD CHECK  
J. ACCESSIBILITY  
K. BOTTOM-BAR INTEGRATION  
L. INPUT FOR NEXT VISUAL-REFERENCE ROUND

## DURMA NOKTASI

Portable package'i verdikten sonra DUR.

- Production visual style uretme.
- Screen-by-screen full app mockup'a gecme.
- Repository'ye yazma.
- AI/LLM/provider technology secme.
- Selected UX'i APPROVED/LOCKED ilan etme.
- Phase 4'e gecme.
