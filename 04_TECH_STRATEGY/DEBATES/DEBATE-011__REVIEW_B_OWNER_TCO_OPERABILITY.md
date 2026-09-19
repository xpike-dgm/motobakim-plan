# DEBATE-011 — Bağımsız Reviewer B: Owner / Gerçek TCO / Operability / Reversibility

**Durum:** `HELD — NO WINNER / A ve B EŞİT BELGESEL STATÜ / ADR NOT READY`  
**Tarih:** 2026-09-19 (Europe/Istanbul)  
**Reviewer:** Bağımsız Reviewer B  
**Kapsam:** `NO-CODE / NO ACCOUNT / NO PURCHASE / GATE 4 -> 5 CLOSED`  
**Aday A:** Supabase'e yakın bounded Edge API runtime  
**Aday B:** Supabase çekirdeğine ayrı managed container API + worker runtime

Bu dosya yalnızca bağımsız adversarial review'dur. Kod, prototip, executable spike, hesap, provider hesabı, plan,
abonelik, ödeme, migration, deployment, ADR veya Gate 4 -> 5 geçişi oluşturmaz. Provider seçmez; A ve B'yi aynı
owner/TCO/operability/recovery kanıt kapısında tutar.

## 0. Kısa hüküm

Yönetici önerisi, Kavriva API'nin mantıksal sınırını doğru kuruyor: istemci veya provider console canonical authority
değil; high-consequence mutation commit anında yeniden yetkilendiriliyor; operation identity ve fingerprint olmadan
blind retry yapılmıyor; protected audit, quarantine, restore ve exit ayrı anlamlar olarak korunuyor; kısa request ile
uzun iş ayrılıyor. Bunlar korunmalıdır.

Ancak önerideki şu cümleler henüz kanıt değil:

- A'nın tek/az control-plane yüzeyinin gerçek güvenli toplam maliyeti ve owner işletim yükü daha düşüktür.
- B, A başarısız olursa hazır ve düşük-riskli ilk fallback'tir.
- Uzun iş doğduğunda queue + worker eklenebilir; bu geçiş mevcut API contract'ını ve maliyeti sürtünmesiz korur.
- Provider-neutral contract clean-room çıkışını fiilen garanti eder.
- ``no-owner-debug`` iki adayda da operasyonel olarak kapanmıştır.

Bu iddialar için provider/account/billing/outage/support, deploy/rollback, worker/queue, protected audit/floor,
restore ve clean-room exit düzlemleri birlikte kanıtlanmalıdır. Bugün iki aday için de belgesel sonuç:

| Hüküm | Aday A — Edge | Aday B — Container + worker |
|---|---:|---:|
| Ortak 16 failure/TCO senaryosu | `0 PASS / 16 HELD / 0 REJECT` | `0 PASS / 16 HELD / 0 REJECT` |
| Owner/TCO/operability sonucu | `HELD` | `HELD` |
| Production activation | Yok | Yok |
| Provider/plan/account seçimi | Yok | Yok |

Bu eşit `HELD`, risklerin aynı olduğu anlamına gelmez. A'da common-mode/provider coupling ve Edge sınırları; B'de
ek account/billing/network/pooling/worker koordinasyonu ve parçalı failure gözlemi öne çıkar. A veya B'nin bir
capability'si aşağıdaki hard-fail'lerden birine düşerse o capability `REJECT-IF-UNMITIGATED` olur; diğer aday otomatik
kazanan sayılmaz.

## 1. Okunan bağlayıcı kanıt ve review yöntemi

Bu review aşağıdaki belgelerin tamamı üzerinden yapılmıştır:

- `00_CONTROL/AI_START_HERE.md`
- `00_CONTROL/CURRENT_STATE.md`
- `00_CONTROL/SOURCE_OF_TRUTH.md`
- `00_CONTROL/DECISION_LOG.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__API_RUNTIME_REQUIREMENTS_SYNTHESIS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__API_RUNTIME_FAILURE_TCO_RESEARCH.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-011__MANAGER_PROPOSAL.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-010__JUDGE_SYNTHESIS.md`

Evidence dili:

- `CONFIRMED`: kaynakta mekanizma veya kural vardır; Kavriva üretim güvenliği otomatik olarak kanıtlanmış değildir.
- `INFERRED`: mekanizma ile proje boundary'sinden türetilen risk; eşit fixture gerekir.
- `OPEN`: plan, provider, account, operasyon sahibi, maliyet veya bağımlılık kapanmamıştır.
- `HELD`: gereksinimle açıkça çelişmiyor; olumlu üretim kanıtı yok, güvenli hold yolu tasarlanabilir.
- `REJECT-IF-UNMITIGATED`: owner/debug, authority bypass, data continuity, audit, spend veya exit gereksinimini
  karşılamayan kullanım; düzeltme ve negative evidence olmadan kullanılamaz.

Review ölçütü, headline runtime fiyatı veya dashboard health'i değildir. Ölçüt şudur: teknik olmayan tek owner ve
bounded AI, kabul edilebilir bir olayda güvenli biçimde durabiliyor, doğru kişiye/escalation yoluna devredebiliyor,
canonical truth'i ve audit/floor'u koruyabiliyor, sonrasında cross-plane reconcile/restore/exit yapabiliyor mu?

## 2. Bağlayıcı owner ve işletim tabanı

`DEC-0029` gereği kullanıcı product/decision owner'dır; developer, debugger, SQL/SSH operatörü veya incident repair
kişisi değildir. `DEC-0030`/`DEC-0032` gereği TRY 2.000–3.000/ay yalnız ileri dönem non-store planning ceiling'idir;
bugünkü ödeme izni değildir ve zorunlu güvence bu tavana sığmıyorsa zayıflatılamaz. `DEC-0034`/`DEC-0035`/`DEC-0037`
gereği API mediation, protected audit/floor, cross-plane recovery, no-owner-debug ve provider/billing hold zorunludur.

### 2.1 Owner'ın görebileceği kararlar

