# DEBATE-009 — Independent Reviewer B: Solo-owner / TCO / Security / AI-operability

Status: HELD — iki finalist de eşit kanıt bekliyor; winner yok; ADR, kod, satın alma ve abonelik yok  
Tarih: 2026-09-18 (Europe/Istanbul)  
Reviewer: Bağımsız Reviewer B  
Kapsam: Finalist A — app-owned SQLite/Drift + Kavriva custom bounded package/delta + durable operation API; Finalist B — PowerSync + Supabase source + Kavriva API

## 0. Bu incelemenin sonucu

Bu dosya DEBATE-009 için teknik olmayan tek sahip, AI-assisted implementation, daha sonra planlanacak TRY 2.000–3.000/ay tavanı ve owner-debug yapılmaması şartları altında bağımsız bir TCO, güvenlik ve işletilebilirlik incelemesidir. Bir teknoloji seçmez, satın alma yapmaz, kod veya prototip üretmez ve bir adayı otomatik olarak yedek/winner ilan etmez.

Belgesel sonuç:

| Sonuç | A Drift/custom | B PowerSync |
|---|---:|---:|
| EQ-01..EQ-18 | 18 HELD | 18 HELD |
| MPR-01..MPR-18 | 18 HELD | 18 HELD |
| PASS | 0 | 0 |
| REJECT | 0 (şu an gözlenen değil; aşağıdaki ihlal koşulları saklı) | 0 (şu an gözlenen değil; aşağıdaki ihlal koşulları saklı) |
| Reviewer disposition | HELD | HELD |

Bu HOLD olumlu güvenlik kanıtı değildir. Gerçek cihaz, auth/API, restore/exit, encryption/key, accessibility, provider-outage, maliyet ve owner-runbook kanıtı yoktur. Her iki aday da documentary olarak güvenli bir state modeli tarif edebilir; hiçbiri mevcut belgelerle production-safe veya TRY tavanına uygun kanıtlanmış değildir.

## 1. Bağlayıcı soru, varsayımlar ve kanıt disiplini

### 1.1 Review sorusu

Teknik olmayan bir owner, iki Android-first / iOS-later lane'ini AI ile taskize ederken:

1. hangi adayın gizli mühendislik ve bakım yükünü daha açık tuttuğunu;
2. hangi bağımlılık, secret, billing, outage ve provider değişikliğinin owner'ı teknik tamire itebileceğini;
3. high-consequence write, recall/delete, conflict, restore ve negative floor sınırının gerçekten API'de kalıp kalmadığını;
4. 24 aylık maliyetin ve clean-room exit yükünün görünür olup olmadığını;
5. AI'ın bounded, diffable, bağımsız review edilebilir task'lar üretebilip üretemediğini

inceler. Bu soru “hangi SDK daha kolay?” sorusu değildir.

### 1.2 Bağlayıcı kararlar

- DEC-0033 Flutter yönünü, Android ilk lane ve iOS sonraki lane'i taşır; portable data/safety/provenance truth Flutter UI veya plugin içine saklanamaz ve owner native/build/debug yapamaz.
- DEC-0034 canonical transactional authority, server/API-mediated sensitive access, bounded versioned package, durable identified operation, visible conflict/hold/unknown, current/history/protected-audit ayrımı, anti-resurrection floor ve no-owner-debug yükümlülüklerini bağlar.
- DEC-0035 managed Supabase PostgreSQL/Auth/private Storage yönünü başlangıç fiziksel adayları olarak taşır; her high-consequence mutation Kavriva API'sinde kalır; RLS/Storage defense in depth'tir; service_role/secret client'a gitmez; Supabase Studio ürün Internal Operations yüzeyi değildir; DB backup Storage bytes'ını kapsamaz.
- Owner'ın TRY 2.000–3.000/ay miktarı daha sonraki planlama tavanıdır; spend authority, hard invoice cap, SLA veya exact total değildir.
- İki finalistte de local row, queue empty, stream checkpoint, HTTP 2xx, push/Realtime event veya provider backup current authority/accepted effect kanıtı değildir.

### 1.3 Kanıt etiketleri

- CONFIRMED-2026: resmi doküman, package metadata, changelog veya source'ta açıkça görülen primitive/sınır.
- INFERRED: primitive ile Kavriva safety contract'ının birlikte yorumlanmasından çıkan tasarım sonucu; acceptance proof değildir.
- OPEN / UNVERIFIED: plan, gerçek kullanım, sözleşme, config, cihaz, hosting, tax/FX, incident veya exit kanıtı yok.
- HELD: documentary model var, fakat güvenli olumlu sonuç için zorunlu kanıt yok.
- REJECT-IF-UNMITIGATED: düzeltme kapanmadan ilgili kullanım güvenli kabul edilemez.

Pazarlama sayfası, “offline-first”, “realtime”, “consistent”, “reactive”, hazır Flutter SDK veya fiyat başlığı safety, owner-operability, restore, conflict, recall veya exit kanıtı sayılmamıştır.

## 2. Okunan girdiler ve current official watch

İnceleme şu repository girdileri ve Supabase skill talimatları okunarak yapıldı:

- 04_TECH_STRATEGY/DEBATES/DEBATE-009__OFFLINE_SYNC_REQUIREMENTS_SYNTHESIS.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__OFFLINE_SYNC_OPTIONS_PRIMARY_RESEARCH.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__MOBILE_PLATFORM_FAILURE_RESEARCH.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__MANAGER_PROPOSAL.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__FINALIST_A_DRIFT_CUSTOM.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__FINALIST_B_POWERSYNC.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__TASK_SIM_OFFSYNC_001.md
- 00_CONTROL/DECISION_LOG.md içindeki DEC-0033, DEC-0034, DEC-0035
- C:/Users/Xpike/.codex/skills/supabase/SKILL.md ve resmi Supabase changelog.md

2026-09-18 current changelog taramasında bu review için operationally önemli breaking/watch maddeleri bulundu:

