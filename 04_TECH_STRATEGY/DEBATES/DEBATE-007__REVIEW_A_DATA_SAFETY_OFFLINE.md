# DEBATE-007 — Review A: Data Safety, Offline Correctness and Domain Integrity

**Date:** 2026-09-18  
**Status:** `INDEPENDENT ADVERSARIAL REVIEW / NO-CODE / NO PROVIDER DECISION`  
**Scope:** `DEBATE-007__DATA_BACKBONE_AND_LOGICAL_BOUNDARIES.md` and its requirements, primary-research and external-intake inputs  
**Reviewer role:** data safety, offline correctness, authority/domain integrity, recovery and provenance review

## 1. Review posture and verdict

### Verdict: `PASS_WITH_CHANGES` — direction-level only; not approvable as written

The proposed shape is directionally sound and may continue as a Phase-4 working direction. The combination of a
canonical transactional authority, server-mediated sensitive operations, separate history/provenance and object/media
boundaries, bounded task-scoped mobile packages, durable user operations, rebuildable projections and restore quarantine
is consistent with `DEC-0023`–`DEC-0027` and with the S1–S36 requirements.

This is **not** a clean pass. The draft currently states several safety properties as intentions without closing the
mechanism that prevents a race, resurrection or cross-class leak. In the adversarial cases below, a technically healthy
system can still:

- re-enable a recalled release or revoked actor after restore;
- let a user act on a package after suspension but before foreground reconciliation;
- install a compact package that is small yet missing a reachable safety/recovery dependency;
- leak or silently erase private/shared/community data through derivatives, exports, caches or restore; or
- lose/duplicate user work when a browser, device, object store or operation response fails.

These are correctable boundary/contract gaps, not a reason to discard the overall shape. `REJECT AS DIRECTION` is **not**
recommended. However, the Critical corrections in Section 5 are approval blockers: no user approval, Phase-5 ADR or
implementation claim should be made until the corresponding no-code evidence exists. This review does not select a
database, provider, storage protocol, framework, API style or paid service.

### Severity meanings

- **Critical:** plausible path to unsafe physical action, authority resurrection, irreversible data loss or material
  privacy/provenance breach. Must be closed before approval.
- **Major:** likely loss, stale-state, conflict, domain-integrity or recovery failure under a realistic fault. Must be
  converted into an explicit contract and scenario before ADR entry.
- **Minor:** clarity, observability or bounded-operability gap that should be corrected, but does not by itself overturn
  the direction.

## 2. What is already strong

The following controls are useful foundations and should be retained:

1. `D7-02` rejects direct general client authority and correctly puts contextual authorization at the server boundary.
2. `D7-03` distinguishes authoritative online operations from browser convenience and names `outcome unknown` rather
   than treating a lost response as success or failure.
3. `D7-04` rejects full-library offline copies and keeps a compact safety/recovery core separate from heavy media.
4. `D7-05` rejects universal last-write-wins and requires durable identity and reconciliation for user work.
5. `D7-06` does not confuse current state, domain history and protected audit.
6. `D7-07` treats files and URLs as untrusted and preserves object identity, version, digest, classification and lineage.
7. `D7-08` keeps search, analytics, cache, notifications and package delivery out of the authority role.
8. `D7-10` correctly treats backup, restore and provider exit as trust transitions rather than successful jobs or files.

The issue is not the declared principles; it is that the draft needs stronger monotonic fences, closure manifests,
classification propagation and fault timelines so the principles cannot collapse during concurrent or degraded events.

## 3. Critical findings

### C-01 — Restore can resurrect newer revocation, deletion, roles or accepted operations

**References:** `D7-06`, `D7-10`; requirements `DB-AC-007`, `DB-AC-018`, `S21`, `S29`, `S34`; `DEC-0025` restore quarantine and
`DEC-0027` migration/revocation controls.

**Adversarial path:** Take a backup at T0. At T1 publish a recall, revoke an operator, accept a user deletion, rotate a
security epoch, and/or commit an operation. Lose the current authority and restore the T0 backup. The draft says to
quarantine and reconcile, but it does not define an authority outside the restored state that proves the T1 floor. If the
current database, audit stream, idempotency ledger and deletion records were all restored from T0, reconciliation can
appear successful while the old package, role, private data or operation is made current again. A restored pending queue
can also replay an operation that was already accepted after T0.

