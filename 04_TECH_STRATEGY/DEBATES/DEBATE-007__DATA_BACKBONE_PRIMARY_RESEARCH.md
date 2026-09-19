# DEBATE-007 — DATA BACKBONE & LOGICAL BOUNDARIES — PRIMARY RESEARCH

Status: `RESEARCH DRAFT — PHASE-4 / NO-CODE / NO PROVIDER DECISION`

Date: `2026-09-18`

Decision level: primary-source research, logical-boundary proposal, and acceptance/rejection gates. This document is not an ADR, provider selection, framework selection, implementation plan, or authorization to spend.

## 1. Decision question

What kind of data backbone can preserve Kavriva's authoritative technical/content truth, user history, media and privacy boundaries, offline task packages, approval/publication/recall semantics, audit/provenance, and provider exit while remaining operable by an AI-assisted, nontechnical solo owner?

The question is deliberately about mechanisms and boundaries, not brand choice. The result must support:

- a Flutter consumer client with Android first and iOS later;
- browser-based Internal Operations for a nontechnical owner;
- data-critical technical guidance where unsafe or stale truth must not be silently presented as current;
- motorcycle/variant applicability, evidence, uncertainty, review, release, suspension, recall, and recovery as distinct concepts;
- user history, private data, and media without making personal data indistinguishable from canonical technical content;
- bounded offline use with a compact safe recovery closure and no large automatic cellular download;
- protected attributable audit/provenance and reproducible release meaning;
- a later non-store operating ceiling of approximately `2,000–3,000 TRY/month` as a planning constraint, not a spend authorization; and
- backup, restore, export, and provider-exit that can be tested by AI with explicit owner decisions where human/legal judgment is required.

Explicit non-decisions in this debate:

- no database, cloud provider, BaaS, broker, storage vendor, CMS, search engine, sync framework, or API framework is selected;
- no dynamic price is treated as current or committed;
- no code, schema, migration, prototype, or deployment is authorized;
- no event-sourcing, microservices, multi-region, or high-availability commitment is implied;
- no local cache, replica, backup, or event log is treated as authoritative merely because it is available offline or has a newer timestamp.

## 2. Approved inputs and product constraints

### 2.1 Control decisions that constrain this debate

Control context is anchored in [AI_START_HERE](../../00_CONTROL/AI_START_HERE.md), [CURRENT_STATE](../../00_CONTROL/CURRENT_STATE.md), [DECISION_LOG](../../00_CONTROL/DECISION_LOG.md), [PROJECT_CHAT_INSTRUCTIONS](../../00_CONTROL/PROJECT_CHAT_INSTRUCTIONS.md), and the [04_TECH_STRATEGY README](../README.md). The product-side data/content boundary is described in [Internal Data & Content Operations Requirements](../../03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md) and [Internal Data & Content Operations Workflow Lifecycle](../../03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKFLOW_LIFECYCLE.md).

The following control decisions are inputs, not re-opened here:

- `DEC-0023`: default offline unit is the smallest safe package for a selected motorcycle and applicable guide/task. A lightweight core includes fit/version/status metadata, text/steps, critical warnings, required checks, and task-specific safe-stop/recovery. Heavy media is optional and on demand; large automatic cellular downloads are out of scope. Dedupe, incremental updates, compression, cache limits, and cleanup remain to be evaluated.
- `DEC-0024`: offline is risk-tiered and bounded. Exact release/client compatibility matters. Unknown, stale, or critical dependencies fail closed. Teaching/history/provenance/safe recovery are distinct from normal application eligibility. Restore, time anomaly, incompatible client, or mixed package cannot create positive authority. Internal Operations approval, publication, recall, and role mutation require authoritative online state.
- `DEC-0025`: approval binds exact immutable consumer-served meaning, including derived artifacts and their inputs. Publication uses a closed release manifest and guarded transition. Outcome unknown is explicit and reconciled against the same operation. Authoritative-current, delivery-observed, and consumer-reconciled states are distinct. Emergency suspension is narrow negative authority; restore is quarantined; rollback is a new controlled event; audit is protected and attributable; overlapping scope applies the most restrictive negative outcome.
- `DEC-0026`: authorization is hybrid-role plus server-authoritative contextual scoped policy. Deny by default; UI or cached role is not authority. High-consequence proposal/reviewer/approval separation, privileged step-up/recovery revocation, versioned protected policy, scoped/time-bound delegation, protected audit, quarantine-first file/URL handling, and separate export handling are required. AI may propose, not silently approve.
- `DEC-0027`: release authorities are distinct for mobile binary, web, backend/API, database migration, content/config/emergency, and related artifacts. Promotion uses exact immutable artifacts and provenance/SBOM. Independent verifier/trust roots and a cross-domain compatibility/revocation graph are required. No OTA assumption.
- `DEC-0028`: boundaries should be AI-native, task-addressable, narrow, context-minimal, no-code-simulatable, and bidirectionally traceable.
- `DEC-0029`: the owner is nontechnical; technical implementation and repair are performed by AI and must be translated into outcome, risk, cost, reversibility, and owner action.
- `DEC-0030`: one owner and limited budget. Current price, free path, hard cap, overage, and exit must be verified before approval. Low cost cannot weaken mandatory assurance.
- `DEC-0031`: mobile fixture is equal across comparisons; no provider or ADR is selected in this phase.
- `DEC-0032`: Android first, iOS later; the future non-store planning ceiling is `2,000–3,000 TRY/month`, not spend authorization.
- `DEC-0033`: Flutter is the current working direction with React Native as fallback; this is not a provider or data-backbone decision.

### 2.2 Internal Operations and content requirements that the backbone must not erase

The data layer must preserve, rather than flatten:

- motorcycle identity, model/year/variant and fit applicability;
- claim, source, evidence, actor, review, current status, and applicability as separate dimensions;
- `accepted`, `disputed`, `insufficient evidence`, and `superseded` as distinct states;
- community information versus official guide information;
- withdrawal, correction, transfer, revocation, and deletion without silently rewriting independent history;
- edit versus approval versus publication as separate operations;
- states such as missing/no research, incomplete/evidence pending, conflict/disputed, stale/critical hold, withdrawn, draft/partial, changes requested, approved-not-published, published, partial/failed, superseded, suspended/recalled, historical only, access denied, and unavailable/offline;
- scope, state, reason, owner, evidence, dependencies, and next action across the Internal Operations workspaces and handoffs; and
- published eligibility, variant applicability, version/freshness, provenance/uncertainty, claim versus history, recall/suspension, and safe recovery in consumer-facing output.