| Current watch | Review etkisi |
|---|---|
| New public tables artık Data/GraphQL API'ye otomatik expose değil; tüm projelerde enforcement 2026-10-30 | Explicit exposure/grant inventory ile RLS ayrı kanıtlanmalı; “table var, client/connector görür” varsayımı kullanılamaz. |
| Realtime schema modifications tamamen kilitli; yalnız RLS policy yönetimi açık | Realtime hint/notification yüzeyi schema migration veya custom object authority gibi kullanılmamalı. |
| Anon key ile OpenAPI spec erişimi kaldırıldı | AI/connector discovery için service_role/secret dağıtımı yapılamaz; explicit schema contract ve least privilege gerekir. |
| OAuth token endpoint 201 yerine 200 döndürüyor | Hard-coded status code, auth/session reconciliation'i kırmamalı; any-2xx ile domain acceptance ayrılmalı. |
| PostgREST otomatik retry yalnız GET/HEAD transient errors için | Bu, mutation idempotency veya duplicate write güvenliği değildir. |
| logs.all endpoint'i 2026-09-23 kaldırılıyor; yeni logs endpoint ClickHouse SQL ister | Monitoring/runbook ve AI gözlem task'ı provider API değişikliğine bağlanmamalı veya versioned tutulmalı. |
| Extension version pinning ignored; default version kuruluyor | Extension/encryption/DB migration safety'si pin varmış gibi varsayılamaz. |
| Self-host Envoy default, API_EXTERNAL_URL /auth/v1, PG 15→17 ve Analytics/Vector opt-in değişiklikleri | Self-host “çıkış kolaylığı” değil; migration, gateway, auth URL, DB ve observability bakım yüzeyidir. |

Bu watch'lar A'nın custom API'sini veya B'nin PowerSync connector'ını seçmez. İkisi için de provider change inventory, compatibility test ve owner-readable failure state gerekir.

## 3. Eşit karşılaştırma birimi

### 3.1 Ortak minimum topology

Her iki finalist aşağıdaki ortak sınırı taşımak zorundadır:

Flutter local state  
  -> bounded package lane + optional media lane  
  -> durable operation/outbox lane  
  -> Kavriva API authority  
  -> Supabase PostgreSQL/Auth/private Storage candidate  
  -> independent protected audit / negative floor / object recovery evidence

Uygulama içinde P0/P1 staging, exact base/target generation, digest/dependency closure, recall/delete tombstone, operation ID/payload fingerprint/expected version, OUTCOME_UNKNOWN, conflict/hold ve restore quarantine state'leri provider adıyla kısaltılamaz. API current auth, action-time authorization, generation fence, idempotency, conflict, audit, deletion/recall floor ve status lookup sağlar. RLS ve Storage policy defense in depth'tir.

### 3.2 Frozen fixture

| Alan | Eşit giriş |
|---|---|
| Mobil | Flutter Android-first, iOS-later; constrained Android API 29 / 4 GB RAM / 64 GB / 2 GB free; main Android 13+; oldest/current non-Pro iOS 16.4+ |
| Süre | İlk release + 24 ay; yılda 4 release window ve gerektiğinde safety correction |
| Kullanıcı/iş yükü | MAU 1k / 10k / 50k; ayda MAU başına 2 compact package transferi; optional media %10 × 100 MB; 0.5 photo × 3 MB |
| Transfer | Selected motorcycle + variant + tek task; compact core hedef 12 MB; optional media 150 MB; cache fixture 250 MB; ilgisiz catalog 2 GB indirilmez |
| Network | Wi-Fi 50 Mbps; cellular 10 Mbps; constrained 1 Mbps / 300 ms / %5 loss; 72 saat offline |
| Consent | Cellular'da 25 MB üstü transfer explicit user choice olmadan başlayamaz |
| Local data | 3/10 motorcycles; 250/2,000 history; 50/500 photo; 100/1,000 notes; 20/200 pending; 3/30 conflict |
| Failure | interruption, process kill/restart, background/lock/call/Doze/force-quit, clock/restore, key loss, migration, correction/withdrawal/recall, billing/provider outage |
| Test IDs | EQ-01..EQ-18 ve MPR-01..MPR-18; TASK-SIM-OFFSYNC-001'in E0..E8 olay dizisi |

Bu sayılar production quota, SLA veya bill estimate değildir. Aday “selective sync” veya “local transaction” diyerek fixture'ı küçültemez.

### 3.3 Candidate boundary normalization

| Yüzey | A — Drift/custom | B — PowerSync |
|---|---|---|
| Local DB | App-owned SQLite/Drift typed/generated schema, transactions, migrations | PowerSync local SQLite/synced tables + app-owned metadata/tables |
| Download | Kavriva package/delta protocol, staging/promote, full reissue | Sync Streams partial projection, üstünde Kavriva package manifest/staging/promote |
| Offline write | Kavriva durable operation/outbox ve API | PowerSync local write + ps_crud/upload queue, hedef upload Kavriva API |
| Conflict | Custom API operation ledger/policy | PowerSync transport conflict-unopinionated; domain policy yine Kavriva API |
| Recall/delete | Custom floor/tombstone/revalidation | Stream/RLS delivery yalnız transport; independent Kavriva floor/tombstone zorunlu |
| Encryption/background | Seçilecek native/SQLite/key path; platform evidence A'nın sorumluluğu | SQLite3MultipleCiphers/SQLCipher seçenekleri ve platform/key evidence B'nin sorumluluğu |
| Provider surface | Daha az sync vendor, fakat daha çok Kavriva custom semantics | Daha az transport kodu, fakat PowerSync service/stream/queue/billing/config surface'i |
| High-consequence authority | Kavriva API zorunlu | Kavriva API zorunlu; direct Supabase/PowerSync write REJECT-IF-UNMITIGATED |

PowerSync'in queue/checkpoint primitive'leri A'nın custom semantic burden'ını azaltabilir; ancak B'nin API, package closure, recall floor, RLS equivalence, outage, billing, licensing ve exit burden'ını ortadan kaldırmaz. Drift'in transaction primitive'i de A'nın custom sync authority'sini veya encryption/key/background proof'unu sağlamaz.

## 4. Critical findings

