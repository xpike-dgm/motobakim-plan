# DEBATE-008 — Independent Security, Recovery and Provider-Exit Review

Status: HELD — INDEPENDENT NO-CODE ADJUDICATION / NO FINAL WINNER / ADR NOT READY  
Date: 2026-09-18 (Europe/Istanbul)  
Scope: Candidate A — managed Supabase composition; Candidate B — Neon managed PostgreSQL + Render Web Service
independent API + Cloudflare R2

## 1. Hakemlik kapsamı ve kanıt tabanı

Bu dosya iki finalist dosyasını güvenlik, veri sürekliliği, restore, clean-room exit, provider/account/billing failure
ve F01-F16 ortak fixture senaryoları açısından bağımsız olarak karşılaştırır. Entegrasyon kolaylığı güvenlik kanıtı,
modülerlik de otomatik güvenlik kanıtı sayılmamıştır.

Okunan kanıt tabanı:

- DEBATE-008__FINALIST_COMMON_FIXTURE.md
- DEBATE-008__FINALIST_A_SUPABASE.md
- DEBATE-008__FINALIST_B_MODULAR_MANAGED.md
- DEBATE-008__EXTERNAL_REPORT_AUDIT.md
- 00_CONTROL/DECISION_LOG.md içindeki DEC-0034 ve ilgili owner/bütçe/AI kararları
- DEBATE-007__JUDGE_SYNTHESIS.md
- DEBATE-008__STACK_CANDIDATES_COST_PRIMARY_RESEARCH.md
- DEBATE-008__STACK_ARCHITECTURE_FIT_RESEARCH.md

External report audit’in hükmü korunur: bazı ürün mekanizmaları birincil kaynaklarla doğrulanabilir; ancak hard cap,
tam uyum, sıfır lock-in, sıfır hesap-kapanma riski, tam offline güvenliği ve doğrudan provider önerileri rapordan
proje kararı olarak alınamaz. Raporun yanlış veya bağlamdan kopuk kesinlikleri bu hakemliğe kanıt değildir.

Bu review kod, prototip, executable spike veya gerçek restore/penetration test yapmaz; hesap açmaz, satın alma veya
provider seçmez; ADR oluşturmaz ve Gate 4 -> 5’i açmaz. Yalnızca ilerideki no-code evidence pack için disposition,
hard-fail ve kanıt boşluğu üretir.

## 2. Karar dili ve genel hüküm

| Etiket | Bu review’de anlamı |
|---|---|
| CONFIRMED | Resmi/primary kaynakta primitive veya plan davranışı açıkça belgelenmiş |
| INFERRED | Primitive ile DEC-0034 invariant’ından çıkan mimari sonuç; daha sonra evidence gerekir |
| OPEN | Ürün politikasına, seçilmemiş adjunct’a, güncel plana veya kanıta bağlı soru |
| HELD | Güvenli pozitif etki için kritik kanıt eksik; güvenli hold/fallback yolu tasarlanabilir |
| REJECT-IF-UNMITIGATED | Adayın önerilen kullanımı, belirtilen kontrol kapanmadan reddedilir |
| PASS | Common fixture kuralına göre güncel resmi kanıt ve kritik control closure mevcut; gerçek production readiness değildir |

### Genel hüküm

- Candidate A: HELD. Managed Supabase relational ve Flutter entegrasyon primitive’leri sunar; fakat
  service-role/RLS/grant/exposed-schema bypass, DB-Storage ayrılığı, same-project audit/floor ve spend-cap dışı
  kalemler kritik kanıt ister.
- Candidate B: HELD. Bağımsız API, PostgreSQL ve object plane ayrımını daha açık kılar; fakat identity/policy,
  protected audit/floor, quarantine, cross-plane recovery, üçlü billing/outage ve API bakım yükü tamamen
  kanıtlanmış değildir.
- F01-F16’nın hiçbirinde iki aday için documentary PASS verilmez. Bu, iki adayın aynı güvenlik seviyesinde olduğu
  anlamına gelmez; kritik risklerin türü ve telafi yükü farklıdır.
- Reversible Phase-4 working-direction önerisi: Evidence pack sırasını yürütmek için Candidate B, yalnızca
  koşullu ve geri alınabilir bir çalışma yönü olarak öne alınabilir. Bu, modüler olduğu için otomatik güvenli olduğu
  iddiası değildir; API/DB/object sınırını ilk sınıf kanıt konusu yaptığı içindir. B’nin owner-independent bakım,
  audit/floor ve clean-room exit kanıtı kapanmazsa bu yön geri alınır; A otomatik kazanan olmaz.
- Bu öneri provider, plan, hesap, satın alma, ADR veya production approval değildir.

## 3. DEC-0034 ile bağlayıcı ortak security/recovery sınırı

Her iki aday aşağıdaki anlamları korumak zorundadır:

1. Her domain için canonical transactional authority ve stable identity/version/generation sözleşmesi.
2. Flutter ve browser için server/API-mediated sensitive access; client SDK, row ID, cache, provider role veya
   hidden UI button authority değildir.
3. Internal Operations için online-authoritative approval, publication, recall/suspension, role/policy ve
   protected-audit mutation’ları.
4. Seçili motorcycle/task ile sınırlı, machine-verifiable, compact safety/application/safe-stop/recovery package.
5. Durable local operation, idempotent retry, explicit conflict/hold/unknown/device-loss sonucu; yüksek sonuçlu
   veride sessiz LWW yok.
6. Current state, domain history/provenance, protected audit ve object/media state’lerinin ayrı anlamları.
7. Quarantine-first untrusted file/URL ingestion; scan/render/AI/OCR yalnız attributable proposal olur.
8. Release/suspension/security/deletion/accepted-operation/migration için restore edilemeyen monotonic floor.
9. DB, object, audit, identity/policy, config, package ve operation düzlemlerini bağlayan consistency manifest.
10. Restore sonrası quarantine, clean-room import, negative test ve owner-independent recovery.

Bir adayın tek bir ürün dashboard’u, managed SLA’sı, free tier’ı, backup success işareti veya SDK’sı bu sözleşmelerin
tamamını kapatmaz.

## 4. Hassas veri ve server/API authority karşılaştırması

### Ortak zorunlu kontrol

Private motorcycle/history/media, shared/community contribution, official technical claim, operator draft, audit ve
export verisi en kısıtlayıcı classification ile taşınır. Canonical DB/object credential’ı Flutter veya browser’a
verilemez. API commit anında actor, session/security epoch, action, exact scope, state, classification, consequence,
independence ve expected version/generation kontrol eder.

### Candidate A — Supabase

Supabase PostgreSQL, Auth, private Storage ve Functions yüzeylerini tek integrated project görünümünde sunar. Bu,
routine integration’ı azaltabilir; ancak:

- exposed Data API, table grant, RLS, view, RPC ve security-definer function yolları ayrı ayrı sınanmalıdır;
- service-role RLS’i bypass eder; owner, superuser ve bypassrls yolları ürün authorization’ı değildir;
- Storage public bucket veya bearer signed URL, private/classified bytes için publication authority olamaz;
- direct client read/write ancak açıkça düşük riskli ve contract ile sınırlandırılmışsa düşünülebilir; high-consequence
  mutation daima server/API arkasında kalır;
- same-project table/activity/log, actor ile evidence’i birlikte değiştirebiliyorsa protected audit değildir.

A’ya özel hard-fail: RLS veya Storage policy’nin contextual authorization/separation-of-duties yerine konması;
service-role, unrestricted SQL/RPC, exposed internal table veya public/original object yolunun ulaşılabilir kalması.
Bu kontrol kapanmadan ilgili kullanım REJECT-IF-UNMITIGATED’dır.

### Candidate B — Neon + Render API + R2

B’de API boundary kompozisyonun merkezindedir: Flutter/browser yalnız Render Web Service HTTPS contract’ını görür;
Neon connection ve R2 key server/workload identity arkasında kalır. Bu, DEC-0034 sınırını daha görünür kılar; fakat
security kanıtı değildir:

- identity/session/recovery ve contextual authorization provider veya implementation olarak seçilmemiştir;
- Render API’de hata, bypass route, leaked runtime secret veya yanlış policy tüm hassas yolları etkileyebilir;
- Neon owner/superuser/BYPASSRLS ve provider console yolları API policy’sini atlayabilir;
- R2 presigned URL bearer transport’tur; key/digest/generation/expiry bağını API’nin kanıtlaması gerekir;
- ayrı component’ler daha fazla workload identity, secret rotation, release/config ve outage state’i üretir.

B’ye özel hard-fail: bağımsız API’nin pratikte opsiyonel kalması veya DB/object/admin/provider-console path’lerinin
aynı contextual policy, audit ve operation ledger olmadan mutation yapabilmesi. Bu gerçekleşirse B, modüler görünümüne
rağmen önerilen composition olarak REJECT-IF-UNMITIGATED’dır.

### Hakem sonucu

B’nin açık API sınırı daha iyi bir kanıt hipotezidir; A’nın integrated SDK yüzeyi daha düşük başlangıç entegrasyon
hipotezidir. Hiçbiri policy proof değildir. B daha çok operasyon ve maintenance yükü açar; A daha çok integrated
credential/recovery coupling riski açar.

## 5. Privileged bypass ve separation-of-duties karşılaştırması

