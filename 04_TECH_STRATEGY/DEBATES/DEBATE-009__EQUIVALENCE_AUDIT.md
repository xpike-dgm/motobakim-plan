# DEBATE-009 — A/B Equivalence Audit: Drift/custom ve PowerSync

Durum: CONDITIONAL EQUIVALENCE / NOT YET PROVEN / NO WINNER / NO-CODE  
Tarih: 2026-09-18  
Kapsam: Flutter Android-first / iOS-later consumer-mobile; A Drift/custom ve B PowerSync  
Denetim kimliği: DEBATE-009-EQ-AUDIT-001

## 1. Kısa hüküm

İki finalist dossier'i ve TASK-SIM-OFFSYNC-001 şu açıdan eşittir:

- aynı frozen workload, aynı 18 EQ + 18 MPR senaryosu ve aynı Android-first/iOS-later yönünü kullanırlar;
- her iki aday da package, durable operation, recall, conflict, restore, accessibility, cost ve exit için
  provider-neutral minimum sözleşmenin gerektiğini kabul eder;
- her ikisi de mevcut no-code düzeyinde 0 PASS / 36 HELD yaklaşımını ve gerçek cihaz/restore/exit kanıtı
  eksikliğini kabul eder;
- aynı 12 MB compact package, 150 MB optional media, 25 MB cellular confirmation ve 250 MB cache
  değerlerini comparison fixture olarak kullanırlar; bunları final ürün limiti saymazlar.

Eşitlik henüz kanıtlanmış değildir. A'nın “ayrı managed sync-provider fee varsayılmıyor” ifadesi
custom package/delta/operation/conflict/recall/migration/key/observability yükünü sıfır maliyet yapmaz.
B'nin selective sync, local queue, causal checkpoint, encryption veya background primitive'leri de
Kavriva'nın package closure, canonical authority, recall floor, idempotency, conflict, accessibility,
restore veya exit kanıtı değildir. B'nin provider/service surface'i ve A'nın custom semantic surface'i
aynı dış davranış ve aynı evidence standardıyla normalize edilmelidir.

Mevcut audit sonucu:

| Alan | A Drift/custom | B PowerSync | Audit kararı |
|---|---|---|---|
| Kapsam/fixture | Aynı | Aynı | EŞİT |
| State/authority sözleşmesi | Büyük ölçüde aynı | Büyük ölçüde aynı | EŞİT, ortak contract'a bağlanmalı |
| 18 EQ | 18 satır, hepsi HELD | 18 satır, hepsi HELD | EŞİT beyan; evidence yok |
| 18 MPR | 18 satır, hepsi HELD | 18 satır, hepsi HELD | EŞİT beyan; real-device kanıt yok |
| Custom/provider burden | Kavramsal olarak görünür, parasal değil | Service/plan/license/stream burden görünür, total değil | NORMALIZE ET |
| Marketing primitive riski | Drift/SQLite primitive'i semantik authority sayılmıyor | PowerSync primitive'leri semantik authority sayılmamalı | Aynı sertlikte uygula |
| AI task surface | 14 custom task ailesi açık | Stream/RLS/queue/service yüzeyi listelenmiş, aynı task kataloğuna bağlanmalı | NORMALIZE ET |
| Current disposition | HELD | HELD | Kazanan yok |

Bu belge kazanan seçmez, weighted score üretmez, kod/prototip/benchmark yapmaz ve Phase-5 ADR kararı vermez.

## 2. Denetim girdileri ve yetki sınırı

Denetim şu kaynakların yalnızca mevcut metinsel kanıtını karşılaştırır:

1. DEBATE-009__OFFLINE_SYNC_REQUIREMENTS_SYNTHESIS.md — OSR-INV, OSR-PKG, OSR-DLT, OSR-OPS,
   OSR-SYN, cache/recall/restore/migration/API gereksinimleri; frozen workload; EQ-01..EQ-18.
2. DEBATE-009__OFFLINE_SYNC_OPTIONS_PRIMARY_RESEARCH.md — A ve B'nin primary capability,
   boundary, cost, data-use, encryption, background, exit ve candidate-specific hold yüzeyleri.
3. DEBATE-009__MOBILE_PLATFORM_FAILURE_RESEARCH.md — resmi Android, Apple, Flutter/Dart mekanizması
   sınırları ve MPR-01..MPR-18.
4. DEBATE-009__MANAGER_PROPOSAL.md — iki local lane, API boundary, atomic promote, restore quarantine,
   owner-debug yasağı, reversal trigger ve eşit no-code evidence beklentisi.
5. DEBATE-009__FINALIST_A_DRIFT_CUSTOM.md — A dossier'i, 18 EQ + 18 MPR, cost/data, AI task ve exit.
6. DEBATE-009__FINALIST_B_POWERSYNC.md — B dossier'i, PowerSync/Supabase primitive ve limitleri,
   service/license/cost/exit, 18 EQ + 18 MPR.
7. DEBATE-009__TASK_SIM_OFFSYNC_001.md — ortak P01..P08 no-code task packet'leri ve E0..E8 failure chain.

Bu denetim kaynaklarda olmayan production guarantee, gerçek fiyat hesabı, provider account sonucu, runtime
kanıtı veya device pass icat etmez. Bir capability “CONFIRMED” olsa bile ürün acceptance'ı ancak ortak
Kavriva evidence sözleşmesiyle değerlendirilebilir.

## 3. Audit yöntemi ve terimler

Her satır dört soruya tabi tutuldu:

1. Aynı girdi mi? Cihaz, ağ, workload, failure injection, release/capability ve user state aynı mı?
2. Aynı external oracle mı? Kullanıcıya görünen state, canonical authority, safe-stop ve recovery
   her iki adayda da aynı sonucu mu istiyor?
3. Aynı kanıt mı? Bir adayın provider primitive'i diğer adayın custom semantic testinin yerine
   geçirilmiş mi; veya tersi mi?
4. Aynı owner sınırı mı? Hiçbir adayda nontechnical owner SQL/SSH/provider-console, raw log,
   queue/database/migration veya native build repair yapmak zorunda mı?

