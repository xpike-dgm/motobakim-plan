# Next Action — Single Current Work Pointer

Status: `DEBATE-016 / TASK-004 REVIEW-009 OPEN`
Phase: `PHASE 4 — TECHNOLOGY STRATEGY`
Gate: `3 -> 4 PASSED / 4 -> 5 CLOSED`

## Current Topic

`DEBATE-016 — AI / LLM / Provider Strategy`

REVIEW-008 residual-M-1 remediation has been completed and manager readback verified:
- report revision 8 -> 9 changed exactly seven Evidence fields: S02-A, S02-C, S02-D, S03-A, S03-D, S09-C and S15-D;
- other 57 Evidence fields show zero changes;
- the other seven mandatory row fields show zero changes across all 64 rows;
- Sections 6, 8, 9 and 12 are unchanged;
- undefined `KAVRIVA-CTX/AUI` and generic `OAI/ANTH/GOOG evidence` tokens are absent;
- S09-C now uses current official Amazon Bedrock tool-use and Google Cloud Vertex AI function-calling evidence while preserving Family-C parity HELD;
- S15-D now uses exact defined managed-provider and local/runtime identifiers and preserves managed↔local behavioral parity HELD;
- M-2, M-3 and m-1 remain closed;
- HANDOFF-TASK-004 and TASK-004 completion evidence record the exact seven-row remediation;
- TASK-004 is back to `REVIEW` in Drive `03_REVIEW`;
- no self-PASS was issued.

`REVIEW-009 — TASK-004 REVIEW-008 RESIDUAL M-1 RE-REVIEW` is OPEN in Drive `05_REVIEWS`.

## Immediate Next Manager Action

Dispatch REVIEW-009 to a fresh independent external reviewer.

The re-review must verify exactly seven Evidence changes, zero collateral changes, exact provenance/source integrity in
S02-A/S02-C/S02-D/S03-A/S03-D/S09-C/S15-D, and current official evidence for S09-C. M-2/M-3/m-1 are already closed and
must not be reopened unless the seven-row remediation itself directly regressed them.

Do not close TASK-004 or synthesize DEBATE-016 before the independent verdict.

## Hard Boundaries

- no provider/model/plan winner;
- no code, production prompt/tool schema/agent workflow/API key/integration;
- no provider account, trial, purchase, payment, model deployment, vector DB or fine-tune;
- no final legal/privacy conclusion or budget commitment;
- no Phase-5 ADR and no Gate 4 -> 5 transition.
