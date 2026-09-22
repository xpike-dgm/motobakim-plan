# DEPENDENCY RULES

Status: PROPOSED (Group 1, reviewed PASS 2026-09-21; enforced by gates in Group 4, built in Phase 8)

1. Direction: dependencies point toward stability — product truth → contracts → capsules → tasks.
2. Classification and authority boundaries (ADR-001/004) propagate across every edge.
3. Cross-boundary use requires an explicit allowed edge; silent imports are violations.
4. Forbidden: upward private leaks, cycles, ownerless public contracts, untested critical behavior consumers.
5. Detection at gates: orphans, broken links, forbidden dependencies, cycles, ownerless contracts, untested
   critical behavior, stale context packs. A hand-drawn diagram alone never counts.