Her iki aday owner'a teknik teşhis değil, aşağıdaki anlaşılır durumları göstermelidir:

- `SERVICE_UNAVAILABLE`: hangi olumlu işlemlerin durduğu, safe read/history'nin sürüp sürmediği ve escalation sahibi;
- `ACCOUNT_HELD` / `BILLING_HELD`: hangi quota/fatura/hesabın etkilenebileceği, kabul edilmiş verinin korunduğu ve
  ödeme/provider desteği gibi açık dış aksiyon;
- `OUTCOME_UNKNOWN`: operation ID, duplicate guard, status resolver ve effect'in neden tahmin edilmediği;
- `AUDIT_HELD`: protected evidence/fallback yazılamadığı için hangi effect'in açılmadığı;
- `DEPLOYMENT_HELD`: release/schema/message generation uyumsuzluğu ve neden cutover yapılmadığı;
- `RESTORE_QUARANTINE`: hangi plane'lerin doğrulanmadığı ve neden eski snapshot'ın authority olmadığı;
- `EXPORT_PARTIAL`: eksik plane, source'un neden değiştirilmediği ve clean-room devam koşulu.

“Retry et”, “loglara bak”, “queue'yu temizle”, “SQL çalıştır”, “provider console'dan düzelt” owner runbook'u değildir.
Bu adımlardan biri normal veya incident yolu için gerekliyse aday/capability `REJECT-IF-UNMITIGATED` olur.

### 2.2 AI'nin izin sınırı

AI task'ları her iki adayda da exact scope, credential class/audience/expiry, allowed-forbidden işlem, dry-run veya
read-only başlangıç, `operation_id`, expected generation, hard-stop, evidence digest, reviewer/validator ve
owner-facing handoff taşımalıdır. AI provider owner/billing root, unrestricted SQL/SSH, `service_role`, global object
credential, raw SMTP/SMS secret, restore-delete, role grant, approval/publication veya privileged recovery authority
alamaz. Provider hesabının legal/billing sahibi ve bağımsız insan/kurum recovery desteği AI tarafından taklit edilemez.

## 3. Yönetici önerisinde korunması gerekenler

Aşağıdaki çekirdek öneri ile uyumludur ve geri alınmamalıdır:

1. API fiziksel runtime'ın ephemeral/replaceable giriş kapısıdır; persistent product truth runtime memory'si değildir.
2. High-consequence mutation current actor/session/epoch/action/scope/generation ile commit anında reauthorize edilir.
3. Aynı operation ID + payload fingerprint status lookup ve idempotent effect için kullanılır; timeout success/failure
   tahminine çevrilmez.
4. Direct Data API/RPC/Storage/signed URL/provider console canonical product authority olamaz; RLS/Storage yalnız
   defense-in-depth'tir.
5. Audit, object, queue, package, restore ve negative floor ayrı anlamlardır; runtime log'u product audit değildir.
6. `waitUntil`/background callback durable queue veya worker completion kanıtı değildir.
7. A/B aynı failure fixture, aynı normalized safe-cost BOM, aynı no-owner-debug ve aynı clean-room gate ile sınanır.
8. A'nın aday olarak tutulması bir production winner değildir; B de otomatik fallback değildir.

## 4. CRITICAL bulgular

### C-01 — `No-owner-debug` iddiası var; recovery/support/account ownership closure yok

**Bulgu.** Manager Proposal owner'a yalnız anlaşılır hold/escalation vereceğini söylüyor; fakat her iki aday için
provider account sahibi, billing/payment failure, domain/DNS/SMTP sahibi, queue/worker recovery sahibi, audit/floor
fallback custodian, support ticket açma yetkisi, provider support seviyesi, account-lock/closure yolu, response target
ve son admin kaybında gerçek insan/kurum zinciri tanımlı değil. “AI-operated” ifadesi bu yetki ve legal sahipliklerin
yerine geçemez.

**Risk.** Provider veya hesap arızasında owner ya SQL/SSH/console repair'a itilir ya da positive işlemler sessizce
beklerken recall/recovery için de güvenli yol kalmaz. A'da tek control-plane bu riski ortadan kaldırmaz; B'de ikinci
account/support zinciri sayısı artar. Bu yalnız dokümantasyon eksiği değil, owner modeline aykırı işletim tasarımıdır.

**Zorunlu düzeltme / evidence.** A ve B için her olayda şu tablo bulunmalıdır: detection source, automatic safe-stop,
owner-visible state, affected scope, protected data retained, external human/provider action, credential class,
support/escalation target, cost/overage behavior, expected recovery/forward-reconcile step, reviewer and exit proof.
Account owner, provider support, recovery verifier ve emergency negative operator görevleri; aynı kişi/credential ile
self-approval yaratmayacak şekilde açıkça ayrılmalıdır. En az bir outage/account-lock/last-admin tabletop'ta owner
yalnız `hold / notify / request-support / safe-stop` seçebilmelidir.

**Hüküm.** Owner'a teknik repair görevi çıkıyorsa A ve B için ilgili capability `REJECT-IF-UNMITIGATED`; bu closure
gelene kadar iki aday `HELD`.

### C-02 — Protected audit/floor ve emergency-negative yolunun failure-domain bağımsızlığı ertelenmiş

**Bulgu.** Öneri “protected audit/floor ve emergency-negative yolunun Supabase ortak failure domain'inden ne kadar
ayrılacağı sonraki dedicated debate/evidence gate'inde kapanır” diyor. Bu, bir sonraki tartışmaya bırakılabilecek bir
detay değil; API runtime adayının minimum safe operating boundary'sidir. Audit/floor, object, DB/Auth/Storage, DNS,
queue/worker ve billing outage'ı aynı anda ayrı ayrı ele alınmadan `ACCEPTED`, `RECALL`, `SUSPEND` veya `RECOVERY` sonucu
owner'a güvenilir biçimde verilemez.

