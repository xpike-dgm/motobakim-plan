# DEPENDENCY GRAPH

Status: PROPOSED (Step 5 epic-level edges + task-DAG verdicts merged 2026-09-21; full machine-readable edge list in Phase 7)

Epic-level edges (each verified acyclic, no E1<->E9 cycle, no E7→E1 dependency, E4 consumed by E1):

- E3: foundation (no incoming epic edges)
- E10: foundation (no incoming epic edges)
- E5: ← E3
- E6: ← E3, E5
- E4: ← E3 (consumed by E1, not dependent on it)
- E9: ← E3, E1-interface (proposes; E1 renders; E3 verifies)
- E1: ← E3, E5, E4
- E2: ← E3, E5 (consumes E8 outputs; decides nothing owned by E6)
- E7: ← E3, E6 (E1 output is acceptance fixture only)
- E8: ← E3 (E2 renders E8 outputs only)

Task-level DAG verdicts (one per review cycle, all acyclic): E3 (41 tasks), E10 (18), E5 (23) + E6 (18), E4 (19) + E9 (11),
E1 (30) + E2 (17), E7 (9) + E8 (13) = 199 total. Cross-epic edges are pack references only (seams), never hard
Depends On, except the above epic edges. No hidden dependencies outstanding; full machine-readable edge list in Phase 7.

Step 6 simulation notes (mechanical DAG rerun 2026-09-21 over 199 task rows / 110 flows): acyclic yes,
topo length = count, max depth 7, no duplicates, all deps resolve, zero flows without task.
Refresh (2026-09-23, OUT-1 B-08 — mechanical rerun over 206 task rows / 115 flows): acyclic yes,
max depth 8, no duplicates, all deps resolve. Removal-impact samples refreshed:
T-E3-001 → 26 (+1 T-E3-037); T-E1-001 → 28 (+1 T-E1-026); T-E10-001 → 17;
T-E2-001 → 16; T-E10-004 → 11; T-E10-007 → 8; T-E5-013 → 9; T-E3-009 → 8.
- Removal-impact samples (transitive dependents): T-E3-001 → 25; T-E1-001 → 27; T-E10-001 → 17;
  T-E2-001 → 16; T-E10-004 → 11; T-E10-007 → 8; T-E5-013 → 9; T-E3-009 → 8; all others ≤5. Blast radius is queryable pre-execution
  via this graph + matrix (owner-readable through catalog rows, not raw IDs).
  Recompute (2026-09-23 correction, OUT-3 B-28: T-E2-001 was 15, verified 16): parse TASK_INDEX.md Depends-On column,
  reverse-graph BFS per task; the other seven samples re-verified unchanged (25/27/17/11/8/9/8).
- Collision rule: tasks sharing a scope (e.g. T-E1-009/T-E1-017 routing taxonomy, T-E1-011/012/013 history screens)
  require frozen pack revisions + distinct outputs for parallel runs; T-E1-012/013 are NOT READY until T-E1-011 DONE.
- Cross-epic seams (pack references, never hard deps): E1/E2/E4/E9 consume E3/E5/E6; all epics consume E10 pack
  schema; E9 proposes / E1 renders / E3 verifies (no E1↔E9 cycle); E2 consumes E8 outputs; E6 decides, E7 executes.
- Manual search remains UNVERIFIED-inclusive until the Phase 8 machine query exists: ambiguous edges are listed,
  never silently dropped.

Bir task'in gizli bagimliligi olmamali.
