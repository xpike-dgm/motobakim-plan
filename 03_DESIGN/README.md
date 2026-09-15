# 03 — DESIGN

Amac: Discovery source-of-truth'undan Kavriva'nin marka kimligini, user-approved UX/visual direction'larini, ekran/state envanterini ve reference sistemini kontrollu sirayla olusturmaktir.

## Current Phase 3 Sequence

1. Brand naming exploration — **DONE**
2. Brand-name selection + second-pass validation — **DONE**
3. Kavriva explicit brand-name approval — **DONE**
4. Logo exploration Round 01 + Round 02 — **DONE**
5. Logo selection / main-manager QA — **DONE: L05A working direction**
6. Anchor visual R2 attempt — **NOT ACCEPTED / DEPRECATED: UX clutter feedback**
7. **Anchor UX Structure Calibration — CURRENT / READY**
8. Selected UX hierarchy QA
9. Visual-style exploration — selected UX structure fixed
10. Full screen inventory + navigation + critical state coverage
11. Design principles / screen specs
12. Screen-by-screen visual references + user approval
13. Gate 3 -> 4 readiness review

Screen inventory/state coverage zorunlulugu kaldirilmamistir. UX structure ve visual style'in ayni anda degistirilmesi artik yasaktir; once hierarchy, sonra visual character kalibre edilir.

## Approved Working Brand

**Kavriva**

Status: `APPROVED WORKING CONSUMER-FACING BRAND NAME`

Canonical source:
- `BRAND_NAME.md`
- DEC-0012

Naming approval legal trademark clearance degildir. Known Kavira/Kaviva similarity risks launch-risk validation olarak korunur.

## Approved Working Logo Direction

**L05A — The Precision Fit**

Status: `APPROVED WORKING DIRECTION`

Canonical source:
- `LOGO_DIRECTION.md`
- `KAVRIVA_LOGO_REVIEW.md`
- DEC-0013
- `REFERENCE_INDEX.md` -> `REF-BRAND-001`

Approved direction semantics:
- precision fit / controlled alignment,
- precise,
- geometric,
- modular,
- controlled,
- restrained angularity,
- deliberate rather than fast,
- calm technical credibility.

Not approved yet:
- production vector master,
- exact geometry/proportions/corner treatment,
- final wordmark font,
- final color palette,
- final launcher-icon spec,
- trademark/legal uniqueness.

## User UX Feedback

Evidence:
- `ANCHOR_UX_FEEDBACK_01.md`

User anchor-screen outputs'i UX olarak karisik buldu ve benzer problemin onceki visual-generation turunda da oldugunu belirtti.

Main-manager diagnosis:
- UX hierarchy + visual style ayni turda varyasyonlandi,
- safety/trust/progress/visual/instruction/success/recovery/detail gibi semantic'ler ayni anda buyuk gorunur blocks olmaya zorlandi,
- image-generation sonucunda card-stack/dashboard hissi tekrarlandi.

Bu diagnosis user feedback'ten turetilmis manager yorumudur; final UX truth degildir.

## UX Simplification Principle

**Accessible != simultaneously prominent.**

Approved product semantics korunur; fakat tum semantics ayni anda ayri buyuk cards olmak zorunda degildir.

Progressive disclosure izinlidir:
- trust/provenance -> compact affordance,
- extra explanation -> on-demand,
- success confirmation -> primary action semantics'ine entegre olabilir,
- recovery -> gorunur ama lower-emphasis,
- motorcycle context -> compact,
- safety -> step criticality'sine gore integrated high-clarity treatment.

Primary UX goal:
User ilk bakista su uc soruyu cevaplayabilmelidir:
1. Ne yapacagim?
2. Nereye bakacagim?
3. Bitirince neye basacagim?

## Current UX Calibration Task

**USE NOW:**
- `PHASE3_ANCHOR_UX_STRUCTURE_CALIBRATION_AI_PROMPT.md`

Selected `Kavriva_L05A.png` image'i ayni delegated sohbetine attach edilmelidir.

Round:
- U01-U05 5 separate UX structure image,
- neutral / monochrome,
- same semantics,
- progressive disclosure,
- no card-per-semantic,
- no dashboard/KPI-chip treatment,
- maximum 1 dominant content surface + 1 primary action zone,
- user selects clearest 1-2 structures.

User selection sonrasi delegated AI:
`PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / KAVRIVA ANCHOR UX STRUCTURE 01`
uretir ve DURUR.

## Visual Style — Only After UX Selection

UX hierarchy main-manager QA'den gectikten sonra yeni visual-style promptu hazirlanir.

O turda selected UX structure SABIT kalir:
- information hierarchy degismez,
- element count logic degismez,
- primary CTA placement logic degismez,
- progressive disclosure degismez.

Yalniz:
- typography character,
- palette family,
- imagery treatment,
- surface depth,
- micro-shape language,
- visual polish
varyasyonlanir.

## Deprecated Prompt

`PHASE3_ANCHOR_VISUAL_EXPLORATION_R2_AI_PROMPT.md` — **DEPRECATED / DO NOT USE**.

Reason: user-reported repeated UX clutter.

Historical V1:
- `PHASE3_ANCHOR_VISUAL_EXPLORATION_R2_AI_PROMPT_DEPRECATED_V1.md`

## Design Reference Authority

`REFERENCE_INDEX.md` icindeki APPROVED/LOCKED references sonraki design calismalari icin otoritedir.

Current approved reference:
- `REF-BRAND-001` -> L05A working logo direction.

Henuz approved anchor UX veya UI visual reference yoktur.

## Coverage Rule

Inventory/state phase'inde happy path disinda loading, empty, error, permission, offline, safety hold, teaching-only, uncertainty/dispute, critical correction, interrupted/recovery, inactive-entitlement, migration/conflict ve downgrade states kapsanmalidir.

## Scope Restrictions

Design asamasi:
- Product Discovery requirement'larini sessizce degistiremez.
- UX simplification product semantics'i kaldiramaz.
- Technology/backend/database/API/auth/sync/framework secemez.
- Final pricing/tier/quota karari veremez.
- Generated UX/visual reference'i user selection + QA olmadan APPROVED/LOCKED ilan edemez.
- Logo selection'i production-ready/trademark-safe asset ilan edemez.

Gate 3 -> 4 icin screen catalog, navigation map, critical state coverage ve yeterli user-approved visual references gereklidir.