The following remain intentionally deferred by the product requirements and must not be smuggled in as settled implementation: data model/database/CMS/search/index/media technology, backend/API/sync/event/release implementation, identity implementation, validation/publication/notification implementation, analytics/retention implementation, and backup/export implementation.

## 3. Primary-source findings

The findings below are mechanism-level observations from official specifications and product documentation. They are evidence for gates and trade-offs, not endorsements.

### 3.1 Relational/PostgreSQL-centric mechanism

PostgreSQL provides an unusually direct fit for facts that must agree in one authoritative transaction: foreign keys, unique constraints, check constraints, and not-null constraints can reject invalid relationships or states at the write boundary. This is valuable for variant applicability, release membership, approval references, object metadata, operation identity, and history links. JSON/JSONB can hold bounded extensible payloads, but JSONB indexing and processing do not replace relational constraints for high-consequence cross-record invariants.

Transaction isolation is a design choice, not a slogan. PostgreSQL's default Read Committed level gives each statement a snapshot; Repeatable Read gives a transaction-stable snapshot; Serializable can fail with a serialization error and requires retry. Therefore an approval/publication operation needs an explicit retry/idempotency policy and must not infer success from a client timeout.

PostgreSQL row-level security can default-deny rows when policies are absent, but table owners, superusers, and roles with `BYPASSRLS` can bypass it. This makes “the database has RLS” insufficient as a complete authorization boundary. A server/API boundary must still own contextual policy, step-up, workflow separation, and audit. Backup and restore jobs also need to account for row-security configuration and privileged roles.

PostgreSQL logical backup is not one mechanism. `pg_dump` produces a consistent logical export and can support selective restore or migration across machines, but it is not a substitute for regular production backup and it does not participate in continuous archiving. Base backup plus archived WAL supports continuous backup and point-in-time recovery, but recovery is cluster-level and introduces archive, retention, restore, and monitoring responsibilities. Logical decoding and logical replication can provide ordered changes, but replication slots retain WAL until consumers advance; a crashed consumer can receive recent changes again; consumers need idempotency and LSN/position tracking; logical decoding does not capture DDL as row changes.

Implication for Kavriva: a relational authority is mechanically well suited to canonical current state and cross-record invariants, while an explicit append-only domain history/provenance model is still required. Relational storage alone does not make a record immutable, tamper-evident, approved, or safe to publish.

### 3.2 Managed relational service mechanism (representative, not a selection)

Managed PostgreSQL services commonly expose standard SQL plus automated backup, snapshot, PITR, replica, or multi-zone features. Official examples document transaction-log shipping and PITR, where a restore creates a new database/server while leaving the source unchanged. This reduces owner-run host maintenance and can make a first recovery drill easier.

The managed boundary also adds risks that must be made explicit:

- backup and restore are control-plane operations with retention, region, identity, quota, and billing dependencies;
- a “successful backup” may not prove that roles, extensions, network policies, object references, private media, audit custody, or application secrets can be restored;
- restore normally produces a new instance/server, so cutover, DNS/API configuration, generation fencing, and client compatibility are separate operations;
- a provider account lock, region incident, quota restriction, or billing suspension can be an application incident even when the database engine is healthy;
- pricing/egress/retention behavior is dynamic and must be checked at the later provider decision, not inferred from a free tier or current table; and
- portability is better when the authoritative data can be exported in standard logical form, but provider-specific extensions, IAM, network policy, object metadata, and operational runbooks still need an exit package.

This option family can reduce day-to-day infrastructure work. It cannot remove the need for an API authority, export manifests, restore drills, audit custody, spending guardrails, and provider-exit tests.

### 3.3 Self-hosted/open-source relational mechanism

An open-source relational engine can avoid a license fee and expose standard data/backup primitives. PostgreSQL's license permits commercial use, but “free software” is not “free operation.” A self-hosted authority requires the owner/AI to maintain host security, patching, disk capacity, encryption, secrets, backup destinations, WAL/archive health, restore tests, monitoring, failover, upgrades, network exposure, and incident recovery.

Self-hosting may improve control over region, versions, extensions, and exit. It also increases the chance that a nontechnical owner is left with a single host, an expired credential, a full disk, an untested backup, or an upgrade that needs expert judgment. A self-hosted candidate is acceptable only if its routine repair and recovery runbooks are automatable, observable, and reversible, and if a real restore test can be executed without relying on one unavailable human.

### 3.4 BaaS and document-oriented mechanism

Document stores optimize for documents/collections and can make client data access and incremental product delivery convenient. Firestore's official model is schemaless collections/documents with nested data and subcollections. Its mobile/web requests are checked by Auth plus Security Rules, while server client libraries use IAM and bypass those rules. Rules are all-or-nothing authorization checks rather than query filters, so the rule/test boundary must be explicit.

Firestore transactions are atomic and retry on concurrent edits, but transactions fail offline. Its mobile SDK offline persistence caches active data and syncs local changes later; concurrent edits to the same document use last-write-wins. Web persistence is not enabled by default and cached data is not automatically cleared. These mechanisms can be useful for low-risk drafts or bounded local use, but they are a poor implicit policy for disputed technical claims, approval, recall, or user history where silent last-write-wins would erase meaningful alternatives.

Firestore export/import and disaster-recovery documentation demonstrates a portability trade-off: managed export requires the billing path and Cloud Storage; exports can include changes made during the export rather than representing a simple exact-start snapshot; import may leave partial updates if cancelled; PITR export covers a restricted time window; and export/import includes service-specific formats and costs. This is not a rejection of BaaS, but it makes “we can export later” an insufficient exit claim.

CouchDB demonstrates a different document/replication model. It is eventually consistent; replication can produce conflicts; revisions form a tree; a deterministic winning revision may be returned while losing revisions remain available for conflict handling. Conflict resolution is application-specific, and the built-in revision tree is not a replacement for domain revision/provenance data. Filtered or partial replicas can help bounded offline distribution, but they do not make a technical claim authoritative.

Implication: BaaS/document stores may be useful as an adjunct for low-risk drafts, community/read models, search-shaped documents, or bounded package distribution. They are not accepted as the sole authority for safety-critical current truth unless they demonstrate explicit invariant enforcement, non-destructive conflict handling, server-authoritative policy, complete export, and tested restore/exit.

### 3.5 Object storage mechanism

