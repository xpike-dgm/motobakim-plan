# DEBATE-011 — API çalışma zamanı birincil kaynak araştırması

Status: PHASE-4 RESEARCH / NO-CODE / NO ACCOUNT / NO PURCHASE / NO WINNER / ADR PENDING  
Date: 2026-09-19  
Research cut: 2026-09-19, Europe/Istanbul  
Scope: Kavriva consumer Flutter + browser Internal Operations + Supabase-centered data direction + replaceable API runtime

Bu kayıt yalnızca resmi/birincil sağlayıcı belgelerine dayanır. Aşağıdaki fiyat, kota ve limitler bu araştırma
kesitinin fotoğrafıdır; ADR veya satın alma kararı değildir.

Evidence etiketleri:

- [CONFIRMED] Sağlayıcının resmi belgesinde açıkça görülen davranış, kota veya fiyat.
- [INFERRED] Resmi kanıtlardan çıkarım; Kavriva için sağlayıcı garantisi değildir.
- [OPEN] Bu araştırmada üretim kararı için yeterli resmi kanıt yok.
- [HELD] Kanıt kapanana kadar yüksek sonuçlu capability açılmaz.

## 1. Karar sorusu ve bağlayıcı sınır

Soru, hangi sağlayıcının daha popüler olduğu değildir:

> Kavriva'nın server/API authority boundary'sini; commit-time authorization, idempotent transaction,
> protected audit, OUTCOME_UNKNOWN, object/queue/recovery semantiği, düşük operasyon yükü ve clean-room exit
> kanıtıyla hangi çalışma zamanı taşıyabilir?

Bu belge runtime, dil, framework, cloud, region, plan, account veya satın alma seçmez; kod/prototype/load test
yapmaz. Mantıksal API sınırı fiziksel olarak tek servis veya birden çok servis olabilir, fakat Flutter/browser,
provider console, generic Data API veya Storage authority bypass'ı kabul edilmez.

Her adayda ortak zorunluluk:

1. JWT/JWKS: exact issuer, audience, algorithm, kid, signature, expiry/clock, rotation, session/security epoch.
2. Authorization: actor, issuer/session assurance, role/grant, competence, independence, scope, resource/version.
3. Secrets: service_role/DB owner/root yalnız server-side custody; client/repo/log/AI context dışında.
4. Mutation: operation ID, payload fingerprint, idempotency, expected version/generation, status lookup.
5. Transaction: canonical state + operation ledger + protected audit; dış etki outbox/worker üzerinden.
6. Timeout: sonucu bilinmeyen işlemde OUTCOME_UNKNOWN; kör retry yok.
7. Background: durable queue, retry, DLQ veya kanıtlı eşdeğer; duplicate delivery güvenli.
8. Observability: structured logs, metrics, traces, correlation, retention/export; platform log'u product audit değil.
9. Deployment: immutable artifact/revision, health gate, gradual deploy, rollback; state/schema rollback ayrı.
10. Cost/exit: egress, quota, spend stop, normal/incident/restore/exit ayları, veri ve state export.

## 2. Yöntem ve Supabase changelog bulgusu

Supabase kapsamı nedeniyle önce C:/Users/Xpike/.codex/skills/supabase/SKILL.md eksiksiz okundu. Resmi Supabase
changelog araştırma başlangıcı olarak tarandı. 2026-09-19 kesitinde runtime kararını etkileyen noktalar:

| Tarih | Resmi değişiklik | Etki |
|---|---|---|
| 2026-07-23 | Management API logs.all kaldırma takvimi; ClickHouse logs endpoint'ine geçiş | AI/log automation endpoint'e kalıcı varsayım yapmamalı |
| 2026-03-11 | Nested/recursive Edge Function calls için yaklaşık 5.000 request/min chain limiti | Fan-out ve LLM tool loop ayrıca test edilmeli |
| 2026-03-05 | Edge Functions dashboard/log-drain iyileştirmeleri | Platform log'u protected product audit değildir |
| 2026-02-17 | OpenAPI anon-key erişiminin kaldırılma takvimi | Anon/publishable ile service/secret key ayrımı zorunlu |
| 2026-04-28 | Yeni tabloların Data/GraphQL API'ye otomatik açılmaması | Generic API exposure authority boundary olamaz |

