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
13. AI Usta UX Structure Calibration — **DONE / A1 APPROVED**
14. **Five-tab main-shell root visual references — CURRENT / READY**
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
- AI Usta root UX: **A1 — Guided Split**, `REF-AIUSTA-001`, DEC-0018.

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

## Approved AI Usta Root UX

Canonical:
- `AI_USTA_UX_STRUCTURE.md`
- `KAVRIVA_AI_USTA_UX_STRUCTURE_REVIEW.md`
- `REF-AIUSTA-001`
- DEC-0018

Direction:
**A1 — Guided Split**

Target:
**1 context + 1 prompt + 2 paths.**

Root:
- compact selected motorcycle context,
- `Nasil yardimci olayim?`,
- `Bir is yapmak istiyorum`,
- `Motorda bir sorun var`,
- optional low-prominence help,
- fixed five-tab nav with AI Usta selected.

Known-task -> `SCR-009`.
Symptom-first -> `SCR-019`.

A1 root free-form technical-answer chat home degildir. Two intents bulky card-stack'e donusturulmez.

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

## Current Task — Five-Tab Main-Shell Root Visual References

**USE NOW:**
`PHASE3_MAIN_SHELL_VISUAL_REFERENCES_AI_PROMPT.md`

This round generates exactly 5 separate root visuals:
- R01 Garaj,
- R02 Bakim,
- R03 AI Usta — A1 fixed,
- R04 Gecmis,
- R05 Topluluk.

Required attachments in delegated visual chat:
- selected `Kavriva_L05A.png`,
- selected `Kavriva_V10_Signature-Kavriva.png`.

Goal:
approved five-tab shell'i ve root responsibilities'i tek coherent visual family olarak test etmek; full app'i bir anda cizmemek.

User reviews only these five roots before deeper visual generation.

## Core Design Protections

- **Accessible does not mean simultaneously prominent.**
- U04 only active-guide anchor DIRECT authority'dir.
- V10 visual DNA'dir, universal layout/token system degildir.
- Shield/check generic trust/safety/certification badge degildir.
- AI Usta technical source-of-truth olamaz ve fit/readiness/safety gates'i bypass edemez.
- A1 two-intent root bulky card-stack olamaz.
- Language/unit/accessibility support profile prerequisite olamaz.
- Generic Settings megascreen, dashboard/KPI home, marketplace home veya permanent social feed convention ile uydurulmaz.

## Still Open

- active physical work sirasinda bottom-bar visibility,
- first post-onboarding landing tab,
- ambiguous full-screen/sheet/modal/inline treatment'lar,
- final production iconography/tokens/components/dark mode,
- exact claim/evidence visual vocabulary,
- optional AI Usta conversational capabilities beyond A1 root.

## Scope Restrictions

Phase 3:
- technology/backend/database/API/auth/sync/framework secemez,
- LLM/provider architecture secemez,
- pricing/tier/quota finalize edemez,
- Gate 3 -> 4 conditions tamamlanmadan Phase 4'e gecemez.

## Gate 3 -> 4

Approved screen/state architecture, navigation, working specs ve AI Usta root UX mevcut. Ancak yeterli screen-by-screen approved visual references tamamlanmadan Gate 3 readiness review yapilmayacak.
