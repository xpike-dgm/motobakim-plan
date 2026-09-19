# DEBATE-003 — Approval, Publication and Emergency Suspension Integrity

Status: `APPROVED WORKING DIRECTION — DEC-0025 / ADR PENDING`
Date: 2026-09-17
Scope: Browser-based Internal Data & Content Operations, publication authority, emergency suspension and outage behavior
Planning constraint: No application code, prototype or executable spike

## 1. Decision question

How should Kavriva ensure that:

1. the exact material reviewed and approved is the material made eligible for consumer use;
2. an edit, stale browser tab, retry or infrastructure failure cannot silently publish another state;
3. unsafe published material can be suspended even when part of the normal identity/publication path is unavailable;
4. rollback, recovery and backup restoration cannot resurrect an unsafe release or erase history; and
5. operators see an honest result when an action succeeds, fails, is partial or has an unknown outcome?

This debate selects product and architecture properties. It does not select a database, cloud, CMS, queue, CDN,
identity provider, signing technology, frontend framework or vendor.

## 2. Existing authority

This debate inherits, rather than reopens:

- `DEC-0021`: Internal Operations is browser-based and planning is no-code.
- `DEC-0024`: approve/publish/recall mutations require an authoritative online result; offline eligibility and recall
  follow the bounded, risk-tiered DEBATE-002 direction.
- `IDCO-RQ-032`: approval captures the exact approved version snapshot; later edits require new review.
- `IDCO-RQ-033`–`037`: publication is controlled, consumer eligibility is explicit and partial/failed publication is visible.
- `IDCO-RQ-038`–`044`: rollback/recall preserve lineage, restrict unsafe future application and retain safe recovery.
- `IDCO-RQ-045`–`050`: material actions are attributable, least-privilege and auditable.
- `IDCO-RQ-060`: failed actions remain recoverable and inspectable; failure is never represented as success.

The relevant open risks are `TSR-006`, `TSR-011`, `TSR-012`, `TSR-014` and `TSR-021`.

## 3. Terms that must not be collapsed

| Term | Meaning |
|---|---|
| Draft | Mutable preparation work. Never consumer-live. |
| Review packet | A bounded candidate plus its exact content, dependencies, evidence, scope and change set. |
| Approved snapshot | The immutable meaning that the approval decision covers. Approval applies only to this snapshot and its recorded conditions. |
| Release candidate | An exact set of approved snapshots and dependency closure prepared for publication. |
| Publication operation | The controlled attempt to make one release candidate current for a defined consumer scope. |
| Current release | The one authoritative release context clients may treat as current for a scope, subject to compatibility, recall and freshness rules. |
| Suspension | Immediate restriction of future normal application for affected scope. It need not provide a corrected replacement. |
| Recall | A controlled safety case that includes affected scope, reason, impact/reach-back and re-entry or replacement work. |
| Rollback | A new controlled publication event that promotes a known-good approved predecessor; it does not erase the intervening release. |
| Outcome unknown | The server may have committed, but the browser has not obtained authoritative confirmation. It is neither success nor failure. |

## 4. Non-negotiable invariants

1. Editing is not approval; approval is not publication; publication is not proof of real-world correctness.
2. Approval is bound to one exact snapshot, dependency set, applicability scope, evidence context and decision record.
3. A later edit creates a new candidate and cannot mutate the approved snapshot in place.
4. Publication can start only from an eligible approved release candidate through one authoritative transition.
5. The operator interface, API and direct data access must not provide a second uncontrolled path to consumer-current state.
6. A current release must never be an unexplained mixture of old and new versions. Any partial or uncertain propagation is explicit and conservative.
7. Retrying the same requested operation cannot create a second different publication effect.
8. A stale page, expired/revoked role or old approval cannot gain authority from browser state; the server re-checks exact version and current permission at mutation time.
9. A timeout cannot be reported as failure or success until authoritative reconciliation is complete.
10. Suspension overrides normal positive eligibility for affected scope. When authority is unknown for critical application, uncertainty does not become permission.
11. Rollback can promote only a known-good, compatible, still-approved release through a new event. If none exists, suspension is safer than guessing.
12. Restoring an old database, cache or backup cannot reduce the known suspension/revocation generation or silently reactivate an unsafe release.
13. Consumer history, provenance, completed-work context and task-specific safe-stop/recovery are not erased by suspension or rollback.
14. Audit history for approval, publish, rollback, suspension, recall, role change and emergency access is append-only or equivalently tamper-evident and independently recoverable.
15. Emergency authority is deliberately narrower than normal administration and cannot be used to author or silently publish replacement content.
16. Approval-to-consumer integrity covers the complete served meaning: derived artifacts, localization, transform profile,
    media, configuration inputs, scope, audience, status and expiry. Mutable runtime substitution cannot change it.