Object storage is appropriate for large media, quarantine inputs, immutable release artifacts, backup/export copies, and derived files whose canonical metadata belongs elsewhere. Object keys, versions/generations, checksums, content type, classification, privacy scope, and provenance should be recorded in the authoritative data layer. A raw public URL is not an authorization model.

Official object-lock mechanisms provide useful but bounded protection. S3 Object Lock uses versioning and WORM retention/legal hold; Azure immutable blob storage provides time-based retention and legal holds. Locks can be one-way or difficult to reverse, can affect lifecycle/deletion and billing, and can coexist with delete markers that hide a protected version from the ordinary latest view. Checksums provide integrity evidence; an ETag is not always a content MD5, especially for multipart uploads.

Implication: protected object storage can hold independent evidence or release/export artifacts, but immutable storage is not the same as domain approval, legal retention policy, or user privacy policy. Selective protection, separate private user data, and explicit deletion/retention rules are required.

### 3.6 Append-only audit and provenance mechanism

The W3C PROV family provides a technology-neutral vocabulary for entities, activities, and agents, with relations and time that can represent how an entity was generated, transformed, reviewed, or attributed. It is a useful semantic basis for Kavriva provenance without forcing an RDF/graph implementation.

A useful provenance minimum is:

- `entity`: source, evidence, claim, content version, derived artifact, release manifest, object version, export, or recovery record;
- `activity`: ingest, parse, transform, review, approve, publish, suspend, recall, restore, export, or delete request;
- `agent`: owner, reviewer, contributor, service identity, AI run, or independent verifier;
- relation/time: used, generated-by, attributed-to, supersedes, invalidates, derived-from, applicable-to, and observed-at;
- integrity: canonical representation, digest, parent/previous event, operation identity, and protected custody location.

An insert-only table in the same mutable database is useful but is not, by itself, tamper evidence. A privileged database operator can alter it; a bad restore can fork or lose its sequence; a provider account can be compromised. High-consequence actions therefore need protected audit custody and a recovery/checkpoint strategy separate enough to detect or resist common failures. A WORM object copy can help, but it must not make private personal data undeletable by accident.

### 3.7 CDC, outbox, and event-log mechanism

PostgreSQL WAL/logical decoding, Debezium, and Kafka illustrate three distinct concepts that are often conflated:

1. database change capture observes committed database changes;
2. an outbox records an application event in the same transaction as the business mutation;
3. an event log/broker transports and retains events for independent consumers.

The outbox pattern is valuable where a canonical mutation and an async notification/projection must not diverge: the business row and an insert-only outbox row commit together, then a relay publishes the outbox event. Event identity supports deduplication; aggregate identity can preserve per-aggregate order. A relay outage leaves an observable pending event rather than inventing a second authority.

CDC connectors need a dedicated least-privilege replication identity, a unique slot, LSN/offset monitoring, retention controls, and idempotent consumers. A slot that stops advancing can retain WAL and fill storage. A lost slot, incompatible upgrade, or unmonitored history gap can cause missed changes. DDL/schema changes need a separate compatibility plan. Change streams may expose a current full document that differs from the value at the event time, so consumers must not infer historical truth from a later lookup.

Kafka's official design documents describe at-least-once processing as the default. Idempotent producers and transactions help, but exactly-once behavior across an external database/API requires cooperation and atomic coordination with the destination. Partition keys give per-partition ordering, not a universal global order. Consumers can duplicate work, lag, reorder across keys, or need dead-letter/replay handling.

Implication: outbox/CDC/event infrastructure can be introduced when a concrete async need exists (search projection, notification, analytics, package distribution, or integration). It must not be the authority for approval, publication, recall, authorization, or current safety eligibility. A broker is an adjunct and a failure surface, not a replacement for committed canonical state.

### 3.8 API boundary mechanism

An API boundary is a logical authority even if the first implementation is a small service. Mobile and browser clients should never write the canonical database or object store directly. The server must re-evaluate authorization, scope, policy version, content/release generation, and compatibility at commit time.

HTTP conditional requests provide a standard optimistic-concurrency mechanism: a strong ETag with `If-Match` can prevent lost updates, with a failed precondition returning without applying the method. This is a useful base for owner edits, review transitions, package acknowledgements, and user-history updates. It does not solve semantic conflicts by itself; a `409 Conflict` or typed domain problem may still be required.

RFC 9457 Problem Details provides machine-readable error shapes with a type, status, title/detail, instance, and extension members. The detail should help correct the request without exposing internal secrets. OpenAPI and JSON Schema can describe request/response shape, but a schema does not prove authorization, current policy, transition validity, or semantic safety.

The API contract should make the following explicit:

- operation identity/idempotency key and safe replay behavior;
- requested versus accepted versus committed versus partially completed versus outcome-unknown state;
- current authoritative version/generation and the client precondition used;
- separate current-state, history/provenance, release-eligibility, and delivery-observation representations;
- typed denial, stale, conflict, dependency, recall, and unavailable errors;
- private object handles or signed access, never raw public canonical links for sensitive media;
- server-side policy/role evaluation, including step-up and high-consequence separation; and
- no success response until the authoritative operation has a durable status, or an explicit outcome-unknown result when the response path failed after submission.

### 3.9 Offline, delta, and package mechanism

SQLite's Online Backup API can make an incremental bitwise snapshot while the source remains usable. SQLite WAL is part of the live database state and must travel with the main database; separating the database and `-wal` file can lose committed transactions or corrupt the copy. A local cache therefore needs atomic package boundaries, integrity checks, and recovery/rebuild behavior.

SQLite session changesets and patchsets can represent local deltas. Patchsets are smaller but provide less conflict detail; changeset application can encounter duplicate primary keys, missing rows, mismatched old values, or constraints, and conflict handlers can omit, replace, or abort. These primitives enable a sync mechanism; they do not create an automatic safe merge policy.

Kavriva's bounded offline package should be treated as a signed/versioned delivery artifact, not a second authority. It needs:

- selected motorcycle/task scope;
- a compact safety core and explicit optional media;
- package schema/client compatibility, content/release generation, base generation, and creation/expiry information;
- per-artifact digest and provenance reference;
- atomic install and atomic delta apply only when the base matches;
- safe fallback to a fresh compact package when a delta is missing, stale, incompatible, partially downloaded, or corrupted;
- a distinction between teaching/history/provenance and current application eligibility;
- recall/suspension check and online revalidation before high-consequence actions; and
- a bounded cache policy, cleanup, deduplication, and no large default cellular download.

