# 03 — DESIGN

Amac: Discovery source-of-truth'undan Kavriva'nin marka kimligini, user-approved UX/visual direction'larini, ekran/state envanterini ve reference sistemini kontrollu sirayla olusturmaktir.

## Current Phase 3 Sequence

1. Brand naming exploration — **DONE**
2. Brand-name selection + second-pass validation — **DONE**
3. Kavriva explicit brand-name approval — **DONE**
4. Logo exploration Round 01 + Round 02 — **DONE**
5. Logo selection / main-manager QA — **DONE: L05A working direction**
6. Anchor visual R2 attempt — **NOT ACCEPTED / DEPRECATED: UX clutter feedback**
7. Anchor UX Structure Calibration — **DONE**
8. U04 selection + main-manager QA — **DONE: U04 working anchor hierarchy**
9. Visual-style exploration with U04 fixed — **DONE: V10 working visual direction**
10. **Full screen inventory + navigation + critical state coverage — CURRENT / READY**
11. Design principles / screen specs
12. Screen-by-screen visual references + user approval
13. Gate 3 -> 4 readiness review

Screen inventory/state coverage zorunlulugu kaldirilmamistir. UX structure ve visual style artik ayni anda degistirilmez; hierarchy once secilir, visual character ayni hierarchy uzerinde kalibre edilir ve full-app screen/state architecture bundan sonra kurulur.

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
- final launcher-icon spec,
- trademark/legal uniqueness.

## Approved Working Anchor UX Structure

**U04 — Progressive Detail**

Status: `APPROVED WORKING ANCHOR UX STRUCTURE`

Canonical source:
- `ANCHOR_UX_STRUCTURE.md`
- `KAVRIVA_ANCHOR_UX_STRUCTURE_REVIEW.md`
- DEC-0014
- `REFERENCE_INDEX.md` -> `REF-UX-001`

Core principle:
**Accessible does not mean simultaneously prominent.**

Default task-first hierarchy:
1. compact brand/context/progress,
2. step title,
3. quiet trust label,
4. one dominant visual,
5. one annotation,
6. concise instruction,
7. integrated critical safety,
8. collapsed flat detail affordance,
9. one dominant completion CTA,
10. lower-emphasis visible recovery path.

U04 is an anchor calibration structure only. It is NOT a universal template for every screen and is NOT the final screen catalog/navigation/state architecture.

## Approved Working Anchor Visual Direction

**V10 — Signature Kavriva**

Status: `APPROVED WORKING VISUAL DIRECTION`

Canonical source:
- `ANCHOR_VISUAL_STYLE.md`
- `KAVRIVA_ANCHOR_VISUAL_STYLE_REVIEW.md`
- DEC-0015
- `REFERENCE_INDEX.md` -> `REF-VISUAL-001`

Working visual-DNA:
- clean near-white canvas,
- deep graphite/navy text,
- restrained electric-blue accent,
- realistic inspection-focused imagery,
- moderate rounding,
- low decorative noise,
- strong typographic hierarchy,
- restrained L05A presence,
- calm technical credibility.

Important constraints:
- handoff'taki exact HEX values final production token DEGILDIR,
- shield/check trust/safety iconography final canonical component semantics DEGILDIR,
- generated motorcycle image verified motorcycle-specific evidence DEGILDIR,
- exact font/spacing/radii/responsive behavior henuz final degildir,
- V10 visual direction universal layout degildir.

## Current Screen Inventory Task

**USE NOW:**
- `PHASE3_SCREEN_INVENTORY_AI_PROMPT.md`

Bu tur image/mockup generation yapmaz. Approved Phase-2 product truth'tan:
- candidate screen catalog,
- navigation/transition map,
- critical state matrix,
- journey/business-rule traceability,
- proposed screen-level design principles,
- design gaps/ambiguities

cikarir.

### Critical rule

U04 ve V10 screen inventory icin reference'tir; tum screen'lere universal template olarak kopyalanmaz.

Inventory phase:
- screen inflation yapmamalidir,
- screen vs sheet/modal vs inline-state ayrimini gereksiz yere kilitlememelidir,
- happy path disinda safety hold, teaching-only, mismatch, insufficient evidence, dispute, critical correction, interruption/resume, material guide change, recovery, offline/stale, inactive entitlement, collaboration revoke, transfer/archive/delete ve migration-conflict states'ini kapsamalidir.

## Previous UX Feedback

Evidence:
- `ANCHOR_UX_FEEDBACK_01.md`

Earlier anchor-screen outputs were judged crowded / dashboard-like because UX hierarchy and visual styling were varied together and too many semantics were forced into simultaneously prominent blocks.

That approach is deprecated.

## Deprecated / Completed Prompts

- `PHASE3_ANCHOR_VISUAL_EXPLORATION_R2_AI_PROMPT.md` — **DEPRECATED / DO NOT USE**.
- Historical V1: `PHASE3_ANCHOR_VISUAL_EXPLORATION_R2_AI_PROMPT_DEPRECATED_V1.md`.
- UX structure calibration prompt — COMPLETED.
- Anchor visual-style exploration prompt — COMPLETED.

## Design Reference Authority

`REFERENCE_INDEX.md` icindeki APPROVED/LOCKED references sonraki design calismalari icin otoritedir.

Current approved references:
- `REF-BRAND-001` -> L05A working logo direction.
- `REF-UX-001` -> U04 working anchor UX hierarchy.
- `REF-VISUAL-001` -> V10 working anchor visual direction.

## Coverage Rule

Inventory/state phase'inde happy path disinda loading, empty, error, permission, offline, safety hold, teaching-only, uncertainty/dispute, critical correction, interrupted/recovery, inactive-entitlement, migration/conflict ve downgrade states kapsanmalidir.

## Scope Restrictions

Design asamasi:
- Product Discovery requirement'larini sessizce degistiremez.
- UX simplification product semantics'i kaldiramaz.
- U04'u universal full-app layout yapamaz.
- V10'u exact final design-system token/component karari yapamaz.
- Technology/backend/database/API/auth/sync/framework secemez.
- Final pricing/tier/quota karari veremez.
- Generated/reference artifact'i user selection + QA olmadan APPROVED/LOCKED ilan edemez.
- Logo selection'i production-ready/trademark-safe asset ilan edemez.

Gate 3 -> 4 icin screen catalog, navigation map, critical state coverage ve yeterli user-approved visual references gereklidir.