Disposition terimleri:

- EŞİT: External contract ve kanıt eşiği aynı; aday-specific mekanizma farklı olabilir.
- NORMALIZE ET: Ortak contract aynı görünür fakat evidence artifact, cost, data-use veya hidden
  dependency bir adayda daha düşük/kapalı tutulmuştur.
- ASİMETRİ RİSKİ: Bir primitive marketing language ile product authority'ye yükseltilmiş veya
  custom/provider burden diğer adaya göre görünmez bırakılmıştır.
- HELD: Güvenli plan tarif edilebilir, ancak gerçek evidence/owner/cost/exit kapanmamıştır.
- REJECT-IF-UNMITIGATED: Ortak hard-fail ihlali; başka adayın avantajı ile telafi edilemez.

## 4. Ortak canonical oracle

Audit boyunca aşağıdaki candidate-neutral contract ID'leri kullanılır. A ve B kendi dosya/servis
adlarını kullanabilir; fakat aynı semantik alanları, aynı state ve aynı evidence alanlarıyla taşımaları
gerekir.

| Contract ID | Ortak minimum | A surface | B surface | Eşitlik koruması |
|---|---|---|---|---|
| PKG-01 | Scope, release, schema, capability, generation, dependency closure, classification | App-owned manifest/staging/Drift projection | Stream projection üstünde Kavriva manifest/package layer | Stream row veya local DB row tek başına package complete değildir |
| PKG-02 | Digest, atomic stage/promote, old valid generation | SQLite transaction/promote | Stream/checkpoint + app-owned stage/promote | Partial/mixed/corrupt current olamaz |
| DLT-01 | Exact base identity/generation/digest; wrong-base reject; full compact fallback | Custom delta/cursor | Stream/checkpoint metadata + API reissue | Causal checkpoint exact package base değildir |
| OPS-01 | Stable op ID, payload fingerprint, expected version/generation, actor/session/device | Custom operation envelope/outbox | Upload queue metadata + Kavriva API | Queue drain/HTTP 2xx/local row accepted değildir |
| OPS-02 | ACCEPTED, CONFLICT, HELD, FAILED, UNKNOWN, RECONCILING | API status ledger | Upload API/status ledger; PowerSync result mapping | Provider retry domain result yerine geçmez |
| RCL-01 | Recall/revoke/delete floor, tombstone, old-client and restore anti-resurrection | API floor/tombstone/local record | API floor + stream/RLS reprocess/local quarantine | Push, stream delivery veya row deletion authority değildir |
| CON-01 | High-consequence two-sided conflict; no universal LWW | Custom conflict table/review | API conflict policy; PowerSync default LWW unusable | “Unopinionated” veya “custom” claim policy boşluğu değildir |
| CCH-01 | Cache, media, staging, active closure, history, pending ops separate | App-owned lanes | Synced DB/queue + app policy + Storage object lane | 250 MB fixture user data/cache policy değildir |
| RST-01 | Restore quarantine; current/history/object/audit/floor/outbox reconcile | App-owned manifest/quarantine | Supabase + PowerSync bucket/checkpoint + API manifest | Backup success tek başına recovery/exit değildir |
| MIG-01 | Stable local IDs, scope preview, idempotent migration, source preserved, partial visible | Custom migration session | Auth/stream switch üstünde API migration session | “Client migration yok” product migration'ı kapatmaz |
| KEY-01 | Key states, no plaintext fallback, backup/rekey/reinstall behavior | External SQLite encryption/key path open | PowerSync encryption option + app/API key path open | “Encrypted” capability matrix yerine geçmez |
| PLT-01 | Android/iOS lifecycle, storage, clock, network, accessibility real evidence | Drift/native/Flutter surfaces | PowerSync/SQLite/encryption/native surfaces | Android pass iOS release gate değildir |
| API-01 | Kavriva API sensitive reads/mutations; privileged secrets server-only | Custom API boundary | Upload API + Supabase source/API | Direct DB/Storage/PowerSync authority REJECT |
| COST-01 | 24-month equal BOM, overage/incident/restore/exit and owner time | Custom engineering/ops cost | Cloud/self-host/service/license cost | Provider fee yok ≠ total cost zero |
| DATA-01 | Wire bytes, retries, reprocess, object egress, local peak and 2 GB negative | Explicit package protocol | Stream predicates/checkpoint/reprocess | Selective sync sloganı byte evidence değildir |
| EXIT-01 | Clean-room export/import preserving negative behavior and history | SQLite/JSON/custom protocol | PostgreSQL/Storage/stream/bucket/checkpoint/license | Portability claim veya SDK license tek başına exit değildir |
| AI-01 | Same bounded task, least privilege, independent reviewer, no owner debug | 14 custom task families | Stream/RLS/queue/service task families | Hazır primitive task/evidence yükünü yok etmez |

Hard-fail invariants: partial package current, wrong-base merge, local success as server success,
lost response blind duplicate, recall bypass, silent high-consequence LWW, consent-free large cellular
transfer, restore resurrection, plaintext fallback, direct privileged provider path, inaccessible
critical state, or owner repair dependency.

## 5. Frozen workload ve data-use eşitlik denetimi

### 5.1 Ortak workload kontrolü

İki dossier'in workload tablosu ve requirements synthesis aynı değerleri taşıyor:

