# DEBATE-008 — Bağımsız Hakemlik: Tek Sahip / TCO / Operasyon Yapılabilirliği

**Durum:** PHASE-4 / NO-CODE / NO PURCHASE / NO WINNER / OVERALL HELD  
**Tarih:** 2026-09-18 (Europe/Istanbul)  
**Kapsam:** Aday A — onaylı server/API authority boundary arkasında yönetilen Supabase; Aday B — Neon managed PostgreSQL + Render Web Service üzerinde bağımsız API + Cloudflare R2.

Bu dosya yalnızca bağımsız planlama ve documentary review'dur. Kod, prototip, hesap, abonelik, satın alma,
provider seçimi, ADR veya Gate 4 → 5 geçişi oluşturmaz.

## 1. Kısa hakem hükmü

Tek teknik olmayan sahip, AI ile geliştirilen Flutter/Android-first ürün ve ilerideki TRY 2.000–3.000/ay planning
ceiling'i birlikte okunduğunda:

- Aday A, routine altyapı bakımını ve görünen core provider/account yüzeyini daha küçük tutma potansiyeline sahiptir.
  Resmî Flutter/Dart yüzeyi, managed PostgreSQL ve tek ana control-plane AI görev paketlerini başlangıçta daha az
  provider geçişiyle tanımlamaya yardım edebilir.
- Aday B, API/DB/object ayrımını baştan görünür ve daha taşınabilir kılar; fakat Neon, Render ve R2'nin üç ayrı
  core account/fatura/region/credential/control-plane yüzeyi daha fazla cross-plane reconciliation, support ve
  drift görevi doğurur.
- Bu avantajların hiçbiri protected audit/floor, quarantine, restore/exit, identity, no-owner-debug veya aylık
  güvenli toplam maliyet kanıtı değildir. Her iki aday da genel olarak HELD'dir.
- Free, alert, Spend Cap, PITR, durability, pg_dump veya başarılı deployment tek başına minimum safe Android
  operation, recovery, exit ya da TRY ceiling uyumu kanıtı değildir.

### Reversible Phase-4 working direction

Bu hakem, yalnızca sonraki eşit no-code kanıt paketi için **Aday A'yı conditionally retain edilen, geri alınabilir
Phase-4 working direction** olarak önerebilir. Bu bir kazanan, sağlayıcı onayı, satın alma veya production-ready
hükmü değildir. Yön ancak şu koşullarla geçerlidir:

1. Server/API authority boundary fiziksel olarak nasıl işletileceği provider hesabı açmadan belgelenecek ve direct
   client/service-role yolu reddedilecek.
2. Supabase ordinary DB/log/account snapshot'ından yeterince bağımsız protected audit ve non-restorable floor
   kanıtlanacak.
3. Object quarantine, scanner/preview isolation, cross-plane manifest, restore quarantine ve clean-room exit
   sahibi AI-operable biçimde tanımlanacak.
4. P0/P1/minimum safe Android/P2/P3/incident/restore/exit için USD + vergi/FX + adjunct maliyet sheet'i ve
   gerçek stop/hold davranışı kapanacak.
5. Teknik olmayan sahibin dashboard/SQL/SSH/incident-debug yoluna bağımlılığı olmayacak.

Bu şartlardan biri reject cue'ya dönüşürse working direction geri çekilir; Aday B yeniden eşit kanıt kapısından
geçirilir. Bu metin iki adaydan birini seçilmiş ilan etmez.

## 2. Okunan kanıt ve tutarlılık notu

| Kanıt | Review'daki kullanım |
|---|---|
| DEBATE-008 Finalist Common Fixture | Eşit P0–P3 workload, 12/150/25/250 MB karşılaştırma değerleri, 15 evidence pack bölümü ve F01–F16 |
| Finalist A — Supabase | API boundary, maliyet, backup/PITR, RLS, Flutter, exit ve 16 senaryo |
| Finalist B — Modular Managed | Neon/Render/R2 maliyet, üçlü failure-domain, API, object, exit ve 16 senaryo |
| External Report Audit | Dış Flutter backend raporunun birincil kaynak, hard-cap, offline, backup, region, lock-in ve hesap-kapanması denetimi |
| Stack Candidates Cost Primary Research | Dated resmi fiyat/limit/backup/region/cap sinyalleri ve ortak acceptance gates |
| Stack Architecture Fit Research | Logical boundary, no-code failure walkthrough, hard-fail register ve AI-operated owner modeli |

### 2.1 Evidence freshness uyuşmazlığı

Workspace review anında DEBATE-008 External Report Audit dosyası mevcuttur. Buna karşın iki finalist dosyasının giriş
bölümleri bu dosyanın yok olduğunu belirtmektedir. Bu bir provider davranışı değil, dossier index/freshness
uyuşmazlığıdır:

- dış audit okunmuş ve bu review'ya dahil edilmiştir;
- finalistlerdeki “audit dosyası yok” ifadeleri güncel workspace durumu değildir;
- bu uyuşmazlık sessizce PASS üretmez; finalist metadata'sı düzeltilene kadar DOCUMENT-FRESHNESS HELD'dir.

Dış audit'in kendi hükmü de provider seçmez; raporu sınırlı araştırma girdisi kabul eder ve common fixture/DEC-0034
ile çelişen direct-client, RLS-only, full-local-first, hard-cap ve sıfır-lock-in sonuçlarını reddeder.

### 2.2 Evidence dili

