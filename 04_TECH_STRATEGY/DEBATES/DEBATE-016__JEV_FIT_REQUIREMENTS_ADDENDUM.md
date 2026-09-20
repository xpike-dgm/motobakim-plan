# DEBATE-016 — Jev Fit Research Addendum

Status: `COMPLETE ADDENDUM / REVIEW-010 PASS / KEEP AS OPTIONAL LATER / NO JEV ADOPTION`

## Why This Addendum Exists

Before the owner approves the pending DEBATE-016 AI/LLM working direction, a newly released AI product named **Jev**
(TypeSafe AI, early access announced 2026-09-15) must be evaluated for Kavriva-specific fit.

This addendum does not reopen the already-reviewed DEBATE-016 authority boundaries. It asks a narrower question:

> Could Jev add meaningful value inside Kavriva's bounded AI assistance architecture, where exactly could it be used,
> where must it not be used, and is the benefit large enough to justify a new provider dependency?

No provider/model/plan winner or adoption decision is authorized.

## Plain-Language Model Hypothesis

Jev is not primarily a chat/text-generation model. TypeSafe positions it as a machine-facing decision model:
unstructured/structured state in, pre-defined typed choices/scores/yes-no-like decisions plus probabilities/confidence out.

That makes it potentially relevant to Kavriva for **routing, classification, triage, scoring and escalation** rather
than for writing explanations or becoming product authority.

The research must independently verify this framing and separate TypeSafe marketing claims from contractually or
technically supported facts.

## Candidate Kavriva Uses To Test

Evaluate each candidate as `GOOD FIT`, `CONDITIONAL`, `POOR FIT` or `HELD`, with evidence and a non-AI fallback.

1. **AI Usta intent routing**
   - classify a user request into known-task, symptom-first, clarification-needed, unsupported/other;
   - Jev may propose the route but may not establish fit/readiness/safety.

2. **Ambiguity / escalation scoring**
   - detect whether available evidence is too uncertain for normal AI assistance;
   - low confidence may trigger HOLD/escalation, but Jev confidence is not itself a safety proof.

3. **Symptom / task classification**
   - map natural-language symptoms/tasks into a controlled taxonomy;
   - may support retrieval but cannot produce final diagnosis or physical-action authority.

4. **Approved-content retrieval/ranking support**
   - score which approved guide/category is most relevant among already-eligible candidates;
   - cannot create source verification or override deterministic eligibility.

5. **Internal Operations triage**
   - classify drafts/reports/incidents/content into queues or review priorities;
   - cannot approve/publish/recall/suspend or grant privilege.

6. **Community/content moderation assistance**
   - flag likely spam/abuse/risk categories for review;
   - cannot be sole removal/ban/publication authority.

7. **Project/company AI workflow routing**
   - route a task to research/review/tool categories or decide whether a human/independent reviewer is required;
   - cannot self-PASS or authorize merge/release/deployment.

8. **Tool-selection proposal**
   - choose among a pre-approved, read-only or otherwise bounded tool list;
   - actual authorization/execution policy remains deterministic and external.

9. **Fallback / model-divergence judge**
   - score whether two AI outputs materially disagree;
   - cannot decide which high-impact output is correct; divergence must still HOLD.

10. **Cost-aware model routing**
    - classify low-risk tasks into cheap vs expensive model paths;
    - cannot route high-impact safety/authority decisions around required review.

## Explicit No-Go / Authority Boundaries

Jev must not become sole authority for:
- motorcycle fit/applicability;
- readiness/safety gate;
- definitive high-risk diagnosis;
- physical actions outside approved guides;
- canonical technical truth/specification;
- source/provenance verification;
- publish/recall/suspension;
- privileged role/grant/policy;
- protected audit truth;
- release/signing/deployment;
- legal/privacy conclusion;
- billing/purchase;
- deletion/retention authority;
- high-impact self-review/PASS.

A typed answer, probability or confidence score does not override these boundaries.

## Mandatory Questions

Research must answer:

### Product / capability
- What exactly are Jev's supported input/output primitives?
- Choice / Score / Noul or equivalent: current limits and semantics.
- Does it generate text? Does it support images/audio/video?
- Context/input limits, question count/choice limits, batching/parallel behavior.
- Probability vs confidence semantics.
- Is behavior deterministic?
- Version pinning/model identifiers and lifecycle/deprecation behavior.
- Rate limits, quotas, service region and outage/status behavior.

### Accuracy / calibration
- What does TypeSafe actually prove for calibration?
- What do public evals measure and what are their limitations?
- Does "zero hallucinations" mean zero wrong decisions, or only constrained/type-safe outputs?
- How should Kavriva set abstain/HOLD thresholds?
- Can confidence be trusted without Kavriva-specific calibration/evals?