| Boyut | Frozen condition | Equivalence finding |
|---|---|---|
| Surfaces | Flutter phone consumer; browser Internal Operations | Her iki candidate aynı boundary'yi kullanıyor |
| Order | Android-first, iOS-later | Her iki candidate Android pass'i iOS yerine saymıyor |
| Horizon | First release + 24 months maintenance | Her iki cost/maintenance dosyasında aynı horizon kullanılmalı |
| Cadence | Yılda 4 release window + safety correction | Stream/source/schema/API ve Drift migration watch aynı takvimde olmalı |
| MAU | 1,000 launch; 10,000 growth; 50,000 stress | A ve B için aynı üç tier; price snapshot tier yerine geçmez |
| Monthly use | 2 compact transfer/MAU; 10% optional media at 100 MB average; 0.5 photo at 3 MB | A'nın custom transferi ve B'nin stream/reprocess/queue transferi aynı formülle ölçülmeli |
| Android constrained | API 29, 4 GB RAM, 64 GB, 2 GB free | Drift WAL/temp ve PowerSync compaction/checkpoint aynı peak-space testine tabi |
| Android main | Android 13+, 6 GB RAM, 128 GB | Aynı lifecycle/network/storage/a11y evidence |
| iOS | Oldest iOS 16.4-capable + current standard non-Pro | iOS-later lane iki aday için release gate |
| Network | Wi-Fi 50 Mbps; cellular 10 Mbps; constrained 1 Mbps/300 ms/5% loss; 72h offline | Background, retry, duplicate, stream and API behavior aynı |
| Local normal/stress | 3/10 motorcycles; 250/2,000 history; 50/500 photos; 100/1,000 notes; 20/200 pending; 3/30 conflicts | Candidate-specific queue/DB/stream size reduction yapamaz |
| Seeded failures | Duplicate, partial upload, corrupt package, interrupted DB change, correction, withdrawal, recall | A custom protocol veya B provider queue bu seti daraltamaz |
| Accessibility | Turkish TalkBack/Switch Access and VoiceOver/Switch Control | Screenshot/automated tree tek başına yeterli değil |

TASK-SIM-OFFSYNC-001 bu workload'un tamamının yerine geçmez. O dosyanın E0..E8 zinciri tek seçili
task, bir P1/D1, bir O-77, bir R-12/C-55 ve bekleyen 150 MB media ile bounded cross-candidate
simulation'dır. A ve B için eşittir; ancak 3/10 device data, 24-month tier, 18 EQ + 18 MPR ve
real-device evidence'in yalnızca bir alt örneğidir.

### 5.2 Karşılaştırma aritmetiği; benchmark değil

Frozen monthly workload için basit üst fixture aritmetiği:

- 2 x 12 MB compact target = 24 MB/MAU/month;
- 10% x 100 MB average optional media = 10 MB/MAU/month;
- 0.5 x 3 MB user photo = 1.5 MB/MAU/month;
- toplam basit fixture üstü yaklaşık 35.5 MB/MAU/month, retry, delta, stream reprocess, status,
  auth, duplicate, object overhead ve compression hariç.

Bu yalnız worksheet girdisidir: 1,000 MAU için 35.5 GB, 10,000 MAU için 355 GB, 50,000 MAU için
1.775 TB basit üst fixture olarak hesaplanabilir. Bu değerler network benchmarkı, SLA, commercial
quota veya final product limit değildir. 150 MB optional media per-artifact comparison constant'ı;
monthly workload'taki 100 MB average kullanım ile aynı şey değildir.

### 5.3 Data-use normalization

| Ölçülecek alan | A Drift/custom | B PowerSync | Normalized evidence |
|---|---|---|---|
| Logical compact payload | Package manifest/closure | Stream rows + app package closure | Selected task, required closure and 2 GB negative manifest |
| Transfer retries | Custom resume/idempotency | Queue/stream retry, checkpoint/reprocess | Per-attempt bytes, reason, dedup and final bytes |
| Delta/update | Exact base/cursor | Stream checkpoint/base mapping + API reissue | Wrong-base/corrupt/out-of-order bytes and full fallback |
| Optional media | Separate on-demand object | Separate Storage/object lane, not Sync Stream | 150 MB gate, cancellation, consent, object egress |
| API/control traffic | Status/reconcile/recall | Auth/stream/upload/status/reprocess | Count and bytes, not hidden in package total |
| Local peak | SQLite staging/WAL/verify | SQLite/WAL/queue/compaction/checkpoint | Old + new + verify + cleanup on 2 GB free |
| Cache eviction | App-owned lane policy | Synced table/queue + app/storage policy | 250 MB fixture; user history/photos and active closure excluded |
| Unrelated catalog | Explicit API/package deny | Stream predicate/RLS deny | 2 GB never selected; deny evidence, not empty result claim |

Audit finding: A'nın explicit protocolu data-use accounting'i daha görünür kılabilir; B'nin
selective stream'i transport bytes'ını azaltabilir. Hiçbiri wire/peak/egress/retry evidence'i
olmadan data-efficient PASS alamaz. A'nın “no full catalog” ve B'nin “selective sync” cümleleri
aynı manifest/byte ledger ile doğrulanmalıdır.

## 6. Hidden burden ve marketing-primitive denetimi

### 6.1 A — custom code/semantic burden'in gizlenmemesi

A'nın app-owned kontrolü bir avantaj veya risk olabilir; fakat aşağıdakiler “Drift sağlar” veya
“sync-provider fee yok” diye kapatılamaz:

1. package manifest, dependency closure, digest, generation, stage/promote ve anti-rollback;
2. exact-base delta, cursor gap, wrong-base, full reissue ve tombstone;
3. operation envelope, idempotency ledger, status lookup, lost response ve cross-plane unknown;
4. consequence/classification alanlarına göre conflict/hold/review;
5. recall/delete/withdrawal floor, active-work closure, old-client and restore quarantine;
6. cache/temporary/media/history/pending-operation lane ayrımı ve low-space peak;
7. encryption engine/key custody/re-key/backup exclusion and key loss;
8. background/network/clock/lifecycle state mapping and observability;
9. account-light/profile migration, clone/wrong-account/device generation;
10. API authorization, object capability, protected audit, outage/billing and independent custody;
11. Android/iOS generated/native/channel/accessibility maintenance;
12. portable export, clean-room import, custom protocol replacement and 24-month AI maintenance.

Audit normalization: A cost sheet, task catalogue and EQ/MPR evidence record bu semantic surface'i
line-item olarak göstermelidir. Custom semantic surface “provider fee” ile sıfırlanamaz.

### 6.2 B — service/provider burden'in gizlenmemesi

B'nin PowerSync primitive'leri aşağıdaki ek yüzeyleri getirir veya dışarıda bırakır:

1. PowerSync Cloud vs self-host seçimi; service version, license/FSL/source-available terms, billing,
   soft-limit/deactivation, region/support ve outage;
2. Sync Streams DSL, source schema/publication/replication, bucket/checkpoint/lag/reprocess ve old-client;
3. RLS vs stream filter/column/classification equivalence; Supabase grant/view/Storage/Auth/JWKS matrix;
4. uploadData/FIFO queue, validation 2xx/error table, poison operation, dead-letter and status lookup;
5. package manifest, exact base/generation/digest, recall floor, tombstone and complete closure — provider
   transportunun üstünde ayrıca Kavriva semantic layer;
6. PowerSync local schema + app-owned metadata migration; source DDL/stream/app/API release order;
7. SQLite/WAL/compaction/queue peak space; object bytes, Storage backup, audit and negative floor custody;
8. encryption/key lifecycle, native SDK/plugin/ABI, Android/iOS background and accessibility;
9. clean-room export/import of source, objects, stream/bucket/checkpoint, queue/conflicts and license transition;
10. additional API/monitoring/on-call/incident/exit costs in addition to Supabase/Storage/egress.

Audit normalization: selective sync, local queue, causal consistency, encryption, background support,
checkpoint veya pricing headline yalnız candidate primitive olarak yazılmalı; common product authority
ve recovery evidence'i olarak puanlanmamalıdır.

### 6.3 Burden parity table

| Surface | A hidden burden | B hidden burden | Normalized requirement |
|---|---|---|---|
| Package | Custom manifest/staging/closure | Stream rows still need package layer | Same PKG-01/02 artifact and negative tests |
| Delta | Custom cursor/base/anti-rollback | Checkpoint is not exact package delta | Same DLT-01 exact-base/full-reissue test |
| Operations | Custom outbox/status/idempotency | PowerSync queue plus API ledger/status mapping | Same OPS-01/02 state machine |
| Conflict | Custom policy/review/audit | Provider unopinionated; default LWW danger | Same classification and two-sided conflict record |
| Recall | Custom floor/tombstone/reach-back | API floor plus stream/RLS reprocess | Same RCL-01, delivery not authority |
| Encryption | Mechanism/key choice open | Provider encryption option plus app key custody | Same KEY-01 matrix and real device tests |
| Migration | Drift schema/data/restore custom | Raw tables + source/stream/API additive order | Same MIG-01 failure matrix |
| Platform | Drift/SQLite/native channel | PowerSync/SQLite/encryption/native channel | Same PLT-01 Android/iOS/a11y matrix |
| Outage | API/DB/object/auth/key/backup | Above plus PowerSync service/stream/billing/Mongo | Same owner-readable states; B extra planes not omitted |
| Cost | Engineering/maintenance/incident/exit | Cloud/self-host/license/service cost | Same 24-month BOM and incident/exit workbook |
| Exit | Custom protocol replacement | Stream/bucket/checkpoint/license replacement | Same clean-room behavior, not export file count |
| AI | 14 semantic task families | Stream/RLS/queue/service task families | Same AI-01 task granularity and credentials |

## 7. EQ-01–EQ-18 equivalence crosswalk

All rows use the requirements synthesis scenario, not a candidate-specific easier variant. Current
disposition for both candidates is HELD. A primitive or documentary plan becomes PASS only after
the same future artifact and real-device/authority gate is closed.

