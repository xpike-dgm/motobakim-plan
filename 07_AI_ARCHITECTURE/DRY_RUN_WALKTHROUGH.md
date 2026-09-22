# DRY-RUN WALKTHROUGH (Path-C Manual-Carry Rehearsal)

Status: PROPOSED (Group 3, reviewed PASS 2026-09-21; complementary to ADR-015 Decision 7 simulation, not a substitute)

Scripted no-code rehearsal of one task end to end: pack → manual carry → implement → BLOCKED card →
status line → owner decision → change-request → re-review.

Guardrails: no code, no registry actuation, no bootstrap proof. Open links stay visible as
MISSING / UNOWNED / BLOCKED / CONFLICT / UNVERIFIED.

Pass criteria include an explicit check that no step required the owner to handle technical content.
Failures return as design defects, narrowed to finding rows per DEC-0056 (never as owner tasks).
