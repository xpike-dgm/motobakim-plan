# CHANGE CONTROL

Status: PROPOSED (Group 5, review loop closed PASS 2026-09-21; re-validation invoked by this doc, defined in Group 4)

All architecture/ADR/contract/scope changes use Protocol Steps 4–5 owner approval (touchpoint 1 options incl.
keep-old; touchpoint 2 apply-only-on-explicit-approval); reviewer = Step 6 different-chat verifier only; push
only on explicit authorization. Seams to `OWNER_STATUS_AND_ESCALATION.md`.

Impact analysis executes Protocol Step 2 by reference and produces its 6 outputs (nodes, edges incl.
depends_on/used_by, UNVERIFIED-inclusive list, counts, term checklist, vocabulary-mapped BLOCKED states).
Manual search now, graph query post-Phase-8; no harness/CI (Group-4 auto-HELD).

Capture/mark/apply quote Protocol Steps 1 (verbatim quote+date+CHANGELOG+PROPOSED note, no
interpretation/overwrite), 3 (BLOCKED awaiting re-scope, SUPERSEDED only as candidate) and 5 (SUPERSEDED with
full old text + re-scope→REVIEW only after approval). Two-stage status rule. Cites ADR-015 §3
supersedes-chain + RULES R-010.

Emergency follows the fast-track sentence (same-cycle Steps 4–6 mandatory, retrospective included).
Step 6 independent verification (PASS/findings→Step 2) is separate from Group-4 re-validation
(VALIDATION_STRATEGY + CLOSURE MATRIX + R-013/R-014 by reference, never redefined).

Guardrail: no tool/vendor/CI/harness selection, no numeric windows, no account/key/purchase/code/deployment;
destructive-change higher assurance means Group-4 tier re-invocation only; owner approval only per
Protocol Steps 4–5 and DEC-0030.
