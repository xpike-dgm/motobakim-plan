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
17. Profile / Collaboration K01–K03 — **DONE / APPROVED WITH CONSTRAINTS**
18. Community R05 + L01–L02 — **DONE / APPROVED WITH CONSTRAINTS**
19. User comments / corrections — **PROCESSED**
20. FAM-01 First Use / Motorcycle Context — **PARTIAL USER ACCEPTANCE**
   - `SCR-001 First-Value Entry` — accepted working visual direction
   - `SCR-002 Add Motorcycle` — accepted working visual direction
   - `SCR-003 Motorcycle Identification & Variant Resolution` — accepted working visual direction
   - `SCR-004 Fit Confirmation / Missing Distinction` — **PENDING**
   - `SCR-005 Garaj` — already covered by R01
21. Internal Data & Content Operations requirements/workflow/screen-architecture addendum — **REQUIRED BEFORE GATE 3 REVIEW**
22. Gate 3 -> 4 readiness review

Remaining new consumer-mobile visual screens: **1**.

Partial FAM-01 review record:
- `03_DESIGN/KAVRIVA_FIRST_USE_VISUALS_01_REVIEW.md`

The two Community-family screenshots accidentally mixed into the latest FAM-01 screenshot batch are explicitly excluded from FAM-01 processing. Existing Community authority remains unchanged.

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
- K01–K03 — `REF-PROFILE-001`
- R05 + L01–L02 Community — `REF-COMMUNITY-001`

No full FAM-01 reference has been added to `REFERENCE_INDEX.md` yet because `SCR-004` is still missing.

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

### Profile / Collaboration — `REF-PROFILE-001`
K01–K03 cover optional profile value, migration scope/conflict review and simple attributed/revocable collaboration.

Protections: profile remains optional for current local/core value; migration preserves local usable state and no-silent-overwrite behavior; role/helper/service != verification; revoke does not erase historical attribution/evidence; private content stays separable. K01 literal absolute security/zero-loss wording and shield/check icon are not production authority.

### Community — `REF-COMMUNITY-001`
R05 remains the root/consumption reference. L01 covers explicit community contribution; L02 covers moderation/revise/resubmit/appeal/withdraw.

Protections: sharing is opt-in; public/private scope remains explicit; publication != technical verification; attached photos != verification; withdrawal does not silently erase dependent provenance/history; no likes/followers/reputation/ranking/marketplace mechanics. L02 fixture date and example brand/model/source moderation requests are not universal product rules.

## FAM-01 Partial Visual Acceptance

User accepted the current working visual directions for:
- `SCR-001 — First-Value Entry`
- `SCR-002 — Add Motorcycle`
- `SCR-003 — Motorcycle Identification & Variant Resolution`

Canonical review record:
- `KAVRIVA_FIRST_USE_VISUALS_01_REVIEW.md`

This is deliberately a partial acceptance, not a full family reference. `SCR-004 — Fit Confirmation / Missing Distinction` still needs visual coverage before FAM-01 can be considered complete.

The Community screens `Toplulukla paylaş` and `Katkın incelendi`, although shown in the same screenshot batch, are not part of this FAM-01 acceptance and were not reprocessed as Community authority.

## Current Task Status

Remaining consumer-mobile visual coverage:
- `SCR-004 Fit Confirmation / Missing Distinction`

`SCR-005 Garaj` remains already covered by R01.

After `SCR-004`, the required Phase-3 sequence remains:
1. Internal Data & Content Operations requirements/workflow/platform-independent screen-workspace architecture addendum,
2. Gate 3 -> 4 readiness review,
3. Phase 4 only after the gate is explicitly satisfied/authorized.

## Internal Data & Content Operations — Approved Requirement

Project scope includes an internal operational capability for motorcycle/technical data research, missing/stale/conflicting-data visibility, provenance, controlled update/review/publishing, coverage/data-quality and operational analytics.

Canonical requirement:
`00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`

Exact form is NOT decided: web vs desktop vs hybrid, database/CMS/API/sync, reviewer-role implementation, publishing mechanics, analytics stack and AI/provider choice remain later controlled decisions.

Before Gate 3 -> 4 review, complete a targeted internal-operations requirements/workflow/platform-independent screen-workspace architecture addendum. Final platform-specific internal visual design must wait for later platform/strategy selection.

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
- Readable type and low-clutter hierarchy take priority over decorative minimalism.
- Multi-screen visual outputs should be produced as separate images, not multiple phone pages combined into one image.

## Scope Restrictions

Phase 3 does not select technology/backend/database/API/auth/sync/framework, LLM/provider architecture, internal-tool platform, or final pricing/tier/quota. Gate 3 -> 4 must not be declared passed before remaining critical mobile visual coverage and the internal-operations addendum are sufficiently covered.
