# ROLLBACK STRATEGY

Status: PROPOSED (Group 5, review loop closed PASS 2026-09-21)

Rollback references (never redefines) ADR-003 rollback/restore rules and ADR-007 release rules:
rollback-as-new-event to still-trusted compatible artifacts only; restore quarantine with reconciliations;
generations never move backward; no silent discard of valid data; no resurrection of revoked authority.

Task-level safe return = ADR-015 §5 BLOCKED / change-request + Group-3 R-009 (not a new rollback class).
Layering: E6 executes release rollback (T-E6-013/014), E3 enforces restore quarantine and floors
(T-E3-023/026/027); Phase-7 constrains, never operates; E3 restore quarantine stays consistent.
No tool/vendor/CI selection, no numeric windows, no account/key/purchase/code/deployment.

Repo + CI layer (added 2026-09-23, OUT-3 B-34 — under DEC-0062 mandate): red-`main` reverts the offending
SHA (`git revert`, recorded here + CHANGELOG); forward-fix without revert is a violation and is
recorded as such. Incident 2026-09-23 (batch-1 push went red-bypassed and was forward-fixed — VIOLATION
(recorded; cause: secret-scan fix urgency under active bypass; any repeat is a further violation).
Incident 2026-09-23 (digest-guard push went red on CRLF skew and was forward-fixed — VIOLATION (recorded;
cause: normalization gap; a revert would have restored two verified evidence holes, which is mitigation,
not permission — the rule stands strict; any exception model belongs to the pending B-01 governance decision).