Changelog sürekli değiştiği için bu kayıt bir change-watch ihtiyacını da kanıtlar. [S1]

## 3. Eşit aday özeti

| Aday | Çalıştırma | Postgres/private networking | Background | Operasyon/rollback | Disposition |
|---|---|---|---|---|---|
| A Supabase Edge/Deno | Global gateway, Deno isolate, TypeScript/WASM | Supabase pooler/direct; Team/Enterprise DB PrivateLink var, hosted Edge'in müşteri VPC'sinde olduğu UNKNOWN | Kısa/idempotent HTTP önerilir; ağır iş için worker/external service | CLI/local stack/logs; immutable traffic rollback UNKNOWN | Koşullu low-ops aday, HELD |
| B Render container | Managed web service/background worker, Docker/Git | Aynı region Render private network; Supabase DB'ye private path UNKNOWN | Worker, Key Value, Cron, Workflows | Health/zero-downtime/artifact rollback | Kalıcı runtime alternatifi, HELD |
| C Cloudflare Workers | Edge isolate, Smart Placement, Hyperdrive | Resmi Supabase Hyperdrive örneği; transaction/session ve private path sınırlı | Queues/Workflows, süre/retention limitli | Versions/gradual/rollback; binding state rollback dışı | Edge/latency alternatifi, HELD |
| D Cloud Run | Regional autoscaled container + Jobs | Google VPC egress; Supabase AWS PrivateLink otomatik değil | Jobs/Cloud Tasks/Pub/Sub | Immutable revision/traffic rollback | Container/queue alternatifi, HELD |
| E Vercel | Managed Function/Fluid Compute | DB/private path ayrıca çözülür | Workflow/Queues plan-bağımlı | Referans ergonomi | Bu debate finalist değil |

Sonuç 0 PASS / 4 primary candidate HELD / 1 reference only'dir.

## 4. Aday A — Supabase Edge Functions / Deno

### Kanıt

Supabase Edge Functions TypeScript-first, Deno-compatible, WASM destekli server-side functions'tır. Gateway
routing ve JWT header validation yapar; docs authenticated/public HTTP endpoints, webhook, küçük AI/LLM
orchestration, email ve bot örnekleri verir. Global/nearest-edge dağıtım gecikmeyi azaltır. [S2][S4]

Docs cold start olabileceğini, kısa ömürlü/idempotent tasarım gerektiğini ve heavy/long-running işi background
worker veya external service'e ayırmayı söyler. Bu kesin uygun/uygunsuz hükmü değil, workload sınırına dair resmi
rehberliktir. [S2][S16]

### DB, auth ve secret

- withSupabase auth=user user JWT + RLS scoped client; supabaseAdmin service role ile RLS bypass eder. Admin
  client yalnız server secret custody'de kalır. [S6][S7]
- Serverless/edge için Supavisor transaction pooler önerilir. Transaction mode session state, advisory lock,
  LISTEN/NOTIFY, temp tables ve prepared statements varsayımlarını sınırlar; kısa transaction ve prepared=false
  gerektirebilir. Direct connection migration/pg_dump/persistent backend için ayrıdır. [S7][S8]
- Gateway verify_jwt varsayılan user JWT doğrulamasıdır. apikey publishable/secret key JWT değildir; webhook veya
  secret-to-secret akışta verification kapatılabilir, ancak handler secret ve business authorization yapmalıdır.
  [S5][S6]
- Kavriva gateway sonrasında issuer/audience/alg/kid/JWKS rotation, current session/epoch, grant/role/scope/
  competence/version kontrolü yapmalıdır. [INFERRED]

### Limit, region ve work

Resmi Edge Function limit kesiti:

| Limit | Değer | Kavriva riski |
|---|---:|---|
| Memory | 256 MB | Büyük media/model runtime'a gömülmemeli |
| Wall-clock | Free 150 s; paid 400 s | Timeout sonucu UNKNOWN olabilir |
| CPU | 2 s/request | CPU-heavy iş worker/external service ister |
| Idle timeout | 150 s | 504 ve lost outcome |
| Bundle | 20 MB CLI local; 5 MB server API/dashboard | Dependency bütçesi gerekir |
| Secrets | 100/project; 48 KiB/secret | Rotation ve secret parçalama gerekir |
| Logs | 10.000 karakter/event; 100 event/10 s | Log product audit değildir |
| Nested chain | yaklaşık 5.000 request/min | Fan-out ve recursive orchestration sınırlı |

Hosted Edge runtime'ın Supabase PrivateLink müşteri VPC'sinde çalıştığı resmi olarak gösterilmedi. PrivateLink
Team/Enterprise'ta AWS VPC-Supabase DB bağlantısı içindir; Edge→PrivateLink placement UNKNOWN'dur. [S3][S9][S16]

### Queue, gözlemlenebilirlik, deployment

Edge HTTP handler bounded command/outbox enqueue için kullanılabilir; operation ledger, idempotency, expected
version, transaction ve status resolver uygulamanındır. Docs'un external worker önerisi durable queue, long AI/
media/ETL, retry/DLQ ve side-effect outbox'ının ayrıca çözülmesini gerektirir. [S2][S3]

Dashboard invocation logs request/response/status/duration, platform ve custom logs sağlar; retention/export ve
protected audit ayrıca kanıtlanmalıdır. CLI/local Supabase stack, hot reload, Deno LSP/test/format parity sağlar.
[S10][S11]

Deploy vardır; reviewed official set Edge için immutable revision, percentage rollout veya previous artifact
rollback sözleşmesini Cloud Run/Workers kadar net göstermedi. [OPEN] [S17]

Paid custom domain + managed SSL API/Functions için belgelenmiştir. Gateway JWT rate limiting veya global abuse
counter değildir; application/IP/user/operation limitleri ayrıca gerekir. DDoS kapsamı bu kaynak setinde açık
bir product contract olarak kapanmadı. [S12] [OPEN]

### Maliyet, exit, fit

Free yaklaşık 500k Edge invocation; Pro 2m dahil, sonrası yaklaşık 2 USD/million. Egress Free 5 GB/Pro 250 GB
dahil, sonrası yaklaşık 0.09 USD/GB. Invocation response status'tan bağımsız sayılabilir. Pro Spend Cap bazı
invocation/egress/log/storage kalemlerini durdurabilir; compute, custom domain, IPv4 ve bazı IOPS/log-drain
kalemleri kapsanmayabilir. Bu tüm faturaya hard cap değildir. [S13][S14][S15]

Deno/source portability olumlu bir exit kanıtıdır; Auth/DB/Storage/gateway/secrets/logs/domain/queue/backup state
exportu ayrıca gerekir. [INFERRED]

**Koşullu kullanım:** kısa idempotent command, webhook+enqueue, RLS-scoped read, Auth/session adapter, küçük
external LLM orchestration.  
**HELD kullanım:** high CPU/long job, durable worker-only design, customer-VPC DB, global abuse counter,
protected audit sink, immutable rollout/rollback veya provider outage sırasında positive authority.

## 5. Aday B — Render managed web service/container

Render Web Service Git/Docker source, region, env/secrets, health check, public/private service, custom domain,
managed TLS, WebSocket, zero-downtime deploy, scaling ve persistent disk seçenekleri sunar. Aynı workspace/region
servisleri internal hostname ile private network'te haberleşir; farklı region ayrı network'tür. [S20][S21][S37]

Render Private Link Pro+ ile AWS-hosted provider/VPC'ye one-way private path sunar; private DNS yoktur ve endpoint/
region uyumu gerekir. Supabase PrivateLink ile otomatik uyum doğrulanmadı. Bu yüzden Supabase DB dışarıda kalırsa
Render private network iddiası DB'yi private yapmaz; public TLS veya uyumlu ayrı network yolu gerekir. [S22][OPEN]

Render secrets env/group/secret file olarak tutulabilir. Supabase JWT/JWKS, epoch, domain authorization ve
service_role misuse otomatik çözülmez; uygulama doğrulaması ve log/crash redaction gerekir. [S32]

