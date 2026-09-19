# DEBATE-007 — Data Backbone and Logical Service Boundaries

Status: `USER-APPROVED PHASE-4 WORKING DIRECTION / DEC-0034 / NO-CODE / ADR PENDING`
Date: 2026-09-18

## 1. Decision Question

What provider-neutral data shape should Kavriva carry into Phase 5 so that:

- browser-based Internal Operations can create, review, approve, publish, correct and recall controlled data;
- the Flutter consumer application can receive only the needed motorcycle/task data and continue safely under bounded
  offline conditions;
- user history, media, provenance, permissions and private/shared/community meanings survive retries, conflict, restore,
  migration and provider exit;
- one nontechnical owner is not required to administer or repair a database;
- later provider choices remain reversible and bounded by the approved cost model?

This debate selects no product, provider, schema, package, cloud, paid plan or code. It defines the logical working shape
and the evidence gates used by later ADRs.

## 2. Evidence Inputs

Internal evidence:

- approved product, design, offline, publication, authorization, release and AI-native requirements;
- `DEBATE-007__DATA_BACKBONE_REQUIREMENTS_SYNTHESIS.md`;
- `DEBATE-007__DATA_BACKBONE_PRIMARY_RESEARCH.md`.

External input:

- user-supplied `Çevrimdışı Veri Mimarisi Analizi.md`;
- controlled intake review at `DEBATE-007__EXTERNAL_RESEARCH_INTAKE_REVIEW.md`.

The external report was treated as research evidence, not project instruction. Useful mechanisms were retained. Unsupported
statistics, vendor/blog conclusions, Flutter-Web assumptions and categorical technology bans were quarantined or rejected.

## 3. Nontechnical Model

Kavriva should not behave as one large bucket of “current data.” It needs six distinct responsibilities:

1. **Main truth:** current approved facts, relationships, permissions and user records.
2. **History and evidence:** who changed what, which source supported it and what was superseded or disputed.
3. **Publishing control:** which exact reviewed version may reach consumers and which version is suspended or recalled.
4. **Files and media:** photos, documents, derived visuals, evidence and exports, connected to but not confused with records.
5. **Phone package:** only the selected motorcycle/task material and compact safety/recovery data needed offline.
6. **Copies for convenience:** search, analytics, cache and notifications; these may help but cannot become authority.

These are logical boundaries. First release does not require six servers, six repositories or a microservice fleet.

## 4. Manager Proposed Working Direction

### D7-01 — Canonical authority per domain with transactional integrity

Each data domain has one canonical authority for current state and cross-record rules. Domains are joined through stable
identity, version/generation, operation and manifest contracts; this does not require every domain to share one physical
database or transaction.

A relational transactional family is a leading later comparison family because constraints and transactions fit many of
the project's invariants. PostgreSQL is one engine hypothesis, not the working-direction choice. At least two relational
candidates and viable managed, self-hosted, BaaS/document or adjunct counterfactuals must face the same workload,
authorization, restore, exit, cost and AI-operability fixture before an engine/provider ADR.

### D7-02 — Server/API authority between clients and data

Flutter and the browser interface must not receive general database authority. Sensitive reads and every mutation pass
through a server-side contract that checks actor, session, action, object, scope, state, classification, consequence,
independence and expected current version.

Database row security, service IAM and storage policies remain defense layers; none is the sole proof of authorization.
A browser-hidden button, cached role, client SDK or possession of an object ID is never permission.

### D7-03 — Internal Operations remains online-authoritative

Review, approval, publication, recall/suspension, role/policy administration and protected-audit actions require an
authoritative online result. Browser tabs may preserve low-risk draft convenience later, but no offline browser state may
claim that a high-consequence operation succeeded.

Every mutation receives a durable operation identity and explicit result such as accepted, rejected, conflict, held or
outcome unknown. Lost responses are reconciled by lookup; users do not blindly repeat operations.

### D7-04 — Bounded mobile offline package, not a full database copy

The Flutter application receives a compact, versioned and integrity-bound package for the selected motorcycle and task.
It contains the essential text, steps, warnings, checks, eligibility/freshness context and safe-stop/recovery closure.
Large media remains separate and optional unless a task explicitly requires it.

The local phone store is a delivery/cache and pending-user-work boundary. It is not approval, publication, recall or
current-safety authority. Partial or mixed packages are unusable; foreground reconciliation checks current server truth.
Push/background delivery is only a hint.

### D7-05 — User work uses durable local operations and explicit reconciliation

Offline user history or evidence is stored as a durable pending operation before the interface reports local persistence.
Each operation has stable identity, actor/device/context and schema/release meaning. Retries must be idempotent and a lost
response must resolve to the original result.