**Risk.** A'da DB/Auth/Storage/Functions yakınlığı common-mode outage ve audit/floor kaybını büyütebilir. B'de API
runtime'ını ayırmak DB/object/audit/floor'u otomatik olarak bağımsız yapmaz; partial health “yeşil API” ile yanlış
başarı izlenimi yaratabilir. Normal audit ve fallback aynı hesap/failure domain'inde ise fallback gerçek fallback
değildir.

**Zorunlu düzeltme / evidence.** İki aday için Auth/API/DB/object/audit/floor/DNS/billing/queue/worker outage matrix'i
aynı fixture ile doldurulmalıdır. Her satır safe read, positive mutation, emergency negative, `OUTCOME_UNKNOWN`,
accepted/history preservation, owner action, independent credential/control-plane, support escalation, cost impact ve
restore reconciliation taşımalıdır. Protected custody veya bağımsız fallback yoksa positive high-consequence effect
`AUDIT_HELD`; negative effect'in minimum evidence ve anti-resurrection koşulu yoksa o yol da açılmamalıdır.

**Hüküm.** A ve B için `HELD`; bağımsız negative/audit/floor koşulu karşılanamıyorsa ilgili production capability
`REJECT-IF-UNMITIGATED`. B'nin ayrı API hesabı tek başına üstünlük kanıtı değildir.

### C-03 — Gerçek toplam maliyet ve bounded spend henüz BOM değil, niyet listesi

**Bulgu.** Yönetici Proposal aynı BOM kalemlerini sayıyor; ancak kalemlerin ölçü birimi, plan/region, dahil kota,
overage, minimum ücret, hard cap, cap dışı kalem, stop action, incident/restore/exit davranışı ve owner approval durumu
belirlenmiş değil. “A daha sade/daha düşük maliyetli” ve “B daha görünür/fazla service” ifadeleri bu nedenle yalnız
hipotezdir. TRY ceiling'e göre güvenli minimum BOM karşılaştırması yapılmış değildir.

**Gizli maliyet yüzeyleri:**

- ortak PostgreSQL/Auth/private Storage çekirdeği, compute/IO/storage/egress/backup/PITR ve Auth kullanım ölçüsü;
- API invocation/CPU/memory/egress veya container instance minimumu, image/build/registry/health/deploy maliyeti;
- queue message/retention/retry/DLQ, worker compute/idle/concurrency, scheduler ve poison-message karantinası;
- object quarantine, scanner/URL fetch, derivative/preview/OCR/AI, object versioning/retrieval/egress ve orphan cleanup;
- protected product audit, independent fallback/floor, log drain, retention/legal hold, monitoring/alert/paging;
- DNS/domain/TLS/certificate, custom SMTP/sender domain/abuse, gerekiyorsa SMS/notification ve support planı;
- duplicate incident capacity, isolated restore/clean-room environment, temporary export/import storage, DNS cutover,
  secret reissue, independent review, decommission ve account closure;
- vergi, kur, kart/komisyon, billing period, provider minimumları, quota denial, overage ve hesap kısıtlaması.

**Risk.** Headline runtime bedeli düşük görünürken zorunlu assurance/fallback sonradan eklenir; fatura limiti yalnız bir
kalemi durdurur, diğer adjunctlar çalışmaya veya unavailable olmaya devam eder. Bütçe baskısıyla protected audit,
recovery veya exit zayıflatılırsa bu DEC-0030'a aykırıdır.

**Zorunlu düzeltme / evidence.** A ve B için ortak satır kimlikli normalized BOM; her satırda `mandatory / deferrable /
optional / scale-triggered`, resmi tarih/plan/region, unit/quota/overage, tax/FX/card belirsizliği, hard cap'in neyi
kapsadığı, stop/hold state, incident/restore/exit ayı ve external support/human dependency bulunmalıdır. Unknown satır
`UNVERIFIED`; mandatory satır tavana sığmıyorsa capability `BILLING_HELD/HELD`. Gerçek toplam maliyet, sadece runtime
etiketi değil güvenli minimum çalışma ve çıkış maliyetidir.

**Hüküm.** İki aday da `HELD`; no-owner spend stop veya unbounded spend varsa capability `REJECT-IF-UNMITIGATED`.

### C-04 — Uzun iş “gerektiğinde eklenir”; queue/worker ve deploy compatibility ilk günden operasyon sözleşmesine bağlı değil

**Bulgu.** Öneri Edge'i yalnız kısa işler için tutarak başlangıçta mikroservis ağı kurmuyor; uzun iş doğduğunda durable
queue + bounded worker ekliyor. Bu yön gereksiz erken dağıtık sistem kurmama açısından makul, fakat “uzun iş doğduğunda”
hangi capability'nin long-job olduğu, hangi sınırı geçince queue'ya ayrılacağı, worker'ın kill/restart/lease/heartbeat,
retry budget/DLQ/backpressure/poison policy'si, queue message version'ı ve deploy sırasında old/new worker uyumu şimdi
tanımlı değil. Uzun iş çoğunlukla package build, object scan/preview, export, AI/OCR, reconciliation ve notification
gibi kritik yan etkili işlerin bir parçasıdır; sonradan eklenen worker product semantics'i yeniden açabilir.

**Risk.** A'da background callback/Edge limitleri işi yarıda bırakabilir; B'de worker/queue ayrı health green görünürken
canonical effect, audit veya outbox mismatch kalabilir. Backlog, retry storm veya DLQ owner tarafından elle düzeltilmek
zorunda kalırsa no-owner-debug ihlali oluşur. Queue'nun “one delivery” sinyali ürün effect'inin tek uygulandığını
kanıtlamaz.

**Zorunlu düzeltme / evidence.** Her aday aynı long-job capability table'ını taşımalıdır: synchronous bounded step,
accepted/queued state, operation identity, lease/heartbeat, idempotent checkpoint/effect, retry budget, DLQ/quarantine,
backpressure, kill/restart, graceful drain, old/new message compatibility, owner-visible backlog/hold ve reconcile
owner. Long-job capability ilk kez eklendiğinde queue/worker/audit/object/restore/exit BOM'u yeniden açılmalı; “sonra
ekleriz” hidden service yükü sayılmalıdır.

