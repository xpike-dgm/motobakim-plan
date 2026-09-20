# Next Action — Single Current Work Pointer

Status: `DEBATE-017 / REVIEW-012 OPEN — REMEDIATION RE-REVIEW`
Phase: `PHASE 4 — TECHNOLOGY STRATEGY`
Gate: `3 -> 4 PASSED / 4 -> 5 CLOSED`

## Current Topic

`TSQ-009 — final production download/storage limits and automatic transfer policy`

TASK-006 narrow REVIEW-011 remediation is delivered.

Remediation result:
- M-1: required safety media is now a semantic subset of required compact core; it is not a second additive budget;
- active-task complete package is one verified required-compact-core generation including all required-safety-media bytes;
- M-2: exact 25/50 MB compact, 100/150 MB safety-media, 500 MB/1 GB cache and 20/10/5% free-space values were downgraded to HELD candidate sensitivity/test points because documentary evidence did not justify exact first-release numeric policy;
- m-1: Android Auto Backup 25 MB file-based per-app-user quota caveat is added and explicitly separated from Kavriva download/cache/core limits;
- CON-005 remains intact.

Manager revision-diff note:
- all 64 scenario rows remain present;
- intended changed rows were S01/S02/S07/S08/S15 A–D;
- S03-D and S14-D also changed to propagate the new M-1 rule that required-safety-media cannot be left to the on-demand lane;
- Executive Finding was updated accordingly;
- REVIEW-012 must decide whether these extra changes are necessary consistency corrections and regression-free.

`REVIEW-012 — TASK-006 REVIEW-011 REMEDIATION RE-REVIEW` is OPEN in Drive `05_REVIEWS`.

## Immediate Next Manager Action

Dispatch REVIEW-012 to a fresh independent reviewer.

Do not close TASK-006 or synthesize a final TSQ-009 owner decision before the re-review verdict.

## Hard Boundaries

- CON-005 remains binding: no cellular/mobile-data, roaming or byte-threshold confirmation gate;
- exact numeric production limits remain unapproved/HELD;
- no code, pseudocode, prototype or device test;
- no provider account/trial/purchase/deployment;
- no final provider selection or commercial budget;
- no Phase-5 ADR and no Gate 4 -> 5 transition.