**Impact:** Recall/authority resurrection, duplicate approval/history, revoked access returning, and privacy deletion
being undone. This is a direct violation of the approved no-resurrection direction, not merely a backup inconvenience.

**Required correction:** Define a monotonic, non-restorable reconciliation floor for at least release/suspension and
security generations, deletion/withdrawal/retention tombstones, accepted operation identities, and migration epochs.
Specify its independent custody/failure domain, read-before-cutover rule, and behavior when the floor is unavailable.
`RESTORE_QUARANTINE` must not exit until the floor, protected audit continuity, policy/identity state, object manifest and
pending-operation ledger reconcile. A restore that cannot prove the floor remains held. Add a no-code timeline covering
old backup + newer recall, role revoke, private delete and already-accepted operation replay.

### C-02 — Recall/suspension is not fenced at the physical-action boundary

**References:** `D7-03`, `D7-04`, Section 5 consumer path; requirements `DB-AC-007`, `DB-AC-010`, `DB-AC-011`, `S14`, `S18`–`S24`;
`DEC-0024` and `DEC-0025`.

**Adversarial path:** A package is valid at download or app foreground. The user reaches a high-consequence step. An
emergency suspension commits between the last reconciliation and the physical action, or the client is offline and the
recall push is lost. “Foreground reconciliation checks current server truth” does not close this time-of-check/time-of-use
window. A stale package can therefore continue one more unsafe action while still carrying a formally valid prior
manifest.

**Impact:** The most serious failure in this product class: a recalled or superseded instruction can be physically acted
upon after the negative authority exists.

**Required correction:** Define an action-bound eligibility assertion/lease (or equivalent monotonic fence) carrying the
latest release and suspension/revocation generation. Require validation at package acceptance, app/foreground/network
return, resume boundary and every high-consequence step/decision boundary. The offline risk class must define the maximum
period and exact actions allowed without revalidation; unknown/stale generation must hold progression while retaining safe
stop/recovery. Emergency suspension must update the same negative floor independently enough to win concurrent use.
Record the last verified generation and interaction depth in history/reach-back evidence. Add a concurrent suspend-versus-
next-action walkthrough, including no push and outcome-unknown suspension cases.

### C-03 — “Compact package” is not yet a machine-verifiable safety/recovery closure

**References:** `D7-04`, `D7-10`; requirements `DB-AC-006`, `DB-AC-011`–`DB-AC-013`, `S7`, `S18`, `S22`–`S25`, `S33`;
`DEC-0023`/`DEC-0024`.

**Adversarial path:** The package contains the selected guide text and nominal steps but omits a variant distinction,
negative branch, warning/check, unit/localization/accessibility resource, prerequisite, recovery state, required
transformation or mandatory media. Alternatively, a delta applies against the wrong base, an external URL is unavailable,
or an “optional” asset is functionally required for safe comprehension. The draft says partial/mixed packages are unusable,
but does not define a closed dependency algorithm or a package-builder gate that proves every reachable physical state is
covered.

**Impact:** A small package can be treated as data-efficient success while silently removing the very safety closure that
`DEC-0023` makes mandatory. The failure may only appear after the user is already at the physical task.

**Required correction:** Make the package a closed, signed/versioned manifest containing selected motorcycle/variant/task,
all reachable physical states and negative branches, prerequisites, warnings/checks, language/unit/accessibility meaning,
claim/evidence/provenance references, client capability, schema/release/base generations, required versus optional media,
and safe-stop/recovery closure. The builder must fail closed on any unresolved dependency; mandatory content may not depend
on a mutable remote URL. Install and delta apply must be atomic, digest-checked and anti-rollback; a missing/stale/incompatible
delta must fall back to a complete compact package. Unknown safety-critical fields or unsupported clients must hold
application. Add a closure manifest walkthrough, not only a byte-size statement.

### C-04 — Private/shared/community classification can be lost across derivatives, restore and deletion

**References:** Section 6 and `D7-06`/`D7-07`; requirements `D12`, `D15`, `DB-AC-015`, `DB-AC-019`, `S5`, `S27`–`S32`;
`DEC-0026`.