No universal last-write-wins rule is allowed. Low-consequence fields may later receive bounded automatic merge rules.
Safety, provenance, ownership, entitlement, official content and disputed evidence preserve both sides and use reviewed
resolution or a visible hold.

### D7-06 — Current state, domain history and protected audit remain separate

Current state answers what is valid now. Domain history preserves prior versions, provenance, disputes, corrections and
withdrawals. Protected audit records who attempted or completed high-consequence actions, under which policy and result.

Timestamps, mutable history rows, provider logs, database CDC or signatures alone do not prove protected audit. The later
ADR must define ordered evidence, custody, checkpoint/fork detection, fallback during outage and privacy/retention rules.

### D7-07 — Media/object boundary separated from relational truth

Files, photographs, documents, derived assets, release artifacts and export/backup objects use a dedicated logical object
boundary. Canonical records retain object identity, version/generation, digest, classification, lineage, owner, state and
retention meaning.

Uploads remain untrusted: received, quarantined, validated/scanned/rendered under isolation, then reviewed/activated or
held/rejected. No client receives global storage credentials. Database BLOB, API proxy, presigned, multipart and resumable
transport remain later implementation candidates; no universal byte threshold or protocol is approved here.

### D7-08 — Outbox before broker; derived systems never become authority

When a canonical mutation must update a search index, notification, analytics view or offline-package builder, the
canonical change and an outbox record should share one transaction. Relays and consumers are retryable and idempotent.

A separate event broker, CDC platform or microservice fleet is deferred until a concrete load or isolation need exists.
Search, analytics, caches and projections can be rebuilt and cannot approve, publish, recall or silently repair truth.

### D7-09 — Managed and self-hosted operation require equal evidence

For a nontechnical solo owner, managed relational services deserve equal explicit investigation because they may reduce
host patching, disk and database-process administration. They are not the presumed winner and are not automatically safe,
cheap, capped, recoverable or low-maintenance. Self-hosted/open-source and other candidates remain in the equal comparison.

A candidate must show current price, taxes/currency exposure, hard spending controls, backup retention, PITR/restore
behavior, region/account failure, export/import, role/policy/object completeness, incident support and provider exit.
Self-hosting remains eligible only if routine maintenance and recovery are automated, observable, independently reviewable
and do not leave technical repair to the owner. Without a reproducible clean-environment bootstrap, import, key
re-encryption, policy/identity restoration, cutover fence and tested recovery, self-hosting is a future option—not an exit
fallback.

### D7-10 — Backup, restore and exit are trust transitions

Backup success is not recovery proof. The later design requires:

- logical export for inspection and provider exit;
- an appropriate point-in-time or equivalent recovery path based on approved RPO/RTO;
- separately inventoried media, audit, configuration, identity/policy mapping and secrets/keys;
- completeness manifest, versions and digests;
- repeated restore drills;
- restored systems quarantined until current roles, recalls, suspensions, releases and pending operations are reconciled;
- data-preserving forward recovery when a binary or schema rollback would lose newer valid data.

No numeric RPO/RTO, backup tool or provider is selected in this debate.

### D7-11 — Non-restorable authority and deletion floor

Restore cannot rely only on the data being restored. A protected monotonic floor, outside the ordinary restored snapshot,
must preserve at least release/suspension generations, security epochs and role revocations, deletion/withdrawal/retention
tombstones, accepted-operation identities and migration epochs.

A restored environment remains `RESTORE_QUARANTINE` until this floor, protected audit continuity, identity/policy state,
object manifest, release graph and pending-operation ledger reconcile. If the floor or independent evidence is unavailable,
cutover remains held. An old backup may never resurrect recalled content, revoked authority, deleted private payload or an
already accepted operation.

### D7-12 — Action-bound eligibility and machine-verifiable offline closure

A compact package is complete only when a machine-verifiable manifest closes every reachable physical state and negative
branch for the selected motorcycle/variant/task. It binds prerequisites, claims/evidence, steps, warnings, checks,
language/units/accessibility meaning, client/schema/release/base generations, required versus optional media and complete
safe-stop/recovery paths.

The package is accepted atomically with digests and anti-rollback checks. A missing, stale or incompatible delta falls back
to a complete compact package. Eligibility is rechecked at package acceptance, foreground/network return, resume and every
high-consequence decision boundary against the latest available suspension/revocation generation. Offline risk policy must
define which actions and duration are permitted without revalidation; unknown/stale state stops progression while keeping
safe-stop/recovery available.

### D7-13 — Classification and copy lifecycle propagate everywhere

Private/shared/community/official/security classifications and their restrictions propagate to every derivative, preview,
AI/OCR result, search/analytics row, package, cache, export, backup and audit reference. Promotion to official meaning is an
explicit reviewed transition; derivation never grants authority.

