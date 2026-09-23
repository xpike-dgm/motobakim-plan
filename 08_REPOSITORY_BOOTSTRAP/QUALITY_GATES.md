# QUALITY GATES

Status: PROPOSED (OUT-1 B-06 closure draft 2026-09-23, declare-and-review PASS 2026-09-23; install record `Q-GATE-001`)

Binding sources (single truth, not copied): Step-4 `CI_DRAFT/CI_PLAN.md` (events, fail conditions, merge gates);
Step-3 `VALIDATION_DRAFT/VALIDATION_COMMANDS.md` (8 commands × tiers) + `ARCHITECTURE_TEST_SUITE.md` (signals
FAIL / WARN-then-FAIL / REJECT); `RULES/README.md` (rule→gate mapping); `TASK_EXECUTION_PROTOCOL.md`
(different-chat review). This file binds them into the single authoritative gate record; it redefines nothing.

## The gates (binding)

1. Per-task gate: the task's tier check set (T1/T2/T3) green on latest commit + different-chat review (R-007);
   T3 additionally requires mandatory independent review with agreement≠approval recorded.
2. Merge gate (`main`): all required checks green + review complete + scope check (manifest-declared seams only) +
   conformance evidence attached for T2/T3; no direct pushes (enforced by ruleset `main-gates` on Pro).
3. Release gate: E6 promotion contract + authority separation + seal/provenance; rollback is lethal-error route only.
4. Bootstrap gate (closed): Phase-8 checklist COMPLETE + proof task verified (E-PR-001 VERIFIED).
5. Evidence rule: every gate decision attaches conformance-shaped records (`vault/EVIDENCE/`); missing evidence = block.

## Non-goals

No new rule authored here; product-code CI (lint/typecheck/unit) arrives with Development, not here.
