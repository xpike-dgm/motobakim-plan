# REFERENCE INDEX

Status: ACTIVE

| Reference ID | Screen/State | File / Link | Version | Approval Status | Supersedes |
|---|---|---|---|---|---|
| `REF-BRAND-001` | Kavriva brand / working logo direction | `03_DESIGN/LOGO_DIRECTION.md` | `L05A — The Precision Fit / Round 2` | APPROVED | — |
| `REF-UX-001` | Anchor screen / normal application-ready structure | `03_DESIGN/ANCHOR_UX_STRUCTURE.md` | `U04 — Progressive Detail / UX Calibration 01` | APPROVED | — |
| `REF-VISUAL-001` | Anchor screen / working visual direction | `03_DESIGN/ANCHOR_VISUAL_STYLE.md` | `V10 — Signature Kavriva / Visual Style 01` | APPROVED | — |
| `REF-ARCH-001` | Full-app working screen / transition / critical-state architecture | `03_DESIGN/SCREEN_CATALOG.md` + `NAVIGATION_MAP.md` + `STATE_MATRIX.md` | `Screen Inventory 01 + Main-Manager Refinement` | APPROVED | — |
| `REF-NAV-001` | Global navigation shell | `03_DESIGN/GLOBAL_NAVIGATION.md` | `5-tab: Garaj / Bakim / AI Usta / Gecmis / Topluluk` | APPROVED | Earlier proposed 1/2/3 shell options |
| `REF-SPEC-001` | Full-app working screen-family / UX specifications | `03_DESIGN/SCREEN_FAMILY_SPECS.md` | `Screen Family + Specs 01 + DEC-0017 refinement` | APPROVED | — |
| `REF-AIUSTA-001` | AI Usta root / known-task vs symptom entry structure | `03_DESIGN/AI_USTA_UX_STRUCTURE.md` | `A1 — Guided Split / AI Usta UX Structure 01` | APPROVED | Earlier A1-A4 candidates |
| `REF-SHELL-001` | Five-tab root visual family | `03_DESIGN/MAIN_SHELL_VISUAL_REFERENCES.md` | `R01 Garaj / R02 Bakim / R03 AI Usta / R04 Gecmis / R05 Topluluk` | APPROVED | — |
| `REF-GUIDE-001` | Guide discovery / fit / preparation visual family | `03_DESIGN/GUIDE_DISCOVERY_FIT_PREPARATION_VISUAL_REFERENCES.md` | `D01–D05 / SCR-009–SCR-013` | APPROVED | — |
| `REF-ACTIVE-001` | Active application / safety / recovery visual family | `03_DESIGN/ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES.md` | `E01 existing V10 + refined E02–E05 v2-L05A / SCR-014–SCR-018` | APPROVED | `REF-ACTIVE-CANDIDATE-001` review state |

## Reference Semantics

### REF-BRAND-001

Authorizes L05A as the **working logo direction / brand visual-DNA reference** for Phase-3 design exploration.

It does NOT make the generated PNG a production-ready vector master, final exact geometry, final wordmark typography, final color palette, final launcher-icon specification or trademark-cleared artwork.

### REF-UX-001

Authorizes U04 as the **working anchor-screen UX hierarchy**.

It means task-first progressive-detail hierarchy is approved for the active-guide anchor fixture. It does NOT mean every Kavriva screen must use U04 or exact generated geometry is production specification.

### REF-VISUAL-001

Authorizes V10 as the **working Kavriva visual direction** for downstream screen/reference work.

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

It does NOT approve exact HEX/font/spacing/radii, final icon family, dark theme, responsive behavior or generated mechanical imagery as verified evidence.

QA constraint: shield/check trust/safety iconography is not canonical final component language.

### REF-ARCH-001

Authorizes user-approved working full-app screen architecture:
- `SCREEN_CATALOG.md`,
- `NAVIGATION_MAP.md`,
- `STATE_MATRIX.md`,
- `DESIGN_PRINCIPLES.md`,
- `SCREEN_COVERAGE_TRACEABILITY.md`.

It does NOT mean 38 permanent routes or exact surface implementation.

DEC-0017 later refines global entry distribution without removing approved contexts.

### REF-NAV-001

Authorizes the working 5-tab bottom navigation shell:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

Responsibilities:
- Garaj = motorcycle context/lifecycle,
- Bakim = maintenance/reminders,
- AI Usta = known-task + symptom-first assistance entry,
- Gecmis = history/evidence/trust,
- Topluluk = community experiences/contribution.

`AI Usta` is a UX role/entry label, not an approved technical AI architecture. It cannot bypass fit/readiness/safety/trust rules.

