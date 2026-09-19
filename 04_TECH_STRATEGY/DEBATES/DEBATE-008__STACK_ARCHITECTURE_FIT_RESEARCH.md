# DEBATE-008 — Stack Architecture Fit Research

Status: `RESEARCH DRAFT — PHASE-4 / NO-CODE / NO WINNER / ADR NOT READY`
Date: 2026-09-18
Scope: Approved logical data backbone against concrete stack families
Planning constraint: No application code, prototype, executable spike, provider selection or purchase

## 1. Decision question

Which stack families can carry the user-approved `DEC-0034` logical data backbone without silently turning a
client SDK, cache, database row, object URL, provider log, backup or AI task into authority?

This document compares mechanisms and failure behavior for:

1. integrated BaaS (`Supabase-like`);
2. Firebase/Firestore;
3. managed relational database + independent API + object storage;
4. Appwrite;
5. edge SQLite/Workers family;
6. self-host baseline.

It does not select a winner. A family can be a fit only as a bounded composition of planes and controls; a product
feature list, a green demo, a vendor SLA, a free tier or a successful backup job is not acceptance evidence.

## 2. Binding context and non-decisions

This research carries forward, without reopening, the following approved working directions:

- `DEC-0023` / `DEC-0024`: offline delivery is selected-motorcycle/task scoped, data-efficient, risk-tiered and
  bounded; compact safety/application/safe-stop/recovery closure is mandatory; Internal Operations positive mutations
  remain online-authoritative.
- `DEC-0025`: approval binds complete immutable consumer-served meaning; publication and suspension are fenced by
  generations; outcome unknown is explicit; restore is quarantined; protected audit is required; emergency action is
  narrow negative authority.
- `DEC-0026`: hybrid understandable roles plus server-authoritative contextual authorization; deny-by-default;
  commit-time reauthorization; separation of duties; protected audit; quarantine-first ingestion; separate export
  authority; AI/OCR is proposal-only.
- `DEC-0027`: release authorities are separate for mobile, web, backend/API, migration, technical content,
  configuration and emergency controls; exact immutable artifacts are promoted; release meaning is cross-domain;
  rollback cannot resurrect revoked truth.
- `DEC-0028` / `DEC-0029`: AI-native task/context/evidence graph; nontechnical owner; AI must not be the sole approver,
  unrestricted superuser, billing/legal owner or owner-debugging substitute.
- `DEC-0030`: one owner and limited budget; current cost, hard cap/overage, free/capped route and exit must be shown
  before approval; mandatory assurance cannot be downgraded for price.
- `DEC-0033`: Flutter is the consumer-mobile working direction; framework truth must remain outside presentation code.
- `DEC-0034`: canonical transactional authority per domain; API mediation; online Internal Operations; bounded closed
  offline packages; durable user operations; separate current/history/protected-audit and object/media meanings;
  anti-resurrection floor; cross-plane export/restore/exit; provider/account/billing and bounded AI operation as
  first-class states.

The governing architecture records are:

- [DEBATE-007 — Data Backbone and Logical Service Boundaries](DEBATE-007__DATA_BACKBONE_AND_LOGICAL_BOUNDARIES.md)
- [DEBATE-007 — Judge Synthesis](DEBATE-007__JUDGE_SYNTHESIS.md)
- [DEBATE-004 — Identity, Scoped Authorization, Audit and Untrusted Ingestion](DEBATE-004__IDENTITY_AUTHORIZATION_AUDIT_UNTRUSTED_INGESTION.md)
- [DEBATE-005 — Software, Content Supply Chain and Release Governance](DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md)

No statement here creates an ADR, approves a provider/plan, authorizes code or advances Gate 4 → 5.

## 3. Evidence method

### 3.1 Source discipline

Only official product documentation/specifications or primary standards are used for mechanism claims. A representative
official product document is evidence of that product's documented behavior, not proof that every member of its family
behaves identically. Product examples are deliberately labelled `representative`, not selected.

Each conclusion uses one of these labels:

- `CONFIRMED`: directly stated by the cited official documentation;
- `INFERRED`: architecture consequence derived from a confirmed mechanism plus Kavriva's approved invariant;
- `EVIDENCE REQUIRED`: cannot be accepted from documentation alone and must be proven in a later no-code contract,
  controlled drill or Phase-5 ADR evidence pack.

Current documentation was checked on 2026-09-18. Limits, retention, product editions, pricing and plan behavior are
changeable and are not treated as project constants.

### 3.2 Acceptance rule

There is no aggregate score. A candidate is an ADR candidate only if every critical boundary is closed with an
authoritative result, protected evidence, recovery owner and residual-risk statement. A missing critical proof is
`HELD`, not an averageable low score.

Every `HF-...` marker in a candidate walkthrough is a candidate-specific reject cue. The following hard-fail register
groups those cues by boundary; an unclosed cue remains `HELD` even when it is not repeated in prose.

`Hard fail` below means: the candidate's proposed use is rejected until the named compensating control is designed and
independently evidenced. It does not mean the underlying product or family can never be used as a bounded adjunct.

### 3.3 Required outcome vocabulary

- `ALLOW`: the authoritative service has committed the requested transition and the required evidence is durably bound.
- `DENY`: the actor/path is not authorized; no domain effect is committed.
- `HOLD`: uncertainty, missing evidence, conflict, stale authority, outage or unavailable independence prevents a
  positive effect; safe recovery/teaching/history may remain available where policy allows.
- `OUTCOME_UNKNOWN`: the client cannot know whether the same operation committed; lookup/reconciliation uses the same
  operation identity. A timeout is never guessed as success or failure.
- `RESTORE_QUARANTINE`: restored data is non-authoritative until the independent floor, audit, identity/policy,
  objects and pending operations reconcile.

## 4. Backbone that every candidate must carry

| Logical contract | Required meaning | Forbidden shortcut |
|---|---|---|
| Canonical current authority | One transactional authority per domain with stable identity/version/generation contracts. It may share one physical engine, but ownership is explicit. | A mutable “current data” bucket, cache, replica, push event or provider console as truth. |
| API/policy boundary | Flutter and browser clients use server/API-mediated sensitive reads and mutations; policy checks actor, session, action, exact scope, state, classification, consequence, independence and expected version. | Hidden button, client SDK, row ID, cached role, RLS/rules/permissions alone or admin SDK as policy. |
| High-consequence lifecycle | Proposal, review, approval, release, recall/suspension and re-entry are distinct guarded operations; negative suspension generation cannot be cleared by older/in-flight positive work. | Self-approval, last-write-wins, signature/hash alone, or normal publish overwriting emergency state. |
| Protected audit | Attributable ordered evidence, independent custody/checkpoint/fork detection and bounded fallback; absent protected evidence holds normal high-consequence work. | A mutable audit table, provider activity feed, database timestamp or ordinary application log alone. |
| Object/media boundary | Files have identity, digest, version/generation, classification, lineage and retention state; quarantine precedes scan/render/review. | Public/raw URL, client-wide storage credential, MIME/type check or successful scan as technical approval. |
| Closed offline package | Selected motorcycle/task only; exact release/client/eligibility context; complete compact safety/application/safe-stop/recovery closure; atomic integrity/anti-rollback. | Full-library download, partial/mixed package use, cache as recall proof or missing closure hidden by a small size. |
| User local operations | Durable identified operation before local-success presentation; idempotent retry; explicit conflict/hold/unknown/device-loss semantics; no silent high-consequence last-write-wins. | Blind repeat, timestamp winner, silent merge or local history becoming official truth. |
| Cross-plane consistency | DB, object, audit and outbox effects use an explicit state machine and operation identity; relay success is not authority. | Claiming one database transaction atomically commits an external object, audit sink and provider queue. |
| Anti-resurrection recovery | Protected non-restorable floor for release/suspension/security/deletion/accepted-operation/migration generations; restore is quarantined. | Old backup/PITR/clone reviving recalled content, revoked role, deleted private data or accepted operation. |
| Export/exit | Coordinated manifest for canonical data, objects, history, audit checkpoint, identity/policy, floor, outbox and keys (without raw secrets); clean-room import proves behavior. | “Export job succeeded”, one vendor dump or a provider clone treated as complete exit. |
| Provider/cost state | Account, billing/quota, region/outage, identity/DNS/key loss and support failure produce safe explicit states; bounded cost and egress controls are observable. | Free-tier assumption, soft alert called a cap, uncapped overage or owner repair/SSH as recovery. |
| AI operation | Minimum-sufficient task context, allowed/forbidden scope, least-privilege credentials, dry run, stop condition,
  evidence and forward recovery; independent review for high consequence. | AI receives a service/root key, document prompt becomes authority, or owner is asked to debug infrastructure. |

## 5. Common no-code failure walkthrough

The following witnesses are applied to every candidate. Each candidate section records where the family naturally
supports the witness, where it requires an external control, and the condition that would be a hard fail.

