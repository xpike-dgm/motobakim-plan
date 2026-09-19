# DEBATE-011 — Kavriva API Runtime, Sınır Uygulama ve Operasyon Yönetici Önerisi

Status: `REVIEWED MANAGER PROPOSAL / CORRECTED JUDGE DIRECTION USER-APPROVED VIA DEC-0038 / NO WINNER / ADR NOT READY`
Date: `2026-09-19`
Scope: `NO-CODE / NO ACCOUNT / NO PURCHASE / GATE 4 -> 5 CLOSED`

## 1. Teknik olmayan kısa anlatım

Kavriva'nın telefon ve şirket içi tarayıcı uygulamaları veriyi doğrudan değiştirmeyecek. Arada, her isteğin gerçekten
yetkili olup olmadığını son anda kontrol eden, işlemi yalnız bir kez uygulayan ve sonucu kanıtıyla birlikte kaydeden bir
Kavriva API kapısı olacak. İnternet cevabı kaybolursa sistem işlemi yeniden körlemesine yapmayacak; aynı işlem numarasıyla
sonucu araştıracak ve gerekirse `SONUÇ BELİRSİZ` diyecek.

Bu kapının nerede çalışacağı için iki gerçekçi yol kaldı:

- **Aday A:** Supabase'e yakın Edge Functions üzerinde kısa API işlemleri; uzun işler yalnız gerektiğinde dayanıklı
  kuyruk ve ayrı işleyiciye verilir.
- **Aday B:** Supabase'ten ayrı, yönetilen bir container hizmetinde API; uzun işler ayrı worker/kuyrukta çalışır.

Aday A başlangıçta daha az hizmet ve daha düşük işletim yükü vaat eder. Aday B çalışma süresi ve taşınabilirlikte daha
fazla kontrol verir, fakat ikinci sağlayıcıyı, ikinci arıza/fatura yüzeyini ve daha fazla kurulum işini getirir. Bu nedenle
öneri bugün bir ürün satın almak değil; Aday A'yı geri alınabilir başlangıç yönü, Aday B'yi önceden tanımlı geçiş yolu
olarak tutmak ve ikisini aynı gerçek arıza senaryolarıyla sınamaktır.

## 2. Karar sınırı

Bu öneri şunları yapar:

- API'nin ürün içindeki görevini ve değişmez güvenlik sözleşmesini tanımlar;
- kısa istek ile uzun arka plan işini ayırır;
- iki finalist mimariyi eşit kapsamda karşılaştırır;
- Cloudflare Workers, Cloud Run ve self-managed seçeneklerin neden finalist veya referans olduğunu açıklar;
- maliyet, arıza, kurtarma, çıkış ve teknik olmayan owner koşullarını bağlar;
- Phase 5'te aranacak gerçek kanıtı tanımlar.

Bu öneri şunları yapmaz:

- runtime, dil, framework, region, plan, kuyruk veya worker ürünü seçmez;
- Supabase, Render, Cloudflare veya Google hesabı açmaz;
- ücretli plan, domain, log/audit ürünü veya destek satın almaz;
- kod, prototype, executable spike, migration veya deployment üretmez;
- ADR oluşturmaz veya Gate 4 -> 5'i açmaz.

## 3. Devralınan bağlayıcı yönler

- `DEC-0034`: hassas erişim API aracılıdır; Internal Operations online-authoritative'dir; restore/exit bütün veri
  düzlemlerini kapsar.
- `DEC-0035`: Supabase-centered backend geri alınabilir Phase-4 yönüdür; API zorunludur; RLS ve Storage policy yalnız
  defense-in-depth'tir; modüler managed composition ilk fallback'tir.
- `DEC-0036`: Flutter seçili görev paketleri ve dayanıklı operation ledger kullanır; HTTP başarısı canonical kabul
  değildir.