Not finalized by this reference:
- exact icons/animation,
- active-guide bottom-bar visibility,
- first post-onboarding landing tab,
- platform routing implementation.

AI Usta root interaction shape is separately authorized by `REF-AIUSTA-001`.

### REF-SPEC-001

Authorizes:
- 9 screen-family grouping,
- `SCR-001` — `SCR-038` working UX specifications,
- default-view simplicity hierarchy,
- per-context trust/safety/action rules,
- profile-independent language/unit/accessibility refinement,
- controlled `SCR-005` refinement under the five-tab shell.

Exact ambiguous surface modality recommendations remain PROPOSED unless later explicitly approved.

### REF-AIUSTA-001

Authorizes **A1 — Guided Split** as the working AI Usta root interaction structure.

Approved hierarchy:
- compact selected motorcycle context,
- `Nasil yardimci olayim?`,
- `Bir is yapmak istiyorum`,
- `Motorda bir sorun var`,
- optional low-prominence help,
- fixed five-tab bottom navigation with AI Usta selected.

Routing:
- known-task -> `SCR-009`,
- symptom-first -> `SCR-019`.

This reference does NOT authorize:
- a free-form technical-answer chatbot home,
- unsupported technical values or diagnosis,
- fit/readiness/safety bypass,
- LLM/provider/backend architecture,
- final production icon/color/font/spacing tokens.

Visual-reference work must keep the root low-clutter and must not turn the two intents into a bulky card stack.

### REF-SHELL-001

Authorizes the user-accepted **R01–R05 five-tab root visual family** as a working Phase-3 reference set.

Approved root-level behavior:
- Garaj remains motorcycle-context focused,
- Bakim remains maintenance-plan focused,
- AI Usta keeps A1's two-path entry,
- Gecmis remains a scannable history surface,
- Topluluk remains separate-authority community discovery/Q&A.

Approved visual family signals:
- near-white canvas,
- dark graphite/navy typography,
- restrained electric-blue accent,
- low decoration,
- strong title hierarchy,
- moderate rounding,
- restrained L05A presence.

This reference does NOT approve:
- exact bottom-tab icons; screenshots contain icon inconsistencies,
- exact typography/color/spacing/radius tokens,
- exact header/logo geometry,
- R03 decorative motorcycle crop as required A1 structure,
- R05 contribution CTA prominence as a permanent engagement rule,
- community wording as proof of verified authenticity,
- generated motorcycle imagery as technical evidence,
- active-repair bottom-bar behavior,
- first post-onboarding landing tab.

Image provenance and SHA-256 values are recorded in `MAIN_SHELL_VISUAL_REFERENCES.md`; PNG binaries are not stored in this repository.

### REF-GUIDE-001

Authorizes the user-accepted **D01–D05 guide discovery / fit / preparation family** as a working Phase-3 reference set.

Approved working behavior:
- D01 task discovery does not imply fit,
- D02 makes scope/applicability/trust meaning understandable without guarantee semantics,
- D03 distinguishes preparation/readiness before physical work,
- D04 blocks application with remediation + recheck rather than bypass,
- D05 preserves teaching/reference while application is closed.

Required constraints:
- D03 `Uygulamaya hazir` is valid only after all mandatory/critical readiness conditions are actually verified,
- generated example tools/materials/optional items are not technical source-of-truth,
- D02 fit/trust copy is fixture-dependent and cannot be shown without supporting evidence,
- D01–D05 blue K-like generated mark is NOT a new logo direction; L05A remains brand authority,
- D01/D02 visible bottom bar and D03–D05 reduced navigation do not finalize routing/navigation visibility.

Image provenance and SHA-256 values are recorded in `GUIDE_DISCOVERY_FIT_PREPARATION_VISUAL_REFERENCES.md`; PNG binaries are not stored in this repository.

### REF-ACTIVE-001

Authorizes the user-accepted E01-E05 working visual set for FAM-03.

- E01 preserves the existing V10 active-guide reference and was not regenerated.
- E02-E05 authority is the refined `v2-L05A` set.
- Reduced/hidden bottom navigation is PROPOSED ONLY.
- PNG binaries are stored under `03_DESIGN/REFERENCES/ACTIVE_APPLICATION_SAFETY_RECOVERY_01/`.
- The first text-only-header E02-E05 files are superseded review history, not current visual authority.
- Approval does not finalize copy, icons, components, tokens, routing, accessibility validation or implementation.

## Authority Rule

Yalnizca APPROVED veya LOCKED references downstream authority kabul edilir.