| ID | No-code failure witness | Expected invariant outcome |
|---|---|---|
| `NF-01` | Browser calls approval/publish API directly after the button is hidden; a service/admin path or RLS bypass is also attempted. | Server-side deny/hold at the authoritative mutation; no domain side effect; actor/path/policy version and reason are audited. |
| `NF-02` | Reviewer/publisher attempts self-approval while a concurrent publish and emergency suspension/recall race. | Separation-of-duties deny/hold; one guarded transition; newer negative generation wins; no positive operation clears it. |
| `NF-03` | Protected audit sink is unavailable, restored with a sequence gap, or controlled by the actor being audited. | Normal high-consequence effect holds unless minimum independent fallback evidence exists; gap/fork is quarantined and reconciled. |
| `NF-04` | Canonical DB commit, object finalization, audit write and outbox relay do not complete together; browser response times out. | Explicit partial/failed/unknown state with one durable operation identity; lookup/reconcile; no duplicate or guessed success. |
| `NF-05` | Package builder is asked for one motorcycle/task while a dependency is stale, missing, oversized or mixed-generation. | Partial/mixed package is rejected; complete compact safety/recovery closure remains available; no unrelated library download. |
| `NF-06` | User records history/evidence offline, retries after a lost response, then reconnects with a conflicting server event or loses the device. | Durable pending operation; idempotent lookup; reviewed conflict/hold; truthful local-loss state; no silent last-write-wins. |
| `NF-07` | PDF/image/archive has active content, traversal, decompression expansion or URL redirect to private metadata; preview is opened. | Quarantine/unknown/reject; isolated untrusted preview; no ambient credentials/network/native viewer; original/derived lineage retained. |
| `NF-08` | Old backup/clone is restored after recall, role revocation, private deletion or accepted operation. | `RESTORE_QUARANTINE`; independent floor/tombstones/operation ledger prevent resurrection; cutover held until reconciliation. |
| `NF-09` | Provider account is locked, billing/quota is held, region/API is unavailable, or support/recovery contact is lost. | Positive mutations/publication hold; consumer safe-stop/teaching/history and independent negative authority are evaluated separately; owner is not the repair path. |
| `NF-10` | Exit exports DB, objects, history, audit, policy, identities, outbox and package manifests into a clean environment. | Consistency manifest, digests, classifications, floor and negative tests verify import; partial export is labelled partial; no raw secrets. |
| `NF-11` | An AI task asks for broad data access, migration cutover, privilege/key change or publication; task pack is incomplete. | Task is denied/held; least-privilege, dry-run and independent review; missing task/contract remains a visible gap; no owner debugging. |
| `NF-12` | Binary/web/API/config/migration/content/offline package have different generations; a valid artifact is available but semantics mismatch. | Closed release-meaning graph holds promotion/consumption; exact artifact is not rebuilt; current suspension/revocation generation is rechecked. |

## 6. Candidate family A — Integrated BaaS (Supabase-like)

### 6.1 Mechanism evidence and architectural reading

