# CURRENT STATE

## Current Phase

`PHASE-3 / DESIGN — AI USTA UX STRUCTURE CALIBRATION READY`

## Current Objective

Phase-2 Product Discovery APPROVED ve Gate 2 -> 3 PASSED.

Approved working design references:
- Brand: **Kavriva** — APPROVED.
- Logo direction: **L05A — The Precision Fit** — APPROVED working direction with QA constraints.
- Anchor UX: **U04 — Progressive Detail** — APPROVED working anchor hierarchy.
- Anchor visual direction: **V10 — Signature Kavriva** — APPROVED working visual direction with QA constraints.
- Full-app working screen/state architecture: **REF-ARCH-001** — APPROVED.
- Global navigation: **REF-NAV-001** — APPROVED.
- Screen-family / UX specifications: **REF-SPEC-001** — APPROVED working specs.

## What Just Changed

User global navigation icin explicit olarak su 5-tab bottom bar'i onayladi:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

DEC-0017 ile:
- `03_DESIGN/GLOBAL_NAVIGATION.md` APPROVED,
- `03_DESIGN/SCREEN_FAMILY_SPECS.md` APPROVED working specs,
- `03_DESIGN/SCREEN_FAMILY_SPEC_REVIEW.md` APPROVED review record,
- `REFERENCE_INDEX.md` -> `REF-NAV-001`, `REF-SPEC-001` APPROVED,
- `SCR-005` broad dashboard/action-hub rolunden Garaj / selected-motorcycle context responsibility'sine controlled refinement ile daraltildi.

## Approved Bottom-Bar Responsibility Split

1. **Garaj** — selected motorcycle context, switch, lifecycle.
2. **Bakim** — maintenance plan/reminders/catch-up.
3. **AI Usta** — center / primary assistance entry for known-task + symptom-first journeys.
4. **Gecmis** — longitudinal history/evidence/trust/correction/export.
5. **Topluluk** — community experiences/Q&A/contribution/moderation; official guide authority'sinden ayri.

## AI Usta Authority Boundary

`AI Usta` bu asamada UX role/entry label'idir; LLM/provider/backend/AI architecture karari DEGILDIR.

AI Usta:
- technical source-of-truth yerine gecemez,
- verified guide/source/provenance yerine gecemez,
- fit/readiness/safety gates'i bypass edemez,
- unsupported technical value veya definitive diagnosis uyduramaz,
- known-task (`SCR-009`) ve symptom-first (`SCR-019`) approved flows'a controlled entry saglar.

## Why Current Task Is UX Calibration Before Visual Generation

User `AI Usta`yi center tab olarak yeni ve kritik bir interaction concept olarak secti. Exact interaction structure henuz belirlenmedi:
- structured intent entry,
- guided prompt,
- conversational interaction,
- hybrid model.

Onceki Phase-3 dersine gore UX structure ile visual style ayni anda degistirilmez. Bu nedenle main-shell visual generation'dan once AI Usta'nin sade interaction hierarchy'si kalibre edilecek.

## Current Phase 3 Sequence

1. Brand naming — DONE.
2. Naming validation — DONE.
3. Kavriva approval — DONE.
4. Logo exploration — DONE.
5. L05A selection + QA — DONE.
6. Earlier Anchor Visual R2 — NOT ACCEPTED / DEPRECATED.
7. UX Structure Calibration — DONE.
8. U04 selection + QA — DONE.
9. Visual-style exploration — DONE: V10.
10. Full screen inventory + navigation + critical state coverage — DONE / USER APPROVED.
11. Screen-family principles + screen specifications — DONE / APPROVED WORKING SPECS.
12. Global five-tab navigation — DONE / USER APPROVED.
13. **AI Usta UX Structure Calibration — READY / CURRENT.**
14. Five-tab main-shell + family-based visual references + user approval.
15. Remaining critical screen/state visual references.
16. Gate 3 -> 4 readiness review.

## Current Prompt

**USE NOW:**
`03_DESIGN/PHASE3_AI_USTA_UX_CALIBRATION_AI_PROMPT.md`

Delegated AI:
- approved five-tab shell'i degistiremez,
- AI Usta icin 4 meaningfully different low-clutter interaction structures uretir,
- known-task + symptom-first approved journeys'i korur,
- free-form unsupported technical-answer chatbot'i authority gibi tasarlayamaz,
- image/mockup style polish ile UX decision'i karistirmadan low-fidelity structure comparison yapar,
- user selection sonrasi portable handoff uretip DURUR.

## Still Open — Not Errors

- AI Usta exact interaction form,
- active physical work sirasinda bottom-bar visibility/interaction,
- first post-onboarding landing tab,
- ambiguous screen/sheet/modal mappings,
- final iconography/tokens/dark mode/components,
- exact claim/evidence visual vocabulary,
- technology/backend/AI architecture,
- pricing/tier/quota.

Language/unit ve accessibility support profile/account prerequisite olamaz.

## Gate Status

Gate 3 -> 4 HENUZ GECILMEDI.

Screen/state architecture, global navigation ve working specs approved olsa da yeterli screen-by-screen approved visual references tamamlanmadan Gate 3 readiness review yapilmaz.

## Last Refreshed

2026-09-15
