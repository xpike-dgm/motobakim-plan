# DEBATE-009 — Independent Reviewer A: Data Safety, Offline Correctness and Platform

Status: `INDEPENDENT REVIEW A / NO-CODE / NO PURCHASE / BOTH FINALISTS HELD / NO WINNER / ADR NOT READY`  
Date: 2026-09-18  
Reviewer posture: adversarial data-safety, offline-correctness, mobile-platform and clean-room review

## 1. Review question and decision posture

This review tests Finalist A (app-owned SQLite/Drift + Kavriva custom bounded package/delta + durable
operation/reconciliation protocol) against Finalist B (PowerSync local SQLite/Sync Streams + Supabase source +
Kavriva API) using the same repository-derived product truth, fixture, failure states and evidence contract.

The review is deliberately hostile to the manager's proposed Drift direction. Drift's typed local persistence,
transactions and migration tooling are useful primitives, but they do not prove bounded package closure, server
authority, operation acceptance, recall, anti-resurrection, encryption/key recovery, background execution or
cross-platform parity. The review is equally hostile to PowerSync marketing: a local queue, Sync Stream, checkpoint,
RLS integration or pricing tier is not a product-safety proof and does not remove Kavriva's authority contracts.

This is a documentary review only. No code, prototype, benchmark, purchase, account, provider commitment, database
change, ADR or phase/gate transition is authorized. `DOCUMENTARY` and `SIMULATED` statements remain evidence plans;
they are not `REAL-DEVICE` or production PASS results.

## 2. Evidence and equality discipline

### 2.1 Repository authority read

The review uses only the current repository evidence:

- `00_CONTROL/DECISION_LOG.md`, especially DEC-0033 (Flutter consumer-mobile direction), DEC-0034 (data backbone,
  canonical authority, durable operations, protected floors and clean-room recovery) and DEC-0035 (Supabase-centered
  physical backend as a replaceable working direction).
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__OFFLINE_SYNC_REQUIREMENTS_SYNTHESIS.md` for product truth, invariants,
  bounded-data rules, EQ-01..EQ-18, hold/reject rules and AI-operability conditions.
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__OFFLINE_SYNC_OPTIONS_PRIMARY_RESEARCH.md` for documented and inferred
  capability boundaries of Drift/custom and PowerSync; capability statements are not acceptance results.
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__MOBILE_PLATFORM_FAILURE_RESEARCH.md` for MPR-01..MPR-18 and the
  Android/iOS failure and evidence boundary.
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__MANAGER_PROPOSAL.md` for the proposed two-lane Drift direction and its
  reversal triggers.
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__FINALIST_A_DRIFT_CUSTOM.md` and
  `04_TECH_STRATEGY/DEBATES/DEBATE-009__FINALIST_B_POWERSYNC.md` for equal finalist dossiers.
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__TASK_SIM_OFFSYNC_001.md` for the P0/G0, P1, D1, O-77, R-12, C-55,
  optional-media and lost-response task chain.

### 2.2 Equality rules applied

1. Both candidates must implement the same logical state contract even if their internal names differ.
2. A provider primitive may be used as transport or storage only when a separate evidence record proves the Kavriva
   contract it carries. “The provider handles it” removes no required scenario.
3. Marketing, README capability, a valid build, a green happy-path demo, a provider backup, an HTTP response, a push
   receipt or a stopped rollout is not by itself a PASS.
4. A local row, stream checkpoint, queue item or provider acknowledgement is never silently promoted to server
   acceptance, package authority, recall authority or provenance truth.
5. A safety violation is not offset by lower cost, fewer files, a managed service, higher throughput or easier setup.
6. `HELD` means the model is potentially safe but documentary, real-device, server-authority, migration/key, exit or
   ownership evidence is absent. `REJECT-IF-UNMITIGATED` means the shortcut is an invalid design, not merely a test
   gap.

## 3. Executive verdict

### 3.1 Current disposition

**Both A and B remain `HELD`; there is no winner and no ADR-ready recommendation.** Both dossiers can describe a
safe-looking recovery path, but neither has proved the negative states on real Android/iOS devices, across restore and
key/migration failure, against the authoritative API, or through a clean-room export/import. The common fixture keeps
the candidates equal; the additional custom surface of A is not a reason to reject it, and the managed/partial-sync
surface of B is not a reason to prefer it.

`PASS_WITH_CHANGES` is appropriate only for continued documentary evaluation. It is not production PASS.

### 3.2 The manager proposal is not yet justified

The manager is directionally right that Kavriva needs a task-scoped package lane, a durable user-operation lane and a
Kavriva API boundary. The manager's proposed primary A direction is not yet evidenced, however. The proposal treats
explicit control and the absence of a sync subscription as advantages, while the hardest semantics—package closure,
generation/floor rules, idempotent command acceptance, delete/recall propagation, restore quarantine, encryption keys,
platform scheduling and exit—become Kavriva's custom burden. A can be the eventual choice only if it closes that burden
with small, machine-checkable contracts and real evidence.

PowerSync cannot be accepted as an automatic fallback. It may reduce transport implementation, but it adds stream,
queue, connector, RLS-equivalence, service, billing, license and restore/exit surfaces. Its documented transport
properties do not provide high-consequence conflict policy, package atomicity, recall floor, API acceptance or
anti-resurrection.

## 4. Adversarial comparison by safety surface

