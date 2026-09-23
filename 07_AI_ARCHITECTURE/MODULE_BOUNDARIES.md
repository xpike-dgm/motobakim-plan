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

Invoke/gate/reference stanza (added 2026-09-23 under DEC-0062, OUT-3 B-16/17 — declare-and-review verdict open;
NON-RUNTIME: these rows never enter the dependency DAG and are enforced by review R-007, not by cycle detection;
prose form is deliberate — arrow syntax would falsely promote them to runtime edges):
E2 invokes E6 flows invoke-only (E2 renders WS-07/WS-11 invoke surfaces T-E2-004/T-E2-005/T-E2-016; E6 authorizes and executes;
exclusively via E3 serving; no direct consumption — Step-2 B-01-new prohibition stands); E3 gate-references E6
(T-E3-033 HELD unless E6 checks pass; T-E3-022 links T-E6-015; E6-from-E3 foundation direction unchanged);
E6 surface-references E1 (T-E6-013 rollout-state surfacing; render-only); E2 served by E3,E5,E8 (serving per the
render/authorize split + E8-output consumption above); E8 sourced from E3 (E8 derives from E3 canonical stores);
E1..E9 served by E10 tooling-plane (registry/pack/checks serve all epics one-way; no epic runtime inbound to E10 —
the Step-2 deferred declaration, made here through the prescribed change-request path).
