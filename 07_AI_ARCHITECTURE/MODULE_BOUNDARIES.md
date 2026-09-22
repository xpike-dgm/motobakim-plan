# MODULE BOUNDARIES

Status: PROPOSED (Group 1, reviewed PASS 2026-09-21)

Capsule anatomy (every field mandatory): purpose; public contract surface; internal scope; allowed/forbidden
dependencies; tests; change/rollback rules; requirement/design/task/test links.

Public vs internal: only the declared public surface may be used across boundaries; internals (storage layout,
caches, helpers, in-flight state) are invisible outside. Private internals never leak upward.

Seam table (complete as of 2026-09-21; binding, not examples): E9 proposes / E1 renders / E3 verifies
(no E1↔E9 cycle); E2 consumes E8 outputs (E8 derives, E2 renders); E6 ← E3,E5, E7 ← E3,E6 (E6 decides, E7 executes);
E4 ← E3, consumed by E1; E5 identity-plane calls E3 runtime edges (single end-to-end owner: E3); E1/E5 entitlement
render/authorize split (E1 renders, E3 serves, E5 authorizes). Completeness rule: any NEW cross-epic seam must be
declared in this table by the authoring task that first needs it, and pass independent review before use;
undeclared seam use is a violation. New seams follow
the same declare-and-review rule.
