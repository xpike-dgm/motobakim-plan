# ADR-014 — AI/LLM Assistance Boundary, Decision Layer and Provider/Model Routing

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-016, user-approved under `DEC-0046`) compared four provider operating-model families plus
a TypeSafe Jev fit addendum through TASK-004/TASK-005 research and independent REVIEW-009/REVIEW-010 PASS
verdicts. Conclusion: cheapest/fastest adequate conversational model by default; AI asks clarification questions;
a Kavriva-owned provider/model-neutral decision layer may propose route/guide candidates; deterministic/canonical
Kavriva systems keep final validation; stronger models only when needed; Jev not adopted now, kept as optional
later. This ADR locks that assistance architecture on top of ADR-001, ADR-004, ADR-006 and ADR-009. It selects no
OpenAI, Anthropic, Google, AWS, Microsoft, TypeSafe/Jev or other provider/model/plan, and authorizes no account,
key, credit, purchase, prompt/tool schema, agent workflow, vector store, fine-tune or integration.

## Decision Drivers

- AI is bounded assistance, never canonical truth, safety authority, publication/recall authority, privileged
  authorization, audit truth, release approval, legal/privacy authority, billing authority or high-impact
  self-review.
- Model cost must follow task need (cheapest adequate first), while cost pressure must never soften safety or
  authority boundaries.
- Provider/model replacement must stay an adapter/configuration plus revalidation exercise, not a product rewrite —
  while honestly acknowledging that tools, schemas, privacy, context and lifecycle still differ.
- Future decision-model options (Jev-like) must remain addable without creating present-day dependency.

## Options Considered

### Option A — Single provider/model everywhere (rejected)

One vendor for conversation, routing, extraction and background AI. Rejected: couples product logic to
provider-specific behavior, surrenders exit leverage, and lets one outage or price change halt all AI assistance.

### Option B — Unbounded agent autonomy with direct tool authority (rejected)

Models calling tools, publishing results and self-approving. Rejected: violates least privilege, audit-before-
effect and independent-review requirements; hostile document instructions could inherit workflow authority.

### Option C — Bounded assistance behind a Kavriva-owned decision boundary (chosen)

Low-cost conversational understanding, controlled clarification, a provider/model-neutral decision layer
proposing bounded candidates, and deterministic/canonical final validation — with escalation to stronger models
only when the task genuinely requires it, and multi-provider/local-memory/autonomous-agent paths deferred until
separately evidenced.

### Option D — Jev (or similar bounded decision model) as the decision layer now (deferred, not rejected)

Reviewed conclusion `KEEP AS OPTIONAL LATER`: no account, key, schema, data store, code path, contract or
recurring dependency is created today to preserve optionality. A Jev-like model may later be evaluated strictly
as an optional adapter for low-risk routing/classification/triage/scoring/ranking if measured benefit over
deterministic rules and the low-cost LLM path justifies the extra dependency. Its confidence scores can never
override deterministic HOLD, safety, eligibility or authorization rules.

## Decision

Kavriva adopts Option C (with Option D deferred) with the following locked rules:

1. **AI Usta flow:** free-text understanding by a low-cost/fast model → controlled clarification questions
   collecting observable evidence → bounded decision layer proposing one of known task, symptom/diagnostic flow,
   more-clarification-needed, unsupported/unknown, safety hold/escalation → Kavriva deterministic/canonical
   verification (correct motorcycle/variant, guide applicability, approved/current status, prerequisites,
   safety/readiness, source/provenance) → show guide/flow, ask more, or hold safely. Proposed routes are never
   final before verification.
2. **Economic principle:** use the cheapest/fastest model adequate for the task; escalate only when necessary.
   Routine intent, clarification, simple classification and low-risk summaries ride the low-cost path; harder
   reasoning inside allowed scope may call stronger models; deterministic rules win wherever they reliably solve
   the problem without probabilistic AI.
3. **Replaceable boundary:** provider/model-specific behavior (structured outputs, function calling, context
   limits, errors/rate limits, privacy/retention, files/vision/search, lifecycle/versioning) stays behind
   adapters; product taxonomy, allowed routes, safety rules, guide eligibility and authorization never scatter
   across provider-specific calls. Model/provider/version identity and behavior change stay observable and trigger
   re-evaluation.