**Hüküm.** A ve B `HELD`; durable worker yaşam döngüsü, no-owner backlog recovery veya message/schema fence yoksa ilgili
long-job capability `REJECT-IF-UNMITIGATED`.

### C-05 — Provider-neutral core, clean-room runtime/provider exit'i fiilen kanıtlamıyor

**Bulgu.** Manager Proposal operation/authorization/audit/object/package/recovery contract'ını Edge SDK'sına
gömmez; bu doğru bir tasarım niyetidir. Fakat clean-room exit, bu logical contract'ın yanında provider-specific
runtime semantics, deployment artifact/config, queue state, secret reissue, object/audit custody, identity/session,
DNS/TLS, support/billing/account closure ve old-runtime drain gerektirir. “Container image taşınabilir” de tek başına
B'nin managed queue/worker, health, network, config ve audit semantics'ini taşımaya yetmez.

**Risk.** A'da Edge invocation, Deno/package, secret/config, Auth/Storage/Management API ve queue semantics; B'de web
service/worker/image registry, health/deploy, pooler/TLS/egress, queue, DNS ve provider account semantics exit sırasında
kaybolabilir. `pg_dump`, object copy, image copy veya provider clone; pending operation, accepted-operation identity,
negative/deletion floor, protected audit continuity ve classified object lineage'ını tek başına taşımaz.

**Zorunlu düzeltme / evidence.** İki aday için source untouched kalacak şekilde isolated clean-room import fixture'ı:

1. canonical current/history/provenance, operation ledger/status/conflict/tombstone;
2. release/package/artifact/config/schema/message generations ve compatibility manifest;
3. provider-qualified identity mapping, policy/grant/competence, sessions/epoch ve recovery state;
4. object bytes + metadata/digest/lineage/classification/retention/disclosure;
5. protected audit/fallback/floor, incident/impact graph ve non-restorable negative/accepted-operation floor;
6. queue pending/DLQ/lease semantics, runtime artifact, deployment/release fence, secret reissue ve DNS cutover;
7. restore/exit sonrası old revoke/recall/delete/suspension/accepted operation'ın dirilmediği ve yeni valid data'nın
   silent rollback ile kaybolmadığı negative test;
8. yeni ortama cutover/dual-run/decommission, provider support/billing closure ve owner-readable `EXPORT_PARTIAL`.

**Hüküm.** Clean-room import ve anti-resurrection kanıtı olmadan A/B `HELD`; truth/floor kaybı veya source'a erken
   müdahale varsa exit capability `REJECT-IF-UNMITIGATED`.

## 5. MAJOR bulgular

### M-01 — Eşit `HELD` tablosu aday-specific operasyon yükünü yeterince görünür kılmıyor

Manager Proposal'ın 16 satırlı tablosu doğru ortak gate'i kuruyor; fakat aynı `HELD` etiketi iki farklı failure şekline
uygulanıyor. A/B eşit muamele, farkları silmek değil aynı kanıtı istemektir.

| Boyut | A — Edge | B — Container + worker | Review sonucu |
|---|---|---|---|
| Control plane | Core provider'a yakın, daha az görünen service | Runtime/worker/queue ve core provider arasında daha fazla yüzey | Hiçbiri otomatik avantaj değil |
| Kısa request | Edge memory/CPU/wall-clock/package/idle sınırları | Daha uzun process/concurrency kontrolü; yine DB/transaction sınırı | Gerçek workload fixture gerekir |
| Long job | External queue/worker sonradan eklenince gizli complexity ve egress | Worker baştan görünür; queue/worker/health/deploy faturası ve coordination artar | Her ikisi `HELD` |
| Pooling/latency | DB'ye yakınlık olumlu sinyal; Edge connection/pool/session varsayımları açık değil | Cross-provider TLS, region, pooler, egress, latency ve retry yüzeyi | Her ikisi `HELD` |
| Outage | Auth/DB/Storage/Function common-mode riski | Partial health ve çoklu outage/account/billing korelasyonu | Bağımsız audit/floor gerekir |
| Deploy/rollback | Function revision rollback DB/schema/queue/object'ı geri almaz | Web/worker/image/config/migration/message drain birlikte uyum ister | Health green yeterli değil |
| Exit | Edge/Auth/Storage/config semantics adapter ister | Image taşınabilir; managed queue/health/config/audit semantics ayrıca taşınır | Clean-room kanıtı gerekir |
| Owner | Daha az rutin yüzey olabilir; hidden adjunct onarımı yine owner'a kalabilir | Daha çok account/support/secret/incident koordinasyonu | AI task/suppport handoff kanıtı gerekir |

**Düzeltme.** Her ortak senaryo için candidate-specific dependency count, failure domain, owner output, external
support action, cost class, exit plane ve `REJECT-IF-UNMITIGATED` cue ayrı yazılmalıdır. Bu ağırlıklandırılmış bir
provider seçimi değildir; eşit kanıtın aday-spesifik riskleri gizlememesidir.

### M-02 — Provider/account/billing/outage/support lifecycle matrix'i eksik

Proposal provider/region/DNS/billing/quota outage'ı sayıyor; fakat account oluşturma/owner değişimi, payment failure,
quota throttle, spend cap'in yalnız belirli kalemleri durdurması, plan downgrade/upgrade, provider incident, region
değişimi, DNS/domain expiration, custom SMTP/notification, support ticket, status-page yanlış pozitifliği, account
closure/export ve provider terms değişikliğinde güvenli state'i uçtan uca göstermiyor.

**Düzeltme.** A ve B için aşağıdaki olaylar ayrı state-machine satırları olmalıdır: login/refresh/step-up; low-risk
read; high-consequence positive hold; emergency negative; queue/worker pause; audit fallback; billing restriction;
provider support; account closure; restore; exit. Her satır accepted history, pending operation, latest safe package,
owner-readable reason, external dependency, cost impact ve resume/forward-reconcile koşulunu göstermelidir.

