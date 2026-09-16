# KAVRIVA DIAGNOSIS VISUAL REFERENCES

Status: APPROVED WORKING VISUAL REFERENCE SET
Approved: 2026-09-16
Reference: `REF-DIAG-001`
Authority: explicit user acceptance + main-manager QA
Evidence: `KAVRIVA_DIAGNOSIS_VISUALS_01_HANDOFF.md`
Review: `KAVRIVA_DIAGNOSIS_VISUALS_REVIEW.md`

## Approval Boundary

G01–G04 are approved as working Phase-3 visual references for FAM-04 Diagnosis. Approval covers hierarchy, state distinction, interaction meaning and visual continuity. It does not finalize production copy, components, tokens, navigation implementation, real diagnostic content or AI/backend architecture.

## Approved Working Set

- **G01 — SCR-019 Symptom Capture**
  - plain-language symptom capture,
  - danger-first continuation gate,
  - no diagnosis conclusion at entry.

- **G02 — SCR-020 One Diagnosis Check**
  - one discriminating observation at a time,
  - `Emin değilim` is valid,
  - no full tree / random replacement.

- **G03 — SCR-021 Supported Outcome**
  - evidence supports a broad direction, not a certain fault,
  - supporting observations visible,
  - dominant next action is guide preview,
  - fit/readiness still required before application.

- **G04 — SCR-021 Unresolved Outcome / Handoff**
  - explicit unresolved outcome,
  - known vs unknown separated,
  - gathered evidence preserved,
  - additional evidence / summary / safe-support paths allowed,
  - no fabricated repair recommendation.

## Approved Flow

`AI Usta`
-> `Motorda bir sorun var`
-> G01 / `SCR-019`
-> G02 / `SCR-020`
-> G03 supported OR G04 unresolved / `SCR-021`.

Supported result may continue only through the existing trusted guide system:
`SCR-021`
-> `SCR-010 Guide Scope / Fit`
-> readiness
-> physical application only when conditions permit.

## Required Constraints

1. G01 screenshot represents safe selection. Unsafe/uncertain selection cannot leave normal diagnostic continuation enabled.
2. Evidence narrows possibilities; no unsupported certainty or fabricated probability.
3. Random part replacement / parts-cannon behavior is prohibited.
4. `Emin değilim` and unresolved outcomes remain legitimate.
5. Photo is requested only when materially useful; it is evidence, not automatic diagnosis authority.
6. Generated mechanical imagery is illustrative and is not motorcycle-specific diagnostic evidence.
7. Supported diagnosis direction does not bypass fit/readiness/safety.
8. G01–G04 reduced/hidden bottom navigation remains PROPOSED ONLY.
9. Exact production copy/icons/tokens/accessibility/dark mode remain non-final.
10. No AI/provider/model/API architecture is implied by this reference.

## Image Provenance

| ID | File | Size | SHA-256 |
|---|---|---:|---|
| G01 | `G01-SCR-019-Symptom-Capture.png` | 941x1672 | `31f864a269e70622b31a6369e26ee5b85ff2dcc9bc8957c48801d6b16a1deedc` |
| G02 | `G02-SCR-020-One-Diagnosis-Check.png` | 941x1672 | `6fc7d07a33265cbe20520a7965eb32bb0596dc2994488098ca479eb88ba906d8` |
| G03 | `G03-SCR-021-Supported-Outcome.png` | 941x1672 | `d91450a59eb5f4d6ea26a129c23b20302de3413398bcd85298bee1884f528168` |
| G04 | `G04-SCR-021-Unresolved-Outcome-Handoff.png` | 941x1672 | `43cf5faf04bbfb9c6eca8c9e3f9aa75bd67acd091ed0c5734b9a5931f1fb3d70` |

## Next Visual Family

FAM-05 — Maintenance / Reminder (`SCR-022`–`SCR-024`).
