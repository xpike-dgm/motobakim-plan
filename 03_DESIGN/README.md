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
16. Active Application / Safety / Recovery visual references — **DONE / E01–E05 APPROVED WORKING SET WITH CONSTRAINTS**
17. **FAM-04 Diagnosis visual references — CURRENT / READY**
18. Remaining critical screen/state visual references
19. Gate 3 -> 4 readiness review

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
- Active Application / Safety / Recovery visual family: **E01–E05**, `REF-ACTIVE-001`, DEC-0019.

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

## Approved Visual Families

### Root shell — `REF-SHELL-001`
- R01 Garaj
- R02 Bakim
- R03 AI Usta
- R04 Gecmis
- R05 Topluluk

### Guide Discovery / Fit / Preparation — `REF-GUIDE-001`
- D01 `SCR-009`
- D02 `SCR-010`
- D03 `SCR-011`
- D04 `SCR-012`
- D05 `SCR-013`

### Active Application / Safety / Recovery — `REF-ACTIVE-001`
- E01 `SCR-014` — existing V10, U04/V10 direct authority
- E02 `SCR-015`
- E03 `SCR-016`
- E04 `SCR-017`
- E05 `SCR-018`

User explicitly reconfirmed E01–E05 after QA:
> onaylıyorum

Important protections:
- no continue-anyway recovery,
- saved UI progress != current physical proof,
- material guide change does not auto-reverse or guess continuation,
- partial/unresolved/safe-stop remain truthful outcomes,
- safe closure/recovery/revalidation cannot be paywalled,
- active-work bottom-bar behavior remains PROPOSED,
- exact production copy/components/tokens remain non-final.

## Current Task — FAM-04 Diagnosis

**USE NOW:**
`PHASE3_DIAGNOSIS_VISUAL_REFERENCES_AI_PROMPT.md`

Generate exactly 4 visuals covering 3 approved contexts:
- G01 — `SCR-019 Symptom Capture`
- G02 — `SCR-020 One Diagnosis Check`
- G03 — `SCR-021 Supported Outcome`
- G04 — `SCR-021 Unresolved Outcome / Handoff`

`SCR-021` intentionally gets two visuals because both supported and unresolved are legitimate critical product states.

Required attachments:
- `Kavriva_L05A.png`
- selected V10 screenshot
- `R03-AI-Usta.png`
- `E02-SCR-015-Problem-Mismatch-Recovery-v2-L05A.png`

Diagnosis protections:
- danger before diagnostic convenience,
- user can describe symptom without technical terminology,
- evidence-driven narrowing,
- one discriminating check at a time,
- `Emin degilim` is valid,
- no random replacement / parts-cannon behavior,
- no unsupported certainty or fabricated probability,
- unresolved is a legitimate outcome,
- supported outcome routes to guide preview and still requires fit/readiness,
- photo is requested only when materially useful; it is evidence, not automatic diagnosis authority,
- Phase 3 does not choose AI provider/model/API architecture.

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

Remaining critical screen/state visual references tamamlanmadan Gate 3 readiness review yapilmayacak.