17. Normal publication and emergency suspension share a fenced precedence rule: publication is conditional on the exact
    current suspension/revocation generation, and a newer suspension can never be cleared by an older/in-flight publish.
18. A release generation or suspension/revocation generation moving backward is a fatal authority error, not a valid rollback.

## 5. Alternatives

### Option A — Approved record becomes live directly

An approved database/CMS record is also the consumer-live record.

Benefits:

- operationally simple;
- little release preparation.

Failure modes:

- an in-place edit can change what the approval meant;
- review and delivery race each other;
- partial updates create mixed meaning;
- direct data access becomes an undeclared publication path;
- rollback and audit lineage become ambiguous.

Result: `REJECT`.

### Option B — Controlled immutable release

Approval binds an exact immutable snapshot. A release candidate contains exact approved versions and dependencies.
Only a controlled publication transition can change the consumer-current release.

Benefits:

- strong approval-to-payload traceability;
- deterministic diff, lineage and rollback candidates;
- safer retries and explicit partial/unknown outcomes.

Limitation:

- if emergency suspension depends on the same identity, database, publisher and delivery path, the safety control can fail
  with the incident it must contain.

Result: `NECESSARY BUT INSUFFICIENT ALONE`.

### Option C — Controlled release plus independent emergency suspension plane

Option B plus a narrowly scoped suspension authority and delivery path designed to remain usable when a material part of
normal publishing is unavailable.

Benefits:

- separates content creation from the ability to stop unsafe future application;
- contains compromised publisher, partial rollout and restoration/replay incidents;
- supports conservative client behavior during uncertainty.

Costs/risks:

- additional operational complexity and security controls;
- misuse could suspend valid content;
- independence must be tested rather than merely described;
- fully offline devices still cannot learn a new suspension immediately, as recorded in DEBATE-002.

Result: `RECOMMENDED DIRECTION`.

### Option D — Manual exports and operator-led consumer updates

Benefits:

- low initial automation.

Failure modes:

- slow and error-prone emergency response;
- weak proof that all consumers received one exact version;
- manual copying and retries create drift;
- unsuitable as the authoritative release mechanism.

Result: `REJECT AS PRIMARY MODEL`; documented out-of-band communication may remain a contingency.

## 6. Recommended policy: B + C

### 6.1 Approval binds exact meaning

The review decision must bind at least:

- immutable snapshot identity and integrity evidence;
- exact included claims/content/media metadata and dependencies;
- motorcycle/model/year/variant and other applicability scope;
- evidence/provenance set considered by the reviewer;
- validation findings and unresolved uncertainty;
- reviewer identity, role/scope at decision time, decision time and rationale;
- conditions, expiry/re-review triggers and consequence classification where applicable.
- all derived/rendered artifacts and transformation inputs that can change consumer meaning, including localization,
  templates, defaults, flags, media transforms and mutable external references.

External URLs or mutable dependencies cannot silently enter consumer meaning after approval. They must be frozen into
the closed approved artifact set, bound to an approved immutable identity, or explicitly excluded from application meaning.

Content-addressing, cryptographic signatures or equivalent mechanisms are candidate implementations; this debate requires
the property, not a specific mechanism.

### 6.2 Release candidate and preflight

A release candidate is a closed, inspectable manifest of exact approved versions. Before it may publish, the system must
verify:

- every included item remains approved for the requested scope;
- required dependencies and task-specific safe-recovery closure are complete;
- no included or dependent item is suspended, recalled, stale beyond policy or semantically incompatible;
- the release is compatible with the declared consumer capability envelope;
- separation-of-duties and authorization requirements are satisfied;
- the expected current release has not changed since preparation;
- the approval/dependency generations and current suspension/revocation generation have not changed;
- the operation has one durable identity for retry/reconciliation.