4. **Least-privilege tools:** retrieved, web, community, document, media and tool content is untrusted data, never
   policy; tool/action authority stays outside model output; retries/outages stay bounded with cost observability;
   critical journeys keep a safe non-AI/deterministic continuation.
5. **Allowed AI help (exhaustive at direction level):** intent/task/symptom understanding; clarification;
   normalization; retrieval-query forming; approved-content summary/explanation; ranking/classifying
   already-eligible candidates; drafting/translation; Internal Operations triage; project/company
   research/drafting/review preparation; proposing a route or tool from a bounded allowed set.
6. **Never sole AI authority for:** unsupported torque/spec/values; canonical technical truth; final
   motorcycle fit/applicability; readiness/safety gates; definitive high-risk diagnosis; physical action outside
   approved guide/state; source/guide verification; approve/publish/recall/suspend; privileged role/policy
   changes; protected audit truth; release/signing/deployment; legal/privacy conclusions; billing/purchase;
   deletion/retention policy; high-impact self-review/self-PASS.
7. **Project/company AI work** follows `DEC-0028`/`DEC-0029`: separate implementer/reviewer/validator roles,
   evidence and independent review; AI never impersonates legal identity, store ownership or qualified attestation.

## Rationale

The shape spends model money only where reasoning is genuinely needed, keeps provider exit cheap by design, and —
most importantly — places the safety-critical judgments (fit, readiness, authority) in deterministic systems that
can be tested exhaustively, while AI does what it is good at: understanding language and proposing bounded
candidates. Deferring Jev avoids paying dependency, evaluation, privacy and operations cost before measured value
exists, without closing the door.

## Consequences

### Positive

- Predictable AI economics with escalation only on demonstrated need.
- Provider incidents, price changes and model deprecations degrade assistance gracefully instead of breaking
  authority (which never lived in the model).
- Every AI suggestion remains re-checkable against deterministic rules and full audit.

### Negative / Trade-offs

- Two-layer design (conversation + decision + validation) is more integration surface than a single chat call.
- Strict HOLD-on-ambiguity behavior will sometimes feel conservative to users mid-task — by design.
- Deferred multi-provider failover, local inference, persistent memory and agent workflows stay unavailable until
  separately evidenced, limiting early resilience options.

## Prohibited / Constrained Alternatives

- Single-provider-everywhere coupling; provider-specific calls scattered through product logic.
- Autonomous multi-agent behavior, persistent consumer AI memory, provider-native agent stacks or dedicated
  inference capacity without separate evidence and approval.
- Model output as authority for any item in the never-list above; confidence/probability overriding HOLD rules.
- Jev/TypeSafe account, key, schema, data store, code path, contract or dependency today.
- Any provider/model/plan, account, key, credit, purchase, prompt/tool schema, agent workflow, vector
  DB/fine-tune, integration, legal/privacy conclusion or recurring budget — none authorized by this ADR.

## Revisit Triggers

- Measured evidence shows a deferred path (second provider, Jev-like adapter, local inference, persistent
  memory) beats the current shape on cost/latency/safety for a bounded use — resolved by superseding ADR scoped
  to that use.
- Exact provider/model/plan, routing thresholds, eval/change-detection design, fallback-divergence policy and
  final budget remain HELD for later evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0046` (binding working direction)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-004__IDENTITY_AUTHORIZATION_SESSION_RECOVERY_AND_PRIVILEGED_ACTIVATION.md`
- `05_ADR/RECORDS/ADR-006__KAVRIVA_API_RUNTIME_AND_DURABLE_LONG_JOBS.md`
- `05_ADR/RECORDS/ADR-009__MOBILE_OFFLINE_PACKAGE_LEDGER_AND_TRANSFER.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-016__MANAGER_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-016__JEV_FIT_REQUIREMENTS_ADDENDUM.md`
- `00_CONTROL/DRIVE_ARTIFACT_INDEX.md` (TASK-004/TASK-005 / REVIEW-007–REVIEW-010 links)
- Downstream: ADR-015 (AI task topology and context packs)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
