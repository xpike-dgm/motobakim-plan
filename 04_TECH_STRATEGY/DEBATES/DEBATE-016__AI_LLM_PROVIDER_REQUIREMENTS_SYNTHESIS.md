# DEBATE-016 — AI / LLM / Provider Strategy Requirements Synthesis

Status: `ACTIVE / PRIMARY RESEARCH READY / NO PROVIDER OR MODEL WINNER`

## Decision Question

Kavriva hangi AI/LLM operating model'ini Phase 4'ten sonraki mimariye taşımalı; consumer AI Usta, Internal Operations
AI assistance ve AI-operated project/company workflows hangi görevlerde model kullanmalı, hangi authority'ler modele
asla bırakılmamalı ve privacy/cost/fallback/provider-exit nasıl bounded tutulmalı?

Bu debate bir model/provider/plan seçmez. Amaç görev sınırı, provider bağımlılığı, data handling, failure behavior,
safe TCO, model/version lifecycle, fallback ve clean-room exit için equal-evidence çalışma yönü üretmektir.

## Canonical Existing Authority

Existing approved directions remain binding:

- `DEC-0018`: AI Usta root bir technical-answer/chat-home değil, controlled intent router / guided assistance entry'dir.
  Known-task ve symptom-first yolları downstream fit/readiness/safety/trust authority'lerine gider.
- Natural language task/symptom capture, clarification ve observable-evidence capture için kullanılabilir; unsupported
  torque/spec/value, definitive diagnosis, fit guessing, readiness/safety bypass veya approved-guide dışı physical
  instruction authority olamaz.
- AI Usta output'u verified guide/source/provenance değildir.
- `DEC-0028`–`DEC-0029`: project AI-native / AI-operated'dır; high-impact AI work separate implementation/review/
  validation evidence ister ve AI output self-proving değildir.
- AI legal identity, store ownership, qualified safety/domain attestation veya genuinely human/organizational authority
  impersonate edemez.
- `DEC-0030`: limited-budget solo ownership; paid AI subscription/API/model hosting silently assumed edilemez.
- `DB-AC-021`: AI output attributable proposal'dır; hostile input policy/tool/verification authority yaratamaz.
- Analytics, CMS, build/release, data, identity and runtime decisions remain separate authority boundaries.

## New Strategy Question

Register as:

`TSQ-018 — AI / LLM / Provider Operating Strategy`

Question:
Which AI/LLM task boundary and provider/model operating strategy can support AI Usta, bounded Internal Operations
assistance and AI-operated project workflows without turning model output into product truth, safety authority,
privileged authorization, release approval or protected audit?

## AI Usage Planes — Must Remain Separate

Research must explicitly separate:

1. **Consumer AI Usta assistance plane**
   - task/symptom natural-language understanding;
   - clarification;
   - evidence organization/summarization;
   - bounded explanation grounded in approved/canonical material;
   - optional future multimodal interpretation only inside explicit safety/privacy gates.

2. **Internal Operations AI assistance plane**
   - drafting, summarization, classification, candidate proposals, evidence triage and operator assistance;
   - never approval, publish, recall/suspension, privileged authorization, protected audit or canonical technical truth.

3. **Project / company AI-operated delivery plane**
   - research, planning, code/document production later when separately authorized, review preparation, testing assistance,
     repository/file operations under explicit task contracts;
   - high-impact work requires independent review/validation and cannot self-PASS.

4. **Non-AI authority plane**
   - canonical product/content/data truth;
   - fit/readiness/safety gate;
   - verified source/provenance;
   - deterministic policy/authorization;
   - human/organizational approval where required;
   - release approval and emergency negative authority;
   - protected audit/security evidence;
   - signing/store/legal identity authority.

One provider may support multiple planes, but that is not an architectural requirement and does not grant authority.

## AI Tasks — Candidate Allow / Deny Boundary

Research must test and refine the following direction.

Potentially allowed when grounded and bounded:
- intent classification;
- clarification questions;
- symptom/task language normalization;
- approved-content summarization/explanation;
- retrieval query generation;
- structured candidate extraction;
- evidence comparison/proposal generation;
- non-authoritative translation/localization draft;
- Internal Ops draft/classification assistance;
- project research/drafting/review assistance;
- optional image interpretation as evidence proposal, never final verification.

Must not be delegated as sole authority:
- unsupported technical specification/value;
- final fit/applicability decision;
- readiness/safety bypass;
- definitive high-risk diagnosis without required evidence;
- physical action outside approved guide/state machine;
- guide/source verification;
- content approval/publish/recall;
- privileged role/grant/policy decision;
- protected audit entry as model-authored truth;
- release/signing/deployment approval;
- legal/privacy conclusion;
- billing/purchase approval;
- deletion/retention authority without deterministic policy;
- self-review/self-PASS for high-impact project work.