- CONFIRMED: 2026 tarihli resmi/primary kaynakta mekanizma veya fiyat sinyali açıkça bulunuyor.
- INFERRED: Mekanizma ile Kavriva sınırından türetilen sonuç; controlled evidence gerekir.
- OPEN / UNRESOLVED: Sağlayıcı, workload, sözleşme, vergi/FX, adjunct veya proje politikası kapanmamış.
- HELD: Güvenli olumlu etki için proof eksik, fakat explicit safe-stop/hold yolu tasarlanabilir.
- REJECT: DEC-0034 veya common fixture ile bağdaşmayan kullanım.

## 3. Dondurulmuş owner ve ürün çalışma koşulu

| Girdi | Bağlayıcı yorum |
|---|---|
| Sahip | Tek teknik olmayan sahip; kod, DB adminliği, SSH, log teşhisi ve incident repair yapmaz |
| AI | Bounded implement/review/validate task pack; root, owner, billing/legal, unrestricted SQL veya service key authority'si yok |
| Mobil | Flutter; Android-first, iOS later |
| Web | Browser-based Internal Operations; provider Dashboard ürün admin paneli değildir |
| Otorite | High-consequence mutation online-authoritative; client/cache/push/local DB kanonik authority değildir |
| Offline | Seçili motorcycle/task için sürümlü bounded package; full-library sync yok |
| Bütçe | TRY 2.000–3.000/ay ileri dönem planning ceiling'i; ödeme/plan onayı değil |
| Fiyat dili | USD resmi liste fiyatları; TRY kur, KDV/VAT, card/FX ve store ücretleri OPEN |
| İşlem sınırı | Hesap açma, satın alma, provider seçimi, kod/prototip yok |

Sahip yalnız plain-language approval/hold, legal/payment/account-owner kararı ve AI özetini okuyabilir. Dashboard
teknik onarımı, SQL/migration/restore cutover, object cleanup, SSH/container/network/log repair ve root/service-role
taşıması owner işine dönüşürse ilgili kullanım bu modelde REJECT; AI-operable ama kanıtsızsa HELD'dir.

## 4. Aday operating-model özeti

| Boyut | Aday A — Supabase arkasında API | Aday B — Neon + Render + R2 |
|---|---|---|
| Core canonical plane | Supabase PostgreSQL adayı | Neon managed PostgreSQL |
| Sensitive authority | Approved server/API; fiziksel runtime OPEN | Render Web Service üzerinde bağımsız API zorunlu |
| Client | Flutter/browser genel DB/object authority almaz | Flutter/browser yalnız API ve scoped object handle görür |
| Defense-in-depth | Grants + RLS + Storage policy; service_role yalnız server | DB role/RLS + runtime identity + R2 policy/handle |
| Object plane | Supabase Storage; quarantine ayrıca kurulmalı | R2; transport/storage, scanner veya approval authority değil |
| Protected audit/floor | Independent custody adjunct OPEN | Üç core'dan ayrı adjunct OPEN |
| Offline | Flutter local operation/package protocol proje işi | Aynı; provider SDK coupling daha az |
| Core account surface | En az bir Supabase org/project; gerçek toplam OPEN | Neon + Render + Cloudflare: en az üç core plane |
| Routine infra burden | Managed core nedeniyle görece düşük olabilir | Managed DB/object olsa da API runtime ve üçlü drift/support yüzeyi |
| Portability | PostgreSQL/pg_dump başlangıç avantajı; Auth/Storage/config ayrıca | PostgreSQL + S3-compatible object avantajı; API/identity/audit ayrıca |
| Documentary status | HELD; unpartitioned BaaS kullanımı reject cue | HELD; core üçlü ve adjunct closure yok |

Her iki composition da identity/recovery, contextual policy, protected audit/floor, quarantine/scanning,
package builder, notification, observability, backup/export/clean-room ve emergency negative authority düzlemlerini
ayrıca göstermelidir.

## 5. Hesap, fatura, region ve failure-domain hakemliği

### 5.1 Hesap/fatura sayısı

| Ölçüm | Aday A | Aday B | Owner/TCO hükmü |
|---|---|---|---|
| Bilinen core billing/control-plane | Supabase organization/project: en az 1; Pro/Team/compute/PITR ayrı kalemler olabilir | Neon organization + Render workspace/service + Cloudflare account/bucket: en az 3 | B'nin aynı üründe üç provider billing/login/policy yüzeyi vardır |
| API runtime hesabı | Authority boundary runtime'ı OPEN; Edge Function veya bağımsız runtime seçilmedi | Render Web Service core runtime'ın parçası | A tek hesap varsayımını kapatmamıştır; B'nin üçlü core sayısı daha nettir |
| Protected audit/floor | Bağımsız custody/provider/account zorunlu; seçilmedi | Bağımsız custody/provider/account zorunlu; seçilmedi | Her ikisinin gerçek minimumu finalistlerde eksiktir |
| Quarantine/scanner/preview | Ayrı logical/failure-domain service gerekir; seçilmedi | Ayrı service/identity/network gerekir; seçilmedi | Adjunct sayısı ve fatura etkisi UNRESOLVED |
| Identity/session/recovery | Supabase Auth veya başka composition; exact contract OPEN | Core üçlü bunu sağlamaz; ayrıca identity gerekir | B ek plane'i açıkça gösterir; A integrated görünüm yanlış güven vermemeli |
| Observability/notification/export | Log drain/monitoring/notification/export custody ayrıca olabilir | Her core ve adjunct için telemetry/alert/export path | Incident headline fiyatları her ikisinde de eksik |

