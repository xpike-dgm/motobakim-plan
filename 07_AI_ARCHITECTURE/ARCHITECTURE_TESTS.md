# ARCHITECTURE TESTS

Status: PROPOSED (Group 4, reviewed PASS 2026-09-21; harness construction HELD for Phase 8)

Modul sinirlari, dependency yonleri, forbidden access ve benzeri kurallarin otomatik testlerle nasil enforce edilecegi burada tasarlanir.

Designed (not built) test families with an explicit detection map — Detection verbatim → Test family →
gate signal: orphans, broken links, forbidden dependencies, cycles, ownerless public contracts, untested
critical behavior, stale context packs, plus identity collisions (duplicate slug/type rejected at gate).
Group 4 consumes open-link labels
(MISSING/UNOWNED/BLOCKED/CONFLICT/UNVERIFIED) and gap-scan outputs; it does not design simulation.

Conformance-test ID + evidence-link shape (field names only, no mechanism): test ID, contract ID+version,
subject digest, result, evidence links, gate verdict, reviewer, timestamp.

Guardrail: no harness/CI implementation, no linter/runner/vendor choice, no coverage-%/timeout numbers,
no account/key/purchase/code. Rule→enforcing-gate mapping lives in `RULES/README.md` (per-task review / release gate / bootstrap gate); these tests invoke it, never duplicate it.