## Four Equal Provider Operating-Model Families

Research must compare all four families to the same evidence standard.

### Family A — Single managed model provider behind a Kavriva AI boundary

One external managed model/API provider is primary; Kavriva owns prompts/contracts, retrieval, authority checks,
telemetry and provider adapter.

Current candidate mechanisms should include at least two of:
- OpenAI API;
- Anthropic API;
- Google Gemini API.

Single-provider simplicity must be balanced against outage, pricing, lifecycle and exit dependency.

### Family B — Multi-provider direct APIs behind a Kavriva router

Kavriva owns one normalized AI boundary and can route/fallback between two or more direct managed providers.

At least two concrete current compositions/mechanisms must be analyzed. Candidate reuse from Family A is allowed because
the comparison is architecture-level; it must not be counted as fake provider breadth.

Research must test semantic portability limits: prompts, tool schemas, structured output, safety behavior, context,
vision, caching and model-version behavior are not assumed interchangeable.

### Family C — Cloud AI platform / model broker

A cloud AI platform/broker provides model access, IAM, region/governance/observability and potentially multiple model
families.

At least two current mechanisms among:
- AWS Bedrock;
- Google Vertex AI;
- Microsoft Azure AI Foundry / Azure model platform.

Do not assume broker access eliminates model/provider lock-in or gives equivalent behavior across models.

### Family D — Split/hybrid task-tiered architecture

Deterministic/canonical systems remain primary; managed models are used only for bounded probabilistic tasks; optional
open-weight/self-hostable/local inference may be used where privacy, offline, fallback or cost evidence justifies it.

Reference mechanisms may include:
- managed provider + provider-neutral Kavriva gateway + deterministic retrieval/policy;
- managed provider + vLLM or Hugging Face TGI/open-weight fallback for explicitly bounded tasks.

Candidate/provider reuse is allowed only to isolate the hybrid architecture effect and must not be treated as fake
breadth.

## Required Research Dimensions

For every family/candidate, research at least:

### Capability and task fit
- text, vision/multimodal, structured outputs and tool/function calling;
- retrieval/RAG support and citations/source binding where available;
- model/context/output limits relevant to the proposed tasks;
- deterministic schema validation and retry/repair boundaries;
- latency/streaming and mobile-facing interaction implications;
- whether model behavior can be version-pinned/snapshotted or only named by moving aliases.

### Authority and safety
- prompt/indirect prompt injection handling;
- tool permissions and least privilege;
- untrusted retrieved/community/web content isolation;
- model output attribution and non-authoritative presentation;
- deterministic enforcement outside the model;
- high-risk symptom/task safe hold and unresolved outcome;
- prohibition on self-approval/self-PASS and privileged authority.

### Privacy / data handling
- API data use for training;
- retention/default logging and opt-out/zero-retention options where officially available;
- region/residency and subprocessors where relevant;
- anonymous/account-light identifiers;
- symptom/free-text/image/media handling;
- private history and Internal Ops drafts;
- secrets/tokens/protected audit exclusion;
- deletion/export implications;
- model/provider telemetry and abuse-monitoring exceptions.

Jurisdiction-specific legal conclusions remain HELD unless separately authorized.

### Provider/model lifecycle
- model deprecation and version retirement;
- aliases versus immutable/snapshot identifiers;
- SDK/API lifecycle;
- rate limits/quota;
- service status/outage;
- safety-policy/model-behavior drift;
- fallback behavior;
- eval/change-detection requirements.

### Cost / TCO
- current official input/output token pricing;
- cached input/batch discounts where relevant;
- image/vision, embeddings, web/search/tool charges where relevant;
- provisioned capacity/hosting cost for broker/open-weight paths;
- storage/vector/observability adjuncts;
- support/SLA;
- abuse/retry/long-context cost;
- engineering/operator/evaluation cost;
- provider switch/dual-run cost;
- tax/currency uncertainty.

Use normalized synthetic monthly text inference bundles:
- Small: 1M input + 0.25M output tokens;
- Medium: 10M input + 2.5M output tokens;
- Large: 100M input + 25M output tokens.

These are comparison fixtures, not traffic forecasts. Vision/search/embedding/tool charges must be shown separately rather
than hidden in the text subtotal.

Where TRY is shown, use a current official/primary FX source and label it illustrative. The existing non-store planning
ceiling is context only, not acceptance or purchase authority.

### Portability / clean exit
- prompt/system-instruction portability;
- structured-output/tool-schema portability;
- embeddings/vector portability;
- retrieval corpus and source citations;
- conversation/memory state;
- eval datasets and acceptance fixtures;
- safety classifiers/policies;
- model-specific features;
- provider logs/telemetry;
- account/project/IAM configuration;
- open-weight model/license/runtime dependencies;
- clean-room replacement evidence.