**A/B eşitliği.** A'da tek provider ticket yüzeyi daha az olabilir ama common-mode etkisi büyür. B'de iki veya daha
fazla account/support/billing hattı vardır; biri unavailable iken diğerinin bypass yaratması yasaktır. İkinci provider
sayısı otomatik resilience değildir.

### M-03 — Deploy/rollback, schema, queue-message ve worker-drain fence'i yeterince somut değil

Proposal rollback'ın kodu geri çevirdiğini, DB/object/audit/floor'u geri çevirmediğini doğru söylüyor; fakat her aday için
`release_id`, `schema_generation`, `message_version`, `operation compatibility window`, old-runtime drain, secret
rotation sırasında in-flight request/worker, failed health ile partial deploy, pre-deploy migration ve forward recovery
durumları birleştirilmiş acceptance sözleşmesine bağlanmıyor.

**Düzeltme.** Runtime revision rollback yalnız uyumlu artifact'e dönsün; DB migration forward-compatible/expand-contract
olsun; queue old/new message'ı explicit version fence ile taşısın; in-flight effect aynı operation identity ve audit
reference ile reconcile edilsin. Deploy green olması canonical transaction/audit/queue/object health değildir.

### M-04 — “Uzun iş” sınıflandırması ve capability activation trigger'ı ölçülebilir değil

“Uzun iş doğduğunda” ifadesi product roadmap, runtime limit, dependency, cost ve recovery kararını ileri iter. Package
build, object scan/preview, export, OCR/AI, notification ve reconciliation'ın hangisinin synchronous kısa adım, hangisinin
durable job olduğu; minimum safe timeout margin'i; kill/restart sonrası outcome; queue backlog threshold'u; worker idle
ve scale-triggered cost'u belirtilmemiştir.

**Düzeltme.** Her workload için bounded synchronous step, `ACCEPTED/QUEUED`, status lookup, lease/heartbeat,
retry/DLQ/backpressure ve owner stop koşulu daha aday seçilmeden fixture'a yazılmalı. Numeric limitlerin seçimi sonraki
kanıt konusudur; fakat “sonradan eklenecek” capability'nin contract ve BOM etkisi şimdiden görünmelidir.

### M-05 — Observability, product audit ve incident evidence ayrımı doğru; fakat retention/custody/owner output işletilmiyor

Runtime logs'in product audit olmadığı açıkça doğru. Eksik olan; log/metric/trace correlation, sampling/truncation,
retention/legal hold, privacy/redaction, independent export, clock/order, gap/fork/replay detection, alert routing,
cost cardinality ve incident evidence manifestinin aday-neutral owner contract'ına bağlanmasıdır. Platform dashboard veya
health check, queue/audit/object/product truth değildir.

**Düzeltme.** Her operation/release/object/package/queue state için current state, last transition, reason, generation,
operation/audit reference, affected scope, resolver, next action, unknown/partial/held denominator ve safe-read/positive-
hold/negative-availability ayrımı owner-readable olmalıdır. Log retention yetersizse effect `UNKNOWN/HELD` ve evidence
export/fallback planı gerekir; bu hizmetler BOM'da ayrı satırdır.

### M-06 — Object quarantine/scan/preview/backup yükü runtime ve TCO'ya tam bağlanmamış

Object workflow'ü yalnız upload endpoint'i değildir. Quarantine, private-address/redirect/SSRF kontrolü, archive/size/
digest, scan/render/OCR/AI, derivative lineage, classification propagation, orphan cleanup, scoped handle, object
backup/restore ve egress/temporary storage uzun veya provider-adjunct iş olabilir. Proposal kalemleri sayıyor; fakat
hangi durumun queue/worker, hangi state'in `OBJECT_QUARANTINE`, hangi scanner/backup/support dış bağımlılığının zorunlu
olduğu açık değil.

**Düzeltme.** Object lifecycle her iki adayda aynı manifest/lineage/digest/generation ile çalışmalı; quarantine veya
scan tamamlanmadan active/public handle verilmemeli; derivative en restrictive classification'ı taşımali; incomplete/
digest mismatch/orphan/restore failure owner-visible olmalı. Scanner, object backup, egress, clean-room temporary storage
ve handle revoke maliyetleri normalized BOM'a eklenmeli.

### M-07 — AI task-pack, runtime/provider configuration ve external human action sınırlarını henüz kanıtlamıyor

Proposal AI'nin narrow credential ve no-owner-debug ilkesini taşıyor; ancak Edge ve B için gerçek task aileleri,
minimum context pack ve forbidden scope örneği yok. Supabase/managed-container secret rotation, queue pause/resume,
deploy drain, schema compatibility, DNS/TLS, SMTP, billing stop, support ticket, audit export, restore quarantine ve
clean-room import işleri provider-specific external action gerektirir.

**Düzeltme.** Her task için exact objective, allowed/forbidden path, credential audience/expiry, dry-run, operation ID,
hard stop, evidence custody, reviewer/validator, rollback yerine forward recovery, external human action ve plain-
language handoff yazılmalıdır. AI owner/billing/root/service role veya approval/publication credential alamaz; owner
provider console repair yapmaz. Task collision/gap/orphan audit'i olmadan “AI-operable” `PASS` değildir.

### M-08 — Restore/failover runbook'u runtime ve account planes'ine kadar kapanmamış

Restore quarantine ve anti-resurrection doğru bağlayıcı koşullardır; ancak DB snapshot/PITR, object bytes, audit/floor,
identity/config/secret, queue pending/DLQ, runtime artifact/release, DNS/TLS ve support/account state ayrı restore edilir.
“Health green” veya başarılı restore job'ı cutover kanıtı değildir. Eski accepted operation, recall, revoke, deletion,
suspension veya old package generation yeniden authority olamaz.

