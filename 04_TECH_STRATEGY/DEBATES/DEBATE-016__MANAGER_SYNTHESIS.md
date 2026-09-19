# DEBATE-016 — AI / LLM / Provider Strategy Manager Synthesis

Status: `USER DECISION PENDING / PHASE-4 WORKING-DIRECTION PROPOSAL / NO PROVIDER OR MODEL WINNER`

## Nontechnical Decision Proposal

Kavriva should keep **deterministic/canonical systems as the authority plane** and use AI/LLMs only as bounded
probabilistic assistance behind a Kavriva-owned boundary.

The practical Phase-4 direction is a **Family-D-shaped authority split**:
- AI may help understand language, clarify intent, summarize approved material, organize evidence, draft, classify and
  propose;
- AI may not become canonical technical truth, motorcycle fit/readiness/safety authority, publication/recall authority,
  privileged authorization, protected audit truth, release/signing/deployment approval, legal/privacy authority,
  billing/purchase authority or high-impact self-review authority;
- a single managed model/provider may later be operationally simplest for an initial bounded AI path, but no provider,
  model or plan is selected here;
- multi-provider routing/failover is added only if measured availability/exit benefit exceeds added divergence, privacy,
  evaluation and cost burden;
- open-weight/local/self-host paths remain optional until runtime security, license, hardware/TCO, recovery and eval
  evidence justify them.

This direction preserves AI Usta as a controlled assistance surface rather than a free-form technical authority.

## Why This Direction

The reviewed research supports five architecture-level conclusions:

1. **Authority separation is more important than model choice.** Structured output, function calling, guardrails,
   RAG/grounding and agentic features improve interface discipline but do not make model output authoritative.
2. **A single provider is simpler but correlated.** One managed provider has the smallest initial integration/operations
   surface, but outage, quota, billing, retention, lifecycle and model-drift risk stay correlated.
3. **Multi-provider is not automatically safer.** Providers differ in context, tools, safety behavior, retention,
   lifecycle and output semantics. High-impact divergence must HOLD rather than auto-route/majority-vote.
4. **Cloud brokers do not remove lock-in.** AWS/Google/Microsoft platform IAM and governance can help, but model/platform
   lifecycle, marketplace/region, retention and migration dependencies remain.
5. **Local/open-weight is not automatically private, cheap or resilient.** Security hardening, logs/backups/egress,
   licenses, compute, uptime, operator recovery and eval burden must be proven.

## Binding AI / Non-AI Boundary Proposed

### AI may be used for bounded assistance

- intent/task/symptom language normalization;
- clarification questions;
- retrieval-query generation;
- approved/canonical content summarization and explanation;
- structured candidate extraction;
- evidence organization/comparison and proposal generation;
- drafting, translation/localization drafts and Internal Operations classification assistance;
- project/company research, drafting and review preparation under explicit task contracts;
- future image/vision interpretation only as an evidence proposal, not final verification.

### AI must not be the sole authority for

- unsupported torque/spec/value or canonical technical truth;
- final motorcycle fit/applicability;
- readiness or safety gate;
- definitive high-risk diagnosis without required evidence;
- physical action outside an approved guide/state machine;
- source/guide verification;
- approve/publish/recall/suspension;
- privileged role/grant/policy changes;
- protected audit truth;
- release/signing/deployment approval;
- legal/privacy conclusions;
- billing/purchase approval;
- deletion/retention authority without deterministic policy;
- high-impact self-review/self-PASS.

## Plane Separation Proposed

1. **Consumer AI Usta assistance plane**
   - controlled natural-language assistance and evidence organization;
   - source-bound where approved material exists;
   - high-risk/ambiguous cases safe-hold rather than invent certainty.

2. **Internal Operations AI assistance plane**
   - drafting, classification, summarization, evidence triage and proposals;
   - no approval/publish/recall/privileged/protected-audit authority.

3. **Project/company AI-operated delivery plane**
   - task-bounded research, planning, drafting, and later separately authorized implementation/test assistance;
   - high-impact work requires independent review and cannot self-PASS.

4. **Non-AI deterministic authority plane**
   - canonical data/content truth;
   - fit/readiness/safety state;
   - verified provenance;
   - IAM/policy/authorization;
   - release approval and emergency negative authority;
   - protected audit/security evidence;
   - signing/store/legal identity and purchase authority.

## First-Release Capability Classification

### Mandatory if any AI path is enabled

- deterministic authority and approved-source boundary outside the model;
- safe-hold behavior for ambiguity, high-risk inputs and provider/model divergence;
- current-context isolation, including motorcycle/task context;
- semantic validation after structured output;
- least-privilege tool policy, or no write-capable AI tools;
- direct and indirect prompt-injection controls for user, retrieval, web, documents/media and tool results;
- privacy/data minimization by data class;
- provider/model/version identifier logging;
- evaluation/change-detection gate before model/version changes;
- bounded retry/rate-limit/outage handling;
- spend/cost observability;
- non-AI continuation for critical product journeys;
- independent review for high-impact project/company AI work.

### Deferrable

- consumer image/vision interpretation;
- provider-native web search/grounding;
- persistent AI memory/history;
- server-side agent tools;
- multi-provider router;
- vector retrieval where approved-source deterministic lookup is sufficient;
- model-specific prompt caching;
- automated model migration.

### Optional

- open-weight/local/self-host inference;
- hot multi-provider failover;
- fine-tuning;
- autonomous multi-agent workflows;
- persistent consumer personalization.

Optional does not mean safe by default; activation still requires the authority/privacy/eval gates above.