- `DEC-0037`: authentication yetki değildir; current session/security epoch ve ürün yetkisi commit anında kontrol
  edilir; protected audit ve end-to-end revoke zorunludur.
- `DEC-0029/0030/0032`: proje AI-operated ve teknik olmayan tek owner içindir; SQL/SSH/debug beklenmez; TRY 2.000–3.000
  aylık tutar ilerideki planlama tavanıdır, bugünkü ödeme izni değildir.

## 4. İki adayda da değişmeyecek Kavriva API sözleşmesi

### 4.1 API ince ve durumsuz giriş kapısıdır

API runtime ürün verisinin kalıcı sahibi değildir. Canonical durum, işlem kaydı, version/generation, güvenlik epoch'u ve
audit ilişkisi Postgres merkezli authoritative kayıtta korunur. Runtime instance'ı kapanabilir veya değişebilir; başka
bir instance aynı operation identity üzerinden güvenli şekilde devam edebilmelidir.

### 4.2 Kritik işlem tek authoritative bütün olarak sonuçlanır

High-consequence işlemde aşağıdakiler birbirinden kopuk client çağrıları olamaz:

1. current actor/session/epoch/action/resource/scope/yetki kontrolü;
2. stable `operation_id` ve payload fingerprint kabulü;
3. expected version/generation ve newer negative floor kontrolü;
4. canonical değişiklik;
5. protected audit intent/event ve canonical sonuç bağlantısı;
6. dış yan etkiler için idempotent outbox/queue kaydı.

Bu çekirdek aynı authoritative DB transaction/constraint sınırında bağlanır. Object, bildirim, tarama, AI/OCR veya başka
sağlayıcı çağrısı transaction içinde başarı varsayılmaz; outbox/kuyruk üzerinden tekrar güvenli işlenir.

### 4.3 Sonucu kaybolan istek yeniden tahmin edilmez

Commit'ten önce veya sonra bağlantı kopabilir. Client aynı operation kimliğiyle status lookup yapar. Sonuç kanıtlanana
kadar `OUTCOME_UNKNOWN` kalabilir. Yeni operation oluşturan kör retry yasaktır. Aynı kimlik ve aynı fingerprint mevcut
sonucu döndürür; farklı fingerprint `CONFLICT/HELD` olur.

### 4.4 Doğrudan provider yolları ürün kapısını atlayamaz

Flutter/browser high-consequence işlem için generic Data API, RPC, view/function, Storage, signed URL veya provider
console kullanamaz. RLS/Storage grant'leri ayrıca dar tutulur. `service_role`, provider owner, unrestricted SQL/SSH ve
global object credential client'a, repository'ye, log'a veya sıradan AI görevine verilmez.

DB function gerekiyorsa yalnız transaction boundary için dar tutulur: exposed schema dışında, açık actor/scope/epoch
kontrolüyle ve public execute kapalı olarak tasarlanması sonraki evidence gate'idir. `SECURITY DEFINER` tek başına güvenli
veya yetkili sayılmaz.

### 4.5 Kısa request ve uzun iş ayrıdır

Senkron API yalnız doğrulama ve kısa transactional command/status/read işlerini yapar. Package üretimi, object tarama,
preview/derivative, büyük export, AI/OCR, bildirim ve geniş reconciliation dayanıklı kuyruk/worker işidir. Function
background callback veya `waitUntil`, worker lifetime sınırına tabi olduğundan dayanıklı kuyruk yerine geçmez.

Queue'nun mesajı bir kez claim ettiğini söylemesi, ürün effect'inin yalnız bir kez gerçekleştiğini kanıtlamaz. Consumer
her zaman operation ledger, fingerprint, lease, retry budget ve idempotent effect kullanır.

### 4.6 Runtime log'u protected product audit değildir

Log/metric teknik teşhis içindir. Approval, publish, recall, role, recovery, export ve delete kanıtı ayrı protected product
audit'tir. Audit-before-effect veya eşdeğer transactional güvence yoksa positive effect `AUDIT_HELD` olur. Primary audit
custody kesildiğinde bağımsız fallback ve sonra reconciliation gereklidir.

