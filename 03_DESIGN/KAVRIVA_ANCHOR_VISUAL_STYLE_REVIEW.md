# KAVRIVA ANCHOR VISUAL STYLE — MAIN-MANAGER QA

Date: 2026-09-15
Status: PASS_WITH_CONSTRAINTS

## Reviewed Selection

User-selected visual direction:

**V10 — Signature Kavriva**

User-supplied reviewed image:
- filename: `Kavriva_V10_Signature-Kavriva.png`
- dimensions: `887 x 1774`
- SHA-256: `c30b5be3837bfbcf13f19a5eacfb5607a4d664a8d23b9a828f5735cbe7098a3a`

Delegated handoff:
- `03_DESIGN/KAVRIVA_ANCHOR_VISUAL_STYLE_01_HANDOFF.md`

## QA Result

`PASS_WITH_CONSTRAINTS`

V10 is suitable as the **working Kavriva anchor visual direction** because it preserves the approved U04 hierarchy and resolves the repeated card-stack/dashboard problem seen in earlier anchor explorations.

## Strengths Confirmed by Visual Review

- U04 task-first hierarchy remains recognizable.
- One dominant task visual creates a clear inspection focus.
- `Burayı kontrol et` annotation is visually coupled to the physical target rather than becoming a separate content block.
- Instruction, safety note, details affordance, primary CTA and recovery path remain in a single downward task flow.
- No card-per-semantic or KPI/dashboard treatment is introduced.
- Primary CTA is clearly dominant; `Sorun var` remains visible but secondary.
- L05A mark is restrained in the header and does not become a decorative background pattern.
- Electric-blue accent is concentrated mainly in progress, task annotation and the primary action rather than being applied to every element.
- Light canvas + graphite text + realistic inspection imagery supports the calm/technical/approachable Kavriva direction.

## Required Constraints Before Production-Style Expansion

### 1. Trust icon must not imply safety certification

The current visual uses a shield/check-style icon next to `Doğrulanmış rehber • Motosiklete özel`.

This risks implying official safety certification, guaranteed correctness or blanket verification. Product truth only supports context-specific trust/provenance semantics.

**Constraint:** future component refinement must use a more neutral provenance/review/trust signifier or otherwise ensure the icon cannot reasonably be read as a safety-certification badge. Exact replacement icon is NOT decided here.

### 2. Safety and trust semantics must not collapse into one icon language

The safety line also uses shield-like visual language. Trust/provenance and current-step safety are distinct semantics.

**Constraint:** later component-system work should visually distinguish provenance/trust from safety/attention without increasing clutter.

### 3. Exact HEX values are candidate starting points only

The handoff proposes:
- `#F8FAFC`
- `#101827`
- `#5C6B84`
- `#1268F3`
- `#D7DEE8`
- `#0E5BD8`

These are **PROPOSED visual starting tokens**, not final/APPROVED production color tokens. Contrast, accessibility, dark mode and semantic color behavior remain to be validated.

### 4. Generated motorcycle image is treatment reference, not motorcycle-specific evidence

The caliper image demonstrates desired photographic treatment and annotation behavior only. It cannot be reused as if it were verified imagery for a particular real motorcycle/version unless that applicability is independently established.

### 5. Exact geometry is not a production spec

The generated screenshot does not freeze:
- exact spacing,
- typeface,
- font sizes,
- corner radii,
- icon set,
- responsive breakpoints,
- safe-area behavior,
- status-bar/system-chrome treatment.

### 6. Header needs responsive/truncation handling later

The header places brand and motorcycle context on the same line. This is acceptable in the reference, but narrower devices, longer motorcycle names and localization may require a controlled responsive behavior. The exact solution belongs to screen/spec work, not this visual approval.

## Approval Scope

Approved as working direction:
- V10 visual character,
- clean near-white canvas,
- deep graphite/navy text character,
- restrained electric-blue accent,
- realistic inspection-focused photography,
- moderate corner rounding,
- low decoration,
- strong typographic hierarchy,
- restrained L05A presence,
- U04 task-first visual balance.

Not approved/finalized:
- exact color tokens,
- final font/type scale,
- exact component geometry,
- final icon family,
- dark theme,
- responsive behavior,
- production photography assets,
- full-app universal layout,
- implementation code.

## Next Step

Proceed to **full screen inventory + navigation + critical state coverage**.

The inventory phase must use V10 as a visual-DNA reference but must NOT force every screen into the U04 anchor layout. U04 remains anchor-specific; V10 visual principles can inform later screen specs after screen/state structure is known.