| ID | Candidate | Finding | Neden critical | Gerekli düzeltme / kapanış kanıtı | Şimdiki disposition |
|---|---|---|---|---|---|
| C-01 | A+B | No-owner-debug şartı henüz işletilebilir değil. A custom protocol/API/migration/key/native stack; B ayrıca stream/queue/RLS/service/billing/Cloud veya Mongo/self-host stack taşır. | Arıza anında tek teknik olmayan owner'ın SQL, SSH, queue cursor, provider console veya native build onarması güvenli operasyon modeli değildir. | Plain-language state + bounded runbook + external operator/reviewer ownership; owner yalnız continue/hold/reject seçmeli; outage/restore/exit drill owner debug gerektirmemeli. | HELD |
| C-02 | A+B | TRY 2.000–3.000/ay ceiling ile exact total cost kapanmamış. | A'da sync invoice olmaması custom engineering/incident/backup/key/monitoring/exit maliyetini sıfırlamaz; B'de PowerSync faturası Supabase/API/egress/object/audit/tax/FX'i içermez. | 1k/10k/50k MAU için mandatory/deferrable/optional/scale-triggered BOM; normal, minimum-safe, P2/P3, incident, restore ve exit ayları; hard/soft cap ve owner action. | HELD / UNVERIFIED total |
| C-03 | A+B | High-consequence mutation ve accepted truth API boundary'sinde kalmalı. | Local transaction, queue drain, stream checkpoint veya HTTP 2xx domain acceptance değildir. B direct source write'a kayarsa source RLS/queue semantics ile Kavriva authority karışır. | Submit/status endpoint, stable operation ID, payload digest, expected generation, action-time session/policy, conflict/held/unknown, protected audit; direct provider write negative test. | REJECT-IF-UNMITIGATED |
| C-04 | A+B | Recall, delete ve negative floor hiçbir adayda built-in olarak kapanmıyor. | Missed stream/push, stale cache, restored DB veya late upload recalled/deleted/accepted truth'u yeniden canlandırabilir. | Independent release/suspension/deletion/security/accepted-operation/migration floor; tombstone/revocation generation; foreground/action revalidation; old-client/restore anti-resurrection drill. | HELD; ihlal REJECT |
| C-05 | A+B; B ek yük | Supabase Auth/RLS/Storage güvenlik sınırı provider primitive'iyle otomatik değildir. B'de Sync Stream filter ve RLS equivalence, A'da custom API/RLS/Storage path ayrı kanıtlanmalı. | TO authenticated, JWT varlığı, stream row görünmesi veya signed URL sahipliği action authorization/tenant isolation/provenance değildir. service_role sızıntısı catastrophic olur. | Data API explicit grants, RLS SELECT/USING/WITH CHECK, view/function review, session/security epoch, Storage capability, stream-vs-RLS deny matrix; secrets never client/log/AI. | HELD; leakage/mismatch REJECT |
| C-06 | A+B | Cross-plane restore/exit floor yok. | DB/local SQLite/PowerSync bucket backup, Storage objects, audit, Auth/session ve negative floor aynı anda tutarlı değilse restore başarılı görünürken deleted/recalled/accepted state resurrect olabilir. | Cross-plane manifest, quarantine, independent object/audit/floor custody, clean-room import/replay with partial labels, key references and no owner repair. | HELD; failed anti-resurrection REJECT |
| C-07 | A+B | Platform correctness background callback'a bırakılamaz. | Android kill/Doze ve iOS suspend/force-quit/call/low-power, plugin/native ABI ve key invalidation gerçek cihaz kanıtı olmadan durable work/recall/freshness iddiası geçersiz. | Local transaction before callback; foreground/network/action reconciliation; Android API 29/main + oldest/current iOS matrix; no worker-required safety. | HELD; callback-only path REJECT |

## 5. Major findings

| ID | Candidate | Finding | Gerekli correction | Status |
|---|---|---|---|---|
| M-01 | A | Drift proposal custom semantic yüzeyi gizli engineering/maintenance maliyetine dönüşebilir. Drift schema/transaction verir; package closure, exact-base delta, tombstone, operation ledger, conflict, restore, key ve owner runbook vermez. | Manager proposal'daki primary dili yalnız reversible documentary direction olarak tutulmalı; 14 custom task family'si ayrı owner/reviewer/validator ve acceptance fixture ile costedilmeli. | MAJOR / HELD |
| M-02 | B | PowerSync hazır transport'tur, hazır Kavriva safety/authority değildir. Conflict docs backend'i unopinionated bırakır; queue error FIFO'yu bloklayabilir; stream/checkpoint package/recall floor değildir. | Upload yalnız Kavriva API; result mapping, dead-letter/hold, status lookup, exact generation and package manifest; no default LWW. | MAJOR / HELD |
| M-03 | B | B ekstra vendor/failure/billing domain ekler. Cloud outage/deactivation/soft-limit veya self-host Mongo/replicator/LB/backup/observability owner'a görünür dependency olur. | Cloud vs self-host kararını ADR öncesi fiyatlandırma/ops/exit worksheet ile aç; provider outage/read-only/held runbook; no console repair. | MAJOR / HELD |
| M-04 | A+B | Encryption yalnız “SQLite encrypted” seçeneğiyle kapanmıyor. Key provisioning, rotation, rekey, backup exclusion, reinstall/restore, passcode/biometric invalidation ve logs/exports açık. | Mechanism + version/ABI + platform key matrix; KEY_UNAVAILABLE/AUTH_REQUIRED/INVALIDATED/REKEY_REQUIRED/MISSING state; plaintext fallback yok. | MAJOR / HELD |
| M-05 | A+B | Migration/version change semantic safety'yi otomatik sağlamaz. | A'da Drift migration; B'de synced schema “migration yok” olsa bile app-owned tables, package/operation/encryption semantics, source/stream/API additive order ve old-client hold ayrı evidence. | MAJOR / HELD |
| M-06 | A+B | Observability ve incident response owner açısından yeterince görünür değil. | A için package cursor/generation, queue, tombstone, idempotency, API status, key, storage; B ek olarak stream lag/checkpoint/bucket/reprocess/PowerSync health/billing; all states owner-readable and redacted. | MAJOR / HELD |
| M-07 | A+B | AI operability “çok dosyayı taskize etmek” değil, dependency-safe boundary gerektirir. | Versioned contract/manifest/fixture/task graph; implementer-reviewer-validator separation; least-privilege credentials; no service_role, billing, destructive migration or conflict decision. | MAJOR / HELD |
| M-08 | A+B | Data efficiency safety closure ile karıştırılabilir. | 12 MB smallest complete safe package; optional 150 MB separate; >25 MB cellular consent; 2 GB negative scope; retries/reprocessing/egress peak and temporary space measured. | MAJOR / HELD |
| M-09 | A+B | Billing/provider failure positive state'i sessizce sürdüremez. | BILLING_HELD / SERVICE_UNAVAILABLE / UNKNOWN / RECONCILING states; safe local read/recovery only; hard/soft limit semantics and notification path known. | MAJOR / HELD |
| M-10 | A+B | Exit claimed as “SQLite portable” or “client Apache-2.0” cannot close service/data exit. | Export source, stream/config, operation/conflict/tombstone, objects, audit/floor, Auth/JWKS mapping, key references, package generations and clean-room negative behavior. | MAJOR / HELD |
| M-11 | A+B | Supabase changelog drift release-managed coupling yaratıyor. | Changelog watch, pinned compatibility matrix, any-2xx auth handling, explicit API grants, Realtime schema lock awareness, logs endpoint migration and self-host break changes in release gate. | MAJOR / HELD |
| M-12 | A+B | Accessibility ve owner copy safety surface'idir. | Turkish semantic labels/hints/actions for pending/paused/failed/conflict/stale/unknown/blocked/complete; screenshots/color/snackbar are not evidence. | MAJOR / HELD |