`CONFIRMED`: Supabase documents a full Postgres database as the foundation for Auth, Storage, Realtime and Edge
Functions. Its RLS guidance says grants and policies both matter, exposed tables may retain default grants, and a
`service_role`/secret key bypasses RLS and must stay server-side. Storage service keys likewise bypass Storage RLS.
([database overview](https://supabase.com/docs/guides/database/overview),
[RLS](https://supabase.com/docs/guides/database/postgres/row-level-security),
[Storage access control](https://supabase.com/docs/guides/storage/security/access-control))

`CONFIRMED`: Supabase's backup documentation states that database backups do not include objects stored through the
Storage API, because the database contains only object metadata. Its restore-to-new-project documentation says Storage
objects/settings, Edge Functions, Auth settings/API keys, Realtime settings and extensions need manual
reconfiguration. ([database backups](https://supabase.com/docs/guides/platform/backups),
[restore to a new project](https://supabase.com/docs/guides/platform/clone-project))

`INFERRED`: The integrated surface is useful for a relational canonical domain and ordinary API delivery, but the
project boundary cannot be treated as one atomic trust/recovery boundary. RLS is a defense layer, not Kavriva's full
contextual authorization model. Realtime/Storage/Edge Functions do not automatically provide protected independent
audit, quarantine, release generations or a non-restorable anti-resurrection floor.

### 6.2 No-code failure walkthrough

| Witness | Walkthrough result if used as the primary stack | Required evidence / hard-fail cue |
|---|---|---|
| `NF-01` | `ALLOW` is possible only through an independent API/policy layer that keeps secret/service keys off Flutter, browser bundles and AI context. Direct Data API, Storage API, SQL, view or service-key paths are `DENY`/`HOLD` unless the same contextual policy and audit contract is enforced. | `HF-BAAS-01` if client authority or service-key/RLS bypass is reachable, or if RLS is presented as sole approval/policy proof. |
| `NF-02` | Postgres can guard a domain transition, but publish versus suspension needs a monotonic generation fence and a separate negative authority. Realtime or a database trigger cannot be accepted as recall proof. | `HOLD` on missing independent suspension/re-entry evidence. `HF-BAAS-02` if normal BaaS publication can overwrite/clear a newer suspension. |
| `NF-03` | A table in the same project is not protected audit custody. Use an independent append-only/WORM or equivalently protected sink and bounded fallback; audit failure holds normal high-consequence work. | `HF-BAAS-03` if Supabase logs/table/activity is the only durable audit or the same project admin can rewrite both effect and evidence. |
| `NF-04` | A Postgres transaction can bind current-state mutation plus an outbox row, not external object finalization, independent audit and relay delivery. Use operation states and digest-bound object finalization. | `HF-BAAS-04` if the design claims one BaaS transaction covers all planes or treats a timed-out Edge Function/relay as success. |
| `NF-05` | An API/package worker can build a selected motorcycle/task package and store a closed manifest. Realtime/cache must be rebuildable; optional media must not displace compact recovery closure. | `HF-BAAS-05` if package correctness depends on a Realtime event, full database snapshot or unbounded Storage download. |
| `NF-06` | Flutter must own a durable operation queue and submit idempotency keys to the API. Postgres expected-version/conflict rows preserve both sides for high-consequence data; no silent realtime merge. | `HOLD` on unknown result/device loss; `HF-BAAS-06` if client cache or Realtime ordering is treated as user-history authority. |
| `NF-07` | Storage RLS can scope bytes but does not establish malware/content correctness. Quarantine, isolated scan/render and URL egress control need a separate worker/storage boundary; public buckets are ineligible for originals. | `HF-BAAS-07` if uploaded bytes become reviewable/publishable merely because Storage accepted them or a scan returned clean. |
| `NF-08` | Official docs explicitly separate database backups from Storage objects. Restore must enter quarantine with external release/security/deletion/operation floor, object manifest and audit reconciliation. | `HF-BAAS-08` if a project restore/clone is treated as complete recovery or can revive deleted/recalled Storage objects. |
| `NF-09` | BaaS account, plan, quota, region and control-plane failure are service states. Consumer safe/recovery and independent negative control need an operational path outside the normal project. | `HF-BAAS-09` if an alert is the only spend control, or owner must use dashboard/SQL/SSH to recover. |
| `NF-10` | Exit requires logical DB dump plus Storage object/digest manifest, Auth/policy/config, functions, release state, audit checkpoint, floor and keys/references; clean-room import must test denies and negative generations. | `HF-BAAS-10` if the vendor project clone or `db dump` alone is called exit proof. |
| `NF-11` | AI tasks may receive a narrow API operation role and dry-run runbook, never a BaaS owner/service key. Migration, key, restore and publication tasks need independent reviewer/validator evidence. | `HF-BAAS-11` if an AI is given Dashboard owner, unrestricted SQL or service-role credentials, or the owner is the incident debugger. |
| `NF-12` | Binary/web/API/config/migration/content/package generations must be recorded outside the integrated convenience layer and checked at promotion and runtime. | `HF-BAAS-12` if a valid BaaS schema/function deployment or old project restore can clear a current suspension. |

### 6.3 Candidate-specific hard fails

- `HF-BAAS-01`: any general client or AI context contains a secret/service role, database credential or unrestricted
  Storage capability; or the architecture relies on RLS/storage policies alone for high-consequence contextual policy.
- `HF-BAAS-02`: publish/recall share one mutable transition with no independent negative authority and monotonic generation
  fence.
- `HF-BAAS-03`: protected audit is an ordinary table/log/activity feed in the same provider account and no independent
  custody/fallback can hold the effect.
- `HF-BAAS-04`: the design claims atomicity across Postgres, Storage bytes, audit sink and outbox/notification, or
  returns success before the required operation/audit relation is durable.
- `HF-BAAS-05`: offline correctness relies on full-library sync, Realtime/push delivery, or a mixed/partial Storage
  package.
- `HF-BAAS-06`: the documented backup/clone path is accepted without a cross-plane manifest, non-restorable floor and
  clean-room import.
- `HF-BAAS-07`: Storage acceptance, a successful scan or a public URL is treated as quarantine/technical approval.
- `HF-BAAS-08`: project restore/clone can go live without object, audit, deletion and authority-floor reconciliation.
- `HF-BAAS-09`: account/billing/quota failure has no safe hold path, hard spending control or owner-independent recovery.
- `HF-BAAS-10`: database dump/project clone is the only export and no clean-room negative-behavior import exists.
- `HF-BAAS-11`: AI or owner requires Dashboard owner, unrestricted SQL/service key or interactive incident repair.
- `HF-BAAS-12`: schema/function/config/package generation can change meaning or clear suspension outside the release graph.

### 6.4 Minimum compensating controls

1. Independent API/policy boundary for every sensitive read/mutation; BaaS RLS/IAM/Storage policy remains a defense
   layer and receives owner/superuser/bypass/BOLA negative tests.
2. Separate release/suspension authority and protected audit custody/fallback, with operation IDs and generation fences.
3. Dedicated quarantine/scan/render boundary; originals never served from the operations origin.
4. Package builder that emits a machine-verifiable selected-motorcycle/task manifest and pins required safety/recovery
   core; optional media is separate.
5. External non-restorable floor plus coordinated DB/object/audit/policy export and clean-room import.
6. Provider/account/billing runbook with observable spend limits, explicit `ACCOUNT_HELD`/`BILLING_HELD` states and AI
   least-privilege tasks.

Provisional disposition: `CONDITIONALLY ELIGIBLE AS A COMPONENT; NOT ACCEPTABLE AS AN UNPARTITIONED TRUST/RECOVERY
BOUNDARY`. It remains an ADR candidate only if each control is evidenced.

## 7. Candidate family B — Firebase / Firestore

### 7.1 Mechanism evidence and architectural reading

`CONFIRMED`: Firestore Security Rules are evaluated for mobile/web client libraries, but server client libraries bypass
all Firestore Rules and use IAM. The official guide also states that rules are not filters: a query is accepted only if
the potential result set satisfies the rule. ([rules conditions](https://firebase.google.com/docs/firestore/security/rules-conditions),
[rules and queries](https://firebase.google.com/docs/firestore/security/rules-query))

`CONFIRMED`: Firestore transactions fail when the client is offline. Offline persistence synchronizes local changes
later and multiple changes to the same document use last-write-wins. ([transactions](https://firebase.google.com/docs/firestore/manage-data/transactions),
[offline data](https://firebase.google.com/docs/firestore/enterprise/enable-offline))

`CONFIRMED`: Managed export/import requires billing and Cloud Storage; an export is not an exact snapshot at export
start and collection groups/subcollections must be explicitly selected. Export/import is charged by reads/writes and
Cloud Storage. ([export and import](https://firebase.google.com/docs/firestore/manage-data/export-import))

`CONFIRMED`: Cloud Storage Rules can control file path, metadata, size and content type, but the documented mechanism is
authorization/validation, not malware quarantine or technical verification. ([Cloud Storage security](https://firebase.google.com/docs/storage/security))

`INFERRED`: Firestore can be useful for bounded read models, low-risk drafts and mobile cache distribution. Its offline
client behavior cannot be allowed to define Kavriva's high-consequence current truth, provenance, approval, recall or
dispute meaning without an external authoritative operation model.

### 7.2 No-code failure walkthrough

| Witness | Walkthrough result if used as the primary stack | Required evidence / hard-fail cue |
|---|---|---|
| `NF-01` | Client Rules can deny ordinary paths, but Admin/server SDK bypasses Rules. All high-consequence operations must enter an independent API that evaluates actor, scope, workflow and independence before any Admin write. | `HF-FS-01` if Admin SDK/IAM is treated as business authorization, or Rules are the only privileged-path control. |
| `NF-02` | Online Firestore transactions can atomically update bounded documents, but they do not create release governance or an independent negative suspension authority. Transaction sentinel + protected audit is still required. | `HOLD` on self-approval/race; `HF-FS-02` if Firestore/FCM transaction or listener is accepted as recall authority. |
| `NF-03` | Firestore documents/exports and provider logs are not independent protected audit custody. Use an external append-only evidence sink and hold when both primary/fallback evidence fail. | `HF-FS-03` if the only audit is a Firestore collection, Cloud Logging feed or actor-controlled Admin path. |
| `NF-04` | A Firestore transaction/batch does not atomically include Cloud Storage bytes, protected audit, package artifacts and delivery/outbox effects. Use operation state, object digest and reconciliation. | `HF-FS-04` if a batch or Cloud Function timeout is treated as all-plane success. |
| `NF-05` | Firestore offline cache is not a closed selected-task package: it may contain active data and later synchronize changes. Build an explicit signed/versioned manifest and reject missing/mixed dependencies. | `HF-FS-05` if offline persistence or listeners are used as package eligibility/recall truth, or if LWW may alter critical guidance. |
| `NF-06` | Offline transactions fail and same-document changes use LWW. Local history/evidence must be an explicit operation queue with conflict records and no silent overwrite; high-consequence writes may be online-only. | `HF-FS-06` if LWW is canonical for safety, provenance, ownership, entitlement, official content or disputed evidence. |
| `NF-07` | Storage Rules can reject type/size/path but cannot establish quarantine, parser isolation, SSRF controls or technical correctness. Use an isolated intake and preview plane. | `HF-FS-07` if upload acceptance or Storage Rule validation releases original bytes to operators/consumers. |
| `NF-08` | PITR/export and Storage restore are separate planes; collection/subcollection coverage and export timing need a manifest. Restored data enters quarantine and external revocation/deletion/operation floor is authoritative. | `HF-FS-08` if Firestore PITR or managed export is treated as anti-resurrection recovery. |
| `NF-09` | Billing-enabled export is a documented control-plane dependency; account/IAM/region/quota failure can block positive writes, export or recovery. Safe consumer recovery and independent negative action need explicit paths. | `HF-FS-09` if billing alerts are called caps or an owner must repair Firebase/GCP credentials manually. |
| `NF-10` | Managed export is service-specific and may not be an exact start snapshot; explicit collection groups, Storage objects, Auth, Rules, Functions, audit and floor are all separate. Clean-room importer must test policy/negative behavior. | `HF-FS-10` if “Firestore export succeeded” is the complete exit claim. |
| `NF-11` | AI may use a narrow API service identity; it cannot receive a service-account private key or broad Admin SDK. Ruleset, Function, IAM, migration and recovery changes need task packs and independent review. | `HF-FS-11` if AI runs with project owner/Admin or the owner is expected to debug IAM/billing/runtime. |
| `NF-12` | Firestore document schema, Rules, Cloud Functions, Storage metadata, app binary, configuration and offline package versions need one release graph; valid document writes cannot clear a suspension. | `HF-FS-12` if a Rules/Function/config change can silently change safety meaning outside release closure. |

### 7.3 Candidate-specific hard fails

- `HF-FS-01`: Firestore Rules or mobile SDK access is the sole control for high-consequence privileged work while a
  server/Admin SDK path bypasses those Rules without an equivalent contextual policy gateway.
- `HF-FS-02`: client offline persistence, listener delivery or FCM is used as current eligibility, recall or publication
  authority.
- `HF-FS-03`: Firestore documents/provider logs are the only audit custody or fallback.
- `HF-FS-04`: a Firestore batch/Function is treated as atomic across Storage, audit, package and relay effects.
- `HF-FS-05`: offline persistence/listeners or mixed cache state are used as the closed safety-package authority.
- `HF-FS-06`: last-write-wins is applied to technical claims, release/suspension state, provenance, ownership,
  entitlement, history or disputed evidence.
- `HF-FS-07`: Storage Rule validation or upload acceptance is treated as quarantine, parser isolation or technical approval.
- `HF-FS-08`: Firestore PITR/export/Storage restore can go live without the external floor and cross-plane reconciliation.
- `HF-FS-09`: billing/IAM/region failure has no safe hold path, hard spending control or owner-independent recovery.
- `HF-FS-10`: managed export/import is the only exit/recovery path and cannot prove exact coverage and clean-room
  negative behavior.
- `HF-FS-11`: AI or owner requires project-owner/Admin SDK credentials or interactive incident repair.
- `HF-FS-12`: Rules/Functions/schema/config/package generations can change meaning outside the release graph.

### 7.4 Minimum compensating controls

1. Treat Firestore as a bounded document/read/cache plane or low-risk draft adjunct unless an independent authority
   closes the relational, history, release and conflict contracts.
2. Route all high-consequence operations through an API/policy service with IAM limited to that service; Rules remain a
   defense and test surface, not approval authority.
3. Disable/avoid offline writes for high-consequence domains; use an identified local operation queue for user work and
   preserve competing values instead of LWW.
4. Keep quarantine originals and protected audit outside the ordinary Firestore/Storage delivery path; use object
   digests, isolated preview and independent custody.
5. Build a cross-plane export/restore manifest and importer that includes collection groups, objects, Auth/Rules/Functions
   configuration, audit checkpoint, release/suspension floor, deletion tombstones and operation ledger.
6. Prove spending/egress controls, billing hold behavior and an AI runbook without project-owner credentials.

Provisional disposition: `NOT FIT AS SOLE CANONICAL HIGH-CONSEQUENCE AUTHORITY UNDER CURRENT DOCUMENTED OFFLINE
SEMANTICS; CONDITIONALLY ELIGIBLE AS A BOUNDED DOCUMENT/CACHE ADJUNCT`. This is not a ban on Firebase features or a
provider selection.

## 8. Candidate family C — Managed relational DB + independent API + object storage

### 8.1 Mechanism evidence and architectural reading

`CONFIRMED`: PostgreSQL supplies relational constraints and row security, but table owners, superusers and `BYPASSRLS`
roles bypass row security. `pg_dump` is a logical export and has an explicit row-security behavior; therefore neither
RLS nor a dump is a complete authorization/exit story. ([PostgreSQL row security](https://www.postgresql.org/docs/current/ddl-rowsecurity.html),
[pg_dump](https://www.postgresql.org/docs/current/app-pgdump.html))

`CONFIRMED`: PostgreSQL transaction isolation can provide serializable behavior, but serialization failures require
application retry. A managed representative such as Amazon RDS restores point-in-time data into a new DB instance while
leaving the source intact. ([transaction isolation](https://www.postgresql.org/docs/current/transaction-iso.html),
[RDS point-in-time restore](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIT.html))

`CONFIRMED`: Object storage can provide temporary scoped bearer access and integrity checks, while S3 Object Lock uses
versioning and WORM retention/legal holds. Object Lock protects the specified version; new versions/delete markers and
privacy/deletion policy still require application handling. ([S3 presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html),
[S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html))

`INFERRED`: This family makes the logical boundaries explicit: relational transactions for canonical state, API/policy
for authority, object storage for bytes, and separately controlled audit/recovery planes. It does not make cross-plane
atomicity or protected audit automatic; those remain design and evidence obligations.

### 8.2 No-code failure walkthrough

| Witness | Walkthrough result if used as the primary stack | Required evidence / hard-fail cue |
|---|---|---|
| `NF-01` | Browser/Flutter receives no general DB or object credential. API evaluates current actor/session/scope/version; DB grants/RLS and object IAM add defense. Direct DB, owner, superuser and BOLA paths are `DENY`. | `HF-RDB-01` if DB endpoint, owner/BYPASSRLS role, object credential or unrestricted API route can replace the policy boundary. |
| `NF-02` | API transaction creates one guarded approval/release event; independent suspension path increments negative generation; commit checks current generation and independence. Concurrent loser is conflict/hold, not LWW. | `HF-RDB-02` if publish and recall share an un-fenced control path or no independent negative authority exists. |
| `NF-03` | Canonical DB can store domain history, but protected audit is a separate custody/fallback with sequence/checkpoint detection. Audit write absence holds the high-consequence mutation. | `HF-RDB-03` if an audit table in the same managed account is the sole tamper evidence or an admin can erase both effect and audit. |
| `NF-04` | DB transaction binds current state + idempotency ledger + outbox intent. Object finalize, audit custody and relay delivery use explicit prepared/partial/unknown/reconciling states. | `HF-RDB-04` if ACID is claimed to cover object/audit/broker planes or timeout is reported as ordinary success. |
| `NF-05` | Package builder queries only selected motorcycle/task, resolves dependency closure and emits an atomic manifest/digests; optional media is separate. Cache pressure cannot evict required closure. | `HOLD` if dependency closure is unresolved; hard fail if package builder uses a full DB dump or accepts mixed generations. |
| `NF-06` | Local operations carry stable identity, actor/device/context, expected version and payload fingerprint. API uniqueness/idempotency resolves retry; high-consequence conflict preserves both sides. | `HF-RDB-05` if API omits an operation ledger or applies silent timestamp/LWW conflict resolution. |
| `NF-07` | Presigned/multipart transport is scoped to an opaque object key and expiry; bytes enter quarantine, isolated scan/render and classification flow before any public/operations read. | `HF-RDB-06` if the object URL or bucket is the review authority, or if presigned bearer links are unbounded/public. |
| `NF-08` | Managed PITR creates a new DB, but the cutover remains `RESTORE_QUARANTINE`; external floor, object versions/tombstones, audit checkpoint, policy/security epoch and accepted-operation ledger block resurrection. | `HF-RDB-07` if PITR/DB snapshot is accepted without the non-restorable floor and cross-plane reconciliation. |
| `NF-09` | Managed DB/account/billing/region failure becomes explicit service state. API stops positive mutations; consumer safe/recovery and independent emergency negative authority are evaluated separately. | `HF-RDB-08` if support console/owner SSH is the only recovery or alerts are mistaken for hard spend caps. |
| `NF-10` | SQL logical export plus object manifest, audit/floor checkpoint, policy/identity mapping, outbox cursor and key references form a consistency manifest. Clean-room import runs deny/hold/negative-generation tests before cutover. | `HF-RDB-09` if provider snapshot or DB dump is called complete exit. |
| `NF-11` | AI tasks operate against narrow API operation contracts and read-only/dry-run roles; migrations, restore, keys, policy and publication require independent review and evidence. | `HF-RDB-10` if AI/owner needs superuser, direct production SQL, SSH or manual incident repair. |
| `NF-12` | Release graph binds API contract, schema/migration state, content manifest, configuration, client capability, package closure and generations; deployment promotes exact artifacts. | `HF-RDB-11` if provider migration/restore or config can make a valid binary semantically unsafe without a hold. |

### 8.3 Candidate-specific hard fails

- `HF-RDB-01`: the independent API is optional in practice, or a direct DB/object/admin path can perform sensitive
  mutation without the same contextual authorization and evidence.
- `HF-RDB-02`: the design treats relational ACID as cross-plane atomicity for object bytes, protected audit, queue,
  notification or release distribution.
- `HF-RDB-03`: no independent protected audit custody/fallback or non-restorable authority/deletion/operation floor is
  available outside the managed DB snapshot/account.
- `HF-RDB-04`: provider export/restore cannot produce a standard logical data export plus object/history/audit/policy
  manifest and a clean-room import with negative tests.
- `HF-RDB-05`: API omits a durable operation ledger or silently resolves high-consequence conflicts with LWW/timestamps.
- `HF-RDB-06`: object transport/bucket is treated as quarantine or review authority, or presigned bearer access is
  unbounded/public.
- `HF-RDB-07`: managed PITR/snapshot can go live without the non-restorable floor and cross-plane reconciliation.
- `HF-RDB-08`: managed operation has no safe provider/billing/region hold or requires owner SSH/support-console repair.
- `HF-RDB-09`: provider export/restore cannot produce a portable cross-plane manifest and clean-room negative tests.
- `HF-RDB-10`: AI or owner requires superuser, direct production SQL, SSH or manual incident repair.
- `HF-RDB-11`: migration/configuration/provider restore can change release meaning outside the closed graph.

### 8.4 Minimum compensating controls

1. Keep DB, API/policy, object/media, protected audit and release/suspension authorities as distinct logical planes,
   even when initially operated by one managed organization.
2. Use DB constraints/transactions for canonical invariants, an idempotency ledger and outbox intent; make every
   cross-plane object/audit/relay transition explicit.
3. Use opaque object identities, short-lived scoped handles and quarantine-first workers; never expose global object
   credentials.
4. Store the anti-resurrection floor and protected audit in a failure domain/control path independent enough to detect
   provider restore or account compromise.
5. Maintain portable logical export and clean-room importer; rehearse restore/cutover and negative behavior.
6. Automate staged cost/cap/overage controls, alerts and provider-failure runbooks; keep AI roles narrow and reviewable.

Provisional disposition: `MECHANISMALLY ALIGNED CANDIDATE; ADR ELIGIBILITY REMAINS CONDITIONAL ON CROSS-PLANE,
PROTECTED-AUDIT, EXIT, COST AND AI-OPERABILITY EVIDENCE`. This wording is an observation, not a winner selection.

## 9. Candidate family D — Appwrite

### 9.1 Mechanism evidence and architectural reading

`CONFIRMED`: Appwrite permissions apply to databases/tables/rows/buckets/files, but Server SDK access with an API key
can access project resources regardless of resource permissions. The authentication guide states that permissions are
ignored when a Server SDK uses an API key. ([permissions](https://appwrite.io/docs/advanced/security/permissions),
[authentication](https://appwrite.io/docs/advanced/security/authentication),
[API keys](https://appwrite.io/docs/partners/project/api-keys))

`CONFIRMED`: Appwrite TablesDB transactions can stage operations across databases/tables and commit atomically with
conflict detection. This protects database rows, not external object bytes, protected audit, release distribution or
provider-control transitions. ([TablesDB transactions](https://appwrite.io/docs/products/databases/tablesdb/transactions))

`CONFIRMED`: Appwrite documents product audit logs, but its retention page currently describes only seven days for Pro
organizations and one hour for Free organizations. Appwrite's backup page describes plan-dependent self-managed backups
and platform disaster-recovery backups; self-hosting requires the operator to manage updates/scaling. ([audit logs](https://appwrite.io/docs/advanced/security/audit-logs),
[backups](https://appwrite.io/docs/advanced/security/backups),
[self-hosting](https://appwrite.io/docs/advanced/self-hosting))

`CONFIRMED`: Appwrite Storage supports bucket/file permissions, file-size/type settings and chunked uploads, but the
upload/download documentation does not establish quarantine, malware scanning or isolated preview. ([Storage upload/download](https://appwrite.io/docs/products/storage/upload-download),
[Storage permissions](https://appwrite.io/docs/products/storage/permissions))

`INFERRED`: Appwrite can reduce ordinary integration work and can expose relational or document database mechanisms,
but resource permissions/API scopes are not the complete contextual separation-of-duties policy. Built-in activity
logs and backups cannot automatically become Kavriva's long-retention protected audit or anti-resurrection floor.

### 9.2 No-code failure walkthrough

| Witness | Walkthrough result if used as the primary stack | Required evidence / hard-fail cue |
|---|---|---|
| `NF-01` | Client permissions can deny normal access, but a Server SDK/API key bypasses resource permissions. High-consequence actions must pass through an independent contextual policy API before using any server credential. | `HF-AW-01` if API-key scope is treated as business authorization or a key can reach the client/AI context. |
| `NF-02` | TablesDB transaction can guard rows, but approval/publish/recall needs independent roles, generation fencing and negative authority. Realtime/Functions are delivery/worker mechanisms, not authority. | `HF-AW-02` if a server key, Function or transaction can bypass separation of duties or clear a newer suspension. |
| `NF-03` | Built-in Activity logs are useful investigation signals, but documented retention and same-project administration are insufficient as protected independent custody. | `HF-AW-03` if Appwrite Activity is the only audit, fallback or restore-continuity evidence. |
| `NF-04` | TablesDB transaction covers staged database operations, not Storage objects, audit sink, package artifact or outbox delivery. Use operation state and object digest reconciliation. | `HF-AW-04` if the Appwrite transaction is claimed to atomically cover all logical planes. |
| `NF-05` | A dedicated package worker can use TablesDB and Storage manifests, but Appwrite Realtime/permissions do not prove package closure or recall reach-back. | `HF-AW-05` if a partial Appwrite query/realtime payload is usable as a safety package. |
| `NF-06` | Flutter local operation queue and Appwrite API must carry idempotency/expected-version semantics; Appwrite row transactions do not resolve device loss or domain conflict policy. | `HF-AW-06` if row transaction success or `$updatedAt` is treated as universal conflict resolution. |
| `NF-07` | Storage permission and chunking control access/transport only. External quarantine, scanning, isolated preview and source/derived lineage are mandatory. | `HF-AW-07` if upload, preview or permission grant is treated as safe evidence or publication eligibility. |
| `NF-08` | Appwrite backup/PITR behavior is plan/database-dependent and may restore in place; restore must be quarantined with external floor, audit checkpoint, object manifest and tombstones. | `HF-AW-08` if in-place restore or built-in DR can resurrect revoked/deleted/accepted state. |
| `NF-09` | Cloud account/plan/quota failure or self-host outage becomes `SERVICE_UNAVAILABLE`/`BILLING_HELD`; positive operations stop; owner must not be the manual maintenance path. | `HF-AW-09` if self-host recovery requires owner SSH/database repair or plan alerts are the only spending control. |
| `NF-10` | Exit must include TablesDB/DocumentsDB data, Storage objects/versions, permissions, Functions/config, audit checkpoint, release floor, operation ledger and identities; clean-room behavior is separate from Appwrite backup. | `HF-AW-10` if a project backup/console export without policy/audit/floor/object verification is called exit proof. |
| `NF-11` | AI uses a narrow API role or scoped ephemeral credential; never a broad API key or Console owner. Function/deployment/restore/key changes need review. | `HF-AW-11` if AI or owner must administer Appwrite directly or repair a failed container/provider incident. |
| `NF-12` | Appwrite API schema, Functions/sites, tables, Storage object generations, configuration and consumer package need one release graph. | `HF-AW-12` if a Function/permission/schema change can alter safety meaning without a gated artifact/revocation check. |

### 9.3 Candidate-specific hard fails

- `HF-AW-01`: Server SDK/API-key bypass is the only way to perform high-consequence work and no separate contextual
  policy/independence gate wraps it.
- `HF-AW-02`: Appwrite permissions, scopes or Function identity are treated as approval competence/separation of duties.
- `HF-AW-03`: Appwrite Activity retention/custody is the sole protected audit mechanism for the required retention and
  restore/fork detection policy.
- `HF-AW-04`: database transaction semantics are used to claim atomicity over Storage, audit, package and release planes.
- `HF-AW-05`: no external quarantine and clean-room export/import/floor can be operated without owner repair.
- `HF-AW-06`: Appwrite row timestamps/transactions are used as universal user conflict/device-loss resolution.
- `HF-AW-07`: upload, preview or permission grant is treated as quarantine, safe evidence or publication eligibility.
- `HF-AW-08`: in-place restore/DR can go live without external floor, audit, object and tombstone reconciliation.
- `HF-AW-09`: plan/account/self-host failure has no safe hold or owner-independent recovery/cost control.
- `HF-AW-10`: Appwrite backup/console export lacks a policy/audit/floor/object manifest and clean-room tests.
- `HF-AW-11`: AI or owner requires broad API keys, Console owner or interactive container/provider repair.
- `HF-AW-12`: API/Function/permission/schema/config/package changes can alter meaning outside release/revocation controls.

### 9.4 Minimum compensating controls

1. Place an independent API/policy boundary in front of all Appwrite Server SDK calls; use separate, minimal keys for
   distinct workload actions and keep key management outside ordinary content operators.
2. Stream protected audit to independent custody before high-consequence effect; treat Appwrite Activity as a secondary
   operational signal, not the protected record.
3. Add quarantine/scan/render/URL retrieval planes and keep original bytes inaccessible from the operations origin.
4. Use TablesDB transactions only for bounded database invariants; model object/audit/outbox transitions explicitly.
5. Define plan-independent export/restore manifests, external floor/tombstones and clean-room import tests.
6. If self-hosted, automate updates, health, backup, restore and failover; otherwise the nontechnical owner becomes the
   unapproved maintenance dependency.

Provisional disposition: `CONDITIONALLY ELIGIBLE AS AN API/CRUD COMPONENT OR SELF-HOSTED ADJUNCT; NOT SUFFICIENT AS THE
SOLE AUTHORIZATION, AUDIT, QUARANTINE OR RECOVERY AUTHORITY`. No product approval is implied.

## 10. Candidate family E — Edge SQLite / Workers family

### 10.1 Mechanism evidence and architectural reading

Cloudflare D1 + Workers + R2 + (where needed) Durable Objects is a representative edge family, not a selected stack.

`CONFIRMED`: D1 is reached through a Worker binding. D1 `batch()` executes prepared statements sequentially and rolls
back the sequence if a statement fails. Read replication requires the Sessions API for sequential consistency. D1 Time
Travel restores a database in place and its documented retention varies by plan; current limits include database size,
row/BLOB/query constraints and restore limits. ([D1 database API](https://developers.cloudflare.com/d1/worker-api/d1-database/),
[D1 Time Travel](https://developers.cloudflare.com/d1/reference/time-travel/),
[D1 limits](https://developers.cloudflare.com/d1/platform/limits))

`CONFIRMED`: Durable Objects provide strongly consistent transactional storage scoped to one Object ID; each Object can
only read/modify keys associated with that Object. R2 is documented as strongly consistent for object operations, but
concurrent writes to one key use last-writer-wins; R2 presigned URLs are bearer tokens; R2's S3 compatibility page
currently marks Object Locking unsupported. ([Workers storage choices](https://developers.cloudflare.com/workers/platform/storage-options/),
[Durable Objects limits](https://developers.cloudflare.com/durable-objects/platform/limits/),
[R2 consistency](https://developers.cloudflare.com/r2/reference/consistency/),
[R2 presigned URLs](https://developers.cloudflare.com/r2/api/s3/presigned-urls/),
[R2 S3 compatibility](https://developers.cloudflare.com/r2/api/s3/api/))

`INFERRED`: Edge placement is attractive for latency, scoped package delivery and per-aggregate coordination. It is not
automatically a global canonical transaction, independent audit custody or anti-resurrection system. D1, R2, Workers,
Durable Objects, account control plane and plan limits remain distinct failure/authority surfaces.

### 10.2 No-code failure walkthrough

| Witness | Walkthrough result if used as the primary stack | Required evidence / hard-fail cue |
|---|---|---|
| `NF-01` | Worker can be the API boundary and D1/DO bindings remain server-side; R2 presigned handles must be exact object/operation/expiry. Dashboard/account tokens are never product authority. | `HF-EDGE-01` if clients use direct D1/admin bindings or broad R2/account credentials, or if Worker auth is only a hidden route. |
| `NF-02` | D1 batch/DO serialization can guard a scoped transition, but global release/suspension and independent negative authority require an explicit coordinator and protected generation. | `HF-EDGE-02` if per-object ordering or Worker deployment is treated as global recall/publication authority. |
| `NF-03` | Worker logs/D1 rows are not independent protected audit custody; use external append-only/WORM/fallback and hold if unavailable. | `HF-EDGE-03` if D1/Workers logs are the only audit evidence or share the same account/admin failure domain. |
| `NF-04` | D1 batch can be atomic for SQL statements, R2 is separate and strongly consistent but not transactionally joined, and relay delivery is separate. Use operation state/idempotency. | `HF-EDGE-04` if D1/R2/DO/queue effects are reported as one ACID commit. |
| `NF-05` | Worker can build selected-task packages and stream optional media, but D1 size/row/request limits and edge cache eviction must not alter required closure. | `HF-EDGE-05` if package truth lives in cache/edge replica, mixed generations are accepted, or required closure exceeds unproven limits. |
| `NF-06` | API/DO can serialize a bounded user aggregate, but local Flutter operations still need durable IDs, idempotency and reviewed cross-aggregate conflicts. | `HF-EDGE-06` if a DO ID or R2 last-writer-wins behavior becomes universal user-history truth. |
| `NF-07` | R2 scoped URLs control transport only; current R2 Object Lock support is marked unavailable. Quarantine/scanning/preview and independent evidence object storage are required. | `HF-EDGE-07` if protected audit/release originals rely on R2 Object Lock, or upload/URL access bypasses quarantine. |
| `NF-08` | D1 Time Travel is an in-place database restore; R2 objects, audit, DO state, account policy and negative generations are not thereby reconciled. External floor and clean-room restore are mandatory. | `HF-EDGE-08` if Time Travel is treated as anti-resurrection or a restore can go live before floor reconciliation. |
| `NF-09` | Worker/D1/R2 account, plan, quota or region outage yields service/billing hold; independent negative authority and mobile safe-stop must be reachable through a separately evidenced path. | `HF-EDGE-09` if account limits/alerts are the only cost control or owner must repair Worker bindings/production state. |
| `NF-10` | D1 export (including documented R2 export route) is only one plane. Exit manifest must include SQLite schema/data, objects, DO state, audit, policy, releases, floor, operations and key references; import is clean-room. | `HF-EDGE-10` if an R2/D1 export or account clone is declared complete exit without negative tests. |
| `NF-11` | AI can operate a scoped Worker/API task or dry-run migration; production account tokens, Wrangler owner credentials and unrestricted SQL are forbidden. | `HF-EDGE-11` if AI/owner must inspect/repair edge runtime or manually recover account state. |
| `NF-12` | Worker script/version, D1 schema, DO class, R2 object generation, configuration and mobile package are separate release artifacts in one graph. | `HF-EDGE-12` if a script/schema rollback or in-place Time Travel can clear a newer suspension or mismatch package meaning. |

### 10.3 Candidate-specific hard fails

- `HF-EDGE-01`: edge replicas/cache/Workers/Durable Objects are used as an unbounded global canonical authority without
  a proven domain partition and independent cross-domain coordinator.
- `HF-EDGE-02`: D1 batch or a single Durable Object is claimed to atomically cover DB, R2, protected audit, release and
  negative authority across scopes.
- `HF-EDGE-03`: protected evidence requires R2 Object Lock, but the selected R2-compatible path has no equivalent
  independently protected retention/immutability control.
- `HF-EDGE-04`: in-place Time Travel restore is accepted without an external non-restorable floor, object/audit/DO
  reconciliation and clean-room evidence.
- `HF-EDGE-05`: fixed or plan-sensitive edge limits make the required package, audit, export or recovery behavior
  unbounded, and no bounded fallback exists within the owner-approved operating envelope.
- `HF-EDGE-06`: a Durable Object ID or R2 same-key last-writer-wins becomes universal user-history authority.
- `HF-EDGE-07`: protected evidence relies on unsupported R2 Object Lock, or direct upload/URL bypasses quarantine.
- `HF-EDGE-08`: in-place D1 Time Travel can roll back negative generations, deletion floor or accepted operations.
- `HF-EDGE-09`: account/plan/region failure has no safe hold, hard limit or owner-independent recovery path.
- `HF-EDGE-10`: D1/R2/DO/account export lacks a cross-plane manifest and clean-room negative tests.
- `HF-EDGE-11`: AI or owner needs Wrangler/account/root credentials or interactive edge-runtime repair.
- `HF-EDGE-12`: Worker/schema/object/config/package generations can change meaning or clear suspension outside release
  closure.

### 10.4 Minimum compensating controls

1. Use Workers/edge delivery as a server/API boundary or scoped projection/package path, not client authority.
2. Keep canonical high-consequence domains in explicit transactional authority with a coordinator that records
   operation/expected-generation state; use Durable Objects only for bounded per-aggregate serialization.
3. Put protected audit and anti-resurrection floor in a separate failure domain; do not infer immutability from R2
   consistency or a signed URL.
4. Build quarantine/scan/render and object metadata lineage outside the direct R2 upload/download path.
5. Rehearse D1/DO/R2 export and clean-room import; include limits, schema, object generations and negative tests.
6. Enforce account/plan caps and AI task runbooks; retain a safe mobile recovery path when edge control plane is down.

Provisional disposition: `CONDITIONALLY ELIGIBLE FOR EDGE API/DELIVERY OR BOUNDED AGGREGATE WORK; PRIMARY BACKBONE
REQUIRES PROOF OF GLOBAL AUTHORITY, PROTECTED AUDIT, RESTORE FLOOR, OBJECT QUARANTINE AND EXIT`. No edge provider is
selected.

## 11. Candidate family F — Self-host baseline

### 11.1 Mechanism evidence and architectural reading

The self-host baseline means an owner-controlled deployment of a standard relational authority, independent API/policy,
object storage, protected audit and automated operations. It is a control/exit baseline, not a recommendation to run a
single server.

`CONFIRMED`: PostgreSQL's documented row-security bypass roles, transaction/isolation behavior and logical dump provide
portable primitives, but still require an API boundary and explicit recovery policy. ([row security](https://www.postgresql.org/docs/current/ddl-rowsecurity.html),
[transaction isolation](https://www.postgresql.org/docs/current/transaction-iso.html),
[pg_dump](https://www.postgresql.org/docs/current/app-pgdump.html))

`CONFIRMED`: self-hosting documentation for representative integrated stacks distinguishes zero-setup managed operation
from manual setup, updates and scaling. ([Appwrite self-hosting](https://appwrite.io/docs/advanced/self-hosting))

`INFERRED`: self-hosting can make custody, region, version and exit explicit, but “open source” or “no license fee” is
not an operating model. A single host, root account, same-disk backup or owner-run SSH recovery directly conflicts with
`DEC-0029` and `DEC-0030`.

### 11.2 No-code failure walkthrough

| Witness | Walkthrough result if used as the primary stack | Required evidence / hard-fail cue |
|---|---|---|
| `NF-01` | Private API, private DB and scoped object handles can close the path; DB owner/superuser/root and orchestration APIs must be included in accumulation tests and cannot silently grant product approval. | `HF-SH-01` if root/DB owner/admin can mutate canonical state, policy and audit without a protected, attributable path. |
| `NF-02` | Separate release/suspension roles, hosts/trust roots and operation fences are possible, but must be explicitly operated; one admin account is not independence. | `HF-SH-02` if publish and emergency controls share one unreviewed root path or recovery bypasses separation of duties. |
| `NF-03` | A self-hosted append-only audit can be designed, but custody must be outside the mutable host/account and survive restore/fork. Fallback failure holds positive work. | `HF-SH-03` if audit and canonical DB share one disk/administrator and no independent checkpoint/copy exists. |
| `NF-04` | DB transaction + outbox intent can be built; objects, audit, queues and deployment remain cross-plane. Explicit operation state and retry/reconciliation are required. | `HF-SH-04` if a shell script/manual operator assumes all services committed because a DB transaction succeeded. |
| `NF-05` | A dedicated package builder can close selected-task dependencies and storage limits are owner-controlled; reproducible build/package evidence is still required. | `HOLD` on missing closure; hard fail if package depends on a full DB mirror or unbounded local disk. |
| `NF-06` | API and DB can implement idempotency/conflict ledger, but local device durability/device loss is still a client contract. | `HF-SH-05` if timestamp/LWW or manual SQL is the conflict/recovery mechanism. |
| `NF-07` | Separate quarantine host/object store/renderer can provide the required boundary; same-origin preview or unrestricted network remains forbidden. | `HF-SH-06` if uploads are written directly into public/operations storage or malware response depends on owner inspection. |
| `NF-08` | Independent offsite floor, audit copy, object manifest and clean bootstrap can prevent resurrection; same-host snapshot cannot. | `HF-SH-07` if restore/failover needs owner SSH or can roll back floor/security/deletion/operation state. |
| `NF-09` | Host, DNS, registrar, storage, backup, certificate and account failures are all explicit dependencies. A second failure domain and automated recovery are required. | `HF-SH-08` if the owner is the only on-call/database administrator or the deployment has no observable cost/resource cap. |
| `NF-10` | Standard logical export plus object/audit/policy/floor manifests can be imported into a clean environment, provided the bootstrap and cutover are reproducible. | `HF-SH-09` if clean-room bootstrap is tribal knowledge, manual-only or untested. |
| `NF-11` | AI can run bounded, auditable automation against narrow service accounts; root/SSH/database superuser stays outside ordinary task packs and requires independent recovery authority. | `HF-SH-10` if an AI or owner must debug kernel, disk, network, certificates or data corruption interactively. |
| `NF-12` | Source/build/migration/config/content/package artifacts can be independently versioned and promoted; self-host control-plane changes must enter the same release graph. | `HF-SH-11` if a manual host change, mutable image or restore can change current meaning without artifact evidence. |

### 11.3 Candidate-specific hard fails

- `HF-SH-01`: all canonical data, object bytes, audit and recovery keys share one host, disk, account or root path.
- `HF-SH-02`: routine patching, backup, failover, certificate renewal, restore or incident response requires the
  nontechnical owner to execute SSH/DB repair.
- `HF-SH-03`: no reproducible clean-environment bootstrap/import, protected floor, external audit custody and tested
  cutover fence exist.
- `HF-SH-04`: backups are only local/same-account snapshots, or restore has not been drilled against revocation,
  deletion, accepted-operation and audit sequence cases.
- `HF-SH-05`: maintenance, capacity, security and overage behavior cannot be observed and bounded within the staged
  cost envelope.
- `HF-SH-06`: uploads are written directly into public/operations storage or malware response depends on owner inspection.
- `HF-SH-07`: restore/failover can roll back floor/security/deletion/operation state or needs owner SSH.
- `HF-SH-08`: host/DNS/storage/account failure leaves the owner as the only repair path or lacks bounded resource cost.
- `HF-SH-09`: clean-room bootstrap/import is tribal knowledge, manual-only or untested.
- `HF-SH-10`: AI or owner must debug kernel, disk, network, certificates or data corruption interactively.
- `HF-SH-11`: manual host/image/restore changes can alter release meaning without artifact/revocation evidence.

### 11.4 Minimum compensating controls

1. Operate self-host as a managed-like product: immutable deployment artifacts, automated patch/backup/restore, health
   checks, alerts, secret rotation, capacity limits and a documented escalation path.
2. Separate API/policy, DB, object/quarantine, protected audit and recovery/floor custody by failure domain and identity;
   no shared root or long-lived shared credentials.
3. Keep offsite immutable copies and a clean-environment bootstrap/import that an AI runbook can execute without owner
   debugging; require human confirmation only for explicit irreversible/legal decisions.
4. Rehearse restore, migration partial states, package building, provider/host loss and key recovery; record evidence and
   residual risk.
5. Maintain a staged cost sheet for compute, storage, egress, backup, monitoring, domain/DNS, support and recovery.

Provisional disposition: `ELIGIBLE ONLY IF OPERATIONS ARE AUTOMATED, OBSERVABLE, INDEPENDENTLY REVIEWABLE AND OWNER-
INDEPENDENT; OTHERWISE REJECTED UNDER THE AI-OPERATED OWNER MODEL`. It remains a baseline, not a recommendation.

## 12. Cross-candidate fit matrix (no ranking)

This matrix is intentionally non-numeric. “Native mechanism” means the family offers a useful primitive; “must be
externalized” means the primitive is not sufficient for the approved invariant. `Hard-fail trigger` is the condition
that rejects the proposed use until compensated.

| Boundary | Integrated BaaS | Firebase/Firestore | Managed relational + API + object | Appwrite | Edge SQLite/Workers | Self-host baseline |
|---|---|---|---|---|---|---|
| Privileged API/RLS | Postgres/RLS useful, service-key bypass must stay server-side; contextual API required. | Rules useful for clients; Admin/IAM bypass requires policy API. | Explicit API is first-class; DB RLS/IAM defense only. | Permissions useful; API-key Server SDK bypass requires policy API. | Worker boundary useful; bindings/account admin remain privileged. | Full control possible; root/owner bypass must be governed. |
| Review/publish/recall | Needs external workflow/negative authority/generation. | Document transaction not governance; needs external coordinator. | API + DB guard can model it; negative authority still separate. | Table transaction not governance; needs external coordinator. | DO/D1 can serialize bounded scope; global fence external. | Custom model possible; separate trust roots/roles required. |
| Protected audit | External custody/fallback mandatory. | External custody/fallback mandatory. | External custody/fallback mandatory. | Built-in logs are secondary; external custody mandatory. | External custody/fallback mandatory. | Possible, but must be outside mutable host/admin. |
| Cross-plane consistency | DB/outbox only; object/audit separate. | Firestore batch only; Storage/audit separate. | DB/outbox only; object/audit separate. | TablesDB transaction only; Storage/audit separate. | D1 batch/DO only; R2/audit separate. | Custom coordinator required. |
| Offline package | API worker can build; Realtime/cache not truth. | Native offline cache has LWW; explicit package required. | Explicit builder/manifest fits. | Builder needed; realtime/permissions not closure. | Edge builder possible; limits/cache need proof. | Builder fully controlled; ops burden. |
| User reconciliation | API idempotency/conflict ledger required. | Offline transaction failure + LWW require separate queue/conflict model. | Natural API/DB operation ledger fit. | API/row transactions help, domain conflict remains external. | DO can serialize a scope, not global/device reconciliation. | Full custom control; must be automated. |
| Media quarantine | Storage policies do not scan/verify; external quarantine. | Storage Rules validate metadata; external quarantine. | Separate object boundary naturally explicit; scanner still external. | Storage permissions/upload only; external quarantine. | R2 transport only; Object Lock currently unavailable; external quarantine/custody. | Dedicated quarantine boundary required. |
| Restore/anti-resurrection | DB backup omits Storage objects; external floor. | PITR/export/Storage separate; external floor. | Managed PITR creates new DB; floor/cutover explicit. | Plan/database-dependent; external floor. | D1 restore in place; external floor. | Maximum control, maximum operational burden. |
| Provider/account/billing | One integrated control-plane blast radius; explicit hold/exit. | Billing required for managed export; IAM/account coupling. | Managed DB/object/API accounts still separate dependencies. | Plan/self-host behavior; audit/backup retention varies. | Plan limits/account coupling; edge failure states explicit. | Host/registrar/DNS/storage/admin dependencies explicit. |
| Export/clean-room | `db dump` + objects/config/audit/floor, not clone alone. | Service-specific export/partial semantics; full manifest required. | Logical SQL + object/policy/audit manifest; strong exit potential. | API/data/object/config/audit manifest required. | D1/R2/DO/account export manifest required. | Standard formats possible; bootstrap proof required. |
| AI/no-owner-debug | Keep service keys/SQL owner outside task packs. | Keep Admin SDK/IAM owner outside task packs. | Narrow API/migration runbooks; no DB superuser. | Keep API keys/Console owner outside task packs. | Keep account/Wrangler/root outside task packs. | Root/SSH/DB admin outside ordinary AI tasks. |
| Hard-fail pattern | Unpartitioned integrated project treated as all-plane authority/recovery. | Offline LWW/rules/Admin path treated as high-consequence authority. | API/object/audit/exit/ops proof missing. | API-key bypass/log retention/backup treated as complete control. | Edge/local restore or object consistency treated as global authority. | Owner-operated single host/same-account recovery. |

## 13. Candidate-specific hard-fail register and compensating-control minimum

| Candidate | Hard-fail IDs that must be closed | Minimum control family before ADR consideration |
|---|---|---|
| Integrated BaaS | `HF-BAAS-01..12` | Independent API/policy, release/suspension, protected audit, quarantine, package builder, floor and clean-room exit. |
| Firebase/Firestore | `HF-FS-01..12` | Admin/IAM gateway, no critical LWW/offline authority, explicit package/operation model, external audit/quarantine/floor, cost/exit evidence. |
| Managed relational + API + object | `HF-RDB-01..11` | API is mandatory; cross-plane state machine; independent audit/floor; portable exit; automated AI-operable managed recovery. |
| Appwrite | `HF-AW-01..12` | API wraps server keys, external audit/quarantine/floor/exit, transaction boundary not overstated, owner-independent operations. |
| Edge SQLite/Workers | `HF-EDGE-01..12` | Explicit canonical coordinator, external audit/floor, object quarantine/immutability, bounded limits, clean-room exit. |
| Self-host baseline | `HF-SH-01..11` | Managed-like automation, separated failure domains, offsite protected custody, reproducible bootstrap/restore, owner-independent runbooks and cost limits. |

## 14. Comparative conclusions without a winner

1. All six families can expose useful primitives, but none is self-proving. Every family needs the same logical
   boundaries: server/API authority, protected audit, quarantine-first objects, closed package builder, operation ledger,
   anti-resurrection floor, clean-room exit and AI runbooks.
2. Integrated BaaS and Appwrite reduce ordinary integration work, but their integrated credentials/control plane and
   product-specific backup/audit boundaries must not be confused with independent custody or cross-plane recovery.
3. Firebase/Firestore's documented offline transaction failure and same-document last-write-wins make it especially
   unsuitable as the sole high-consequence current/history authority. It remains a possible bounded document/cache
   adjunct only with explicit conflict and package contracts.
4. The managed-relational/API/object family makes the approved boundaries explicit and gives direct transactional and
   portable primitives, but it is not automatically safe: API bypass, RLS bypass, cross-plane atomicity, managed restore,
   object bearer URLs, protected audit, cost and AI-operability still require evidence.
5. Edge SQLite/Workers can be a strong delivery/API or bounded per-aggregate coordination layer. D1 in-place restore,
   R2 bearer/object-lock limitations, per-object transaction scope and account/plan limits prevent using edge placement
   alone as proof of global canonical authority or anti-resurrection.
6. Self-host maximizes control and portability only if the operation is automated and independently recoverable. A
   single-host or owner-SSH baseline is directly incompatible with the approved AI-operated nontechnical-owner model.
7. The correct Phase-4 result is therefore a set of conditional candidates and hard-fail controls, not a winner. A
   later ADR may select a composition only after every selected boundary and its failure-domain assumptions are evidenced.

## 15. Required no-code evidence before a Phase-5 ADR

For each retained candidate/composition, produce the same owner-readable evidence pack:

1. Privileged-path matrix covering browser/API/RLS or Rules/permissions, admin SDK, worker/function, migration,
   restore, object callback, support/break-glass, provider-console and billing paths.
2. `NF-01..NF-12` walkthrough with expected allow/deny/hold/unknown state, side effects, protected evidence, visible
   reason, recovery owner and residual risk.
3. Cross-plane operation state machine and idempotency ledger showing DB/object/audit/outbox partial and unknown outcomes.
4. Release/suspension generation and recall-versus-next-action race proof, including installed/offline residual risk.
5. Machine-verifiable selected-motorcycle/task package closure, optional-media boundary, cache-pressure non-eviction and
   interrupted/mixed-package rejection.
6. User local-operation reconciliation matrix covering retry, duplicate, conflict, device loss, clone/restore and
   account-light history transfer.
7. Quarantine/URL retrieval/preview boundary with original/derived lineage and no ambient credentials/network.
8. Restore drill from an old backup containing revoked role, recalled content, deleted private data and already accepted
   operation; prove monotonic floor and protected audit reconciliation.
9. Coordinated export manifest plus clean-room import outside the source provider; run negative authorization, deletion,
   classification and suspension tests before cutover.
10. Provider/account/billing/region/identity/DNS/key/support failure state model; current staged costs, caps/overage,
    egress and deferred/optional costs; no unapproved purchase assumption.
11. AI task packs with allowed/forbidden scope, credential class, dry run, stop condition, evidence, forward recovery and
    independent reviewer; owner action limited to understandable approvals.
12. Independent review of the evidence pack; unresolved critical item remains `HELD` and cannot be offset by price,
    latency, feature breadth or a successful demo.

## 16. Official/primary source ledger

### Integrated BaaS / Supabase representative

- [Supabase database overview](https://supabase.com/docs/guides/database/overview) — integrated Postgres foundation.
- [Supabase Row Level Security](https://supabase.com/docs/guides/database/postgres/row-level-security) — grants,
  policies and `service_role`/bypass behavior.
- [Supabase Storage access control](https://supabase.com/docs/guides/storage/security/access-control) — Storage RLS
  and service-key bypass.
- [Supabase database backups](https://supabase.com/docs/guides/platform/backups) — backup/PITR limits and Storage
  object exclusion.
- [Supabase restore to a new project](https://supabase.com/docs/guides/platform/clone-project) — database-only clone
  boundary and manual reconfiguration items.

### Firebase / Firestore

- [Firestore security rule conditions](https://firebase.google.com/docs/firestore/security/rules-conditions) — Rules
  and server-library/IAM bypass; Rules are not filters.
- [Firestore securely query data](https://firebase.google.com/docs/firestore/security/rules-query) — all-or-nothing
  query authorization behavior.
- [Firestore transactions and batched writes](https://firebase.google.com/docs/firestore/manage-data/transactions) —
  atomic online transaction behavior and offline failure.
- [Firestore offline data](https://firebase.google.com/docs/firestore/enterprise/enable-offline) — offline persistence
  and same-document last-write-wins.
- [Firestore export/import](https://firebase.google.com/docs/firestore/manage-data/export-import) — billing/Cloud
  Storage dependency, export timing and collection-group/cost behavior.
- [Cloud Storage for Firebase security](https://firebase.google.com/docs/storage/security) — path/metadata/size/type
  Rules, not quarantine or technical verification.

### Managed relational + API + object representative mechanisms

- [PostgreSQL row security policies](https://www.postgresql.org/docs/current/ddl-rowsecurity.html) — default-deny
  behavior and owner/superuser/`BYPASSRLS` bypass.
- [PostgreSQL transaction isolation](https://www.postgresql.org/docs/current/transaction-iso.html) — isolation,
  serialization failure and retry implications.
- [PostgreSQL `pg_dump`](https://www.postgresql.org/docs/current/app-pgdump.html) — logical export and row-security
  behavior.
- [Amazon RDS point-in-time restore](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIT.html) —
  representative managed relational restore-to-new-instance behavior.
- [Amazon S3 presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html) — scoped
  bearer access and expiry/integrity considerations.
- [Amazon S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html) — versioned WORM,
  retention/legal hold and new-version/delete-marker limitations.

### Appwrite

- [Appwrite permissions](https://appwrite.io/docs/advanced/security/permissions) and
  [authentication](https://appwrite.io/docs/advanced/security/authentication) — resource permissions versus
  Server SDK API-key bypass.
- [Appwrite API keys](https://appwrite.io/docs/partners/project/api-keys) — secret/server-side API-key scope model.
- [Appwrite TablesDB transactions](https://appwrite.io/docs/products/databases/tablesdb/transactions) — atomic
  staged database operations and conflict detection scope.
- [Appwrite audit logs](https://appwrite.io/docs/advanced/security/audit-logs) — product Activity log and documented
  retention behavior.
- [Appwrite backups](https://appwrite.io/docs/advanced/security/backups) — plan/database-dependent backup and DR
  behavior.
- [Appwrite self-hosting](https://appwrite.io/docs/advanced/self-hosting) — managed versus manual setup/maintenance.
- [Appwrite Storage upload/download](https://appwrite.io/docs/products/storage/upload-download) — transport/upload
  behavior; no quarantine proof.

### Edge SQLite / Workers representative mechanisms

- [Cloudflare D1 database API](https://developers.cloudflare.com/d1/worker-api/d1-database/) — Worker binding and batch
  transaction behavior.
- [Cloudflare D1 Time Travel](https://developers.cloudflare.com/d1/reference/time-travel/) and
  [D1 limits](https://developers.cloudflare.com/d1/platform/limits/) — in-place restore and plan-sensitive limits.
- [Cloudflare Workers storage choices](https://developers.cloudflare.com/workers/platform/storage-options/) —
  Durable Object per-ID consistency/transaction scope.
- [Cloudflare R2 consistency](https://developers.cloudflare.com/r2/reference/consistency/) — strong object consistency
  and same-key last-writer-wins.
- [Cloudflare R2 presigned URLs](https://developers.cloudflare.com/r2/api/s3/presigned-urls/) — bearer URL behavior.
- [Cloudflare R2 S3 compatibility](https://developers.cloudflare.com/r2/api/s3/api/) — documented unsupported Object
  Locking operations.

### Standards and repository primary research

- [DEBATE-007 primary research](DEBATE-007__DATA_BACKBONE_PRIMARY_RESEARCH.md) — mechanism-level relational,
  document, object, audit, outbox, restore and exit research with primary links.
- [NIST SP 800-53](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final) — least privilege, separation of duties and
  audit protection properties.
- [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)
  — deny-by-default, per-request server-side authorization.
- [OWASP File Upload Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html) —
  allowlists, quarantine/isolation and layered upload validation.
- [OWASP SSRF Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html)
  — URL/address/redirect/egress controls.

## 17. Status and handoff

This document is a Phase-4 no-code research comparison. It records candidate-specific hard fails and minimum
compensating controls; it does not close them with implementation evidence.

- No winner selected.
- No engine, BaaS, API runtime, object store, identity service, backup tool, cloud, paid plan or self-host deployment
  is approved.
- No application code, prototype, proof-of-concept, executable spike or purchase is authorized.
- Any candidate lacking one critical `NF` proof remains `HELD`; cost, latency or convenience cannot compensate for a
  safety/data-continuity hard fail.
- The next controlled step is an equal no-code ADR evidence pack for the retained candidate compositions, followed by
  independent review. Gate 4 → 5 remains closed.
