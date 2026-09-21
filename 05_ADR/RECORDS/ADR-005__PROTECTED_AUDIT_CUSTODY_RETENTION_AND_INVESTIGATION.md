# ADR-005 — Protected Audit Custody, Retention and Investigation

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

ADR-004 locked audit governance (audit-before-effect, append-only integrity, custody independence from publishers).
Phase-4 strategy (DEBATE-004 §8 under `DEC-0026`, DEBATE-011 §4.1 under `DEC-0038`) defined what the custody must do:
durably record minimum protected evidence through normal or independent fallback paths, survive sink outage without
false success, support object-centered investigation, and handle retention, legal hold, redaction and export as
explicit policy. This ADR locks the custody, retention and investigation contract. It selects no log/SIEM/audit
product, retention engine or vendor, and authorizes no account, purchase, code or deployment.

## Decision Drivers

- The actor who can publish must never be able to erase or rewrite evidence of its own actions — custody must be
  structurally independent from ordinary publisher and access administration.
- Audit failure must never create false success: missing normal and fallback evidence holds positive action and
  quarantines emergency action until reconciled (ADR-003 outage matrix).
- Investigators need a readable object-centered chain, not raw log piles; privacy needs redaction without destroying
  proof.
- Retention, legal hold and export are policy choices with legal weight and must be explicit, not emergent defaults.

## Options Considered

### Option A — Publisher-owned log tables as audit (rejected)

Audit rows live in the same database, access regime and backup as product data, writable by whoever publishes.
Rejected: the audited actor controls the evidence; tampering, silent rewrite and loss-with-restore are
undetectable; provider logs alone prove even less.

### Option B — Independent append-only custody with protected fallback (chosen)

Audit evidence lives in separately protected, append-only (or equivalently tamper-evident) custody with independent
administration (write-only/read-only/dual-controlled by function), ordered server time plus monotonic sequence,
integrity checkpoints with gap/fork/replay detection, and a bounded separately protected buffer when the normal sink
fails. Investigation access is itself scoped and audited.

### Option C — External managed SIEM/log platform as the whole answer (not selected now)

A managed security-log platform could serve as a custody component, but no product is selected in this ADR: cost,
retention control, export/exit fidelity and independence from the publisher's provider account are unproven. Remains
an implementation candidate evaluated against the contract below.

## Decision

Kavriva adopts Option B with the following locked contract:

1. **Event coverage:** authentication, recovery, session/step-up lifecycle; access grant/deny/change/expiry and
   policy change; sensitive reads, private-evidence access, search and export; upload/URL retrieval, quarantine,
   scan, parse, preview, release and deletion/retention actions; draft/review/approval/rejection/publication/
   rollback/suspension/recall/restore; denied/failed/partial/outcome-unknown operations; audit inspection/export and
   emergency/break-glass attempts.
2. **Minimum event meaning:** actor, effective role/scope, session/assurance context, ordered server time plus
   monotonic sequence, action, object/version/state, reason, policy version/decision, operation identity, old/new
   meaning and result. Credentials, session secrets and unnecessary sensitive payloads are excluded; sensitive detail
   travels by protected reference.
3. **Before-effect linkage:** the protected event (or equivalent transactional assurance) is accepted by primary or
   fallback custody and bound to the exact intended effect before high-consequence positive effects open; commit
   re-verifies receipt, authorization and generation; aborted effects close as `NO_EFFECT/ABORTED`, uncertain ones as
   `OUTCOME_UNKNOWN/RECONCILING`. Runtime/provider logs are never the receipt.
4. **Fallback discipline:** if the normal sink fails, a bounded separately protected buffer records the same minimum
   evidence. If neither path can durably record, normal high-consequence action stays `HELD`; emergency negative
   action follows the ADR-003 exception policy and stays quarantined/unknown until reconciled. State changes with
   uncertain audit persistence are never reported as ordinary success.
5. **Integrity properties:** append-only or equivalent tamper evidence; monotonic ordering with checkpoints;
   gap/fork/replay detection; restore reconciliation that preserves audit continuity before the restored system may
   serve authority; alerting on missing sequence, policy bypass, privilege escalation, repeated denial, unusual
   export and ingestion anomalies.
6. **Retention and legal handling:** retention periods, legal-hold behavior, privacy redaction rules, export periods
   and custody independence are explicit policy decisions recorded separately — never silent defaults. Retention
   change and redaction are themselves audited events.
7. **Investigation contract:** an authorized investigator can reconstruct the chain
   `current state → operation → actor/effective grant/delegation → policy version → artifact/version →
   decision/result → dependent impact`, with proof of sensitive exposure preserved through protected references
   instead of duplicated private payloads. Audit search, retrieval, redaction, retention change and export are
   themselves audited. Audit supports accountability, not surveillance by default, and never substitutes
   authorization.
8. **Administration separation:** audit administration is functionally separated from publisher and access
   administration (write-only, read-only or dual-controlled by function); direct control-plane/storage changes
   require detection, protected audit and incident handling.

## Rationale

Only structurally independent custody makes "the publisher cannot erase its own trail" true instead of aspirational.
Binding retention, fallback and investigation behavior now — while leaving the physical product open — keeps every
custody candidate (owned store, managed SIEM, hybrid) testable against one contract and prevents a future purchase
from quietly redefining what counts as proof.

## Consequences

### Positive

- Evidence survives publisher compromise, sink outage and restore — the three classic audit killers.
- Investigators and reviewers share one reconstructable chain across approval, publication, identity and recovery events.
- Retention and redaction become reviewable policy instead of hidden configuration.

### Negative / Trade-offs

- Independent custody is a separate cost, retention and operations surface (covered by the normalized BOM rule, not
  assumed free).
- Held-on-missing-audit behavior deliberately blocks normal high-consequence work during custody outages.
- Redaction-by-reference design is more complex than plain log rows.

## Prohibited / Constrained Alternatives

- Publisher/admin-writable audit tables; provider logs presented as product audit.
- Effect-before-audit for high-consequence actions; success reported while audit persistence is uncertain.
- Silent retention expiry, silent redaction, or retention change without an audited event.
- Audit inspection/export granting authority to modify source evidence.
- Any audit/log product, retention engine, account, purchase or deployment — none authorized by this ADR.

## Revisit Triggers

- Evidence shows the independence/fallback contract cannot be operated within bounded AI workflows, or a concrete
  custody product passes the full contract including restore reconciliation and clean-room exit — resolved by
  superseding ADR.
- Exact retention periods, redaction rules, alert thresholds, legal-hold destinations and the custody product choice
  remain HELD for later policy/procurement evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0026`, `DEC-0038` (binding working directions)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-002__PHYSICAL_BACKEND_PLATFORM_AND_API_AUTHORITY.md`
- `05_ADR/RECORDS/ADR-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md`
- `05_ADR/RECORDS/ADR-004__IDENTITY_AUTHORIZATION_SESSION_RECOVERY_AND_PRIVILEGED_ACTIVATION.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-004__IDENTITY_AUTHORIZATION_AUDIT_UNTRUSTED_INGESTION.md` (§8)
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__JUDGE_SYNTHESIS.md` (§4.1)
- Downstream: ADR-006 (receipt protocol), ADR-010 (web audit surfacing), ADR-012 (analytics/audit separation)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