| Safety surface | A — Drift/custom adversarial read | B — PowerSync adversarial read | Reviewer result |
|---|---|---|---|
| Bounded data use | App-owned package scope can be narrow and explicit, but every filter, dependency and media boundary is custom. Drift does not stop a full-catalog query. | Sync Streams can partially subscribe, but a stream projection is not automatically the selected task's complete safety closure. Auto-subscribe, bucket, TTL and filter behavior need a product contract. | Same manifest, size, dependency and negative-scope evidence required. `HELD`. |
| Package closure | Staging/promote/digest/generation/tombstone can be designed, but no Drift primitive makes a package complete or atomic as a product object. | Stream convergence and causal checkpoint can look complete while required rows, tombstones, policy and digest closure are absent. | Stream/table state cannot be package authority. Partial or mixed package active => `REJECT-IF-UNMITIGATED`. |
| Wrong-base/out-of-order delta | A must invent exact base comparison, cursor gap and full-reissue behavior; “custom” makes silent closest-base merge a live risk. | Checkpoint/convergence is not proof that D1's declared base is G0; stream reprocess can hide a semantic mismatch. | Exact base/target/generation contract and atomic reject required. `HELD`. |
| Durable operation and idempotency | Stable operation ID, payload digest, expected generation and status ledger are all Kavriva-owned and therefore all Kavriva liability. | Per-client queue operation identity/FIFO is useful transport, but domain acceptance, duplicate scope and 2xx validation outcome remain API-owned. | Same command ledger, status lookup and same-ID replay proof required. `HELD`. |
| Conflict/provenance | Custom conflict table and API rule can preserve both sources, but no default safety behavior exists. | PowerSync is documented as conflict-unopinionated; LWW examples are unsafe for authority-sensitive provenance. | High-consequence hold/review and protected audit are mandatory. Silent LWW => `REJECT`. |
| Recall/delete | Tombstone, floor, late-operation denial, local purge and object handling are custom and easy to leave incomplete. | RLS/stream deletion/reprocess is delivery/filtering, not a recall floor; cached rows, queues and old clients can outlive it. | Negative authority must win across all planes. Push, stream or row absence is insufficient. `HELD`. |
| Anti-resurrection | A can own a portable floor, but restore/export/replay paths must not omit it. | B must carry the floor outside source-row/stream convergence and rebuild it through service/source restore. | Old package, queue, object, backup or late write must not recreate a recalled/deleted/accepted state. `HELD`. |
| Background/process death | Drift isolate/background open helps execution, not scheduling or callback delivery; local commit boundaries must be explicit. | WorkManager/background-sync evidence is platform-specific; iOS partial/failed fetch and provider callbacks do not establish correctness. | Foreground and restart paths are authority; background is latency only. Real-device evidence absent. `HELD`. |
| Migration/encryption/key | Drift schema snapshots/transactions help, but encryption is not built in; key custody, ABI, rotation and restore are app-owned. | PowerSync local encryption/key setup is likewise app-owned; synced schema/config and service version add migration coupling. | Both need identical migration/key/backup/quarantine evidence. No provider claim closes it. `HELD`. |
| Android/iOS parity | A controls the domain contract but must own native encryption, lifecycle and Flutter bridge differences. | B adds SDK/plugin/generated/native/service differences; Android background results do not transfer to iOS. | Android-first does not waive the iOS-later release gate. `HELD`. |
| Supabase/API boundary | Custom API must enforce auth, idempotency, conflict, floor and audit; direct client writes remain out of scope. | PowerSync upload backend must not turn queue transport into direct canonical writes; RLS protects uploads, streams only downloads. | Kavriva API is the command authority; service-role is server-only; RLS/Storage are defense in depth. `HELD`. |
| Cache/media/eviction | Two lanes are useful only if purgeable cache cannot contain required closure or pending work. | Synced rows, queue, media and cache can be confused by configuration; selective sync is not optional media policy. | Separate durable/core/media/cache classes and pressure rules required. `HELD`. |
| Account-light migration | Stable IDs and operation transfer can be fully app-owned but are custom and privacy-sensitive. | Local queue/stream identity does not prove safe merge into a profile; source partition and duplicate/conflict handling remain custom. | Preview, classification, conflict and accepted/reconciled target are required. `HELD`. |
| Clean-room exit | Portable SQLite/JSON/package/operation formats are possible, but protocol/runbook reconstruction is real work. | Exit includes source DB, PowerSync buckets/service config, stream definitions, upload backend, auth and history; SDK replaceability is not exit. | Export alone is not clean-room PASS. Both require an independent restore/import drill. `HELD`. |
| AI/owner operability | Fewer providers do not mean fewer state transitions; undocumented custom protocol is the largest AI failure risk. | Less transport code may mean more distributed configuration and dashboard/service states; docs/AI links are not owner proof. | Machine-readable state, evidence and owner-safe runbook required for both. `HELD`. |

## 5. Critical findings

### CRIT-01 — Neither local persistence nor partial sync proves package closure

**Observation.** A's Drift database can store a manifest, staging rows, promoted rows and a cursor, but Drift has no
knowledge of Kavriva's dependency closure, safety/recovery completeness, release compatibility, digest or recall floor.
B's Sync Streams can deliver selected rows and a causal checkpoint, but row convergence does not prove that the bounded
task package contains every required entity, tombstone, policy, content digest or safe-stop instruction.

**Failure if ignored.** A half-transferred P1, a filtered B stream, a corrupt row, a missing dependency or an old
manifest can become active while the UI reports a complete task. The 2 GB unrelated catalog can also be pulled through
an overbroad query without either local engine objecting.

**Required correction.** Define one provider-neutral package contract containing user/tenant/task scope, package and
schema/release versions, exact base/target generations, dependency closure, content and manifest digests, expiry,
recall/revoke/delete floor, client compatibility, data classification, optional-media policy and revalidation rule.
Both candidates must stage outside the active pointer, verify the whole closure, promote atomically and retain the
last valid package until promotion succeeds. B's stream is a delivery projection under that contract; A's custom
package is not accepted merely because it is app-owned.

**Disposition.** `HELD` now. If either candidate promotes a partial/mixed package or treats a stream/table/checkpoint
as complete without the common contract, `REJECT-IF-UNMITIGATED`.

### CRIT-02 — Wrong-base and cursor-gap handling is an authority boundary, not a database feature

