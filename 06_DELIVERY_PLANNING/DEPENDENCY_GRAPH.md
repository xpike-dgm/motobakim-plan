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

Task-level DAG verdicts (one per review cycle, all acyclic): E3 (41 tasks), E10 (18), E5+E6 (41), E4+E9 (29),
E1+E2 (36 with T-E2-014/015), E7+E8 (22) = 187 total. Cross-epic edges are pack references only (seams), never hard
Depends On, except the above epic edges. No hidden dependencies outstanding; full machine-readable edge list in Phase 7.

Step 6 simulation notes (mechanical DAG analysis 2026-09-21 over 185 task rows + 2 added = 187 total):
- Global DAG acyclic: yes. Topological order length = task count. Max dependency depth 6. No duplicate IDs.
  All Depends On references resolve; no dangling edges.
- Removal-impact samples (transitive dependents): T-E3-001 → 19 tasks; T-E1-001 → 19; T-E10-001 → 17;
  T-E2-001 → 13; T-E10-004 → 11; T-E10-007 → 8; T-E3-009 → 7; others ≤5. Blast radius is queryable pre-execution
  via this graph + matrix (owner-readable through catalog rows, not raw IDs).
- Collision rule: tasks sharing a scope (e.g. T-E1-009/T-E1-017 routing taxonomy, T-E1-011/012/013 history screens)
  require frozen pack revisions + distinct outputs for parallel runs; T-E1-012/013 are NOT READY until T-E1-011 DONE.
- Cross-epic seams (pack references, never hard deps): E1/E2/E4/E9 consume E3/E5/E6; all epics consume E10 pack
  schema; E9 proposes / E1 renders / E3 verifies (no E1↔E9 cycle); E2 consumes E8 outputs; E6 decides, E7 executes.
- Manual search remains UNVERIFIED-inclusive until the Phase 8 machine query exists: ambiguous edges are listed,
  never silently dropped.

Bir task'in gizli bagimliligi olmamali.