**Adversarial path:** A private user photo or community attachment is linked to a shared motorcycle, included in a review
packet, OCR/AI-extracted, previewed, transformed, indexed, packaged, exported or copied to a backup. The user then revokes
sharing, withdraws the contribution or requests deletion. If the class is only metadata on the original row, a derivative
or cache can remain public; if the original is hard-deleted, the independent attribution/provenance/history chain can be
silently broken. Restore can bring either the payload or the old visibility back.

**Impact:** Privacy disclosure and cross-domain authority confusion on one side; loss of independent history/provenance and
evidence continuity on the other. A single `private/shared/community/official` field is not enough to express this lifecycle.

**Required correction:** Specify restrictive classification inheritance for every derivative, preview, AI/OCR result,
analytics/search row, package, export, backup and audit reference; an explicit reviewed promotion path is required before
any user/community material contributes to official meaning. Add a deletion/withdrawal ledger and non-restorable erasure
floor, cache/package invalidation, access-expiry behavior and redacted/pseudonymized provenance references where the
payload must be removed but the independent event must remain. Separate private payload from protected audit identity.
Run the S5/S27/S28/S29 paths through restore and export, not only through the original object.

### C-05 — “Complete export/restore” has no cross-boundary consistency point

**References:** `D7-07`, `D7-08`, `D7-10`; requirements `DB-AC-017`, `DB-AC-018`, `DB-AC-024`, `S21`, `S28`, `S34`.

**Adversarial path:** Logical data is exported at T1, media/object versions at T0 or T2, audit at another sequence, and
outbox/package/release state at yet another point. The manifest calls the export complete, but a restored claim points to a
missing object, a release points to a later object generation, an audit sequence has a gap, or a pending event is replayed
against a different schema. A provider snapshot can be internally successful while the product graph is semantically
incomplete.

**Impact:** Phantom evidence, missing private media, broken provenance, unreproducible release meaning and an exit package
that cannot be safely imported. The issue can also defeat C-01 because the restored state is not a trustworthy baseline.

**Required correction:** Define a cross-boundary snapshot/export barrier and manifest: canonical data sequence, object
generation/digest inventory, audit checkpoint, policy/security epoch, release/suspension floor, outbox/operation cursor,
package artifacts and schema/config versions. Import must verify references, ACL/classification, digests, audit continuity,
pending-operation semantics and deletion tombstones before cutover. If domains cannot share a consistent point, the result
must be explicitly partial/quarantined, never a complete exit or restore.

## 4. Major findings

### M-01 — Durable local work is not yet protected against device loss, clone, tamper or media failure

`D7-05` makes local operations durable before UI persistence, but does not define local encryption/key recovery, queue and
media retention, device identity/clone handling, local integrity/tamper semantics, or what can be recovered after device
loss. A restored phone can replay an accepted event, while an evicted or corrupted pending attachment can leave a history
event without its evidence. Define encrypted local storage, device/installation generation, operation/media dependency
states, export/recovery behavior, non-evictable pending work, duplicate detection and an explicit `local-only`/`unverified`
label. Device loss must yield a truthful loss/held state, not silent completion.

### M-02 — Conflict policy is a principle, not a domain contract

`D7-05` allows bounded automatic merges for low-consequence fields and reviewed resolution for safety/provenance/ownership,
but no field/operation consequence matrix, causal metadata, delete-versus-update rule, cross-entity ordering or transfer
policy is defined. A provider can therefore reintroduce LWW through a “low-risk” default, or merge two individually low-risk
fields into an invalid high-risk invariant. Define per-operation merge/hold rules, parent/version evidence, both-side
retention, tombstones, causal order, reviewer competence and tests for edits, transfers, revokes, corrections and migration
collisions.

### M-03 — Operation identity is not explicitly atomically bound to effect, audit and outbox

`D7-03`/`D7-05` require durable identities and retry reconciliation, but do not state where the idempotency ledger lives,
how payload fingerprints and actor/scope binding are enforced, how long results remain replayable, or how a partially applied
cross-domain operation is represented. If the response is lost after the effect but before the ledger/outbox/audit commit,
the same operation cannot be safely resolved. Add atomic accepted-operation recording, typed `failed` and `partial` states,
payload-mismatch rejection, durable status lookup and a resolver owner. “Retryable” alone is not idempotency evidence.

