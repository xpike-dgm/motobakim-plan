# DEBATE-017 — Production Download, Storage Limits and Automatic Transfer Policy — Manager Synthesis

Status: `USER-APPROVED PHASE-4 WORKING DIRECTION / DEC-0047 / NUMERIC LIMITS HELD`

## Plain-Language Proposal

Kavriva'nın download/storage davranışı şu şekilde ilerlesin:

1. Kullanıcı bir motosiklet ve görev seçtiğinde, o görev için gereken güvenli offline paket otomatik hazırlanır.
2. Bu paket, gerekli bütün metinleri, uyarıları, kontrolleri, safe-stop/recovery içeriğini ve güvenli anlamak için şart olan görsel/video/media byte'larını içerir.
3. Safety için gerekli media ayrı bir ikinci paket/bütçe değildir; required compact core'un içindedir.
4. Required selected-task içerik Wi-Fi, normal cellular veya roaming olduğu için kullanıcıdan ekstra indirme onayı istemez.
5. Safety için zorunlu olmayan ağır/ek media compact core'un dışında kalabilir ve ihtiyaç olduğunda on-demand alınabilir.
6. Uygulama cihaz alanını sessizce yönetir: önce temp/yarım dosyalar, sonra nonessential media ve eski refetchable cache temizlenir.
7. Active-task complete package ile user history/notes/photos/evidence/pending-or-accepted operation truth/protected authority-audit data cache gibi silinmez.
8. Yeni package önce stage edilir, tamamen doğrulanır, sonra atomik olarak current hale gelir. Yarım veya bozuk download kullanılamaz.
9. OS background execution ve network koşulları transferi geciktirebilir; correctness timely background callback'e bağlı olmaz.
10. İlk Phase-4 kararında exact MB/GB/% limit seçilmez. Mevcut 5/12/25/50/100 MB, 25/100/150/300/500 MB, 100/250/500 MB/1 GB/2 GB ve 20/10/5% değerleri yalnız sensitivity/test noktalarıdır ve HELD kalır.

## Proposed Qualitative Working Direction

`Family D — small mandatory complete core + safety-nonrequired eligible media on-demand + adaptive bounded refetchable cache`

Family D'nin seçilme nedeni exact numeric değerler değildir. Direction şu product/architecture özelliklerine dayanır:

- selected motorcycle/task scope;
- one complete verified safe core before offline-start eligibility;
- required safety media inside that same core;
- nonessential/safety-nonrequired media outside package completeness and eligible for on-demand transfer;
- dynamic/adaptive storage handling based on real device/OS capacity signals;
- refetchable cache evicted before active/protected truth;
- data efficiency without removing safety closure;
- CON-005 automatic mobile-data behavior;
- provider-neutral transfer/storage meaning and clean re-fetch/exit.

## Binding Owner Constraint — CON-005

Kavriva required selected-task content için:
- cellular/mobile data;
- roaming;
- byte/MB threshold

nedeniyle kullanıcıdan download confirmation istemez.

Historical `25 MB cellular confirmation` is not future product behavior.

Data Saver / Low Data Mode / OS constrained-network state may delay or restrict execution where the platform requires, but this must not become a Kavriva confirmation dialog.

## Authoritative Content Composition

### Required compact core

The complete selected-task offline safety/application package.

It includes:
- selected motorcycle/variant/task identity and applicability;
- release/generation/status/compatibility metadata;
- required text and steps;
- critical warnings/checks;
- task-specific safe-stop/recovery closure;
- manifest/digest/dependency information;
- every visual/video/media byte whose absence would make a required step or reachable safe-stop/recovery state unsafe or ambiguous.

### Required safety media

A semantic subset of required compact core.

It is **not**:
- a separate additive allowance;
- optional media merely because it is large;
- content that can wait until after offline-start eligibility.

If safety requires it, its bytes are part of the compact-core total and must already be present/verified in the same generation.

### Active-task complete package

Exactly one verified generation of required compact core including the entire required-safety-media subset.

It is protected from routine auto-eviction while active.

### Nonessential / safety-nonrequired media

Examples:
- high-resolution enhancement;
- gallery/extra imagery;
- extended teaching/video;
- convenience material not required for safe completion/recovery.

This can be on-demand, canceled, evicted and re-fetched.

### Refetchable cache

Server-reconstructable/package-derived/inactive content whose loss only causes re-fetch/rebuild.

It does not own:
- current approval;
- recall/suspension;
- authorization;
- user history;
- protected audit/authority truth.

### Durable / protected data