| Bypass yolu | Candidate A riski | Candidate B riski | Ortak gerekli kanıt |
|---|---|---|---|
| Stale browser role/session | UI ve cached claims authority sanılabilir; server reauth zorunlu | Render API route/server session aynı riski taşır | F01 commit-time reauth, revoked session, fresh step-up ve no-side-effect |
| Admin/service key | Supabase service_role RLS’i bypass eder | Render→Neon/R2 workload key’i veya provider account key’i bypass edebilir | F02 rotation, affected sessions/operations/handles, impact graph ve protected audit |
| DB owner/bypass | PostgreSQL owner/superuser/bypassrls | Neon aynı PostgreSQL bypass semantics’ine sahiptir | Direct DB/migration/restore negative paths; API dışı mutation DENY/HOLD |
| Object credential | Storage service key/public bucket/signed bearer | R2 account key/presigned bearer/list/delete | F04 quarantine, object capability, digest/generation, expiry/replay/delete |
| Function/worker | Edge Function/Realtime delivery authority sanılabilir | Render worker/package/outbox sonucu authority sanılabilir | Workload identity, operation ID, idempotency, no approval/audit substitution |
| Provider console/support | Supabase dashboard/Management API | Neon/Render/R2 consoles and billing/support | Provider admin product approval değildir; legal owner ve AI sınırı |
| Restore/migration | Project restore veya DB role old truth’u açabilir | Neon branch/PITR + Render release + R2 object ayrı restore edilir | Restore quarantine, floor and release-generation recheck |
| Break-glass | Integrated account blast radius | Çoklu account recovery coordination | Narrow, time-bound, attributable, independent review and protected evidence |

Self-approval, role/policy change ile publication, emergency recall ile normal publish veya restore ile current
authority aynı actor/path üzerinden bypass edilemez. İki adayda da competence/independence ayrımı provider permission’ı
ile değil, server policy ve protected evidence ile kurulmalıdır.

## 6. Object quarantine, classification ve protected audit/floor

### 6.1 Object/quarantine

İki adayın object primitive’i yalnız transport/access control düzeyindedir:

- A: Supabase Storage private bucket, RLS ve signed URL; upload/content-type/size kabulü malware quarantine,
  parser isolation veya technical correctness değildir.
- B: R2 private prefix, S3/REST API ve presigned GET/PUT/HEAD/DELETE; strong consistency ve 11-nine durability
  hedefi quarantine, backup, audit immutability veya publication authority değildir. Aynı key’de last-writer-to-complete
  davranışı immutable generation key ihtiyacını artırır.

Her iki aday için zorunlu lifecycle:

1. API creates opaque quarantine identity and expected type/size/classification.
2. Isolated scanner/parser/renderer ve URL egress/SSRF/redirect control.
3. Original/derived digest, generation, classification, owner/scope ve lineage.
4. Scan/render sonucu attributable proposal; approval/publication ayrı guarded transition.
5. Manifest ve audit intent ile DB binding; başarısızlıkta ORPHAN_QUARANTINE.
6. Scoped short-lived serve handle; public/raw URL authority değildir.
7. Delete/withdraw/revoke tombstone; preview, cache, package, export ve backup kopyalarının invalidation/reconcile’i.

Bu scanner, renderer, quarantine network ve observability servisleri iki finalistte de ayrıca görünür olmalıdır.
Integrated BaaS veya modular object store bunları gizli şekilde sağlamış sayılmaz.

### 6.2 Protected audit

Her iki adayın ordinary DB table, provider activity feed, object metadata, timestamp, CDC veya log stream’i tek
başına protected audit değildir. Gerekli evidence:

- ordered attributable event, operation ID, actor/session, scope, policy/version/generation, result ve payload/object digest;
- independent custody veya actor’ın aynı evidence’i silemeyeceği append-only/WORM-equivalent yol;
- checkpoint, fork/sequence-gap detection, fallback ve retention/privacy kuralları;
- normal ve fallback evidence yoksa high-consequence effect HELD.

A için same Supabase project snapshot’ı audit ve canonical state’i birlikte geri sarabilir. B için R2 Object Locking
desteklenmediği belgelenmiş olduğundan R2 tek başına protected WORM floor olamaz; Neon veya Render logları da bağımsız
floor değildir. Her iki aday için ek custody seçimi OPEN’dır.

### 6.3 Non-restorable floor

Floor release/suspension, security epoch, role revocation, deletion/withdrawal tombstone, accepted operation,
migration epoch ve package eligibility/residual-risk generation taşır. Old backup, recall/revoke/delete/replay sonucu
floor ile karşılaştırılmadan authority olamaz. Floor’un aynı ordinary project/account restore’u içinde tutulması ortak
hard-fail’dir.

## 7. Backup, PITR, restore ve anti-resurrection

