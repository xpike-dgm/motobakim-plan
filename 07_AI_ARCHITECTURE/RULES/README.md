# ENFORCEABLE RULES — PROPOSED (Group 4, reviewed PASS 2026-09-21)

Kodlama sirasinda enforce edilecek numarali mimari/engineering kurallari burada parcalanabilir. Her kuralin otomatik, yari otomatik veya manual dogrulama yontemi belirtilmelidir.

Numbered rules derived from Groups 1–3, each with verification method (auto / semi-auto / manual) and owning
gate. Definitions: auto/semi-auto/manual per DEC-0051 (free = templates + GitHub automation; any auto gate
HELD until Phase 8; no API actuation).

- R-001 Capsule anatomy complete — Group 1 — semi-auto.
- R-002 No orphan artifacts — Group 1 — auto (HELD until Phase 8).
- R-003 Dependency direction + explicit allowed edge — Group 1 — auto (HELD until Phase 8).
- R-004 Stable identity + metadata fields present — Group 1 — semi-auto.
- R-005 Pack 14 fields present — Group 3 — semi-auto.
- R-006 Lifecycle states respected — Group 3 — manual.
- R-007 Different-chat review + no self-PASS — Group 3 — manual.
- R-008 Manual-carry default, no API actuation — Group 3 — manual.
- R-009 BLOCKED/change-request discipline — Group 3 — manual.
- R-010 History preservation (supersede, never erase) — Groups 1+3 — manual.
- R-011 Contract fields complete + version/supersedes split — Group 2 — semi-auto.
- R-012 Public-surface + classification propagation — Groups 1+2 — semi-auto.
- R-013 Conformance-test IDs + evidence links present — Group 4 — manual (format gate in Phase 8).
- R-014 Closure-evidence across 10 layers, no open links smoothed — Group 4 — manual.

Every rule cites its source section; rules without a Group 1–3 source were removed. Group 5 may add
change-invoked re-validation rules with reason (deferred note, not smuggled content).

## Rule → enforcing-gate mapping

- Per-task review gate: R-001, R-004, R-005, R-006, R-007, R-008, R-009, R-010, R-011, R-012.
- Release gate: R-013, R-014.
- Bootstrap gate (Phase 8): R-002, R-003 (auto-method rules; per-task review applies interim).