Not disposable cache:
- history;
- notes;
- photos/evidence;
- pending/accepted operation identity/result truth;
- conflicts/holds;
- recall/suspension/deletion/security negative floors;
- protected audit/authority records.

## Automatic Transfer Policy

- Required selected-task transfer starts automatically when the task requires it.
- No network/byte/roaming confirmation gate.
- Required core gets priority over nonessential media.
- Slow/interrupted transfers use resumable/bounded retry where supported; exact retry/backoff/chunk values remain HELD.
- Background APIs may improve continuity but are not correctness authority.
- Partial files remain in staging only.
- New package cannot replace the current valid package until manifest/digest/dependency/compatibility verification succeeds.
- Download complete does not equal current authorization.

## Low-Storage / Eviction Direction

Qualitative order:

1. invalid/orphan/temp staging data;
2. nonessential media;
3. old inactive refetchable cache/content;
4. other rebuildable projections.

Do not routinely auto-evict:
- active-task complete package;
- required safety media within that package;
- durable user-owned data;
- pending/accepted operation truth;
- protected audit/authority/negative-floor data.

If staging cannot safely complete after disposable cleanup, hold the new transfer rather than silently deleting protected truth or exposing an incomplete package.

## Numeric Policy Status

No exact first-release numeric production policy is approved by the current documentary evidence.

The following remain `HELD CANDIDATE SENSITIVITY / TEST POINTS`:

- compact package: 5 / 12 / 25 / 50 / 100 MB;
- required-safety-media subtype: 25 / 100 / 150 / 300 / 500 MB;
- refetchable cache: 100 / 250 / 500 MB / 1 GB / 2 GB;
- device free-space: 20% / 10% / 5% test bands.

Specifically HELD:
- exact compact target;
- exact compact review trigger;
- absolute compact hard cap;
- exact required-safety-media subtype target;
- exact media review trigger;
- absolute media hard maximum;
- exact cache soft budget;
- exact cache ceiling;
- exact free-space percentage trigger;
- universal absolute free-space reserve;
- exact retry/backoff/chunk/partial-retention settings;
- real-device production proof.

These values require later measured evidence from:
- real guide/media corpus distribution;
- safety classification;
- device-storage cohorts;
- peak old+new+verification space;
- cache hit/refetch behavior;
- compression/dedup results;
- interruption/retry behavior;
- supported Android/iOS real-device evidence.

## Android Auto Backup Caveat

Android Auto Backup's file-based quota is a separate platform backup-service constraint.

The researched 25 MB Auto Backup quota:
- is not Kavriva's compact-package limit;
- is not Kavriva's cache limit;
- is not a download threshold;
- is not the historical 25 MB cellular-confirmation fixture.

Concrete large durable-data restore strategy and real-device restore proof remain HELD.

## Research / Review Closure

- TASK-006 completed the four-family research with 16 scenarios × 4 families = 64 rows and 12 required fields per row.
- REVIEW-011 returned CHANGES_REQUESTED limited to M-1, M-2 and m-1.
- Narrow remediation:
  - nested required-safety-media inside required compact core;
  - downgraded unsupported exact numeric recommendations to HELD candidates;
  - added Android Auto Backup quota caveat.
- REVIEW-012 independently compared revision 13 -> 15 and returned PASS with no Critical, Major or Minor findings.
- S03-D and S14-D changes were accepted as necessary M-1 consistency corrections with no material regression.
- TASK-006 is manager-closed DONE.

## Owner Decision

The owner explicitly approved this Phase-4 working direction under `DEC-0047`:

> Kavriva selected motorcycle/task için bütün gerekli safety/recovery içeriğini tek verified offline core içinde otomatik hazırlasın. Safety için gereken media bu core'un içinde sayılsın; ayrı ikinci bir bütçe olmasın. Cellular/mobile data, roaming veya MB threshold nedeniyle kullanıcıdan indirme onayı istenmesin. Safety için zorunlu olmayan media on-demand gelebilsin. Uygulama cihaz alanını adaptif yönetsin ve önce refetchable/nonessential içeriği temizlesin; active-task package ile durable/protected user/authority data otomatik silinmesin. Şimdilik hiçbir exact MB/GB/% production limiti seçmeyelim; gerçek corpus ve device evidence gelene kadar sayıları HELD tutalım.

## Boundary

This proposal does not approve:
- any exact MB/GB/% production limit;
- CDN/storage provider;
- account, plan, purchase or payment;
- code, schema, downloader implementation or deployment;
- device proof;
- final commercial budget;
- Phase-5 ADR;
- Gate 4 -> 5 transition.