| Kontrol | Candidate A — managed Supabase | Candidate B — modular managed | Hakem sonucu |
|---|---|---|---|
| DB recovery primitive | PostgreSQL daily DB backup; paid PITR yaklaşık 7/14/28 gün planları ve compute şartı | Neon history/PITR, restore branch/timestamp/LSN ve pg_dump/pg_restore | İki tarafta da DB plane primitive’i CONFIRMED; RPO/RTO/retention approval’da OPEN |
| Object inclusion | Supabase DB backup Storage object bytes’ını kapsamaz | Neon restore R2 object’lerini kapsamaz; R2 durability backup değildir | Cross-plane manifest zorunlu; tek DB recovery REJECT-IF-UNMITIGATED |
| API/runtime/config | Functions, Auth settings/API keys, Realtime settings, extensions ve secrets manual reconfiguration olabilir | Render artifact/config/region/secret mapping ayrı; Web Service deploy/PITR DB restore değildir | Exact immutable release graph ve secret reference backup gerekir |
| Audit/floor | Same project ordinary evidence rollback riski | R2 Object Lock unavailable; independent custody henüz yok | Floor external/independent olmadan iki aday HELD |
| Restore target | Restore/new project inspect edilmeden authority olamaz; deletion/recall reconcile gerekir | Neon branch/new target, R2 object state ve Render artifact ayrı reconcile edilir | RESTORE_QUARANTINE; floor/audit/policy/object/package/operation closure olmadan cutover yok |
| Anti-resurrection | Old project/DB restore recalled Storage/private data/role/accepted op’u diriltebilir | Old Neon PITR + stale R2 object/Render config aynı riski taşır | F08/F09 documentary HELD; drill ve negative tests şart |

### Restore proof’un zorunlu manifesti

Her iki candidate için consistency manifest şunları taşımalıdır:

- canonical sequence, schema/config/migration version;
- current/history/provenance ve operation/idempotency ledger;
- object identity/key, version/generation, digest, classification, lineage ve tombstone;
- protected audit checkpoint ve non-restorable floor;
- identity/role/policy/delegation security epoch;
- release/suspension/revocation ve package dependency closure;
- outbox/notification cursor ve partial/unknown states;
- key references/re-encryption epoch, raw secret olmadan;
- clean-room import, deny/recall/delete/classification/accepted-operation test sonuçları.

Successful backup job, PITR availability, R2 durability veya Supabase/Neon clone bu manifestin yerine geçmez.

## 8. Cross-plane partial/unknown/reconcile güvenliği

İki adayın DB transaction’ı en fazla canonical current/history/idempotency/outbox intent’i aynı transaction’da bağlar.
Aşağıdakiler aynı ACID işlemi değildir:

- object bytes/finalization;
- protected audit custody;
- identity/session/security epoch;
- notification/relay delivery;
- package artifact;
- provider account/billing/region state;
- API deploy/config veya emergency negative authority.

Her operation stable operation ID, payload fingerprint, actor/device/session, expected version/generation taşır.
Durumlar en az PREPARED, COMMITTED, PARTIAL, FAILED, OUTCOME_UNKNOWN, RECONCILING, HELD ve
RESTORE_QUARANTINE olmalıdır. Client timeout başarı veya failure olarak tahmin edilemez; aynı ID ile lookup gerekir.

A farkı: PostgreSQL/Supabase transaction ve outbox primitive’i daha bütünleşik hissedilir; Storage/audit/Functions
ayrı kaldığı için cross-plane iddiası yine yanlıştır.

B farkı: Neon, Render ve R2 fiziksel olarak daha açık ayrı plane’lerdir; partial/unknown state zorunluluğu görünürdür,
ancak daha çok operation relay, credential, monitoring ve incident runbook’u gerekir.

Modülerlik recovery proof değildir; integrated transaction görünümü de recovery proof değildir.

## 9. Clean-room provider exit ve lock-in

### Candidate A

PostgreSQL schema/data/roles ve pg_dump yolu engine-level portability sağlar. Ancak Auth/session, Storage bytes/
metadata/lifecycle, Edge Functions, Realtime, secrets/config, logs/audit/floor ve region/account state ayrı taşınır.
Supabase restore-to-self-host ve restore-to-new-project dokümanlarındaki manual reconfiguration, “DB taşındı =
system exited” iddiasını çürütür.

### Candidate B

PostgreSQL logical export ve R2 S3-compatible object API portability’yi artırır; API’nin HTTP contract’ı da provider
SDK’sından ayrılabilir. Buna karşılık Neon branch/PITR/compute/region, Render deploy/build/secrets/health/logs ve R2
jurisdiction/presigned/cache/lifecycle/billing semantics adapter ister. Identity, audit, scanner, notification ve
observability provider’ları ayrıca exit dossier’e girmelidir.

### Equal clean-room exit test

Normal account dışındaki temiz ortamda:

1. coordinated consistency point veya açık PARTIAL etiketi;
2. DB current/history/roles/policy ve stable IDs;
3. object bytes/metadata/digest/generation/classification/lineage/tombstones;
4. audit sequence/checkpoint/floor ve security epoch;
5. package manifests, cache non-eviction ve offline negative closure;
6. duplicate/unknown/conflict operation reconciliation;
7. wrong-owner, revoked-role, recalled-content, deleted-private-data ve expired-handle deny tests;
8. key re-encryption, provider credential invalidation ve notification/scanner config;
9. independent review ve cutover fence.