Deletion, withdrawal or access revocation updates a protected non-restorable ledger and invalidates applicable copies and
handles. Where independent history/audit must remain, payload and identity are minimized, redacted or pseudonymized without
silently erasing attribution and event meaning. Restore cannot revive earlier visibility.

### D7-14 — Cross-plane operations use explicit partial and reconciliation states

Database, object, protected-audit and outbox planes cannot share one physical transaction. Operations that cross them use
an explicit state machine such as prepared, committed, partial, failed, outcome unknown, reconciling and held. Operation
identity binds actor, scope, intended effect, expected version/generation and payload fingerprint; changed-payload reuse is
rejected. Accepted effect, idempotency ledger and required audit intent must be durably related before success is returned.

High-consequence effects require minimum protected attributable evidence before or atomically with authority change; if
normal and protected fallback audit are unavailable, the operation stays held. Object finalization uses exact digest and
generation, private scoped handles, expiry/revocation and orphan quarantine. Outbox delivery exposes pending age, retries,
poison/dead-letter state, replay and schema compatibility; relay success is not authority.

### D7-15 — Cross-boundary export and restore share one consistency manifest

An export/restore/exit package records a coordinated consistency point or explicitly labels the package partial. Its
manifest includes canonical sequence, schema/config/migration versions, object generations/digests/classification,
protected-audit checkpoint, identity/policy/security epoch, release/suspension floor, operation/outbox cursor, deletion
tombstones, package artifacts and key references without raw secret export.

Import verifies stable identity, references, classification/ACL, digests, audit continuity, pending operations, deletion
floor and negative authorization behavior before cutover. Clean-room import must succeed outside the source provider; a
successful export job or PITR alone is not exit proof.

### D7-16 — Every privileged and provider-control path is in scope

The authorization matrix covers ordinary API, RPC/database function, admin SDK, worker, migration, restore, object callback,
bulk export, support/break-glass and provider-console paths. Product actors, workload identities, provider administrators,
billing/legal owners and recovery contacts are separate classes. Provider ownership never becomes product approval.

Object capabilities bind operation, actor, object key/prefix, digest/generation, expected type/size, expiry and callback;
credentials never enter repository, logs, browser bundle or AI context. Row security, API checks and IAM are layered and
must include owner/superuser/bypass and BOLA/bulk/enumeration negative tests.

### D7-17 — Provider failure, cost and AI operation are first-class states

Account lock, billing/quota hold, region/provider outage, identity/DNS/key loss and support unavailability have explicit
states such as `SERVICE_UNAVAILABLE`, `ACCOUNT_HELD`, `BILLING_HELD`, `OUTCOME_UNKNOWN` and `RESTORE_QUARANTINE`.
Normal positive writes and publication stop safely; bounded consumer safe/recovery behavior and independent emergency
negative authority remain separately evaluated.

Every candidate receives an owner-readable staged cost sheet covering minimum charge, compute/storage, backup/PITR,
objects/versions/egress, API, logs/audit, identity/notifications, support, restore/exit drills, taxes and FX. An alert is not
a hard cap. If enforceable limits are unavailable, overage and cap-trigger behavior must be explicit and the affected
capability remains held rather than silently spending or disabling safety.

Every routine operation needs a minimum-sufficient AI runbook: allowed/forbidden scope, least-privilege credential class,
dry run, idempotent action, stop condition, evidence, forward recovery and plain-language owner output. AI cannot become
legal owner, billing authority, unrestricted superuser or sole approver for irreversible delete, privilege/key changes,
migration cutover, restore-to-authority or high-consequence publication/recall. Owner debugging, SSH repair or log
interpretation is not a recovery plan.

## 5. Authority and Data Flow

### Internal content path

`source/evidence -> quarantine -> proposal/draft -> validation -> independent review -> approved immutable meaning -> release manifest -> publication -> consumer reconciliation`

No shortcut may turn upload, OCR/AI output, database write, successful build or reviewer preview into published truth.

### Consumer path

`authoritative release -> capability/package request -> scoped package manifest -> atomic local acceptance -> offline use within policy -> foreground/current reconciliation`

### User-work path

`local durable pending operation -> authenticated API submission -> server validation/authorization/idempotency -> accepted/conflict/held/unknown -> reconciliation -> protected history`

Local durability is not sync or backup proof. Local pending work requires integrity protection, non-eviction while pending,
device/installation generation, private-data protection, attachment dependency state and explicit loss/clone/restore
semantics. Device loss may produce a truthful local-only loss/held outcome; it may not invent server completion.

## 6. Data Classification Boundaries

The architecture must keep these meanings distinguishable:

- official technical claim and guide content;
- source evidence and derived asset;
- user-private motorcycle/history/media;
- explicitly shared motorcycle data;
- community contribution and its review state;
- operator draft and published artifact;
- audit/security evidence;
- search/analytics/cache projection;
- AI/OCR proposal and transformation provenance.