**Observation.** A must implement exact declared-base comparison and gap handling. B must prevent Sync Stream
convergence, reconnect or checkpoint movement from silently accepting D1 whose base is G-1 while local P0 is G0.
Neither Drift nor PowerSync supplies the Kavriva semantic rule “no closest-base merge, no partial application, no
cursor rollback.”

**Required correction.** Treat the base generation, target generation, schema/policy compatibility and package digest
as an atomic precondition. A mismatch, out-of-order delta, missing predecessor or checksum error leaves G0 active,
quarantines the delta and requests a bounded full reissue. Cursor advancement occurs only after the complete verified
transaction. Recovery must be visible as `DELTA_REJECTED_WRONG_BASE`, `RECONCILING` or `SAFE_STOP`, never as a silent
fallback.

**Disposition.** `HELD` for both. A “nearest generation” merge, or B “checkpoint means converged” shortcut, is a hard
`REJECT`.

### CRIT-03 — Transport retry is not domain operation acceptance

**Observation.** In A, every idempotency, duplicate, timeout and status lookup semantic is custom. In B, a PowerSync
local write plus `ps_crud` queue and per-client operation identifier can make transport replay safer, but it does not
decide whether Kavriva accepted O-77, held a provenance claim, rejected a stale generation or recorded protected
audit. FIFO can also block behind a validation/error item unless dead-letter/hold behavior is explicit.

**Required correction.** Use one durable operation envelope in both candidates: stable operation ID and idempotency
scope, actor/session/device, resource, payload digest, expected base/version, observed generation, client timestamp
as observation only, attempt record, and explicit `PENDING`, `SUBMITTED`, `ACCEPTED`, `REJECTED`, `CONFLICT`, `HELD`,
`OUTCOME_UNKNOWN`, `RECONCILING` and `FAILED` states. A lost response must become `OUTCOME_UNKNOWN`; the next action
is same-ID status lookup/replay, never a new operation. B must map provider queue state to this domain ledger and make
2xx-but-domain-error, blocked FIFO, dead-letter and late response observable.

**Disposition.** `HELD`. A custom retry without an auditable status authority or B queue success treated as accepted is
`REJECT-IF-UNMITIGATED`.

### CRIT-04 — High-consequence conflict cannot be delegated to LWW or local optimism

**Observation.** The task fixture deliberately combines R-12 recall with C-55 ownership/provenance conflict. A has
room to build a conflict table, but that is an unimplemented product rule. B is explicitly conflict-unopinionated and
its simple per-field LWW examples are not safe for authority-sensitive provenance. A local note or synced row cannot
grant ownership, source truth or completion.

**Required correction.** Define server/API conditional mutation on expected generation or version. Preserve both
source payloads, provenance, operation IDs and protected audit; return visible `CONFLICT`/`HELD` and a reviewed
resolution path. Permit deterministic merge only for explicitly low-consequence fields with attribution, reversibility
and a written rule. Recall/revoke/delete has negative precedence over cached positive data and accepted operation
display.

**Disposition.** `HELD`; universal LWW, silent drop, local-final labeling or provider-default conflict is `REJECT`.

### CRIT-05 — Recall, delete and anti-resurrection must cross every data plane

**Observation.** A's custom tombstone/floor can be portable only if every replay, restore and export path preserves it.
B's RLS, stream filter, source-row deletion and stream reprocess govern access/delivery but do not prove that an offline
package, local cache, upload queue, optional media, backup, object export or old client cannot recreate the state.

**Required correction.** Model negative authority as a protected monotonic floor with scope, generation and reason.
Apply it to current/history/protected audit/object references, package and delta issuance, local projections, pending and
unknown operations, optional media, device restore, account migration and clean-room import. A late operation against a
recalled/deleted resource must be rejected or held without creating a new positive copy. Foreground/API revalidation
must fail closed when the floor is unknown; push/Realtime/stream events are latency hints only. Sign-out, role revoke
and device loss also need local partition, token, queue and media policy.

**Disposition.** `HELD`. Any path where an old backup, stream replay, cached row, late queue item or accepted response
resurrects recalled/deleted authority is `REJECT-IF-UNMITIGATED`.

### CRIT-06 — Process death and background scheduling cannot be correctness authorities

**Observation.** A's background isolate/database-open capability does not ensure the OS will schedule work or deliver a
lifecycle callback. B's documented WorkManager/background route does not erase iOS partial/failed fetch risk or force-
quit behavior. Both candidates can lose a last callback while local state is mid-update.

**Required correction.** Commit required state transactionally before exposing success; separate active package pointer,
staging, durable user operation, outbox attempt and purgeable media metadata. On process kill, reboot, force-quit or
power loss, restart must read the last durable state and reconcile; no callback is a commit. Background work is
opportunistic and may improve latency only. Foreground/network return must perform generation, floor, session and
operation revalidation. Exercise Android constrained/main and iOS oldest/current cohorts with real process-kill,
suspend, force-quit, low battery and storage-pressure evidence.

**Disposition.** `HELD` for both. “Push/background completed it” as correctness proof is `REJECT`.

### CRIT-07 — Migration, encryption and key loss are unresolved on both candidates

**Observation.** Drift does not include an encryption engine; PowerSync's at-rest encryption options likewise leave key
provisioning and lifecycle to the app. Both still need app-owned tables, package schema, migration order and provider
compatibility. A new key, a stale OS backup, an interrupted migration or an incompatible old client can otherwise
silently drop pending work or make stale data look current.

**Required correction.** Establish versioned schema/data formats, preflight/free-space checks, transactional or
quarantined migration, resumable/retry-safe steps and an exportable migration log. Separate `KEY_UNAVAILABLE`,
`AUTH_REQUIRED`, `KEY_INVALIDATED` and `REKEY_REQUIRED`; never fall back to plaintext or silently start an empty
database. Define secure provisioning, rotation, deletion, backup exclusion, crash/log redaction and Android/iOS binary
compatibility. Restore always enters quarantine and rechecks server negative floors, package generation, entitlement,
operation status and object manifest.