kanıtlanmadan exit PASS değildir. A’da relational core portability’si daha olgun görünür; B’de DB/object/API sınırı
exit manifestine daha doğrudan map edilir. İkisinde de lock-in sıfır değildir.

## 10. Provider/account/billing/region outage ve owner-independent recovery

### Candidate A

Tek integrated organization/project control plane basit görünür, ancak aynı account/project outage’u DB, Storage,
Auth, Functions ve management yüzeylerini birlikte etkileyebilir. Supabase Spend Cap yalnız bazı usage item’larını
kapsar; compute, PITR, custom domain, IOPS/throughput, IPv4, log drain ve MFA phone gibi kalemler dışarıda kalabilir.
Free route pause, quota, backup ve log/metrics sınırlamalarını safety proof yapmaz.

Managed OS/database maintenance yükünü azaltabilir; yine de owner’ın dashboard/SQL/SSH ile incident repair yapması
recovery planı olamaz.

### Candidate B

Neon, Render ve R2 ayrı account/billing/region/outage boundaries’idir. Bu, failure isolation ve replacement
seçeneklerini görünür kılabilir; aynı zamanda:

- composite monthly hard cap kanıtlanmamıştır;
- Neon spending limitleri alert ağırlıklıdır;
- Render Web Service workspace/service/bandwidth metering’i genel hard cap değildir;
- R2 direct egress free olsa da storage/Class A/Class B/IA retrieval/orphan/version cost’ları vardır;
- bir provider/account outage API, DB, object veya exit path’lerinden birini kısmi olarak durdurabilir.

B’nin üç hesaplı yapısı otomatik resilience değildir. Account outage sonrası positive work hold, bounded safe-stop/
history/read, independent negative authority ve owner-independent export/recovery ayrı kanıtlanmalıdır.

### Ortak owner modeli

Owner yalnız plain-language approval, legal/account/payment ve açık geri dönüşü olmayan kararları verir. AI:

- provider owner/billing/legal identity, root/superuser, unrestricted SQL/SSH veya global object key alamaz;
- migration cutover, restore-to-authority, irreversible delete, privilege/key change, publish/recall işlerinde sole approver olamaz;
- eksik context, timeout, partial result veya support failure’ı owner’a teknik repair olarak devredemez.

## 11. Flutter ve bakım açısından güvenlik/recovery etkisi

| Boyut | Candidate A | Candidate B | Hakem değerlendirmesi |
|---|---|---|---|
| İlk Flutter integration | Resmi Supabase Dart/Flutter SDK Database/Auth/Storage/Realtime/Functions surface’i verir | Provider-specific SDK zorunlu değil; HTTPS API ve scoped object handle | A daha az başlangıç entegrasyon işi vaat eder; bu authorization/recovery proof değildir |
| Offline/package | SDK hazır closed package, high-consequence conflict veya anti-rollback authority kanıtlamaz | Protocol tamamen API/package/local store işi | B’de control daha açık, özel bakım daha büyüktür |
| Native/plugin drift | Supabase SDK + Flutter plugin/generated registrant + Android/iOS build ve provider defaults | Flutter generic network/storage + custom secure local/offline; Render/Neon/R2 API drift | A SDK drift, B custom contract drift taşır; ikisi için pin/evidence/real-device validation gerekir |
| Owner-independent maintenance | Managed DB/OS yükü daha düşük olabilir | API runtime, migration, object, audit, scanner, identity ve monitoring runbook’ları ayrı | A operasyon kolaylığına sahip olabilir; B’nin çoklu plane yükü owner-debug kabul edilmez |
| AI task surface | Data API/RLS/service_role bypass ve Supabase changelog watch gerekir | Çoklu provider credentials, API policy, cross-plane reconcile ve outage watch gerekir | AI convenience claim güvenlik metriği değildir; iki tarafta narrow task pack gerekir |

Flutter’ın resmi SDK’sı veya generic HTTPS daha iyi bakım hipotezidir; gerçek evidence değildir. Özel offline,
secure local persistence, accessibility, rollback/recall ve cross-plane state machine her iki adayda ürün işidir.

## 12. Candidate-specific hard-fail register

### 12.1 Ortak hard-fail’ler

- HF-COMMON-01: Flutter/browser doğrudan genel canonical DB veya object mutation yapar.
- HF-COMMON-02: UI/cache/provider role/RLS/rule/permission tek başına approval, publication, recall veya audit authority sayılır.
- HF-COMMON-03: High-consequence veride silent LWW, duplicate retry veya local completion official history’ye dönüşür.
- HF-COMMON-04: Partial/mixed offline package kullanılır veya full-library download güvenlik closure’ı yerine konur.
- HF-COMMON-05: Object upload, clean scan, CDN/URL veya preview official technical correctness/publication sayılır.
- HF-COMMON-06: DB transaction/backup/PITR object, audit, identity, config, package ve notification plane’lerini atomik
  kapatmış gibi sunulur.
