# HANDOFF

## Project
Motobakim

## Persistent Memory Repository
`xpike-dgm/motobakim-plan`

## Current Role
ChatGPT proje mimari muhendisi ve yoneticisi.

## Current Phase
`PHASE-3 / DESIGN — KAVRIVA ANCHOR VISUAL STYLE EXPLORATION READY`

## What Just Happened

Kavriva brand name ve L05A working logo direction daha once onaylandi.

User anchor UX Structure Calibration turunda **U04 — Progressive Detail** yapisini secti:

> U04

Delegated package ana yonetici sohbetine getirildi ve repository'ye kaydedildi:
- `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_01_HANDOFF.md`

Main-manager QA sonucu:
- `PASS_WITH_CONSTRAINTS`
- review: `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_REVIEW.md`

Bunun sonucunda:
- DEC-0014 U04 working anchor UX structure APPROVED,
- `03_DESIGN/ANCHOR_UX_STRUCTURE.md` canonical working anchor hierarchy source,
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-UX-001` APPROVED,
- visual-style exploration acildi,
- `03_DESIGN/PHASE3_ANCHOR_VISUAL_STYLE_EXPLORATION_AI_PROMPT.md` olusturuldu.

## Approved Brand

**Kavriva** — APPROVED working consumer-facing brand.

Source:
- `03_DESIGN/BRAND_NAME.md`
- DEC-0012

## Approved Working Logo Direction

**L05A — The Precision Fit** — APPROVED working direction.

Source:
- `03_DESIGN/LOGO_DIRECTION.md`
- DEC-0013
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-BRAND-001`

Logo direction production vector/font/palette/trademark-safe asset degildir.

## Approved Working Anchor UX

**U04 — Progressive Detail** — APPROVED working anchor UX structure.

Source:
- `03_DESIGN/ANCHOR_UX_STRUCTURE.md`
- `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_REVIEW.md`
- DEC-0014
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-UX-001`

Core principle:
**Accessible does not mean simultaneously prominent.**

Working hierarchy:
1. compact brand/motorcycle/progress context,
2. step title,
3. quiet trust label,
4. one dominant task visual,
5. one focus annotation,
6. concise instruction,
7. integrated critical safety note,
8. collapsed flat detail affordance,
9. one dominant completion CTA,
10. lower-emphasis visible recovery path.

U04 is an anchor calibration hierarchy, NOT the universal layout for all Kavriva screens.

## Why This Matters

Earlier visual-generation rounds repeated the same problem:
- too many semantics were simultaneously prominent,
- card-per-semantic treatment appeared,
- result felt like dashboard/card stack,
- UX hierarchy and visual style were being changed at the same time.

That approach is now deprecated.

Current rule:
**freeze UX first, then vary visual style.**

## Current Visual-Style Task

**USE NOW**
- `03_DESIGN/PHASE3_ANCHOR_VISUAL_STYLE_EXPLORATION_AI_PROMPT.md`

The delegated chat should receive two image attachments:
1. reviewed `Kavriva_L05A.png`,
2. selected actual `Kavriva_U04_Progressive-Detail.png` screenshot.

The U04 handoff included a Windows-local `file:///` link; that path is not portable and the repository does not store the PNG binary. Exact visual-fidelity work must use the actual screenshot attachment.

## UX Freeze During Visual Exploration

Must NOT change across V01-V10:
- hierarchy order,
- element-count logic,
- visible-vs-on-demand semantics,
- primary CTA placement logic,
- critical-safety visibility,
- compact trust visibility,
- recovery emphasis,
- progressive-disclosure behavior.

May change:
- typography character,
- palette family,
- image treatment,
- contrast,
- surface/depth language,
- micro-shape/corner language,
- icon character,
- visual polish.

No:
- new cards/panels,
- nested cards,
- KPI chips,
- equal-weight multiple CTAs,
- new navigation patterns,
- oversized logo or logo-shape cloning.

## Current Phase 3 Sequence

1. Brand naming — DONE.
2. Naming validation — DONE.
3. Kavriva approval — DONE.
4. Logo exploration — DONE.
5. L05A selection + QA — DONE.
6. Earlier Anchor Visual R2 — NOT ACCEPTED / DEPRECATED due to UX clutter.
7. UX Structure Calibration — DONE.
8. U04 selection + QA — DONE.
9. **Visual-style exploration with U04 fixed — CURRENT / READY.**
10. Full screen inventory + navigation + critical state coverage.
11. Design principles / screen specs.
12. Screen-by-screen references + approval.
13. Gate 3 -> 4 review.

## Important Protections

- Approved product semantics cannot be removed for visual simplicity.
- Safety remains visible when critical.
- Trust remains compact but visible.
- Recovery remains visible but secondary.
- U04 approval does not establish the full-app screen catalog.
- No visual style is approved yet.
- Full screen inventory/navigation/state coverage is still mandatory after visual-style selection + QA.
- No technology/backend/database/API/auth/sync/framework decisions are allowed here.

## Next Action

User opens a new AI chat and provides:
1. `03_DESIGN/PHASE3_ANCHOR_VISUAL_STYLE_EXPLORATION_AI_PROMPT.md`,
2. `Kavriva_L05A.png`,
3. `Kavriva_U04_Progressive-Detail.png`.

Delegated AI generates 10 separate images with U04 frozen, then asks for 1-3 favorites/hybrid preference.

After user selection it produces:
`PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / KAVRIVA ANCHOR VISUAL STYLE 01`

and stops.

Main-manager QA is required before full screen inventory begins.

## Last Updated
2026-09-15