## 6. Solo-owner TCO review

### 6.1 Cost model rule

Maliyet “aylık vendor invoice” ile sınırlı değildir. Bu review dört ayrı maliyet sınıfı kullanır:

1. Mandatory runtime: backend, DB/Auth/Storage, API, local package, object, monitoring, audit/floor, backup.
2. Hidden engineering/maintenance: custom protocol, schema/release, native/plugin, test cohort, migration, incident and reviewer time.
3. Scale/incident: MAU, stream/update/retry/egress, optional media, storage, outage replay, restore and security event.
4. Exit: clean-room export/import, object/audit/key transition, provider replacement, historical operation/conflict replay and runbook.

Exact TRY conversion, tax/FX, Supabase plan/usage, API host, object and monitoring price, PowerSync workload, store/device cost and incident labor are UNVERIFIED. Current official PowerSync price snapshot is evidence only:

| PowerSync Cloud signal (2026-09-18 official page) | Review reading |
|---|---|
| Free: $0; 2 GB synced/month; 500 MB hosted; 50 peak clients; 2 instances; 1 source DB connection/instance; inactivity deactivation; soft limits | Hard bill ceiling veya continuity guarantee değildir. Supabase/API/egress/object dahil değildir. |
| Pro: from $49/month; 30 GB synced; 1,000 peak; listed overages for synced/hosted/clients/instances | Workload total, tax/FX, Supabase and incident total UNVERIFIED. |
| Team: from $599/month; version locking, checkpoints, alerts/roles, private endpoints/customer bucket options | Owner ceiling ile görünür gerilim; exact contract/limits/SLA UNVERIFIED. |
| Self-host | Cloud fee yerine Mongo/replicator/API containers/LB/backup/observability/patch/on-call/license/restore maliyeti gelir. |

### 6.2 Candidate A — Drift/custom hidden cost

**Maliyeti azaltabilecek yüzeyler:**

- ayrı sync provider invoice yok varsayımı;
- package scope, cache/optional media ve operation formatı app/API tarafından kontrol edilebilir;
- SQLite logical export ve provider-neutral package/operation manifests tanımlanabilir;
- stream/RLS equivalence gibi ekstra transport coupling yok.

**Gizli veya kaçınılmaz yüzeyler:**

- exact-base delta, package digest/dependency/closure, cursor/tombstone/floor;
- durable operation/outbox, idempotency ledger, unknown/status lookup, high-consequence conflict;
- API auth/session/authorization, audit, object capability, recall/delete/reach-back;
- encryption library/native ABI/key lifecycle/backup exclusion/rekey;
- Drift schema generator, low-space/WAL/transaction/restore/old-client migration;
- Android/iOS lifecycle, background, network, thermal, accessibility and store/toolchain evidence;
- metrics, redaction, incident runbook, backup/restore/exit and independent review.

“No sync fee” yalnız bir satırdır. Bu custom surface bir teknik olmayan owner'ın parasını doğrudan invoice olarak değil, AI task sayısı, review kapasitesi, incident response ve safe maintenance zamanı olarak tüketir. Bu süre ve incident price currently UNVERIFIED.

### 6.3 Candidate B — PowerSync extra vendor cost

**Maliyeti azaltabilecek yüzeyler:**

- selective Sync Streams ve local SQLite/queue/checkpoint transport primitives;
- queue/local write atomicity ve operation ID affordance;
- provider-native partial delivery ile full-library transfer riskini azaltma potansiyeli.

**Eklenen ve gizlenmemesi gereken yüzeyler:**

- PowerSync Cloud plan/overage/peak/hosted/client/instance billing veya self-host infrastructure;
- Supabase source schema, publication/connector, RLS mirror, stream definition, bucket/checkpoint, API upload and auth/JWKS coupling;
- queue blocked/dead-letter/2xx error/status mapping; stream lag/reprocess/TTL/checkpoint dashboards;
- package manifest/digest/recall floor/restore quarantine still custom;
- SQLite app-owned migration/encryption/key/native and Android/iOS evidence still needed;
- service outage/deactivation/region/billing/provider support and version/license change;
- Cloud-to-self-host exit, bucket rebuild, conflict/operation preservation, clean-room import and FSL/source-available terms.

PowerSync Pro/Team resmi list price'ı TRY ceiling'i otomatik olarak aştı veya aşmadı denemez; exact usage and total bill UNVERIFIED. Free “soft limits” hard fail-closed cap değildir. Team $599/month signal'ı küçük owner envelope ile açık risk yaratır; purchase recommendation değildir.

### 6.4 TCO disposition

| TCO sorusu | A | B | Reviewer sonucu |
|---|---|---|---|
| Küçük launch'ta invoice avantajı | Sync fee yok varsayımı; Supabase/API/common ve custom labor durur | Free/Pro seçimi workload, soft limits ve total dependencies'e bağlı | Numeric winner yok |
| 10k/50k MAU ölçeği | Custom API/egress/storage/ops ve sync semantics büyür | Synced bytes, hosted, peak, instances, Supabase/egress ve outage replay büyür | Scale worksheet yok; HELD |
| Incident month | Az vendor, fazla custom diagnosis/implementation | Fazla vendor, daha görünür support/health ama extra outage boundary | No-owner-debug evidence yok |
| Self-host/exit | App protocol daha portable olabilir; API/Supabase/floor/objects yine taşınır | Service/source/license/bucket/Mongo/stream mapping ekstra | Exit drill yok |
| TRY 2k–3k/month | Exact total ve labor bilinmiyor | Exact total, FX/tax/overage ve plan bilinmiyor | UNVERIFIED |

## 7. Security and secret review

### 7.1 Common non-negotiables

