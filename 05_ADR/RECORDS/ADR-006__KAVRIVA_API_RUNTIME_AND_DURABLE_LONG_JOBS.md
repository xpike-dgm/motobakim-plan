# ADR-006 — Kavriva API Runtime and Durable Long-Job Execution

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-011, user-approved under `DEC-0038`) compared runtime paths for the mandatory Kavriva API
boundary with current official research, 18 failure/TCO scenarios, a manager proposal and two independent reviews.
Both finalists stayed documentary `0 PASS / 16 HELD / 0 REJECT`: short DB-near Supabase Edge Functions as a
reversible hypothesis, managed container API + worker as the equal-evidence alternative — no production winner.
This ADR locks the runtime-independent product protocol every candidate must satisfy, plus the equal-evidence
transition rule between the hypotheses. It selects no language, framework, queue/worker product, region, plan,
account or deployment, and authorizes no purchase, code or production activation.

## Decision Drivers

- High-consequence product authority lives in an explicit protocol, not in any runtime's behavior: authorization,
  operation identity, audit precondition and negative floors must hold identically on either hypothesis.
- Long jobs (package build, scan/derivative, export, AI/OCR, notification, broad reconciliation) must never be
  squeezed into synchronous requests or background callbacks.
- The transition rule must be evidence-gated in both directions: A's failure never auto-promotes B, and intuition
  ("more flexible", "cheaper headline") is never a migration reason.
- Owner/support boundaries and normalized cost must be decided before, not after, a runtime commits the project.

## Options Considered

### Option A — Short DB-near Supabase Edge Functions as the initial hypothesis (kept, not crowned)

Low-operations candidate for short command/status/read requests behind the API boundary. Held because of CPU/memory/
wall-clock/bundle/log limits, transaction-pooler behavior, rollout/rollback drain proof gaps, common-mode coupling
with Auth/DB/Storage, and hidden adjunct TCO. If long jobs are forced into background callbacks, effects commit
without audit/floor, direct provider bypass appears, or restore resurrects negative state, the affected capability is
rejected-until-mitigated.

### Option B — Managed container API + bounded worker as the equal-evidence alternative (kept, not fallback)

Persistent runtime with visible worker lifecycle for custom dependencies and long jobs. Held because of second
provider/account/billing/support/credential surfaces, cross-provider TLS/region/pooler/latency/egress, web/worker/
queue/deploy/schema/message coordination, image portability limits and partial-health ambiguity. Container health,
queue delivery and image rollback are not product truth, effect proof or data recovery.

### Challenger paths (open, not selected)

Cloudflare Workers for narrow edge/emergency-negative/gateway or later-proven edge workloads; Cloud Run as a managed
container/control-plane alternative. Self-managed VMs are not a starting candidate until owner patch/SSH/restore load
closes. None is selected today.

## Decision

Kavriva locks the following runtime-independent protocol (any present or future runtime must satisfy all of it):

1. **Ephemeral runtime, durable product state:** instances/functions/containers may die and restart; runtime memory is
   never truth. Durable state covers canonical domain versions, operation identity/fingerprint/status, authorization/
   policy/grant/competence/epoch references, audit receipts and ordered floor, outbox/queue intent and effect keys,
   object/package manifests with lineage/classification/negative floors, and all release/suspension/recall/deletion/
   accepted-operation/migration floors.
2. **Full commit-time authorization tuple:** every sensitive effect re-authorizes immediately before commit over
   actor/workload, issuer/session/assurance/step-up/epoch, action, exact object/tenant/scope/classification,
   role/grant/delegation/competence/independence/policy version, object/release/schema/config/package/client
   generations, current negative floors, operation ID with immutable request fingerprint, reason, intended effect,
   audit readiness/receipt and runtime compatibility. Cached claims, UI state, stale tabs, provider roles, RLS
   results and client-supplied IDs never substitute.
3. **Authoritative core vs cross-plane effects:** one narrow DB-assured core binds operation acceptance, current
   authorization/generation fence, canonical transition, audit precondition/receipt reference, deterministic
   outbox/effect intent and reconciliation state. Object, notification, queue, scanner, AI/OCR and external-provider
   effects run as separate idempotent protocols with deterministic keys, manifests, lease/retry budgets, generation/
   epoch rechecks and reconciliation state. DB commit, empty queue and worker success prove nothing about external
   effects.
4. **Operation and idempotency scope:** same semantic retry returns the existing result read-only; different
   payload/actor/scope becomes `CONFLICT/HELD`; cross-tenant status lookup is `DENIED`. Lost responses stay
   `OUTCOME_UNKNOWN` until canonical lookup resolves them.
5. **Long-job capability gate:** package builds, object finalization/scan/render/derivative/OCR, large
   export/import/restore verification, bulk notification and long AI/batch work never run synchronously. Each job
   separates `ACCEPTED/QUEUED` from proven effect and carries operation/effect key, lease/heartbeat/checkpoint,
   bounded retry, DLQ/quarantine, poison/backpressure handling, cancel, deploy drain, message compatibility,
   owner-visible backlog and resolver. Queue "exactly once" or emptiness never proves single completion.
6. **Monotonic negatives:** recall/suspension/revoke/delete/eligibility/accepted-operation/migration floors are
   re-read before every commit; equal-or-newer negative generation beats positive effects; missing/unknown/tie,
   audit outage and stale leases yield `HELD/OUTCOME_UNKNOWN`, never success. Old runtimes, queue messages, caches,
   handles and offline packages cannot clear a newer floor.