The local store can record drafts and observations. It cannot grant positive authority to an unreviewed, recalled, stale, restored, or unknown-state item. Critical offline paths should fail closed while retaining safe stop/recovery instructions.

### 3.10 Backup, PITR, export, restore, and provider-exit mechanism

Backups serve different purposes and should not be collapsed into one checkbox:

- logical export supports migration, inspection, selective restore, and provider exit;
- filesystem/base snapshots support faster full restore but can be engine/platform/configuration specific;
- WAL/continuous archiving supports point-in-time recovery but requires archive health, retention, and replay testing;
- object copies protect media, release artifacts, and evidence but need version/generation/digest manifests;
- audit/provenance copies preserve attribution and sequence/checkpoints; and
- client/package caches are delivery copies, not backups of canonical truth.

PostgreSQL documentation states that WAL plus a base backup enables PITR and warm standby, while `pg_dump` is a logical consistent export and not a continuous-archiving component. Managed relational and document/BaaS documentation similarly shows that restore often creates a new resource, that export/import can have service-specific formats or billing prerequisites, and that a run can observe changes while it is in progress. Therefore a tested exit package must include a completeness manifest, export generation/time, schema/version, data, object inventory, digests, roles/policy mapping, audit/provenance, configuration, and import/reconciliation results.

Restore must be quarantined before becoming authoritative. The restored state may contain an old recall, revoked role, stale policy, incompatible release, or an operation already accepted by the current system. Recovery needs a new restore generation, revalidation of revocations/policy/release compatibility, API cutover fencing, and an audit record. A rollback is a new controlled event; it is not a silent rewrite of the past.

## 4. Technology-neutral logical boundary model

The following boundaries are logical ownership and authority boundaries. They do not require separate services, databases, or repositories in the first release. Splitting them prematurely would add operational failure modes without proving a product need.

| Boundary | Owns / represents | Must not be confused with |
|---|---|---|
| B1. Canonical product/data authority | Motorcycle/variant identity, canonical claims, applicability, current content state, release eligibility, invariant links | Search index, cache, client copy, event log, or historical observation |
| B2. User/private/history authority | User-owned history, observations, drafts, preferences, private media references, consent/privacy state | Official technical truth or anonymous aggregate analytics |
| B3. Workflow/review/release authority | Proposal, evidence review, approval, publication, suspension, recall, recovery, role/delegation transitions | A UI badge, current row alone, or a client-cached role |
| B4. Media/evidence/object authority | Original uploads, quarantined files, derivatives, release artifacts, backup/export objects, object version/generation/digest | Relational joins, public URLs, or approval meaning |
| B5. Audit/provenance authority | Attributable operations, entity/activity/agent relations, policy/release generations, protected checkpoints and custody | Mutable application status, a provider log, or a timestamp without actor/operation |
| B6. API/authz/policy boundary | Server-side authorization, contextual policy, optimistic concurrency, idempotency, typed outcomes, private object access | Direct database/SDK access from clients or UI visibility |
| B7. Offline package/cache/sync boundary | Selected compact package, local draft, base/delta, digest, compatibility, freshness, safe recovery, apply status | Positive authority, global current truth, or silent conflict winner |
| B8. Async integration/read-model boundary | Outbox, CDC, projections, search, notifications, analytics, metrics, package delivery queues | Approval/publication/recall commit or authoritative current eligibility |
| B9. Backup/restore/export/exit trust boundary | Recovery generations, export manifests, import checks, provider-independent fixtures, exit/cutover proof | A backup file existing, a successful snapshot job, or a restored DB becoming trusted automatically |

### 4.1 What must be atomic versus what may be eventual

| Concern | Required consistency posture | Reason |
|---|---|---|
| Canonical mutation plus operation identity/idempotency record | Atomic at authority | A timeout must not create an unknown duplicate or two different outcomes |
| Approval plus exact immutable consumer meaning, inputs, dependencies, and audit intent | Atomic or one guarded authoritative transition | Approval must bind what consumers will receive |
| Publication/suspension/recall plus release generation/manifest and audit | Atomic guarded transition | A consumer must not see a manifest that lacks its eligibility/revocation meaning |
| User history event plus attribution and privacy scope | Atomic at the owning authority | History must not disappear or be misattributed because an async relay failed |
| Local package/delta installation | Atomic locally | No mixed base/new package or partially installed safety core |
| Search/read projections | Eventual with freshness and rebuild status | A lagging index must be visible and cannot grant authority |
| Notifications and analytics | Eventual, idempotent, replayable | They should not decide whether a release or recall committed |
| Media derivatives/CDN/package distribution | Eventual with object digest/version checks | Delivery can lag while canonical metadata remains authoritative |
| CDC/outbox relay | Eventual with pending/failed/dead-letter state | Core transaction survives relay downtime; consumers reconcile |
| Restore/export completion | Explicitly staged, never silently trusted | A restore or export can be technically complete but semantically incomplete |

### 4.2 Non-silent invariants

The following must produce an explicit conflict, hold, denial, or outcome-unknown state rather than choosing a convenient winner:

- two edits to the same high-consequence content;
- claim/source/evidence conflict;
- a recalled or superseded package used after its last valid check;
- a delta whose base generation does not match;
- a restore that includes an older role, policy, release, or recall state;
- an export missing an object, audit segment, role/policy mapping, or private-data scope;
- an audit/provenance sink unavailable for an approval, publication, recall, or role mutation;
- an outbox/CDC event duplicated, delayed, reordered, or missing a known LSN/offset;
- an object digest/version mismatch or delete marker hiding the latest protected version; and
- an API response lost after the authority may have committed.

## 5. Option-family comparison