### M-04 — Browser stale-state and disconnected-draft behavior needs an explicit contract

`D7-02` correctly requires commit-time checks, but the draft lacks a browser read-freshness marker, tab/session/security-
epoch invalidation, conditional version contract, schema compatibility behavior and offline-draft import rules. A stale tab
can show an approval-ready object, a changed policy can be hidden until a submit, or an offline local draft can be applied
after classification/release dependencies changed. Define read state as non-authoritative, require `If-Match`/equivalent
expected-version checks, reauthorize at commit, preserve the draft as a proposal on rejection, and cover policy/session
revocation, two tabs, browser crash and migration. Map directly to S11–S17.

### M-05 — Rebuildable projections can still deliver stale or recalled meaning

`D7-08` says projections cannot become authority, but it does not require the package builder, cache, search result or
notification payload to be generated from a closed canonical release and current negative floor. A stale projection can
still be rendered as a seemingly official guide before the final eligibility check; a recalled object can remain in a cache,
search index or package queue. Define projection generation/observed generation, revocation filtering, cache invalidation or
bounded TTL, package-builder input fence and read-time eligibility checks. “Projection is rebuildable” is not the same as
“projection cannot expose recalled content.”

### M-06 — Recall reach-back and dormant/offline cohort accounting are absent

Foreground reconciliation is necessary but cannot prove that a dormant or long-offline user was reached. The direction does
not yet define an impact ledger for package cohorts and interaction depth (downloaded, opened, active step, evidence,
completion), delivery attempts, acknowledgement/failed channels or residual offline risk. Add a recall-impact graph and
reach-back state; absence of a push receipt must remain unknown, while the next safe app boundary must conservatively hold
new physical progression. Do not claim immediate offline recall propagation.

### M-07 — Media and URL ingestion threat controls are too abbreviated for the stated boundary

`D7-07` says quarantine/validate/scan/render, but the direction must also carry the specific adversarial cases from S30/S31:
active content and polyglots, decompression bombs, traversal, EXIF/location leakage, remote redirects/private endpoints,
DNS rebinding/SSRF, ambient browser cookies, mutable URL content, preview-origin credentials, scanner timeout/unknown,
orphaned uploads and finalization races. Store the captured source/digest and exact fetch policy; isolate untrusted preview
and rendering from privileged operations; preserve original/derived lineage; never turn a scan/render success into technical
correctness or approval. A quarantine label without these transitions is not an ingestion safety contract.

### M-08 — Object version, access and deletion semantics are underspecified

Object identity/version/generation/digest are listed, but there is no required rule for finalization atomicity, delete markers,
old-version access, signed-handle expiry/revocation, checksum semantics, orphan cleanup or classification/retention drift
between object metadata and canonical records. A mutable “latest” URL can return a different object than the approved digest,
and a private object can remain accessible after permission revocation. Add object-manifest checks, private handle policy,
version-specific reads, revocation/expiry, orphan quarantine and reconciliation before use/export.

### M-09 — Old clients, restored caches and local clocks are not fully fenced

The draft mentions version/compatibility and foreground reconciliation but does not explicitly require unknown critical
fields to fail closed, anti-rollback package/client semantics, cloned-cache quarantine, monotonic time treatment or the
wall-clock/reboot/restore cases in S20–S23. A client can ignore a newly required safety field, extend freshness by changing
the clock, or restore a formerly eligible package. Add an `UNSUPPORTED_CLIENT`/`RESTORE_QUARANTINE` contract, server-anchored
freshness, anti-rollback floor and explicit teaching/history/safe-recovery fallback.

### M-10 — Protected audit availability and effect ordering are not binding in D7 itself

`D7-06` correctly warns that timestamps, provider logs, CDC and a mutable audit row are insufficient, but `D7-03` does not
explicitly require high-consequence effects to remain `HELD` when protected audit evidence is unavailable. Add the
effect-before-audit rule: either minimum protected attributable evidence is durable before approval/publication/recall/role
mutation, or the operation is held/unknown with a separately protected fallback buffer. Require sequence/checkpoint/fork
detection and restore reconciliation. Keep private payload erasable even when the accountability event is retained.

