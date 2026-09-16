# 03 — DESIGN

Amac: Discovery source-of-truth'undan Kavriva'nin marka kimligini, user-approved UX/visual direction'larini, ekran/state mimarisini, global navigation'i ve screen specifications'i kontrollu sirayla olusturmaktir.

## Current Phase 3 Sequence

1. Brand naming + validation — **DONE**
2. Kavriva approval — **DONE**
3. Logo exploration + L05A selection — **DONE**
4. Anchor UX U04 — **DONE**
5. Anchor visual V10 — **DONE**
6. Full screen inventory + navigation + critical states — **DONE / USER APPROVED**
7. Screen-family principles + specs — **DONE / APPROVED WORKING SPECS**
8. Five-tab navigation — **DONE / USER APPROVED**
9. AI Usta A1 Guided Split — **DONE / APPROVED**
10. Main-shell root visuals R01–R05 — **DONE / APPROVED**
11. Guide Discovery / Fit / Preparation D01–D05 — **DONE / APPROVED WITH CONSTRAINTS**
12. Active Application / Safety / Recovery E01–E05 — **DONE / APPROVED WITH CONSTRAINTS**
13. Diagnosis G01–G04 — **DONE / APPROVED WITH CONSTRAINTS**
14. Maintenance / Reminder H01–H04 — **DONE / APPROVED WITH CONSTRAINTS**
15. History / Evidence / Trust I01–I06 — **DONE / APPROVED WITH CONSTRAINTS**
16. Motorcycle Lifecycle / Entitlement J01–J05 — **DONE / APPROVED WITH CONSTRAINTS**
17. **FAM-08 Profile / Collaboration — CURRENT / READY**
18. FAM-09 Community — pending 2 new critical visuals; R05 already covers SCR-038 root
19. FAM-01 First Use / Motorcycle Context — pending 4 new visuals; R01 already covers SCR-005 Garaj context
20. Internal Data & Content Operations requirements/workflow/screen-architecture addendum — **REQUIRED BEFORE GATE 3 REVIEW**
21. Gate 3 -> 4 readiness review

Remaining new mobile visual screens: **9**.

## Approved Working References

- Kavriva — `BRAND_NAME.md`, DEC-0012
- L05A — `REF-BRAND-001`, DEC-0013
- U04 — `REF-UX-001`, DEC-0014
- V10 — `REF-VISUAL-001`, DEC-0015
- Screen/state architecture — `REF-ARCH-001`, DEC-0016
- Five-tab navigation — `REF-NAV-001`, DEC-0017
- Screen-family UX specs — `REF-SPEC-001`, DEC-0017
- AI Usta A1 — `REF-AIUSTA-001`, DEC-0018
- R01–R05 — `REF-SHELL-001`
- D01–D05 — `REF-GUIDE-001`
- E01–E05 — `REF-ACTIVE-001`, DEC-0019
- G01–G04 — `REF-DIAG-001`
- H01–H04 — `REF-MAINT-001`
- I01–I06 — `REF-HISTORY-001`
- J01–J05 — `REF-LIFECYCLE-001`

## Approved Global Navigation

**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

- Garaj -> motorcycle context / switching / lifecycle
- Bakim -> maintenance / reminders
- AI Usta -> known-task + symptom-first assistance
- Gecmis -> history / evidence / trust
- Topluluk -> community Q&A / experience / contribution

`AI Usta` UX role/entry label'idir; LLM/provider/backend architecture karari degildir.

## Approved Visual Families

### Root shell — `REF-SHELL-001`
R01 Garaj, R02 Bakim, R03 AI Usta, R04 Gecmis, R05 Topluluk.

### Guide Discovery / Fit / Preparation — `REF-GUIDE-001`
D01 `SCR-009`, D02 `SCR-010`, D03 `SCR-011`, D04 `SCR-012`, D05 `SCR-013`.

### Active Application / Safety / Recovery — `REF-ACTIVE-001`
E01 `SCR-014` existing V10; E02 `SCR-015`; E03 `SCR-016`; E04 `SCR-017`; E05 `SCR-018`.

Protections: no continue-anyway; saved UI progress != physical proof; guide change does not auto-reverse/guess; partial/unresolved/safe-stop remain truthful; active-work bottom-bar behavior remains PROPOSED.

### Diagnosis — `REF-DIAG-001`
- G01 `SCR-019` plain-language symptom + danger-first gate
- G02 `SCR-020` one discriminating check; `Emin degilim` valid
- G03 `SCR-021` supported direction, not certain fault; guide preview next
- G04 `SCR-021` explicit unresolved outcome / handoff

