# ADR-009 — Mobile Offline Package, Local Persistence, Durable Ledger and Transfer Policy

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy answered offline eligibility and safety (DEBATE-002, `DEC-0023`/`DEC-0024`), the Flutter
data/sync mechanism (DEBATE-009, `DEC-0036`: SQLite/Drift + complete compact package + durable operation ledger,
PowerSync as first re-evaluation candidate), and production transfer/storage policy (DEBATE-017, `DEC-0047`:
one verified required compact core containing all required-safety-media, `CON-005` confirmation-free required
transfer, adaptive eviction, exact MB/GB/% limits HELD). This ADR fuses the three layers into one binding offline
contract on top of ADR-001, ADR-002, ADR-003, ADR-006 and ADR-008. It selects no library version, encryption plugin,
sync provider, CDN/storage product, numeric limit or account, and authorizes no code, purchase or device proof.

## Decision Drivers

- Offline must be data-efficient (selected motorcycle/task only) without ever removing safety/recovery closure.
- The phone store is delivery/cache plus pending user work — never approval, publication, recall or safety authority.
- Required content must flow over cellular/roaming without a user confirmation gate (`CON-005`, binding).
- User work must survive process death, storage pressure, restore and device migration without silent loss, silent
  overwrite or silent last-write-wins.
- A wrong offline guess must fail closed while keeping safe-stop/recovery available.

## Options Considered

### Option A — Generic table replication / full-library sync (rejected)

Copying server tables to the phone with row-level sync. Rejected: downloads the unrelated catalog by default,
cannot express complete safe closure per task, invites silent last-write-wins, and turns the phone into a
pseudo-authority for data it cannot verify.

### Option B — Complete compact package + app-owned persistence and ledger (chosen)

One immutable, complete, verified compact package per selected motorcycle/task (SQLite through Drift locally),
plus a separate durable app-owned operation ledger for user history/notes/evidence submitted through the Kavriva
API. Complex delta sync deferred until measured savings justify it; PowerSync kept as first re-evaluation
candidate, never an automatic fallback.

### Option C — Managed sync service now (not selected)

PowerSync (or equivalent) would reduce transport plumbing but adds service/configuration/billing/license/outage
surfaces without a proven total cost, while no generic replication requirement exists for first release. Re-enters
only through the same 36-scenario, cost, key, migration, outage and exit gates if Option B trips a reversal trigger.

## Decision

Kavriva adopts Option B with the following locked contract:

1. **Package composition:** one verified generation of required compact core per selected motorcycle/task, containing
   identity/applicability metadata, release/generation/compatibility context, required text/steps, critical
   warnings/checks, task-specific safe-stop/recovery closure, manifest/digest/dependencies — **including every
   visual/video/media byte required for safe understanding** (`required safety media` is a semantic subset of the
   core, never a second additive budget, never moved on-demand to fit a size target). Safety-nonrequired media stays
   outside completeness: separate, explicit, cancelable, evictable, re-fetchable.
2. **Acceptance:** stage → verify complete manifest/digest/dependencies/compatibility → atomic promote. Partial,
   corrupt, mixed, stale or incompatible downloads never become actionable; missing/stale deltas fall back to a
   complete package. Package transition needs peak old+new+verification space — addressed by eviction, never by
   silently deleting protected truth.
3. **Automatic transfer (`CON-005` binding):** required selected-task transfer starts automatically when the task
   requires it, over Wi-Fi, cellular or roaming, with no network/byte-threshold confirmation dialog. Required core
   has priority over nonessential media; resumable bounded retry where supported (exact values HELD). OS Data
   Saver/constrained-network states may delay execution but must never become a Kavriva confirmation gate. Download
   completion alone is not authorization, recall state or technical truth.
4. **Adaptive storage:** eviction order is invalid/orphan/temp staging data → nonessential media → old inactive
   refetchable cache → other rebuildable projections. Never routinely auto-evicted: the active-task complete
   package, required safety media inside it, durable user data, pending/accepted operation truth, protected
   audit/authority data and negative floors. If staging cannot complete after disposable cleanup, the new transfer
   holds.
