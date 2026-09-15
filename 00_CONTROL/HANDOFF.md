# HANDOFF

## Project
Motobakim

## Persistent Memory Repository
`xpike-dgm/motobakim-plan`

## Current Role
ChatGPT proje mimari muhendisi ve yoneticisi.

## Current Phase
`PHASE-3 / DESIGN — AI USTA UX STRUCTURE CALIBRATION READY`

## What Just Happened

User screen-family/spec QA sonrasinda global navigation icin 5-item bottom bar istedi ve explicit olarak onayladi:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

DEC-0017 APPROVED.

Canonical additions:
- `03_DESIGN/GLOBAL_NAVIGATION.md` — APPROVED
- `03_DESIGN/SCREEN_FAMILY_SPECS.md` — APPROVED WORKING SPECS
- `03_DESIGN/SCREEN_FAMILY_SPEC_REVIEW.md` — APPROVED review
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-NAV-001`, `REF-SPEC-001`

## Approved Tab Responsibilities

- **Garaj:** selected motorcycle context, switching, lifecycle.
- **Bakim:** maintenance plan, reminders, catch-up.
- **AI Usta:** center / primary assistance entry for known-task + symptom-first journeys.
- **Gecmis:** history, evidence, trust, correction/dispute, export.
- **Topluluk:** community experiences/Q&A/contribution/moderation, official guide authority'sinden ayri.

## AI Usta Boundary

`AI Usta` bir UX role/entry label'idir, technology/LLM/provider/backend karari degildir.

AI Usta:
- technical source-of-truth yerine gecemez,
- verified guide/provenance yerine gecemez,
- motorcycle fit/readiness/safety gates'i bypass edemez,
- unsupported technical value veya definitive diagnosis uyduramaz,
- known-task -> `SCR-009`, symptom-first -> `SCR-019` approved flows'a controlled entry saglar.

Exact structured/conversational interaction model henuz OPEN design decision'dir.

## Screen-Family Specs

9 working families APPROVED:
- FAM-01 First Use / Motorcycle Context
- FAM-02 Guide Discovery / Fit / Preparation
- FAM-03 Active Application / Safety / Recovery
- FAM-04 Diagnosis
- FAM-05 Maintenance / Reminder
- FAM-06 History / Evidence / Trust
- FAM-07 Motorcycle Lifecycle / Entitlement
- FAM-08 Profile / Collaboration
- FAM-09 Community

All `SCR-001` — `SCR-038` have working specs.

Main-manager refinement:
- language/unit/accessibility support profile/account prerequisite olamaz.

## Controlled Navigation Refinement

`SCR-005` eski broad action hub rolunden Garaj / selected-motorcycle context responsibility'sine daraltilmistir.

Primary entry distribution:
- task + symptom -> AI Usta,
- maintenance -> Bakim,
- history -> Gecmis,
- community -> Topluluk,
- lifecycle / switch -> Garaj.

Capability silinmedi; dashboard/card-stack riskini azaltacak sekilde dagitildi.

## Existing Approved References

- Kavriva — DEC-0012.
- L05A — `REF-BRAND-001`, DEC-0013.
- U04 — `REF-UX-001`, DEC-0014.
- V10 — `REF-VISUAL-001`, DEC-0015.
- Screen architecture — `REF-ARCH-001`, DEC-0016.
- Five-tab navigation — `REF-NAV-001`, DEC-0017.
- Screen-family specs — `REF-SPEC-001`, DEC-0017.

Core principle:
**Accessible does not mean simultaneously prominent.**

## Current Task

**USE NOW:**
`03_DESIGN/PHASE3_AI_USTA_UX_CALIBRATION_AI_PROMPT.md`

Delegated AI must compare exactly 4 low-fidelity AI Usta interaction structures:
- A1 Guided Split
- A2 Hybrid Prompt + Guided Intents
- A3 Conversation-Led / Structured Handoff
- A4 Compact Assistant Launcher

It must keep bottom bar fixed and cannot make AI Usta free-form technical authority.

User selects favorite 1 or hybrid 2. Delegated AI then produces:
`PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / AI USTA UX STRUCTURE 01`
and stops.

## Why This Comes Before Polished Visuals

Earlier Phase-3 clutter problem came from changing UX hierarchy and visual styling at the same time. AI Usta is a new central interaction concept, so its UX structure is calibrated before five-tab polished visual-reference generation.

## Still Open

- AI Usta exact interaction model,
- active-guide bottom bar visibility,
- first post-onboarding landing tab,
- ambiguous surface modalities,
- final icons/tokens/components/dark mode,
- technology/backend/AI architecture,
- pricing/tier/quota.

## Current Sequence

1. Brand — DONE.
2. Logo — DONE.
3. Anchor UX — DONE.
4. Anchor visual — DONE.
5. Screen architecture — DONE / APPROVED.
6. Screen-family specs — DONE / APPROVED working specs.
7. Five-tab navigation — DONE / APPROVED.
8. **AI Usta UX Structure Calibration — CURRENT.**
9. Five-tab main-shell + family-based visual references.
10. Remaining critical visual references.
11. Gate 3 -> 4 review.

No Phase 4 transition yet.

## Last Updated
2026-09-15