**Disposition.** `HELD`; unencrypted sensitive local data, destructive reset, owner-only repair or restored positive
authority is `REJECT-IF-UNMITIGATED`.

### CRIT-08 — Supabase is a physical boundary, not the product authority shortcut

**Observation.** DEC-0034/DEC-0035 require a Kavriva API boundary and keep RLS/Storage as defense in depth. A could
accidentally expose a broad client write because the custom path appears simple. B could accidentally let the PowerSync
upload backend write canonical tables directly or treat RLS/Sync Stream filter equivalence as complete authorization.
`service_role`/secret credentials cannot be in the Flutter client. Supabase DB backup also does not prove private Storage
objects, audit/floor records or clean-room recovery.

**Required correction.** Route every high-consequence command through the Kavriva API/equivalent server boundary with
auth verification, idempotency, expected generation, conflict/hold, audit and status lookup. For B, PowerSync upload
must be an adapter behind that API, not a direct canonical write path. Keep RLS enabled and scoped on exposed tables;
mirror stream filters and RLS but do not call the mirror an authority. Treat Auth session/role revoke freshness, Storage
object digests, database records, audit/floor and independent restore as separate evidence planes. Keep privileged keys
server-only.

**Disposition.** `HELD`. Direct client/provider canonical writes, service-role exposure or a Supabase backup declared as
full product recovery is `REJECT`.

### CRIT-09 — Device loss and account-light migration can create false ownership

**Observation.** A can preserve account-light records in an app-owned operation lane, but transfer to a profile is custom.
B's local queue and stream identity do not decide which records are private, duplicate, already accepted, conflicted or
owned by the target profile. Reinstall/device replacement can lose local-only work or replay it twice.

**Required correction.** Use stable record and operation IDs, classification, source-device/session metadata and a
scope preview before migration. Preserve local source until target acceptance and reconciliation are authoritative;
make cancellation/failure leave the source usable. Distinguish server-accepted, synchronized, pending/local-only,
unknown, media and lost states. A restored or replacement device must not inherit entitlement or re-create a recalled,
deleted or already accepted operation.

**Disposition.** `HELD`; silent merge, silent loss, duplicate side effect or local ownership assertion is
`REJECT-IF-UNMITIGATED`.

## 6. Major findings

### MAJ-01 — The data-efficiency claim needs a negative-scope proof

The 12 MB compact package, separate 150 MB optional media, 25 MB cellular-consent threshold, 250 MB cache fixture and
2 GB unrelated catalog are evaluation constants, not product caps. A has better potential to express exact task scope,
but a custom API/query can still over-fetch. B has selective Sync Streams, but stream filters, auto-subscribe, TTL,
bucket limits and media/object transfer can still produce an incomplete or overbroad user experience.

**Required correction:** For both candidates, record requested bytes, accepted bytes, dependency graph, cache class,
peak staging space and the explicit reason for every transfer. Prove that optional media never blocks compact safety
closure, that no hidden cellular transfer occurs, and that the unrelated catalog is never default scope.

**Disposition:** `HELD`; overbroad default download or safety closure made optional is `REJECT`.

### MAJ-02 — Eviction must not confuse cache, package and durable operation lanes

The manager's two-lane proposal is useful but incomplete unless the purgeable cache, optional media, compact package,
history, pending operation, protected audit and tombstone/floor are explicitly distinct. A custom evictor can delete
the wrong table; B can remove a synced row while leaving queue or stream state that reintroduces it.

**Required correction:** Define retention, classification and recovery for every class. Under pressure, evict optional
media and re-fetchable content first; retain active closure, pending/unknown operation, required attachment metadata,
negative floor and audit. A failed cleanup must be visible as `NEEDS_SPACE`/`SAFE_STOP`, not silent success.

**Disposition:** `HELD` for both.

### MAJ-03 — Freshness, old clients and mixed releases need a single fail-closed rule

Neither custom package logic nor stream schema evolution guarantees that an old client understands a new safety semantic.
A can version its manifest; B must also coordinate source schema, stream definitions, SDK/service versions and old clients.
Store prompts and provider compatibility badges do not enforce safety.

**Required correction:** Bind package eligibility to exact client capability, schema, policy/release and generation.
Unknown/incompatible freshness or recall state must stop affected progression while keeping safe recovery/history
visible. Material guide changes require a reviewed mapping; no client-invented reversal.

**Disposition:** `HELD`; accepting mixed/incompatible positive authority is `REJECT`.

### MAJ-04 — Android-first is sequencing, not evidence of iOS parity

A reduces provider layers but still owns Flutter bridge, encryption ABI, lifecycle and native fallback. B adds SDK,
generated-schema, connector, background and service differences. Android WorkManager or constrained-device success does
not prove iOS background, keychain, backup, force-quit or storage behavior.

**Required correction:** Keep one platform-neutral domain/state contract and separate Android/iOS evidence matrices.
Require real-device MPR-04, MPR-05, MPR-07, MPR-08, MPR-09, MPR-13, MPR-15 and MPR-16 evidence for each release lane.

**Disposition:** `HELD` until iOS-later gate is planned and executable evidence exists; no Android-only PASS.

### MAJ-05 — PowerSync's queue can reduce plumbing while adding a blocked-queue/service incident surface

PowerSync FIFO and per-client operation IDs are useful transport properties, not proof that an operation is accepted.
Validation errors, blocked queue items, 2xx response bodies, dead-letter policy, reconnect gaps, service deactivation,
soft limits, source outage and stream lag need explicit owner-safe states. PowerSync pricing soft limits are not a
universal billing hard cap; self-hosting moves the burden to Mongo/replication/load-balancer/backup/observability.