Preflight success is not permanent authority. The authoritative transition re-checks the relevant conditions at commit.

### 6.3 Publication state model

The minimum conceptual states are:

`PREPARED → AUTHORIZED → PUBLISHING → AUTHORITATIVE_CURRENT → DELIVERY_OBSERVED → CONSUMER_RECONCILED`

with explicit branches:

- `HELD`: no publication because a prerequisite or policy is unresolved;
- `FAILED`: authoritative evidence says the operation did not commit;
- `OUTCOME_UNKNOWN`: commit may have occurred; reconcile before retrying or claiming a result;
- `PARTIAL_PROPAGATION`: the authoritative current release changed but one or more delivery layers are not confirmed;
- `SUPERSEDED`: a newer controlled release is current;
- `SUSPENDED`: immediate negative authority restricts normal future application for affected scope;
- `RECALL_OPEN`: a suspension-backed case includes impact, reach-back, correction and re-entry/replacement work.

`AUTHORITATIVE_CURRENT` means the guarded authoritative transition completed; it does not imply instant delivery.
`DELIVERY_OBSERVED` means the declared online delivery layers have provided the required propagation evidence.
`CONSUMER_RECONCILED` is separately observable and never implies a genuinely offline device received the change.

### 6.4 One authoritative current-release transition

For each consumer scope, changing the current release requires:

- expected-current-version checking so a stale operation cannot overwrite a newer result;
- an idempotent operation identity so a retry resolves to the same recorded result;
- atomic promotion of a complete release manifest or an equivalent all-or-explicit-partial guarantee;
- server-derived result, timestamp and audit event;
- a read-after-operation status lookup that works independently of the initiating browser request.
- one conditional/fenced transition over candidate identity, approval/dependency generations, expected current-release
  generation, expected suspension/revocation generation and current authorization context.

Normal publication and emergency suspension are ordered by a protected authority tuple such as
`(release generation, suspension/revocation generation)`. The exact representation is deferred, but these semantics are
not: a publish prepared against an older suspension generation is rejected; a suspension never grants positive authority;
re-entry requires a new explicit controlled event; unknown/mismatched tuple state fails closed for affected critical use.

The durable operation identity is bound to the action type, actor/authority, exact candidate/suspension payload, scope,
expected generations, intended effect and validity context. Reusing it with different meaning is rejected. Retention,
cross-region uniqueness and controlled supersession are later design requirements.

The browser may prepare, request and inspect the operation. It does not decide success locally.

### 6.5 Browser failure and stale-session behavior

- Reconnect or refresh must query operation status rather than silently resubmit.
- An operator sees `outcome unknown` when confirmation is missing, plus the operation identity and a safe reconciliation path.
- A stale tab must be blocked when its expected version, review packet or role context no longer matches the server.
- Role revocation and high-consequence step-up requirements are evaluated by the authoritative service at action time.
- Browser cache, service worker state or optimistic UI is never evidence that publication/recall succeeded.
- Mutation requests, their authoritative status and their result are network-authoritative and non-cacheable. Stale
  browser code may become read-only until refreshed; server-side current-policy/version checks remain decisive.

### 6.6 Emergency suspension plane

Emergency suspension is a negative safety authority: it can restrict affected future application but cannot create new
positive eligibility or publish replacement technical truth.

Required properties:

- narrower action set than the normal publisher: identify scope/release, suspend, state reason/severity and initiate recall;
- operational independence sufficient to survive defined failures of the normal publisher, primary data plane or normal
  operator session path;
- strongly authenticated emergency access, minimal membership, explicit invocation reason and time-bounded use;
- two-person or equivalent independent confirmation for high-consequence use where delay would not increase harm;
- a documented single-actor emergency path only for cases where waiting is more dangerous, followed by mandatory rapid
  retrospective confirmation;
- every attempt, success, denial, expiry and recovery action recorded in protected audit evidence;
- a durable emergency operation identity and authoritative status lookup with the same `outcome unknown` honesty as normal publishing;
- regular drills that test real isolation, credentials, propagation and restoration behavior;
- suspension generation/epoch cannot move backward during restore or failover.

