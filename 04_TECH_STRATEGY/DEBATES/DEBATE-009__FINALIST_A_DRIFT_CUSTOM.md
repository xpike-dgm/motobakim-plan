# DEBATE-009 — Finalist A: App-Owned SQLite/Drift + Kavriva Custom Bounded Package/Delta + Durable Operation API

Status: `FINALIST DOSSIER / NO-CODE / EVIDENCE PENDING / NO WINNER`  
Date: 2026-09-18  
Candidate: `A`  
Scope: Flutter consumer mobile, Android-first / iOS-later, managed Supabase-centered backend working direction  
Decision level: Equal Phase-4 no-code finalist dossier; not an ADR

## 1. Executive disposition

Finalist A means:

1. an app-owned SQLite local data boundary exposed through Drift's typed/generated schema and transaction facilities;
2. a Kavriva-owned, task-scoped bounded package and delta protocol rather than a general database replica;
3. a Kavriva-owned durable local operation/outbox and reconciliation contract behind the server/API boundary; and
4. the `DEC-0035` managed Supabase-centered backend direction used only through the Kavriva API authority boundary.

This is a candidate shape, not an implementation claim. Drift supplies useful local database primitives, but it does not
provide Kavriva's package authority, recall floor, delta correctness, conflict policy, idempotency contract, encryption
key lifecycle, restore quarantine or server authorization. Those semantics remain product/API obligations.

Current no-code result:

| Evidence family | `PASS` | `HELD` | `REJECT` |
|---|---:|---:|---:|
| 18 DEBATE-009 equal repository scenarios (`EQ-01`–`EQ-18`) | 0 | 18 | 0 |
| 18 mobile-platform failure scenarios (`MPR-01`–`MPR-18`) | 0 | 18 | 0 |

Every scenario is `HELD` because this phase has no application code, real-device run, restore/exit drill, encryption-key
proof, accessibility evidence or production cost closure. The candidate has documentary mechanisms and a coherent
requirements mapping, but no marketing page, README, package metadata, “offline-first” label, “reactive” claim or API
primitive is counted as a safety `PASS`.

`HELD` does not mean the candidate is rejected. It means the candidate remains eligible for the same later evidence gates
as every other finalist. A `REJECT` result is reserved for an observed or required unsafe property such as partial-package
use, silent high-consequence last-write-wins, restore resurrection, plaintext key fallback, direct canonical authority or
an owner-only repair path.

## 2. Authority, scope and evidence labels

### 2.1 Binding repository authority

This dossier is derived from:

- `04_TECH_STRATEGY/DEBATES/DEBATE-009__OFFLINE_SYNC_REQUIREMENTS_SYNTHESIS.md` — candidate-neutral requirements,
  frozen fixture, `EQ-01`–`EQ-18`, hold/reject rules and AI-operability conditions;
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__OFFLINE_SYNC_OPTIONS_PRIMARY_RESEARCH.md` — Drift/SQLite, package/delta,
  outbox, encryption, background, Supabase coupling, cost, exit and A-specific hold evidence;
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__MOBILE_PLATFORM_FAILURE_RESEARCH.md` — official Android/iOS/Flutter limits and
  `MPR-01`–`MPR-18` equal failure scenarios;
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__MANAGER_PROPOSAL.md` — reversible two-lane proposal and reversal triggers;
- `00_CONTROL/DECISION_LOG.md` — `DEC-0033`, `DEC-0034`, `DEC-0035`.

### 2.2 What the decisions mean for this candidate

- `DEC-0033` carries Flutter into later planning, with Android first and iOS later. Portable product/data/safety truth
  must remain outside Flutter presentation code; native/generated/channel effects must be task-addressable and exportable.
- `DEC-0034` requires canonical transactional authority per domain, server/API-mediated sensitive access, bounded
  versioned offline packages, durable identified operations, visible conflict/hold/unknown states, distinct current/
  history/protected-audit/object meanings and anti-resurrection recovery floors.
- `DEC-0035` carries a managed Supabase-centered physical backend direction: PostgreSQL/Auth/private Storage are initial
  candidates, but the Kavriva API remains mandatory; RLS/Storage are defense in depth; `service_role` stays server-only;
  Studio is not Internal Operations; object bytes, protected audit and non-restorable floors need independent recovery
  evidence; no account, purchase, plan or Phase-5 ADR is approved.

### 2.3 Evidence labels

The source research distinguishes:

- `CONFIRMED`: a documented Drift/SQLite/platform/provider primitive or stated platform limitation;
- `INFERRED`: a candidate design consequence that still needs Kavriva contract and acceptance evidence;
- `OPEN`: a policy, implementation, cost, device or recovery question not closed by the sources;
- `HELD`: the candidate cannot claim acceptance until the required later evidence exists.

No source's marketing or README capability is treated as a recall, restore, idempotency, accessibility, encryption,
provider-exit or safety proof.

## 3. Candidate boundary and authority flow

The candidate has two durable local lanes and separate re-fetchable/temporary material:

```text
Kavriva API
   ├── scoped complete package / exact-base delta
   │      -> staging -> manifest/digest/dependency checks
   │      -> atomic Drift transaction -> accepted PackageStore
   └── authenticated user command
          <- durable local operation + outbox
          -> idempotent submit/status lookup -> accepted/conflict/held/unknown

optional media / temporary transfer / rebuildable cache
   -> separate lifecycle and eviction rules