**Required correction:** B must document domain-to-provider state mapping, queue unblock/dead-letter policy, cost alerts,
outage hold behavior and cloud/self-host restore. It cannot use a dashboard or provider retry as an owner recovery
instruction.

**Disposition:** `HELD`; provider status/marketing substituted for domain evidence is `REJECT`.

### MAJ-06 — Drift's custom protocol is an AI-maintenance risk, not a free simplicity dividend

The manager's “one app-owned local format and one API contract” is attractive, but the hidden state count rises if
generation, floor, tombstone, staging, retry, status, conflict, restore and migration rules are not frozen. An AI can
edit small files safely only when state transitions, invariants and ownership are machine-checkable. Without that, a
smaller dependency graph creates a larger undocumented semantic graph.

**Required correction:** For A, keep package, operation, floor and restore contracts versioned and provider-neutral;
require deterministic fixtures, schema snapshots, migration tests, crash/retry matrices and independent review. Treat
custom protocol design, encryption/key choice, high-consequence policy and release migration as human-approval surfaces.

**Disposition:** `HELD`; no claim that Drift's type safety or generated migrations closes sync semantics.

### MAJ-07 — Clean-room exit is a safety test, not an architecture slogan

A's SQLite/JSON portability is a relative advantage but not a clean-room proof: the replacement must reconstruct
package graphs, operation history, conflicts, negative floors, object digests, identity mapping and restore quarantine.
B's exit is more distributed: source Postgres, PowerSync bucket/Mongo state, stream definitions, upload adapter, JWT/JWKS,
service versions, billing/license terms and protected history all matter. Neither provider can be credited merely for an
export button or open client SDK.

**Required correction:** Define an exit manifest and perform a no-secrets clean-room import/reconciliation drill for
both candidates, including partial import labels, tombstone/floor precedence, unresolved operations and object recovery.

**Disposition:** `HELD`; export without re-running safety invariants is not PASS.

### MAJ-08 — Accessibility is part of state correctness

`PENDING`, `OUTCOME_UNKNOWN`, `CONFLICT`, `RECALL_KNOWN_STOP`, `MEDIA_BLOCKED_CELLULAR_CONSENT`, `SAFE_STOP` and
`RECONCILING` cannot be reduced to color, icon or a transient snackbar. A owns the app copy directly; B must also map
provider/stream/queue states to accessible app states. Neither dossier has real TalkBack/VoiceOver/Switch evidence.

**Required correction:** Every state has semantic Turkish name/value/hint, action and recovery text, with real-device
accessibility evidence on both platform lanes. Unknown must not be announced as complete.

**Disposition:** `HELD`; inaccessible safety state or hidden error is `REJECT`.

### MAJ-09 — Cost and capacity evidence must include the custom path

The absence of a sync-provider line item in A is not zero cost: protocol design, API idempotency store, migration,
encryption, test matrix, storage/egress, incident handling and clean-room drills remain. B's plan and usage numbers are
not a purchase authorization or a hard cap; Supabase, service, egress, object, self-host and license costs remain.

**Required correction:** Keep an equal no-purchase worksheet for P1/P2/P3 workload, 18 EQ, 18 MPR, outage, restore and
exit operations. Show mandatory, deferrable, optional and scale-triggered categories; do not count marketing Free/soft
limits as a safety or budget ceiling.

**Disposition:** `HELD`; no vendor cost claim decides the architecture.

### MAJ-10 — Evidence ownership must not turn the product owner into a debugger

Both candidates require several roles: AI implementer, independent data/safety reviewer, platform reviewer, candidate
reviewer and machine/evidence validator. A manager can choose evidence capacity/continue/hold, but should not repair SQL,
advance a cursor, clear a queue, reconcile a conflict or recover a key manually.

**Required correction:** Every gap needs a bounded artifact, responsible role, platform/cohort, reviewer and exit
condition. Owner-facing recovery must be safe state plus next action, never console surgery.

**Disposition:** `HELD`; owner-debug dependency is a rejection condition under DEC-0033/DEC-0034.

## 7. Adversarial review of the manager proposal

| Manager claim | Adversarial challenge | Correction before the claim can stand |
|---|---|---|
| “SQLite + Drift is the primary reversible working direction.” | Reversible storage is not reversible semantics. Drift does not solve package authority, delta generation, recall, operation acceptance, encryption or background. The custom surface may exceed the surface it replaces. | Keep A as a hypothesis only; freeze the common contracts and require A-specific protocol, key, migration, crash, restore, Android/iOS and exit evidence. |
| “Two local data lanes make user truth explicit.” | A lane split can still leak cache rows into durable history, promote local notes into authority, or evict pending work. B can make the same mistake with synced tables/queue. | Add explicit classification/retention/floor rules and a state lattice that never equates local saved with server accepted. |
| “The complete package is the recovery baseline.” | Completeness is an assertion until dependency closure, digest, generation, policy, tombstone and storage peak are proven. A custom package can be incomplete; a B stream can appear converged but omit closure. | Require provider-neutral manifest, atomic staging/promotion, exact base and full reissue; treat B streams as delivery only. |
| “No separate sync-provider subscription reduces risk.” | It removes one invoice but transfers protocol, observability, incidents, encryption and exit work to Kavriva. For a solo/nontechnical owner, hidden custom correctness can be more dangerous than visible service cost. | Compare total maintenance/incident/exit cost; do not count no subscription as PASS. |
| “PowerSync is a challenger/fallback.” | A provider fallback is unsafe if it changes package, queue, conflict or recall meaning. B adds RLS/stream equivalence, service/version/license and outage states; marketing does not close them. | B may advance only under the exact same common state/evidence contract; no automatic fallback. |
| “Realtime and push are hints.” | Correct direction, but the same discipline must cover stream checkpoints, queue acks, provider callbacks and Supabase RLS events; all are hints/transport until the API authority is checked. | Put every signal in a non-authoritative event plane and require foreground/API revalidation. |
| “Background/restore cannot be correctness authorities.” | Correct direction, but the proposal must state what happens to keys, pending operations, object media, negative floors and migration records when callbacks do not arrive. | Add MPR-03..09/13/18 evidence and explicit quarantine/reconciliation state. |
| “Owner is not expected to debug.” | True only if candidate runbooks and evidence artifacts prevent owner console/SQL/queue/key interventions. Custom A and self-host/PowerSync B can both violate this. | Reject any recovery path that requires owner cursor repair, database edits, service-console surgery or manual conflict invention. |
| “Reversal triggers protect the primary direction.” | The triggers are useful but omit a hard equal-evidence rule: A must not be preferred when B has evidence, and B must not be preferred from marketing. | Add the common EQ/MPR matrix, independent review and clean-room exit as explicit gates; no score or provider claim substitutes. |