| Option family | Mechanism/strength | Kavriva fit | Main failure/operation cost | Exit shape | Phase-4 posture |
|---|---|---|---|---|---|
| Managed relational / PostgreSQL-centric | Constraints, transactions, standard SQL, logical export, WAL/PITR, optional replicas | Strong candidate shape for canonical invariants and current state | Control-plane/account/region/billing dependency; restore/cutover; extension/role/object export; managed pricing and quotas | SQL/logical export plus object/audit manifests; test import outside provider | Keep as leading investigation family; no vendor or final engine decision |
| Self-hosted/open-source relational | Maximum host/version/region control; no engine license fee; standard primitives | Can fit canonical authority if AI-operable and independently recoverable | Patching, security, backups, storage, HA, monitoring, restore, single-host risk, expert dependency | Standard logical dumps and filesystem/WAL artifacts, but runbook/secrets/network still need migration | Accept only with automated operations and real restore/exit proof |
| Backend-as-a-service | Fast auth/client integration, managed data/backup, rules, SDKs, mobile sync features | Useful for low-risk adjuncts and delivery convenience | Server SDK/admin bypass, opaque rule boundary, offline LWW/transaction limits, quota/billing, service-specific export | Must export data, rules/config, auth mapping, audit, object/media and provenance; test independent import | Do not grant sole authority without closing all invariant/audit/exit gates |
| Document/replication store | Flexible documents, partial replicas, eventual replication, conflict revisions | Possible community/read model, drafts, bounded package distribution | Winner/last-write semantics, conflict resolution, indexes/queries, eventual staleness, domain revision loss | Export must preserve losing revisions, conflict metadata, attachments and policy | Adjunct only until non-destructive conflict and exit are proven |
| Event log/broker | Durable ordered partitions, replay, decoupled consumers, async scale | Outbox relay, notifications, projections, analytics, package delivery | At-least-once duplicates, lag, ordering scope, retention, schema evolution, replay/DLQ operations | Topic/event schema/offset/retention plus canonical source; cannot be only exit artifact | Defer until a concrete async need; never approval authority |
| Object storage | Large blobs, versioning, checksums, WORM/legal hold, cheap independent copies | Strong for media, evidence, quarantined originals, artifacts, exports | Public URL leakage, delete markers, retention/privacy conflict, version/lifecycle/egress cost, metadata drift | Version/generation/digest inventory and object export; map back to canonical records | Use as media/evidence/backup boundary, not relational authority |
| Append-only audit/provenance custody | Attributable entity/activity/agent history, protected checkpoints, independent evidence | Mandatory for high-consequence operations and release meaning | Storage/retention/custody, tamper detection, replay/checkpoint, deletion/privacy tension | Independent audit/export with digests, sequence/checkpoints and custody evidence | Mandatory logical boundary; physical implementation remains open |
| Local SQLite/package/delta | Small local cache, atomic local snapshot, changesets/patchsets, offline drafts | Good for bounded selected-task offline and local history staging | WAL/copy corruption, stale/recalled data, delta base mismatch, conflict semantics, device loss/privacy | Rebuild from server package; export local unsynced drafts intentionally | Use as bounded delivery/cache boundary, never positive authority |
| Direct client-to-DB/object/SDK writes | Low initial API code and fast SDK paths | Unsafe for canonical/high-consequence writes | Bypass policy/audit, stale role, overbroad credentials, RLS/admin mismatch, schema coupling | Hard to reproduce/export authorization and operation history | Reject as a general boundary; clients use server API |

### 5.1 Working shape indicated by the evidence (not an approval)

The evidence currently points to a conservative shape for the next debate/ADR stage:

1. one canonical transactional authority for cross-record invariants and current state;
2. server/API-mediated reads and writes, with no direct client database/object authority;
3. explicit current state plus append-only domain history/audit/provenance; event sourcing is not required;
4. object storage for media, quarantined evidence, release artifacts, backup/export copies, and private blobs, with object version/generation/digest in canonical metadata;
5. a bounded local store/package for selected motorcycle/task use, with compact safety closure, compatibility, generation/digest, atomic apply, and full-package fallback;
6. outbox/CDC only for concrete projections, notification, analytics, or integration needs;
7. document/event/BaaS facilities, if later used, as adjuncts with explicit freshness/conflict semantics; and
8. restore/export/exit states quarantined until generation, policy, revocation, compatibility, object, and audit checks pass.

The shape is intentionally provider-neutral and may still be rejected by a later ADR if owner decisions, workload evidence, or restore/exit tests do not support it.

## 6. Acceptance and rejection rules

### 6.1 Mandatory gates for any candidate family

**A. Semantic losslessness.** The candidate must preserve fit/applicability, source/evidence, uncertainty, review, approval, publication, version, recall, supersession, current versus historical meaning, and user/private boundaries without flattening them into one status or winner.

**B. Invariant closure.** High-consequence state transitions must be rejected or held when required related records, policy generation, object digests, compatibility, or operation identity are missing. A client, cache, replica, or event consumer cannot create positive authority.

**C. Server authority.** Every canonical/high-consequence write must pass server-side authorization and current policy at commit time, with idempotency, optimistic concurrency or explicit conflict, typed outcome, and protected attribution. Direct DB/SDK client writes are rejected for these paths.

**D. Bounded offline.** Offline content must be scoped, compact, integrity-checked, versioned, compatible, recall-aware, and atomically applied. Unknown/stale/recalled/ambiguous critical state fails closed while safe stop/recovery remains available.

**E. Audit/provenance.** Approval, publication, suspension, recall, role/delegation, restore, export, and deletion-sensitive actions must produce attributable history that cannot be silently rewritten. High-consequence audit requires protected custody or a demonstrable tamper-detection strategy.

**F. Media/privacy.** Media and evidence need private access, quarantine, classification, digest/version, retention/deletion policy, and provenance. Object lock/WORM must be selective and must not silently conflict with user deletion/privacy obligations.

**G. Recovery/exit.** The candidate must support a documented export and restore drill, including canonical data, object inventory, audit/provenance, roles/policy mapping, schema/configuration, secrets-handling boundaries, and reconciliation. A backup that has never been restored is not evidence of recovery.

**H. AI operability and cost control.** Routine operation, monitoring, repair, and restoration must be describable in narrow AI-run tasks with observable results and an owner escalation path. Dynamic price, quota, overage, egress, minimum-bill, and region/tax behavior must be verified at the eventual decision; open-source or free-tier wording is not a cost guarantee.

### 6.2 Family-specific acceptance/rejection gates