Free instance 512 MB ve workspace başına 750 free instance-hour; free web service spin down/suspend olabilir,
production için önerilmez. Paid container uzun HTTP/WebSocket/persistent worker için daha esnek; Render comparison
web response için 100 dakikaya kadar ifade verir. Build 120 dakika, predeploy 30 dakika, start 15 dakika; failed
deploy eski instance'ı korur, SIGTERM default shutdown 30 saniyedir. [S19][S24][S38]

Background Worker sürekli çalışabilir; Key Value veya external queue poll eder. Cron UTC, tek aktif run, 12 saat
stop; Workflows retry/rapid spin-up sunar. Workflows limit kesitinde root 50/min Hobby, 1.500/min Pro+, chained
1.000/min, default timeout 2 saat/max 24 saat, max 500 task ve 4 MB args vardır. [S29][S30][S31]

Logs retention Hobby 7 gün/Pro 14 gün/Scale 30 gün; Pro+ request logs ve OTel metrics stream vardır. Rollback
previous successful build/artifact'a döner; DB schema, queue, object veya dış side effect rollback olmaz. Docker
tag yerine immutable digest gerekir. [S25][S26][S27][S28]

Render Cloudflare edge ile L3/L4 ve heuristic L7 DDoS azaltımı açıklar; credential stuffing/API abuse/slow-read
application responsibility'dir. Multi-instance rate limit için dağıtık Key Value gerekir. [S34]

2026-09-19 fiyat kesiti: Hobby 0 USD + compute, Pro 25 USD + compute; örnek 512 MB paid 7 USD/ay, 1 CPU/2 GB
25 USD/ay; outbound Hobby 5 GB/Pro 25 GB/Scale 1 TB dahil, sonrası yaklaşık 0.15 USD/GB; Private Link yaklaşık
30 USD/ay ve 0.03 USD/GB. Render genel tüm hizmetleri kapsayan hard spend cap bu araştırmada doğrulanmadı. [S18][S23][OPEN]

**Rol:** persistent runtime, custom library, worker/queue ve container debug için güçlü alternatif; Supabase
private DB uyumu, owner operasyon yükü, cost-stop ve exit state'i kapanana kadar HELD.

## 6. Aday C — Cloudflare Workers + Hyperdrive

Workers resmi limit kesiti: Free 100.000 request/day; Paid request limit yok; CPU Free 10 ms/Paid max 5 min
(default 30 s); memory 128 MB; subrequests 50/10.000; six simultaneous outgoing; startup 1 s; Worker 64 MiB;
waitUntil 30 s; Queue/Cron consumer 15 dakika. HTTP client bağlı kaldığında sabit request süresi olmayabilir, fakat
client sonrası waitUntil durable queue değildir. [S39]

Varsayılan placement kullanıcıya yakın data center; Smart Placement backend'e yakınlık seçebilir. Regional
Services execution/TLS'ı sınırlandırsa da code/secrets global deploy edilir ve Queue/Cron/outbound otomatik
regionalized değildir. [S41][S42]

Hyperdrive resmi Supabase Postgres direct connection örneği ve global pooling sağlar. Transaction pooling session
state/advisory lock/LISTEN/NOTIFY sınırları getirir; uzun transaction pool exhaustion yaratır. Limit kesitinde
initial timeout 15 s, idle 10 dakika, query 60 s, response cache 50 MB; config başına yaklaşık 20 Free/100 Paid
origin connection vardır. Auth/session/permission/read-after-write için cache kapatılmalıdır. [S45][S46][S47]

Free yaklaşık 100k Hyperdrive query/day; Paid unlimited ve Workers Paid'e dahil; Workers egress ücretsiz ifadesi
Supabase/external provider egressini kaldırmaz. Private DB için Tunnel/Access veya VPC yolu ayrıdır; Supabase
PrivateLink otomatik değildir. [S48][OPEN]

Cloudflare arbitrary Supabase JWT'yi otomatik authorize etmez. Access resmi örneği Worker'ın JWT signature,
issuer ve audience'ı JWKS ile kod içinde doğrulamasını ister; aynı desen Supabase adapter'ına uygulanmalıdır.
Encrypted secret, local .dev.vars/.env, binding capability vardır; external service_role yine secret'tır. [S43][S44][S61]