- Flutter/browser hiçbir zaman general canonical DB/object authority taşımaz.
- service_role, secret, unrestricted Postgres credential, global Storage key, signing/recovery key ve billing credential client, repository, log, export veya normal AI context'ine giremez.
- Authenticated JWT/TO authenticated tek başına ownership, role, action competence veya separation-of-duties değildir.
- user_metadata user-editable olduğu için authorization source değildir; authoritative relation/app_metadata/server state gerekir.
- Session termination, role revoke veya user deletion mevcut access token'ı otomatik olarak her hassas operation'da etkisiz kılmaz; action-time session/security epoch/session_id check gerekir.
- RLS exposed table'larda explicit policy, UPDATE için SELECT + USING + WITH CHECK, views/functions için security-invoker/exposure/grant review gerektirir.
- Storage upsert permissions, private bucket, signed URL ve DB backup tek başına object capability, recall, deletion veya backup proof değildir.
- Logs/crash analytics/AI task context redacted olmalı; payload, photo, token, key ve provider secret sızmamalı.

### 7.2 A security finding

A'nın daha az sync-vendor taşıması güvenliği otomatik artırmaz. Custom API operation ledger, session/fence/expected-generation, object capability, RLS defense, audit/floor, key lifecycle ve redaction A'nın sorumluluğundadır. Drift/SQLite local encryption path seçilmemiştir; plaintext fallback veya kayıp key sonrası “başarı” gösterimi REJECT-IF-UNMITIGATED'dir. Custom code surface azalmaz; yalnız ownership Kavriva'ya geçer. Bunun iyi tarafı portable boundary kurma potansiyelidir; kötü tarafı tek owner ve AI için bug/monitoring surface'inin genişliğidir.

### 7.3 B security finding

B'de iki ayrı policy yüzeyi vardır: Supabase RLS/Storage ve PowerSync Sync Stream filter/connector. Bunların “aynı” olduğu varsayılamaz. Tenant/user/task/classification, deleted/recalled row, old JWT, revoked session, optional object and app-owned private metadata için deny matrix gerekir. PowerSync service veya upload worker source write credential taşımamalıdır. Upload queue direct PostgREST/DB write yaparsa B'nin yüksek-consequence use'ı reddedilir. Stream row visibility, checkpoint, queue empty, HTTP 2xx veya RLS pass domain acceptance değildir.

## 8. Incident response, monitoring ve owner-readable operation

### 8.1 A

Minimum observable signals: package stage/complete pointer, digest/base/generation gap, tombstone/floor, pending/unknown queue, API status, duplicate/conflict, key state, storage/space, migration quarantine, restore state, object dependency and audit checkpoint. A'da provider console azalır; ancak custom metrics/runbook yoksa owner'a “logları oku ve DB düzelt” denebilir. Bu kabul edilemez.

### 8.2 B

A sinyallerine ek olarak stream subscription/filter hash, source/stream schema version, bucket/checkpoint, lag, reprocess, queue blocked/dead-letter, PowerSync service health/version/plan/quota, Cloud deactivation, Supabase publication/RLS/config, JWKS and API upload status görünür olmalıdır. Bu observability surface bir “hazır service” ile yok olmaz. Cloud support iletişim yolu olsa bile acceptance/recovery proof değildir; self-host'ta on-call burden Kavriva'ya geçer.

### 8.3 Owner contract

Owner'ın göreceği sonuçlar plain-language PENDING, OUTCOME_UNKNOWN, CONFLICT, HELD, RECALL_KNOWN_STOP, SERVICE_UNAVAILABLE, BILLING_HELD, NEEDS_SPACE, KEY_UNAVAILABLE, RESTORE_QUARANTINE ve RECONCILING gibi state'lerdir. Her state için:

1. neyin authority olmadığı;
2. kullanıcıya hangi local read/safe-stop yolunun açık olduğu;
3. hangi role hangi evidence'i üreteceği;
4. owner'ın yalnızca continue/hold/reject/approve-next-evidence kararı

gösterilmelidir. SQL/SSH, PowerSync dashboard'dan cursor ileri alma, queue silme, migration elle tamir etme veya kullanıcıya duplicate submit ettirme runbook değildir.

## 9. AI-operability and task modularity

### 9.1 A'nın task modularity profili

A, semantic ownership'ı kontrol edebildiği için aşağıdaki küçük task pack'lerine bölünebilir: schema/migration; package manifest/stage/promote; exact-base delta; operation envelope/outbox/status; conflict/hold; cache/storage; key/encryption; lifecycle/network/clock; restore/device generation; account-light migration; API/RLS/Storage; recall/delete/floor; Android/iOS/accessibility; exit/cost/runbooks. Bu iyi bir modülerlik fırsatıdır, fakat toplam task graph'ın semantic surface'i geniştir. Her pack'in fixture ID, forbidden scope, state transition, reviewer, rollback and evidence output'u yoksa AI custom davranışı sessizce uydurabilir.

### 9.2 B'nin task modularity profili

B'de stream definitions, source schema, RLS equivalence, auth/JWKS, upload API, queue/status/error, checkpoint/lag/reprocess, package closure, object, floor, encryption, lifecycle, migration, billing/outage, self-host/exit gibi ek dependency nodes vardır. Transport task'ı daha hazır görünür, fakat config drift ve cross-system ordering task'ları artar. AI'ın bir stream filter'ını değiştirip RLS veya package closure'ı güncellememesi B'de güvenlik açığı yaratabilir.

### 9.3 AI gate

Her iki aday için AI:

- yalnız versioned/diffable context packet ve least-privilege test credentials almalı;
- production DB, service_role, raw secret, recovery key, billing/provider account veya high-consequence approval alamamalı;
- task output olarak contract diff, fixture trace, deny matrix, migration plan, cost/exit row ve reviewer handoff üretmeli;
- “green unit test”, queue empty, local row, stream checkpoint veya 2xx'ı accepted/recall/authority saymamalı;
- bilinmeyeni HELD bırakmalı.

Teknik olmayan owner AI çıktısını değerlendirirken provider log/SQL/native build debug'ına yönlendirilemez. Implementer, independent data/safety reviewer, platform reviewer, security/migration reviewer ve evidence validator ayrımı korunmalıdır.

## 10. Eşit 18 EQ senaryosu: owner/TCO/security review

Tüm satırlar TASK-SIM-OFFSYNC-001 fixture'ındaki aynı P0/G0, P1 yaklaşık %50 staged, D1 base G-1, O-77, R-12, C-55, 150 MB media, 25 MB consent ve 250 MB pressure ile okunmuştur. Her satır current no-code disposition olarak HELD'dir; correction sütunu acceptance gate'i belirtir.

