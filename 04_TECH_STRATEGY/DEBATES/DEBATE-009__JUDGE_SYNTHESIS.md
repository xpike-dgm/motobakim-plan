# DEBATE-009 — Judge Synthesis: Offline Data, Package and Sync Direction

Status: `PASS_WITH_CHANGES — INCORPORATED / USER APPROVED DEC-0036 / NO-CODE / ADR NOT READY`  
Date: 2026-09-18

## Result in plain language

Kavriva'nın ilk çevrimdışı düzeni genel bir “sunucudaki tabloları telefona kopyala” sistemi olmamalıdır. Bunun yerine:

- telefonda dayanıklı yerel kayıt için **SQLite/Drift**;
- seçili motosiklet ve görev için küçük, kapalı ve doğrulanabilir **tam görev paketi**;
- kullanıcı geçmişi/notları/kanıtları için ayrı **dayanıklı işlem kuyruğu**;
- sunucuya yalnız Kavriva API kapısından gönderim;
- Realtime/push yalnız “yenilik olabilir” haberi, hiçbir zaman senkronizasyon veya geri çağırma kanıtı değil.

PowerSync yararlı bir teknoloji adayıdır, ancak Kavriva'nın ilk sürümünde genel veritabanı çoğaltma gereksinimi
bulunmadığı için ek hizmet, ücret ve arıza yüzeyi şu anda gerekli görünmemektedir. İlk belgeli geri dönüş seçeneği olarak
korunur.

## Evidence reviewed

- repository-derived requirements synthesis;
- current official/primary option research and Supabase changelog review;
- 18 equal product/data scenarios and 18 mobile-platform failure scenarios;
- equal Drift/custom and PowerSync finalist dossiers;
- common no-code AI task simulation;
- equivalence audit;
- independent Data Safety/Platform and Owner/TCO/Security reviews.

Both finalists remain `0 PASS / 36 HELD / 0 REJECT` at documentary level because real implementation, device, restore,
accessibility and exit evidence is prohibited in this phase. This does not prevent a reversible planning direction; it
prevents a production-readiness claim.

## Reviewer findings incorporated

### Correction 1 — Drift is not sync

Drift is accepted only as a local SQLite persistence/query/migration candidate. It does not prove package completeness,
delta correctness, encryption, recall, conflict resolution, background execution or server acceptance.

### Correction 2 — Complete package before complex delta

The first-release planning baseline uses a complete compact package for the selected motorcycle/task. Delta delivery is
optional and deferred until it proves meaningful data savings under exact-base, digest, dependency, ordering and
full-package-fallback rules. No generic row-by-row replication is required to launch.

### Correction 3 — Custom does not mean one large code area

The package and operation protocol is divided into bounded contracts/tasks:

1. local data-classification/storage map;
2. package manifest and immutable generation;
3. staging, verification and atomic promotion;
4. complete-package fetch/resume/cancel;
5. optional exact-base delta and fallback;
6. durable user-operation record and payload fingerprint;
7. API idempotency/result lookup;
8. conflict/hold/reconciliation;
9. recall/delete/tombstone and negative floor;
10. cache/media eviction and data-use consent;
11. migration/process-death/low-space recovery;
12. local encryption/key lifecycle;
13. restore/device/account-light migration quarantine;
14. observability, export and clean-room recovery.

Each later implementation task requires its own contract, fixtures, stop conditions, independent review and evidence.

### Correction 4 — Cost comparison remains honest

Drift has no separate sync-service invoice, but custom protocol design, tests, monitoring, incident handling, encryption,
backup and exit are not free. PowerSync can reduce transport plumbing but adds service/configuration/billing/license/
outage and stream/RLS equivalence work. Neither has a proven total TRY cost. This direction selects fewer initial external
dependencies, not a proven cheapest lifecycle.

### Correction 5 — PowerSync is not automatic fallback

If the app-owned protocol fails a reversal trigger, PowerSync re-enters the same 36-scenario, cost, key, migration,
outage, Android/iOS and clean-room exit gates. It cannot inherit approval merely because it offers a queue/checkpoint.

## Proposed reversible Phase-4 direction

1. **Local persistence:** SQLite through Drift is the Flutter local-data working direction.
2. **Content delivery:** one immutable, complete compact package per selected motorcycle/task is the first-release
   baseline. It contains complete safety/application/safe-stop/recovery closure without optional media.
3. **Optional media:** separate, explicit and cancelable; never required for compact-package validity unless reclassified
   as required and included in the compact closure.
4. **User work:** history, notes, evidence metadata and pending uploads use a durable app-owned operation ledger.
5. **Server sync:** operations go through the Kavriva API with stable operation identity, expected version/generation,
   idempotent result lookup and explicit accepted/conflict/held/unknown/reconciling states.
6. **Authority:** local write, HTTP success, queue empty, Realtime event, push receipt or Drift transaction never by itself
   means canonical server acceptance, freshness, approval or recall completion.
7. **Refresh:** Supabase Realtime/push may trigger a foreground/API recheck; periodic/background work is latency help only.
8. **Data efficiency:** the 12/150/25/250 MB comparison fixture and the 2 GB negative catalog case remain binding for
   later equal evidence, but are not final product limits.
9. **Restore and deletion:** package generations, pending operations, tombstones and the current negative floor reconcile
   before restored/device-migrated data can regain authority.
10. **Encryption:** exact SQLite encryption/key mechanism remains a separate held decision; plaintext fallback is prohibited.

## Reversal triggers

Reopen the direction and re-evaluate PowerSync/other retained candidates if:

- the 14 bounded task families cannot be implemented/reviewed without broad cross-project context;
- complete compact packages cannot stay data-efficient enough at measured workload;
- user operations cannot remain idempotent, observable and safely reconcilable;
- delete/recall/tombstone or old-restore anti-resurrection behavior remains ambiguous;
- Drift migration, encryption/native dependency or iOS parity requires owner debugging;
- monitoring and recovery require SQL, queue surgery or manual cursor changes by the owner;
- current total maintenance cost is worse than an equally measured PowerSync route;
- export/import cannot preserve package generations, pending operations, conflicts and tombstones.

## What this direction does not approve

- code, schema or prototype;
- a Drift, SQLite, SQLCipher or PowerSync version/package;
- a PowerSync account, plan or purchase;
- final package sizes, cache quota, freshness window or retention period;
- background execution as a correctness dependency;
- production readiness, Phase-5 ADR or Gate 4 -> 5.

## Owner decision

The owner approved the following direction on 2026-09-18 with `onaylıyorum`:

> Phase-4 planning will use SQLite/Drift as the Flutter local-data working direction. First release will prefer complete,
> compact, selected-task offline packages plus a separate durable user-operation queue through the Kavriva API. Complex
> delta sync is deferred until it proves necessary and safe. PowerSync remains the first re-evaluation candidate, not an
> approved service or automatic fallback.

Decision authority: `DEC-0036`. The 36 documentary scenarios remain held for later real evidence, and all reversal
triggers above remain binding.
