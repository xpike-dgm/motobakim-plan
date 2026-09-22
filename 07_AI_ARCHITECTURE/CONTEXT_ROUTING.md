# CONTEXT ROUTING

Status: PROPOSED (Group 3, reviewed PASS 2026-09-21; construction in Phase 8)

## Selection rule (planning-only)

Eligible task = Depends On all DONE + not BLOCKED. Order = topological depth, then Task-ID. Parallel
eligibility is preserved per DEC-0041; "first READY" never implies automation priority.

## Inputs and output

Inputs: registry states, dependency DAG, BLOCKED list. Output: selected task ID + pack pointer (contents are
executed from the pack, not by the router).

## Manual-carrying compatibility (binding)

Copy-paste handoff by the owner is the default (DEC-0051). Allowed free automation = templates + GitHub
automation only (built Phase 7–8). Paid API forbidden without separate cost-sheet + explicit approval
(DEC-0030/0051). Automated actuation (API-opened chats, auto-submit) is HELD for Phase 8.

No router software, API, key, account, purchase or code is selected here.
