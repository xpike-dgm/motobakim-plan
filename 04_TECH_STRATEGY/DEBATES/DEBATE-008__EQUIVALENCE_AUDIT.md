# DEBATE-008 — Finalist Equivalence Audit

**Durum:** `DOCUMENTARY EQUIVALENCE AUDIT / NO-CODE / NO WINNER / ADR NOT READY`  
**Tarih:** `2026-09-18` (Europe/Istanbul)  
**İncelenenler:**

- [DEBATE-008 — Finalist Common No-Code Fixture](DEBATE-008__FINALIST_COMMON_FIXTURE.md)
- [Finalist A — Yönetilen Supabase](DEBATE-008__FINALIST_A_SUPABASE.md)
- [Finalist B — Modular Managed Composition](DEBATE-008__FINALIST_B_MODULAR_MANAGED.md)
- [DEBATE-008 — Flutter Backend Karşılaştırma Matrisi Dış Raporu Denetimi](DEBATE-008__EXTERNAL_REPORT_AUDIT.md)

Bu dosya iki finalist dosyasının aynı karşılaştırma sözleşmesine uyup uymadığını denetler. Kod, provider seçimi,
puanlama, satın alma veya kazanan ilanı değildir. Aday dosyaları değiştirilmemiştir.

## 1. Kısa hüküm

**Eşdeğerlik şu anda yalnızca kısmen sağlanmıştır.** Her iki dosyada 15 kanıt bölümü ve F01–F16 senaryolarının
tamamı bulunuyor; her iki adayın genel durumu `HELD`, hiçbir senaryo `PASS` değil ve her ikisi de provider
dashboard/console yolunu Kavriva Internal Operations otoritesi saymıyor. Bunlar gerçek bir eşitlik çekirdeğidir.

Ancak fiyatın güncelliği, zorunlu adjunct servislerin görünürlüğü, maliyet ufukları, kanıt etiketlerinin anlamı ve
F senaryolarındaki aday-spesifik kanıt ayrıntısı eşit değildir. Şu haliyle bir toplam maliyet, yönetim yükü veya
“daha hazır” sonucu iki dosyadan adil biçimde çıkarılamaz.

En önemli dengesizlikler:

1. **B’nin Neon fiyat/kota snapshot’ı güncel resmi pricing sayfasıyla uyumsuzdur.** B §1 (`FINALIST_B`, yaklaşık
   L56–70) Free için 10 proje/50 CU-hour kullanır; güncel [Neon pricing](https://neon.com/pricing) sayfasında
   2026 snapshot’ında Free 100 proje ve proje başına 100 CU-hour sinyali görünür. B ayrıca 30 günlük history/PITR
   bilgisini plan kapsamından ayırmaz; güncel fiyat sayfasında Free/Launch/Scale history pencereleri farklıdır.
   Bu, B’yi güncel olmayan daha düşük Free kotasıyla ve kapsamı belirsiz restore maliyetiyle değerlendirir.
2. **A’nın API boundary’si fiziksel olarak `OPEN` bırakılmıştır; B’nin API runtime’ı Render olarak fiyatlanmıştır.**
   A §1–2’deki belirsiz API/worker maliyeti ve region/failure domain’i hesaba katılmadan A’nın “managed daha az
   yük” görünümü B’nin seçilmiş Render runtime’ı ile karşılaştırılamaz.
3. **B zorunlu adjunct servisleri açıkça listelerken A bunları aynı tekil tablo ve maliyet statüsüyle listelemez.**
   A’da identity/recovery, protected audit/floor, quarantine/scanner, package worker, notification ve monitoring
   bazı satırlara dağılmış veya `OPEN` kalmıştır. Supabase Auth/Storage/Functions bunların mekanizma primitive’leri
   olabilir; proje çözümü, bağımsız recovery veya protected custody kanıtı değildir.
4. **Maliyet ufku satırları aynı değildir.** Common fixture minimum güvenli closed test, minimum güvenli Android,
   iOS ekleme, P2/P3, restore drill, exit drill ve incident month ister. A restore/exit satırlarını yazıp Android/iOS
   satırlarını ayrı yazmaz; B Android/iOS satırlarını yazıp restore/exit maliyetini ayrı satır olarak yazmaz.
5. **Kanıt standardı aynı granularitede değildir.** A’da 15 maddelik negative-test matrisi ve `HF-BAAS-01..12`
   register’ı vardır; B’de benzer testler çoğunlukla bullet kümeleridir ve aday-spesifik hard-fail register’ı yoktur.
   Aynı `CONFIRMED` kelimesi de A’da 2026’da okunmuş resmi kaynak, B’de ise eski resmi blog rate’leri için kullanılmaktadır.

Bu nedenle disposition: **`KISMEN EŞDEĞER / DOKÜMANTASYON DÜZELTMESİ GEREKLİ / NO WINNER`**. Her iki adayın F01–F16
sonuçları belge kapanana kadar `HELD` kalır.

## 2. Denetim yöntemi ve ortak ölçüt

Common fixture §1–§8 şu bağlayıcı ölçütleri verir:

- iki kompozisyon da `DEC-0034` canonical authority, server/API mediation, online-authoritative Internal Operations,
  bounded offline package, durable operation, protected audit/floor, object boundary, cross-plane restore/exit ve
  provider/billing failure state sınırlarını korur;
- iki aday da identity, protected audit, quarantine/scanning, monitoring, notification, backup/export ve emergency
  negative authority için gereken ek düzlemleri görünür kılar;
- her aday aynı 15 evidence section'ı, aynı P0–P3 active-user fixture'ını, aynı 12 MB/150 MB/25 MB/250 MB
  comparison values'ını ve aynı F01–F16 required outcome'larını karşılar;
- `PASS`, güncel resmi evidence ve candidate-specific closure olmadan verilemez; `HELD` bilinmeyen kritik kontrol
  güvenli biçimde tutulabiliyorsa kullanılır.

Bu audit aşağıdaki etiketleri kullanır:

| Etiket | Anlam |
|---|---|
| **EŞDEĞER** | Kapsam, varsayım, workload, kanıt tazeliği ve sonuç standardı iki dosyada aynı seviyede. |
| **KISMEN EŞDEĞER** | Aynı mekanizma veya senaryo var, fakat kanıt derinliği, maliyet kapsamı veya açık varsayımlar farklı. |
| **EŞDEĞİL** | Bir adayda zorunlu yüzey seçilmiş/fiyatlanmış, diğerinde gizli veya `OPEN`; ya da birincil fiyat/plan karşılığı aynı tarihte değil. |
| **UNRESOLVED** | Bu belgeyle hangisinin daha iyi olduğu söylenemez; düzeltme ve yeniden kanıt gerekir. |

`EŞDEĞER` bir üretim geçişi veya fiziksel test başarısı anlamına gelmez.

## 3. 15 kanıt bölümünün karşılaştırması

| # | Common fixture konusu | Aday A — Supabase | Aday B — Neon + Render + R2 | Eşdeğerlik hükmü ve gerekli düzeltme |
|---:|---|---|---|---|
| 1 | Exact products, dated official price/limit | Supabase fiyatı ayrıntılı ve güncel görünür; API runtime `OPEN`. | Üç çekirdek ürün görünür, fakat Neon Free/rate snapshot’ı eski ve history planı ayrışmamış. | **EŞDEĞİL.** B güncel Neon pricing’e göre yenilenmeli; A da API runtime/adjunct maliyetlerini B ile aynı görünürlükte vermeli. |
| 2 | Account/project/region/billing failure domains | Supabase organization/project ayrıntılı; API, audit/floor, quarantine ve bazı identity alanları `OPEN`; notification/monitoring ayrı yüzey olarak eksik. | Üç provider ve identity/audit/scanner/notification/observability adjunct’ları ayrı tabloyla açık. | **EŞDEĞİL.** A’ya B’deki provider-neutral adjunct tablosunun eşdeğeri eklenmeli; B’nin çoklu domain yükü gerçek risk olarak kalabilir ama A’nın belirsiz servisleri gizli avantaj olmamalı. |
| 3 | Client/API/DB/object/worker/admin/provider-console privileged paths | İzin verilen low-risk direct Data API istisnası açıkça sınırlandırılmış; service-role/RPC/Storage yolları ayrıntılı. | Tüm client trafiği Render API’den; Neon/R2 direct yolları yasak; provider console ayrı. | **KISMEN EŞDEĞER.** A’nın direct low-risk read istisnası test edilmeden capability kredisi almaz; B’nin API-only yolu da authorization kanıtı değildir. Aynı allow/deny/hold test ID’leri kullanılmalı. |
| 4 | Credentials, owner/legal actions, AI rules, rotation/recovery | Supabase Auth/service-role/Management API sınıfları var; session freshness, protected custody ve bazı recovery ayrıntıları `OPEN`. | Identity, secret manager, audit custody ve scanner provider’ları seçilmemiş; workload identities ayrıntılı. | **EŞDEĞİL.** A’da Supabase Auth seçilmiş görünse de phishing-resistant step-up, security epoch, recovery ve legal owner closure B ile aynı `OPEN` standardına çekilmeli; B’nin adjunct seçilmemiş olması saklı negatif değildir. |
| 5 | Canonical transaction / cross-plane partial / reconcile | PostgreSQL current/history/idempotency/outbox transaction sınırı ve state machine ayrıntılı. | Neon transaction/idempotency/outbox ve R2 object state machine aynı dağıtık sınırı kabul ediyor. | **EŞDEĞER (mekanizma düzeyi).** Hiçbir Postgres transaction’ı object, bağımsız audit, notification veya provider billing’i atomik yapmaz; bu kural iki dosyada aynı tutulmalı. |
| 6 | Authorization and negative tests, privileged bypass | 15 satırlı matrix, RLS/grant/view/security-definer/service-role bypass testleri ve her satır `HELD`. | Aynı familyalar bullet kümeleri olarak var; test başına evidence status/owner/acceptance ID yok. | **KISMEN EŞDEĞER.** B, A ile aynı test ID, expected result, evidence artifact ve `HELD` gerekçesiyle tabloya dönüştürülmeli; A’nın ayrıntı seviyesi B’ye gizli kalite puanı sağlamamalı. |
| 7 | Offline package/local operation/conflict/retry | 12/150/25/250 MB karşılaştırma değerleri, manifest, durable operation ve no silent LWW var. | Aynı değerler, package verifier, local operation ve explicit conflict/hold var. | **EŞDEĞER (documentary design).** Her iki provider SDK/native feature’ı bounded package, anti-rollback, queue, secure local persistence veya reconciliation proof sayılmamalı. |
| 8 | Protected audit and non-restorable floor | Aynı Supabase project/account snapshot’ına güvenmeme; physical custody/floor `OPEN`. | Neon branch/PITR veya R2 durability/Object Lock’ın tek başına yeterli olmadığı belirtilmiş; custody `OPEN`. | **EŞDEĞER (kritik closure yok).** A ve B aynı independent custody/fork/gap/restore-floor drill’ini ve aynı retention/cost status’ünü göstermeli. |
| 9 | Media quarantine/object lifecycle | Supabase private bucket/signed URL ve quarantine-first lifecycle; scanner/renderer bağımsız. | R2 presigned handle, immutable key/generation, scanner/renderer ve orphan lifecycle ayrıntılı. | **KISMEN EŞDEĞER.** A object operation/transform/orphan-cleanup maliyetini B’nin Class A/B/retrieval/version alanları kadar açık yazmalı; R2 durability veya Supabase private bucket hiçbirinde scan/approval authority değildir. |
| 10 | DB/object/audit/identity/policy/config/package backup and restore | Supabase daily backup/PITR/DB-only clone sınırı ayrıntılı; server/API artifact ve adjunct recovery tam bir plane tablosu değil. | Neon history/pg_dump, Render artifact, R2 object ve adjunct manifestleri açık; Neon retention/restore price scope `OPEN`/eski kaynaklı. | **EŞDEĞİL.** Her iki aday aynı cross-plane manifest alanlarını, API artifact/config/identity recovery’yi, RPO/RTO, retention, restore downtime ve incident cost’ını taşımalı. |
| 11 | Logical export/clean-room import outside normal account | `pg_dump`/Supabase restore primitive’leri, object/Auth/Functions manual reconfiguration ve clean-room negative tests var. | pg_dump + R2 S3 export, Render artifact/config ve clean-room acceptance var. | **KISMEN EŞDEĞER.** İki dosya aynı external target, stable IDs, policy/object/audit/floor, secrets re-encryption, negative tests ve exit-drill maliyetini göstermeli; provider-native clone/export tek başına exit proof değildir. |
| 12 | Observability, incident support, no-owner-debug AI runbook | Supabase/Flutter changelog ve log retention ayrıntılı; API runtime/adjunct monitoring yine `OPEN`. | Üç provider sinyali ve adjunct monitoring/support `OPEN`; current official changelog matrix yok. | **EŞDEĞİL.** B’de her provider için dated official drift/support evidence eklenmeli; A’da API/identity/scanner/notification observability aynı zorunlu yüzey olarak maliyetlenmeli. |
| 13 | P0–P3 cost, cap/overage, safe budget-hold | P0/P1/P2/P3 + restore/exit/incident satırları var; Android/iOS ayrı satır değil; API/adjunct total eksik. | P0/P1/Android/iOS/P2/P3/incident satırları var; restore/exit ayrı maliyet satırı değil; Neon snapshot eski. | **EŞDEĞİL.** Ortak tek cost worksheet kullanılmalı; tüm zorunlu servisler, minimum safe closed test/Android/iOS, restore ve exit aynı satırlarda `USD / UNRESOLVED` olarak görünmeli. |
| 14 | Provider replacement/architecture exit | Supabase relational core ve integrated feature lock-in ayrıntılı; self-host bakım yükü açık. | Neon/Render/R2 adapter ve multi-provider exit ayrıntılı; adjunct lock-in açık. | **KISMEN EŞDEĞER.** Aynı clean-room target, migration labor, re-encryption, support/region/legal cost ve cutover fence olmadan iki portability iddiası da yalnız primitive seviyesindedir. |
| 15 | PASS/HELD/REJECT per scenario and overall | F01–F16 tümü `HELD`; ek olarak A-only `HF-BAAS-01..12` register’ı var. | F01–F16 tümü `HELD`; aday-spesifik eşdeğer hard-fail register yok. | **KISMEN EŞDEĞER.** Sonuç statüsü eşit; kabul/red koşullarının granularitesi değil. Candidate-neutral hard-fail taxonomy common fixture’a eklenmeli veya B’ye A ile eşdeğer register konmalı. |

## 4. Ürün, varsayım ve zorunlu servis eşitliği

### 4.1 Aday A’da açık, B’de açık veya tersi olan yüzeyler

Common fixture’in “ek zorunlu düzlem gizlenemez” kuralına göre iki dosyada aşağıdaki ortak inventory bulunmalıdır:

| Zorunlu yüzey | Aday A’daki mevcut görünüm | Aday B’deki mevcut görünüm | Eşitlenmesi gereken okuma |
|---|---|---|---|
| Identity, session, recovery, step-up | Supabase Auth primitive’i var; recovery/security epoch ve privileged step-up tam kapanmış değil. | Identity provider seçilmemiş; açıkça `OPEN`. | İkisi de `primitive mevcut` ile `project identity/recovery closure`ı ayırmalı. A’ya Auth için haksız tamamlanmışlık kredisi verilmemeli; B’nin açık seçimsizliği de gizlenmemeli. |
| Contextual authorization | A’da fiziksel server/API runtime `OPEN`; RLS defense-in-depth. | Render API zorunlu boundary; policy engine seçilmemiş. | İkisinde de route-level authorization, independence, expected version/generation ve bypass testleri aynı evidence pack olmalı. |
| Protected audit/floor | Physical custody `OPEN`; ordinary Supabase table/log kabul edilmiyor. | Independent custody `OPEN`; R2 durability/Object Lock yeterli sayılmıyor. | Eşit `HELD`; hiçbir native log/PITR/durability bunu kapatmaz. |
| Quarantine/scanner/renderer | Ayrı boundary/ürün `OPEN`; Storage upload kabulü yeterli değil. | Ayrı scanner/renderer `OPEN`; R2 transport yeterli değil. | Aynı scan, SSRF/redirect, lineage, orphan ve retention acceptance’ı ve maliyeti yazılmalı. |
| Package builder/outbox/worker | Edge/worker yardımcı aday; fiziksel runtime `OPEN`. | Render worker veya başka runtime `OPEN`. | İkisi de zorunlu servis; “Supabase Functions mevcut” veya “Render Web Service mevcut” tek başına package/operation closure değildir. |
| Notification/delivery | A’da ayrı mandatory failure domain olarak görünür değil. | Ayrı `OPEN` adjunct olarak görünür. | A’ya notification/delivery, quota, retry ve recall-hint yüzeyi eklenmeli. Bildirim hiçbirinde authority değildir. |
| Monitoring/incident evidence | Logs/metrics ve log drain anlatılıyor; adjunct API/scan/audit monitoring ayrı seçilmemiş. | Monitoring provider/retention/support açıkça `OPEN`. | Her iki aday aynı provider-agnostic signal inventory, retention, alert failure ve no-owner escalation tablosunu taşımalı. |
| Backup/export/clean-room | Supabase DB/PITR primitive’i güçlü; API/object/audit/identity/config/package closure ayrıca açık. | Neon/R2/Render plane’leri ayrı; adjunct closure açık. | DB backup/PITR, object durability, deploy rollback ve provider clone hiçbirinde bütün sistem restore’u sayılmamalı. |
| Emergency negative authority | Generation fence tasarımı var; independent physical custody `OPEN`. | Generation/floor tasarımı var; authority `OPEN`. | İki adayda aynı monotonic negative generation, restore quarantine ve F05/F08 acceptance’ı aranmalı. |

### 4.2 API runtime ve hesap sayısı karşılaştırması

A’nın “managed Supabase” olması API boundary’sini ortadan kaldırmaz. Common fixture, yüksek sonuçlu mutation’ların
onaylı server/API policy boundary arkasında olmasını ister. A’nın bu runtime’ı fiziksel olarak seçilmediği için:

- A’nın API compute, deploy, secrets, logs, region, outage, backup ve incident cost’ı `UNRESOLVED` kalır;
- B’nin Render Web Service fiyatı ve ayrı account/workspace failure domain’i A’ya karşı otomatik dezavantaj sayılamaz;
- A için ya Supabase Edge Functions/başka API runtime’ın **temsilci** cost/failure dossier’i yazılmalı ya da B’nin
  Render cost/failure alanları da karşılaştırma sırasında `OPEN` kabul edilmelidir;
- aynı kural identity, scanner, notification, audit custody, monitoring ve export destination için de geçerlidir.

B’nin üç core vendor’ı olması gerçek bir operasyon/incident yüzeyidir; fakat [external audit §3.5](DEBATE-008__EXTERNAL_REPORT_AUDIT.md)
bu yükün tek başına dealbreaker olmadığını söyler. A’nın daha az görünen control plane’i de tek failure domain,
bundled quota ve provider account recovery risklerini otomatik olarak çözmez.

### 4.3 Hazır yönetim paneli ile Kavriva Internal Operations ayrımı

İki finalist dosyası bu konuda genel olarak doğru davranır:

- A §3’te `Browser Internal Operations` yalnız intent/form gönderir; Supabase provider dashboard/Management API
  product authority değildir.
- B §3’te browser Internal Operations Render API üzerinden gider; Neon/Render/R2/provider console approval,
  publication, recall veya audit replacement değildir.
- Common fixture’teki Internal Operations, Kavriva’nın role/scope/state/independence/version kontrolü yapan ürün
  panelidir; Supabase Studio, Neon Console, Render Dashboard veya Cloudflare dashboard bunun yerine geçemez.

Bu nedenle **hiçbir adaya hazır panel kredisi verilmemelidir**. Her iki dosya da no-code olduğu için gerçek panel,
workflow completeness, audit display, safe-hold display veya owner-readable recovery UI kanıtlamamıştır. Documentation
fix: her iki dosyaya aynı açık cümle eklenmeli: “Provider console/admin UI operasyon aracıdır; Kavriva Internal Operations
paneli değildir ve F01/F05/F10/F13 otoritesini sağlamaz.”

### 4.4 Provider-native feature, proje çözümü değildir

| Native özellik | Doğrulanabilir primitive | DEC-0034/common fixture closure’ı değildir |
|---|---|---|
| Supabase RLS / `auth.uid()` | Row policy ve grant layer | Contextual approval, independence, service-role/owner bypass, protected audit veya server API boundary. |
| Supabase Auth | Session/identity primitive’i | Phishing-resistant privileged auth, security epoch, legal recovery, domain competence veya role-revocation drill. |
| Supabase Storage private bucket/signed URL | Transport access control | Malware isolation, classification correctness, quarantine, revocation floor veya object–audit atomicity. |
| Supabase daily backup/PITR | Database recovery primitive’i | Storage bytes, API artifact, identity/policy/config, audit/floor, package ve anti-resurrection restore. |
| Neon transaction/PITR/branch | PostgreSQL transaction/history primitive’i | R2 object, API artifact, identity, protected floor, notification veya cross-plane cutover. |
| Render deploy/rollback | API artifact/runtime primitive’i | Database/object/audit restore, authorization correctness veya provider account recovery. |
| R2 presigned URL/strong consistency/durability | Object transport/availability/durability primitive’i | Scanner, approval, WORM/protected audit, deletion floor, backup, clean-room exit veya zero bill. |

Bu ayrım her iki finalist dosyasında genel olarak yazılıdır; audit standardı gereği fiyat, convenience veya
“managed/portable” anlatısında bu primitive’ler proje closure’ı gibi sayılmamalıdır.

## 5. F01–F16 eşdeğerlik denetimi

Her iki dosyada da senaryo sonucu `HELD` olduğundan burada olumlu sonuç verilmemektedir. Tablo, aynı required outcome,
aynı evidence depth ve aynı cost/failure varsayımının bulunup bulunmadığını denetler.

| ID | Common fixture required outcome | Aday A / Aday B mevcut durum | Eşdeğerlik bulgusu ve documentation fix |
|---|---|---|---|
| F01 | Stale browser role commit-time deny/hold; cached UI authority değil | A: server reauthorization + RLS, `HELD`. B: Render API + step-up/identity, `HELD`. | **KISMEN EŞDEĞER.** Aynı stale-token/session-revocation test ID’si, artifact ve reason alanı iki dosyada da gösterilmeli. RLS veya API route varlığı canlı negatif kanıt değildir. |
| F02 | Privileged key leak; rotate/revoke, affected sessions/operations audit; no client exposure | A: `service_role` server-only ve signed URL flow. B: Neon/R2 workload keys, identity provider `OPEN`. | **KISMEN EŞDEĞER.** A’nın Supabase key dokümanı kapanış değildir; B’nin unselected identity’si explicit hold olarak kalmalı. Aynı impact graph, residual handle ve recovery evidence istenmeli. |
| F03 | Lost response; operation lookup returns original result; no duplicate | Her ikisi operation ID, idempotency ledger, `OUTCOME_UNKNOWN` ve reconcile state machine tanımlar; ikisi de `HELD`. | **EŞDEĞER (documentary).** A Postgres, B Neon demesi sonucu değiştirmez; timeout/retry drill yok. |
| F04 | Object success + metadata/audit failure => quarantine/orphan, no official availability | A Supabase Storage quarantine; B R2 quarantine/scanner; ikisi `HELD`. | **KISMEN EŞDEĞER.** Aynı scan evidence, orphan cleanup/retention, object digest/generation ve operation-cost fields eklenmeli. Private bucket/presigned URL tek başına quarantine değildir. |
| F05 | Newer negative generation beats in-flight publish | Her ikisi monotonic generation fence ve independent negative authority tasarlar; fiziksel custody `OPEN`; `HELD`. | **EŞDEĞER (unproved).** Aynı concurrency/race acceptance test ve restore-floor kanıtı gerekir; transaction primitive’i tek başına yeterli değildir. |
| F06 | Wrong-base/incomplete offline delta atomically rejected; last safe complete context | Her ikisi aynı 12 MB/150 MB/25 MB/250 MB comparison values, manifest/digest/anti-rollback ve `HELD` kullanır. | **EŞDEĞER (documentary).** Provider SDK/Realtime/object delivery hiçbirinde package verifier veya cache non-eviction proof sayılmamalı. |
| F07 | Offline conflict preserves evidence; high-consequence action held/reviewed | Her ikisi expected version, durable operation, no silent LWW ve preserve/hold tanımlar; `HELD`. | **EŞDEĞER (documentary).** Device loss/clone/attachment loss drill iki adayda da yok. |
| F08 | Old backup cannot resurrect recall/revoke/delete/accepted operation | A Supabase DB/PITR + external floor; B Neon history + R2 + external floor; ikisi `HELD`. | **KISMEN EŞDEĞER.** B’nin Neon history retention/plan scope’u güncellenmeli; her iki aday aynı restore-quarantine, object/audit/policy/identity manifest ve anti-resurrection drill’ini maliyetlemeli. |
| F09 | DB restore/object/audit/config mismatch detected; no authority cutover | A DB/Storage/audit/config manifest var, API artifact explicit değil. B Render artifact/config ve cross-plane manifest var. | **EŞDEĞİL.** A’ya server/API artifact, runtime config, dependency/provenance ve identity/scanner/notification restore alanları B ile aynı seviyede eklenmeli. |
| F10 | Account/billing/quota suspension => safe hold, owner-readable recovery/export, no surprise overage | A Supabase Spend Cap inclusion/exclusion; B Neon/Render/R2 composite alerts; ikisi `HELD`. | **KISMEN EŞDEĞER.** A’nın single-account cap’i genel hard cap değildir; B’nin three-account alerts’i de değildir. Item-by-item cap/overage/deny/hold table aynı cost sheet’te olmalı. |
| F11 | Primary provider/region unavailable => bounded safe read/recovery; no owner repair | A local safe package + Supabase/API region, API runtime `OPEN`. B multi-provider regions + safe-stop/history, adjuncts `OPEN`. | **KISMEN EŞDEĞER.** A API region ve B adjunct outage behavior same required matrix’e sokulmalı; owner SSH/dashboard repair hiçbirinde fallback sayılmamalı. |
| F12 | Clean-room exit outside normal account; stable IDs/policy/object/audit/floor survive | Her ikisi clean-room import ve negative tests tanımlar; A `HELD`, B `HELD`. | **EŞDEĞER (documentary).** Aynı external target, import labor, object egress, re-encryption ve cutover fence cost rows eksik. Native clone/pg_dump başarı sinyali değil. |
| F13 | AI ordinary task => minimum context/least privilege; no owner/root/global key | Her ikisi task pack, dry-run, scoped key, reviewer ve owner-debug yasağı tanımlar; `HELD`. | **EŞDEĞER (documentary).** A Management API/PAT, B provider owner/Neon superuser/R2 key için aynı prohibition ve evidence artifact açıkça eşlenmeli. |
| F14 | AI half-failure => machine-readable partial/unknown, forward recovery, independent review | Her ikisi PARTIAL/UNKNOWN/RECONCILE states ve reviewer handoff tanımlar; `HELD`. | **EŞDEĞER (documentary).** Her iki aday için aynı evidence digest/checkpoint, poison/dead-letter ve no-blind-retry acceptance’ı eklenmeli. |
| F15 | P2/P3/incident over-quota => actual cap/overage and safe held mode; no unlimited assumption | A current Supabase cap exclusions but API/adjunct cost gap. B multi-provider alerts and outdated Neon prices. | **EŞDEĞİL.** Common cost worksheet, current Neon prices, normalized request/object/restore workload and mandatory adjunct totals olmadan F15 karşılaştırılamaz. |
| F16 | Provider API/default/security drift => dated changelog, compatibility hold, revalidation | A Supabase changelog watch detailed; B generic watch, no equivalent dated source matrix. | **EŞDEĞİL.** B için Neon/Render/R2/identity/scanner drift sources and compatibility artifact; A için API runtime/adjunct drift matrix aynı standarda getirilmeli. |

## 6. Fiyat ve maliyet ufku eşitleme planı

### 6.1 Güncel Neon düzeltmesi

B §1 ve B §13, 2025 resmi blogundaki `10 project / 50 CU-hour` sinyalini 2026 karşılaştırma snapshot’ı olarak
kullanıyor. [Güncel Neon pricing](https://neon.com/pricing) tekrar okunmalı ve kaynakta şu ayrımlar ayrı satırlara
konmalıdır:

- Free: güncel project/CU/storage/history limitleri;
- Launch: `$0.106/CU-hour`, storage ve instant-restore history kapsamı;
- Scale: `$0.222/CU-hour` ve daha uzun history kapsamı;
- branch-hour, scale-to-zero, egress, restore branch ve connection/compute pressure;
- organization spending alerts’ın hard invoice cap olmadığı;
- 30 günlük history’nin tüm planlara ait olmadığı.

Eski resmi blog tamamen silinmemeli; “tarihsel kaynak” diye etiketlenmeli. Güncel resmi pricing ile çelişen eski
snapshot `CONFIRMED-2026` olarak kalamaz.

### 6.2 Ortak cost worksheet zorunluluğu

Her aday için aynı satır ve aynı `mandatory now / mandatory later / deferrable / optional / scale-triggered /
contingency / UNRESOLVED` sütunları kullanılmalıdır:

1. P0 documentary evaluation;
2. minimum safe private/closed test (P1=100);
3. minimum safe Android production;
4. later iOS addition;
5. P2=10,000;
6. P3=50,000;
7. one restore drill;
8. one clean-room exit drill;
9. one incident month with elevated retry/log/export/object/scan/notification/support activity.

Her satırda aynı workload conversion verilmelidir: active users yalnızca başlangıç sayısıdır; MAU, authenticated
sessions, API request, DB read/write/compute, package download, media bytes, object Class A/B/retrieval, log volume,
backup history, restore bytes ve incident operations ayrı ölçülür. Supabase MAU’su ile Neon/Render/R2 kullanıcı sayısı
aynı metrikmiş gibi toplanamaz.

Minimum safe closed test için A’nın Pro/compute/PITR yolu ile B’nin Neon/Render/R2 free/paid yolu aynı adjunct
servisleri (identity/recovery, audit/floor, scanner, package worker, notification, monitoring, backup/export,
incident support) içermelidir. “Free core” satırı safety/recovery closure yerine geçmez.

### 6.3 Cap/overage standardı

Her iki aday için tek `hard cap var/yok` hücresi yasaktır. Şu item-by-item alanlar istenir:

`compute`, `storage`, `egress`, `object operations`, `history/PITR`, `logs`, `worker/functions`, `identity/SMS`,
`monitoring`, `backup/export`, `support`, `domain`, `tax/FX`, `account suspension`, `quota deny`, `safe hold`.

Supabase Spend Cap, Neon 80/100% alert, Render billing alert ve R2 free egress ayrı mekanizmalardır. Hiçbirisi
tek başına bütün composite fatura veya provider continuity hard ceiling kanıtı değildir. `BILLING_HELD` yetkili
positive effect’i durdurabilmeli; safety, audit, restore ve export kapatılarak bütçe korunmamalıdır.

## 7. Evidence standard ve dokümantasyon düzeltmeleri

### 7.1 Kanıt etiketi normalization

Her iki finalist dosyasında şu ortak kayıt biçimi kullanılmalıdır:

`[CONFIRMED-2026] exact URL + read date + product/plan/region + quoted mechanism/limit`  
`[INFERRED] primitive ile Kavriva contract’ının birlikte okunmasından çıkan mimari sonuç`  
`[UNVERIFIED] güncel birincil kaynak, ölçüm, sözleşme veya test yok`  
`[HELD] güvenli positive effect için kanıt kapanmadı`

B’deki eski Neon values `CONFIRMED-2026` değil `UNVERIFIED/STALE-PRIMARY` olarak işaretlenene kadar cost result
karşılaştırmaya alınmamalıdır. A’daki provider-specific official evidence B’nin generic “CONFIRMED” bullet’larından
daha güçlü bir toplam sonuç olarak sayılmamalı; her iki aday aynı link/read-date/plan/region formatını kullanmalıdır.

### 7.2 Candidate-neutral hard-fail register

A’da `HF-BAAS-01..12` bulunması iyi bir traceability primitive’idir, fakat B’de karşılığı yoktur. Aşağıdaki
provider-neutral hard-fail taxonomy common fixture’a veya her iki adayın §15’ine aynı biçimde eklenmelidir:

- direct client/provider-console canonical authority;
- privileged key or owner/superuser bypass;
- no independent negative authority/protected audit/floor;
- cross-plane atomicity or object/audit partial-state denial;
- unsafe offline package/LWW/eviction;
- DB-only restore or resurrection-prone cutover;
- quarantine/scan/preview treated as approval;
- no bounded billing/account/region hold;
- no clean-room exit or non-exportable truth;
- owner SSH/dashboard/debug dependence;
- unversioned API/config/package/provider drift.

Provider names yalnızca test adapter’ında değişmeli; kabul standardı değişmemelidir.

### 7.3 External report cross-reference

Her iki finalist dosyasında “`DEBATE-008__EXTERNAL_REPORT_AUDIT.md` workspace’te yoktur” cümlesi vardır. Bu equivalence
audit oluşturulduğu anda bu cümle stale/yanlış hale gelmiştir. İki dosyada da:

- dış rapor, provider seçimi veya talimat olarak değil, kanıt kalite girdisi olarak linklenmeli;
- dış raporun `[50] yippee-bot.com`, hard-cap, tam uyum, sıfır lock-in, sıfır hesap kapanması ve AI-RLS iddiaları
  [external audit](DEBATE-008__EXTERNAL_REPORT_AUDIT.md) sınıflandırmasına göre kullanılmalı;
- finalist sonucu dış raporun önerisini yeniden üretmemeli;
- source ledger içinde resmi current pricing ve source-quality disposition ayrı tutulmalıdır.

Bu yalnız documentation fix’tir; bu audit dış rapordan kazanan seçmez.

### 7.4 Internal Operations wording

İki adayın §3 ve §12’lerine ortak olarak şu sınır eklenmelidir: provider console/dashboard, generated admin UI,
Neon branch console, Render dashboard, R2 bucket UI veya Supabase Studio Kavriva Internal Operations paneli değildir.
Kavriva paneli browser-based, online-authoritative, contextual server reauthorization, audit evidence, safe hold,
recall/suspension generation ve owner-readable recovery state sağlamalıdır. Aday dosyaları bunu no-code plan olarak
tanımlayabilir; hazır provider panelini implement edilmiş capability sayamaz.

### 7.5 Restore/exit plane completeness

A §10/§11’e API runtime artifact/config/dependency/provenance ve adjunct identity/scanner/notification/monitoring
restore/export alanlarını B ile aynı seviyede eklemeli. B §10/§11’e current official Neon history pricing/retention,
Render deploy recovery ve adjunct backup cadence/cost source’larını aynı evidence formatında eklemeli. Her iki aday:

- DB, object, audit, identity/policy, config/API artifact, package, operation/outbox ve keys-reference manifestini;
- restore quarantine, anti-resurrection floor, clean-room import ve negative tests’i;
- restore drill, exit drill, incident month ve operator/reviewer labor cost’ını

aynı `HELD`/`UNRESOLVED` standardında göstermelidir.

## 8. Sonuç ve sınır

- 15 bölüm başlıkları ile F01–F16 coverage iki dosyada da mevcut olduğundan yapısal eşitlik çekirdeği vardır.
- F03, F05, F06, F07, F12, F13 ve F14’te documentary invariants büyük ölçüde eşdeğerdir; yine de hiçbiri gerçek
  test sonucu değildir ve `HELD` kalır.
- B’nin güncel olmayan Neon pricing snapshot’ı, A’nın seçilmemiş API runtime’ı, adjunct servis görünürlüğü,
  cost-horizon satır farkı, evidence granularity farkı ve A-only hard-fail register’ı karşılaştırmayı şu anda
  eşdeğer olmaktan çıkarır.
- Provider-native RLS/Auth/PITR/transaction/presigned/durability/deploy primitive’leri iki tarafta da ürün
  çözümü, Internal Operations paneli, protected audit, full offline protocol, full restore veya zero lock-in
  sayılmayacaktır.
- İki adayın da genel sonucu `HELD`; bu audit kazanan seçmez, cost score üretmez ve Gate 4 → 5 geçişi önermez.

**Final disposition:** `KISMEN EŞDEĞER — DOCUMENTATION FIXES REQUIRED — NO WINNER`.