| ID | Common oracle | A path and risk | B path and risk | Audit finding / normalization |
|---|---|---|---|---|
| EQ-01 | Only selected motorcycle/task compact closure; 2 GB catalog not requested; manifest/size/dependency evidence | A custom package manifest can make scope explicit; proof depends on issuer/closure/byte ledger | Sync Stream predicate and RLS can scope rows; stream alone does not prove closure or deny all 2 GB paths | NORMALIZE: same request/response manifest, denied-query evidence and wire-byte ledger. Stream selectivity is not a lower evidence bar |
| EQ-02 | Partial/corrupt transfer never current; old complete package remains | Drift stage/digest/atomic promote is proposed; process/peak-space evidence open | PowerSync checkpoint/local transaction helps transport, but cross-row safe package promote is app-owned | NORMALIZE: inject cut/digest/process kill identically; require current pointer, prior generation and cleanup evidence |
| EQ-03 | Exact base ID/generation/digest; wrong-base/out-of-order rejects; full compact fallback | Custom cursor and delta contract are the burden | Checkpoint/causal consistency is not automatically package base/digest/tombstone fence | ASYMETRİ RİSKİ: do not credit B checkpoint as DLT-01; require same mismatch matrix and full reissue |
| EQ-04 | 72h bounded offline; visible freshness/risk; no invented recall; unknown high consequence holds | Package risk/freshness policy custom; numeric windows open | Stream TTL/checkpoint/local rows are transport context, not product freshness/eligibility | NORMALIZE: same server generation/expiry/risk oracle and offline exposure record; TTL is not PASS |
| EQ-05 | Missed push/offline recall; reconnect/action revalidation wins; safe closure/history remain | API floor/tombstone/reach-back custom and independent emergency path open | API floor plus stream/RLS tombstone/reprocess needed; live stream cannot teach offline device | EŞİT external result; require same negative-floor artifact and late-delta/late-upload test |
| EQ-06 | Foreground/network return reconciles release/capability/suspension/ops; duplicate maps to original ID | Custom outbox/API status/idempotency | FIFO upload queue and API status; queue drain/HTTP 2xx is not acceptance | NORMALIZE: same operation ledger, status lookup and server generation trace; transport callbacks ignored as authority |
| EQ-07 | Freshness expiry stops next physical step; safe-stop/closure remains reachable | Custom active-work boundary/safe closure | Stream/package freshness must be mapped by API; TTL cannot define safe boundary | EŞİT rule; use same physical-state mapping and a11y state, not provider TTL |
| EQ-08 | Material guide change stops old continuation; reviewed safe remap only | Custom release/package remap and active-work capture | Source/stream version plus API/package builder; old stream row is not safe remap | NORMALIZE: same reviewed mapping artifact, no client-invented reversal; B schema additive order does not close content semantics |
| EQ-09 | Clock/reboot/restore cannot extend authority; restore quarantine; history version retained | Drift/local manifest quarantine and cross-plane floor open | PowerSync local/bucket/checkpoint restore also needs API floor/object/audit recheck | EŞİT external result; same restore manifest and anti-resurrection test; backup/provider restore success not enough |
| EQ-10 | Old client/new safety semantic fails closed; representable teaching/history/recovery only | Capability envelope and full compatible reissue custom | Stream schema may be flexible/additive; app semantic capability still required | ASYMETRİ RİSKİ: “client migration not required” cannot lower B's old-client gate |
| EQ-11 | Stable operation ID one effect; lost response UNKNOWN/status lookup; blind duplicate denied | Custom operation ledger/status is large semantic burden | Per-client PowerSync ID plus API ledger; provider ID alone is not protected accepted-operation floor | NORMALIZE: same payload fingerprint, status endpoint, accepted/rejected/conflict/unknown trace and duplicate negative test |
| EQ-12 | High consequence preserves both sides/visible hold; bounded low-risk merge only | Custom classification/merge/audit/review | PowerSync backend unopinionated; default LWW/deletes-win examples cannot be used | ASYMETRİ RİSKİ: B marketing/default conflict primitive gets no credit; A custom policy also needs real evidence |
| EQ-13 | Optional/re-fetchable evicted first; active closure/pending/required attachment protected | App-owned lanes and pinning explicit; low-space/peak open | Synced DB/queue cleanup and Storage object policy still need app classification/pinning | NORMALIZE: same 250 MB/2 GB-free peak and user-data protection evidence; cache fixture not product cap |
| EQ-14 | Device loss distinguishes server accepted, synced, pending/local-only, media/lost | App-owned local operation/migration/rebind custom | Replacement reauth/stream retrieves server rows; local queue/object/key recovery remains open | EŞİT rule; same account/device-generation/key matrix and no invented completion |
| EQ-15 | Account-light migration preview, stable IDs, classification/conflicts, source usable on cancel/failure | Custom migration session and wrong-account/clone quarantine | Auth/stream subscription switch is not migration; API session and classification still required | ASYMETRİ RİSKİ: B auth primitive cannot shorten migration evidence; require same MIG-01 artifact |
| EQ-16 | API/provider/billing outage holds mutation/UNKNOWN; safe local/reference/recovery; no owner repair | Supabase/API/DB/object/auth/key outage surfaces | Above plus PowerSync Cloud/self-host/stream/billing/deactivation/Mongo surfaces | NORMALIZE: A must list all base planes; B must list extra service planes; same owner-readable runbook and no SQL/SSH |
| EQ-17 | Publish fenced by current suspension generation; newer negative wins; protected audit | Custom API release fence and audit | PowerSync stream cannot fence publish; API must perform exact same check | EŞİT: no stream/checkpoint advantage; same generation race and old in-flight negative test |
| EQ-18 | DB/object/audit/identity/package/ops/negative floor clean-room reconcile; partial labeled | SQLite/JSON/custom protocol export still needs semantic replay | PostgreSQL/Storage/stream/bucket/checkpoint/queue/license export much larger | NORMALIZE: artifact inventory, negative behavior and clean-room action trace; successful provider/DB backup alone no PASS |

EQ audit summary: A and B declare the same external result for all 18 rows and both remain HELD.
The main asymmetry risk is B being credited for Sync Streams/checkpoints as if they close package,
recall or authority semantics; the reciprocal risk is A being credited for “app-owned control” as
if custom protocols were already tested or costed.

## 8. MPR-01–MPR-18 equivalence crosswalk

MPR rows use the official Android, Apple and Flutter/Dart limits already researched. No lifecycle
callback, background API, key API, backup, SDK feature or provider service is accepted as product
correctness without the common artifact and later real-device evidence.