**Ölçüm sonucu:** Aday A'nın görünen core account sayısı daha küçük olabilir; fakat “tek hesap, tek fatura, tek
recovery” değildir. B'nin üç core hesabı daha şeffaftır; adjunct'larla birlikte her iki adayın gerçek sayısı
UNRESOLVED'dır. Hesap sayısı tek başına güvenlik veya winner skoru değildir.

### 5.2 Region ve blast radius

- Aday A tek primary Supabase region'ı seçer; 2026 snapshot'ında Türkiye region'ı listelenmemiştir. Europe etiketi
  Türkiye saklama, GDPR/KVKK compliance veya backup/object/audit residency kanıtı değildir.
- B'de Neon, Render ve R2 region/jurisdiction semantiklerinin her biri ayrıdır. R2 eu/us/fedramp seçimi,
  Render/Neon region veya hukuki uyumun yerine geçmez; location hint best-effort'tur.
- A'nın tek control-plane blast radius'u daha büyük olabilir; B'nin ayrışmış plane'leri provider arızasını
  sınırlayabilir. Buna karşılık B'de partial/unknown/reconcile ve yanlış “system healthy” riski artar.
- Her iki adayda primary outage, backup region, negative authority ve restore cutover kanıtı HELD'dir.

### 5.3 Zorunlu failure states

Her iki aday owner-readable şekilde en az şu durumları göstermelidir:

SERVICE_UNAVAILABLE, ACCOUNT_HELD, BILLING_HELD, OUTCOME_UNKNOWN, OBJECT_QUARANTINE, AUDIT_HELD,
RESTORE_QUARANTINE, KEY_COMPROMISED, EXPORT_PARTIAL.

Provider Dashboard'daki green project bu ürün etkilerini açıklamaz. Positive publication, approval, recall veya
safety mutation bu durumlardan biri açıkken otomatik devam edemez.

## 6. Yönetim paneli ayrımı

| Panel | Aday A | Aday B | Kural |
|---|---|---|---|
| Provider Dashboard | Supabase Studio/org/billing/backup/config | Neon, Render ve Cloudflare ayrı console | Provider paneli product approval/publish/recall/audit authority değildir |
| Internal Operations | Approved API üzerinden browser | Approved Render API üzerinden browser | UI/cached role/hidden button authority değildir; commit reauth şart |
| Billing view | Supabase plan/cap/usage; cap dışı kalemler ayrıca | Üç provider usage/alert/fatura; composite cap kanıtlanmadı | Owner plain-language cost/hold görür, technical mutation yapmaz |
| Restore/exit view | DB/object/audit/floor/config/package manifest | Neon/R2/Render/artifact/audit manifest | Dashboard restore success = cutover değildir |
| Incident view | Supabase + adjunct durumları | Üç provider + adjunct correlation | AI runbook; owner debug yok |

Studio'nun admin paneli olması veya üç provider console'unun owner tarafından elle yönetilmesi REJECT cue'dur.
Provider console ile product operations paneli ayrı olmalıdır. Her iki modelde aynı operation ID, policy version,
generation ve evidence digest iki görünüm arasında bağlanmalıdır.

## 7. Dated cost/limit snapshot ve gizli adjunctlar

### 7.1 Aday A — Supabase

| Kalem | 2026 resmi sinyal | TCO/operasyon okuması |
|---|---|---|
| Free | 0 USD; 2 active project; 50K MAU; 500 MB DB; 5 GB egress; 1 GB file | Exploration; auto backup/PITR yok, 1 hafta pause, 50 MB max upload, 1-day API/DB logs, platform audit/metrics yok |
| Pro | 25 USD/ay; first project; additional project from 10 USD; 100K MAU; 8 GB disk; 250 GB egress; 100 GB file | Paid baseline olabilir; 10 USD compute credit Micro için, bütün composition için değil |
| Compute | Micro 10, Small 15, Medium 60 USD gibi seviyeler | Compute Spend Cap dışı kalabilir; scale bütçesi ayrıca |
| Backup | Pro 7, Team 14, Enterprise up to 30 gün daily DB backup | Storage object, independent audit/floor, identity/config/package değil |
| PITR | Pricing snapshot yaklaşık 100 USD/ay per 7-day retention; research snapshot 14/28 gün için yaklaşık 200/400 USD; Small compute gerekir | PITR paid add-on; daily backup ile aynı anda değil; downtime/RPO/RTO ve object/audit recovery OPEN |
| Team/support | 599 USD/ay; longer logs/backups ve daha geniş support/assurance | Solo owner için zorunluluk varsayılmaz; ceiling etkisi ayrı |
| Usage | MAU, disk, egress, storage, functions, realtime, image transform ve ek proje metered | P2/P3/incident total workload olmadan çıkarılamaz |

Supabase Spend Cap yalnız belirli usage item'larında over-quota kullanımını kısıtlar. Compute, branching/read-replica
compute, custom domain, IOPS/throughput, IPv4, log-drain hours/events, MFA phone ve PITR kapsam dışıdır. Cap,
tüm invoice veya tüm failure mode'lar için hard ceiling değildir.

### 7.2 Aday B — Neon + Render + R2