**Düzeltme.** Cross-plane manifest ve verifier; isolated import; current negative/security floor karşılaştırması;
audit continuity; object/package integrity; queue replay/dedupe; secret reissue; old runtime drain; owner-readable
`RESTORE_QUARANTINE`; source unchanged until acceptance; ardından positive cutover fixture'ı her aday için aynı olmalıdır.
Restore drill'i ve temporary isolated environment cost'u BOM'a eklenmelidir.

### M-09 — Safe state'ler ve kullanıcı/owner denominator'ları cost stop ile bağlanmamış

Proposal state isimlerini veriyor; fakat hangi state'in normal read'i, user pending work'ü, nonessential upload'ı,
queue intake'ını, positive approval'ı, negative suspension'ı veya billing spend'ini durdurduğu her aday için açık değil.
`BILLING_HELD` yalnız fatura uyarısı değil; accepted history ve pending operation korunarak yeni spend ve yüksek sonuçlu
effect'in sınırlandırılmasıdır.

**Düzeltme.** State transition matrix'e her state için allowed/blocked effects, retained data, retry policy, cost stop,
resolver/support, audit event ve exit/restore impact satırı eklenmelidir. Alert/cap olmayan veya cap dışı adjunct çalışmaya
devam eden durum production-ready sayılmaz.

## 6. MINOR bulgular

### m-01 — “İnce / stateless” ifadesi ephemeral runtime ile state'siz ürün anlamını ayırmıyor

API runtime stateless/replaceable olabilir; operation ledger, security epoch, audit intent, object manifest, queue state
ve release/floor state'siz değildir. Metin bu ayrımı her owner-facing özetinde korumalı; aksi halde runtime restart ile
ürün state'i kaybolabilir sanılır veya tersine runtime memory'si authority sanılır.

### m-02 — A/B etiketleri ve provider isimleri karar seviyelerini karıştırmayacak şekilde her tabloda scope etiketi taşımalı

Bu review'da A/B runtime adaylarıdır; DEBATE-010'daki A/B identity compositions ile aynı etiketler kullanılmamalıdır.
Supabase/Render/Cloudflare isimleri representative mechanism'dir; plan/account/purchase seçimi değildir. Her tablo
`runtime candidate / representative / not selected` ibaresini taşımalıdır.

### m-03 — Headline fiyat veya limit sinyallerinde tarih, plan, region, quota ve “purchase quote değil” etiketi görünür olmalı

USD sinyali, TRY karşılığı, tax/FX, annual-vs-monthly, support/SLA, overage ve exit maliyetini taşımaz. Resmî kaynak
değişebilir; future ADR öncesi yeniden doğrulama gerekir.

### m-04 — “Anlamlı biçimde daha pahalı/karmaşık” geçiş dili ölçülebilir evidence condition'a çevrilmeli

Provider seçmezken numeric threshold kilitlemek gerekmez; yine de comparison fixture her adayda aynı workload, safety
margin, support/recovery requirement, owner task count, incident/restore/exit reserve ve normalized cost category ile
“A gate failure / B equal pass” sonucunu üretmelidir. Yalnız sezgisel complexity veya headline fiyat geçiş nedeni olamaz.

## 7. Düzeltilmiş ve eşit normalized BOM

A ve B için aynı satır kimlikleri kullanılmalıdır. Bu tablo fiyat hesabı değildir; gizli hizmet ve operasyon yüklerini
görünür kılan minimum BOM düzeltmesidir. Her satır sonraki araştırmada resmi tarih/plan/region/unit/quota/overage/tax/
FX/support/stop/exit kanıtıyla doldurulacak ve `mandatory / deferrable / optional / scale-triggered` sınıfı alacaktır.

