# KAVRIVA ANCHOR UX STRUCTURE — MAIN-MANAGER REVIEW

Status: `PASS_WITH_CONSTRAINTS`
Date: 2026-09-15
Reviewed candidate: `U04 — Progressive Detail`

## Evidence Reviewed

- User-selected UX handoff: `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_01_HANDOFF.md`
- Prior user feedback: anchor-screen outputs felt crowded / dashboard-card-stack-like.
- Approved product source: `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`
- Approved brand: `03_DESIGN/BRAND_NAME.md`
- Approved working logo direction: `03_DESIGN/LOGO_DIRECTION.md`

## Review Result

U04 is accepted as the **working anchor-screen UX hierarchy** for visual-style calibration.

This approval is intentionally narrow. It does NOT establish:
- the final full-app information architecture,
- the final screen catalog,
- a universal layout template for every screen,
- final components, typography, colors or spacing tokens,
- implementation behavior or technical architecture.

## Why U04 Passes

U04 directly addresses the repeated clutter problem by separating **availability** from **simultaneous prominence**.

The default view centers the physical task:
1. current step/context,
2. one dominant visual,
3. one concise instruction,
4. contextual safety,
5. one primary completion action.

Trust/provenance, deeper explanation, expected-success detail and detailed recovery remain accessible without competing with the physical action.

The structure also removes the need for a dedicated success card and keeps the recovery path visible but secondary.

## Constraints That Must Remain

1. `Doğrulanmış rehber` is a compact context-specific trust label, not a certification badge.
2. Critical brake-related safety meaning stays visible; it cannot be hidden inside expandable details.
3. `Sorun var` remains visible but lower-emphasis than the primary completion CTA.
4. The collapsed detail affordance must remain flat/inline; it must not become another visual card.
5. The primary CTA must not claim guaranteed repair success or perfect workmanship.
6. No dashboard, KPI-chip, card-per-semantic or nested-card treatment.
7. One dominant content surface and one clear action zone remain the target.
8. L05A remains restrained brand context and must not compete with the inspection task.
9. Visual-style exploration may not silently reorder the hierarchy or add/remove semantic blocks.
10. U04 is an anchor calibration structure, not proof that every Kavriva screen should use the same composition.

## Visual-Style Round Rule

The next visual-style round must hold U04 fixed.

May vary:
- typography character,
- palette family,
- imagery treatment,
- surface/depth language,
- micro-shape language,
- icon character,
- visual polish.

Must NOT vary:
- hierarchy order,
- visible-vs-on-demand semantics,
- element-count logic,
- CTA placement logic,
- critical-safety visibility,
- trust-label visibility,
- recovery emphasis,
- progressive-disclosure behavior.

## Reference Fidelity

The handoff includes a local Windows `file:///` path for the selected U04 image. That path is not portable and the repository does not contain the PNG binary.

For visual-style generation, the delegated session should receive the actual selected U04 screenshot as an attachment when available, alongside the L05A logo image. The text hierarchy in the canonical UX source remains authoritative for semantics even if image-generation fidelity varies.