### 4.7 Rollback yalnız kodu geri çevirebilir

Runtime revision rollback, database schema/data, queue message, object, audit veya negative floor'u geri alamaz.
Database için expand/contract uyumluluk ve forward recovery; runtime için version/release fence gerekir. Restore önce
`RESTORE_QUARANTINE` durumuna gelir ve revoke/recall/delete/accepted-operation dirilmediği kanıtlanmadan açılmaz.

## 5. Aday A — Supabase'e yakın bounded API runtime

### 5.1 Bileşim

- kısa Kavriva API request'leri için Supabase Edge Functions;
- authoritative Postgres transaction/operation ledger;
- Supabase Auth yalnız identity/session input'u, Kavriva API current authorization owner'ı;
- private Storage'a API-issued scoped object handle;
- uzun iş gerçekten doğduğunda durable queue + bounded worker;
- protected audit/floor ve object backup için production öncesi bağımsızlık kanıtı.

Queue veya worker'ın exact ürünü bu öneride seçilmez. Supabase Queues bir aday primitive'dir; Edge background task tek
başına durable worker kabul edilmez.

### 5.2 Güçlü taraflar

- API ile database aynı ana platform/region çevresinde tutulabilir; DB-heavy kısa işlemlerde daha az ağ ve credential
  koordinasyonu beklenir.
- İlk dönemde ayrı sürekli çalışan API sunucusu gerektirmeyebilir; tek owner için daha dar control plane sağlar.
- Supabase Auth/DB/Storage yönüyle uyumludur ve ilk trafik seviyesinde kullanım tabanlı maliyet daha sade olabilir.
- Geri alınabilir tutulursa ayrı container API'ye geçiş için aynı provider-neutral contract kullanılabilir.

### 5.3 Zayıf taraflar ve hard hold'lar

- Function memory, CPU, wall-clock, idle, package ve log sınırları uzun/ağır işi aynı yerde tutmaya uygun değildir.
- DB/Auth/Storage/Functions aynı provider failure domain'inde yoğunlaşır; bağımsız emergency-negative ve audit/floor
  ihtiyacı ortadan kalkmaz.
- Gateway JWT kontrolü current session, security epoch ve product authorization yerine geçmez.
- Edge/shared transaction pooling kısıtları, prepared/session-state varsayımları ve connection davranışı ayrıca
  kanıtlanmalıdır.
- Deno/Edge runtime bağımlılık uyumu, deploy/revision, secret rotation ve provider limit drift'i izlenmelidir.
- Function invocation fiyatı düşük görünse bile queue/worker, audit, object backup, monitoring, restore ve exit maliyeti
  headline'a dahil değildir.

## 6. Aday B — Bağımsız managed container API + worker

### 6.1 Bileşim

- yönetilen bir container web service üzerinde Kavriva API;
- ayrı bounded background worker ve durable queue;
- Supabase PostgreSQL/Auth/private Storage çekirdeğine server-side bağlantı;
- aynı authoritative transaction/operation ledger;
- aynı protected audit/floor, object backup ve clean-room exit gereksinimleri.

Render bu karşılaştırmada somut düşük-operasyon temsilcisidir. Cloud Run portability/scale-to-zero karşılaştırma
referansıdır; bu belge Render veya Cloud Run seçmez.

### 6.2 Güçlü taraflar

- Runtime, dil/library ve process yaşam süresi üzerinde daha fazla kontrol; ağır veya uzun worker'ı API request'inden
  açıkça ayırma kolaylığı.
- Container artifact başka managed container hizmetine taşınabilir; runtime-provider exit yolu daha görünürdür.
- Health check, revision/deploy ve worker gibi sınırlar ayrı işletim yüzeyi olarak görülebilir.
- Supabase Functions sınırları ihtiyaçları karşılamazsa aynı API contract'ı korunarak geçiş yolu sağlar.