**Reviewer conclusion on the proposal:** retain the task-scoped/two-lane/API principles; do not promote Drift/custom to a
decision. The proposal is a reversible hypothesis with unresolved critical findings, not a selection.

## 8. Equal EQ-01..EQ-18 disposition

The following matrix records the adversarial risk for both candidates under the exact requirements-synthesis scenarios.
Every row remains documentary `HELD`; the final column names the condition that would turn an unsafe implementation into
`REJECT` rather than allowing a score-based trade-off.

| ID | A — Drift/custom risk | B — PowerSync risk | Common correction / current disposition |
|---|---|---|---|
| EQ-01 | Narrow scope is controllable but custom query/dependency closure can over-fetch or omit required rows. | Stream filters can be narrow while still not representing the complete selected-task package; default/TTL behavior needs proof. | Manifest, dependency graph, bytes and 2 GB negative-scope evidence. `HELD`; full catalog or incomplete closure => `REJECT`. |
| EQ-02 | Drift staging/transaction must be explicitly separated from promoted package; checksum alone is insufficient. | Stream/table/checkpoint retry must not promote a half package or mixed generation. | P1 stays non-active; complete digest/closure then atomic promote; P0 survives. `HELD`. |
| EQ-03 | Exact base/cursor comparator and gap recovery are fully custom. | Causal checkpoint or stream convergence cannot substitute for D1 base=G0 validation. | Atomic wrong-base reject, no closest merge, full bounded reissue. `HELD`; silent merge => `REJECT`. |
| EQ-04 | 72h local use can be bounded, but expiry/freshness and critical-action revalidation are custom. | Token/stream freshness and local rows do not by themselves define the 72h safety window. | Visible eligibility and bounded read-only/safe-stop rules; no invented recall knowledge. `HELD`. |
| EQ-05 | Recall floor/tombstone must reach every custom projection and restored copy. | Missed stream/event, RLS change or reconnect gap can leave cached positive rows. | Negative authority/floor wins before progression; push/stream is hint. `HELD`; cached positive after known recall => `REJECT`. |
| EQ-06 | Foreground reconcile and API status are custom; retry/state mapping may drift. | Queue, stream reconnect and API status can disagree; provider ack is not domain acceptance. | Stable op ID, generation/floor/session check and authoritative status. `HELD`. |
| EQ-07 | Active-work freshness boundary is an app/API policy, not Drift behavior. | Stream freshness can make a row look current without physical-work stop mapping. | Stop at reviewed safe boundary; retain history/recovery; no silent continuation. `HELD`. |
| EQ-08 | Release/material-guide mapping and old package behavior are custom. | Source schema/stream evolution may deliver semantics an old client cannot represent. | Exact client capability/release contract and reviewed remap; no client-invented reversal. `HELD`. |
| EQ-09 | Clock/restore/key/migration rules are app-owned and high surface. | Synced source/service state must be reconciled with restored local rows and floor. | Wall clock is observation; restore quarantine; negative generations cannot regress. `HELD`. |
| EQ-10 | A owns compatibility manifest but must enforce it in every action path. | Stream/service version and old client schema can be mismatched even when rows load. | Fail closed for affected safety semantic; store prompt is not enforcement. `HELD`. |
| EQ-11 | Stable identity/status/idempotency is entirely custom; highest A protocol risk. | Per-client queue IDs help transport but not domain idempotency scope/result. | Same-ID replay and status lookup; no blind duplicate/publication. `HELD`; new duplicate effect => `REJECT`. |
| EQ-12 | Custom policy can preserve both sides but may accidentally default to LWW. | Provider is unopinionated; backend LWW examples are unsafe. | High-consequence hold/audit; bounded attributable merge only for low-risk data. `HELD`. |
| EQ-13 | Custom eviction can delete required closure or pending work. | Synced rows/queue/cache retention can diverge under pressure. | Evict optional/re-fetchable first; retain closure, ops, floor and audit. `HELD`; silent loss => `REJECT`. |
| EQ-14 | Replacement/export/replay behavior is custom and can invent completion. | Provider/source restore does not identify local-only/accepted/unknown states by itself. | Recovery classification and no invented upload/eligibility. `HELD`. |
| EQ-15 | Stable-ID/profile merge and privacy policy are custom. | Queue/stream identity does not prove safe account-light migration. | Preview, classification, conflict, source preservation and authoritative target acceptance. `HELD`. |
| EQ-16 | Custom API outage/unknown/dead-letter runbook can demand engineering. | Service outage, deactivation, soft limit and blocked FIFO add provider incidents. | Visible hold/unknown, bounded retry, owner-safe runbook and no console/SQL repair. `HELD`. |
| EQ-17 | Publish/suspension generation ordering is custom. | Source/stream ordering and RLS do not make old/in-flight publish harmless. | Newer negative floor wins; protected audit and status lookup. `HELD`; suspension can be cleared by old publish => `REJECT`. |
| EQ-18 | App-owned exports are more direct but must carry floor, conflict, objects and identity. | Exit includes source DB, service bucket/config, stream/upload history and license/restore state. | Full consistency manifest and clean-room import/reconciliation. `HELD`; export-only claim => `REJECT`. |