- **Managed relational:** accept only if standard logical export and a provider-independent restore path are demonstrated; PITR/backup retention, roles/extensions/network assumptions, object copies, audit custody, quota, account recovery, and spend/overage controls are explicit. Reject if a critical semantic depends on an opaque proprietary feature with no exit fixture.
- **Self-hosted/open-source:** accept only if patching, monitoring, encrypted backup, restore, disk/credential recovery, and cutover can be AI-operated and tested, with no single-human/single-host dependency. Reject if “the owner can SSH and fix it” is the recovery plan.
- **BaaS:** accept only when high-consequence writes are server-mediated; rules/admin SDK paths are tested; offline conflicts are not used for critical truth; complete export includes data/config/auth/audit/media; and quotas/billing/exit are known. Reject if client rule state or an admin SDK bypass is mistaken for the application authority.
- **Document/replication store:** accept as an adjunct only if conflicts, losing revisions, partial replicas, stale state, and domain history are explicit and queryable. Reject sole authority when deterministic winner or LWW can hide disputed technical truth, approval, or recall.
- **Event broker/CDC:** accept only for async consumers with idempotency, ordering key, offset/LSN, lag/retention monitoring, replay/DLQ, and schema evolution. Reject use as the approval/publication/recall authority or as the only backup.
- **Object storage:** accept for blobs/evidence/export/artifacts when private access, version/generation, checksum, quarantine, lifecycle, and deletion/retention policy exist. Reject mutable public links, unverified multipart integrity, or object metadata used as the only domain status.
- **Append-only audit/provenance:** accept when operation identity, actor/service, policy/release generation, causal links, digest/checkpoint, and protected custody are recorded. Reject “a mutable audit table” as sufficient tamper evidence for high-consequence decisions.
- **Local package/delta:** accept when base generation/digest, client compatibility, atomic installation, package size/classification, stale/recall hold, and full-package recovery are explicit. Reject automatic full-library download, silent mixed-version apply, or LWW for critical conflicts.
- **Direct client access:** reject as a general model because credentials, policy, audit, schema, and operation semantics cannot be safely controlled by a client or cached role.

## 7. No-code failure-mode matrix

| Failure mode | Required system behavior | Must not happen | Recovery/audit evidence |
|---|---|---|---|
| Canonical authority unavailable | Serve only explicitly safe cached/recovery content; hold high-consequence writes; show unavailable state | Treat cache/replica as current authority | Availability event, held operation, last valid generation and revalidation result |
| Network timeout after a write may have committed | Return outcome-unknown; reconcile by same operation identity/idempotency key | Blind retry that creates a duplicate approval/history event | Operation status, request identity, authoritative result, client reconciliation |
| Replica/index is behind | Mark freshness/lag; route high-consequence decision to authority | Approve/publish/recall from stale projection | Observed generation/LSN and stale-read reason |
| Role/policy changes after page load | Re-authorize and re-check policy at commit; deny/hold if changed | Trust cached UI role or old permission | Actor, policy version, step-up result, denial reason |
| Concurrent edit to approved/high-consequence item | ETag/version precondition fails; preserve both inputs; open conflict/review | Last-write-wins overwrite of disputed meaning | Parent version, attempted patch, conflict record, reviewer action |
| Partial schema/migration rollout | Explicit migration compatibility state; block incompatible writes/reads; keep rollback/cutover guard | Mixed clients silently write incompatible shape | Migration artifact, compatibility matrix, affected operations |
| Provider outage/account lock/quota | Hold writes, retain bounded safe cache, activate incident/recovery path | Retry unboundedly or claim successful publication | Provider/tenant incident, retry budget, owner escalation, cutover generation |
| PITR restore contains old recall/revocation/policy | Quarantine restored authority; recheck current revocations/policy/releases before cutover | Restore old state directly and re-enable unsafe content | Restore generation, source time, quarantine checks, current-state merge/reconciliation |
| Backup restores data but not roles/extensions/network/object access | Mark restore incomplete; do not cut over; repair missing dependencies | Equate “backup job succeeded” with application recovery | Restore checklist, dependency inventory, failed gate, owner decision |
| Export omits audit, ACL, roles, objects, or private-data scope | Fail completeness manifest; preserve missing list; block exit/cutover | Ship a partial export as a complete exit package | Export manifest/digests, item counts, missing categories, import test |
| Object version/digest mismatch or delete marker hides latest version | Quarantine object; resolve by manifest/version; use safe fallback | Show an object based on mutable/latest URL alone | Object key/version/generation, checksum, quarantine decision |
| Audit/provenance sink unavailable | Hold approval/publication/recall/role mutation; optionally buffer only low-risk events | Confirm high-consequence transition without protected attribution | Sink health, held operation, buffer identity, eventual reconciliation |
| CDC slot lag/WAL bloat/slot loss/duplicate | Alert, throttle or rebuild consumer; dedupe by event/LSN; verify gap | Allow silent storage exhaustion or missed event | Slot/LSN metrics, retention, gap check, rebuild/replay evidence |
| DDL not represented in CDC | Treat schema migration as separate release/compatibility event | Assume row stream proves schema compatibility | Migration artifact, consumer version, compatibility gate |
| Outbox committed but relay down | Keep canonical mutation committed; expose pending relay state; retry idempotently | Roll back canonical truth because notification failed | Outbox event ID, relay attempts, last delivery, DLQ/replay status |
| Event duplicate/out-of-order/consumer crash | Idempotent consumer and per-aggregate ordering; replay/DLQ | Send duplicate notification or overwrite projection with older state | Event ID, aggregate key, offset, consumer state, replay result |
| Local SQLite/WAL separated or corrupted | Rebuild cache/package; preserve unsynced drafts for explicit reconciliation where possible | Treat corrupted local snapshot as authority | Package checksum, local recovery result, unsynced draft/export, user-visible hold |
| Delta base mismatch or partial package | Atomically reject delta; fetch full compact package; keep previous valid package | Apply mixed generations or partial safety core | Base/new generation, digest, apply status, fallback package |
| Recall arrives while client is offline | Keep safe stop/recovery; mark eligibility unknown/stale; recheck online before high-consequence action | Promise immediate recall propagation offline | Last recall check, package generation, online revalidation result |
| BaaS admin/server SDK bypasses client rules | Force all high-consequence operations through server policy/API; test admin paths | Assume mobile/web rules protect server-side code | Auth path, rule test, server policy decision, audit actor |
| Document-store conflict has a deterministic winner | Expose disputed/unresolved state; retain both revisions; require review | Treat winning revision as verified technical truth | Conflict IDs, revisions, reviewer resolution, supersession chain |
| Heavy media auto-downloads on cellular | Require size class/consent/optional fetch; keep compact core usable | Download full library by default | Package size, media class, network policy, user action |
| Privacy/deletion request meets audit/cache/backup copy | Apply explicit retention/minimization policy; separate immutable evidence from private payload | Leave personal data in public links, caches, exports, or indefinite backups unintentionally | Deletion scope, legal/owner basis, affected copies, exceptions and expiry |
| Provider API/SDK deprecated or changes semantics | Contract tests, pinned fixtures, adapter boundary, export rehearsal | Allow silent semantic drift in approval/recall/sync | Version, fixture result, migration decision, rollback/cutover record |

