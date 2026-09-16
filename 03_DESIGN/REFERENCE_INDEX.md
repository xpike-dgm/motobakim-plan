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
| `REF-DIAG-001` | Diagnosis visual family | `03_DESIGN/DIAGNOSIS_VISUAL_REFERENCES.md` | `G01–G04 / SCR-019–SCR-021` | APPROVED | — |
| `REF-MAINT-001` | Maintenance / reminder visual family | `03_DESIGN/MAINTENANCE_REMINDER_VISUAL_REFERENCES.md` | `H01 existing R02 + H02–H04 / SCR-022–SCR-024` | APPROVED | — |

## Reference Semantics

### REF-BRAND-001
Authorizes L05A as the working logo direction / brand visual-DNA reference. It does not make the generated PNG a production vector master, exact geometry, final wordmark typography/palette/app-icon specification or trademark-cleared artwork.

### REF-UX-001
Authorizes U04 as the working active-guide anchor hierarchy. It does not make U04 a universal full-app template or exact production geometry.

### REF-VISUAL-001
Authorizes V10 as the working Kavriva visual direction: near-white canvas, graphite/navy typography, restrained electric-blue accent, realistic inspection-focused imagery, moderate rounding, low decoration, strong hierarchy and restrained L05A. Exact HEX/font/spacing/radii/icons/dark-mode/responsive behavior are not final. Generated mechanical imagery is not verified evidence. Generic shield/check trust/safety semantics are not canonical.

### REF-ARCH-001
Authorizes the approved working full-app screen/state architecture in `SCREEN_CATALOG.md`, `NAVIGATION_MAP.md`, `STATE_MATRIX.md`, `DESIGN_PRINCIPLES.md` and `SCREEN_COVERAGE_TRACEABILITY.md`. `SCR-001`–`SCR-038` are product interaction contexts, not a permanent route count. Exact surface implementation remains open where not explicitly approved.

### REF-NAV-001
Authorizes the five-tab shell:
**Garaj · Bakim · AI Usta · Gecmis · Topluluk**.
Responsibilities: Garaj motorcycle context/lifecycle; Bakim maintenance/reminders; AI Usta known-task + symptom-first assistance; Gecmis history/evidence/trust; Topluluk community experience/contribution. Exact icons/animation, active-work bottom-bar behavior, first landing tab and routing implementation remain non-final.

### REF-SPEC-001
Authorizes the 9-family grouping and `SCR-001`–`SCR-038` working UX specifications, including default hierarchy/action/trust/safety behavior and profile-independent language/unit/accessibility refinement. Ambiguous modality recommendations remain PROPOSED unless separately approved.

### REF-AIUSTA-001
Authorizes A1 — Guided Split:
- compact motorcycle context,
- `Nasil yardimci olayim?`,
- `Bir is yapmak istiyorum` -> `SCR-009`,
- `Motorda bir sorun var` -> `SCR-019`,
- optional low-prominence help,
- five-tab shell at root.
It does not authorize a free-form technical-answer chatbot home, unsupported diagnosis/specification, fit/readiness/safety bypass, or LLM/provider/backend architecture.

### REF-SHELL-001
Authorizes R01–R05 as the working five-tab root visual family. Exact tab icons, production tokens/header geometry, R03 decorative image requirement, R05 contribution CTA prominence, generated imagery as technical evidence, active-work bottom-bar behavior and first landing tab remain non-final.

### REF-GUIDE-001
Authorizes D01–D05 Guide Discovery / Fit / Preparation behavior:
- task selection does not imply fit,
- scope/applicability/trust are separated,
- readiness precedes physical work,
- blocked readiness uses remediation + recheck rather than bypass,
- teaching/reference remains available when application is closed.
Constraints: `Uygulamaya hazir` only after actual mandatory/critical verification; generated tool/material examples are not technical truth; confirmed-fit copy requires evidence; D-series blue K drift is not an approved logo; bottom-bar treatments remain non-final.

### REF-ACTIVE-001
Authorizes E01–E05 Active Application / Safety / Recovery behavior. E01 preserves V10; E02–E05 authority is refined `v2-L05A`. Saved UI progress is not physical proof; no continue-anyway recovery; guide change cannot auto-reverse/guess continuation; partial/unresolved/safe-stop remain truthful outcomes. Reduced/hidden bottom navigation is PROPOSED ONLY. Exact copy/components/tokens/routing/accessibility/implementation remain non-final.

### REF-DIAG-001
Authorizes G01–G04 as the working Diagnosis visual family:
- G01 plain-language symptom capture with danger-first gate,
- G02 one discriminating check at a time and `Emin degilim` as valid,
- G03 evidence-supported direction without certain-fault claim and handoff to guide preview,
- G04 explicit unresolved outcome with evidence preservation and useful next paths.
Required constraints:
- unsafe/uncertain G01 state cannot continue normal diagnosis,
- evidence narrows possibilities; no random replacement or fabricated probability,
- photo is contextual evidence, not default/automatic diagnosis authority,
- supported result still requires guide fit/readiness before application,
- generated mechanical imagery is illustrative, not diagnostic evidence,
- reduced/hidden bottom navigation remains PROPOSED ONLY,
- exact copy/tokens/components/accessibility/technology remain non-final.

### REF-MAINT-001
Authorizes H01–H04 as the working Maintenance / Reminder visual family:
- H01 preserves the existing approved R02 Bakim root,
- H02 separates guide entry, actual-work recording and reminder snooze,
- H03 provides calm safety/use-impact-first catch-up ordering,
- H04 explicitly preserves uncertain maintenance timing rather than fabricating due/overdue truth.
Required constraints:
- no invented interval/date/mileage/threshold,
- `Yaklasiyor`/due-type states require applicable verified maintenance support plus usable history/completion evidence,
- user-entered work is not automatically verified truth,
- snooze/postpone never means completed,
- H03 is not a universal `brakes always first` rule,
- critical historical correction remains separate from routine reminder UI,
- generated imagery is illustrative only,
- H02/H03/H04 navigation treatments remain PROPOSED ONLY,
- exact copy/tokens/components/notification cadence/accessibility/technology remain non-final.

## Authority Rule

Only APPROVED or LOCKED references are downstream authority. Working references preserve their stated approval boundaries and do not silently finalize implementation details.
