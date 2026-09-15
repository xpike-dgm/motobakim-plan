# REFERENCE INDEX

Status: ACTIVE

| Reference ID | Screen/State | File / Link | Version | Approval Status | Supersedes |
|---|---|---|---|---|---|
| `REF-BRAND-001` | Kavriva brand / working logo direction | `03_DESIGN/LOGO_DIRECTION.md` | `L05A — The Precision Fit / Round 2` | APPROVED | — |
| `REF-UX-001` | Anchor screen / normal application-ready structure | `03_DESIGN/ANCHOR_UX_STRUCTURE.md` | `U04 — Progressive Detail / UX Calibration 01` | APPROVED | — |
| `REF-VISUAL-001` | Anchor screen / working visual direction | `03_DESIGN/ANCHOR_VISUAL_STYLE.md` | `V10 — Signature Kavriva / Visual Style 01` | APPROVED | — |
| `REF-ARCH-001` | Full-app working screen / transition / critical-state architecture | `03_DESIGN/SCREEN_CATALOG.md` + `NAVIGATION_MAP.md` + `STATE_MATRIX.md` | `Screen Inventory 01 + Main-Manager Refinement` | APPROVED | — |

## Reference Semantics

### REF-BRAND-001

Authorizes L05A as the **working logo direction / brand visual-DNA reference** for Phase-3 design exploration.

It does NOT make the generated PNG:
- a production-ready vector master,
- final exact geometry,
- final wordmark typography,
- final color palette,
- final launcher-icon specification,
- trademark-cleared artwork.

Exact reviewed visual provenance is recorded in `LOGO_DIRECTION.md` and `KAVRIVA_LOGO_REVIEW.md` including its SHA-256. The repository does not currently store the PNG binary; visual-generation sessions requiring exact fidelity must receive the user-supplied selected image as an attachment.

### REF-UX-001

Authorizes U04 as the **working anchor-screen UX hierarchy** for Phase-3 visual-style calibration.

It means:
- task-first progressive-detail hierarchy is approved for the anchor fixture,
- accessible information does not need simultaneous high prominence,
- visual-style exploration must preserve U04 hierarchy and progressive-disclosure behavior.

It does NOT mean:
- every Kavriva screen must use U04,
- final screen catalog/navigation/state architecture is decided by U04,
- final visual style, font, palette or component system is approved,
- exact generated U04 screenshot geometry is a production specification.

### REF-VISUAL-001

Authorizes V10 as the **working Kavriva anchor visual direction** for Phase-3 screen/spec/reference work.

Working signals:
- clean near-white canvas,
- deep graphite/navy text,
- restrained electric-blue accent,
- realistic inspection-focused imagery,
- moderate corner rounding,
- low decoration,
- strong typographic hierarchy,
- restrained L05A use,
- calm technical credibility.

It does NOT approve/finalize:
- exact HEX values as production tokens,
- exact font/type scale,
- exact spacing/radii,
- final icon family,
- dark theme,
- responsive behavior,
- generated motorcycle imagery as verified motorcycle-specific evidence,
- U04 as a universal layout for every Kavriva screen.

QA constraint: shield/check trust/safety iconography in the selected screenshot is not canonical final component language and must not imply official safety certification or guaranteed correctness.

### REF-ARCH-001

Authorizes the user-approved **working full-app screen architecture** for Phase-3 downstream design work.

Canonical architecture sources:
- `SCREEN_CATALOG.md` — 38 product interaction contexts,
- `NAVIGATION_MAP.md` — product-level transitions,
- `STATE_MATRIX.md` — critical state coverage,
- `DESIGN_PRINCIPLES.md` — approved working screen-level principles,
- `SCREEN_COVERAGE_TRACEABILITY.md` — journey/rule coverage.

This reference means those contexts, transitions and invariants are valid inputs for screen-family/spec work.

It does NOT mean:
- 38 permanent implementation routes are required,
- every candidate is a full screen,
- final bottom navigation/home shell is decided,
- exact sheet/modal/inline choices are locked,
- final MVP scope is decided,
- component library or technology is decided.

Yalnizca APPROVED veya LOCKED referanslar sonraki asamalar icin otorite kabul edilir.