## 8. Cost and operations categories

No numeric provider price is asserted here. The later selection must verify current official pricing and billing terms for the chosen region, currency, tax treatment, minimum bill, free path, hard cap, overage, storage, egress, backups, logs, and support.

| Category | Cost/operation drivers | Kavriva guardrail or question |
|---|---|---|
| Canonical DB compute/storage/connections | Baseline instance, IOPS, storage growth, connection pooling, idle minimums | Measure initial records, writes, reads, concurrent Internal Operations users, and connection shape |
| Backup/PITR/WAL/replica/geo | Retention, archive volume, restore staging, replicas, cross-region copies, WAL lag | Define RPO/RTO and which data requires PITR versus logical export |
| Object bytes/versions/retention/egress | Original media, derivatives, old versions, WORM/legal holds, downloads, transfer | Keep media optional/on-demand; version only evidence/artifacts that need it; model deletion/retention |
| BaaS read/write/delete/op quotas | Per-operation pricing, indexes, listeners, offline cache, export/restore billing prerequisites | Never infer total cost from a free quota; set alerts/kill-switches and verify owner billing authority |
| API/compute/egress/CDN | Requests, runtime, authentication, signed URLs, package distribution, cache misses | Keep authority API small and observable; do not let delivery copies bypass policy |
| CDC/connector/event retention | Connector runtime, slot/WAL retention, broker partitions, event bytes, retention/replay, DLQ | Defer until a concrete async consumer is needed; monitor lag and storage |
| Audit/provenance custody | Append-only volume, protected copies, digests/checkpoints, retention, retrieval, independent storage | Decide what must be immutable, what is erasable, and what can be independently verified |
| Monitoring/alerts/logs | Metrics retention, error traces, audit logs, alert delivery, on-call/escalation | Monitor backup freshness, restore tests, lag, disk, quotas, object drift, auth failures, and spend |
| Identity/auth/recovery | User auth, admin step-up, email/SMS/SMTP, recovery, key rotation, account lock | Keep recovery independent enough to avoid one account/credential becoming the only path |
| Restore/exit drills and AI work | Staging resources, test imports, fixtures, runbook execution, failed drills, review/support | Budget recurring drills; a written backup policy without a restore result is incomplete |
| FX/tax/minimum/overage/support | Currency movement, tax, regional availability, minimum charges, provider support tiers | Treat `2,000–3,000 TRY/month` as planning ceiling; no approval without current official terms |

### 8.1 Staging

**Mandatory before real user data or high-consequence release:** canonical authority, API/authz/policy boundary, encryption and private-access boundaries, data minimization, backup plus logical export, a real restore test, protected audit/provenance, private media/quarantine where media exists, monitoring/alerts, deletion/export procedure, and outcome-unknown/idempotency behavior.

**Deferrable until evidence requires it:** multi-region HA, extra replicas, extended PITR retention, search index, CDC/event broker, heavy media CDN/derivative pipeline, WORM archive for every object, advanced analytics, and complex conflict-free replicated data types.

**Optional convenience, not assurance:** BaaS SDK shortcuts, premium dashboards, automated image variants, full-text search, rich push notification fan-out, and broad offline library caching.

**Scale-triggered:** read replicas/partitioning, event broker, multi-region, dedicated audit retention, larger object/CDN plan, workload-specific indexing, and a separate integration boundary should be introduced only when measurements or a safety/reliability requirement justify them.

## 9. Owner decisions and unresolved questions

These are intentionally not answered by this research:

1. Which records, evidence, release artifacts, and audit events must be independently immutable, and which private/user records must remain erasable or minimized? What retention/deletion policy and legal review apply in the operating jurisdictions?
2. What are the numeric offline classes, freshness windows, package size limits, cellular behavior, cache retention, and recall/revalidation rules for each risk tier?
3. What RPO/RTO is acceptable for canonical data, user history, media, audit/provenance, and unsynced offline drafts? How much loss is acceptable after device loss or provider incident?
4. Is a separate independent audit/provenance custody required from the first user, only at publication/recall, or after a scale/risk trigger? Who can review it independently?
5. What initial and expected 12-month volumes are plausible for users, motorcycles, claims, attachments, private media, release packages, reads/writes, exports, and egress?
6. Does the `2,000–3,000 TRY/month` planning ceiling include taxes, FX movement, backups, object egress, email/SMS, support, monitoring, restore drills, and emergency overage? Is a hard kill-switch required, and what must remain available when it trips?
7. Who owns provider accounts, domain/DNS, signing keys, recovery factors, billing, export encryption keys, and emergency access? What happens if the owner loses access?
8. What provider portability level is required: standard SQL/data only, independently runnable restore, or a complete semantic exit including policy, audit, release manifests, media, and user identity mapping? How often must exit be rehearsed?
9. Is BaaS convenience worth accepting a service-specific rules/export/offline model, or is a narrower API-controlled relational core more important even if initial delivery is slower?
10. At what measured workload or product requirement does search, analytics, CDC, event delivery, or a document/read model become necessary rather than optional?
11. What is the owner-approved independent reviewer/recovery contact when the AI cannot safely resolve an approval, conflict, restore, billing, legal-retention, or identity incident?
12. How should backups, caches, logs, exports, object versions, and offline packages respond to a user deletion or privacy request, and what documented exceptions/expiry are acceptable?
13. What exact API contract is wanted for idempotency key, operation status, ETag/version, patch/conflict format, typed Problem Details, and client reconciliation UX?
14. Is temporary self-hosting acceptable if it reduces provider lock-in but increases patching/restore responsibility, or must the first operating shape minimize owner-run infrastructure even at the cost of managed-service dependence?

## 10. Phase-4 conclusion (no final selection)

The primary-source evidence favors a clear separation of concerns rather than one “magic” backend:

- a transactional authority is needed for current truth, cross-record invariants, approval/publication/recall transitions, and attributable user history;
- an API/policy boundary is needed even when the underlying engine has rules or row security;
- media/evidence/export copies belong in an object boundary with private access, version/generation, digest, quarantine, and explicit retention;
- audit/provenance needs an explicit vocabulary and protected custody, not merely mutable timestamps or a hidden provider log;
- local offline data is a bounded delivery/cache/draft boundary with compatibility and safe recovery, not a positive authority;
- outbox/CDC/event infrastructure is useful only for explicit asynchronous consumers and needs idempotent, replayable, observable semantics; and
- backup, PITR, restore, export, and exit are trust transitions that require manifests, drills, quarantine, and reconciliation.