| ID | A Drift/custom okuması | B PowerSync okuması | Reviewer gate / disposition |
|---|---|---|---|
| EQ-01 | Scoped package stage/promote; 2 GB catalog seçilmez. | Stream predicate/subscription selected task ile sınırlı; package closure ayrıca kanıtlanır. | Transfer manifest, filter/RLS, peak/data proof; unbounded scope REJECT. HELD |
| EQ-02 | P1 partial/corrupt staging'de; P0 pointer korunur. | Checkpoint/SQLite row partial package authority yapamaz; app staging/digest gerekir. | Kill, digest, closure, atomic promote. HELD |
| EQ-03 | D1 exact G0 mismatch reject; cursor ilerlemez; full reissue. | Stream convergence closest-base merge değildir; API exact validator gerekir. | Base/target/generation/digest test; mixed merge REJECT. HELD |
| EQ-04 | 72h offline bounded closure; stale/high consequence hold. | Cached stream local read sağlar; token/freshness/API revalidation authority'dir. | Exposure window, stale critical hold, no offline authz. HELD |
| EQ-05 | Missed push/Realtime recall'ı kaçırsa da next boundary floor uygular. | Stream tombstone/reprocess gecikebilir; independent floor gerekir. | Recall/delete anti-resurrection and residual race evidence. HELD |
| EQ-06 | Network return API status/idempotent operation drain. | fetchCredentials + PowerSync queue only transport; API status authoritative. | Same ID, late/duplicate response and generation fence. HELD |
| EQ-07 | Freshness expiry active work'te safe-stop/recovery. | TTL/checkpoint product freshness değildir. | Action boundary and user-readable stale state. HELD |
| EQ-08 | Guide correction old continuation'ı kapatır; safe remap reviewed. | New stream generation old row'u authority yapmaz; API/package remap. | Old-client/semantic capability and closure proof. HELD |
| EQ-09 | Clock/restore quarantine; floor revalidation. | Restored local SQLite/checkpoint source authority değildir. | Cross-plane restore and clock evidence. HELD |
| EQ-10 | Unknown safety field capability hold/full reissue. | Schemaless/client schema migration yokluğu semantic compatibility değildir. | Old-client capability matrix; silent field use REJECT. HELD |
| EQ-11 | O-77 same ID/payload status lookup. | Per-client queue ID API accepted-operation ledger değildir. | Lost response, duplicate, changed payload and audit. HELD |
| EQ-12 | High consequence conflict two sides/hold; no default LWW. | PowerSync unopinionated/default LWW cannot be domain policy. | Field taxonomy, reversible resolution, reviewer/audit. HELD |
| EQ-13 | Optional/re-fetchable evict first; pending/closure pinned. | PowerSync cleanup does not prove classification/pinning. | 250 MB/peak/WAL/queue/attachment test. HELD |
| EQ-14 | Device loss separates server accepted/local-only/media lost. | Replacement reauth/stream only recovers server state; local-only truth is lost/held. | Device/key/object recovery and truthful UI. HELD |
| EQ-15 | Scope preview/stable migration/private-shared/conflict. | Subscription/user filter switch is not migration acceptance. | Wrong-account/clone/idempotent migration. HELD |
| EQ-16 | API/provider/billing held; local safe read not positive mutation. | PowerSync outage/deactivation/soft limit plus Supabase/API outage separate. | Owner-readable outage and no console/SQL repair. HELD |
| EQ-17 | Publish checks current suspension generation; newer negative wins. | Stream/checkpoint cannot fence publication. | Independent floor/audit race test. HELD |
| EQ-18 | Export DB/objects/audit/floor/ops manifests; clean-room no resurrection. | Add stream/bucket/checkpoint/source/license/Mongo mapping. | Cross-plane exit drill; backup success alone REJECT. HELD |

## 11. Eşit 18 MPR senaryosu: platform/TCO/security review

| ID | A Drift/custom | B PowerSync | Reviewer gate / disposition |
|---|---|---|---|
| MPR-01 | Durable package/ops/history ayrı; re-fetchable cache temizlenebilir. | Synced SQLite projection purgeable olabilir; app-owned durable lane ayrılmalı. | Storage class, purge and restart evidence; safety data purge REJECT. HELD |
| MPR-02 | Stage/digest before promote; old complete generation survives kill. | Checkpoint cross-row closure/digest değildir; app promote contract gerekir. | 12 MB interruption/peak test. HELD |
| MPR-03 | Drift local transaction history/outbox metadata atomic; orphan quarantine. | Data+ps_crud atomic primitive var; app metadata/object dependency transaction eklenir. | Power-loss/duplicate/orphan evidence. HELD |
| MPR-04 | Callback correctness değildir; commit before lifecycle callback. | Queue callback/SDK event correctness değildir. | Android kill/iOS force-quit real device; callback-only REJECT. HELD |
| MPR-05 | Backup/restore quarantine; floor/identity/package revalidate. | Local DB/bucket/checkpoint restore floor değildir. | Stale restore anti-resurrection. HELD |
| MPR-06 | Reinstall/re-auth/device generation; local-only loss truthful. | Reinstall stream resubscribe, Auth/device binding and local queue semantics open. | Account continuity/keychain/restore. HELD |
| MPR-07 | External encryption choice/key state open. | SQLCipher/SQLite3MultipleCiphers option; key custody still app responsibility. | Key invalidation/rekey/no plaintext. HELD |
| MPR-08 | Drift schema migration stepwise/idempotent/quarantine. | Synced protocol migration azalabilir; app-owned schema/source/stream/API order remains. | Low-space/old/new/future schema. HELD |
| MPR-09 | Background opportunistic; foreground reconciliation. | Android WorkManager support does not make iOS/background correctness. | Doze/force-quit/partial fetch no safety dependency. HELD |
| MPR-10 | Core independent, optional 150 MB media pause/cancel. | Stream catch-up/media worker must not starve core or retry storm. | Thermal/battery scheduling and user state. HELD |
| MPR-11 | Stable op ID/idempotency/status over loss. | FIFO queue + API ID; blocked/dead-letter semantics open. | 1 Mbps/300 ms/%5 loss, lost response and duplicate. HELD |
| MPR-12 | Explicit >25 MB cellular consent. | Selective sync does not supply consent UI or object data budget. | Metered/Low Data Mode/2 GB negative scope. HELD |
| MPR-13 | Peak old+new+verify space; optional evicts first. | WAL/compaction/PowerSync DB/temp peak unknown. | Android 2 GB free and iOS storage evidence. HELD |
| MPR-14 | Server generation/time; wall clock no authority. | Checkpoint ordering plus API server time; product expiry separate. | Clock rollback/restore/freshness. HELD |
| MPR-15 | Turkish states in Flutter accessibility. | SDK callback/state has no product TalkBack/VoiceOver proof. | AT semantic labels/actions, no color-only. HELD |
| MPR-16 | Drift/native encryption/channel and iOS parity open. | PowerSync generated/native/Gradle/CocoaPods/SwiftPM/ABI/version coupling added. | Android-first plus iOS later evidence. HELD |
| MPR-17 | Core without media; object/cache separate; 2 GB never selected. | Stream rows and Storage bytes separate; signed URL/backup/classification open. | Peak/cache/object recovery. HELD |
| MPR-18 | Mixed package/client/release/floor quarantined. | Stream version/reprocess/service release plus API floor must align. | Old-client/recall/rollback anti-resurrection. HELD |