### 6.3 Zayıf taraflar ve hard hold'lar

- İkinci provider/account/billing/outage/support ve secret yüzeyi oluşur.
- Supabase DB/Auth/Storage ile API arasında ağ, region, TLS, pooler, egress ve latency yanlış yapılandırma riski vardır.
- Web service + worker + queue + logs/monitoring birlikte ücretlenebilir; düşük web-service etiketi toplam maliyet değildir.
- Container health green olması database transaction, audit, queue veya product truth'in sağlıklı olduğunu kanıtlamaz.
- Scale-to-zero/cold start, graceful shutdown, in-flight request/worker drain ve schema/message compatibility ayrıca
  sınanmalıdır.
- Teknik olmayan owner'ın deploy, queue veya log tamiri yapması gerekirse bu aday managed görünse bile kabul edilmez.

## 7. Diğer adayların konumu

### 7.1 Cloudflare Workers — challenger, otomatik core API değil

Global edge, düşük başlangıç tabanı ve fail-closed route yetenekleri değerlidir. Ancak Kavriva'nın çekirdek istekleri
çoğunlukla Frankfurt'taki canonical DB'ye current authorization ve transaction için ulaşacaktır. Edge'e dağıtmak DB
otoritesini dağıtmaz; ek uzak ağ, custom auth/DB adapter, Queue/Workflow ve log/audit ayrımı getirir. Bu nedenle Workers:

- bağımsız dar emergency-negative/gateway yolunda;
- ileride gerçekten global, cacheable veya edge-uygun workload oluştuğunda;
- ya da A/B gerçek kanıtta yetersiz kalırsa

yeniden değerlendirilir. Şimdilik core DB-heavy API finalisti değildir.

### 7.2 Google Cloud Run — container portability referansı

Cloud Run arbitrary container, revision, concurrency ve scale-to-zero açısından güçlü karşılaştırmadır. Fakat GCP IAM,
region/network, billing, log/monitoring ve daha geniş control-plane'i tek teknik olmayan owner için ek işletim yükü
getirebilir. Aday B kanıtında Render sınırları yetersiz kalırsa veya taşınabilirlik/ölçek gereksinimi doğarsa eşit
fixture ile değerlendirilir; bugün ayrı üçüncü finalist değildir.

### 7.3 Self-managed VM/container — maliyet referansı, başlangıç adayı değil

Düşük VM etiketi patch, CVE, firewall, secret, backup, restore, failover, monitoring ve on-call maliyetini içermez. Owner
SQL/SSH/debug yapmayacağı için bu işlerin güvenli, kanıtlı ve owner-independent şekilde managed/AI-operated olmadığı her
durum `REJECT-IF-UNMITIGATED`tir. Ucuz otomatik fallback sayılmaz.

## 8. Eşit no-code senaryo sonucu

Bu tablo mekanizma ve plan walkthrough sonucudur; üretim `PASS` değildir.