| ID | Common oracle | A path and risk | B path and risk | Audit finding / normalization |
|---|---|---|---|---|
| MPR-01 | Purgeable cache separate from history/pending/package closure; cache miss rebuilds only | Drift lanes can be app-owned; exact storage/backup/purge placement open | Synced SQLite projection can be re-synced; queue/package metadata and history need non-purgeable policy | EŞİT: classify every local table/file/object; same cache-clear and cold-start test |
| MPR-02 | 12 MB cut at 50%, digest failure/process kill; old complete generation survives | Stage/promote contract explicit but unimplemented | Stream checkpoint does not prove complete safety closure or atomic package promote | ASYMETRİ RİSKİ: same injection and prior-pointer evidence; provider checkpoint no shortcut |
| MPR-03 | DB/history/outbox/media metadata transaction all-or-nothing; orphan quarantined; no duplicate effect | Drift transaction can cover local rows but not server/object/audit | PowerSync table+queue atomicity helps; app metadata/object dependency still separate | NORMALIZE: same crash point and cross-plane PARTIAL/UNKNOWN state; neither local atomicity is global |
| MPR-04 | Process death/lifecycle callback omission cannot erase or falsely complete | Drift correctness before Flutter callback; real Android/iOS run open | PowerSync queue/background catch-up best-effort; SDK callback cannot be commit | EŞİT: same kill/force-quit/incoming-call test; background completion claim REJECT |
| MPR-05 | Backup/restore stale/partial enters quarantine; negative floor prevents resurrection | App manifest/quarantine/floor custom | Local DB/bucket/checkpoint restore adds provider state but still needs API/object/audit floor | NORMALIZE: same cross-plane restore manifest and restore-before-launch evidence |
| MPR-06 | Uninstall/reinstall does not assume local state; reauth/rebind; key/pending loss truthful | Drift data/key/device generation custom | Auth, subscription and PowerSync local state/key behavior open | EŞİT: same reinstall/restore/account continuity matrix; no stale token/duplicate bind |
| MPR-07 | Key unavailable/invalidated/auth/rekey states; no plaintext/silent replacement | Encryption mechanism intentionally open; key custody burden explicit | PowerSync encryption option is a primitive; exact SQLCipher/platform key path still open | ASYMETRİ RİSKİ: B “encryption available” cannot outrank A “mechanism open”; same key matrix and binary evidence |
| MPR-08 | Versioned/idempotent migration or quarantine; low-space/future-schema no destructive reset | Drift schema/migration task explicit; integration and low-space open | Synced schema may avoid some client migration; raw tables/source/stream/API release order remains | ASYMETRİ RİSKİ: no-migration marketing claim cannot remove B migration task; same old/new/interrupt/future schema test |
| MPR-09 | Doze/suspend/force-quit only delay; durable state resumes foreground; no background correctness | Custom queue/transfer scheduling open | PowerSync/WorkManager catch-up also best-effort; iOS force-quit boundary remains | EŞİT: same background/force-quit evidence and user state; scheduler name not evidence |
| MPR-10 | Battery/thermal/low-power prioritizes core; optional media pause/cancel; no retry storm | App scheduler/priority custom | Provider queue/stream plus media scheduler could create retries; service does not set product priority | NORMALIZE: same battery/thermal trace, bytes/retries and visible defer reason |
| MPR-11 | 1 Mbps/300 ms/5% loss, kill/reconnect; stable ID, unknown, no duplicate | Custom API/idempotency | FIFO queue + operation ID + API; poison/blocked/dead-letter semantics open | EŞİT external rule; same lost-response/late-ack and blocked queue evidence |
| MPR-12 | >25 MB cellular explicit choice; 12 MB core/150 MB media/2 GB catalog separated | App transfer policy explicit; network OS hints not consent | Sync Stream/network policy does not itself provide consent UI or data budget | ASYMETRİ RİSKİ: selective sync cannot lower consent/size evidence; same UI/a11y and wire-size log |
| MPR-13 | Peak old+new+verify space; optional evict first; NEEDS_SPACE; no user loss | Drift WAL/temp/verify placement open | PowerSync WAL/compaction/checkpoint/queue peak open | NORMALIZE: exact 2 GB-free constrained device and removable/iOS purge test |
| MPR-14 | Server generation/monotonic interval, wall-clock anomaly visible; stale cannot freshen | App clock state custom | PowerSync checkpoint ordering is not freshness or negative floor | EŞİT: same clock-change/reconnect/restore and server-time trace |
| MPR-15 | Turkish pending/paused/failed/conflict/stale/unknown/blocked/complete semantic states and actions | Flutter UI plus Drift state mapping; real AT absent | Flutter UI plus PowerSync/API mapping; SDK offers no product a11y proof | EŞİT: same TalkBack/VoiceOver/Switch Access script; screenshots/tree not PASS |
| MPR-16 | Flutter/native/channel/generated dependency visible; Android success not iOS gate | Drift/SQLite/encryption/native path and iOS parity open | PowerSync/SQLite/encryption/native plugin surface is at least as visible, not less | NORMALIZE: exact versions/generated diff/owner/fallback for both; unmaintained critical path REJECT |
| MPR-17 | Compact core complete without 150 MB media; 250 MB cache/2 GB negative; object/classification separate | Separate package/media/cache contract custom | Stream rows/queue versus Supabase Storage object lane; signed handle/revoke/backup open | EŞİT: same peak installed/temp, cancellation/eviction and object recovery artifact |
| MPR-18 | Exact client/package/release/generation/recall floor; mixed/rollback cannot positive or resurrect | Custom manifest/floor/old-client behavior open | Stream/API version/reprocess/old-client and service release order open | NORMALIZE: same mixed-release/rollback/recall matrix; current stream alone not authority |

MPR audit summary: both candidates are correctly HELD for real Android/iOS evidence. B's SDK/service
does not lower the mobile platform bar; A's app-owned database does not remove native key, backup,
storage or lifecycle evidence.

## 9. Encryption/key, migration, platform, outage and exit parity

### 9.1 Encryption and key

| Question | A | B | Required normalization |
|---|---|---|---|
| Mechanism | Drift/SQLite encryption engine remains open | PowerSync encryption option plus SQLite/platform key path remains open | Neither gets a mechanism PASS without exact version/build/config |
| Key custody | Android Keystore/iOS Keychain integration custom | Same platform stores plus provider SDK/native integration | Same key state enum: available, auth-required, invalidated, missing, rekey |
| Backup/restore | Explicit exclusion/reference/restore quarantine required | Same, plus PowerSync local/bucket/service state | Same backup matrix; no raw secret export |
| Reinstall/passcode/biometric | Real device tests absent | Real device tests absent | Same MPR-06/07 matrix |
| Failure behavior | No plaintext/silent replacement; HELD | Same; provider exception cannot be swallowed | Same user-visible state and owner action |

Normalization: B'nin “encryption available” metadata'sı A'nın “mechanism open” durumundan
daha yüksek bir evidence label alamaz. Her iki candidate exact library/ABI/version, key reference,
backup exclusion, rotation/re-key, invalidation and clean-room behavior artifact'i üretmelidir.

### 9.2 Migration and release

| Boundary | A burden | B burden | Common evidence |
|---|---|---|---|
| Local schema | Drift generated snapshots/stepwise migration | PowerSync synced schema plus app-owned raw tables | Old/new schema, interrupted migration, low space, future schema |
| Domain semantics | Package/operation/conflict/custom format migration | Same package/operation plus source/stream/API semantic migration | State-preserving migration log/export |
| Source/stream | API/package release order | Postgres DDL, publication/stream, transform/cast, app/API order | Closed release graph and old-client hold |
| Rollback | Prevent old package/negative floor resurrection | Prevent old stream/checkpoint/service reprocess resurrection | Anti-rollback and recall floor |
| Owner action | No owner repair | No provider console/SQL/SSH repair | Same owner-readable recovery/runbook |

Normalization: “PowerSync synced schema migration gerektirmeyebilir” yalnız transport schema
primitive'idir. Application package, operation ledger, encryption metadata, release capability,
RLS/stream policy and API state migration remains in scope. A'nın Drift migration surface'i de
green generated snapshot ile kapanmaz.