Queues: message 128 KB, batch 100/256 KB, retry 100, default retry 3, retention Free 24 saat/Paid 14 gün,
backlog 25 GB, consumers 250, consumer 15 dakika, delay 24 saat, throughput 5.000 msg/s/queue. Ack/DLQ ve
duplicate-safe handler ayrıca gerekir. [S49][S50]

Workers logs/Tail/Logpush/OTel traces ve metrics sunar. Her code/config change version; percentage gradual
deployment ve rollback vardır, fakat KV/R2/DO/D1/binding state versionlanmaz. Rate-limit binding per-location,
eventual-consistency counter'dır; global exact idempotency counter değildir. [S51][S54][S55][S56][S58][S59]

Fiyat kesiti: Free 100k request/day; Paid yaklaşık 5 USD/account/month, 10m request + 30m CPU-ms dahil, sonra
yaklaşık 0.30 USD/million request ve 0.02 USD/million CPU-ms; egress ücretsiz. Hyperdrive/Queues ve Supabase
cost'ları ayrıca normalize edilmelidir. [S40]

**Rol:** edge latency, versioned deploy, Hyperdrive ve Queue için alternatif; DB transaction/session, 128 MB/CPU,
private path, global rate ve state exit kapanana kadar HELD.

## 7. Aday D — Google Cloud Run + Tasks/Jobs/Pub/Sub

Cloud Run region-basedir; data seçilen region'da tutulur. Multi-region için ayrı deployment + global external
HTTP(S) Load Balancer ve health failover gerekir. Direct VPC egress/connector Google VPC'ye erişir; Supabase AWS
PrivateLink otomatik cross-cloud path değildir. [S62][S63][S64][S65]

Secret Manager env veya volume, pinned version ve least-privileged service identity sağlar. Cloud Run end-user
Supabase JWT/JWKS'yi yönetmez; user token uygulama tarafından doğrulanır. Google service-to-service OIDC audience
Google çağrısında kullanılabilir, fakat Kavriva domain authorization yerine geçmez. [S66][S67][S68]

Default scale-to-zero; min instances cold start azaltır. Pending queue yaklaşık 10 s veya 3.5x startup penceresi;
max instances DB overload'u kontrol eder. Request default 5 dakika/max 60 dakika; timeout connection'ı kapatsa da
container çalışmayı sürdürebilir, docs idempotency/reconnect önerir. Quota concurrency 1.000/instance, HTTP
response 32 MiB, outbound yaklaşık 700/s ve 5.000/min/open 50k'dir. [S69][S70][S71][S72]

Cloud Run Jobs 10.000 task, default 10 dakika/max 168 saat, retry 0–10; Cloud Tasks yaklaşık 500 dispatch/s,
1 MiB task, schedule 30 gün, retention 31 gün; Pub/Sub 10 MB message, unacked retention default 7 gün/max 31
gündür. Retry duplicate yaratır; operation ID/claim/lease/DLQ şarttır. [S73][S74][S75]

Cloud Logging/Monitoring/Error Reporting/Trace/audit logs ve trace correlation vardır. Her deploy immutable
revision; traffic split, gradual rollout, tagged revision ve rollback vardır. State/schema/queue/object/external
effect rollback değildir. [S76][S77][S78][S79]

Production custom domain/TLS için global external Application Load Balancer önerilir; direct Cloud Run domain
mapping Preview/region-limitedtir. Cloud Armor rate throttle/ban ek katmandır; public service application
authorization/rate limitine yine ihtiyaç duyar. [S80][S81]

Fiyat request/instance, CPU/memory, region/network/egress/VPC kalemlerine ayrılır. Free kesit yaklaşık 2m
request, 360k GB-s memory, 180k vCPU-s ve North America 1 GB outbound; billing account gerekir. Budget alert
harcamayı durdurmaz. Spend Cap preview hedef aşımında yeni usage'ı durdurabilir, gecikmeli olabilir ve persistent/
in-flight kaynakları tam kapsamayabilir. [S82][S83][S84][S85]