The most plausible next-stage working shape is therefore a provider-neutral canonical transactional core plus API authority, object/media boundary, protected audit/provenance, and bounded offline package. A relational/PostgreSQL-centric family is a leading research hypothesis because its constraints, transactions, logical export, and WAL/PITR mechanisms map well to the required invariants, but this is not a final engine/provider decision. BaaS, document stores, event brokers, and self-hosted alternatives remain eligible only if they pass the gates above and satisfy owner decisions about cost, operation, recovery, privacy, and exit.

No provider, framework, schema, deployment, paid plan, or ADR is approved by this document.

## 11. Official primary-source inventory

Accessed/checked for this research on `2026-09-18`. Links are official specifications or first-party documentation; marketing pages and secondary comparisons are intentionally excluded.

### PostgreSQL

- [Transaction isolation](https://www.postgresql.org/docs/18/transaction-iso.html)
- [Constraints](https://www.postgresql.org/docs/18/ddl-constraints.html)
- [JSON types](https://www.postgresql.org/docs/18/datatype-json.html)
- [Backup and restore overview](https://www.postgresql.org/docs/18/backup.html)
- [Continuous archiving and PITR](https://www.postgresql.org/docs/18/continuous-archiving.html)
- [pg_dump](https://www.postgresql.org/docs/18/app-pgdump.html)
- [Logical decoding explanation](https://www.postgresql.org/docs/18/logicaldecoding-explanation.html)
- [Logical replication](https://www.postgresql.org/docs/18/logical-replication.html)
- [Row-level security](https://www.postgresql.org/docs/18/ddl-rowsecurity.html)
- [Role attributes and superuser privileges](https://www.postgresql.org/docs/18/role-attributes.html)
- [Monitoring statistics](https://www.postgresql.org/docs/18/monitoring-stats.html)
- [PostgreSQL license](https://www.postgresql.org/about/licence/)

### Representative managed relational mechanisms (not recommendations)

- [Amazon RDS for PostgreSQL PITR](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIT.html)
- [Amazon RDS for PostgreSQL](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_PostgreSQL.html)
- [Azure Database for PostgreSQL backup/restore concepts](https://learn.microsoft.com/en-au/azure/postgresql/backup-restore/concepts-backup-restore)
- [Azure PostgreSQL full-backup restore](https://learn.microsoft.com/en-us/azure/postgresql/backup-restore/how-to-restore-full-backup)

### SQLite and local delta mechanisms

- [SQLite Online Backup API](https://sqlite.org/backup.html)
- [SQLite WAL](https://www.sqlite.org/wal.html)
- [SQLite transactions](https://www.sqlite.org/lang_transaction.html)
- [SQLite session extension](https://www.sqlite.org/sessionintro.html)
- [SQLite changesets and conflict handling](https://www.sqlite.org/session.html)

### Firestore/BaaS mechanisms

- [Firestore data model](https://firebase.google.com/docs/firestore/data-model)
- [Firestore security overview](https://firebase.google.com/docs/firestore/security/overview)
- [Firestore server libraries and IAM](https://firebase.google.com/docs/firestore/security/rules-fields)
- [Firestore Rules testing](https://firebase.google.com/docs/firestore/security/test-rules-emulator)
- [Firestore transactions](https://firebase.google.com/docs/firestore/manage-data/transactions)
- [Firestore offline data](https://firebase.google.com/docs/firestore/enterprise/enable-offline)
- [Firestore quotas and limits](https://firebase.google.com/docs/firestore/quotas)
- [Firestore export/import](https://firebase.google.com/docs/firestore/manage-data/export-import)
- [Firestore disaster recovery](https://firebase.google.com/docs/firestore/disaster-recovery)

### CouchDB document/replication mechanisms

- [CouchDB consistency and conflicts](https://docs.couchdb.org/en/stable/intro/consistency.html)
- [CouchDB conflict handling](https://docs.couchdb.org/en/stable/replication/conflicts.html)
- [CouchDB overview](https://docs.couchdb.org/en/stable/intro/overview.html)
- [CouchDB replication](https://docs.couchdb.org/en/stable/replication/intro.html)

### Object storage and integrity mechanisms

- [Amazon S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html)
- [Amazon S3 Object Lock management](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-managing.html)
- [Amazon S3 versioning](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html)
- [Amazon S3 object integrity checks](https://docs.aws.amazon.com/AmazonS3/latest/userguide/checking-object-integrity-upload.html)
- [Amazon S3 multipart upload](https://docs.aws.amazon.com/AmazonS3/latest/userguide/mpuoverview.html)
- [Azure immutable blob storage overview](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview)
- [Azure version-level WORM policies](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-version-level-worm-policies)
- [Azure secure blobs](https://learn.microsoft.com/en-us/azure/storage/blobs/secure-blobs)

### CDC, outbox, and event-log mechanisms

- [Debezium PostgreSQL connector](https://debezium.io/documentation/reference/stable/connectors/postgresql.html)
- [Debezium outbox event router](https://debezium.io/documentation/reference/stable/transformations/outbox-event-router.html)
- [Apache Kafka design](https://kafka.apache.org/40/design/design/)
- [Apache Kafka introduction](https://kafka.apache.org/intro/)

### API and contract mechanisms

- [HTTP Semantics, including conditional requests](https://www.rfc-editor.org/rfc/rfc9110.html)
- [HTTP Problem Details](https://www.rfc-editor.org/rfc/rfc9457.html)
- [OpenAPI Specification](https://spec.openapis.org/oas/)
- [JSON Schema Specification](https://json-schema.org/specification)

### Provenance, privacy, and deletion mechanisms

- [W3C PROV-O](https://www.w3.org/TR/prov-o/)
- [W3C PROV-DM](https://www.w3.org/TR/prov-dm/)
- [W3C PROV constraints](https://www.w3.org/TR/prov-constraints/)
- [NIST Privacy Framework](https://www.nist.gov/privacy-framework)
- [NIST data minimization glossary](https://csrc.nist.gov/glossary/term/minimization)
- [Turkish KVKK regulation on deletion, destruction, or anonymization](https://www.kvkk.gov.tr/Icerik/5441/KISISEL-VERILERIN-SILINMESI-YOK-EDILMESI-VEYA-ANONIM-HALE-GETIRILMESI-HAKKINDA-YONETMELIK)