| Core | 2026 research snapshot resmi sinyali | TCO/operasyon okuması |
|---|---|---|
| Neon Free | 10 project; 50 CU-hour/project/month; 0.5 GB/project; 10 branch/project; 5 GB egress | Exploration; paid history/compute/storage/egress workload'a bağlı |
| Neon paid | Launch 0.106 USD/CU-hour, Scale 0.222 USD/CU-hour son açık resmi rate; approval'da tekrar okunmalı | 80/100% spending limit e-mail alert; genel invoice hard-cap değil |
| Render Web Service | Free 0 USD; örnek paid 7 USD (512 MB'a kadar) ve 25 USD (1 CPU/2 GB); Pro workspace 25 USD sinyali | Runtime/workspace/bandwidth/log/deploy/support ayrı |
| Render metered | 5 GB sonrası yaklaşık 0.15 USD/GB bandwidth; persistent disk yaklaşık 0.25 USD/GB-month | Composite cap kanıtlanmamış |
| R2 Standard | 0.015 USD/GB-month; free 10 GB-month; 1M Class A ve 10M Class B free | Ucuz object storage; versions/orphans/lifecycle/backup/ops ayrıca |
| R2 operations | Class A 4.50 USD/million, Class B 0.36 USD/million; IA 0.01 USD/GB-month + 0.01 USD/GB retrieval; direct internet egress free | Egress-free total bill veya hard cap değildir; budget alert hard-cap değildir |

Neon, Render ve R2 aynı invoice veya billing contract değildir. “R2 egress 0” ile “Aday B aylık 0” aynı şey
değildir.

### 7.3 Gizli/adjunct maliyetler

| Adjunct | Neden gerekir | Aday A | Aday B |
|---|---|---|---|
| Identity/session/recovery | Auth, revocation, security epoch, step-up | Supabase Auth olsa bile policy/rotation/recovery ayrıca | Core üçlü sağlamaz; ayrıca identity |
| Contextual API runtime | Sensitive mutation, idempotency, generation fence | Physical runtime OPEN | Render runtime core; instance/worker/deploy/support maliyeti |
| Protected audit/floor | Restore/account compromise sonrası anti-resurrection | Independent custody şart | Independent custody şart |
| Quarantine/scanner/preview | Malware/archive/SSRF/renderer isolation | Storage upload bunu kapatmaz | R2 upload bunu kapatmaz |
| Object backup/export | DB backup object bytes'ı kapsamaz; durability backup değildir | Storage bytes/manifest/restore ayrıca | R2 versions/manifest/clean-room ayrıca |
| Observability | Incident evidence ve provider drift | Log drain/retention/monitoring ayrıca | Üç core correlation ve monitoring ayrıca |
| Notification | Push/email/SMS yalnız projection/hint | Ayrı provider/usage | Ayrı provider/usage |
| Package builder/worker | Bounded offline package, outbox, reconcile | Function/worker/runtime OPEN | Render worker/başka runtime OPEN |
| Domain/DNS/TLS | Endpoint ve outage boundary | Custom domain ayrı | Render/Cloudflare/DNS ayrı |
| Support/SLA | No-owner-debug escalation | Free community, Pro email, Team priority/SLA sinyali | Üç provider support path seçilmedi |
| Clean-room | Re-encryption, validation, reviewer ve alternate environment | DB dump + objects/config/audit/floor | pg_dump + R2 + Render artifact/config/audit/floor |
| Flutter/mobile delivery | Android/iOS build/store/device/CI | SDK/native/plugin/changelog drift | HTTPS API coupling azalır; Flutter/toolchain kalır |
| Turkey cost | KDV/VAT, FX, card, withholding, store | OPEN | OPEN; çoklu invoice etkisi |

Protected audit, quarantine, API boundary, restore/exit, identity ve no-owner-debug closure mandatory safety work'tür.
Convenience Realtime, advanced transforms, analytics, premium AI ve extra regions safety closure'dan sonra
deferrable/optional olabilir.

## 8. Cost horizons: P0, P1, minimum safe Android, iOS, P2, P3, incident, restore, exit

Bu tablo satın alma teklifi değildir. USD sinyalleri dated research'tir; TRY ceiling için güncel kur, vergi, card ve
provider invoice path ayrıca ölçülmelidir.

| Horizon / olay | Aday A | Aday B | Disposition |
|---|---|---|---|
| P0 — 0 user / planning | 0 USD çalışma; account/paid plan yok; evidence/cost/runbook hazırlanır | Aynı; üç provider hesabı açılmaz | Documentary ALLOW; code/account/purchase yok |
| P1 — 100 closed/internal | Free exploration mümkün ama backup/PITR, logs, audit/metrics ve 50 MB upload sınırıyla safe production değil. Pro 25 USD baseline; adjunctlar OPEN | Free core exploration olabilir; identity/audit/quarantine/backup/monitoring toplamı ve Render runtime closure yok | HELD; free ≠ safe closed-test |
| Minimum safe Android | Paid baseline + API/policy + independent audit/floor + quarantine + object backup + restore/exit + observability + package builder. PITR seçilirse 100 USD+ ve Small compute; total UNRESOLVED | Neon compute/history + Render API/workspace/bandwidth + R2 bytes/ops + aynı adjunctlar; composite cap yok; total UNRESOLVED | HELD; safe total yok |
| iOS later | Backend benzer; Apple/macOS/build/store/device/CI maliyetleri provider table dışında | Aynı; HTTPS API client migration'ı ayırabilir | OPEN; backend winner sonucu yok |
| P2 — 10.000 active | 100K MAU included egress/media/compute/storage/audit/export maliyetini sıfırlamaz; PITR/scale/support yeniden ölçülür | CU, Render compute/bandwidth/log, R2 storage/ops ve adjunct volume artar | HELD; workload measurement yok |
| P3 — 50.000 active | Egress/media/compute/retention/incident ve Team/assurance ihtiyacı bilinmiyor; 599 USD Team varsayılmaz | Scale/replication/retention/support/egress/ops pressure bilinmiyor | HELD; forecast değil stress checkpoint |
| Incident month | Logs/retries/export/object/quarantine/PITR/custom domain/compute cap dışı artabilir | Üç ayrı alert/billing ve adjunct retry/export birleşik hard-cap değil | HELD; positive work safe-hold'a gider |
| Restore drill | DB daily/PITR Storage bytes, audit/floor, identity/config/package'ı geri getirmez; project downtime ve quarantine gerekir | Neon history DB plane; R2 object/manifest, Render artifact/config, audit/floor/identity ayrıca | HELD; restore proof yok |
| Exit drill | pg_dump/SQL başlangıçtır; Auth/Storage/Functions/config/audit/floor/object clean-room test edilir | pg_dump + R2 S3 export + Render artifact/config; provider semantics adapter ister | HELD; clean-room negative test yok |

### 8.1 Cost sınıfı

- **Mandatory now (doc-only):** cost BOM, account/region map, authority boundary, owner-readable hold states, adjunct inventory.
- **Mandatory later:** API/policy, protected audit/floor, quarantine, package closure, identity recovery, backup/exit/restore drill, no-owner-debug.
- **Deferrable:** longer PITR/history, extra region/read replica, premium support, advanced log drain, broad transforms/branches.
- **Optional:** convenience Realtime, dashboard cosmetics, noncritical analytics, premium AI, nonessential media.
- **Scale-triggered:** compute/CU, storage, egress, MAU, object Class A/B, retrieval, logs, scanner, notification, support/HA.
- **Contingency:** incident month, account recovery, clean-room environment, re-encryption and emergency review.
- **Separate:** Google Play/Apple accounts, payment processor, domain, SMS/e-mail, device lab, CI/macOS and legal/tax/accounting.

## 9. Harcama sınırı gerçekliği ve safe budget-hold

| Kontrol | Aday A | Aday B | Hüküm |
|---|---|---|---|
| Hard cap | Spend Cap belirli usage item'larını quota sonrası kısıtlar | Neon/Render/R2 sinyalleri alert/usage metering ağırlıklı; composite stop yok | Hiçbiri tüm invoice hard ceiling'i değil |
| Cap dışı risk | Compute, PITR, domain, IOPS/throughput, IPv4, log drain, MFA phone | Neon history/compute, Render workspace/service/bandwidth/disk, R2 IA/ops/versions ve adjunct | Safety kapatmadan stop/hold gerekir |
| Free | Bill yok ama pause/quota/no-backup/no-audit availability ve recovery kanıtı değil | Free quotas/alert transitions safe production kanıtı değil | No invoice ≠ no failure |
| Incident | Cap açık olsa da cap dışı kalemler sürer | Üç billing path ve adjunct retry/export sürer | BILLING_HELD şart |
| Owner action | Technical cap tuning/console repair yasak | Aynı, üç provider nedeniyle daha kritik | AI-operable stop veya REJECT |

TRY 2.000–3.000 ceiling için aynı sheet'te subscription, compute/CU, DB disk/history/PITR, object/ops/egress,
identity, audit/floor, scanner, monitoring, notification, restore/exit contingency, tax/FX/card ve incident headroom
yer almalıdır. Total ve safe-hold ceiling altında kanıtlanmıyorsa HELD'dir. Mandatory safety plane'ini kapatıp fiyata
sığdırmak REJECT'tir. Unavoidable unbounded overage ve positive work'ü durduracak mekanizma yoksa ilgili kullanım
REJECT'tir.

### 9.1 Ortak safe budget-hold state machine

1. New publication, approval, high-consequence mutation ve nonessential upload durur.
2. BILLING_HELD veya ACCOUNT_HELD owner-readable reason ile görünür olur.
3. Accepted operation ID, audit intent, local pending work ve son güvenli package korunur.
4. Safe-stop/history/teaching/recovery closure policy izin verdiği kadar sürer.
5. Blind retry, silently spend, quota bypass veya owner dashboard repair yapılmaz.
6. Billing/provider durumu doğrulanıp reconcile edilmeden positive path açılmaz.

Bu state machine uygulanamazsa maliyet riski owner modeline aykırı REJECT riskidir.

## 10. Support, on-call ve no-owner-debug

Supabase managed DB/Auth/Storage, OS patching ve database-process bakımını azaltabilir. Free community, Pro email,
Team priority/SLA ve Enterprise support sinyalleri mevcut olsa da plan seçilmemiştir. API/policy, RLS/grants/
functions, key compromise, quarantine, audit/floor, object consistency, restore/exit, billing/cap ve Flutter
maintenance yine bizim ürün operasyonumuzdur.

B'nin API/DB/object sınırları daha görünürdür; fakat Neon, Render, Cloudflare ve adjunct support/account/region/
billing path'leri aynı SLA veya incident queue değildir. Cross-provider correlation, deployment/DB/object/
identity mismatch ve support escalation ayrı task pack'ler ister.

| Incident | AI output | Owner-facing output |
|---|---|---|
| Account/billing hold | Affected plane, stopped positive effects, known-safe package, next human/legal action | Plain-language hold/reason; repair talebi yok |
| Key compromise | Credential class, affected scope/generation, rotation/handle state, pending op disposition | Security approval; raw secret yok |
| Restore mismatch | Manifest diff, RESTORE_QUARANTINE, no-cutover reason, forward recovery | Hangi verinin authority olmadığı |
| Object/quarantine failure | Object state, digest, lineage, cleanup/review state | Orijinalin yayınlanmadığı ve next action |
| API/provider outage | Service state, safe history/package, retry/reconcile status | False success yok |
| Partial exit | Planes included/missing, PARTIAL label, source untouched | Exit'in tamamlanmadığı |

Provider support, Dashboard, SQL, SSH veya owner intervention bu çıktının yerine geçiyorsa HELD; tek recovery yolu
bunlarsa REJECT'tir. Free/community support production incident closure kanıtı değildir. Paid support/SLA deferrable
gibi görünse de owner-independent recovery için gerekebilir; seçilmeden “destek var” denemez.

## 11. AI görev paketlenebilirliği ölçümü

Her AI task pack şu 10 alanı taşımalıdır:

1. objective ve exact scope;
2. allowed operations;
3. forbidden operations;
4. credential class ve expiry/scope;
5. read-only/dry-run başlangıcı;
6. operation ID, expected version/generation ve payload fingerprint;
7. hard stop / hold condition;
8. evidence artifact, digest/checkpoint ve reviewer;
9. safe forward recovery / reconciliation;
10. owner plain-language handoff ve irreversible action için bağımsız approval.

| AI task-pack yüzeyi | Aday A | Aday B | Hakem notu |
|---|---|---|---|
| Authority scope | Server/API zorunlu, fiziksel runtime OPEN; direct Data API DENY | Render API zorunlu; Neon/R2/identity scope'ları ayrı | B boundary daha görünür; ikisi HELD |
| Credential minimization | Public/session, server identity, service_role, migration, Storage/audit ayrımı | Render→Neon, Render→R2, identity, audit, presigned, provider owner ayrımı | B'de rotation handoff daha geniş |
| Cross-plane state | Supabase transaction + Storage + external audit | Neon transaction + R2 + Render artifact + external audit | A integrated atomicity trap'i; B daha çok handoff |
| Cost task | Spend Cap coverage/exclusions, PITR/compute | Üç billing path, R2/Neon/Render usage | Universal hard cap yok |
| Restore task | DB/PITR + Storage + floor + identity/config/package | Neon history + R2 + Render artifact/config + floor | İkisi clean-room olmadan HELD |
| Exit task | pg_dump + Auth/Storage/Functions/config/audit/floor | pg_dump + R2 + Render artifact/config/audit/floor | Negative import test yok |
| Drift watch | Supabase changelog/exposure/RLS/Flutter | Neon/Render/R2/API/Flutter | B watch list daha geniş |
| Owner handoff | Bir provider özeti mümkün; Studio yine authority değil | Üç provider özeti korele edilmeli | A routine burden düşük olabilir |
| Overall packageability | MEDIUM / CONDITIONAL / HELD | LOW–MEDIUM / CONDITIONAL / HELD | Aggregate score veya security PASS değildir |

Sonraki no-code evidence pack'te 10/10 alan, forbidden scope, explicit stop state, PARTIAL/UNKNOWN/RECONCILING/
RESTORE_QUARANTINE/BILLING_HELD artifact'ı, owner handoff, independent reviewer ve no-dashboard/SSH completion
işaretlenmelidir. “AI geliştirir, sahibi uğraşmaz” bu kapanmadan INFERRED kalır.

## 12. Android-first minimum safe operation

Her aday için minimum safe Android operation:

1. exact client/release/schema/generation manifest;
2. selected-task bounded package ve safe-stop/recovery closure;
3. 12 MB compact transfer, 25 MB cellular confirmation, 250 MB cache ve 150 MB optional media'nın fixture
   comparison olduğu; final limit olmadığı;
4. required compact core'un cache pressure altında evict edilememesi;
5. device loss/clone/restore için truthful LOCAL_LOSS/HELD;
6. online reauthorization, recall/suspension generation ve outcome-unknown reconciliation;
7. Flutter plugin/native dependency, Android runner/build ve provider/API drift watch;
8. backup/restore/export/exit'in Android generation'ıyla uyumu;
9. owner'ın teknik repair yapmadan safe-stop sonucu görmesi.

| Android/Flutter alanı | Aday A | Aday B |
|---|---|---|
| Client integration | Resmi Dart/Flutter Database/Auth/Storage/Realtime/Functions surface | HTTPS API + scoped object handle; vendor SDK coupling az |
| Native maintenance | Supabase package, Flutter plugin, Data API/RLS/Storage/changelog | Flutter/toolchain + API contract + Render/Neon/R2 semantics |
| Offline correctness | SDK bounded package/durable reconciliation kanıtlamaz | Provider SDK bunu sağlamaz; protocol tamamen project contract |
| API drift | Exposure/grants/default/changelog watch | Üç provider API/pricing/region + API contract watch |
| Disposition | HELD | HELD |

## 13. F01–F16 eşit failure-scenario hakemliği

| ID | Aday A | Aday B | Kritik hüküm |
|---|---|---|---|
| F01 stale role | API commit reauth + RLS defense; live proof yok → HELD | Render API reauth + DB/object scope; live proof yok → HELD | Cached role/direct client authority → REJECT |
| F02 key leak | service_role server-only, rotate/impact/signed handle; drill yok → HELD | Render→Neon/R2/identity keys and presigned handle drill yok → HELD | Client/AI/root exposure → REJECT |
| F03 lost response | Postgres idempotency/outbox + same op lookup; drill yok → HELD | Neon ledger + API reconcile; drill yok → HELD | Duplicate/guessed success → REJECT |
| F04 object partial | Storage quarantine/orphan + external audit; drill yok → HELD | R2 orphan/manifest/scanner; drill yok → HELD | Upload/scan success official truth → REJECT |
| F05 publish/suspend race | Generation fence + negative authority; proof yok → HELD | Aynı; Neon/Render otomatik sağlamaz → HELD | Newer negative generation temizlenirse REJECT |
| F06 wrong offline delta | Package manifest/anti-rollback/fallback proof yok → HELD | API verifier/cache closure proof yok → HELD | Mixed/full-library authority → REJECT |
| F07 provenance conflict | Durable op + expected version + preserve-both; drill yok → HELD | Aynı; provider handoff daha geniş → HELD | High-consequence silent LWW → REJECT |
| F08 old restore | DB/PITR Storage/floor'dan ayrı; quarantine proof yok → HELD | Neon/R2/floor/identity/config split; proof yok → HELD | Old snapshot live/recalled truth revival → REJECT |
| F09 cross-plane mismatch | DB backup Storage/audit/config'i kapsamaz; manifest yok → HELD | Neon/R2/Render manifest yok → HELD | Mismatch sonrası cutover → REJECT |
| F10 billing suspend | Spend Cap partial; excluded cost stop/hold yok → HELD | Üç billing path composite cap/hold yok → HELD | Safe hold yok veya unbounded spend → REJECT |
| F11 outage/region | Single control-plane + external negative authority proof yok → HELD | Three-provider fallback/correlation proof yok → HELD | Owner SSH/Dashboard repair → REJECT |
| F12 clean-room exit | SQL + Auth/Storage/Functions/config/audit/floor proof yok → HELD | SQL + R2 + Render + floor proof yok → HELD | One dump/clone complete exit → REJECT |
| F13 ordinary AI task | Narrow API role/evidence pack; execution proof yok → HELD | Narrow multi-plane role; proof yok → HELD | Broad secret/owner/root context → REJECT |
| F14 AI halfway | PARTIAL/UNKNOWN/RECONCILING defined; rehearsal yok → HELD | Same, more handoff; rehearsal yok → HELD | Owner debug/blind retry → REJECT |
| F15 quota/incident | Cap dışı compute/PITR/others; total yok → HELD | Alerts not composite cap; total yok → HELD | Safety dependent unbounded spend → REJECT |
| F16 provider drift | Changelog/exposure/RLS/Flutter gate operational değil → HELD | Neon/Render/R2/API/Flutter gate operational değil → HELD | Silent production drift → REJECT |

## 14. Kritik hold/reject koşulları

### Ortak REJECT

1. Flutter/browser direct general DB/object write, public/original object, global bucket credential veya cached role
   canonical authority yapılırsa.
2. RLS, Storage policy, permission veya admin SDK tek başına approval, provenance, recall, separation-of-duties
   veya protected audit sayılırsa.
3. DB backup/clone/PITR/durability ile object, audit, identity, policy, config, package ve floor kendiliğinden
   restore edilmiş varsayılırsa.
4. Restore sonrası recall, revoke, deletion veya accepted operation yeniden authority olabiliyorsa.
5. Audit/floor aynı mutable snapshot/account'ta ve actor/admin ikisini birden silebildiği halde positive effect açılırsa.
6. Quarantine/scanner/preview veya signed/presigned URL technical correctness/approval authority yapılırsa.
7. Owner'ın SSH, unrestricted SQL, Dashboard repair, log diagnosis veya provider incident repair'i zorunluysa.
8. AI'ya root/owner/service-role/global object/billing/legal credential verilirse.
9. Cap/alert bilinmezken unavoidable unbounded overage veya safety plane'i kapatma varsayılırsa.

### HELD

Mechanism ve safe hold tasarlanabilir fakat controlled proof yoksa; exact plan/retention/region/support/tax/FX/
PITR/egress/adjunct cost güncel değilse; identity/audit/floor/scanner/monitoring/package/API runtime provider'ı
açık değilse; restore/exit rehearsal yoksa; finalist metadata'sı ile mevcut workspace çelişiyorsa HELD kalır.

### Aday A özgü

service_role/secret client, repository, log veya AI context'e girerse; Studio/Data API product authority yapılırsa;
Spend Cap tüm faturanın hard cap'i diye sunulursa; DB backup Storage/audit/floor recovery diye okunursa; physical
API runtime, independent audit/floor veya quarantine “integrated olduğu için hazır” varsayılırsa REJECT.

### Aday B özgü

Render API optional olur ve direct client/Neon/R2 path açık kalırsa; owner/BYPASSRLS/global R2 key task pack'e
girer; R2 egress-free/durability global cap veya audit immutability sayılırsa; üç core support/billing/region
owner tarafından elle yönetilirse; adjunctlar gizlenirse REJECT.

## 15. Reversible direction için minimum next evidence pack

1. A ve B için aynı USD BOM: subscription, compute/CU, storage, egress, operations, PITR/history, logs, support,
   identity, audit, scanner, monitoring, notification, domain, tax/FX, incident contingency.
2. Her provider/adjunct için account, billing owner, region/jurisdiction, credential ve support map.
3. Provider Dashboard ile Internal Operations authority separation ve owner-readable state dictionary.
4. F01–F16 için expected ALLOW/DENY/HOLD/UNKNOWN, evidence owner ve stop path.
5. 10-field AI task-pack; no secret/root/owner context; independent reviewer.
6. Android package/cache/wrong-base/device-loss/outcome-unknown closure.
7. P1 minimum safe closed-test; Free/Pro transition ve budget-hold evidence.
8. P2/P3 workload measurement: MAU/egress/media/DB/ops/log/scan/notification/restore/exit.
9. Incident-month budget-hold ve provider outage owner-facing report.
10. Old revoked/deleted/recalled/accepted-operation state ile restore quarantine drill.
11. Normal account/provider dışı clean-room export/import; negative authorization/deletion/classification/suspension tests.
12. Flutter/Android plugin, API/schema, provider changelog ve release graph watch.
13. External Report Audit link/index mismatch'in iki finalistte resolution'ı.
14. Independent reviewer sign-off; unresolved critical row HELD kalır, fiyat/convenience ile telafi edilmez.

## 16. Overall disposition

| Hakem ekseni | Aday A | Aday B |
|---|---|---|
| Solo owner routine burden | Daha düşük olma potansiyeli; managed core ve az görünen provider surface | Daha yüksek cross-provider burden; boundaries daha açık |
| TCO visibility | Headline fiyat kolay; adjunct/cap-dışı trap var | Üç provider açık; composite total/support daha karmaşık |
| Budget proof | Yok; Spend Cap partial | Yok; alert/usage composite hard cap değil |
| Flutter/Android | Resmi Dart/Flutter surface; SDK/native/changelog drift | HTTPS API coupling düşük; Flutter/toolchain yine var |
| No-owner-debug | Managed core yardım eder; product/recovery proof dışarıda | Three-provider incident/support correlation daha zor |
| Portability | Relational core iyi; integrated features/objects/config/auth ayrı | SQL/S3/API contract iyi; provider/adjunct state ayrı |
| Current result | HELD | HELD |

**Bağımsız hakem sonucu:** Aday A, yalnızca solo owner'ın routine managed burden'ını azaltma ihtimali nedeniyle
sonraki **reversible Phase-4 working direction** olarak tutulabilir. Aday B, API/portability sınırlarının daha
görünür olması nedeniyle eşit comparison candidate olarak korunur. Bu ifade winner, provider approval veya satın
alma kararı değildir. F01–F16 ve minimum safe TCO/owner-operability kanıtları kapanana kadar production readiness,
ADR veya Gate 4 → 5 sonucu yoktur.

## Official / primary source ledger

- [Supabase Pricing](https://supabase.com/pricing), [Control your costs](https://supabase.com/docs/guides/platform/cost-control), [Database Backups](https://supabase.com/docs/guides/platform/backups), [Billing FAQ](https://supabase.com/docs/guides/platform/billing-faq)
- [Supabase Regions](https://supabase.com/docs/guides/platform/regions), [Securing the Data API](https://supabase.com/docs/guides/api/securing-your-api), [RLS](https://supabase.com/docs/guides/database/postgres/row-level-security), [Storage downloads](https://supabase.com/docs/guides/storage/serving/downloads), [Dart/Flutter](https://supabase.com/docs/reference/dart/introduction), [Changelog](https://supabase.com/changelog)
- [Neon usage pricing](https://neon.com/blog/new-usage-based-pricing), [Neon PITR](https://neon.com/blog/announcing-point-in-time-restore), [Neon spending limits](https://neon.com/blog/introducing-organization-spending-limits), [Neon PostgreSQL export](https://github.com/neondatabase/website/blob/main/content/docs/guides/export-neon-postgres-compatible.md)
- [Render pricing](https://render.com/pricing), [Render Web Services](https://render.com/docs/web-services), [Render regions](https://render.com/docs/regions), [Render PostgreSQL backups](https://render.com/docs/postgresql-backups)
- [Cloudflare R2 pricing](https://developers.cloudflare.com/r2/pricing/), [R2 presigned URLs](https://developers.cloudflare.com/r2/api/s3/presigned-urls/), [R2 consistency](https://developers.cloudflare.com/r2/reference/consistency/), [R2 durability](https://developers.cloudflare.com/r2/reference/durability/), [R2 data location](https://developers.cloudflare.com/r2/reference/data-location/), [R2 usage billing](https://developers.cloudflare.com/billing/understand/usage-based-billing/)

### Repository evidence

- [DEBATE-008 common fixture](DEBATE-008__FINALIST_COMMON_FIXTURE.md)
- [DEBATE-008 Finalist A](DEBATE-008__FINALIST_A_SUPABASE.md)
- [DEBATE-008 Finalist B](DEBATE-008__FINALIST_B_MODULAR_MANAGED.md)
- [DEBATE-008 external report audit](DEBATE-008__EXTERNAL_REPORT_AUDIT.md)
- [DEBATE-008 cost primary research](DEBATE-008__STACK_CANDIDATES_COST_PRIMARY_RESEARCH.md)
- [DEBATE-008 architecture-fit research](DEBATE-008__STACK_ARCHITECTURE_FIT_RESEARCH.md)