Docker/source deploy, gcloud/Cloud Build/Artifact Registry ve local Docker/Cloud Code geniş test yüzeyi verir.
IAC/IAM/Secret Manager/VPC/LB/Armor/Tasks/PubSub/Trace exit bağımlılıkları ayrıca listelenmelidir. [S86][S87]

**Rol:** container, long request, job/queue, immutable revision ve GCP VPC için güçlü alternatif; cross-cloud
private path, IAM/control-plane, cost stop ve exit kapanana kadar HELD.

## 8. Aday E — Vercel/serverless reference

Vercel Functions Fluid Compute active CPU, provisioned memory ve invocations ile fiyatlanır; 2026-09-19 fiyat
sayfası Hobby/Pro dahil usage ve Enterprise custom fiyatı gösterir. Node.js/Python Pro/Enterprise duration için
2026-06-15 changelog 30 dakikaya kadar davranış duyurur; runtime/framework koşulları değişkendir. [S88][S89][S90][S91]

Supabase Postgres private networking, durable queue, protected audit, service_role custody, cross-provider
private path ve clean-room exit bu debate için Vercel'de eşit araştırılmadı. Vercel yalnız referans, finalist değil.
[S92][OPEN]

## 9. Eşit karşılaştırma matrisi

| Kriter | Supabase Edge | Render | Cloudflare | Cloud Run |
|---|---|---|---|---|
| Bounded HTTP | C | C | C | C |
| Long/CPU-heavy | H: 2 s CPU | I/C: container/worker | H: 128 MB/CPU | I/C: 60 min/Jobs |
| Supabase Postgres | C pooler/direct | C public TLS; private O | C Hyperdrive; session O | C public/VPC; cross-cloud O |
| JWT/JWKS/domain auth | Gateway C; domain O | O app-owned | O app-owned | O app-owned |
| service_role custody | C server secret | C env secret | C encrypted secret | C Secret Manager |
| Durable background | H/external worker | C worker/Workflows | C Queues | C Jobs/Tasks/PubSub |
| Logs/metrics/traces | C logs/metrics; audit O | C logs/OTel | C logs/OTel | C Logging/Monitoring/Trace |
| Immutable rollout | O | C artifact rollback | C version/gradual | C revision/traffic |
| Domain/TLS | C paid SSL | C managed TLS | C managed cert | C LB recommended |
| DDoS/rate | O | C baseline; app abuse O | C but per-location/eventual | C Armor add-on; app O |
| Spend hard stop | C itemized, not universal | O | O | O/preview |
| Local/test | C Supabase/Deno | C Docker | C Wrangler | C Docker/Cloud Code |
| Exit | I; provider state O | I; provider state O | I; bindings/state O | I; GCP state O |

Herhangi bir sütunda bütün hücreler C değildir. Bu tablo kazanan değil, Phase-5 test kapsamıdır.

## 10. Supabase Edge Functions için kesin olmayan, kanıta dayalı değerlendirme

Resmi docs kısa/idempotent HTTP, webhook, Auth/Postgres/Storage integration, RLS-scoped access, küçük AI/LLM
orchestration ve local Deno/Supabase parity için düşük operasyonlu bir aday hipotezini destekliyor. Aynı docs
2 s CPU, 256 MB, 150/400 s wall-clock ve heavy work için external worker uyarısı veriyor. Bu nedenle:

- Bounded command + transaction/outbox enqueue için koşullu aday.
- Heavy CPU, long job, durable worker-only, large media/model, private VPC, global rate, protected audit,
  immutable rollback veya outage-independent authority için kanıt açığı.

Bu ifade “Edge kesin uygundur” veya “kesin uygun değildir” değildir. Seçim ancak aynı fixture'larla duplicate/
timeout, JWKS rotation, pooler transaction, queue retry, audit, rollout, outage, cost-stop ve exit testleri
geçerse Phase-5 ADR'ye girebilir.

## 11. Phase-5 kapıları

