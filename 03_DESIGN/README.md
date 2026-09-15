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
9. **Visual-style exploration — U04 UX structure fixed — CURRENT / READY**
10. Full screen inventory + navigation + critical state coverage
11. Design principles / screen specs
12. Screen-by-screen visual references + user approval
13. Gate 3 -> 4 readiness review

Screen inventory/state coverage zorunlulugu kaldirilmamistir. UX structure ve visual style artik ayni anda degistirilmez; hierarchy once secilir, sonra visual character ayni hierarchy uzerinde kalibre edilir.

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

## Visual Style — Current Task

**USE NOW:**
- `PHASE3_ANCHOR_VISUAL_STYLE_EXPLORATION_AI_PROMPT.md`

Required attachments to the delegated visual-generation chat:
- `Kavriva_L05A.png`
- actual selected `Kavriva_U04_Progressive-Detail.png`

The selected U04 image was referenced by a non-portable local `file:///` path in the delegated handoff. Repository canonical truth is the semantic U04 hierarchy; exact visual fidelity requires the actual screenshot attachment.

### UX Freeze

Across all 10 visual-style variants, these must stay fixed:
- hierarchy order,
- visible-vs-on-demand semantics,
- element-count logic,
- CTA placement logic,
- critical-safety visibility,
- compact trust visibility,
- recovery emphasis,
- progressive-disclosure behavior.

Only these may vary:
- typography character,
- palette family,
- imagery treatment,
- contrast strategy,
- surface/depth language,
- micro-shape/corner language,
- icon character,
- visual polish.

Anti-clutter still applies:
- no card-per-semantic,
- no nested cards,
- no KPI/metric-chip dashboard,
- no equal-weight multiple CTAs,
- no oversized logo or repeated logo geometry.

## Previous UX Feedback

Evidence:
- `ANCHOR_UX_FEEDBACK_01.md`

Earlier anchor-screen outputs were judged crowded / dashboard-like because UX hierarchy and visual styling were varied together and too many semantics were forced into simultaneously prominent blocks.

That approach is deprecated.

## Deprecated Prompts

- `PHASE3_ANCHOR_VISUAL_EXPLORATION_R2_AI_PROMPT.md` — **DEPRECATED / DO NOT USE**.
- Historical V1: `PHASE3_ANCHOR_VISUAL_EXPLORATION_R2_AI_PROMPT_DEPRECATED_V1.md`.
- UX structure calibration prompt — COMPLETED.

## Design Reference Authority

`REFERENCE_INDEX.md` icindeki APPROVED/LOCKED references sonraki design calismalari icin otoritedir.

Current approved references:
- `REF-BRAND-001` -> L05A working logo direction.
- `REF-UX-001` -> U04 working anchor UX hierarchy.

Henuz approved anchor **visual style** yoktur.

## Coverage Rule

Inventory/state phase'inde happy path disinda loading, empty, error, permission, offline, safety hold, teaching-only, uncertainty/dispute, critical correction, interrupted/recovery, inactive-entitlement, migration/conflict ve downgrade states kapsanmalidir.

## Scope Restrictions

Design asamasi:
- Product Discovery requirement'larini sessizce degistiremez.
- UX simplification product semantics'i kaldiramaz.
- Visual style UX hierarchy'yi degistiremez.
- Technology/backend/database/API/auth/sync/framework secemez.
- Final pricing/tier/quota karari veremez.
- Generated visual reference'i user selection + QA olmadan APPROVED/LOCKED ilan edemez.
- Logo selection'i production-ready/trademark-safe asset ilan edemez.

Gate 3 -> 4 icin screen catalog, navigation map, critical state coverage ve yeterli user-approved visual references gereklidir.