### M-11 — Lifecycle, entitlement and transfer races can attach offline work to the wrong scope

`D7-05` records actor/device/context, but the draft does not specify how a motorcycle transfer, collaborator revoke,
entitlement downgrade, account merge or profile migration affects a pending local operation or package. An offline event can
arrive after ownership changes and be silently attached to a new owner or treated as official. Bind every pending operation
and package to actor, motorcycle identity, scope/entitlement generation and used release; on mismatch preserve the event in
conflict/held state with attribution and require reviewed transfer resolution. Existing history and correction access must
remain available after inactive/entitlement changes.

### M-12 — Cache-pressure and optional-media rules need a non-eviction guarantee

The draft says heavy media is optional but does not explicitly make the safety/recovery core, active-work context and
pending evidence non-evictable or define behavior when the device cannot retain them. Add storage-pressure states, user-visible
size/cleanup controls, resumable re-fetch for optional media, and safest available stop/preserve-state behavior when required
content or local evidence cannot be retained. Data efficiency must never turn a required recovery asset into a best-effort
cache item.

### M-13 — Deletion/retention behavior for copies is still an open hazard, not just a policy question

`D7-10` inventories backups, media, audit, configuration and keys, but does not yet define copy-level deletion/expiry for
offline packages, browser caches, search/read models, exports, object versions and logs. A user-facing delete can therefore
be truthful for the canonical row while leaving private data in a package or export, or can over-delete independent
provenance. Require a copy inventory, deletion/withdrawal propagation state, legal-hold exception and expiry, residual-copy
warning and restoration reapplication of the erasure floor.

### M-14 — Failure-domain fencing for failover is not explicit

Provider/account/region failure is acknowledged, but a restored or secondary authority could accept writes concurrently with
the old primary unless a writer epoch/fencing token is required. That creates two authoritative histories and undermines
recall ordering. Add single-writer/epoch fencing, cutover proof, stale-primary denial and audit of the transition. This is a
logical safety requirement; it does not prescribe a topology.

### M-15 — AI/OCR derivative provenance and classification need to be first-class in the backbone contract

The input documents correctly say AI/OCR is a proposal, but D7-06/07/Section 6 do not require every extracted field,
transformation config/model version, uncertainty and source span to travel with the derivative. Without this, a plausible
measurement can outlive or outscope the private/quarantine source and appear as a clean claim. Require attributable input,
model/config/version, transformation, uncertainty, classification inheritance and human-review state for every AI/OCR
artifact; it may not write canonical technical truth.

### M-16 — Analytics and coverage projections need an explicit unknown/held denominator

`D7-08` correctly keeps analytics non-authoritative, but a dashboard can still turn stale, disputed, inaccessible or
unknown records into a clean quality score and hide the safety backlog. Require metric definitions with denominators,
unknown/conflict/held counts, generation/freshness and drill-down to claim/evidence/audit. No metric may auto-close a gap,
promote a source or clear a recall.

## 5. Required corrections before approval or ADR entry

### P0 — approval blockers

1. **Anti-resurrection recovery contract:** add the non-restorable generation/deletion/operation floors, restore state
   machine, failover fencing and T0/T1 restore timelines (`C-01`, `C-05`, `M-03`, `M-14`).
2. **Recall/use race contract:** add action-bound eligibility/suspension fencing, offline risk windows, interaction-depth
   evidence and no-push/no-network scenarios (`C-02`, `M-06`).
3. **Closed package contract:** add machine-verifiable dependency/recovery closure, signed manifest/trust and anti-rollback,
   mandatory/optional media rules, unsupported-client behavior and atomic delta/fallback (`C-03`, `M-05`, `M-09`, `M-12`).
4. **Classification and deletion contract:** define restrictive derivative inheritance, consent/promotion, deletion/withdrawal
   ledger, copy invalidation, erasure floor, redacted provenance and restore reapplication (`C-04`, `M-13`, `M-15`).