1. Auth: issuer/aud/alg/kid/JWKS rotation, revoked session, security epoch, stale tab, collision.
2. Secrets: service_role leak in client/repo/log/crash/AI; rotation and least privilege.
3. Mutation: same operation parallel/serial retry, payload mismatch, timeout-after-commit, status lookup.
4. Transaction: pooler/direct semantics, prepared statement, version conflict, audit-before-effect.
5. Queue: duplicate, retry, poison, DLQ, worker crash, retention and lease boundary.
6. Limits: cold start, memory/CPU/wall time, connection spike, concurrency and bundle/body size.
7. Observability: correlation, redaction, retention/export, platform log/product audit separation.
8. Deployment: health gate, partial rollout, traffic split, rollback, in-flight request, schema compatibility.
9. Network: public TLS/private path, DNS/TLS failure, region outage, egress and residency assumptions.
10. Abuse/cost: flood, credential stuffing, per-user/IP/global rate, queue flood, cap/alert/stop.
11. Exit: clean-room restore of schema/data/object/audit/ledger/queue; revoke old keys/DNS and replay status.
12. AI operations: task-scoped credential, bounded diagnostics, reversible deploy, no owner-debug dependency.

## 12. Disposition

- Supabase Edge/Deno: Supabase-centered low-ops short HTTP için koşullu ilk aday; high-consequence authority HELD.
- Render: persistent container/worker ve runtime esnekliği için somut alternatif; private DB/cost/exit HELD.
- Cloudflare Workers: edge latency, Hyperdrive, versioned deploy ve Queue alternatifi; transaction/private/state
  exit HELD.
- Cloud Run: container, long request, Jobs/Tasks/PubSub, immutable revision ve GCP VPC alternatifi; cross-cloud
  private path, IAM, cost-stop ve exit HELD.
- Vercel: reference only.

Final hüküm: 0 PASS / 4 PRIMARY CANDIDATES HELD / 1 REFERENCE ONLY. ADR, eşit workload fixture'ları, security/
transaction/queue/outage/exit evidence ve normalized cost BOM kapanmadan yazılmamalıdır.

## 13. Resmi kaynak envanteri

### Supabase

- [S1] https://supabase.com/changelog.md
- [S2] https://supabase.com/docs/guides/functions
- [S3] https://supabase.com/docs/guides/functions/limits
- [S4] https://supabase.com/docs/guides/functions/architecture
- [S5] https://supabase.com/docs/guides/functions/auth-headers
- [S6] https://supabase.com/docs/guides/functions/auth
- [S7] https://supabase.com/docs/guides/functions/connect-to-postgres
- [S8] https://supabase.com/docs/guides/database/connecting-to-postgres/pooling-and-limits
- [S9] https://supabase.com/docs/guides/platform/privatelink
- [S10] https://supabase.com/docs/guides/functions/development-environment
- [S11] https://supabase.com/docs/guides/functions/logging
- [S12] https://supabase.com/docs/guides/platform/custom-domains
- [S13] https://supabase.com/docs/guides/platform/billing-on-supabase
- [S14] https://supabase.com/docs/guides/platform/cost-control
- [S15] https://supabase.com/docs/guides/platform/manage-your-usage/edge-function-invocations
- [S16] https://supabase.com/docs/guides/troubleshooting/edge-function-cpu-limits
- [S17] https://supabase.com/docs/guides/functions/deploy

### Render

- [S18] https://render.com/pricing
- [S19] https://render.com/docs/free
- [S20] https://render.com/docs/web-services
- [S21] https://render.com/docs/private-network
- [S22] https://render.com/docs/private-link
- [S23] https://render.com/docs/outbound-bandwidth
- [S24] https://render.com/docs/deploys
- [S25] https://render.com/docs/rollbacks
- [S26] https://render.com/docs/logging
- [S27] https://render.com/docs/service-metrics
- [S28] https://render.com/docs/metrics-streams
- [S29] https://render.com/docs/background-workers
- [S30] https://render.com/docs/cronjobs
- [S31] https://render.com/docs/workflows-limits
- [S32] https://render.com/docs/configure-environment-variables
- [S34] https://render.com/articles/how-render-handles-ddos-attacks
- [S35] https://render.com/docs/custom-domains
- [S36] https://render.com/docs/tls
- [S37] https://render.com/docs/regions
- [S38] https://render.com/docs/render-vs-vercel-comparison

