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
15. **FAM-06 History / Evidence / Trust visual references — CURRENT / READY**
16. Remaining critical mobile visual references
17. Internal Data & Content Operations requirements/workflow/screen-architecture addendum — **REQUIRED BEFORE GATE 3 REVIEW**
18. Gate 3 -> 4 readiness review

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
- H01 existing R02 Bakim root / `SCR-022`
- H02 `SCR-023` maintenance item / reminder detail
- H03 `SCR-024` catch-up / priorities
- H04 `SCR-022/023` uncertain maintenance timing

Protections: no invented interval/km/date/threshold; snooze != completion; due/upcoming state needs supported maintenance source + usable history evidence; standalone user record does not auto-verify truth; H03 is not universal brake-first prioritization; critical correction is separate from routine reminder; deep-flow bottom-bar treatment PROPOSED ONLY.

## Current Task — FAM-06 History / Evidence / Trust

**USE NOW:**
`PHASE3_HISTORY_EVIDENCE_TRUST_VISUAL_REFERENCES_AI_PROMPT.md`

Existing R04 Gecmis root is I01 and must NOT be regenerated.
Generate exactly 5 new visuals:
- I02 — `SCR-026 Historical Record & Provenance`
- I03 — `SCR-027 Record Work — Self / Hobby / External Service`
- I04 — `SCR-028 Correction / Dispute / Evidence Review`
- I05 — `SCR-029 Critical Correction / Safety Reach-Back`
- I06 — `SCR-030 Data Export`

Required attachments:
- `Kavriva_L05A.png`
- selected V10 screenshot
- `R04-Gecmis.png`
- `H02-SCR-023-Maintenance-Item-Reminder-Detail.png`

History/trust protections:
- current usable claim/record meaning before raw event-history detail,
- no silent overwrite or silent dispute winner,
- actor/source/evidence/current claim state are separate meanings,
- service/professional attribution does not auto-create verification,
- critical correction / safety reach-back is stronger than routine reminder and survives inactive/entitlement changes,
- basic history/export/provenance/correction access is not retroactively paywalled,
- no trust score, fabricated certainty or generic certification badge.

## Internal Data & Content Operations — Approved Requirement

Project scope also includes an internal operational capability for motorcycle/technical data research, missing/stale/conflicting-data visibility, provenance, controlled update/review/publishing, coverage/data-quality and operational analytics.

Canonical requirement:
`00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`

Exact form is NOT decided: web vs desktop vs hybrid, database/CMS/API/sync, reviewer-role implementation, publishing mechanics, analytics stack and AI/provider choice remain later controlled decisions.

Current mobile family work continues first. A targeted internal-operations requirements/workflow/screen-architecture addendum is required before final Gate 3 -> 4 readiness review.

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