### 9.3 Platform

Both candidates must use the same:

- Android API 29 constrained and Android 13+ main profiles;
- iOS 16.4-capable oldest-end and current non-Pro profile;
- process kill, force-quit, Doze/suspend, incoming call, low battery/thermal, storage pressure,
  network loss/reconnect, clock change, backup restore, reinstall and key invalidation;
- Turkish TalkBack/Switch Access and VoiceOver/Switch Control;
- versioned generated/native/channel error map and owner-owned fallback.

B has additional PowerSync/SQLite/encryption native dependency surface; A has Drift/SQLite/encryption
and app-owned protocol surface. Neither may claim Android-first evidence closes iOS-later.

### 9.4 Outage and owner-safe operations

| Outage plane | A | B | Normalized state |
|---|---|---|---|
| API/auth/JWKS/session | HELD/UNKNOWN/UNAVAILABLE | Same | Positive sensitive mutation stops |
| Supabase DB/Storage/object | HELD/UNKNOWN; independent audit/floor | Same | Object and DB state not conflated |
| Key/backup/restore | KEY/RESTORE_QUARANTINE/HELD | Same plus provider local state | No owner repair |
| Sync transport | No separate sync service, but custom retry/reconcile/API | PowerSync service/stream/checkpoint/FIFO/dead-letter | SYNC_UNAVAILABLE, QUEUE_HELD, RECONCILING explicit |
| Billing/account/region | Supabase/API plan/region | Supabase plus PowerSync Cloud/plan/deactivation/license | BILLING_HELD or SERVICE_UNAVAILABLE; no console repair |
| Provider/admin path | Studio/admin hidden bypass prohibited | PowerSync/Supabase console hidden bypass prohibited | API boundary and protected audit remain |

B has more outage planes; A has less transport service but more app/API semantics. This is not a
winner claim. It is a requirement to expose every plane and every owner-readable state in the same
runbook template.

### 9.5 Exit

Common clean-room exit must preserve:

1. current/history/local-only/accepted/unknown/conflict/held operation meanings;
2. package manifests, generations, digests, dependency closure, tombstones, recall/delete floors;
3. object bytes, classification, lineage, quarantine/finalization, and private/local semantics;
4. protected audit and non-restorable negative/security/deletion/accepted-operation/migration floor;
5. Auth/session/device/profile mapping without raw secret export;
6. schema/config/migration/release/capability versions and old-client behavior;
7. full package reissue and wrong-base rejection;
8. clean-room import with partial/quarantine labels and observable recovery;
9. no provider console, owner SQL/SSH or hidden license/service authority.

A's SQLite/JSON portability is a logical control opportunity, not proof that custom API semantics
are replaceable. B's Apache-2.0 client or self-host possibility is not proof that service license,
bucket/checkpoint/stream/queue/conflict history and FSL/source-available terms are portable.

## 10. AI task surface audit

### 10.1 Common task catalogue

Both candidates must expose the following same bounded task IDs. Candidate-specific files or services
may differ, but input, output, forbidden scope, reviewer and acceptance state must not:

| AI task ID | Shared task | A emphasis | B emphasis |
|---|---|---|---|
| AI-P01 | Local schema/data lane | Drift schema, generated migration | Synced/app-owned schema, raw tables |
| AI-P02 | Package closure/stage/promote | Custom manifest and transaction | Stream projection plus app package layer |
| AI-P03 | Exact delta/cursor/floor | Custom protocol | Checkpoint-to-package fence and API reissue |
| AI-P04 | Durable operation/idempotency | Outbox/status ledger | Upload queue/API/status mapping |
| AI-P05 | Conflict/hold/review | Classification/merge policy | API policy over unopinionated transport |
| AI-P06 | Cache/media/storage | App lanes and low-space | Synced DB/queue/Storage object separation |
| AI-P07 | Recall/delete/active work | Tombstone/floor/reach-back | API floor + stream/RLS reprocess |
| AI-P08 | Key/encryption/backup | External engine/key custody | SDK encryption + platform/app key custody |
| AI-P09 | Lifecycle/network/clock | Custom retry/reconcile state | Queue/checkpoint/background service behavior |
| AI-P10 | Restore/device/clone | App quarantine/device generation | Source/bucket/checkpoint + app quarantine |
| AI-P11 | Account-light/profile migration | Custom migration session | API migration before stream binding |
| AI-P12 | API/auth/privileged paths | Kavriva API/Supabase boundary | Upload API/RLS/Storage/JWKS matrix |
| AI-P13 | Platform/accessibility/release | Drift/native/iOS lane | PowerSync/native/iOS lane |
| AI-P14 | Outage/cost/exit/runbook | Custom semantic and API ops | Cloud/self-host/service/license ops |

A dossier's list length may differ in presentation, but no candidate may omit any AI-P01..P14
surface by saying “SDK handles it” or “custom protocol”.

### 10.2 TASK-SIM-OFFSYNC-001 parity

The task simulation is equivalent at the declared task level:

| Dimension | A | B | Audit |
|---|---|---|---|
| Fixture | 12 MB cut at 50%, wrong-base D1, process kill, O-77, lost response/duplicate, R-12/C-55, 150 MB no consent | Same | EŞİT |
| Packets | A-P01..A-P08 | B-P01..B-P08 | Same P01..P08 semantics |
| Expected states | Package current/staged/rejected, operation pending/unknown/reconciling, recall/held, media blocked | Same | EŞİT |
| Conceptual files | App-owned package/outbox/API/recall/media/platform | Stream/RLS/queue/API/recall/media/platform/service | Candidate-specific, no scope reduction |
| Recovery | Full bounded reissue, status lookup, floor, conflict hold, consent gate | Same plus stream reprocess/queue/outage handling | EŞİT external oracle |
| Reviewer evidence | Manifest/digest/transaction/API/platform/a11y/owner | Stream/RLS/queue/API/platform/a11y/owner | Same EVID-01..12 fields |
| Owner action | Evidence/capacity decision, no DB debug | Evidence/capacity decision, no console/queue debug | EŞİT |
| Current result | HELD | HELD | EŞİT; not a benchmark |