- HF-COMMON-07: Protected audit/floor aynı mutable restore snapshot’ı içindedir veya custody/fallback yoktur.
- HF-COMMON-08: Restore old recall/revoke/delete/accepted operation truth’unu diriltebilir.
- HF-COMMON-09: Export job, provider clone veya standard SQL/S3 dump clean-room exit kanıtı sayılır.
- HF-COMMON-10: Billing/region/account/support failure’da owner SSH/dashboard repair veya uncapped surprise spend
  zorunlu olur.

Her ortak hard-fail ilgili capability için REJECT-IF-UNMITIGATED’dır; fiyat, latency veya integration convenience ile
offset edilemez.

### 12.2 Candidate A hard-fail’leri

- HF-A-01: service_role/secret, unrestricted SQL/RPC/Storage, owner/bypassrls veya exposed internal path API policy
  dışında erişilebilir.
- HF-A-02: RLS/grant/view/security-definer exposure veya user-editable claim business authorization sanılır.
- HF-A-03: Supabase project table/log/activity protected audit veya non-restorable floor’ın tek custody’sidir.
- HF-A-04: Supabase DB backup/clone Storage bytes, Auth/Functions/config/audit/floor ile complete recovery sanılır.
- HF-A-05: Storage private/signed/public URL quarantine, malware isolation veya recall proof’u yerine konur.
- HF-A-06: Realtime/push/cache veya SDK offline persistence bounded closed package/eligibility/recall authority’sidir.
- HF-A-07: Spend Cap compute/PITR/domain/log/MFA/incident gibi dış kalemleri de evrensel hard cap olarak sunar.

### 12.3 Candidate B hard-fail’leri

- HF-B-01: Render API pratikte opsiyonel kalır veya Neon/R2/admin/provider console policy/audit/operation ledger
  olmadan hassas mutation yapar.
- HF-B-02: Neon owner/superuser/BYPASSRLS, Render runtime secret veya R2 broad/presigned credential API boundary’yi
  bypass eder.
- HF-B-03: R2 consistency/durability/presigned URL protected audit, WORM floor, quarantine veya deletion authority sayılır.
- HF-B-04: Neon PITR/branch DB restore, R2 object restore, Render artifact/config veya identity/policy restore’u
  kapsıyormuş gibi authority cutover yapılır.
- HF-B-05: Üç core provider’ın dışında kalan identity, audit, scanner, notification, observability ve exit custody
  gizli varsayılır veya owner’ın elle işletmesine bırakılır.
- HF-B-06: Neon/Render/R2 alert, free tier veya egress-free davranışı composite invoice hard cap olarak sunulur.

## 13. Compensating control ve evidence-gap matrix

| Control | Candidate A telafisi | Candidate B telafisi | Kapanış kanıtı |
|---|---|---|---|
| Server/API authority | Supabase Data API/Storage direct client yalnız bounded low-risk; independent API/policy gateway | Render API tek zorunlu mutation boundary; Neon/R2 server-only | Privileged-path matrix; direct DB/object/admin negative tests; F01/F02 |
| Contextual auth + SoD | RLS/grants defense; service_role server-only; policy gateway | API policy; Neon role/R2 capability defense | Role/scope/state/classification/independence matrix; self-approval race |
| Key containment | service_role, PAT, signed URL secret inventory/rotation | Render→Neon/R2 workload identities and presigned handles | Leak/revoke/rotate/impact graph; no AI/owner root |
| Object quarantine | Storage private bucket yalnız transport; external scanner/renderer | R2 private quarantine prefix; external scanner/renderer/URL egress | F04; digest/generation/lineage/orphan cleanup |
| Protected audit/floor | Same project dışında independent custody/fallback | R2 dışında independent custody/fallback | F03/F05/F08; checkpoint/fork/tombstone drill |
| Offline closure | Server builder + Flutter verifier/local operation log | Same; no provider sync assumption | F06/F07; wrong-base, non-eviction, conflict/device-loss |
| Cross-plane restore | DB + Storage + Auth/Functions/config + audit/floor manifest | Neon + R2 + Render artifact/config + adjunct manifest | F08/F09 restore quarantine and forward recovery |
| Clean-room exit | pg_dump + object/auth/policy/functions/audit/floor mapping | pg_dump + S3 object mapping + API/runtime/adjunct mapping | F12 import outside normal account and negative tests |
| Cost/billing hold | Spend Cap covered items + independent excluded-item stop | Three-provider item-level metering + safe hold | F10/F15 P0-P3 and incident-month evidence |
| Outage/owner independence | Managed operations plus external negative/export path | Automated multi-plane recovery and no manual SSH/dashboard repair | F11/F14 plain-language state and forward runbook |
| Drift/maintenance | Supabase/Flutter changelog, grants/RLS and native plugin watch | Neon/Render/R2 changelog, API contract and custom protocol watch | F16 dated compatibility hold; exact artifact/config graph |