| BOM satırı | Asgari kapsam | Sınıf / hard-stop | A'ya özgü görünmeyen yük | B'ye özgü görünmeyen yük |
|---|---|---|---|---|
| Shared canonical core | DB compute/IO/storage, Auth usage, private object bytes/ops/egress, region ve base backup | `mandatory`; quota/billing hold | Aynı provider içinde “core dahil” sanılan adjunctlar | Core provider faturası + runtime'a ağ/egress |
| API request runtime | Edge invocation/CPU/memory/idle/wall-clock veya web instance/concurrency/minimum uptime | `mandatory`; unbounded usage yok | Function limits, nested calls, revision/secret cutover | Web service minimum instance, cold start, image/build/registry |
| Queue/worker plane | Queue retention/message/retry/DLQ, worker compute/idle/concurrency, lease/heartbeat, scheduler | Long job için `mandatory`; backlog/poison `HELD` | Sonradan eklenecek external queue/worker ve egress | Web + background worker + queue/health/drain |
| Transaction/connection | Pooler, TLS, connection limits, retry, region latency, transaction/lock evidence | `mandatory`; mismatch `DEPLOYMENT_HELD` | Edge/shared pool/session-state varsayımları | Cross-provider network/egress/pooler/latency |
| Protected product audit | Primary custody, independent fallback/floor, append-only evidence, retention/legal hold, gap/fork/replay | `mandatory`; `AUDIT_HELD` | Provider logs/fallback aynı domain'de kalabilir | Audit sink, log drain ve second account koordinasyonu |
| Runtime observability | Logs/metrics/traces, correlation, retention, sampling, alert/paging, evidence export | `mandatory`; gap `UNKNOWN/HELD` | Platform log limits/retention ve cap dışı drain | Web/worker/deploy stream korelasyonu ve storage |
| Object safety plane | Quarantine, scanner/URL fetch, digest/lineage/classification, derivative, orphan cleanup, scoped handle | `mandatory`; active handle yok | Storage backup, scanner ve resumable lifecycle ayrışması | Worker/queue/temporary storage/egress koordinasyonu |
| Object backup/restore | Bytes + metadata + version + classification + digest, restore quarantine, clean-room import | `mandatory`; old negative state dirilmez | DB backup'ın object/audit/floor'u kapsamaması | DB/object/runtime/audit ayrı restore ve verification |
| Deploy/release | Immutable artifact, build/registry, release ID, schema/message generation, migration runner, drain/forward recovery | `mandatory`; mismatch `DEPLOYMENT_HELD` | Function revision DB/object/queue rollback değildir | Web/worker/config/image/health rollback ayrışır |
| Provider/account/billing | Legal owner, payment, plan, quota, hard cap scope, overage, account lock/closure, support escalation | `mandatory`; `ACCOUNT_HELD/BILLING_HELD` | Tek provider common-mode ve cap dışı kalemler | İkinci account/billing/support/credential yüzeyi |
| Domain/network/notification | DNS/TLS/cert, custom domain, SMTP/sender/abuse, notification/SMS gerekiyorsa country/fraud cost | Capability-dependent; failure positive hold | Provider custom-domain/SMTP limitleri | API/runtime/core provider arasında DNS/TLS/egress |
| Incident capacity | Retry spike, duplicate safe capacity, temporary quarantine/audit/object/log storage, support/escalation | `mandatory reserve`; cost stop | Common-mode outage ve temporary independent path | Partial health, multiple incident/support tickets |
| Restore drill | Isolated environment, reviewer, import/verification, downtime/read-only, quarantine cleanup | `mandatory`; `RESTORE_QUARANTINE` | Managed backup planesi eksik olabilir | DB/object/queue/artifact/config/runtime ayrı import |
| Clean-room exit | Logical export/import, identity/principal, operations, audit/floor, object, package, queue, artifact/config, DNS cutover | `mandatory`; `EXPORT_PARTIAL` | Edge/Auth/Storage/management semantics adapter'ı | Provider queue/worker/health/config/support semantics |
| Secret/key operations | Scoped secrets, rotation, old runtime drain, in-flight invalidation, reissue, no raw secret logs | `mandatory`; leak sonrası hold | Project secret blast radius | DB/object/queue/runtime/second account key seti |
| Support/recovery people | Provider support plan, escalation/SLA, independent audit/floor custodian, recovery verifier, last-admin route | `mandatory external dependency`; yoksa `HELD` | Tek zincirin common-mode oluşu | İki veya daha fazla zincirin mapping/recovery yükü |
| AI task operations | Task pack, allowed/forbidden scope, credential class, evidence, reviewer, validator, owner handoff | `mandatory`; forbidden scope `REJECT` | Provider-specific function/admin context | Service-by-service secret/context collision |

Not: `deferrable` veya `optional` etiketi yalnız convenience capability için kullanılabilir. Safety, privacy, protected
audit, data continuity, owner-operability ve clean-room exit için gerekli satırlar convenience diye ertelenemez.

## 8. A/B eşit kabul paketi ve geçiş tetikleyicileri

### 8.1 Her iki aday için aynı minimum kabul paketi

1. Commit öncesi/sonrası timeout, process kill, response loss, same/different fingerprint retry ve canonical status
   lookup; duplicate effect yok.
2. Stale session/role/epoch, cross-tenant direct path, direct DB/RPC/Storage, signed handle ve provider console
   bypass negative testleri.
3. Publish/approval ile newer recall/suspension yarışında negative generation wins; protected ordered audit korunuyor.
4. DB/outbox/queue/object mismatch, duplicate/poison/DLQ, worker kill/restart, lease/heartbeat, retry storm ve
   backpressure; accepted operation ile delivery/consumer reconciliation ayrılıyor.
5. Audit primary/fallback outage, gap/fork/replay, log retention/export/legal hold ve effect-before-audit negative.
6. Object incomplete/digest mismatch/quarantine/classification/lineage/handle revoke; downloaded-copy residual risk.
7. Deploy health failure, old/new runtime drain, schema/message compatibility, secret rotation ve forward migration;
   code rollback'un data rollback olmadığı gösteriliyor.
8. Provider/region/DNS/account/billing/quota/support outage; safe read, positive hold, emergency negative availability,
   accepted history/pending preservation, owner-readable cost stop ve external escalation.
9. Restore/failover isolated quarantine, cross-plane manifest, no-resurrection, source untouched until acceptance ve
   old revoke/recall/delete/suspension/accepted operation'ın geri gelmediği kanıt.
10. Clean-room runtime/provider import; principal/identity/policy/object/audit/floor/package/ledger/queue/artifact/
    config/secret/DNS continuity; `EXPORT_PARTIAL` source protection.
11. Normal, incident, restore ve exit ayları için aynı normalized BOM; official plan/region/usage/tax/FX/support,
    cap/overage/stop action ve TRY ceiling karşılaştırması. Bu review sayısal maliyet hesaplamaz.
12. One end-to-end AI task pack; forbidden credential check; independent validator/reviewer; owner only plain-language
    decision/support/payment/legal actions.

### 8.2 A'dan B'ye geçiş için önceden tanımlı tetikleyiciler

Aşağıdaki bir sonuç gerçek, eşit fixture ile kanıtlanırsa A zorlanmamalı; B ancak aynı paketin tamamını geçerse öne
alınmalıdır:

- gerekli kısa request veya dependency Edge memory/CPU/wall-clock/idle/package/runtime sınırına güvenli margin ile
  sığmıyor;
- required library/runtime desteği kararlı değil, provider drift ile tekrar tekrar kırılıyor veya function deployment
  /secret rotation / old revision drain güvenli kapanmıyor;
- A'nın gerekli queue/worker/observability/audit/fallback adjunctları B'nin eşdeğer bileşiminden daha karmaşık,
  daha pahalı veya owner-operability açısından daha riskli hale geliyor;
- Supabase common failure domain'i protected audit/floor, emergency negative, recovery veya outage safe-stop hedefini
  karşılamıyor;
- Edge connection/pooler/transaction davranışı commit-time authorization, idempotency, outbox veya audit evidence'ını
  geçmiyor;