## 9. Equal MPR-01..MPR-18 disposition

The mobile-platform matrix is intentionally not scored in favor of the framework with the shorter API. Both candidates
need the same real Android-first and iOS-later evidence. Documentary claims below remain `HELD`.

| ID | A — Drift/custom risk | B — PowerSync risk | Common correction / current disposition |
|---|---|---|---|
| MPR-01 | App-owned schema makes lane separation possible but purge policy is custom. | Synced tables, queue and cache can be retained/evicted under different provider rules. | Cache purge cannot remove history, package manifest, pending work or floor. `HELD`; cache-only authority => `REJECT`. |
| MPR-02 | Drift transaction/staging does not itself validate full package closure. | Stream retry/checkpoint does not itself validate package promotion. | Digest/dependency/manifest closure before active use; old complete package survives. `HELD`. |
| MPR-03 | Local history/outbox/media metadata transaction and orphan cleanup are custom. | Queue/table atomicity still needs domain/audit mapping and orphan media policy. | Crash matrix proves all-or-nothing state and no duplicate side effect. `HELD`; half-row/lost pending work => `REJECT`. |
| MPR-04 | Background isolate or lifecycle callback may be absent. | WorkManager/plugin callback may be absent; iOS force-quit limits remain. | Durable commit independent of callback; restart reconciles. `HELD`; callback-only success => `REJECT`. |
| MPR-05 | App-owned restore quarantine must preserve floors and operation history. | Source/service bucket restore and local synced state need cross-plane quarantine. | Restore cannot create current/entitled/accepted state or reduce negative floor. `HELD`; direct authority restore => `REJECT`. |
| MPR-06 | Reinstall/re-auth/account rebind and lost key/pending work are custom. | Service reconnect does not decide local partition cleanup or duplicate binding. | Explicit recovery/export, no stale token/key entitlement, no duplicate device binding. `HELD`. |
| MPR-07 | Encryption/key choice, secure storage, rotation and fallback are app-owned. | PowerSync encryption setup/key lifecycle is also app-owned; SDK does not protect secrets by itself. | Separate key states; no plaintext or silent empty DB. `HELD`; insecure fallback => `REJECT`. |
| MPR-08 | Drift snapshots/migration tests help but failure/space/rekey policy is still custom. | Synced schema/config/service version plus app tables widen migration order. | Versioned, idempotent, preflight/transactional or quarantine migration. `HELD`; destructive reset => `REJECT`. |
| MPR-09 | OS schedule/Doze/suspend still not guaranteed. | WorkManager/background-sync docs do not guarantee iOS or force-quit. | Foreground continuation and visible delay; background cannot be correctness. `HELD`. |
| MPR-10 | Custom transfer planner could let optional media starve core or retry storm. | Stream/media/queue scheduling could have the same starvation or retry issue. | Core closure first, media cancelable, bounded retry and battery/data reason visible. `HELD`. |
| MPR-11 | Custom outbox is entirely liable for network loss and duplicate prevention. | Provider queue helps but response loss, 2xx domain error and blocked FIFO remain. | Stable ID/expected version/unknown status and same-ID replay. `HELD`; optimistic accepted or silent LWW => `REJECT`. |
| MPR-12 | App-owned consent gate is explicit but must cover every transfer path. | Selective stream does not authorize optional object transfer or hidden background bytes. | >25 MB cellular choice, measured size, no hidden transfer, no closure reduction. `HELD`. |
| MPR-13 | App evictor/staging peak space and durable classes are custom. | Local SQLite/queue plus service stream can exceed expected peak or evict wrong class. | Free/peak-space preflight, optional eviction, `NEEDS_SPACE`, no overwrite. `HELD`; required loss => `REJECT`. |
| MPR-14 | Custom monotonic/server-generation handling required. | Provider timestamps/checkpoints do not make device wall clock authoritative. | Clock anomaly visible; freshness/eligibility cannot increase from local time. `HELD`. |
| MPR-15 | A controls app state mapping but must prove Turkish AT semantics. | B must map stream/queue/provider states without hiding unknown/blocked meaning. | TalkBack/VoiceOver/Switch evidence for all states/actions. `HELD`; color/icon-only => `REJECT`. |
| MPR-16 | Flutter/native encryption and lifecycle bridge is A-owned. | SDK/plugin/generated registrant/service/connector adds asymmetry and version coupling. | Versioned channel/error contract, capability detection and iOS gate. `HELD`; unmaintainable critical native dependency => `REJECT`. |
| MPR-17 | Custom package/media/cache classes can accidentally make media safety-critical. | Stream projection can be mistaken for media/closure and cache pressure can remove required rows. | Core complete without media; media classification/digest/consent/eviction; 2 GB never default. `HELD`. |
| MPR-18 | Manifest/old client/revoke/rollback rules are custom. | Mixed source/stream/service releases and reconnect can replay stale positives. | Exact compatibility/floor and anti-resurrection across rollback/restore. `HELD`; mixed generation positive authority => `REJECT`. |

## 10. Required correction package before any recommendation

The next evidence packet must be provider-neutral first and candidate-specific second. It must not be written as an
implementation plan or purchase request.

### 10.1 Common contract corrections

1. Freeze the package manifest, dependency-closure, digest, generation, cursor, expiry, compatibility, recall/delete
   floor, media and revalidation fields.
2. Freeze the local operation envelope, status lattice, idempotency scope, expected generation, payload digest, audit
   record and lost-response/status-lookup behavior.
3. Freeze precedence: recall/revoke/delete floor, conflict/held/unknown, server-confirmed acceptance and local pending
   state. Document what the user sees in each state and how it is announced accessibly.