Bu tablo implementation task’ı değildir; ileride aynı fixture için evidence acceptance listesi olarak kullanılmalıdır.
Bir satırda critical gap kalırsa HELD; hard-fail kapanmıyorsa ilgili composition REJECT-IF-UNMITIGATED olur.

## 14. F01-F16 bağımsız karşılaştırmalı disposition

Ortak fixture’ın beklenen invariant’ı korunur. İki aday için de current sonuç documentary olarak HELD’dir; aşağıdaki
karşılaştırma nedenini ve relative risk yüzeyini gösterir.

| ID | Beklenen invariant | Candidate A | Candidate B | Hakem kritik gap’i |
|---|---|---|---|---|
| F01 | Stale browser role commit-time deny/hold; cache authority değil | HELD — API gateway ve RLS defense tanımlı, live negative drill yok; direct Data API/RLS bypass riski | HELD — explicit API boundary var, identity/policy ve route-bypass kanıtı yok | Reauth, step-up, scope/state/version, no-side-effect audit |
| F02 | Key leak sonrası rotation/revocation/session-operation-handle impact | HELD — service_role ve signed URL residual semantics kritik | HELD — Render/Neon/R2 workload keys ve presigned bearer kritik | Security epoch, secret inventory, rotation, pending operation reconciliation |
| F03 | Lost DB response same operation result; no duplicate | HELD — Postgres idempotency/outbox primitive’i uygun, timeout drill yok | HELD — Neon idempotency ledger öneriliyor, timeout drill yok | Durable operation ledger ve lookup evidence |
| F04 | Upload success + metadata/audit failure quarantine/orphan; no official availability | HELD — Storage object DB backup’tan ayrı; scanner external | HELD — R2 object strong consistency transport; scanner/audit external | Object capability, quarantine, digest/generation, orphan cleanup |
| F05 | Newer negative suspension generation wins publish race | HELD — Postgres fence inferred; independent negative authority open | HELD — modular boundary explicit; negative authority/floor open | Concurrency race and release/suspension generation evidence |
| F06 | Wrong/incomplete offline delta atomic reject; safe complete fallback | HELD — SDK package closure proof değil | HELD — package builder custom, cache non-eviction open | Machine-verifiable dependency closure, anti-rollback, safe-stop |
| F07 | Offline ownership/provenance conflict preserves both and holds | HELD — local operation/reconciliation custom | HELD — same custom protocol, provider does not solve it | Expected version, idempotency, device-loss and no silent LWW |
| F08 | Old backup cannot resurrect recall/revoke/delete/accepted op | HELD — DB backup excludes Storage; same-project floor risk | HELD — Neon PITR, R2 object and Render config separate; floor open | RESTORE_QUARANTINE, external floor/tombstones, forward recovery |
| F09 | DB restore/object/audit/config mismatch blocks cutover | HELD — DB clone/manual Auth/Storage/Function reconfig | HELD — three-plane mismatch is explicit but untested | Coordinated consistency manifest and clean-room mismatch evidence |
| F10 | Billing/quota suspension holds positive work; owner-readable recovery | HELD — Spend Cap partial; compute/PITR/domain/log exclusions | HELD — no composite hard cap across Neon/Render/R2 | Item-level cap/overage, billing state, export path, safe hold |
| F11 | Provider/region unavailable; bounded safe recovery; no owner repair | HELD — integrated control-plane blast radius and external negative path | HELD — multi-provider partial outage and API dependency | Safe-stop/history, independent negative authority, automated recovery |
| F12 | Clean-room exit preserves IDs/policy/objects/audit/floor and negative tests | HELD — PostgreSQL core portable; integrated plane reconfiguration open | HELD — PG/S3/API portable primitives; three adapters and adjuncts open | External account import, role/deny/delete/recall tests |
| F13 | AI ordinary task minimum context/least privilege | HELD — service_role/PAT temptation; runbook not executed | HELD — many workload keys and API tasks; runbook not executed | Task pack, dry-run, stop condition, no owner/root |
| F14 | Half-failed AI operation stops and forwards safely; no owner debug | HELD — Function/Management API and cross-plane state | HELD — API/worker/provider reconciliation state | Machine evidence, idempotent forward recovery, reviewer |
| F15 | P2/P3/incident quota behavior and safe hold known | HELD — more integrated cost surface but Spend Cap exclusions | HELD — three metered vendors and adjunct costs | Workload-specific USD/TAX/FX, incident month, cap/overage evidence |
| F16 | Provider drift dated, compatibility held, migration/revalidated | HELD — Supabase/Flutter defaults, grants, logs and plugins drift | HELD — Neon/Render/R2 plus custom API/offline protocol drift | Dated changelog watch, pinned artifact/config and migration gate |