### Scale-triggered

- provisioned/reserved throughput;
- dedicated inference capacity;
- active-active regions;
- hot second-provider standby;
- enterprise retention/ZDR/residency contracting where required;
- large vector infrastructure;
- automated dual-run/shadow evaluation;
- dedicated 24/7 incident support.

## Privacy / Data Direction

Kavriva should treat provider privacy claims as feature-specific rather than provider-wide.

The operating boundary should require:
- explicit data-class mapping before a feature can send data to a model;
- no casual inclusion of secrets, signing keys, unrestricted service credentials or protected-audit evidence;
- separate treatment for public approved content, motorcycle context, account-light identifiers, symptom/free-text/image,
  private history, Internal Ops drafts and project/company context;
- feature-level verification of training use, retention/logging, abuse-monitoring exceptions, files, caches, sessions,
  embeddings/vector stores, search/tool traces, residency and deletion/export behavior;
- jurisdiction-specific legal/privacy conclusions remain separate and HELD until specifically authorized.

“No training” must never be interpreted as “no retention,” and platform/model/provider paths must not be assumed to share
one privacy regime.

## Prompt Injection / Tool Direction

Untrusted content includes not only user prompts but also retrieval results, community/web content, uploaded documents or
media and tool outputs.

The proposed rule is:
- retrieved/tool content is data, never policy;
- tool arguments are untrusted model proposals;
- Kavriva-owned allow-lists, state preconditions, authorization and consequence-bearing confirmations sit outside AI;
- provider tool/function/agent mechanisms never grant privilege by themselves;
- invalid or out-of-bound structured output/tool calls fail closed.

## Fallback / Model Change Direction

Provider/model fallback is not majority voting.

For high-impact input:
- materially divergent fallback output -> HOLD;
- re-check canonical source/state;
- run the relevant eval fixture;
- continue only when deterministic acceptance criteria are met.

Every model/provider/version change should be treated as a revalidation event when it can affect behavior, context,
structured outputs, tools, safety or privacy.

## Cost / TCO Interpretation

The reviewed token-price fixtures show that raw text inference can be inexpensive at small volumes, but **token price is
not safe total cost**.

Separate budget lines remain necessary for:
- vision/images;
- embeddings/vector storage/query/re-indexing;
- web/search/grounding/tools;
- storage and observability;
- prompt/context caching;
- provisioned or self-host capacity;
- support/SLA;
- retries/abuse;
- evaluation/operator labor;
- provider switch and dual-run.

The research also shows current model prices and residency modifiers can change. Therefore no current headline token rate
is sufficient to approve a provider or 12/24-month budget.

## Clean-Room Exit Direction

Provider replacement must preserve or reconstruct more than prompts.

Exit evidence must cover:
- system/prompt instructions;
- structured-output/tool schemas;
- approved retrieval corpus and source citations;
- embeddings/vector state where used;
- conversation/memory state where used;
- evaluation datasets and acceptance fixtures;
- safety/policy classifiers and deterministic rules;
- provider-specific features;
- logs/telemetry;
- IAM/project configuration;
- open-weight runtime/model/license dependencies where applicable.

An OpenAI-compatible API or exported prompt text alone is not clean-exit proof.

## HELD Evidence After Research

The following remain HELD and are not silently approved by this working direction:
- provider/model/plan winner, accounts, trials and purchases;
- final jurisdiction-specific privacy/legal conclusion;
- exact Kavriva eligibility for ZDR/modified retention, residency, subprocessors and enterprise controls;
- real production traffic, concurrency, latency, context-size distribution, media/search/tool volume and retry rates;
- exact broker/platform deployment pricing;
- self-host/open-weight hardware/TCO/security/operations;
- legal suitability of specific open-weight licenses;
- production prompts, router, tool schemas, agent workflow, vector store and runtime integration;
- real model quality/safety/latency eval PASS;
- clean-room replacement rehearsal;
- deletion/export proof;
- final recurring AI budget;
- persistent account-light consumer memory/history.

## Research / Review History

- TASK-004 compared four provider operating-model families with equal evidence standards.
- The failure walkthrough contains 16 mandatory scenarios × four families = 64 rows with eight required fields.
- REVIEW-007 returned CHANGES_REQUESTED with M-1/M-2/M-3 and Minor m-1.
- REVIEW-007 remediation rewrote all 64 Evidence fields; revision comparison showed zero changes to the other seven fields.
- REVIEW-008 closed M-2/M-3/m-1 and left residual M-1 in seven Evidence rows only.
- The residual remediation changed exactly those seven Evidence fields and nothing else in the mandatory row set or
  Sections 6/8/9/12.
- REVIEW-009 returned PASS with no Critical, Major or Minor findings.
- TASK-004 is DONE after manager readback.

## Owner Decision Requested

Approve or reject this Phase-4 working direction:

> Keep deterministic/canonical Kavriva systems as the authority plane; permit managed AI only for bounded probabilistic
> assistance behind a Kavriva-owned boundary; keep high-risk ambiguity and provider/model divergence on HOLD; treat one
> managed provider as a possible simple implementation shape but do not select one now; defer multi-provider and
> open-weight/local complexity until measured availability, privacy, exit, TCO and evaluation evidence justify it.

## Boundary

This proposal does not approve a provider, model, plan, API key, account, trial, purchase, production prompt, tool schema,
agent workflow, model deployment, vector database, fine-tune, legal/privacy conclusion, final budget, Phase-5 ADR or
Gate 4 -> 5 transition.