### Privacy / data
- Training use of Customer Data.
- Telemetry rights and whether Input/Output can contribute to telemetry.
- Retention/logging and deletion/export behavior.
- DPA, subprocessors, international transfers, residency.
- Sensitive free text / symptom data / identifiers.
- Whether any zero-retention or enterprise privacy option exists and eligibility.

### Commercial / lifecycle
- Early-access status.
- Current pricing and whether TypeSafe itself flags sustainability/subsidy uncertainty.
- Credits/billing behavior and what happens at zero balance.
- API compatibility/update commitments.
- SLA/support/status page.
- Company/vendor concentration risk.
- Export/clean exit and whether a substitute can be implemented with deterministic code or another model.

### Architecture
- Does Jev reduce or increase complexity versus:
  1. deterministic rules;
  2. a normal managed LLM with structured output;
  3. the proposed Kavriva-owned AI boundary?
- Which tasks are worth a separate Jev dependency?
- Which tasks should remain plain deterministic code because the answer space is already fixed?
- Which tasks still require a generative LLM because explanation/context creation is needed?

## Mandatory Comparative Matrix

For each of the 10 candidate uses compare:
- deterministic code/rules;
- normal managed LLM structured-output path;
- Jev;
- hybrid: LLM writes/understands, Jev scores/routes, deterministic code authorizes/acts.

Fields:
- user value;
- latency;
- expected cost;
- correctness/eval burden;
- privacy exposure;
- authority risk;
- provider dependency;
- fallback behavior;
- clean-exit difficulty;
- first-release necessity;
- recommendation status: GOOD FIT / CONDITIONAL / POOR FIT / HELD.

No option may be declared a winner without evidence.

## Failure Walkthrough

At minimum analyze:
1. Jev confidently selects the wrong route.
2. Jev returns low confidence.
3. Jev disagrees with canonical state.
4. Jev disagrees with a generative LLM.
5. Jev's probability changes after a model update.
6. TypeSafe API outage.
7. Rate/credit/billing exhaustion.
8. Input contains personal/sensitive symptom data.
9. Indirect malicious text tries to influence routing/classification.
10. Classification taxonomy changes and old decisions become incompatible.
11. A Jev-specific workflow must be replaced with deterministic code or another provider.
12. Nontechnical owner receives a Jev-related incident.

For every case state:
- expected safe state;
- whether Jev is advisory or decision-driving;
- deterministic guard;
- evidence;
- recovery owner;
- next action;
- privacy/cost impact;
- exit impact;
- HELD gaps.

## Official / Primary Sources Required

Use current first-party sources wherever available:
- TypeSafe AI official launch / Jev announcement;
- TypeSafe official docs;
- TypeSafe official pricing;
- TypeSafe Master Customer Agreement;
- TypeSafe DPA / privacy / trust/subprocessor/security materials;
- TypeSafe status/support/lifecycle docs;
- TypeSafe official workflow eval methodology and caveats.

Third-party launch articles, directories and community demos may be used only for discovery or clearly labelled external
experience; they cannot establish production suitability.

## Key Claims That Must Be Challenged

- "zero hallucinations";
- "calibrated probabilities";
- "20–200x faster";
- "40–400x cheaper";
- "$0.042/M input tokens";
- output tokens free;
- one-call parallel decisions;
- long-term pricing sustainability;
- claim that structured decisions are more reliable than LLM structured outputs.

Provider-reported benchmark claims must be presented as provider-reported unless independently reproduced.

## Required Deliverable

Drive:
- `CTX-P4-017 — JEV KAVRIVA FIT AND DECISION-LAYER RESEARCH`
- `TASK-005 — DEBATE-016 JEV FIT PRIMARY RESEARCH`
- output: `DEBATE-016__JEV_FIT_PRIMARY_RESEARCH`
- handoff: `HANDOFF-TASK-005`

Report must end with a simple owner-facing answer:
- **Use now**, **Keep as optional later**, **Do not use**, or **HELD pending evidence**;
- if use is proposed, list exact Kavriva locations and exact forbidden locations;
- no provider adoption/purchase is authorized by the report.

## Boundary

No TypeSafe account, waitlist enrollment, API key, credit purchase, trial, payment, live API call, benchmark execution,
code, pseudocode, integration, production workflow, final legal/privacy conclusion, final budget, provider selection,
Phase-5 ADR or Gate 4 -> 5 transition.

This addendum pauses owner approval of the DEBATE-016 manager synthesis until the Jev evidence is reviewed.