### Relative disposition, not score

- A’nın F01/F02/F04/F08/F09 riskleri integrated service-role, Storage ve project-restore coupling çevresinde
  yoğunlaşır.
- B’nin F01/F02/F05/F09/F10/F11 riskleri custom API policy, multi-provider coordination ve owner-independent
  operations çevresinde yoğunlaşır.
- A’nın managed operation convenience’i A’nın hard-fail’lerini kapatmaz.
- B’nin explicit modular boundaries’i B’nin hard-fail’lerini kapatmaz.
- Hiçbir F senaryosunda integration kolaylığı veya component separation kritik kanıt eksikliğini telafi etmez.

## 15. Reversible Phase-4 direction and handoff boundary

### Koşullu yön önerisi

Eşit documentary karşılaştırmada **Candidate B, yalnızca reversible Phase-4 evidence-first working direction olarak
öne alınabilir**. Gerekçe:

1. DEC-0034 server/API boundary’sini fiziksel kompozisyonda açıkça zorunlu kılar.
2. Neon PostgreSQL canonical transaction ile R2 object bytes’ı baştan ayrı planes olarak gösterir; DB backup’ın
   object/audit/config’i otomatik kapsadığı yanlış varsayımı daha zor yapılır.
3. PostgreSQL logical export ve R2 S3-compatible transport exit dossier’e doğrudan map edilebilir.
4. Aday A’nın Supabase Data API/service-role/RLS/Storage/backup/project-control-plane coupling’i kritik negative test
   yüzeyini daha fazla görünür kılar.

Bu yön B kazandı, B production-ready veya B daha güvenli demek değildir. B şu koşullarda otomatik geri alınır veya
A ile yeniden eşitlenir:

- independent API, identity, policy, audit/floor, quarantine, notification, monitoring, backup/exit adjunct’ları
  owner-debug gerektirmeden kapatılamazsa;
- üç provider account/billing/region outage, composite cap/overage ve clean-room exit F10-F12/F15 kanıtını kapatamazsa;
- Flutter offline package/operation/reconciliation ve cross-plane release graph’i güvenli şekilde taşınamazsa;
- B’nin maintenance/credential/incident yükü teknik olmayan sahip için otomatik ve reviewable runbook’a bağlanamazsa.

Aynı koşullu evidence pack A için de yürütülmelidir. A, B’nin kanıt başarısızlığında otomatik fallback veya kazanan
değildir; A’nın kendi HF-A-01..07 ve ortak hard-fail’leri kapanmadan seçilemez.

### ADR öncesi minimum evidence pack

1. İki aday için aynı privileged-path ve provider-console bypass matrix.
2. F01-F05 security/operation/object/release race no-code walkthrough’u.
3. F06-F07 closed package ve local operation conflict/device-loss matrix.
4. F08-F09 old-backup restore quarantine, floor/tombstone ve cross-plane manifest drill.
5. F10-F11 provider/account/billing/region outage state ve owner-independent recovery.
6. F12 clean-room exit import, negative authorization/delete/classification/suspension tests.
7. F13-F14 AI task pack, half-failure evidence, forward recovery ve independent reviewer.
8. F15 P0-P3 ve incident-month cost/cap/overage table; F16 dated changelog/compatibility hold.
9. Identity/auth, protected audit/floor, scanner/quarantine, notification, observability, backup/exit ve emergency
   negative authority’ın seçilmemiş olsa bile sorumluluk ve cost owner’ları.
10. Her critical gap için residual risk, fallback, stop condition ve nontechnical owner output’u.

Evidence pack tamamlanmadan:

- hiçbir aday için PASS veya provider/plan/region approval verilmez;
- hesap, subscription, purchase, code, prototype veya ADR oluşturulmaz;
- Gate 4 -> 5 kapalı kalır;
- owner’dan database administration, SSH, log diagnosis veya incident repair beklenmez.

## Evidence links

- [DEBATE-008 — Finalist A](DEBATE-008__FINALIST_A_SUPABASE.md)
- [DEBATE-008 — Finalist B](DEBATE-008__FINALIST_B_MODULAR_MANAGED.md)
- [DEBATE-008 — Finalist Common No-Code Fixture](DEBATE-008__FINALIST_COMMON_FIXTURE.md)
- [DEBATE-008 — External Report Audit](DEBATE-008__EXTERNAL_REPORT_AUDIT.md)
- [DEBATE-007 — Judge Synthesis](DEBATE-007__JUDGE_SYNTHESIS.md)
- [DEBATE-008 — Stack Candidates & Cost Primary Research](DEBATE-008__STACK_CANDIDATES_COST_PRIMARY_RESEARCH.md)
- [DEBATE-008 — Stack Architecture Fit Research](DEBATE-008__STACK_ARCHITECTURE_FIT_RESEARCH.md)
- [Decision Log — DEC-0034](../../00_CONTROL/DECISION_LOG.md)