Emergency scope is a closed dependency-aware case, not free text. It identifies the affected claim/content/guide/release,
motorcycle/variant applicability and required recovery closure. When scopes overlap, the most restrictive applicable
negative authority wins; narrower safe re-entry requires an explicit reviewed event and cannot implicitly cancel a
broader suspension.

Before the emergency effect is accepted, minimum protected evidence must durably bind operation identity, actor or
emergency authority, scope, reason/incident, intended effect, ordered time/sequence and result. If the normal audit sink is
down, an independently recoverable tamper-detectable buffer is required. Any exceptional path without that minimum must
be separately authorized by user policy, recorded out of band and quarantined for mandatory reconciliation; it is not
silently assumed here.

The exact break-glass identity, quorum, channel and infrastructure topology remain Phase-5 design choices after failure
testing and staffing analysis.

### 6.7 Outage matrix

| Failure | Normal publish | Emergency suspend | Safe product behavior |
|---|---|---|---|
| Browser loses connection after request | No duplicate retry; status is unknown until lookup | Same | Show `OUTCOME_UNKNOWN`; reconcile by operation identity. |
| Normal identity provider unavailable | Hold new normal approvals/publications | Use separately protected emergency path if incident scope requires | Existing safe content may remain subject to DEBATE-002 bounds; no new positive authority. |
| Publication service unavailable | Hold normal publish | Suspension path must not depend solely on it | Restrict affected critical application when current authority cannot be confirmed. |
| Primary database unavailable/corrupt | Hold normal publish | Use independently recoverable suspension state/path | No reconstruction from browser/cache; preserve history and conservative eligibility. |
| CDN/cache propagation delayed | Do not claim full delivery | Publish suspension/revocation through independently testable route and verify | Affected online clients treat unconfirmed critical eligibility conservatively; offline residual risk remains explicit. |
| Audit sink unavailable | High-consequence normal action holds unless durable protected evidence can be queued safely | Emergency stop may proceed only under documented contingency with later reconciliation | Never discard or silently rewrite the emergency record. |
| Backup/region restored to older state | No release until monotonic authority and lineage reconcile | Latest suspension/revocation state wins | Restored positive state cannot resurrect a release with newer suspension knowledge. |
| Publisher credential suspected compromised | Disable normal publishing authority | Emergency authority suspends affected release/scope; rotate/recover separately | No replacement content until normal trust is re-established. |
| Emergency path unavailable or result unknown | No normal action may override or guess its state | Reconcile with the same durable emergency operation identity; escalate through documented out-of-band reach-back | Never claim suspension success; affected high-consequence positive eligibility holds while current negative authority is unknown. |

The failure domains and independence claims must be named and tested before ADR approval. “Separate button” is not an
independent emergency plane.

A restored system enters quarantine/reconciliation rather than immediately becoming authoritative. It must establish
current-release identity, the latest suspension/revocation floor, audit continuity and content integrity before it may
serve positive eligibility or accept normal publication.

`Publisher unavailable`, `known current release`, `suspension authority unknown` and `known suspended` remain distinct
operator and consumer states. Infrastructure failure is not falsely displayed as a recall; each state carries its own
reason, owner, next action and effect on application versus teaching/history/safe recovery.

### 6.8 Rollback and correction

Rollback is allowed only when the candidate predecessor:

- is an exact previously approved release;
- remains applicable, compatible and not recalled/suspended;
- has known dependency and recovery closure;
- is promoted through the same controlled release event and audit path.

If those conditions are not met, suspend and prepare a corrected release. Rollback does not cancel reach-back or remove
the historical record of the unsafe/intervening release.

### 6.9 Audit and evidence separation

Audit must let an authorized investigator reconstruct:

- which exact snapshot was reviewed and approved;
- who had which role/scope at each material decision;
- which release candidate was authorized;
- every publication/suspension/rollback request and authoritative result;
- current-release and suspension-generation transitions;
- partial, failed, denied and unknown outcomes;
- emergency access, failed access, role changes and restoration/failover events.

The actor who can publish must not be able to silently erase or rewrite the evidence that proves what was published.
Retention, privacy, export and exact tamper-evidence technology remain separate policy decisions.

Audit ordering requires an authoritative timestamp plus monotonic sequence/order evidence. Client wall-clock values are
context only. Emergency fallback evidence remains quarantined until continuity, actor binding and result are reconciled.

## 7. Consumer contract implications