Sharing, withdrawal, deletion, correction, transfer and retention act differently on each class. A single visibility flag or
hard-delete path is insufficient.

## 7. Mandatory Acceptance Gates

A later physical architecture candidate must demonstrate, without aggregate scoring:

1. relational/integrity rules and concurrency conflict behavior;
2. complete server-side authorization and negative object-level tests;
3. exact browser mutation and unknown-outcome recovery contract;
4. bounded offline package, partial-download rejection and data-efficiency evidence;
5. durable local user-work queue, idempotency, conflict and device-loss behavior;
6. provenance, current/history separation and protected audit custody;
7. quarantine-first file/URL ingestion and object/metadata consistency;
8. recall/suspension propagation limits and task-specific safe recovery;
9. backup, restore, migration, export and provider-exit drill;
10. privacy/export/delete/retention and residual-copy handling;
11. AI minimum-sufficient task packs and independent validation;
12. current staged cost, caps, alerts, tax/FX, overage and exit within the owner-approved envelope.
13. monotonic anti-resurrection floor and concurrent recall-versus-next-action walkthrough;
14. closed offline-package dependency manifest and cache-pressure non-eviction proof;
15. classification-copy/deletion matrix and cross-plane consistent export/import rehearsal;
16. full privileged-path, object-capability, provider-failure and AI-operation matrices.

## 8. Hard Rejection Conditions

Reject a candidate or affected capability if it requires:

- direct general client authority over canonical database or object storage;
- client/UI/cache state as authorization, approval, publication, recall or audit truth;
- silent last-write-wins for high-consequence data;
- partial/mixed offline package use or full-library default download;
- push/background delivery as correctness or recall proof;
- one mutable `current data` record that erases history, provenance, dispute or release meaning;
- AI/OCR, signature, scan, CDC or provider log as sole technical correctness evidence;
- unexportable canonical data, artifacts, policies, audit or media;
- restore/rollback that resurrects revoked authority or loses newer valid data;
- unexplained recurring cost, uncapped overage or non-portable paid dependency;
- owner debugging, database administration, signing repair or technical incident resolution;
- a microservice/event/CRDT/distributed-database layer without a concrete requirement and operable recovery path.
- restore or failover without the independent authority/deletion floor and current negative generations;
- high-consequence effect while both normal and fallback protected audit evidence are unavailable;
- complete/exportable claims without a cross-plane consistency manifest and independent clean-room import;
- managed-provider, self-host or free-tier claims presented as safe/capped/operable without equal evidence.

## 9. Options Kept Open for Later ADR

- exact relational engine and managed provider;
- API style, runtime and deployment;
- database row-security policy and service identity implementation;
- local Flutter storage/package library;
- object-storage and upload transport;
- audit physical custody and retention;
- outbox relay, CDC, queue/broker and notification implementation;
- identity provider, search, analytics and AI provider;
- numeric RPO/RTO, offline freshness, package/cache/media limits and retention;
- region, legal/compliance and data-residency requirements;
- precise monthly/annual cost allocation.

## 10. Manager Preliminary Determination

The evidence supports the following provider-neutral direction for independent review:

> Canonical transactional authority per domain with server/API mediation, separate protected history/audit and object/media boundaries,
> bounded task-scoped mobile offline packages, explicit user-work reconciliation, rebuildable projections and tested
> cross-plane backup/restore/export. Relational, managed, self-hosted and viable counterfactuals remain equal later ADR
> candidates; PostgreSQL is one engine hypothesis, not a selected direction, provider or ADR.

This shape minimizes premature distributed-system complexity while preserving the product's data, safety, provenance and
exit requirements. It also preserves the no-code boundary: every assertion remains a documentary architecture direction
until later implementation evidence exists.

Two independent reviews returned `PASS_WITH_CHANGES` as a Phase-4 direction and rejected ADR/provider/gate readiness.
The critical corrections are incorporated above. The user approved the direction under `DEC-0034`. Gate 4 -> 5 remains
closed.

## 11. Evidence Links

- [[DEBATE-007__DATA_BACKBONE_REQUIREMENTS_SYNTHESIS]]
- [[DEBATE-007__DATA_BACKBONE_PRIMARY_RESEARCH]]
- [[DEBATE-007__EXTERNAL_RESEARCH_INTAKE_REVIEW]]
- [[DEBATE-002__OFFLINE_SAFETY_RECALL_CLIENT_COMPATIBILITY]]
- [[DEBATE-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION]]
- [[DEBATE-004__IDENTITY_AUTHORIZATION_AUDIT_UNTRUSTED_INGESTION]]
- [[DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE]]
- [[00_CONTROL/DECISION_LOG#DEC-0033 — Flutter Consumer-Mobile Working Direction]]