- A deploy/schema/message compatibility, secret rotation veya no-owner-debug fixture'ında hard-fail veriyor;
- normalized normal + incident + restore + exit BOM'unda A'nın zorunlu güvence maliyeti B'den anlamlı biçimde kötü
  çıkıyor; headline runtime fiyatı yeterli değildir;
- clean-room replacement yalnız provider-specific Edge/management/queue semantics nedeniyle tamamlanamıyor.

“B öne alındı” kararı ancak B aynı API-AC, 16 failure, owner, cost, restore ve exit gates'ini `PASS`/kanıtla geçerse
verilebilir. A'nın bir hard-fail'i B için muafiyet yaratmaz.

### 8.3 B'nin otomatik fallback olmadığını doğrulayan tetikleyiciler

B şu durumlarda otomatik seçilmez; konu `HELD` kalır ve gerekirse Cloud Run/Workers veya başka challenger aynı fixture ile
yeniden açılır:

- ikinci account/billing/support hattı owner'a teknik koordinasyon veya iki farklı emergency recovery gerektiriyor;
- cross-provider TLS/network/pooler/egress/latency transaction, idempotency veya audit-before-effect'i belirsiz bırakıyor;
- web + worker + queue + log/audit/fallback minimum cost'u cap/stop olmadan taşınıyor;
- deploy health green olsa da worker drain, schema/message compatibility, queue replay veya DB forward recovery
  kapanmıyor;
- container image taşınsa da managed queue/worker/config/health/audit/floor/identity semantics clean-room'da yeniden
  kurulup doğrulanamıyor;
- provider/region/DNS/billing/account outage'ında owner SQL/SSH/queue surgery/support bypass'a zorlanıyor;
- normalized incident/restore/exit maliyeti veya external human/support bağımlılığı owner bütçesi ve availability'siyle
  açıklanabilir değil.

### 8.4 Her iki aday da geçmezse

A ve B aynı mandatory gate'lerden geçemezse “en az kötü olanı seç” sonucu çıkarılamaz. İlgili capability `HELD`, positive
effect kapalı, accepted/history/pending work korunmuş ve challenger yeniden açılabilir durumda tutulur. Safety, privacy,
audit, recovery, no-owner-debug veya exit standardı maliyet/kolaylık için düşürülemez.

## 9. Manager proposal'a düzeltilmiş etki

1. A, yalnız kısa DB-yakın API için geri alınabilir Phase-4 çalışma adayı olarak tutulabilir; bu üretim kazananı veya
   satın alma izni değildir.
2. B, önceden tanımlı runtime fallback adayı olarak tutulabilir; ikinci provider/account/worker/queue yüzeyi BOM ve
   support/recovery matrix'inde görünmeden “hazır fallback” sayılamaz.
3. Long-job capability “ihtiyaçta eklenir” diye operation/retry/lease/message/deploy/restore contract'ından ayrılmaz;
   ihtiyaç doğduğu anda yeniden mimari tartışma açmamak için semantic boundary ve acceptance şimdiden yazılır.
4. Protected audit/floor ve emergency-negative failure-domain kararı Phase-4 handoff'unun dışında bırakılamaz; exact
   teknoloji sonraki evidence gate'inde açık kalabilir, fakat minimum safe outcome ve hold state şimdi bağlanmalıdır.
5. Cost BOM sadece shared core + API + queue değildir; support, account, incident, restore, exit, object/audit/
   monitoring, network/egress, domain/SMTP ve external human dependency'yi taşır.
6. Owner-readable state, AI task-pack, provider support/escalation ve clean-room source-protection kanıtı yoksa A/B'nin
   hiçbirinde positive production activation önerilemez.

## 10. Son disposition

**Manager proposal:** `HELD_WITH_REQUIRED_CHANGES / NO WINNER`  
**Aday A:** `HELD — 0 PASS / 16 HELD / 0 REJECT`  
**Aday B:** `HELD — 0 PASS / 16 HELD / 0 REJECT`  
**Bulgu sayısı:** `5 CRITICAL / 9 MAJOR / 4 MINOR`  
**Capability hard-fail:** Yukarıdaki `REJECT-IF-UNMITIGATED` koşulları uygulanır; bu review tüm adayları bugün topyekûn
reject etmez çünkü çalışma no-code/documentary aşamadadır ve güvenli hold yolu teorik olarak tanımlanabilir.

Bu hüküm `DEC-0035` managed Supabase-centered Phase-4 working direction'ını veya `DEC-0037` identity/no-owner-debug
kurallarını değiştirmez. Consumer/Auth çalışma yönü provider seçimi değildir; privileged/high-consequence runtime
production activation'ı hâlâ evidence gate'ine bağlıdır. A/B için provider hesabı, plan, ödeme, code/prototype,
deployment, ADR veya Gate 4 -> 5 geçişi yoktur.

## 11. Kapanış için gereken minimum teslimler

- A/B ortak 16 senaryo için candidate-specific failure-domain, owner action, support, cost, exit ve reject cue matrisi;
- owner/provider/account/billing/support/last-admin/outage no-code tabletop ve no-owner-debug runbook;
- long-job queue/worker/lease/retry/DLQ/backpressure/shutdown/message-compatibility fixture;
- deploy/secret/schema/object/audit/floor compatibility ve forward-recovery fixture;
- normal/incident/restore/exit normalized BOM; hidden adjunct, tax/FX, cap/overage, support ve temporary environment;
- protected audit/fallback/floor, object quarantine/backup, restore quarantine ve anti-resurrection evidence planı;
- isolated clean-room export/import, source untouched, secret reissue, DNS cutover, old-runtime drain ve decommission;
- task-scoped AI execution pack, forbidden credential check, independent reviewer/validator ve plain-language handoff;
- A/B eşit bağımsız security/recovery ve owner/TCO/operability review'ları tamamlanmadan ADR veya production gate yok.

**Nihai karar:** `HELD / NO WINNER / A ve B'ye eşit kanıt kapısı / capability-level REJECT-IF-UNMITIGATED`.