5. **Durable user ledger:** history, notes, evidence metadata and pending uploads persist as identified operations
   (stable identity, payload fingerprint, expected version/generation) with explicit
   pending/submitted/accepted/conflict/held/failed/outcome-unknown/reconciling states; all submission and lookup
   goes through the API; local write, HTTP success, empty queue, Drift transaction, Realtime event and push receipt
   never alone mean canonical acceptance. No silent last-write-wins for high-consequence data; restore/migration
   enters reconciliation quarantine and cannot resurrect recall, revoke, deletion, suspension or accepted operations.
6. **Risk-tiered eligibility:** unknown/unclassified or stale critical dependencies fail closed with the highest
   consequence inherited; offline start requires complete compact recovery closure for all reachable physical
   states; restored backups, clock anomalies, incompatible old clients and mixed packages create no new positive
   authority; Internal Operations mutations stay online-authoritative.
7. **Encryption without fallback:** local encryption and key custody is a separate held decision, but plaintext
   fallback is prohibited — the capability holds until the mechanism is proven.
8. **Numeric policy held honestly:** 5/12/25/50/100 MB compact points, 25/100/150/300/500 MB safety-media points,
   100/250 MB/1 GB/2 GB cache points and 20/10/5% free-space bands remain `HELD CANDIDATE SENSITIVITY / TEST
   POINTS` until measured corpus/device evidence (real guide/media distribution, safety classification,
   device-storage cohorts, compression/dedup, interruption behavior, Android/iOS real-device proof) selects them.
   Android Auto Backup's 25 MB file quota is a backup-service constraint, unrelated to these limits.

## Rationale

Complete-package-first is the only offline shape that guarantees safe closure without depending on connection
quality, delta correctness or server round-trips at the roadside; the separate ledger gives user work the
durability and explicit states that sync-transparent replication hides. Deferring delta and managed sync avoids
paying for complexity before measured data proves the need, while the reversal triggers keep the re-evaluation
honest.

## Consequences

### Positive

- Bounded, testable offline surface: one package, one manifest, one ledger — every behavior attributable.
- Roaming/mountain-road usability without nagging dialogs, with safety closure intact.
- Restore, device loss and migration produce truthful outcomes (loss/held/reconcile), never invented server state.

### Negative / Trade-offs

- Full-package re-downloads cost more bytes than deltas until and unless delta proves itself — data-efficiency
  pressure stays on corpus measurement.
- Staging verification needs transient extra space; low-storage devices hold new transfers instead of updating.
- Exact limits unknown until real corpus/device measurement — first-release sizing stays provisional.

## Prohibited / Constrained Alternatives

- Full-library/unrelated-motorcycle default download; partial/mixed package use.
- Safety-media exclusion to fit a size target; safety closure removed for data savings.
- Cellular/roaming/byte-threshold confirmation gates for required content.
- Silent last-write-wins; local/queue/push success presented as server acceptance, freshness or recall.
- Plaintext local fallback; routine eviction of active/durable/protected truth.
- Background execution as a correctness dependency.
- Any library version, encryption mechanism, sync provider account/plan, numeric production limit, code or device
  proof — none authorized by this ADR.

## Revisit Triggers

- Complete packages cannot stay data-efficient at measured workload; ledger semantics cannot stay
  idempotent/observable/reconcilable; recall/tombstone/anti-resurrection turns ambiguous; Drift/encryption/iOS
  parity demands owner debugging; recovery needs SQL/queue surgery; measured PowerSync total cost beats the
  app-owned route with equal safety — any trigger reopens the mechanism with evidence (binding, from `DEC-0036`).
- Exact MB/GB/% limits, retry/backoff/chunk settings, freshness windows and real-device proof remain HELD for
  measured evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0023`, `DEC-0024`, `DEC-0036`, `DEC-0047` (binding directions)
- `01_WORKSPACE/CONSTRAINTS.md` — `CON-005`
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-002__PHYSICAL_BACKEND_PLATFORM_AND_API_AUTHORITY.md`
- `05_ADR/RECORDS/ADR-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md`
- `05_ADR/RECORDS/ADR-006__KAVRIVA_API_RUNTIME_AND_DURABLE_LONG_JOBS.md`
- `05_ADR/RECORDS/ADR-008__CONSUMER_MOBILE_FRAMEWORK.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-009__JUDGE_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-017__MANAGER_SYNTHESIS.md`
- Downstream: ADR-014 (AI retrieval over packaged content), Phase-6 offline task decomposition

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
