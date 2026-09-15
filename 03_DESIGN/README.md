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
14. Five-tab main-shell root visual references — **DONE / R01–R05 APPROVED WORKING SET**
15. Guide Discovery / Fit / Preparation visual references — **DONE / D01–D05 APPROVED WORKING SET WITH CONSTRAINTS**
16. **Active Application / Safety / Recovery visual references — CURRENT / READY**
17. Remaining critical screen/state visual references
18. Gate 3 -> 4 readiness review

## Approved Working References

- Brand: **Kavriva** — `BRAND_NAME.md`, DEC-0012.
- Logo: **L05A — The Precision Fit** — `REF-BRAND-001`, DEC-0013.
- Anchor UX: **U04 — Progressive Detail** — `REF-UX-001`, DEC-0014.
- Anchor visual: **V10 — Signature Kavriva** — `REF-VISUAL-001`, DEC-0015.
- Screen/state architecture: **REF-ARCH-001**, DEC-0016.
- Global navigation: **REF-NAV-001**, DEC-0017.
- Screen-family / UX specs: **REF-SPEC-001**, DEC-0017.
- AI Usta root UX: **A1 — Guided Split**, `REF-AIUSTA-001`, DEC-0018.
- Five-tab root visual family: **R01–R05**, `REF-SHELL-001`.
- Guide Discovery / Fit / Preparation visual family: **D01–D05**, `REF-GUIDE-001`.

## Approved Global Navigation

Bottom bar:

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

Responsibilities:
- Garaj -> selected motorcycle context / switching / lifecycle,
- Bakim -> maintenance/reminders,
- AI Usta -> known-task + symptom-first primary assistance entry,
- Gecmis -> history/evidence/trust,
- Topluluk -> community Q&A/experience/contribution.

`AI Usta` is a UX role/entry label, not a technology/LLM architecture decision.

## Approved AI Usta Root UX

Direction: **A1 — Guided Split** (`REF-AIUSTA-001`).

Target: **1 context + 1 prompt + 2 paths.**

Known-task -> `SCR-009`.
Symptom-first -> `SCR-019`.

A1 root free-form technical-answer chat home degildir. Two intents bulky card-stack'e donusturulmez.

## Approved Five-Tab Root Visual Family

Canonical:
- `MAIN_SHELL_VISUAL_REFERENCES.md`
- `KAVRIVA_MAIN_SHELL_VISUALS_REVIEW.md`
- `REF-SHELL-001`

Approved working set:
- R01 Garaj
- R02 Bakim
- R03 AI Usta
- R04 Gecmis
- R05 Topluluk

Root-set constraints:
- exact bottom-tab icons are NOT canonical,
- R03 motorcycle crop is optional visual treatment,
- R05 contribution CTA prominence is not a permanent engagement rule,
- community wording cannot imply unsupported verification/authenticity,
- generated motorcycle imagery is not technical evidence,
- exact fonts/colors/spacing/radii/header geometry remain non-final.

## Approved Guide Discovery / Fit / Preparation Visual Family

Canonical:
- `GUIDE_DISCOVERY_FIT_PREPARATION_VISUAL_REFERENCES.md`
- `KAVRIVA_GUIDE_DISCOVERY_FIT_PREPARATION_VISUALS_REVIEW.md`
- `REF-GUIDE-001`

Working set:
- D01 `SCR-009 Known Task Find / Select`
- D02 `SCR-010 Guide Scope / Fit / Selection Preview`
- D03 `SCR-011 Preparation / Readiness`
- D04 `SCR-012 Readiness Hold / Remediation / Recheck`
- D05 `SCR-013 Teaching-Only Topic View`

Required constraints:
- D03 `Uygulamaya hazir` only after actual mandatory/critical readiness verification,
- generated preparation examples are not technical truth,
- D02 confirmed-fit copy needs real supporting evidence,
- D01–D05 blue K-like generated mark is NOT approved; L05A remains logo authority,
- D01/D02 visible bottom bar and D03–D05 reduced navigation are not final routing decisions.

Continuity:
- AI Usta `Bir is yapmak istiyorum` -> D01/D02,
- Bakim item/detail -> explicit `Bakimi yap` / `Rehberi ac` -> same guide system,
- no sixth `Rehberler` tab.

## Approved Working Screen Families / Specs

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

Canonical:
- `SCREEN_FAMILY_SPECS.md`
- `SCREEN_FAMILY_SPEC_REVIEW.md`
- `REF-SPEC-001`

## Current Task — Active Application / Safety / Recovery Visual References

**USE NOW:**
`PHASE3_ACTIVE_APPLICATION_SAFETY_RECOVERY_VISUAL_REFERENCES_AI_PROMPT.md`

Family:
- E01 = existing approved V10 / `SCR-014 Active Guide Step` — **do not redesign**,
- E02 = `SCR-015 Problem / Mismatch / Recovery`,
- E03 = `SCR-016 Resume Revalidation`,
- E04 = `SCR-017 Material Guide Change / Physical-State Remap`,
- E05 = `SCR-018 Completion / Safe Closure / Record`.

Delegated session generates only E02–E05 as new images. U04/V10 remain direct authority for E01.

Required attachments:
- `Kavriva_L05A.png`
- selected/reviewed V10 active-guide screenshot
- `D03-SCR-011-Preparation-Readiness.png`
- `D04-SCR-012-Readiness-Hold-Recheck.png`
- `D05-SCR-013-Teaching-Only.png`

Important protections:
- do not redraw L05A into the D-series blue K drift,
- no continue-anyway recovery,
- saved UI progress is not current physical proof,
- guide change does not auto-reverse or guess the next step,
- completion cannot coerce partial/unresolved work into success,
- safe closure cannot be paywalled,
- active-work bottom-bar behavior remains PROPOSED until explicitly decided.

## Core Design Protections

- **Accessible does not mean simultaneously prominent.**
- U04 only active-guide anchor DIRECT authority'dir.
- V10 visual DNA'dir, universal layout/token system degildir.
- Shield/check generic trust/safety/certification badge degildir.
- AI Usta technical source-of-truth olamaz ve fit/readiness/safety gates'i bypass edemez.
- A1 two-intent root bulky card-stack olamaz.
- Language/unit/accessibility support profile prerequisite olamaz.
- Generic Settings megascreen, dashboard/KPI home, marketplace home veya permanent social feed convention ile uydurulmaz.
- Bakim reminder listesi dead-end olamaz; ilgili is icin guide flow'a explicit action gerekir.

## Still Open

- active physical work sirasinda exact bottom-bar visibility,
- first post-onboarding landing tab,
- ambiguous full-screen/sheet/modal/inline treatment'lar,
- final production iconography/tokens/components/dark mode,
- exact claim/evidence visual vocabulary,
- optional AI Usta conversational capabilities beyond A1 root,
- exact community contribution CTA weight.

## Scope Restrictions

Phase 3:
- technology/backend/database/API/auth/sync/framework secemez,
- LLM/provider architecture secemez,
- pricing/tier/quota finalize edemez,
- Gate 3 -> 4 conditions tamamlanmadan Phase 4'e gecemez.

## Gate 3 -> 4

Approved screen/state architecture, navigation, working specs, AI Usta root UX, five-tab root visual family and Guide Discovery/Fit/Preparation visual family mevcut. Remaining critical screen/state visual references tamamlanmadan Gate 3 readiness review yapilmayacak.
