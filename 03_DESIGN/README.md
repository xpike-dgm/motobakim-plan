# 03 — DESIGN

Amac: Discovery source-of-truth'undan Kavriva'nin marka kimligini, user-approved UX/visual direction'larini, ekran/state mimarisini, global navigation'i ve screen specifications'i kontrollu sirayla olusturmaktir.

## Current Phase 3 Sequence

1. Brand naming exploration — **DONE**
2. Brand-name selection + second-pass validation — **DONE**
3. Kavriva explicit brand-name approval — **DONE**
4. Logo exploration Round 01 + Round 02 — **DONE**
5. Logo selection / main-manager QA — **DONE: L05A**
6. Earlier anchor visual R2 attempt — **NOT ACCEPTED / DEPRECATED**
7. Anchor UX Structure Calibration — **DONE**
8. U04 selection + QA — **DONE**
9. Visual-style exploration with U04 fixed — **DONE: V10**
10. Full screen inventory + navigation + critical state coverage — **DONE / USER APPROVED**
11. Screen-family principles + screen specifications — **DONE / APPROVED WORKING SPECS**
12. Global five-tab navigation — **DONE / USER APPROVED**
13. **AI Usta UX Structure Calibration — CURRENT / READY**
14. Five-tab main-shell + family-based visual references + user approval
15. Remaining critical screen/state visual references
16. Gate 3 -> 4 readiness review

## Approved Working References

- Brand: **Kavriva** — `BRAND_NAME.md`, DEC-0012.
- Logo: **L05A — The Precision Fit** — `REF-BRAND-001`, DEC-0013.
- Anchor UX: **U04 — Progressive Detail** — `REF-UX-001`, DEC-0014.
- Anchor visual: **V10 — Signature Kavriva** — `REF-VISUAL-001`, DEC-0015.
- Screen/state architecture: **REF-ARCH-001**, DEC-0016.
- Global navigation: **REF-NAV-001**, DEC-0017.
- Screen-family / UX specs: **REF-SPEC-001**, DEC-0017.

## Approved Global Navigation

Bottom bar:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

Canonical:
- `GLOBAL_NAVIGATION.md`
- `REF-NAV-001`
- DEC-0017

Responsibilities:
- Garaj -> selected motorcycle context / switching / lifecycle,
- Bakim -> maintenance/reminders,
- AI Usta -> known-task + symptom-first primary assistance entry,
- Gecmis -> history/evidence/trust,
- Topluluk -> community Q&A/experience/contribution.

`AI Usta` is a UX role/entry label, not a technology/LLM architecture decision.

## Approved Working Screen Families / Specs

Canonical:
- `SCREEN_FAMILY_SPECS.md`
- `SCREEN_FAMILY_SPEC_REVIEW.md`
- `REF-SPEC-001`

Families:
- FAM-01 First Use / Motorcycle Context
- FAM-02 Guide Discovery / Fit / Preparation
- FAM-03 Active Application / Safety / Recovery
- FAM-04 Diagnosis
- FAM-05 Maintenance / Reminder
- FAM-06 History / Evidence / Trust
- FAM-07 Motorcycle Lifecycle / Entitlement
- FAM-08 Profile / Collaboration
- FAM-09 Community

Controlled refinement:
- `SCR-005` broad action-hub degil; Garaj / motorcycle-context responsibility'sine daraltilmistir.
- task/symptom primary entry AI Usta,
- maintenance primary entry Bakim,
- history primary entry Gecmis,
- community primary entry Topluluk.

This preserves approved capabilities while reducing dashboard/card-stack pressure.

## Current Task — AI Usta UX Structure Calibration

**USE NOW:**
`PHASE3_AI_USTA_UX_CALIBRATION_AI_PROMPT.md`

Reason:
AI Usta center tab olarak approved, fakat exact interaction shape henuz approved degil.

Calibration compares 4 structures:
- A1 Guided Split,
- A2 Hybrid Prompt + Guided Intents,
- A3 Conversation-Led / Structured Handoff,
- A4 Compact Assistant Launcher.

Goal:
known-task ve symptom-first journeys'i en dusuk cognitive load ile ayirip approved flows'a safe handoff yapmak.

This step intentionally separates UX structure from polished visual style.

## Core Design Protections

- **Accessible does not mean simultaneously prominent.**
- U04 only active-guide anchor DIRECT authority'dir.
- V10 visual DNA'dir, universal layout/token system degildir.
- Shield/check generic trust/safety/certification badge degildir.
- AI Usta technical source-of-truth olamaz ve fit/readiness/safety gates'i bypass edemez.
- Language/unit/accessibility support profile prerequisite olamaz.
- Generic Settings megascreen, dashboard/KPI home, marketplace home veya permanent social feed convention ile uydurulmaz.

## Still Open

- AI Usta exact structured/conversational interaction model,
- active physical work sirasinda bottom-bar visibility,
- first post-onboarding landing tab,
- ambiguous full-screen/sheet/modal/inline treatment'lar,
- final production iconography/tokens/components/dark mode,
- exact claim/evidence visual vocabulary.

## Scope Restrictions

Phase 3:
- technology/backend/database/API/auth/sync/framework secemez,
- LLM/provider architecture secemez,
- pricing/tier/quota finalize edemez,
- Gate 3 -> 4 conditions tamamlanmadan Phase 4'e gecemez.

## Gate 3 -> 4

Approved screen/state architecture, navigation ve working specs mevcut. Ancak yeterli screen-by-screen approved visual references tamamlanmadan Gate 3 readiness review yapilmayacak.