Without selecting transport or storage, the consumer side must be able to evaluate:

- exact release identity and integrity;
- applicability scope and dependency closure;
- current/superseded/suspended/recall meaning;
- minimum supported capability envelope;
- monotonic release and suspension/revocation ordering;
- last authoritative reconciliation context;
- safe-reference/safe-stop content distinct from normal application authority.

An older cached release cannot become current merely because it is internally intact. Push notification is advisory and
cannot be the sole suspension authority. A fully offline device retains the residual recall race already accepted as an
explicit DEBATE-002 constraint.

Safety artifacts use immutable version-addressed identity. Mutable `current` discovery may point to an exact version but
is not itself application authority. When delivery is partial or current status cannot be reconciled, consequence-tier
policy chooses between a specifically known-safe release, reference/safe-recovery-only access or a hold; it never treats
an arbitrary stale cache as current. Service-worker cache behavior and emergency invalidation are explicit requirements,
not assumed consequences of HTTP cache headers.

## 8. Separation of duties working rule

The policy does not require maximum ceremony for every typo. It requires consequence-proportionate independence:

- the author cannot unilaterally approve and publish a high-consequence change;
- review/approval authority is scoped to competence and affected domain;
- controlled publication authority confirms release integrity and policy, not technical truth on its own;
- emergency suspension authority can stop but not create technical content;
- audit/security oversight can inspect without becoming the ordinary publisher.

Exact role names, staffing fallback and quorum rules require the next identity/RBAC debate.

## 9. Acceptance scenarios for later architecture evaluation

Every candidate architecture must walk through, without code:

1. An editor changes one warning after approval but before publication.
2. Two browser tabs try to publish different candidates against the same current release.
3. The network drops after the server commits but before the browser receives the response.
4. One dependency is recalled while a release candidate waits for publication.
5. Publication reaches the authoritative store but not every cache/delivery layer.
6. The identity provider is unavailable during a critical safety incident.
7. The primary database is restored from backup older than the latest suspension.
8. Publisher credentials are suspected compromised.
9. A known-good predecessor is no longer compatible with current clients.
10. There is no known-good rollback candidate.
11. A dormant/offline client reconnects with a lower release/suspension generation.
12. The emergency operator acts alone because waiting for a second person would increase harm.
13. The emergency mechanism itself is unavailable or produces an unknown outcome.
14. A normal publish passes preflight, then an overlapping emergency suspension commits before the publish commits.
15. Localization, a rendering template, feature flag or external media changes after approval.
16. A claim-level suspension overlaps multiple releases and one unaffected variant should remain usable.
17. The protected audit sink and its emergency buffer are both unavailable.
18. A reviewer or approver credential, rather than the publisher credential, is suspected compromised.

A candidate fails if it invents success, permits silent mixed state, moves revocation authority backward, depends on one
unexamined failure domain or loses the approval/publication/audit chain.

## 10. Measurements required before ADR

No numeric target is invented here. Accountable owners must later define and test:

- maximum acceptable time to place a suspension into authoritative effect;
- propagation/acknowledgment objectives per consequence tier;
- recovery time and recovery point objectives for publication, suspension and audit evidence;
- time-bound emergency credential/session policy;
- minimum safe number and availability of emergency operators;
- how long `OUTCOME_UNKNOWN` may remain unresolved and who owns escalation;
- restore/failover reconciliation and anti-resurrection test criteria;
- supported dormant-client behavior and reach-back escalation.
- resolution ownership, legal transitions and escalation age for every unknown/partial normal or emergency operation;
- failure-domain dependency matrix for identity, DNS/network, key/trust root, storage, audit, operator device and consumer path.

## 11. Residual truths and limitations

- No online architecture can immediately update a device that is genuinely disconnected.
- An independent emergency plane reduces correlated failure; it does not eliminate every common dependency.
- Two-person control reduces misuse but can delay response; the exception path must be explicit and reviewed.
- Tamper-evident evidence reveals or resists rewriting according to design; it does not guarantee every human decision was correct.
- Exact-snapshot integrity proves what was approved/published, not that the motorcycle instruction is factually correct.

## 12. Open decisions