7. **End-to-end epoch:** revocation reaches in-flight API operations, retries, worker leases, object handles, browser
   caches/service workers, Flutter packages/ledgers, key state, exports and migrations. Downloaded copies cannot be
   remotely guaranteed away — stated honestly.
8. **Shared state dictionary:** `ACCEPTED`, `QUEUED/SUBMITTED`, `DENIED`, `HELD`, `OUTCOME_UNKNOWN`,
   `PARTIAL/RECONCILING`, `AUDIT_HELD`, `BILLING_HELD`, `ACCOUNT_HELD`, `DEPLOYMENT_HELD`, `OBJECT_QUARANTINE`,
   `RESTORE_QUARANTINE`, `EXPORT_PARTIAL`, `SERVICE_UNAVAILABLE`, `RECOVERY_REQUIRED` — each with allowed/blocked
   effects, retained data, retry policy, cost stop, resolver/support, audit reference and restore/exit impact. Green
   dashboards, HTTP 2xx, worker success and empty queues never override product state.
9. **Direct-path inventory:** exposed tables/views/functions/RPC/Storage/signed URLs/Studio surfaces are inventoried
   and negatively tested; generic client paths carry no high-consequence mutation, export or private-object
   authority. Browser contract covers storage, origins, CSRF/PKCE, step-up binding and lookup disclosure limits.
10. **Equal-evidence transition rule:** A and B are evaluated on identical route/capability classes, workloads,
    fault injection, audit/object/queue/recovery scope and normalized BOM. Migration from A to B happens only if A
    fails a mandatory gate on real fixtures **and** B passes the same gate package with proof. If neither passes,
    the capability stays `HELD` and challengers reopen on equal terms — standards are never lowered to pick a winner.
11. **Owner/support/AI and cost gates:** every outage defines detection, safe-stop, scope, retained data, visible
    state, external actor, credentials, support, cost and reconciliation; the owner only makes plain-language
    approve/hold/stop/payment/legal-support decisions. AI tasks carry narrow scope, short-lived credentials, dry
    runs, hard stops, evidence and independent reviewers, never provider-owner/billing/`service_role`/SQL/SSH/
    approval authority. The normalized safe-cost BOM (compute, queue, audit/fallback, observability, object safety,
    deploy/secret compatibility, accounts/support, DNS/notifications, incident/restore/exit drills, external people,
    AI operations — each classified mandatory/deferrable/optional/scale-triggered) gates every capability; unaffordable
    mandatory assurance holds the capability instead of weakening it.

## Rationale

Locking the protocol instead of the product is the honest conversion of a `0 PASS / 16 HELD` strategy result: it
makes both hypotheses (and any challenger) falsifiable against identical gates, keeps long-job and audit semantics
non-negotiable from the first capability, and prevents the classic failure where the runtime choice silently
redefines correctness, cost and exit.

## Consequences

### Positive

- Runtime becomes replaceable ingress/compute: ingress/decision/effect workers own no product truth.
- No capability can open without its queue, audit, epoch, floor, cost and exit proof — the 16-scenario acceptance
  package in DEBATE-011 §10 is the binding test list.
- Migration decisions become boring evidence comparisons instead of architectural rewrites.

### Negative / Trade-offs

- Protocol rigor (tuples, receipts, leases, dictionaries) is real design/implementation weight carried into every
  later task.
- Neither hypothesis is usable for production today; everything waits on real fixtures — schedule honesty at the
  cost of speed.
- Two-hypothesis maintenance (fixtures for both) costs planning effort until one passes.

## Prohibited / Constrained Alternatives

- Runtime memory, container health, queue delivery/emptiness, worker success, dashboards or HTTP 2xx presented as
  product truth, effect proof or audit receipt.
- Synchronous long jobs; background callbacks/`waitUntil` presented as durable queues.
- A-to-B migration on intuition, headline limits/prices, or A's failure alone.
- Direct provider bypass paths carrying high-consequence effects.
- Any runtime language/framework, queue/worker product, region, plan, account, purchase, deployment or production
  activation — none authorized by this ADR.

## Revisit Triggers

- Real fixtures crown a winner or disqualify a hypothesis — recorded by superseding ADR with the evidence attached.
- Exact queue/worker product, first-release capability list, numeric limits, namespace/retention/cross-region
  behavior and challenger evaluations remain HELD for later implementation evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0038` (binding working direction)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-002__PHYSICAL_BACKEND_PLATFORM_AND_API_AUTHORITY.md`
- `05_ADR/RECORDS/ADR-004__IDENTITY_AUTHORIZATION_SESSION_RECOVERY_AND_PRIVILEGED_ACTIVATION.md`
- `05_ADR/RECORDS/ADR-005__PROTECTED_AUDIT_CUSTODY_RETENTION_AND_INVESTIGATION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__API_RUNTIME_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__API_RUNTIME_PRIMARY_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__API_RUNTIME_FAILURE_TCO_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__REVIEW_A_SECURITY_RECOVERY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__REVIEW_B_OWNER_TCO_OPERABILITY.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__JUDGE_SYNTHESIS.md`
- Downstream: ADR-007 (deploy compatibility), ADR-009 (offline ledger submission), ADR-010 (web runtime modes),
  ADR-014 (AI workload identities)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
