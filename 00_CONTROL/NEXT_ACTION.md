# Next Action — Single Current Work Pointer

Status: `DEBATE-015 MANAGER SYNTHESIS / USER DECISION PENDING`
Phase: `PHASE 4 — TECHNOLOGY STRATEGY`
Gate: `3 -> 4 PASSED / 4 -> 5 CLOSED`

## Current Topic

`DEBATE-015 — Mobile Build/Release Access, Hosted Build Cost and AI Operability Closure`

TASK-003 research/review is complete:
- REVIEW-005 returned CHANGES_REQUESTED with one Major M-1 across all 64 Recovery owner fields and two Minor findings;
- the narrow remediation rewrote all 64 Recovery owner fields and corrected both Minor findings without changing the
  other seven failure-row fields;
- REVIEW-006 returned PASS with no Critical, Major or Minor findings and verified no regression;
- manager readback closed TASK-003 as `DONE` and moved it to Drive `06_DONE`.

Canonical proposal:
`04_TECH_STRATEGY/DEBATES/DEBATE-015__MANAGER_SYNTHESIS.md`

## Immediate Next Manager Action

Present the DEBATE-015 Phase-4 working-direction proposal to the owner for explicit approve/reject/change instruction.

Proposed direction:
- keep Android release continuity independent and active;
- keep iOS/macOS activation HELD until real Mac/Xcode access, Apple signing custody, provider-neutral provenance,
  no-owner-debug recovery and clean-room rebuild are proven;
- use a split/hybrid boundary so Android can stay on a low-cost replaceable path while macOS/iOS capacity is activated
  only when needed;
- avoid a fixed Mac/hosted-build/provider commitment before those activation gates are proven.

Do not create a decision record until the owner explicitly approves or changes the proposal.

## Hard Boundaries

- no Mac/hosted-build/CI/mobile-CI provider or plan winner;
- no provider/store account, trial, purchase, payment or store submission;
- no build, signing setup, certificate/profile/key creation, CI config, code or executable spike;
- no final budget commitment;
- no Phase-5 ADR and no Gate 4 -> 5 transition.
