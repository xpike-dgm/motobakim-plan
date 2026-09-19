# Next Action — Single Current Work Pointer

Status: `DEBATE-016 / TASK-004 CHANGES_REQUESTED`
Phase: `PHASE 4 — TECHNOLOGY STRATEGY`
Gate: `3 -> 4 PASSED / 4 -> 5 CLOSED`

## Current Topic

`DEBATE-016 — AI / LLM / Provider Strategy`

Independent REVIEW-007 returned `CHANGES_REQUESTED`:
- Critical: none.
- Major M-1: Section 17 Evidence field across all 64 rows collapses to only 12 repeated texts and is not scenario-specific substantive evidence.
- Major M-2: Family-C privacy/data evidence under-specifies Amazon Bedrock retention modes and Microsoft Foundry Claude hosting/data-processing/residency splits.
- Major M-3: Bedrock lifecycle evidence omits the current policy split between models launched on/after 2026-09-07 and earlier legacy-policy models.
- Minor m-1: Safe-TCO arithmetic is correct but must label GPT-5.6 Sol pricing as promotional/time-sensitive and add the conditional Anthropic 1.1× US-only inference multiplier for Claude 4.6+.

Official-source manager spot-check confirmed these current-fact findings.

TASK-004 is now `CHANGES_REQUESTED` in Drive `04_CHANGES_REQUESTED`.

## Immediate Next Manager Action

Dispatch a narrow remediation to the research-producing external AI:
1. Rewrite only the Section-17 `Evidence` field across all 64 rows so every row has scenario-specific and family-specific substantive evidence and explicit HELD gaps.
2. Update Sections 6/8 Family-C privacy evidence and only impacted Family-C rows for Bedrock retention modes and Microsoft Foundry Claude hosting/data-processing differences.
3. Update Sections 6/9 and S08-C for the current/legacy Bedrock lifecycle policy split.
4. Keep Section-12 arithmetic but add the GPT-5.6 Sol promotional-pricing caveat and the conditional Anthropic 1.1× US-only residency multiplier.
5. Preserve the other seven row fields, AI/non-AI authority boundaries, HELD states and conditional Family-D direction unless a newly verified source forces a narrow factual correction.
6. Update HANDOFF-TASK-004 and TASK-004 completion evidence, return TASK-004 to REVIEW / 03_REVIEW and request a fresh independent re-review. No self-PASS.

## Hard Boundaries

- no provider/model/plan winner;
- no code, prompt/tool implementation, agent workflow, API key or integration;
- no provider account, trial, purchase, payment, model deployment, vector DB or fine-tune;
- no final legal/privacy conclusion or budget commitment;
- no Phase-5 ADR and no Gate 4 -> 5 transition.
