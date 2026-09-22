# MODULE BOUNDARIES

Status: PROPOSED (Group 1, reviewed PASS 2026-09-21)

Capsule anatomy (every field mandatory): purpose; public contract surface; internal scope; allowed/forbidden
dependencies; tests; change/rollback rules; requirement/design/task/test links.

Public vs internal: only the declared public surface may be used across boundaries; internals (storage layout,
caches, helpers, in-flight state) are invisible outside. Private internals never leak upward.

Seams (binding examples, not exhaustive): E9 proposes / E1 renders / E3 verifies (no E1↔E9 cycle); E2 consumes
E8 outputs; E6 ← E3,E5, E7 ← E3,E6; E4 ← E3, consumed by E1. New seams follow the same declare-and-review rule.
