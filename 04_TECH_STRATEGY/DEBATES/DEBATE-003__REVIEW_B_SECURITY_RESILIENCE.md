# DEBATE-003 — Review B: Security, Resilience and Distributed Failure

Date: 2026-09-17
Reviewer: Independent Luna Max adversarial reviewer
Mode: Read-only, no code
Verdict: `PASS_WITH_CHANGES — REJECT AS ADR/GATE BASIS UNTIL CRITICAL PROPERTIES ARE TESTED`

## Scope

The reviewer attacked end-to-end snapshot binding, conditional/idempotent transitions, partial propagation, browser and
service-worker caching, emergency-plane independence, identity/data/audit outages, break-glass abuse, restore/replay and
audit tamper evidence.

## Critical findings and incorporated corrections

### C1 — Authoring snapshot did not cover the complete served meaning

Localization, templates, defaults, feature flags, media transforms, external URLs or CDN transformations could change
meaning after approval while the original snapshot hash remained valid.

Correction: approval/release closure now binds all derived artifacts and meaning-changing transformation inputs.
Mutable runtime substitution is prohibited; external dependencies are frozen, immutably bound or excluded from
application meaning.

### C2 — Partial propagation lacked a client safety contract

The authoritative pointer can change while HTTP or service-worker caches remain stale.

Correction: the draft separates `AUTHORITATIVE_CURRENT`, `DELIVERY_OBSERVED` and `CONSUMER_RECONCILED`; requires immutable
version-addressed artifacts; treats mutable current discovery as non-authoritative; and applies consequence-tiered
known-safe/reference-only/hold behavior. Mutation results/status are network-authoritative and non-cacheable.

### C3 — Emergency independence was asserted, not demonstrated

A separate endpoint can still share identity, account, DNS/network, key store, database, audit, trust root or operator
device with normal publication.

Correction: a failure-domain dependency matrix and outage/credential-compromise drills are now pre-ADR requirements.
The draft explicitly says a separate button is not an independent plane.

### C4 — Restore could not prove the latest suspension from an old database

Correction: both release and suspension generations are protected monotonic authorities; backward movement is fatal.
Restore enters quarantine and cannot serve positive eligibility or accept normal publication until current identity,
suspension floor, audit continuity, content integrity and key trust reconcile.

### C5 — Break-glass during audit outage could become unaudited authority

Correction: the emergency effect requires independently recoverable, actor-bound, ordered and tamper-detectable evidence.
Emergency operations also have outcome-unknown and reconciliation semantics. Policy for simultaneous failure of both
normal and emergency evidence paths remains explicitly open.

## Major findings and incorporated corrections

- Operation identity now binds action, actor/authority, exact payload, scope, expected generations, effect and validity;
  reuse with different meaning is rejected.
- Commit is one conditional/fenced transition over approval/dependency, current-release, suspension and authorization
  generations; HTTP conditional requests alone are not claimed to supply multi-object atomicity.
- Unknown/partial operations require durable guarded transitions, one resolver, escalation age and controlled supersession.
- A newer suspension cannot be cleared by an in-flight normal publish; re-entry requires a new explicit event.
- Browser mutation/status responses are non-cacheable, server-versioned and revalidated; stale UI may become read-only.
- Break-glass threat-model requirements now include scoped credentials, step-up, expiry, incident binding, review and
  credential rotation; exact mechanism remains open.

## Evidence notes

The review supports the use of RFC 8785/7515/9421 for limited integrity properties, RFC 9110/6585 for conditional and
retry semantics, RFC 9111 plus the current W3C Service Workers specification for cache limitations, NIST SP 800-53/34
for separation/audit/contingency controls, TUF for rollback/freeze properties and NIST SP 800-193 for secure-recovery
principles. These establish properties and risks; none is silently selected as the Kavriva implementation.

## Reviewer conclusion

B+C is the correct provisional no-code direction after the corrections. It remains non-ADR until end-to-end artifact
binding, scope rules, emergency common-mode independence, restore anti-resurrection, protected emergency audit and
acceptance drills have named owners and evidence.