Bu 36 satırda hiçbir candidate “provider bunu halleder” diyerek evidence alanı çıkaramaz. Eksik alanın owner action'ı “owner debug” değil, belirli role ve cohort'a atanmış evidence packet'tir.

## 12. Manager Proposal'daki Drift yönüne bağımsız düzeltme

Manager proposal Drift/custom'ı reversible primary working direction, PowerSync'i challenger olarak çerçeveliyor. Bu yön mantıksal olarak kontrol/exit avantajı taşıyabilir; fakat Reviewer B şu düzeltmeleri gerekli görür:

1. Drift yalnız local DB primitive'idir; proposal metninde custom package/delta/outbox/recall/floor semantics'i “küçük bounded package” denilerek düşük maliyetli varsayılmamalı.
2. No sync provider fee satırı custom engineering, security review, native encryption, incident, restore and exit labor'ını TCO'dan silemez.
3. Encryption mechanism, key custody, backup exclusion, rekey and platform ABI seçilmeden local DB güvenliği kapanmış sayılmamalı.
4. Custom protocol state machine, API status lookup, idempotency ledger, conflict policy, tombstone/floor and old-client compatibility ayrı versioned contracts olmalı.
5. A'nın önerilen primary yönü ancak AI task pack'leri gerçekten small/reviewable, external operator-runbook ile no-owner-debug ve total TCO ceiling evidence'i kapattığında sürdürülebilir aday sayılmalı.
6. Drift transaction'ı network/server/object/audit transaction'ına genişletilmemeli; PARTIAL, UNKNOWN, RECONCILING, HELD görünür kalmalı.
7. Manager proposal'daki reversal trigger'ları “PowerSync'e otomatik geç” şeklinde okunmamalı; B aynı 36 scenario, cost, security, restore/exit ve owner gate'inden geçmeli.

**Düzeltilmiş A yorumu:** Drift/custom, provider coupling'i azaltan ve logical export üzerinde kontrol sağlayabilecek bir finalisttir; bunu low-ops veya low-TCO kanıtı yapan hiçbir current evidence yoktur.

## 13. PowerSync'i hazır hizmet diye otomatik seçmeme gerekçesi

PowerSync için resmi evidence güçlü bir transport surface gösterir: Flutter/SQLite local store, reactive watch, atomic local write + upload queue, Sync Streams partial data, auth connector, checkpoint/causal consistency ve encryption options. Bu evidence şunları göstermez:

- package'ın safety-complete/atomic/anti-rollback olduğu;
- high-consequence API authority, idempotency/status, conflict hold veya protected audit;
- stream/RLS filter equivalence ve deletion/recall/negative floor;
- queue poison/dead-letter/2xx mapping'in owner-safe olduğu;
- iOS background/force-quit, encryption key, schema migration or accessibility;
- PowerSync Cloud outage/deactivation/billing, Supabase outage, self-host Mongo/replicator/backup;
- FSL/source-available service exit, bucket/checkpoint export, clean-room behavior veya TRY total.

B'nin direct-write, silent LWW, stream-only recall, queue-empty-as-accepted, secret-in-client, owner console repair veya unbounded billing yolu görülürse ilgili use REJECT-IF-UNMITIGATED'dır. B transport burden'ı azaltabilir, fakat operational coupling'i çoğaltabilir.

## 14. Required corrections before any candidate promotion

### 14.1 Common

1. Candidate-neutral package/operation/recall/restore state contract and all 36 scenario rows.
2. Real Android constrained/main and iOS oldest/current evidence matrix: process kill, Doze/force-quit, storage, network, clock, restore, key, migration and accessibility.
3. API authority contract: action-time auth/session, stable ID, payload digest, expected generation, status lookup, conflict/held/unknown, audit/floor.
4. Supabase security inventory: explicit Data API grants, RLS SELECT/USING/WITH CHECK, views/functions, Storage capabilities, Auth session/security epoch, no secret exposure.
5. Independent object/audit/negative floor custody, restore/quarantine, clean-room export/import and no resurrection.
6. Equal BOM with 1k/10k/50k MAU, retries/reprocess, optional media, egress, tax/FX, incident, restore, exit, self-host and operator/reviewer labor. Unknown rows stay UNVERIFIED.
7. Owner-readable outage, billing, key, migration, conflict and unknown runbooks with no SQL/SSH/provider-console repair.
8. AI task packs with input/output/forbidden scope, fixture/reviewer/validator, rollback, changelog watch and least-privilege credential map.

### 14.2 A-specific

- Custom protocol minimum spec and deterministic negative tests for partial, wrong-base, out-of-order, late, recall, delete, duplicate, conflict, restore and exit.
- Drift schema/migration/transaction/WAL/low-space/old-client and encryption/key evidence.
- Exact cost of custom implementation, review, incident, platform maintenance and exit.
- Native/plugin reversal trigger and iOS parity plan.

### 14.3 B-specific

- Stream/RLS equivalence matrix and deny tests by tenant/user/task/role/classification.
- Upload path proof: PowerSync queue never direct-writes high-consequence source; Kavriva API validates and records result.
- Queue blocked/dead-letter/unknown/2xx mapping, checkpoint-to-package-generation fence and reprocess/TTL behavior.
- PowerSync Cloud Pro/Team/Free and self-host total BOM, soft-limit/outage/deactivation behavior, license/contract and clean-room exit.
- Service version locking/config migration, Supabase source/stream/API additive order, bucket/objects/audit/floor backup.