1. Which consequence categories require independent approval and which may use a lighter path?
2. What exact emergency single-actor exception is permitted, and who performs retrospective confirmation?
3. Which normal failure domains must the emergency path survive?
4. Which operations hold when the protected audit path is unavailable?
5. What are the numeric suspension, propagation, reconciliation, RTO and RPO targets?
6. How are out-of-band affected-user reach-back and acknowledgment governed?
7. Which content scopes can safely remain usable during publication ambiguity or partial propagation?
8. Which implementation properties prove immutable snapshot identity, monotonic suspension ordering and audit tamper evidence?
9. What is the canonical release/suspension scope lattice and allowed independent publication boundary?
10. Is an emergency stop permitted if neither the normal protected audit sink nor the independent evidence buffer is available?

## 13. Manager working direction

Proceed with Option B + C as the provisional Phase-4 direction:

- exact immutable approval snapshot;
- closed release manifest and one authoritative publication transition;
- idempotent operations, expected-version checks and explicit unknown/partial states;
- narrow, independently recoverable emergency suspension authority;
- a fenced precedence rule between normal publication and emergency suspension;
- monotonic suspension/revocation truth across failover and restore;
- rollback only as a new event to a still-valid known-good release;
- protected attributable audit and consequence-proportionate separation of duties.

The user approved this reviewed working direction under `DEC-0025`. It is not an ADR and does not pass Gate 4 → 5.
Numeric targets, exact governance and implementation technology remain open.

## 14. Primary research basis

The following sources establish properties and limitations, not vendor selections:

- [RFC 8785 — JSON Canonicalization Scheme](https://www.rfc-editor.org/rfc/rfc8785.html): a stable representation is
  required before a structured snapshot can be hashed consistently.
- [RFC 7515 — JSON Web Signature](https://www.rfc-editor.org/rfc/rfc7515.html) and
  [RFC 9421 — HTTP Message Signatures](https://www.rfc-editor.org/rfc/rfc9421.html): signatures protect covered bytes;
  uncovered fields, freshness, key trust and replay remain separate concerns.
- [RFC 9110 — HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110.html): `If-Match` supports lost-update prevention;
  idempotent intended effects can be retried after communication failure, but HTTP does not supply application-level
  exactly-once audit or operation reconciliation.
- [RFC 6585](https://www.rfc-editor.org/rfc/rfc6585.html): `428 Precondition Required` exists to require conditional
  mutation and avoid lost updates.
- [RFC 9111 — HTTP Caching](https://www.rfc-editor.org/rfc/rfc9111.html): caches can serve stale responses under defined
  conditions; cache directives do not prove instant global recall propagation.
- [W3C Service Workers](https://www.w3.org/TR/service-workers/): Cache API state is separate from the
  browser HTTP cache and requires application-managed update/expiry behavior.
- [NIST SP 800-53 Rev. 5](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final): AC-5/AC-6 require separation of duties and
  least privilege; AU-9/AU-10 cover audit protection and attributable actions; CP-10 covers recovery to a known state.
- [NIST SP 800-34 Rev. 1](https://csrc.nist.gov/pubs/sp/800/34/r1/upd1/final),
  [NIST RTO](https://csrc.nist.gov/glossary/term/Recovery_Time_Objective) and
  [NIST RPO](https://csrc.nist.gov/glossary/term/recovery_point_objective): recovery objectives are business-impact
  targets that must be defined and exercised; backup existence does not prove recovery performance.
- [NIST SP 800-193](https://csrc.nist.gov/pubs/sp/800/193/final): authenticated update, unauthorized-change detection
  and secure recovery support the anti-rollback/known-state direction.
- [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html),
  [Transaction Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Transaction_Authorization_Cheat_Sheet.html)
  and [Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html): deny-by-default,
  server-side per-request authorization, transaction binding, trustworthy event fields and protected centralized evidence.
- [The Update Framework specification](https://github.com/theupdateframework/specification/blob/master/tuf-spec.md): an
  official security specification that models rollback/freeze attacks and rejects lower or expired metadata. Kavriva
  adopts the required anti-rollback property here, not TUF as a selected implementation.

Research inferences used by this debate are explicitly architecture requirements: exact snapshot + closed manifest,
application-level operation identity/status lookup, protected monotonic suspension floor, restore quarantine and a narrow
emergency negative authority. A valid old hash/signature proves old artifact integrity, not current approval or safety.
