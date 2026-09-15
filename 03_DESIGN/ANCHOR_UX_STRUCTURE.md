# KAVRIVA ANCHOR UX STRUCTURE

Status: APPROVED WORKING ANCHOR UX STRUCTURE
Approval Date: 2026-09-15
Approved By: USER SELECTION + MAIN-MANAGER QA

## Working Structure

**U04 — Progressive Detail**

Purpose:
Provide a simple, task-first anchor-screen hierarchy for Phase-3 visual-style calibration without repeating the earlier card-stack/dashboard clutter.

This is an **anchor calibration structure**, not the final full-app screen catalog or a universal template for every Kavriva screen.

## Core Principle

**Accessible does not mean simultaneously prominent.**

Approved product semantics remain available, but the default view prioritizes the physical task.

The first glance should answer:
1. What should I do?
2. Where should I look?
3. What should I press when finished?

## Default Hierarchy

1. Compact brand + motorcycle context + progress
2. Step title
3. Quiet first-level trust label
4. One dominant task visual
5. One focus annotation
6. One concise instruction
7. Integrated critical safety note when the step requires it
8. One collapsed flat detail affordance
9. One dominant completion CTA
10. One lower-emphasis visible recovery path

Anchor fixture wording currently used for calibration:
- Step title: `Kaliper kontrolü`
- Progress: `Adım 4 / 9`
- Annotation: `Burayı kontrol et`
- Primary action: `Kontrolü tamamladım`
- Recovery: `Sorun var`

Fixture wording is not a final production copy approval.

## Must Stay Visible

- step title,
- compact progress,
- motorcycle context,
- dominant task visual,
- one focus annotation,
- concise instruction,
- critical safety meaning when applicable,
- compact trust label,
- primary completion action,
- visible lower-emphasis recovery path.

## Accessible On Demand

- full provenance / review chain,
- source/date/freshness detail,
- optional explanation,
- deeper expected-success detail,
- detailed recovery / re-validation guidance,
- additional evidence or rationale,
- expanded external-support guidance where relevant,
- deeper technical/context history where relevant.

## Progressive-Disclosure Rules

- Trust stays visible as a compact first-level label.
- Deeper provenance is accessed through a flat detail affordance.
- Extra explanation is collapsed by default.
- Deeper expected-success detail is on demand.
- Recovery entry remains visible, while detailed recovery flow opens only when needed.
- Critical safety information cannot be hidden inside optional detail.
- Completion is represented by one primary CTA; it must not imply guaranteed repair success or perfect workmanship.
- The collapsed detail affordance must not become a nested card or a second content panel.

## Anti-Clutter Constraints

- No card-per-semantic layout.
- No nested cards.
- No dashboard/KPI/metric-chip treatment.
- No equal-weight multiple CTAs.
- No large trust, safety and progress panels competing at the same time.
- No oversized logo or logo geometry repeated through every component.
- Target: one dominant content surface + one clear primary action zone.

## Safety / Trust Invariants

- `Doğrulanmış rehber` does not mean guaranteed success or official safety certification.
- Critical safety mismatch must stop progression and open recovery / re-validation.
- `Sorun var` cannot silently continue the guide.
- Required critical confirmation remains explicit and reviewable.
- Previous confirmations do not automatically carry forward after interruption, guide change or physical-state uncertainty.
- Core safety information and completion flow cannot be hidden behind optional access or monetization.

## Visual-Style Calibration Boundary

The next visual-style exploration MUST keep this UX structure fixed.

May vary:
- typography character,
- palette family,
- imagery treatment,
- surface/depth language,
- icon character,
- micro-shape language,
- visual polish.

Must NOT vary:
- hierarchy order,
- element-count logic,
- visible-vs-on-demand semantics,
- primary CTA placement logic,
- trust visibility,
- safety visibility,
- recovery emphasis,
- progressive-disclosure behavior.

## Provenance

- User/delegated handoff: `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_01_HANDOFF.md`
- Main-manager QA: `03_DESIGN/KAVRIVA_ANCHOR_UX_STRUCTURE_REVIEW.md`
- Decision record: `00_CONTROL/DECISION_LOG.md` DEC-0014

## Change Rule

If the anchor UX hierarchy changes after later testing, this file must not be silently rewritten without recording the superseding user-approved decision and updating the changelog/reference index.