5. **Consistent export/restore proof:** add a cross-domain snapshot barrier/manifest and import verification for canonical
   data, objects, audit, policy/identity, releases, packages, outbox and tombstones (`C-05`).

### P1 — required before any physical candidate can pass

6. Publish the per-domain conflict/merge matrix and causal/ordering contract; no provider default may supply it (`M-02`).
7. Define local queue/media privacy, encryption, device generation, loss/clone/tamper behavior and recovery/export (`M-01`).
8. Define browser stale-read/session/schema/conditional-write and offline-draft behavior (`M-04`).
9. Define media/URL quarantine threat states, private object handles, finalization and version/deletion reconciliation
   (`M-07`, `M-08`).
10. Make protected audit availability and effect ordering explicit, including fallback/hold and checkpoint/fork detection
    (`M-10`).
11. Bind packages and pending operations to actor, motorcycle, entitlement/scope generation and used release; cover transfer
    and revoke races (`M-11`).
12. Require projection/package-builder freshness and recall filtering; define dormant-client reach-back states (`M-05`, `M-06`).

### P2 — clarity and operability corrections

13. Expand typed operation results in `D7-03` to include `failed`, `partial`, `partial propagation`, `restore quarantine`
    and `reconciliation required`; retain `outcome unknown` semantics.
14. Mark every unresolved numeric policy (freshness, package/cache size, RPO/RTO, retention, idempotency retention) as
    `OPEN/HELD`, never as an implied default.
15. Keep the managed-relational/PostgreSQL wording visibly as an investigation hypothesis. It must not be copied into a
    provider, engine or ADR decision without the same safety, export, restore, cost and owner-operability evidence.
16. Add a compact authority map showing which of current state, history, audit, package, projection and object metadata is
    authoritative for each read/write; “canonical core” alone is too broad for adversarial review.

## 6. Minimum no-code evidence package for re-review

Re-review should require timelines and artifacts, not implementation claims or green-build assertions:

- `C-01`: restore an old snapshot after newer recall, role revoke, private deletion and accepted operation; prove no
  resurrection, duplicate or authority cutover before reconciliation (`S21`, `S29`, `S34`).
- `C-02`: concurrent publish/suspend/next physical action with missing push and lost suspension response; show monotonic
  negative fence, hold/safe-stop and interaction-depth reach-back (`S14`, `S17`–`S24`).
- `C-03`: package closure graph and manifest for nominal, negative, mismatch, localization/accessibility and recovery
  branches; interrupted download, wrong-base delta, unknown field, stale package and optional-media eviction (`S7`,
  `S18`, `S22`–`S25`, `S33`).
- `C-04`: private photo and community contribution through review, derivative/AI, package, export, withdrawal, deletion,
  cache and restore; show restrictive inheritance and retained independent provenance (`S5`, `S27`–`S32`).
- `C-05`: export/import drill with canonical rows, object versions, audit checkpoint, policy/identity, release/package,
  outbox/operation state and tombstones at a declared consistency point; intentionally omit each category and prove hold.
- `M-01`–`M-04`: device loss/clone, duplicate retry, conflicting edits, transfer/revoke, two browser tabs, stale policy,
  crash and offline draft re-entry.
- `M-05`–`M-16`: stale projection/recall purge, URL/active-content quarantine, object revocation, client clock rollback,
  audit sink outage, failover writer fence, AI derivative provenance and metric denominator/unknown-state drill-down.

Every scenario must state: expected allow/deny/hold, visible state, side effects, protected evidence, recovery owner and
what remains intentionally non-authoritative. “Button hidden”, “backup succeeded”, “cache is signed” or “AI generated a
manifest” is not sufficient evidence.

## 7. Final determination

`DEBATE-007` can proceed as a no-code, provider-neutral direction **only with the P0 corrections carried forward as
binding requirements**. The current draft has the right separation of concerns but leaves the exact places where systems
usually lose data or authority—restore cutover, concurrent recall, package closure, deletion propagation and cross-store
consistency—too implicit. Until those contracts and scenario proofs exist, the truthful state is:

> **PASS_WITH_CHANGES for continued Phase-4 analysis; NOT APPROVED, NOT AN ADR, NOT IMPLEMENTATION-READY.**

No other file was changed by this review.