## 15. Conditional recommendation (winner değil)

Bu reviewer'ın conditional recommendation'ı bir technology winner değil, evidence gate'idir:

- **A yalnız şu koşullarda devam adayı olarak tutulabilir:** custom package/delta/outbox/recall/floor API contract'i bounded and diffable task'lara bölünür; 36 scenario'da no-owner-debug, encryption/key, restore/exit, platform/accessibility ve TCO evidence'i kapanır; total safe recurring + maintenance + incident envelope TRY ceiling ile owner tarafından kabul edilir.
- **B yalnız şu koşullarda devam adayı olarak tutulabilir:** stream/RLS equivalence, API-only high-consequence upload, queue/dead-letter/unknown, independent recall/delete floor, real Android/iOS/key/restore evidence, Cloud/self-host/license/billing/exit and total cost evidence kapanır; provider outage owner debug gerektirmez.
- **A veya B aşağıdaki durumda seçilmemeli:** exact total cost UNVERIFIED kalıyor, owner'a native/SQL/provider-console repair veriliyor, restored/late/stream state negative floor'ı düşürebiliyor, direct write veya silent LWW bulunuyor, optional media/package data consent ve storage contract'ını ihlal ediyor.

Staging kararı: A ve B eşit Phase-4 documentary finalists olarak HELD kalsın; önce common evidence packet ve bağımsız reviewer gates kapatılsın. Manager proposal'daki Drift yönü “directional candidate”, PowerSync ise “automatic fallback” değildir. Bir sonraki karar yalnız current evidence ile, aynı fixture ve açık owner capacity/budget ile verilebilir.

## 16. Final disposition

HELD — NO WINNER — 0 PASS / 36 HELD / 0 REJECT (no-code documentary review).

Bu disposition:

- kod, prototype, provider hesabı, plan/subscription, purchase veya Phase-5 ADR yetkisi vermez;
- PowerSync pricing headline'ını TRY total veya hard cap saymaz;
- Drift transaction'ını global transaction, encryption, recall veya canonical authority saymaz;
- Supabase RLS/Storage/Realtime/backup'ını Kavriva authority, negative floor veya clean-room exit proof'u saymaz;
- bilinmeyenleri olumlu authority'ye çevirmez;
- owner'ı implementer, debugger, SQL/SSH operator, provider-console operator veya conflict arbitrator yapmaz.

Bir mandatory reject koşulu gözlenirse puanla telafi edilmez; ilgili kullanım reddedilir ve diğer finalist otomatik kazanan olmaz.

## 17. Primary sources / evidence links

Repository documents:

- 04_TECH_STRATEGY/DEBATES/DEBATE-009__OFFLINE_SYNC_REQUIREMENTS_SYNTHESIS.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__OFFLINE_SYNC_OPTIONS_PRIMARY_RESEARCH.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__MOBILE_PLATFORM_FAILURE_RESEARCH.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__MANAGER_PROPOSAL.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__FINALIST_A_DRIFT_CUSTOM.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__FINALIST_B_POWERSYNC.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-009__TASK_SIM_OFFSYNC_001.md
- 00_CONTROL/DECISION_LOG.md — DEC-0033/0034/0035

Supabase / security:

- Supabase skill: C:/Users/Xpike/.codex/skills/supabase/SKILL.md
- [Supabase changelog](https://supabase.com/changelog.md)
- [Tables not automatically exposed](https://supabase.com/changelog/45329-breaking-change-tables-not-exposed-to-data-and-graphql-api-automatically)
- [Realtime schema lock](https://supabase.com/changelog/realtime-schema-locked-down-against-modification)
- [OpenAPI anon-key removal](https://supabase.com/changelog/42949-breaking-change-removing-access-to-openapi-spec-via-the-anon-key)
- [PostgREST retries](https://supabase.com/changelog/45071-automatic-postgrest-retries-for-transient-errors)
- [Supabase sessions](https://supabase.com/docs/guides/auth/sessions)
- [RLS](https://supabase.com/docs/guides/database/postgres/row-level-security)
- [Storage access control](https://supabase.com/docs/guides/storage/security/access-control)
- [Database backups](https://supabase.com/docs/guides/platform/backups)

PowerSync / local / platform:

- [PowerSync Flutter package](https://pub.dev/packages/powersync)
- [PowerSync Flutter SDK](https://docs.powersync.com/client-sdks/reference/flutter)
- [Sync Streams](https://docs.powersync.com/sync/streams/overview)
- [PowerSync client integration](https://docs.powersync.com/configuration/app-backend/client-side-integration)
- [Writing client changes](https://docs.powersync.com/handling-writes/writing-client-changes)
- [Handling update conflicts](https://docs.powersync.com/handling-writes/handling-update-conflicts)
- [PowerSync consistency](https://docs.powersync.com/architecture/consistency)
- [PowerSync RLS and Sync Streams](https://docs.powersync.com/integrations/supabase/rls-and-sync-streams)
- [Schema changes](https://docs.powersync.com/maintenance-ops/deploying-schema-changes)
- [Data encryption](https://docs.powersync.com/client-sdks/advanced/data-encryption)
- [Background syncing](https://docs.powersync.com/client-sdks/advanced/background-syncing)
- [Pricing](https://powersync.com/pricing)
- [Self-hosting](https://docs.powersync.com/maintenance-ops/self-hosting/overview)
- [Licensing terms](https://powersync.com/legal/licensing-terms)
- [Drift](https://drift.simonbinder.eu/)
- [SQLite WAL](https://www.sqlite.org/wal.html)

Platform:

- [Android process lifecycle](https://developer.android.com/guide/components/activities/process-lifecycle)
- [Android Auto Backup](https://developer.android.com/identity/data/autobackup)
- [Android Doze](https://developer.android.com/training/monitoring-device-state/doze-standby)
- [Apple files and directories](https://developer.apple.com/documentation/technologyoverviews/files-and-directories)
- [Apple background execution](https://developer.apple.com/documentation/uikit/extending-your-app-s-background-execution-time)
- [Apple Keychain accessibility](https://developer.apple.com/documentation/security/restricting-keychain-item-accessibility)
- [Flutter AppLifecycleState](https://api.flutter.dev/flutter/dart-ui/AppLifecycleState.html)

Bu kaynaklar capability ve limitation evidence'idir. Safety, exact cost, restore, owner-operability, accessibility, total bill ve clean-room exit source'ta açıkça kapanmadığında sonuç UNVERIFIED/HELD olarak bırakılmıştır.
