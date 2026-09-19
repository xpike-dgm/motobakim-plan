# Next Action — Single Current Work Pointer

Status: `DEBATE-016 / TASK-004 REVIEW-008 OPEN`
Phase: `PHASE 4 — TECHNOLOGY STRATEGY`
Gate: `3 -> 4 PASSED / 4 -> 5 CLOSED`

## Current Topic

`DEBATE-016 — AI / LLM / Provider Strategy`

REVIEW-007 remediation has been completed and manager readback verified:
- Section 17 still contains exactly 64 scenario/family rows;
- all 64 `Evidence` fields changed and now contain 64 distinct values;
- Drive revision 6 -> 8 comparison shows zero changes to the other seven mandatory row fields;
- Sections 6/8 now distinguish Bedrock `none/default/aws_review` retention behavior and Microsoft Foundry Claude Hosted-on-Azure versus Hosted-on-Anthropic data-processing/residency paths;
- Sections 6/9 now distinguish current Bedrock lifecycle for models launched on/after 2026-09-07 from the separate legacy policy for earlier models;
- Section 12 retains the existing arithmetic while adding GPT-5.6 Sol promotional/time-sensitive pricing and the conditional Anthropic 1.1× US-only inference modifier;
- current official-source spot-check supports these remediation facts;
- AI/non-AI authority boundaries, Family-D conditional status and HELD boundaries remain unchanged;
- HANDOFF-TASK-004 and TASK-004 completion evidence record the remediation;
- TASK-004 is back to `REVIEW` in Drive `03_REVIEW`;
- no self-PASS was issued.

`REVIEW-008 — TASK-004 REVIEW-007 REMEDIATION RE-REVIEW` is OPEN in Drive `05_REVIEWS`.

## Immediate Next Manager Action

Dispatch REVIEW-008 to a fresh independent reviewer.

The re-review must inspect all 64 Evidence fields, verify zero regression in the other seven fields, confirm M-2/M-3/m-1
with current official sources, preserve authority/HELD/Family-D boundaries and issue PASS / CHANGES_REQUESTED / BLOCKED.

Do not close TASK-004 or synthesize a DEBATE-016 working direction before the independent verdict.

## Hard Boundaries

- no provider/model/plan winner;
- no code, production prompt/tool schema/agent workflow/API key/integration;
- no provider account, trial, purchase, payment, model deployment, vector DB or fine-tune;
- no final legal/privacy conclusion or budget commitment;
- no Phase-5 ADR and no Gate 4 -> 5 transition.
