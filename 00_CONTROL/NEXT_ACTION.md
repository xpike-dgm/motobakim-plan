# Next Action — Single Current Work Pointer

Status: `DEBATE-017 / REVIEW-011 CHANGES_REQUESTED — TASK-006 REMEDIATION`
Phase: `PHASE 4 — TECHNOLOGY STRATEGY`
Gate: `3 -> 4 PASSED / 4 -> 5 CLOSED`

## Current Topic

`TSQ-009 — final production download/storage limits and automatic transfer policy`

REVIEW-011 returned `CHANGES_REQUESTED`.

Review result:
- Critical: none;
- Major M-1: required compact core vs required safety media composition/eligibility mapping is ambiguous;
- Major M-2: proposed 25/100/500 MB, 1 GB and 20/10/5% bands are correctly labeled as product policy but not sufficiently derived against adjacent sensitivity points;
- Minor m-1: Android Auto Backup file-based 25 MB per-app-user quota caveat is missing from A6/S15 evidence.

What passed and must not be reopened unless remediation directly regresses it:
- 4 equal policy families;
- 16 × 4 = 64 failure rows;
- 12/12 required fields in every row;
- CON-005: no cellular/mobile-data, roaming or byte-threshold download confirmation;
- core platform mechanism interpretation;
- safety/truth invariants;
- provider-neutral scenario-based TCO;
- no production approval/provider/code/ADR/gate transition.

## Immediate Next Manager Action

Send the narrow REVIEW-011 remediation prompt back to the TASK-006 research chat.

Remediation must stay limited to M-1, M-2 and m-1 plus the minimum HANDOFF-TASK-006 / TASK-006 completion-evidence updates needed to record the remediation.

After remediation, TASK-006 must remain/return to `REVIEW` for a fresh independent re-review.

## Hard Boundaries

- do not reintroduce a cellular/roaming/MB-threshold confirmation gate;
- do not broaden into new implementation or provider research;
- no code, pseudocode, prototype or device test;
- no provider account/trial/purchase/deployment;
- no final provider selection or commercial budget;
- no Phase-5 ADR and no Gate 4 -> 5 transition.