Normalization caveat: simulation's one task and one operation are deliberately bounded. It cannot
replace full 18 EQ + 18 MPR, frozen scale tiers, 24-month cost, key/migration, real platform,
outage or clean-room exit evidence. A/B should not report P01..P08 as a winner or benchmark.

## 11. Documentation normalization actions

Before an Architect/Judge comparison, apply these documentation changes conceptually to both dossier
sets. This audit does not edit those source dossiers.

### 11.1 One common evidence row

Every EQ/MPR row for both candidates should use exactly these columns:

1. scenario ID and fixture revision;
2. failure injection and precondition;
3. external expected state/authority;
4. candidate path;
5. provider/framework primitive boundary;
6. custom semantic boundary;
7. conceptual files/contracts/services touched;
8. user-visible/accessibility state;
9. evidence artifact and evidence label (DOCUMENTARY, SIMULATED, REAL-DEVICE);
10. recovery/rollback/anti-resurrection action;
11. owner action and forbidden owner-debug path;
12. cost/data/exit dependency if applicable;
13. PASS/HELD/REJECT and exact missing/failed gate.

### 11.2 Candidate surface manifests

Require one machine-readable conceptual manifest per candidate:

- A: Drift schema/generator, local transaction/WAL, package/delta protocol, operation/status API,
  conflict/recall floor, key/encryption, Flutter/native, Supabase/API, backup/object/audit, cost/exit.
- B: PowerSync SDK/service/version/license, stream definitions/source publication, RLS/Auth/JWKS,
  local synced/app schema, upload queue/FIFO/dead-letter, Kavriva API/status, package/delta layer,
  Storage/object/audit/floor, key/encryption, Flutter/native, Cloud/self-host, cost/exit.

The manifest must name owner, reviewer, version, dependency, data classification, failure state,
export artifact and exit path. “Provider handles it” or “custom protocol” cannot be a terminal row.

### 11.3 Common cost worksheet

Both candidates must fill the same 24-month workbook for 1,000/10,000/50,000 MAU:

- platform/base: Supabase/API/Auth/Storage, devices/stores, monitoring, qualified safety/a11y review;
- transport: A custom protocol engineering/maintenance/observability versus B Cloud/self-host,
  stream/service/license/Mongo/replicator/LB/backup/monitoring;
- semantic: package/delta, operation/idempotency, conflict, recall/floor, migration, encryption/key;
- data: compact/media/photo bytes, retry/reprocess/status/auth, object egress, peak local storage;
- incident: API/provider/billing/region/JWKS/key/outage, restore, backup and emergency recall;
- exit: clean-room export/import, replay, license/contract replacement, key/object transition;
- owner/AI: review, runbook, nontechnical owner time and forbidden debugging capacity;
- overage/soft limit/tax/FX/hard-stop/alert behavior.

“No separate sync-provider fee” must be labeled as an assumption with confidence and residual
engineering cost. PowerSync Free/Pro/Team price headline must be labeled as a snapshot and not as
a total bill, hard cap or purchase approval. The manager's future TRY planning ceiling is not spend
authority and cannot replace the worksheet.

### 11.4 Common data-use ledger

Each candidate must emit the same fields:

- request/package/stream ID, scope, manifest/digest/generation;
- payload logical bytes, wire bytes, compression, retries, duplicate bytes and fallback bytes;
- API/auth/status/reconcile bytes;
- media object bytes, consent/transport, cancellation and re-fetch;
- local staging/WAL/queue/compaction/verify peak;
- cache eviction and user-created data exclusion;
- 2 GB denied query/stream evidence;
- service/cloud/storage/egress cost linkage.

### 11.5 Common encryption/migration/platform/runbook gates

Use the same test scripts and state names for:

- key unavailable/invalidated/auth-required/rekey/missing;
- interrupted/future/old-client/low-space migration;
- process kill/force-quit/Doze/suspend/clock/backup/reinstall;
- TalkBack/VoiceOver/Switch Access pending/unknown/held/conflict/blocked;
- API, DB, object, auth, key, sync service, billing, region and license outage;
- clean-room import and negative-floor anti-resurrection.

### 11.6 Common disposition rule

No candidate receives a positive score for a provider primitive or a custom design claim. Current
state stays:

- PASS only with the same external behavior, official/product evidence, later real-device/authority
  plan and independent review;
- HELD for missing critical evidence, cost, owner capacity, restore/exit/key/migration/platform;
- REJECT-IF-UNMITIGATED for common hard-fails.

## 12. Final audit disposition

Equivalence status: CONDITIONAL / NOT YET PROVEN.

The dossiers are structurally comparable and the task simulation is genuinely equal at the fixture,
state, packet and reviewer level. They are not yet evidence-equivalent in the broader sense because:

1. A's custom semantic engineering and maintenance burden is not priced as a complete BOM;
2. B's service/cloud/self-host/license/stream/RLS/queue/reprocess burden is not priced or operated as a
   complete BOM;
3. B's transport primitives risk being mistaken for package/authority/recall/restore semantics;
4. A's app-owned protocol risks being mistaken for tested portability/correctness;
5. encryption/key, migration, platform, outage, accessibility and clean-room exit are still documentary;
6. the common task simulation is a bounded subset, not a 36-scenario benchmark.

Current result:

| Candidate | Current audit result | Required next action |
|---|---|---|
| A Drift/custom | HELD — semantic/cost/real-platform evidence pending | Fill common surface manifest, cost/data ledger, key/migration/platform/outage/exit artifacts |
| B PowerSync | HELD — provider/service/semantic/real-platform evidence pending | Fill stream/RLS/queue/service/license/exit artifacts plus same key/migration/platform/outage evidence |

No winner, no ranking, no code, no prototype, no benchmark and no provider purchase is authorized by
this audit. A future decision can only use normalized artifacts and the same PASS/HELD/REJECT gate;
unknown state remains HELD and any common hard-fail remains REJECT-IF-UNMITIGATED.