Raw prompt export or API compatibility alone is not clean-exit proof.

## Mandatory Failure Scenarios

Apply all four families to all 16 scenarios:

1. Known-task user asks for maintenance help while an approved canonical guide exists.
2. Symptom-first interaction is ambiguous or high-risk and evidence is insufficient.
3. Model answer conflicts with canonical guide/provenance/fit/readiness/safety state.
4. Retrieved community/web/document content contains indirect prompt injection or malicious instructions.
5. Anonymous/account-light user submits free text or an image containing personal/sensitive information.
6. Network/model/provider outage occurs during consumer AI assistance.
7. Rate limit, quota or billing hold blocks the model path.
8. Model/API version is deprecated or behavior materially changes after an upgrade/alias change.
9. Structured output/tool call is invalid, incomplete or requests a tool outside its permission boundary.
10. Internal/project AI attempts privileged action, secret access, self-approval or policy bypass.
11. Long context/stale conversation/wrong-motorcycle context risks contamination or truncation.
12. User requests deletion/export while provider logs, prompts, embeddings or derived state may exist.
13. Token/vision/search/tool usage spikes unexpectedly or abuse drives cost above the planning envelope.
14. Primary model/provider must be replaced cleanly.
15. Fallback model/provider returns materially divergent output for the same high-impact input.
16. Nontechnical owner receives an AI/provider incident affecting consumer or internal/company workflows.

For every scenario/family row, state all eight fields explicitly and substantively:
- expected state;
- safe hold;
- evidence;
- recovery owner;
- next action;
- security/privacy/authority impact;
- cost/latency impact;
- exit/fallback impact.

Field labels alone are not enough. Unknown or Kavriva-specific unproven behavior remains `HELD`.

## Required Official / Primary Evidence

Prefer current official/primary sources:

- OpenAI API/model/pricing/data-controls/retention/security/lifecycle/tool/structured-output documentation;
- Anthropic API/model/pricing/privacy/data-usage/lifecycle/tool-use documentation;
- Google Gemini API and Google Vertex AI official model/pricing/data-governance/lifecycle docs;
- AWS Bedrock official model/pricing/security/data-protection/lifecycle docs;
- Microsoft Azure AI Foundry / Azure AI official pricing/model-governance/security/lifecycle docs;
- vLLM and Hugging Face TGI official project documentation;
- official model-provider documentation for open-weight models considered;
- NIST/other official public-sector AI risk/security guidance where useful;
- provider status pages and deprecation notices.

Time-sensitive model names, context limits, prices, retention behavior, data-use policies, regions and deprecation claims
must carry an access date.

Provider marketing claims such as "safe", "private", "enterprise", "agentic", "reasoning", "state-of-the-art",
"zero data retention" or "model agnostic" are not acceptance evidence by themselves.

## Required Deliverable

Drive package:
- `CTX-P4-016 — AI LLM PROVIDER AND MODEL STRATEGY`
- `TASK-004 — DEBATE-016 AI LLM PROVIDER PRIMARY RESEARCH`

Research output:
- `DEBATE-016__AI_LLM_PROVIDER_PRIMARY_RESEARCH`
- `HANDOFF-TASK-004`

Research report must include:
- nontechnical executive summary;
- AI usage / non-AI authority matrix;
- plane separation for consumer, Internal Ops, project/company and deterministic authority;
- equal four-family/candidate matrix;
- current official-primary source ledger;
- data/privacy handling matrix;
- model/provider lifecycle and deprecation matrix;
- tool/agent permission and prompt-injection boundary;
- 16 × 4 = 64 failure rows with all eight required fields;
- normalized Small/Medium/Large text-token cost comparison;
- separate vision/search/embedding/tool/hosting/support TCO adjuncts;
- latency/rate-limit/outage analysis;
- eval/change-detection strategy;
- fallback and model-divergence analysis;
- clean-room provider/model replacement analysis;
- unresolved/HELD evidence;
- recommended next evidence;
- mandatory / deferrable / optional / scale-triggered first-release AI capabilities.

At most one conditional Phase-4 architecture/operating-model direction may be proposed. It must not select a provider,
model, plan or purchase winner.

## Boundary

No code, pseudocode, prompt implementation, production system prompt, tool schema, agent workflow, API key, provider
account, trial, plan, purchase, payment, model download, self-host deployment, vector database setup, fine-tune,
store/deployment action, final legal/privacy conclusion, final budget commitment, Phase-5 ADR or Gate 4 -> 5 transition
is authorized.

Research PASS would mean only that the evidence package is sufficient for manager synthesis. It would not prove model
quality, production safety, real latency, real cost, autonomous operation or provider readiness.