Protections: no random replacement/probability fabrication; unsafe G01 cannot continue normally; photo contextual evidence only; supported result still requires fit/readiness; generated mechanical imagery is not diagnostic evidence; bottom-bar reduction PROPOSED ONLY.

### Maintenance / Reminder — `REF-MAINT-001`
H01 existing R02 Bakim root, H02 item/reminder detail, H03 catch-up priority, H04 uncertain timing.

Protections: no invented interval/km/date/threshold; snooze != completion; due/upcoming state needs supported maintenance source + usable history evidence; standalone user record does not auto-verify truth; H03 is not universal brake-first prioritization; critical correction is separate from routine reminder; deep-flow bottom-bar treatment PROPOSED ONLY.

### History / Evidence / Trust — `REF-HISTORY-001`
I01 existing R04 Gecmis root + I02–I06.

Protections: current usable meaning before event history; actor/source/evidence/current claim state separate; no silent overwrite/fake dispute winner; service role != verification; critical correction survives inactive/entitlement state; basic history/provenance/correction/dispute/export cannot be retroactively paywalled.

### Motorcycle Lifecycle / Entitlement — `REF-LIFECYCLE-001`
J01–J05 cover active/inactive switching, lifecycle actions, transfer scope, delete scope and preserved-access entitlement state.

Protections: inactive != delete/history lock; archive/inactive != transfer != delete; transfer partial != complete and does not verify records; delete respects independent/shared data; new-activity gating cannot lock existing truth/safety/history/export/correction/safe recovery; pricing/tier/quota/legal retention/permission implementation remain non-final.

## Current Task — FAM-08 Profile / Collaboration

**USE NOW:**
`PHASE3_PROFILE_COLLABORATION_VISUAL_REFERENCES_AI_PROMPT.md`

Generate exactly 3 new visuals:
- K01 — `SCR-006 Profile / Persistence Value`
- K02 — `SCR-007 Local-to-Profile Migration / Conflict Review`
- K03 — `SCR-034 Participants / Access / Revoke / Attribution`

Required attachments:
- `Kavriva_L05A.png`
- selected V10 screenshot
- `R01-Garaj.png`
- `I03-SCR-027-Record-Work-Self-Hobby-External-Service.png`
- `J01-SCR-008-Motorcycle-Switch-Active-Inactive-Management.png`

Profile/collaboration protections:
- profile optional for current local/core value where approved,
- language/units/accessibility cannot require profile,
- migration preview + no silent loss/overwrite + conflict review,
- cancel/failure preserves usable local/source state,
- collaborator/helper/service role != verification,
- revoke future access without erasing prior attribution/evidence/history,
- private/personal content remains separable,
- no auth/sync/backend/provider/pricing invention.

## Internal Data & Content Operations — Approved Requirement

Project scope includes an internal operational capability for motorcycle/technical data research, missing/stale/conflicting-data visibility, provenance, controlled update/review/publishing, coverage/data-quality and operational analytics.

Canonical requirement:
`00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`

Exact form is NOT decided: web vs desktop vs hybrid, database/CMS/API/sync, reviewer-role implementation, publishing mechanics, analytics stack and AI/provider choice remain later controlled decisions.

Current mobile family work continues first. A targeted internal-operations requirements/workflow/screen-architecture addendum is required before final Gate 3 -> 4 readiness review. Internal visual design should not be finalized before platform/strategy selection.

## Approved Working Screen Families

- FAM-01 First Use / Motorcycle Context
- FAM-02 Guide Discovery / Fit / Preparation
- FAM-03 Active Application / Safety / Recovery
- FAM-04 Diagnosis
- FAM-05 Maintenance / Reminder
- FAM-06 History / Evidence / Trust
- FAM-07 Motorcycle Lifecycle / Entitlement
- FAM-08 Profile / Collaboration
- FAM-09 Community

Canonical: `SCREEN_FAMILY_SPECS.md`, `SCREEN_FAMILY_SPEC_REVIEW.md`, `REF-SPEC-001`.

## Core Design Protections

- **Accessible does not mean simultaneously prominent.**
- U04 is DIRECT only for active-guide anchor.
- V10 is visual DNA, not universal layout/tokens.
- Shield/check is not generic trust/safety/certification authority.
- AI Usta cannot bypass fit/readiness/safety/trust.
- Language/unit/accessibility support cannot require profile.
- No generic dashboard/KPI home, marketplace home or permanent social-feed convention.
- Bakim reminder list cannot be a dead end; guide entry must be explicit.

## Scope Restrictions

Phase 3 does not select technology/backend/database/API/auth/sync/framework, LLM/provider architecture, or final pricing/tier/quota. Gate 3 -> 4 must not be declared passed before remaining critical visual coverage and the internal-operations addendum are sufficiently covered.