| Senaryo | Aday A — Edge | Aday B — Container | Ortak kabul sonucu |
|---|---|---|---|
| Commit sonrası cevap kaybı | `HELD` | `HELD` | Aynı operation ile lookup; `OUTCOME_UNKNOWN`; duplicate effect yok |
| Aynı/farklı payload retry | `HELD` | `HELD` | DB unique ledger; aynı fingerprint mevcut sonuç, farklısı conflict |
| Stale token/rol/sekme | `HELD` | `HELD` | Current session + epoch + authorization commit anında |
| Publish ile newer recall yarışı | `HELD` | `HELD` | Generation fence; negative wins; ordered protected audit |
| DB commit / queue veya object kesintisi | `HELD` | `HELD` | Transactional outbox + idempotent worker + reconcile |
| Audit sink kesintisi | `HELD` | `HELD` | Protected fallback yoksa positive effect `AUDIT_HELD` |
| Uzun işte runtime kapanması | `HELD` | `HELD` | Durable queue, lease, heartbeat, retry budget, DLQ |
| Secret sızıntısı/rotasyon | `HELD` | `HELD` | Dar blast radius, versioned rotation, epoch/reconcile |
| Deploy ve DB schema ayrışması | `HELD` | `HELD` | Compatibility fence + forward recovery; DB rollback varsayılmaz |
| Provider/region/DNS outage | `HELD` | `HELD` | Positive hold; safe read/recovery; independent negative path |
| Billing/quota kısıtı | `HELD` | `HELD` | Owner-readable `BILLING_HELD`; accepted/history korunur |
| Eski backup restore | `HELD` | `HELD` | Quarantine + negative floor + anti-resurrection |
| Clean-room runtime/provider exit | `HELD` | `HELD` | Logical export/import + object/audit/identity/ledger/floor doğrulaması |
| Owner incident işletimi | `HELD` | `HELD` | SQL/SSH/log/queue surgery yok; anlaşılır safe next action |
| AI task yürütmesi | `HELD` | `HELD` | Narrow credential, forbidden scope, evidence + reviewer |
| Safe total cost | `HELD` | `HELD` | Normal/incident/restore/exit BOM; hard-stop ve TRY karşılığı |

Belgesel sonuç: iki aday da `0 PASS / 16 HELD / 0 REJECT`. Bu eşitlik iki adayın aynı olduğu anlamına gelmez; gerçek
fixture ve toplam maliyet henüz yokken birini production-ready ilan etmenin yanlış olduğunu gösterir.

## 9. Yönetici önerisi — Koşullu A, önceden tanımlı B geçişi

Phase 4 çalışma yönü olarak:

1. **İnce API:** Kavriva API stateless/replaceable ingress, authorization ve effect-protocol katmanı olur; persistent
   truth Postgres merkezli authoritative kayıttadır.
2. **Başlangıç adayı:** Supabase Edge Functions yalnız kısa DB-yakın request'ler için geri alınabilir liderdir.
3. **Uzun işler:** İlk günden boş bir mikroservis ağı kurulmaz; ancak bilinen long-job ailelerinin semantic contract'ı
   şimdiden bağlanır. İlgili capability açılmadan durable queue + bounded worker gerekir; function background task
   kuyruk sayılmaz.
4. **Geçiş adayı:** Managed container API + worker, Edge limitleri, bağımlılık uyumu, failure-domain, işletim veya maliyet
   kapısını geçemezse ilk runtime fallback'idir.
5. **Provider-neutral core:** Operation/authorization/audit/object/package/recovery contract Edge SDK'sına gömülmez.
6. **Tek transaction:** High-consequence canonical mutation, authorization generation, operation ledger, audit intent
   ve outbox aynı DB assurance sınırında bağlanır.
7. **Bağımsız güvenlik:** Protected audit/floor ve emergency-negative yolunun minimum safe behavior/failure-domain
   sözleşmesi şimdi bağlanır; exact teknoloji ve topoloji sonraki eşit evidence gate'inde kapanır.
8. **No-owner-debug:** Her iki aday da owner'a yalnız anlaşılır karar/hold/escalation verir; SQL/SSH/queue repair gizli
   işletim modeli olamaz.

Bu yön Aday A'yı üretim kazananı, Supabase Queues'i seçilmiş ürün veya Render'ı satın alınmış fallback yapmaz.

## 10. A'dan B'ye geçiş tetikleyicileri

Aşağıdakilerden biri gerçek fixture ile doğrulanırsa Aday A zorlanmaz; Aday B eşit kanıtla öne alınır:

- gerekli request veya dependency Edge memory/CPU/wall-clock/package/runtime sınırına güvenli biçimde sığmıyor;
- gerekli library/runtime desteği güvenilir değil veya provider değişikliğiyle tekrar tekrar kırılıyor;
- durable worker/queue ve observability ekleri Edge yaklaşımını container'dan daha karmaşık/pahalı yapıyor;
- Supabase ortak failure-domain'i protected audit/negative path/recovery hedefini karşılamıyor;
- DB connection/pooler/transaction davranışı idempotency ve commit-time authorization kanıtını geçmiyor;
- deploy/secret rotation/schema compatibility/no-owner-debug fixture'ı başarısız;
- normalize normal + incident + restore + exit maliyeti container seçeneğinden anlamlı biçimde kötü;
- clean-room runtime replacement yalnız provider-specific Edge davranışı nedeniyle kapanmıyor.

B de otomatik kazanmaz. İkinci provider koordinasyonu, ağ/pooling, worker/queue, billing veya owner-operability fixture'ı
başarısızsa konu `HELD` kalır ve Cloud Run/Workers gibi challenger'lar aynı kapsamla yeniden açılır.

## 11. Owner-readable maliyet kapısı

Satın alma/ADR öncesi iki aday aynı BOM'u taşır:

- shared Supabase plan/compute/Auth/DB/Storage/egress;
- API invocation veya container instance;
- durable queue ve background worker;
- protected product audit, independent fallback/floor ve log drain;
- object quarantine/scan/backup/restore;
- monitoring, alert, DNS/domain, support/escalation;
- normal, incident, restore drill ve clean-room exit ayı;
- vergi, kur, kart/komisyon, quota/overage ve hard-stop davranışı.

Her kalem `mandatory / deferrable / optional / scale-triggered` olur. TRY 2.000–3.000/ay gelecekteki tavan, bugün satın
alma izni değildir. Güvenlik veya recovery bütçeye sığmıyorsa daha zayıf moda sessizce geçilmez; capability
`BILLING_HELD/HELD` kalır.

## 12. Phase 5 gerçek kabul paketi

- timeout-before/after-commit, same/different fingerprint retry ve canonical status lookup;
- stale JWT/session/role/epoch, cross-tenant ID ve direct DB/RPC/Storage negative tests;
- publish/approval vs recall/suspension yarışında negative generation kazanması;
- DB transaction/outbox, queue duplicate/poison/DLQ, worker kill/restart ve backpressure;
- audit primary/fallback outage, gap/fork/replay ve effect-before-audit negative test;
- object incomplete/digest mismatch/quarantine/classification/lineage/handle revoke;
- deploy rollback + forward DB recovery + old/new request/message compatibility;
- secret leak/rotation, in-flight operation ve old runtime drain;
- provider/region/DNS/billing/quota outage ve owner-readable safe hold;
- clean-room restore/exit, no-resurrection ve source untouched until acceptance;
- Android/browser operation/recovery/accessibility walkthrough;
- normalized safe BOM, current official price/plan/region/tax/FX ve cost stop;
- one end-to-end AI task pack, forbidden credential check ve independent validation;
- independent security/recovery ve owner/TCO/operability reviews.

## 13. Kullanıcı onayından sonra kayda geçebilecek yön

Kullanıcı bağımsız review düzeltmeleriyle birlikte onaylarsa yalnız şu Phase-4 yönü bağlanabilir:

- kısa DB-yakın API için Supabase Edge Functions geri alınabilir lider çalışma adayı;
- persistent authority ve operation/audit/outbox DB assurance sınırında;
- uzun işler için yalnız ihtiyaç doğduğunda durable queue + bounded worker;
- managed container API + worker ilk önceden tanımlı runtime fallback'i;
- direct provider bypass yok, protected audit/negative path/restore/exit ayrıca kapanacak;
- iki aday için no-owner-debug ve normalized safe-cost hard gate.

Onay; runtime/framework/dil/queue/worker/provider/region/plan seçimi, hesap, ödeme, kod, prototype, deployment, ADR veya
Gate 4 -> 5 geçişi değildir.