```

The app-owned database is a local projection, durable-work ledger and package boundary. It is not:

- approval, publication, recall, suspension or current safety authority;
- a full canonical database copy;
- a substitute for protected audit/history or server-generated operation results;
- a substitute for the Supabase/API authority boundary;
- proof that an encrypted/restored/old package remains eligible.

The server/API remains authoritative for current data, sensitive reads, user ownership, official content, eligibility,
publication, recall/suspension, roles, protected audit, migration and deletion. The local app can preserve context and
bounded user work without claiming server success.

## 4. Requirement-to-candidate mapping

| DEBATE-009 requirement | A's intended mechanism | A-specific burden / status |
|---|---|---|
| Bounded task package | Kavriva package manifest, staged rows, dependency closure, digest and generation stored in Drift | Package issuer, schema, integrity, risk and safe-closure contract are custom. `HELD`. |
| Wrong-base delta | Exact base identity/generation/digest check; reject and request a complete compact package | Cursor/delta protocol and reissue behavior are not provided by Drift. `HELD`. |
| Durable local work | Domain row plus operation envelope/outbox in one local transaction | Outbox state/result semantics and server operation ledger are custom. `HELD`. |
| Reconciliation | Foreground/network-return/action-bound API recheck plus operation status lookup | Background is only opportunistic; all boundaries and residual race handling need evidence. `HELD`. |
| Cache eviction | Separate package, optional-media, temporary, pending-operation and user-data lanes; active closure pinned | Storage/backup placement and low-space behavior are app/platform work. `HELD`. |
| Recall/suspension | Tombstone/revocation floor in package/API contract; known negative authority wins | Offline exposure, emergency independence and reach-back are not local DB features. `HELD`. |
| Device loss/restore | Restore quarantine, generation/floor reconciliation and server rebind | Cross-plane manifest, object bytes, audit and key recovery remain open. `HELD`. |
| Account-light migration | Stable local IDs, migration scope preview, conflict/partial state and idempotent migration operation | Wrong-account/clone, private/shared classification and cleanup need protocol and device evidence. `HELD`. |
| Supabase boundary | API-mediated commands/package requests; RLS/Storage defense only | Runtime, auth, privileged paths, outage and provider exit remain unimplemented. `HELD`. |
| AI-operability | Versioned schema/manifests/operation contracts and task-sized changes | Custom semantic surface is large; deterministic task graph and independent review required. `HELD`. |

## 5. Local schema and data-lane dossier

The following are conceptual logical entities, not an approved SQL schema. They are included to make the local contract
addressable and reviewable by AI tasks.

### 5.1 Durable package lane

| Conceptual entity | Minimum meaning |
|---|---|
| `package_manifest` | Package identity, scope (user/account-light, motorcycle/model/year/variant, task), schema/release/capability, base/target generation, issued/expiry context, risk/consequence, suspension/revocation floor, manifest/content digests and complete-closure status. |
| `package_dependency` | Required/optional dependency identity, version/generation, digest, classification, applicability and closure relation. Missing required dependency blocks acceptance. |
| `package_item` / local projection | Version-bound content/claim/step/check/warning/reference data; current projection is disposable relative to server truth and retains historical package identity. |
| `package_tombstone` | Delete/withdraw/recall/supersede generation, scope, reason and anti-resurrection relation. A local row deletion alone is insufficient. |
| `package_stage` | Temporary incoming bytes/rows, expected digest, transfer status, verification status and failure/quarantine reason. It is never current use. |
| `package_media_ref` | Required/optional media identity, digest, size, classification, generation, storage state and re-fetch/eviction policy. Heavy media is separate from required closure. |
| `package_generation` | Accepted complete package and monotonic local observation; it advances only after atomic verification and promotion. |

Required state separation:

- `STAGING` is not `CURRENT`;
- `CURRENT_COMPLETE` is not `CURRENT_AUTHORITY`;
- `RECALL/SUSPENSION/EXPIRED/INCOMPATIBLE/QUARANTINE` cannot be rendered as normal physical application;
- history/provenance and safe recovery can remain available when the normal package is held;
- a package that cannot close every reachable physical state is ineligible, even if its byte count is small.

### 5.2 Durable user-operation lane

| Conceptual entity | Minimum meaning |
|---|---|
| `local_user_record` | User history/evidence metadata, notes, motorcycle context and local outcome with classification, provenance and guide/release version used. |
| `operation_envelope` | Stable operation ID; actor/account-light/profile context; installation/device generation; action/object/scope; payload/content fingerprint; schema/release meaning; expected version/generation; classification; attachment dependencies; local/server timestamps. |
| `operation_status` | `PENDING`, `SUBMITTED`, `ACCEPTED`, `CONFLICT`, `HELD`, `FAILED`, `OUTCOME_UNKNOWN`, `RECONCILING` or equivalent, plus server result/owner/next action when known. |
| `operation_attachment` | Photo/file/evidence identity, digest, size, classification, quarantine/validation/activation state and dependency status. |
| `migration_session` | Source/local scope, target profile, preview/differences, conflict/exclusion set, migration operation ID, partial/unknown/accepted state and reconciliation evidence. |
| `device_installation` | Installation/device generation and binding state used to reject replay from clone/restore/uninstall/reinstall or wrong profile. |

Local persistence is truthful only for the local lane. `ACCEPTED` must come from the server/API result or authoritative
status lookup; a local row written in a transaction is not server acceptance.

### 5.3 Non-durable/re-fetchable lane

Optional media, transfer fragments, thumbnails, temporary manifests, search projections, notifications and rebuildable
cache entries are separate from required package closure, pending operations, user history and protected metadata. They may
be evicted or rebuilt according to explicit policy. They cannot be the only copy of active safe-stop/recovery, pending
work or audit meaning.

### 5.4 Identity, clock, lifecycle and key state

A's local contract must expose, as inspectable states rather than hidden booleans:

- `KeyState`: available, locked, missing, invalidated, auth-required, re-key-required;
- `ClockState`: server time/generation, monotonic interval where useful, device-clock anomaly;
- `LifecycleState`: foreground, background, deferred, killed, resumed;
- `NetworkState`: request result, metered/expensive/constrained hint, timeout, retry, duplicate and unknown;
- `CapabilityState`: client/build/schema compatibility and unknown safety-critical field behavior;
- `RestoreState`: normal, restore quarantine, reconciling, recovery-only, current-authority re-established.

## 6. Schema migration and transaction surface

### 6.1 Documentary primitives

The primary research identifies Drift as providing a typed/reactive SQLite wrapper, generated schema/migration support,
transactions, savepoints and a native background-isolate path. These are `CONFIRMED` primitives. They are not proof that
Kavriva's package/outbox/reconciliation semantics are correct.

The candidate would use those primitives to make these boundaries explicit:

1. stage package rows and media references;
2. verify schema/release/policy/digest/dependency/closure/floor;
3. atomically promote one complete package generation;
4. append a local operation and its outbox record in one transaction;
5. advance a cursor/generation only after the complete delta transaction commits;
6. record tombstone/floor state instead of relying on row deletion;
7. preserve accepted local history and operation evidence separately from disposable projections.

### 6.2 Required migration behavior

| Boundary | A requirement | Evidence status |
|---|---|---|
| Known schema upgrade | Versioned schema snapshots and deterministic stepwise migration; migration result is inspectable/exportable. | Drift mechanism documented; A integration `HELD`. |
| Interrupted migration | Transactional/idempotent step or quarantine; no half-schema write; old valid data remains recoverable. | No implementation/device evidence; `HELD`. |
| Unknown future schema | Do not guess or destructively downgrade; hold/quarantine and show a recovery path. | Product requirement; protocol `HELD`. |
| Low free space | Preflight peak space for old data + new data + verification; fail as `NEEDS_SPACE` rather than overwrite. | Fixture required; `HELD`. |
| Package schema mismatch | Reject/quarantine package or use a complete compatible reissue; do not partially map safety meaning. | Contract proposed; `HELD`. |
| Local/user data migration | Preserve stable IDs, classification, provenance, pending operations and partial/unknown states. | Custom protocol; `HELD`. |
| Rollback/forward recovery | Do not discard newer valid user data or revive revoked/recalled/deleted/accepted truth. | Cross-plane restore evidence absent; `HELD`. |

### 6.3 Transaction limitations

SQLite/Drift local atomicity cannot make a network request, object upload, server mutation and protected audit one physical
transaction. A must therefore expose cross-plane states such as `PARTIAL`, `OUTCOME_UNKNOWN` and `RECONCILING`; it cannot
return a local transaction commit as a global success claim.

An interrupted local transaction must result in either the old complete state or the new complete state. Orphan media,
staged package fragments and unfinished migration artifacts enter quarantine/cleanup, not normal current use.

## 7. Encryption and key lifecycle surface

Drift does not itself provide the required encryption engine. The source research keeps SQLite3MultipleCiphers, SQLCipher
or an equivalent native/platform path open; this dossier does not select one.

Minimum A contract:

- protected fields, local operation data and private media metadata have an explicit at-rest classification;
- key provisioning, secure storage, rotation, re-key/copy, deletion, backup exclusion and restore behavior are documented;
- key states are distinguishable: `KEY_UNAVAILABLE`, `AUTH_REQUIRED`, `KEY_INVALIDATED`, `REKEY_REQUIRED`, `KEY_MISSING`;
- key failure never falls back to plaintext, secret export, silently generated replacement key or silently invisible data;
- crash logs, analytics, exports and AI task contexts cannot contain plaintext secrets or global storage credentials;
- OS backup, server backup, screenshots, exported packages and already exported copies are separately treated as disclosure
  surfaces;
- Android lock-screen/biometric changes and iOS passcode/Keychain/`ThisDeviceOnly` behavior are tested on real devices;
- loss of a local key produces a truthful held/recovery path, not fabricated server completion.

Current result: `HELD`. No encryption mechanism, key custody, restore/re-key matrix or Android/iOS binary evidence is
approved. A README/package claim that “SQLite can be encrypted” cannot close this gate.

## 8. Background, lifecycle and process-failure surface

Android/iOS/Flutter research establishes that process death, Doze/low-power, force-quit, suspension, incoming calls,
thermal pressure and power loss can prevent lifecycle callbacks or background work. Therefore:

- the correctness commit boundary is a local durable transaction, not `onPause`, `onStop`, `didChangeAppLifecycleState`
  or an equivalent callback;
- background work may progress a durable queue or transfer, but is only an opportunistic latency optimization;
- foreground launch/return, network return and next authorized action revalidate package/release/suspension/eligibility;
- force-quit or process termination leaves `PENDING`, `PAUSED`, `FAILED` or `OUTCOME_UNKNOWN`, never an inferred success;
- compact safety/recovery content is separated from optional 150 MB media so optional work can pause/cancel without blocking
  required closure;
- retries are bounded and idempotent; battery/thermal/storage pressure does not create retry storms;
- user-visible Turkish states expose pending, paused, failed, conflict, stale, unknown, blocked and complete to
  TalkBack/VoiceOver/Switch Access without color-only meaning.

Current result: `HELD`. No real Android/iOS lifecycle, force-quit, Doze, background URLSession, low-power, thermal,
accessibility or process-kill evidence exists in this dossier.

## 9. Package, delta and data-usage contract

### 9.1 Complete package as recovery baseline

The compact package is accepted only when it contains the selected motorcycle/model/year/variant and task, exact release/
client contract, fit/readiness context, required warnings/checks, complete safe-stop/recovery closure, dependency closure,
classification, language/units/accessibility meaning, digest and suspension/revocation/freshness context.

The last valid complete package remains intact until its replacement is fully verified and promoted. A staging artifact,
partial download or optional-media-only state is not usable as a package.

### 9.2 Delta behavior

The A delta contract is:

1. API issues a target manifest bound to exact base package identity/generation/digest and client capability.
2. Client checks base identity, digest, generation, scope, schema, dependency closure, classification and negative floor.
3. Any missing base, wrong base, cursor gap, checksum mismatch, out-of-order target, stale/withdrawn/recalled base,
   unknown generation or incompatible client rejects the delta atomically.
4. Client records `REJECTED_WRONG_BASE`/`FULL_PACKAGE_REQUIRED` (or equivalent), retains an active complete safe package if
   still permitted, and requests a complete compact replacement.
5. Cursor/generation advances only after the target package/delta fully commits.
6. Tombstones and recall/deletion generations prevent a late delta or operation from recreating invalid data.

No closest-base merge, partial application, silent downgrade or delta-created positive eligibility is allowed.

### 9.3 Same fixture data-use rules

All A evidence uses the frozen DEBATE-009 fixture:

- compact selected-task transfer up to 12 MB;
- optional high-resolution media separately selected up to 150 MB;
- cellular confirmation above 25 MB;
- 250 MB default re-fetchable content cache excluding user history/photos;
- unrelated 2 GB catalog present only to prove it is not downloaded by default;
- 3/10 motorcycles, 250/2,000 history/evidence records, 50/500 photos at 3 MB, 20/200 pending operations and 3/30
  deliberate conflicts;
- stable Wi-Fi, ordinary cellular, 1 Mbps/300 ms/5% loss, transfer interruption, 72 hours offline, background/lock/call/
  process termination/restart and clock-change/restore profiles.

These are comparison constants, not final product or commercial limits. Required safety/recovery closure cannot be removed
to meet a size number, and transfer size is not peak installed size.

Current result: `HELD`. No candidate implementation demonstrates package size, temporary-space, peak-storage, optional-
media, cellular-consent or 2 GB negative-case behavior.

## 10. Recall, delete, conflict and session behavior

### 10.1 Recall/suspension

A's custom protocol must carry release identity, capability, last authoritative reconciliation context and monotonic
suspension/revocation floor. Supabase Realtime, push, background workers and network callbacks may be hints, but cannot be
recall authority.

Required behavior:

- known suspension/recall blocks normal application for its affected scope;
- offline devices retain an explicit residual race; bounded expiry and next-authorized-request recheck limit exposure;
- foreground/network return checks current release, capability, applicability, freshness and negative generation;
- active work closes/stops/recoveries safely; the same recovery material cannot open unrelated new work;
- publication prepared against an older suspension generation is rejected;
- restore/failover cannot lower the negative floor;
- affected interaction depth (view/open/active step/evidence/completion) remains traceable for proportional reach-back.

The independent emergency suspension plane is outside Drift. A local tombstone can record known negative state, but cannot
invent a recall that the offline device has not received.

### 10.2 Delete/withdrawal

Deletion is a cross-copy operation, not a local `DELETE` statement. The A contract must address current rows, local package,
delta/tombstone, optional media, pending operations, server records, backup/export, restore floors, private/shared/
community/official classification and independent audit/history.

- A server tombstone/floor prevents late package/operation replay from recreating withdrawn/deleted data.
- A local cache purge does not prove server deletion or authority revocation.
- A delete/withdrawal that must preserve attribution, correction history or independent evidence minimizes/redacts payload
  without silently erasing event meaning.
- A late operation against a deleted/recalled resource is rejected or held according to domain policy, never implicitly
  re-created.
- Sign-out, role revoke, password/session termination and device loss have explicit local partition/token/queue/media
  cleanup states; no stale token success.

### 10.3 Conflicts and idempotency

The local row plus outbox receives a stable operation identity, expected base version/generation, payload fingerprint and
classification. The API records/returns accepted, rejected, duplicate, conflict, held or unknown. A timeout is unknown
until status lookup.

- High-consequence safety, provenance, ownership, entitlement, official-content, deletion, recall and evidence conflicts
  preserve both sides and enter visible review/hold.
- A low-consequence merge is only allowed after field scope, audit meaning, rollback and exposure are explicitly governed.
- A server `2xx`, queue drain or local transaction does not by itself prove accepted technical truth.

Current result: `HELD`. No A implementation, negative test, conflict policy, delete floor or session/revoke drill exists.

## 11. Restore, device loss and account-light migration

### 11.1 Restore/device loss

An Android/iOS backup, reinstall, clone or restored SQLite file is input to `RESTORE_QUARANTINE`, not current authority.
The re-entry check must reconcile:

- current package/release/capability/applicability/freshness;
- suspension/revocation/security/deletion/accepted-operation/migration floors;
- operation ledger and installation/device generation;
- history/provenance/protected audit checkpoint;
- object bytes/manifests/classification;
- identity/session/policy/configuration;
- newer valid user data that an old binary/schema must not discard.

The system distinguishes server-accepted, synchronized, pending/local-only, local-only media and irrecoverable local
state. It never claims recovery of data that never left the lost device.

### 11.2 Account-light → profile

Migration uses a stable local identity and durable migration operation:

1. show source/target scope, dates, guide versions, classifications, attachments, pending operations, conflicts and
   exclusions;
2. stage without deleting source local value;
3. upload/reconcile via the server/API with idempotency and authorization;
4. preserve source/date/difference/provenance and historical version meaning;
5. mark partial/conflict/unknown explicitly; only a reconciled result is accepted;
6. retain local safe recovery if migration is canceled, rejected, offline or held.

Wrong-account, clone, stolen-device, revoked-session and profile-binding conflicts quarantine affected work before upload.
Profile creation does not grant current technical truth, entitlement, publication or safety authority.

Current result: `HELD`. No restore, clean-room, device-loss, key-loss, wrong-account or migration evidence exists.

## 12. Supabase/API boundary dossier

### 12.1 Required API contract

The A local protocol must never turn Drift into a direct Supabase authority. The server/API must mediate:

- scoped package/delta requests;
- sensitive reads and all canonical mutations;
- user-operation submission and status lookup;
- account/profile migration;
- official content, eligibility, publication, recall/suspension, deletion and role/policy operations;
- protected audit and restore/exit transitions.

At action time the API checks actor/session, action, object, exact scope, workflow state, classification, consequence,
independence/separation of duties and expected version/generation. Each request binds operation identity, payload digest,
intended effect and a changed-payload rejection rule.

### 12.2 Supabase-specific constraints inherited by A

- Managed Supabase PostgreSQL/Auth/private Storage are initial physical candidates only; exact API runtime remains
  replaceable until the Phase-5 ADR.
- RLS and Storage policies are required defense in depth, not sole approval/publication/recall/provenance/protected-audit
  or separation-of-duties authority.
- `service_role`/privileged secrets remain server-only and never enter the Flutter bundle, browser bundle, repository,
  logs, exports or ordinary AI task context.
- Supabase Studio/provider administration is not the Kavriva Internal Operations product and cannot become a hidden
  approve/publish/recall/role/audit bypass.
- Database backup does not cover Storage object bytes. Object export/backup, protected audit and the non-restorable
  negative/deletion/accepted-operation floor require sufficiently independent custody and cross-plane evidence.
- Provider/account/billing/region/identity/DNS/key/support outage maps to owner-readable `HELD`, `UNKNOWN`,
  `SERVICE_UNAVAILABLE`, `BILLING_HELD` or equivalent; owner SQL/SSH/debug is not an operating model.
- Stable logical IDs, package/operation/tombstone/conflict manifests and clean-room import are required for exit.

### 12.3 API response/state requirements

The API cannot rely on client timeout or provider retry behavior for mutation correctness. It must expose authoritative status
lookup independent of the initiating request and distinguish:

`ACCEPTED`, `REJECTED`, `DUPLICATE/ALREADY_APPLIED`, `CONFLICT`, `HELD`, `FAILED`, `PARTIAL`, `OUTCOME_UNKNOWN` and
`RECONCILING` (or semantically equivalent states).

Provider native Realtime may reduce notification latency, but it does not replace package generation, tombstones,
foreground/action revalidation, idempotent commands or protected audit.

Current result: `HELD`. No API, auth, privileged-path, object-capability, provider outage or cross-plane restore evidence
exists.

## 13. Maintenance surface matrix

| Surface | A's intended control | Main maintenance risk | Required evidence before any `PASS` |
|---|---|---|---|
| Local schema | Drift-generated schema snapshots and versioned local entities | Generated/manual drift, data-format incompatibility | Android/iOS old/new schema and unknown-schema matrix; exported migration log. |
| Migration | Stepwise, idempotent, transactional/quarantined migrations | Low space, interruption, destructive reset, owner repair | Kill/power/low-space/future-schema real-device evidence. |
| Transaction | Local row + outbox/package promotion atomic at SQLite boundary | Cannot span server/object/audit; orphan dependencies | Interrupt and cross-plane unknown/partial walkthrough. |
| Encryption | External SQLite encryption + platform secure key state | Key invalidation, backup leakage, re-key, native ABI/plugin risk | Mechanism decision, key lifecycle, lock/passcode/reinstall/restore tests. |
| Key custody | No plaintext fallback; explicit key states and re-auth/recovery | Lost key or auth-bound key can strand local data | Device/key-loss matrix and owner-readable recovery. |
| Background | Best-effort queue/transfer progress; foreground correctness | Doze/suspend/force-quit/process death; retry storm | Android/iOS lifecycle, force-quit, low-power and reconnect evidence. |
| Restore | Restore quarantine and negative-floor reconciliation | Old backup resurrects recall/delete/accepted operation | Cross-plane manifest, restore drill, clean-room import and forward-recovery evidence. |
| Data usage | Task package, optional media separation, 2 GB negative test | Full-library drift, hidden cellular transfer, peak storage | Size/consent/temporary-space/storage-pressure evidence. |
| Recall | Generation/tombstone/floor + API revalidation | Offline residual race, independent suspension path | Recall/delete/reconnect/old-client and emergency-plane walkthrough. |
| Delete/withdrawal | Tombstones, copy lifecycle and anti-resurrection | Late operation or backup reintroduces deleted data | Cross-plane delete/restore/export test with classification. |
| Conflict | Stable op ID, expected version, explicit high-consequence hold | Custom merge semantics grow without audit/rollback | Duplicate, timeout, concurrent delete/update and review evidence. |
| API | One Kavriva server/API authority | Hidden provider/admin/direct paths; outcome ambiguity | Negative authorization matrix and status lookup drill. |
| Supabase boundary | RLS/Storage defense plus server policy | Coupling, provider outage/billing, object/audit recovery gaps | `DEC-0035` reversal triggers and independent recovery evidence. |
| AI task surface | Portable manifests/schema/operation contracts | Largest custom semantic surface; undocumented hidden state | Bounded task packs, implementer/reviewer/validator separation and no-owner-debug proof. |
| Exit | SQLite/JSON/package/operation/tombstone/conflict/object manifests | Protocol/runbook migration burden; API/Supabase remains | Clean-room export/import preserving negative behavior and history. |
| Cost | No separate sync-provider fee assumed; bounded data usage | Custom engineering/observability/backup/key/incident cost; Supabase overage | Normalized bill of materials, cap/overage, incident/restore/exit drills. |

## 14. Equal fixture and no-code evidence method

The candidate must be evaluated under the same DEBATE-009 fixture as all retained alternatives:

- 12 MB compact package, 150 MB optional media, 25 MB cellular confirmation, 250 MB re-fetchable cache, 2 GB unrelated
  catalog negative case;
- 3/10 motorcycles, 250/2,000 history/evidence records, 50/500 photos at 3 MB, 20/200 pending operations, 3/30
  deliberate conflicts;
- one duplicate operation, partial upload, corrupt package, interrupted DB change, source correction, content withdrawal
  and safety recall;
- Android constrained/main and iOS oldest/current cohorts;
- stable Wi-Fi, ordinary cellular, 1 Mbps/300 ms/5% loss, transfer interruption, 72 hours offline, background/lock/call/
  process termination/restart and clock-change/restore;
- Turkish TalkBack/VoiceOver/Switch Access states and Android-first/iOS-later evidence lanes.

No candidate-specific reduction is allowed. Drift's local transaction capability does not permit skipping platform failure,
restore, encryption, data-use, accessibility, API or exit evidence.

## 15. EQ-01–EQ-18: equal repository scenarios

All rows below use the same fixture. The result is `HELD` for each row because the candidate has no implementation or
execution evidence in this no-code phase.

| ID | A-specific expected behavior | Missing proof / hold reason | Result |
|---|---|---|---|
| `EQ-01` | API issues only selected motorcycle/task compact package; Drift staging excludes the 2 GB catalog and promotes only complete closure. | No implementation or transfer/size evidence; manifest/dependency closure remains proposed. | `HELD` |
| `EQ-02` | Interrupted/corrupt package stays in staging; digest/manifest/dependencies must pass before atomic promotion; prior complete package remains. | No process-kill/atomic-promotion test or exportable state evidence. | `HELD` |
| `EQ-03` | Delta requires exact base ID/generation/digest/capability; wrong-base/gap/out-of-order delta is rejected and full compact package is requested. | Custom delta/cursor protocol and reissue behavior are not implemented or tested. | `HELD` |
| `EQ-04` | 72-hour offline behavior is bounded by manifest risk/freshness and closure; unknown/high-consequence state holds without pretending the local DB is authority. | Numeric windows, risk taxonomy and real device/offline evidence remain open. | `HELD` |
| `EQ-05` | Missed push/Realtime event does not authorize a recalled package; foreground/network/action revalidation compares tombstone/floor and blocks known suspension. | Recall propagation, residual race and independent emergency path are unproven. | `HELD` |
| `EQ-06` | Network return drains durable operation IDs and asks API for status; duplicate/out-of-order results remain explicit; server generation is authoritative. | No API/idempotency/status lookup or reconnect evidence. | `HELD` |
| `EQ-07` | Expiry during active work stops ordinary next step at the reviewed boundary while safe-stop/recovery remains in the pinned complete package. | Guide-specific decision boundaries and active-work device evidence are absent. | `HELD` |
| `EQ-08` | Material guide change closes old continuation; current physical state is captured and only a reviewed safe remap may reopen. | Remap semantics and correction reach-back are not implemented/tested. | `HELD` |
| `EQ-09` | Clock/reboot/restore cannot extend eligibility; old SQLite/package is quarantined and reconciled against server release/suspension/deletion/accepted-operation floor. | Restore drill and independent floor/object/audit evidence are absent. | `HELD` |
| `EQ-10` | Client capability envelope rejects unknown safety-critical fields and uses full compatible reissue; teaching/history/recovery only remain if representable. | Old-client matrix and compatibility enforcement are unproven. | `HELD` |
| `EQ-11` | Same operation ID/payload fingerprint resolves duplicate/timeout through API status; no blind second publication/recall/approval effect. | Operation ledger and outcome-unknown API are not implemented. | `HELD` |
| `EQ-12` | High-consequence conflict preserves both sides and enters visible hold/review; any low-risk merge is explicit and reversible. | Field classification/merge policy and audit evidence are open. | `HELD` |
| `EQ-13` | Optional media/unused re-fetchable content is evicted first; active closure, pending operations and required attachments are protected. | Low-storage/peak-space/eviction tests are absent. | `HELD` |
| `EQ-14` | Device-loss recovery distinguishes server-accepted, synchronized, pending/local-only, media and lost state; no local-only success is invented. | Device replacement, key, server rebind and loss evidence are absent. | `HELD` |
| `EQ-15` | Account-light migration previews scope, preserves source, uses stable IDs/idempotency and exposes private/shared/conflict/partial states. | Migration protocol, wrong-account/clone and conflict review are open. | `HELD` |
| `EQ-16` | API/provider/billing outage holds positive mutation and exposes `UNKNOWN`/`HELD`/`UNAVAILABLE`; bounded local/reference/recovery remains. | Provider runtime, outage runbook, cost controls and owner-operability evidence are absent. | `HELD` |
| `EQ-17` | Publication operation binds current suspension generation; a newer suspension wins and an older/in-flight publish cannot clear it. | Cross-domain release fence, protected audit and emergency path are unimplemented. | `HELD` |
| `EQ-18` | Restore/export/exit carries a consistency manifest across DB, objects, audit, identity/policy, package generations, operations and negative floor; clean-room import rechecks behavior. | No cross-plane restore/exit drill or independent custody proof. | `HELD` |

## 16. MPR-01–MPR-18: mobile-platform failure scenarios

The following rows apply the official Android/iOS/Flutter failure findings to A. Platform APIs are evidence inputs, not
automatic product guarantees.

| ID | A-specific expected behavior | Missing proof / hold reason | Result |
|---|---|---|---|
| `MPR-01` | Durable Drift lanes retain history, pending operations, package manifest and required closure when re-fetchable cache is cleaned; cache miss triggers rebuild/redownload only. | Storage placement, purge, backup and cold-start evidence absent. | `HELD` |
| `MPR-02` | Stage + manifest/digest/dependency verification precedes promote; old complete generation survives a kill; user sees paused/failed, not complete. | No 12 MB interrupted-transfer and promote evidence. | `HELD` |
| `MPR-03` | Drift transaction commits history/outbox/media metadata all-or-nothing; orphan media is quarantined; operation ID does not duplicate. | No power-loss/process-kill transaction and orphan cleanup evidence. | `HELD` |
| `MPR-04` | Correctness is committed before lifecycle callbacks; missing `onPause`/`onStop`/Flutter lifecycle notification cannot erase or falsely complete work. | No lifecycle/process-death real-device run. | `HELD` |
| `MPR-05` | Auto Backup/iOS restore enters quarantine; restored package/identity/generation/digest and negative floor reconcile before authority; cache is rebuildable. | OS-specific backup scope, restore-before-launch and cross-plane evidence absent. | `HELD` |
| `MPR-06` | Uninstall/reinstall does not assume local state; re-auth/API rebind and explicit local-loss/recovery path handle missing key/pending work; old cache grants no new entitlement. | Android/iOS reinstall, backup/keychain and device-binding evidence absent. | `HELD` |
| `MPR-07` | Key unavailable/invalidated/auth-required/rekey-required are separate states; no plaintext or silent replacement-key fallback. | Encryption mechanism and secure key lifecycle are open; no locked/passcode/biometric tests. | `HELD` |
| `MPR-08` | Drift schema migration is versioned/idempotent/transactional or quarantined; low space/future schema does not destructive-reset user data. | Old/new build, low-space, interruption and future-schema matrix absent. | `HELD` |
| `MPR-09` | Doze/iOS suspend/force-quit only delay queue/transfer; foreground resumes the same durable state; no background completion guarantee. | Android/iOS scheduler/force-quit evidence absent. | `HELD` |
| `MPR-10` | Compact required closure proceeds independently; optional 150 MB media pauses/cancels; retry storm and battery/thermal starvation are avoided. | Battery/thermal/low-power measurements and scheduling evidence absent. | `HELD` |
| `MPR-11` | Stable operation ID, idempotency key and expected version handle 1 Mbps/latency/loss, kill and reconnect; accepted is not inferred from callback. | Network-loss/duplicate/out-of-order API evidence absent. | `HELD` |
| `MPR-12` | Measured package size is shown; cellular >25 MB requires explicit choice; no hidden full catalog/optional transfer; required closure is not trimmed. | Android/iOS metered/Low Data Mode/consent evidence absent. | `HELD` |
| `MPR-13` | Peak space preflight covers old+new+verification; optional cache evicts first; required closure/history/pending work are protected; failure is `NEEDS_SPACE`. | Low-storage/removable-storage/iOS purge behavior not exercised. | `HELD` |
| `MPR-14` | Server generation/time and monotonic intervals handle clock anomaly; device wall time cannot freshen stale content or skip recall/expiry. | Time-change/restore/reconnect evidence absent. | `HELD` |
| `MPR-15` | All sync/recovery states have Turkish semantic labels/value/hints and accessible actions under TalkBack/VoiceOver/Switch Access; color/icon is not sole meaning. | Real-device assistive-technology evidence absent. | `HELD` |
| `MPR-16` | Drift/domain state is portable from Flutter UI; channel/plugin/native errors are versioned/exportable; Android success does not close iOS; owned fallback/reversal trigger remains. | Encryption/native/platform package choice and iOS lane evidence absent. | `HELD` |
| `MPR-17` | Compact core is complete without optional media; media has separate digest/classification/lifecycle; 250 MB cache pressure evicts media, not closure; 2 GB is never selected. | Peak installed size and optional-media/cache evidence absent. | `HELD` |
| `MPR-18` | Exact client/package/release/generation compatibility and suspension floor reject mixed/old/recalled state; rollback cannot revive negative state. | Cross-client, mixed-manifest, recall and anti-resurrection device evidence absent. | `HELD` |

## 17. AI task and maintenance operating model

Candidate A's main advantage is control over the package/operation format. Its main risk is that custom semantics are the
largest hidden change surface among the retained candidates. “Custom” is acceptable only if it is documented and split into
small, independently reviewable AI tasks.

### 17.1 Required task families

Each task must have a bounded context pack, explicit input/output contracts, fixture references, forbidden scope, stop
conditions and independent validation:

1. local schema and generated migration snapshot;
2. package manifest/dependency/digest/closure and staging promotion;
3. exact-base delta/cursor/tombstone/anti-rollback protocol;
4. durable operation envelope/outbox/status and idempotency ledger;
5. conflict/hold/review semantics by consequence and classification;
6. cache lanes, active-work pinning, low-space and user cleanup;
7. key state/encryption/backup exclusion/re-key behavior;
8. lifecycle/background/network/clock state mapping;
9. restore quarantine, device generation and cross-plane recovery manifest;
10. account-light/profile migration and wrong-account/clone quarantine;
11. API authorization/status lookup/object capability and Supabase boundary;
12. recall/suspension/delete/tombstone/reach-back and old-client handling;
13. Android/iOS platform bridges, accessibility and release evidence;
14. export/clean-room exit and cost/overage/incident runbooks.

### 17.2 AI-operability constraints

- Manifests, operation schemas, migration snapshots, tombstones, conflict records and state transitions must be portable,
  diffable and graph-linked to task/requirement/scenario IDs.
- Implementer, reviewer and validator roles remain separate. A generated migration or green unit check does not prove
  cross-device restore, recall, accessibility or content correctness.
- AI receives least-privilege task credentials only; it cannot receive `service_role`, unrestricted SQL/SSH, global object
  credentials, signing/recovery keys, billing authority or sole high-consequence approval.
- Provider changelog, Flutter/Dart SDK, Drift generator, SQLite/encryption ABI, Supabase API/Auth/Storage and cost changes
  are explicit dependency-watch inputs.
- Unknown/partial/timeout/quarantine states must be observable; AI must not infer success from a missing error.
- If evidence or owner-readable recovery is missing, task status is `HELD`, not “probably works.”
- The nontechnical owner must not debug native builds, repair migrations, read raw logs, run SQL/SSH, recover secrets or
  arbitrate an unresolved high-consequence conflict.

### 17.3 Required AI simulation before any implementation decision

The manager proposal requires at least two no-code task simulations using the same fixture:

- an interrupted compact package with wrong digest/process termination followed by complete-package recovery;
- a conflicting offline user operation with lost response, duplicate retry, attachment dependency and explicit resolution.

The task simulation must show bounded context, changed files/contracts, evidence produced, review handoff, failure/rollback
path and owner-readable output. No code is authorized by this dossier.

## 18. Exit, portability and provider coupling

### 18.1 What is portable in A

The candidate can define portable export forms for:

- package manifests, dependencies, generations, digests, classifications and tombstones;
- operation envelopes, statuses, conflicts, accepted-operation identities and migration sessions;
- SQLite logical local data, JSON manifests and historical/provenance relations;
- object identities/digests/generation/classification without exporting raw secrets;
- API contract/version/capability envelope and restore/quarantine runbooks.

This is a control opportunity, not proof of exit. The custom protocol, conflict semantics, API implementation and Supabase
current state still require a clean-room import/replay/negative-behavior drill.

### 18.2 Exit requirements

An A exit claim is forbidden unless an independent environment can:

1. import current/history/operation/conflict/tombstone/package/object/audit manifests;
2. preserve classification, attribution, deletion/withdrawal and negative floors;
3. prevent recalled/deleted/accepted operations from resurrection;
4. recover account/profile mapping and local pending-operation semantics;
5. reissue a complete bounded package and reject wrong-base/mixed deltas;
6. represent `HELD`, `UNKNOWN`, `CONFLICT`, `RECOVERY_ONLY` and `RESTORE_QUARANTINE` states;
7. continue without provider-console authority or owner SQL/SSH repair.

`DEC-0035` retains Neon + independent API + Cloudflare R2 as a documented fallback, not an automatic parallel implementation
or approved purchase. A's app-owned protocol may reduce sync-provider coupling, but it does not remove Supabase/API exit
work.

## 19. Cost and data-consumption dossier

### 19.1 Cost categories

| Category | A-specific reading | Status |
|---|---|---|
| Sync-provider fee | No separate managed sync-provider fee is assumed for Drift/custom protocol. | `CONFIRMED` as a cost category, not zero total cost. |
| Product-wide baseline | Managed Supabase DB/Auth/private Storage/API, object/audit backup, monitoring, identity/notifications, devices, stores and qualified safety/accessibility review. | Required for all candidates; exact BOM `OPEN`. |
| A-specific engineering | Package/delta protocol, operation ledger, conflict/reconciliation, tombstone/recall floor, migration, observability, encryption/key integration and two-platform evidence. | Likely larger custom surface; not priced. `HELD`. |
| A-specific maintenance | Drift generator/schema changes, SQLite/encryption ABI, Flutter/Dart upgrades, platform lifecycle, native/channel and iOS-later parity. | Must be taskized and costed; `HELD`. |
| Optional/deferred | Realtime notification acceleration, heavy media, advanced PITR, CDN, extra replicas/support. | No purchase approved. |
| Scale-triggered | Supabase compute/storage/egress/object/version/audit/backup/API usage, optional media and incident/restore/exit events. | Usage caps/overage not fully bounded; `HELD`. |
| Exit cost | Clean-room import, API/protocol migration, replay of operation/conflict/tombstone history and key/object transition. | Must be separately costed; `HELD`. |

The Supabase Pro headline is not the safe total and is not a purchase approval. The owner's future TRY 2,000–3,000/month
planning ceiling remains a ceiling, not spend authority. Before any account/plan decision, the equal worksheet must show
closed-test, minimum-safe Android production, P2/P3, incident-month, restore-drill and exit-drill costs with tax/FX,
overage, hard-stop/soft-alert behavior and exit path.

### 19.2 Data-usage reading

A's app-owned package protocol can explicitly prevent full-library replication and keep optional media on demand, but it
must still prove:

- 12 MB compact closure and peak temporary space;
- 150 MB optional-media pause/cancel/eviction;
- >25 MB cellular confirmation;
- 250 MB cache policy without user-history/photo loss;
- 2 GB unrelated catalog never selected;
- duplicate asset reuse/incremental update only when integrity and exact-base rules are closed;
- outage/retry behavior does not create unbounded transfer loops.

No data-efficiency claim is a `PASS` until these are evidenced on the same fixture.

## 20. Reversal triggers and candidate posture

The A direction must be reopened if any of the following occurs:

1. package/delta/checkpoint or operation semantics cannot be represented as small, testable AI task contracts;
2. migration, transaction, process-death or restore behavior requires owner debugging;
3. selective transfer violates the approved package/data-use rules;
4. retry, duplicate, conflict, delete, recall or anti-resurrection semantics remain ambiguous;
5. encryption/key recovery requires an unacceptable unmaintained or unsafe native/plugin dependency with no controlled
   fallback;
6. equal current cost shows a retained challenger closes the required safety/recovery/AI evidence with materially lower
   owner burden;
7. Android-first evidence cannot be reproduced for the later iOS lane;
8. clean-room export/import cannot preserve operations, conflicts, tombstones, package generations and negative behavior;
9. sensitive/high-consequence operations cannot remain behind the Kavriva API boundary;
10. provider/account/billing/region failure or cross-plane restore requires owner SQL, SSH, raw-log diagnosis or technical
    repair;
11. Supabase coupling makes safe exit materially worse than the retained fallback.

PowerSync or another candidate is not an automatic winner after a reversal. It must pass the same 18 EQ + 18 MPR fixture,
cost, recovery, AI-operability, API-boundary and exit gates.

## 21. Final finalist verdict and next evidence

Finalist A is a plausible reversible working candidate for the product's bounded package and owner-operability goals. Its
strongest evidence is control: task scope, package closure, portable local format, explicit operation identity and no
additional sync-provider subscription assumption. Its largest risk is also clear: the custom protocol transfers the
semantic burden for delta correctness, conflict, recall/delete, encryption, background behavior, restore, observability,
AI task governance and cross-platform maintenance to Kavriva.

This dossier records:

- `0 PASS / 36 HELD / 0 REJECT` at the current no-code evidence level;
- no winner and no recommendation to implement;
- no marketing/README capability counted as safety proof;
- no account, purchase, subscription, code, prototype, production claim, Phase-5 ADR or Gate 4 → 5 transition.

Before a later user decision or ADR, the evidence packet must include:

1. equal candidate-neutral walkthroughs for all `EQ-01`–`EQ-18` and `MPR-01`–`MPR-18`;
2. local schema/migration/transaction map with interruption, unknown-schema and low-space evidence;
3. encryption/key/backup/re-key decision and Android/iOS real-device matrix;
4. package/delta manifest, exact-base, tombstone, cursor-gap and anti-rollback contract;
5. durable operation/idempotency/conflict/status API and lost-response walkthrough;
6. recall/delete/session/revoke/old-client/active-work closure evidence;
7. account-light/profile migration, wrong-account/clone and device-loss/restore/quarantine evidence;
8. API/Supabase privileged-path, RLS/Storage defense, provider outage, object/audit/floor and clean-room exit evidence;
9. equal staged cost/data-usage worksheet with caps, overage, incident, restore and exit rows;
10. bounded AI task simulation, independent implementer/reviewer/validator evidence and no-owner-debug proof.

Until those gates close, Finalist A remains `HELD / CANDIDATE EVIDENCE PENDING`.