### Cloudflare

- [S39] https://developers.cloudflare.com/workers/platform/limits/
- [S40] https://developers.cloudflare.com/workers/platform/pricing/
- [S41] https://developers.cloudflare.com/workers/configuration/placement/
- [S42] https://developers.cloudflare.com/data-localization/how-to/workers/
- [S43] https://developers.cloudflare.com/workers/configuration/secrets/
- [S44] https://developers.cloudflare.com/workers/runtime-apis/bindings/
- [S45] https://developers.cloudflare.com/hyperdrive/examples/connect-to-postgres/postgres-database-providers/supabase/
- [S46] https://developers.cloudflare.com/hyperdrive/platform/limits/
- [S47] https://developers.cloudflare.com/hyperdrive/concepts/connection-pooling/
- [S48] https://developers.cloudflare.com/hyperdrive/platform/pricing/
- [S49] https://developers.cloudflare.com/queues/platform/limits/
- [S50] https://developers.cloudflare.com/queues/configuration/batching-retries/
- [S51] https://developers.cloudflare.com/workers/observability/
- [S54] https://developers.cloudflare.com/workers/versions-and-deployments/
- [S55] https://developers.cloudflare.com/workers/versions-and-deployments/gradual-deployments/
- [S56] https://developers.cloudflare.com/workers/versions-and-deployments/rollbacks/
- [S58] https://developers.cloudflare.com/workers/runtime-apis/bindings/rate-limit/
- [S59] https://developers.cloudflare.com/waf/rate-limiting-rules/
- [S60] https://developers.cloudflare.com/workers/configuration/routing/custom-domains/
- [S61] https://developers.cloudflare.com/cloudflare-one/access-controls/applications/http-apps/authorization-cookie/validating-json/

### Google Cloud Run

- [S62] https://docs.cloud.google.com/run/docs/locations
- [S63] https://cloud.google.com/run/docs/multiple-regions
- [S64] https://docs.cloud.google.com/run/docs/securing/private-networking
- [S65] https://docs.cloud.google.com/run/docs/configuring/vpc-direct-vpc
- [S66] https://docs.cloud.google.com/run/docs/configuring/services/secrets
- [S67] https://docs.cloud.google.com/run/docs/authenticating/end-users
- [S68] https://docs.cloud.google.com/run/docs/authenticating/service-to-service
- [S69] https://docs.cloud.google.com/run/docs/about-instance-autoscaling
- [S70] https://docs.cloud.google.com/run/docs/configuring/min-instances
- [S71] https://docs.cloud.google.com/run/docs/configuring/request-timeout
- [S72] https://docs.cloud.google.com/run/quotas
- [S73] https://cloud.google.com/run/docs/create-jobs
- [S74] https://docs.cloud.google.com/tasks/docs/quotas
- [S75] https://docs.cloud.google.com/pubsub/quotas
- [S76] https://docs.cloud.google.com/run/docs/monitoring-overview
- [S77] https://docs.cloud.google.com/run/docs/logging
- [S78] https://docs.cloud.google.com/run/docs/trace
- [S79] https://cloud.google.com/run/docs/rollouts-rollbacks-traffic-migration
- [S80] https://docs.cloud.google.com/run/docs/mapping-custom-domains
- [S81] https://docs.cloud.google.com/armor/docs/rate-limiting-overview
- [S82] https://cloud.google.com/run/pricing
- [S83] https://docs.cloud.google.com/free/docs/free-cloud-features
- [S84] https://docs.cloud.google.com/billing/docs/how-to/budgets
- [S85] https://docs.cloud.google.com/billing/docs/how-to/budgets-spend-caps
- [S86] https://docs.cloud.google.com/run/docs/testing/local
- [S87] https://docs.cloud.google.com/run/docs/deploying-source-code

### Vercel reference

- [S88] https://vercel.com/docs/functions
- [S89] https://vercel.com/pricing
- [S90] https://vercel.com/docs/functions/usage-and-pricing
- [S91] https://vercel.com/changelog/vercel-functions-can-now-run-up-to-30-minutes
- [S92] https://vercel.com/docs/plans
