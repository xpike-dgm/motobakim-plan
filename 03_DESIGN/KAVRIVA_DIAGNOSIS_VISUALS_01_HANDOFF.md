# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / DIAGNOSIS VISUALS 01

Status: USER ACCEPTED WORKING VISUAL SET  
Date: 2026-09-16  
Scope: FAM-04 — Diagnosis (`SCR-019`–`SCR-021`)

## A. Source check

The current `main` branch of `xpike-dgm/motobakim-plan` was read at commit:

- `c2b1f0e4676a80761d3be3eaa1db7203ad859597`
- `Record explicit active-family approval and diagnosis prompt`

The requested control, design and approved Phase-2 synthesis sources were checked. Current authority places the project in Phase 3 with FAM-04 Diagnosis as the active visual-reference task. Gate 3 -> 4 has not passed.

No repository files were changed.

## B. Attached reference check

All required visual references were present and used:

- `Kavriva_L05A.png` — exact working brand/logo direction
- `Kavriva_V10_Signature-Kavriva.png` — approved working visual DNA
- `R03-AI-Usta.png` — approved AI Usta entry continuity
- `E02-SCR-015-Problem-Mismatch-Recovery-v2-L05A.png` — approved safety/recovery continuity

L05A was preserved as a restrained black symbol + `Kavriva` wordmark. No blue-K, robot, brain or sparkle authority mark was introduced.

## C. User feedback verbatim

> genel set iyi

Interpretation: G01–G04 are accepted as a working visual-reference set. This does not make copy, tokens, components, navigation behavior or implementation production-final.

## D. Accepted/refined G01–G04 set

| ID | Context | Accepted working meaning | File |
|---|---|---|---|
| G01 | `SCR-019 Symptom Capture` | Plain-language symptom capture with danger-first continuation gate | `G01-SCR-019-Symptom-Capture.png` |
| G02 | `SCR-020 One Diagnosis Check` | One discriminating observation at a time, including `Emin değilim` | `G02-SCR-020-One-Diagnosis-Check.png` |
| G03 | `SCR-021 Supported Outcome` | Evidence supports a broad direction without claiming a certain fault; next step is guide preview | `G03-SCR-021-Supported-Outcome.png` |
| G04 | `SCR-021 Unresolved Outcome / Handoff` | Explicit unresolved result with preserved evidence and useful next paths | `G04-SCR-021-Unresolved-Outcome-Handoff.png` |

No post-feedback refinement was requested.

## E. AI Usta entry continuity

Accepted flow:

`AI Usta`
-> `Motorda bir sorun var`
-> G01 / `SCR-019`
-> G02 / `SCR-020`
-> G03 or G04 / `SCR-021`.

The flow remains a controlled diagnosis path, not a free-form technical-answer chatbot and not a direct repair engine.

## F. Danger-first behavior

G01 places immediate safety before diagnostic convenience:

- asks whether brake response is normal and the motorcycle is stable,
- allows normal continuation only through the represented safe response,
- explicitly tells the user not to continue diagnosis if the answer is no or uncertain,
- retains a clear exit route.

If an unsafe response were selected in production, normal diagnostic progression must stop rather than leave `Devam et` available as though nothing changed.

## G. Evidence/narrowing behavior

- The symptom is captured in ordinary language.
- G02 asks one discriminating observation only: when the sound occurs.
- `Emin değilim` remains a valid answer.
- No complete decision tree is exposed.
- Evidence narrows possibilities; it does not manufacture certainty.
- No part replacement, shopping action, probability or technical threshold is shown.

## H. Supported-outcome behavior

G03 communicates `Bulgular bir yönü destekliyor`, not `kesin arıza`.

- Supporting observations are visible.
- Other possibilities remain accessible.
- No numeric confidence or probability is fabricated.
- The supported direction is deliberately broad: controlled inspection of the front-brake area.
- The dominant action is `Rehberi incele`.
- Guide fit and readiness still require separate checks before application.
- There is no direct `Parçayı değiştir` or active-application CTA.

## I. Unresolved/handoff behavior

G04 treats unresolved diagnosis as a legitimate result:

- clearly states `Sonuç netleşmedi`,
- explains why the observations are insufficient,
- separates what is known from what remains unknown,
- preserves gathered observations,
- offers additional evidence, summary saving and safe-support paths,
- does not invent a failure, replacement or guaranteed repair path,
- avoids failure or shame language.

## J. Photo/evidence cost-aware UX behavior

- Photo capture is not the default interaction on G01 or G02.
- The illustrated G02 check can be answered through a simple observation, so no photo control is shown.
- A future photo request should appear only when it materially reduces uncertainty.
- Previously supplied evidence should be reused rather than repeatedly uploaded.
- A photo remains evidence, never automatic diagnosis authority.
- No AI provider, model or API architecture is selected.

## K. Clutter/trust/safety QA

| QA item | Result |
|---|---|
| Single current job is immediately clear | PASS |
| Danger precedes convenience | PASS |
| Evidence is collected/communicated without invented certainty | PASS |
| Accidental part-replacement suggestion | PASS — none present |
| `Emin değilim` and unresolved meaning are preserved | PASS |
| Photo feels contextual rather than mandatory | PASS |
| L05A is preserved | PASS |
| Screens remain calm and low-clutter | PASS |
| Fabricated percentage/confidence gauge | PASS — none present |
| Generic verification shield/check authority | PASS — none used |

## L. Accessibility notes

- Controls use explicit text labels rather than icon-only meaning.
- Critical caution combines text, icon and color; color is not the sole carrier.
- Primary actions are large and visually distinct.
- Selected/unselected observation states use shape and border treatment as well as color.
- Heading order and reading flow are clear in the fixtures.
- Production work must still validate Dynamic Type, screen-reader order/labels, localization expansion, contrast, focus behavior and dark mode.

## M. Navigation treatment — PROPOSED ONLY

G01–G04 omit the five-tab bottom bar to protect focus in the deeper AI Usta diagnosis flow. This remains a proposed visual treatment only.

It does not finalize:

- whether or when the global bottom bar is hidden,
- route structure,
- gesture/back behavior,
- state persistence after exit,
- platform-specific navigation implementation.

Every fixture retains a visible back or `Tanıdan çık` path. Leaving diagnosis must not fabricate a result.

## N. What remains non-final

- Exact production copy and localization details
- Exact icons, typeface, spacing, radii and color tokens
- Final claim/evidence visual vocabulary
- Responsive and small-screen behavior
- Production accessibility and dark mode
- Exact bottom-bar visibility and routing behavior
- Real technical diagnosis content and evidence rules per motorcycle/task
- Photo-analysis feasibility and implementation
- Technology, backend, database, auth, sync, API, LLM/model/provider architecture
- Pricing, billing, tier or quota decisions
- Gate 3 -> 4 status

## O. Recommended next critical visual family

Recommended next family after controlled repository integration and planning review:

**FAM-05 — Maintenance / Reminder**

- `SCR-022 Maintenance Plan`
- `SCR-023 Maintenance Item / Reminder Detail`
- `SCR-024 Catch-Up & Critical Priorities`

This recommendation does not start that family and does not authorize moving to Phase 4.
