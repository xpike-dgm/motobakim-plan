# KAVRIVA DIAGNOSIS VISUALS — MAIN-MANAGER REVIEW

Status: APPROVED WORKING QA RECORD
Date: 2026-09-16
Scope: FAM-04 Diagnosis / G01–G04 / `SCR-019`–`SCR-021`

## Inputs Reviewed

- User-supplied G01–G04 images
- `KAVRIVA_DIAGNOSIS_VISUALS_01_HANDOFF.md`
- Approved product rules and Phase-3 design authorities

User acceptance evidence:
> genel set iyi

Latest continuation instruction confirms no further refinement request before moving on.

## QA Result

`PASS_WITH_CONSTRAINTS`

The set is suitable as an approved working visual reference family.

## Screen Review

### G01 — Symptom Capture
PASS.
- Plain-language symptom entry is clear.
- Danger-first check is visible before diagnostic continuation.
- Fixture represents the safe choice as selected.

Constraint: in production, if `Hayır veya emin değilim` is selected, normal `Devam et` progression must be disabled/replaced by the appropriate safe-stop path. The screenshot must not be interpreted as authorizing an always-active continue CTA.

### G02 — One Diagnosis Check
PASS.
- One discriminating observation is asked at a time.
- `Emin değilim` is legitimate.
- No tree, part replacement or fabricated threshold is exposed.

### G03 — Supported Outcome
PASS WITH CONSTRAINTS.
- `Bulgular bir yönü destekliyor` correctly avoids definitive diagnosis language.
- Supporting observations are visible.
- `Rehberi incele` is the correct dominant handoff rather than direct repair.

Constraints:
- generated mechanical imagery is illustrative, not diagnostic evidence,
- supported direction cannot bypass `SCR-010` fit/scope/freshness and readiness checks,
- no future copy may turn this state into guaranteed fault identification or repair success.

### G04 — Unresolved Outcome / Handoff
PASS.
- Unresolved is treated as a valid outcome.
- Known vs unknown is separated.
- Additional evidence, summary and safe-support paths avoid a dead end.
- No random replacement is suggested.

## Cross-Family Protections

1. Diagnosis narrows with evidence; it does not manufacture certainty.
2. `Emin değilim` remains a valid input.
3. Photo is contextual evidence, not a mandatory/default step and not automatic diagnosis authority.
4. Previously captured evidence should be reusable at product-behavior level; exact caching/AI implementation is deferred.
5. Supported outcome routes to guide preview, then fit/readiness, before physical application.
6. Unresolved outcome cannot be coerced into a repair recommendation.
7. G01–G04 hidden bottom bar remains PROPOSED ONLY, not routing authority.
8. L05A is preserved; no blue-K/robot/AI-authority mark is introduced.
9. No probability/confidence percentage is approved.
10. Exact copy, icons, components, tokens, accessibility implementation and technology remain non-final.

## Image Provenance

| ID | File | Size | SHA-256 |
|---|---|---:|---|
| G01 | `G01-SCR-019-Symptom-Capture.png` | 941x1672 | `31f864a269e70622b31a6369e26ee5b85ff2dcc9bc8957c48801d6b16a1deedc` |
| G02 | `G02-SCR-020-One-Diagnosis-Check.png` | 941x1672 | `6fc7d07a33265cbe20520a7965eb32bb0596dc2994488098ca479eb88ba906d8` |
| G03 | `G03-SCR-021-Supported-Outcome.png` | 941x1672 | `d91450a59eb5f4d6ea26a129c23b20302de3413398bcd85298bee1884f528168` |
| G04 | `G04-SCR-021-Unresolved-Outcome-Handoff.png` | 941x1672 | `43cf5faf04bbfb9c6eca8c9e3f9aa75bd67acd091ed0c5734b9a5931f1fb3d70` |

PNG binaries are not treated as production assets by this review.

## Next

Proceed to FAM-05 Maintenance / Reminder visual references. Do not move to Phase 4.