4. Freeze durable data classes and eviction/restore/backup/key policies for package, history, operation, cache, media,
   tombstone/floor, audit and exports.
5. Freeze the Supabase/API boundary: no direct canonical writes from Flutter or provider service, server-only privileged
   credentials, RLS/Storage defense in depth, stream/filter equivalence evidence and separate object/audit/floor recovery.
6. Freeze the Android/iOS evidence matrix, including lifecycle absence, process kill, storage pressure, key failure,
   migration, restore, clock, accessibility and mixed-release behavior.
7. Freeze the clean-room export/import manifest and the owner-safe recovery/runbook boundary.

### 10.2 A-specific correction gates

- Show the complete custom package/delta/state-machine specification, including exact wrong-base, gap, tombstone,
  recall-floor and full-reissue behavior.
- Show local transaction boundaries for promoted package, outbox, operation history, conflict and restore quarantine;
  prove process-kill behavior without lifecycle callback assumptions.
- Show encryption/key choice as an open evidence item until Android and iOS key loss, rotation, backup exclusion and
  upgrade evidence exists; do not label Drift as encrypted by default.
- Show server operation ledger/idempotency/status and Supabase API implementation boundary as contracts, not Dart type
  names or local queue states.
- Show custom protocol maintenance/AI task decomposition, deterministic fixtures and clean-room reconstruction cost.

### 10.3 B-specific correction gates

- Show an explicit separation between PowerSync Sync Stream/queue delivery and the Kavriva package, generation, recall
  floor and acceptance contracts.
- Show Stream-filter/RLS equivalence, cached JWT/session/role revoke behavior, reconnect gaps, tombstone/reprocess and
  late write rejection.
- Show mapping for upload queue FIFO, blocked validation, 2xx domain errors, dead-letter, duplicate retry and status
  lookup; queue success must not become domain acceptance.
- Show Android/iOS background, encryption/key, schema/config/service-version, outage/deactivation and restore evidence.
- Show cloud/self-host/exit, license, pricing soft-limit/overage, backup, object and audit recovery; no marketing or
  plan feature is accepted as product safety evidence.

### 10.4 Evidence and disposition format

For each EQ and MPR row, record fixture identity, state before/after, generation/cursor, manifest/payload digest,
transaction boundary, network/process/platform event, authoritative server result, user-visible accessible state,
recovery/owner action, reviewer role, residual risk and `DOCUMENTARY`/`SIMULATED`/`REAL-DEVICE` label. Missing real
evidence remains `HELD`; shortcut violations are `REJECT`.

## 11. Disposition and conditional recommendation

### 11.1 Formal reviewer disposition

| Candidate | Current disposition | What is accepted | What is not accepted |
|---|---|---|---|
| A — Drift/custom | `HELD — DOCUMENTARY MODEL ONLY` | App-owned bounded package and local operation lanes are a plausible control boundary; Drift is a plausible local persistence primitive. | Drift as sync/recall/encryption/background proof; undocumented custom protocol; local accepted truth; no restore/key/iOS/exit evidence. |
| B — PowerSync | `HELD — DOCUMENTARY MODEL ONLY` | Selective local transport/queue is a plausible delivery primitive if kept below the Kavriva API and package authority. | Stream/checkpoint/queue/RLS/2xx/marketing as package, acceptance, recall, conflict, anti-resurrection or owner-recovery proof. |

No finalist receives a production PASS. No finalist is rejected solely because it has more or fewer dependencies. Any
candidate that violates a common hard rule is rejected for the affected capability; it does not get a compensating score.

### 11.2 Conditional recommendation

**Conditional recommendation: continue both candidates under one provider-neutral safety contract; do not choose a
winner now.**

- A may become the working direction only if it closes all common gates and the A-specific custom protocol, operation
  ledger, floor/anti-resurrection, encryption/key, migration, Android/iOS, owner-runbook and clean-room evidence with
  the same fixture. The current “no sync fee” and app ownership are not sufficient reasons to select it.
- B may become the working direction only if it proves that Sync Streams and the upload queue are delivery primitives,
  not authorities; closes API idempotency/conflict/recall, RLS/stream equivalence, blocked queue/dead-letter, native
  parity, service outage, cost/limit, license and clean-room restore gates. PowerSync marketing is not a reason to select
  it.
- If A fails its custom semantic/maintenance gates and B passes all equal gates, B can be selected on evidence—not as
  an automatic fallback. If B fails service/stream/exit or common safety gates and A passes, A can be selected on
  evidence—not because it was the manager's proposal.
- If neither closes the gates, keep high-consequence offline mutation/recall capability `HELD` or reject that scope;
  do not weaken the contract to force a provider decision.

## 12. Owner-safe handoff and clean-room boundary

The owner action after this review is limited to deciding whether to fund/allocate the equal evidence packet, device
cohorts and independent reviewers. The owner is not asked to inspect SQL, advance a cursor, clear a queue, merge a
conflict, recover an encryption key, edit a Supabase policy or operate a PowerSync dashboard.

The next reviewer should receive only the bounded contracts, fixture, candidate boundary, evidence template and open
questions. Secrets, service-role keys, production databases, provider accounts and live console access remain out of
the AI task context. Any future clean-room exercise must demonstrate that export/import preserves current records,
objects, protected audit, package graph, operation outcomes, unresolved conflicts, identity/policy mapping and negative
floors, with partial/unknown states explicit.

## 13. Final traceability statement

This review supports the repository's product truth: data-efficient task-scoped offline use, durable local work,
explicit server/API authority, visible unknown/conflict/hold states, recall/delete precedence, anti-resurrection,
owner-safe recovery and replaceable physical providers. It does not select Drift, PowerSync, SQLite encryption, an API
host, a Supabase plan, a PowerSync plan, a library version, a license path or a purchase. The only current decision is
that both finalists remain equal documentary candidates under the same `EQ-01..EQ-18` and `MPR-01..MPR-18` gates.

