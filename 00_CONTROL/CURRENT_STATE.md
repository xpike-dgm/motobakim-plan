# CURRENT STATE

## Current Phase

`PHASE-3 / DESIGN — PROFILE + COLLABORATION VISUAL REFERENCES READY`

## Approved Working References

- Kavriva brand — APPROVED
- L05A logo direction — `REF-BRAND-001`
- U04 anchor UX — `REF-UX-001`
- V10 visual direction — `REF-VISUAL-001`
- Screen/state architecture — `REF-ARCH-001`
- Five-tab navigation — `REF-NAV-001`
- Screen-family UX specs — `REF-SPEC-001`
- AI Usta A1 Guided Split — `REF-AIUSTA-001`
- Root visuals R01–R05 — `REF-SHELL-001`
- Guide Discovery / Fit / Preparation D01–D05 — `REF-GUIDE-001`
- Active Application / Safety / Recovery E01–E05 — `REF-ACTIVE-001`
- Diagnosis G01–G04 — `REF-DIAG-001`
- Maintenance / Reminder H01–H04 — `REF-MAINT-001`
- History / Evidence / Trust I01–I06 — `REF-HISTORY-001`
- Motorcycle Lifecycle / Entitlement J01–J05 — `REF-LIFECYCLE-001`

## What Just Changed — FAM-07

User supplied the accepted J01–J05 set and portable handoff. J05 had been refined twice after explicit clutter feedback; accepted authority is J05 v3.

Main-manager QA: `PASS_WITH_CONSTRAINTS`.

Working authority:
- J01 active/inactive switching while preserving inactive history/trust access,
- J02 inactive/archive vs transfer vs delete distinction,
- J03 partial transfer scope/gaps without verification shortcut,
- J04 destructive delete scoped to applicable user-owned data while respecting independent/shared boundaries,
- J05 v3 new-activity gate that preserves existing history/evidence/provenance/correction/export/critical recovery.

Required constraints:
- inactive != delete/history lock,
- archive/inactive != transfer != delete,
- transfer partial != complete and transfer != verification,
- delete cannot silently erase independent/shared data,
- J04 exact irreversibility wording must later align with legal/retention/backup implementation,
- entitlement may gate relevant new activity but not existing truth/safety/history/export/correction/safe-recovery,
- J05 v3 supersedes earlier J05 candidates,
- no final price/tier/quota/billing decision,
- focused-flow bottom navigation remains PROPOSED ONLY.

Canonical:
- `03_DESIGN/MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUAL_REFERENCES.md`
- `03_DESIGN/KAVRIVA_MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUALS_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUALS_REVIEW.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-LIFECYCLE-001`

## Current Phase-3 Sequence

1. Brand/logo/anchor — DONE.
2. Screen architecture/specs/navigation/AI Usta — DONE / APPROVED.
3. Root visuals — DONE / APPROVED.
4. Guide Discovery / Fit / Preparation — DONE / APPROVED.
5. Active Application / Safety / Recovery — DONE / APPROVED.
6. Diagnosis — DONE / APPROVED.
7. Maintenance / Reminder — DONE / APPROVED.
8. History / Evidence / Trust — DONE / APPROVED.
9. Motorcycle Lifecycle / Entitlement — **DONE / APPROVED WITH CONSTRAINTS.**
10. **FAM-08 Profile / Collaboration — READY / CURRENT.**
11. FAM-09 Community — pending critical visual coverage.
12. FAM-01 First Use / Motorcycle Context — remaining visual coverage for SCR-001–SCR-004; SCR-005 Garaj already has R01 authority.
13. Internal Data & Content Operations requirements/workflow/screen-architecture addendum — REQUIRED BEFORE GATE 3 REVIEW.
14. Gate 3 -> 4 readiness review.

Remaining new mobile visual screens at this point: **9**
- FAM-08: 3
- FAM-09: 2 new visuals (`SCR-038` root already R05)
- FAM-01: 4 new visuals (`SCR-005` root already R01)

## Current Prompt

**USE NOW:**
`03_DESIGN/PHASE3_PROFILE_COLLABORATION_VISUAL_REFERENCES_AI_PROMPT.md`

Generate exactly 3 visuals:
- K01 — `SCR-006 Profile / Persistence Value`
- K02 — `SCR-007 Local-to-Profile Migration / Conflict Review`
- K03 — `SCR-034 Participants / Access / Revoke / Attribution`

Required attachments:
- `Kavriva_L05A.png`
- selected V10 screenshot
- `R01-Garaj.png`
- `I03-SCR-027-Record-Work-Self-Hobby-External-Service.png`
- `J01-SCR-008-Motorcycle-Switch-Active-Inactive-Management.png`

Core protections:
- profile is optional for current core/local value where approved,
- language/units/accessibility cannot require profile,
- migration preview + no silent loss/overwrite + conflict review,
- cancel/failure preserves usable local/source state,
- collaborator/helper/service role != verification authority,
- revoke stops future access as scoped but does not erase historical attribution/evidence,
- private/personal content remains separable,
- no auth/sync/backend/provider/pricing invention.

## Internal Data & Content Operations

Still APPROVED project requirement: `00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`.

Before Gate 3 -> 4 readiness, targeted requirements + workflow + screen architecture for the internal data/content operations capability must be completed. Web vs desktop vs hybrid and all technology choices remain open; internal visual design should not be finalized before that platform/strategy work.

## Gate Status

Gate 3 -> 4 HENUZ GECILMEDI.

## Last Refreshed

2026-09-17
