# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / KAVRIVA ANCHOR UX STRUCTURE 01

## A. SOURCE CHECK

- Current phase: Phase 3 — Anchor UX Structure Calibration.
- Working brand: Kavriva — APPROVED.
- Working logo direction: L05A — The Precision Fit — APPROVED WITH CONSTRAINTS.
- Product source: Approved Phase-2 Product Synthesis.
- User feedback: anchor screen previously felt crowded and dashboard/card-stack-like.
- L05A is used only as restrained brand context, not as a large decorative hero.

## B. USER FEEDBACK PROBLEM STATEMENT

Previous screens made motorcycle context, progress, visual guidance, trust, safety, instruction, success, recovery and explanation simultaneously prominent.

Correction principle:

**Accessible does not mean simultaneously prominent.**

Approved semantics remain available, but the default screen must prioritize:

1. What should I do?
2. Where should I look?
3. What should I press when finished?

## C. U01–U05 STRUCTURES

- U01 — Visual First / Guided Step — Visual leads the task.
- U02 — Instruction First / Compact Visual — Action sentence leads.
- U03 — Full-Screen Step Canvas — One continuous visual canvas.
- U04 — Progressive Detail — Core path visible, deeper detail on demand.
- U05 — Balanced Everyday — Balanced consumer-product default.

Selected candidate: `U04 — Progressive Detail`.

Original delegated-session local link was non-portable:
`file:///C:/Users/Xpike/Documents/Codex/2026-09-15/phase-3-kavriva-anchor-ux-structure/outputs/Kavriva_U04_Progressive-Detail.png`

## D. USER SELECTION — VERBATIM

> U04

## E. SELECTED UX HIERARCHY

U04 default hierarchy:

1. Compact brand, motorcycle context and progress
2. Step title: `Kaliper kontrolü`
3. Quiet first-level trust label
4. One dominant brake-caliper visual
5. One focus annotation: `Burayı kontrol et`
6. One concise instruction
7. Integrated critical safety note
8. One collapsed detail affordance
9. One dominant completion CTA: `Kontrolü tamamladım`
10. Lower-emphasis recovery path: `Sorun var`

No separate success card is required.

## F. PROGRESSIVE-DISCLOSURE RULES

- Trust remains visible as a compact label.
- Deeper provenance, source, reviewer, date, applicability and uncertainty remain behind the detail affordance.
- Extra explanation remains collapsed by default.
- Deeper expected-success detail is available on demand.
- `Sorun var` remains visible, but recovery guidance opens only when needed.
- Safety remains visible because this is a brake-related step; it must not be hidden inside details.
- Completion is integrated into the primary action, but the action must not imply guaranteed repair success or perfect workmanship.
- The collapsed detail affordance must be a flat inline row, not a nested card.

## G. WHAT MUST STAY VISIBLE VS ACCESSIBLE-ON-DEMAND

### Must stay visible
- Step title and `Adım 4 / 9`
- Motorcycle context
- Main visual and one annotation
- Concise instruction
- Critical safety meaning
- Compact trust label
- Primary CTA
- Secondary `Sorun var` path

### Accessible on demand
- Full provenance and review chain
- Source/date/freshness detail
- Optional explanation
- Deeper expected-success detail
- Detailed recovery and re-validation guidance
- Additional evidence or rationale
- Expanded help or external-support guidance
- Full technical/context history where relevant

## H. CLUTTER / COGNITIVE-LOAD RISKS

- The detail row can become a third card if visually over-emphasized.
- Trust icons must not imply safety certification or guaranteed outcome.
- The instruction should remain one short sentence, ideally no more than two lines.
- `Sorun var` must not become an equal-weight CTA.
- The primary CTA should remain visually sticky and immediately findable.
- The L05A mark should stay small and contextual; it must not compete with the physical inspection task.
- Hidden detail must be discoverable without becoming a second content surface.
- No dashboard, KPI, metric-chip or card-per-semantic treatment.

## I. PRODUCT-RULE SAFETY CHECK

- No torque, part number, measurement or technical specification is fabricated.
- This fixture assumes normal application-ready state; it does not bypass motorcycle fit, variant or readiness verification.
- The motorcycle must be stable and the work area safe before continuation.
- A safety mismatch must stop progression and open recovery/re-validation.
- `Sorun var` must not silently continue the guide.
- Critical confirmation must remain explicit and reviewable.
- Previous confirmations must not automatically carry forward after interruption, guide change or physical-state uncertainty.
- Trust language must remain context-specific; `Doğrulanmış rehber` does not mean guaranteed success.
- Required safety information and core completion flow cannot be hidden behind monetization or optional access.

## J. INPUT FOR NEXT VISUAL-STYLE EXPLORATION

After main-manager QA, use U04 as the fixed UX hierarchy.

The next visual-style round may change only:
- typography character,
- palette,
- surface language,
- imagery treatment,
- micro-shape language,
- visual polish and character.

It must not change:
- information hierarchy,
- element count,
- CTA placement logic,
- progressive-disclosure behavior,
- trust visibility,
- safety visibility,
- recovery emphasis.

This package is a UX structure handoff, not a final screen-catalog decision. No visual-style exploration is generated in this step.
