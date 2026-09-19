# DEBATE-008 — Finalist A: Yönetilen Supabase

**Durum:** `DOCUMENTARY FINALIST DOSSIER / PHASE-4 / NO-CODE / NO WINNER / ADR NOT READY / OVERALL HELD`  
**Araştırma ve resmi kaynak kontrol tarihi:** `2026-09-18` (Europe/Istanbul)  
**Aday:** Yönetilen Supabase; onaylı server/API authority boundary arkasında  
**Yetki sınırı:** Bu dosya yalnızca planlama ve belgelemedir. Kod, prototip, executable spike, provider hesabı, satın alma,
abonelik veya ADR oluşturmaz.

## Bu dosyanın anlamı

Bu dosya `DEBATE-008__FINALIST_COMMON_FIXTURE.md` içindeki **Aday A** için eşit karşılaştırma dosyasıdır. Bir
sağlayıcı seçimi veya kazanan ilanı değildir. `PASS`, `HELD` ve `REJECT` ifadeleri yalnızca ortak fixture'daki
documentary disposition dilidir; gerçek build, restore, export, cihaz veya release kanıtı değildir.

Supabase burada ancak şu ayrımlı kompozisyon olarak incelenir:

```text
Flutter / browser client
        │  no general canonical DB or object authority
        ▼
approved server/API authority boundary
        │  contextual authorization, idempotency, audit intent, generation fence
        ▼
managed Supabase primitives
  PostgreSQL · Auth · private Storage · bounded Functions/worker use · optional Realtime
```

`RLS` ve Storage policy savunma katmanıdır; tek başına ürün yetkisi, approval, publication, recall veya protected
audit authority değildir. `service_role`/secret key yalnızca server-side kontrollü bağlamda kalır; Flutter, browser,
repository, log veya AI context'ine girmez. Doğrudan istemci kanonik otorite değildir.

### Kanıt etiketleri

- **[CONFIRMED-2026]**: 2026-09-18 tarihinde okunmuş resmi Supabase/Flutter kaynağında açıkça belirtilen mekanizma,
  limit veya fiyat.
- **[INFERRED]**: Resmi primitive'in `DEC-0034` ve ortak fixture ile birlikte okunmasından çıkan mimari sonuç; ADR
  öncesi ayrıca kanıtlanmalıdır.
- **[OPEN]**: Resmi kaynakta yeterince kesinleşmeyen, proje politikasına veya ilerideki ADR kanıtına bağlı konu.
- **[HELD]**: Güvenli pozitif etki için kanıt eksik. Bu durum kullanıcıya teknik on-call veya owner-debug görevi
  yüklemez.
- **[REJECT-IF-UNMITIGATED]**: Aşağıdaki sınır ihlal edilirse bu kompozisyonun ilgili kullanımı reddedilir.

### Bağlayıcı proje girdileri

- `DEC-0030`: tek teknik olmayan sahip, sınırlı bütçe, fiyat/cap/overage/exit görünürlüğü zorunluluğu.
- `DEC-0032`: Android-first, iOS later; TRY 2.000–3.000/ay yalnızca sonraki harcama dönemi için planlama tavanı.
- `DEC-0033`: Flutter consumer-mobile çalışma yönü; implementation veya provider ADR'si değildir.
- `DEC-0034`: canonical authority per domain, server/API mediation, bounded offline package, durable operations,
  protected audit, object boundary, non-restorable floor, tested backup/restore/export/exit.
- `DEBATE-007` ve Judge synthesis: provider-neutral boundary, restore quarantine, anti-resurrection, clean-room exit,
  owner-independent AI operation.
- `DEBATE-008__FINALIST_COMMON_FIXTURE.md`: P0–P3 eşit workload ve F01–F16 failure scenarios.

`DEBATE-008__EXTERNAL_REPORT_AUDIT.md` sonradan tamamlanmıştır. Dış rapor sağlayıcı seçimi veya talimat olarak
değil, yalnızca kaynak-kalitesi girdisi olarak kullanılır. Audit'in doğruladığı mekanizmalar korunur; hard-cap,
tam mevzuat uyumu, sıfır lock-in/hesap riski, dakikalar içinde self-host ve AI'ın RLS'yi güvenilir biçimde yazdığı
gibi aşırı kesin iddialar finalist lehine kanıt sayılmaz.

---

## 1. Exact provider products ve dated official price/limit snapshot

### 1.1 Candidate A bileşimi

| Mantıksal rol | Aday A'daki durum | Yetki yorumu |
|---|---|---|
| Transactional core | Managed Supabase PostgreSQL | Domain invariants, version/generation ve idempotency ledger için aday primitive; provider seçimi değildir. |
| Auth/session | Supabase Auth primitive'i veya ileride onaylanacak identity composition | Authenticated olmak approval/competence değildir; server-side contextual authorization gerekir. |
| Object plane | Supabase Storage, varsayılan private bucket hedefi | Storage policy byte erişimini sınırlar; quarantine veya teknik doğruluk kanıtı değildir. |
| Server/API authority | Supabase'in önünde/arkasında onaylı server/API boundary; fiziksel runtime/provider **[OPEN]** | Tüm high-consequence mutation, review, publish, recall, role/policy ve export işlemi burada yeniden yetkilendirilir. |
| Edge/worker | Sınırlı yardımcı iş, package builder veya relay adayı; **[OPEN]** | Function/worker sonucu ürün approval veya protected audit yerine geçmez. |
| Realtime/cache | Rebuildable projection veya delivery hint | Eligibility, recall, release veya history authority değildir. |
| Protected audit/floor | Supabase proje snapshot'ından yeterince bağımsız custody; fiziksel çözüm **[OPEN]** | Normal high-consequence etki, bağımsız kanıt yoksa `HELD`. |
| Quarantine/scan/render | Ayrı mantıksal/failure-domain boundary; ürün/servis henüz seçilmedi | Upload/scan/render hiçbir zaman publication veya technical correctness authority'si değildir. |

Supabase'in integrated görünümü bu rollerin hepsini tek transaction veya tek trust boundary yapmaz. Aday A ancak bu
ayrımlar korunursa incelenebilir.

### 1.2 2026-09-18 resmi fiyat ve kota sinyalleri (USD)

Kaynak: [Supabase Pricing](https://supabase.com/pricing), [Billing FAQ](https://supabase.com/docs/guides/platform/billing-faq).
Fiyat sayfası dinamik olduğundan aşağıdaki değerler **2026-09-18 resmi sayfa gözlemi**dir; TRY karşılığı değildir.

| Katman / kalem | Resmi snapshot | Kavriva anlamı |
|---|---|---|
| Free | `$0/month`; 2 active project; 50.000 MAU; 500 MB DB; 5 GB uncached egress; 5 GB cached egress; 1 GB file storage | Planlama/keşif için kullanılabilir; automatic backup/PITR yoktur ve bir hafta inactivity sonrası pause olabilir. Safety/recovery kanıtı olarak varsayılamaz. |
| Free object/operation limits | Pricing sayfasında max file upload `50 MB`; Realtime 2M messages/month, 200 peak connections, 256 KB message; Edge Functions 500K invocation | Fixture'taki 12 MB compact transfer sığabilir; 150 MB optional media tek dosya olarak Free upload sınırını aşar. Bu değerler ürün limiti olarak onaylanmış değildir. |
| Free logs/security | API/DB log retention `1 day`; platform audit logs ve metrics endpoint Free'de dahil değil; community support | Protected audit ve incident evidence için yetersiz kabul edilir; ayrı custody/runbook gerekir. |
| Pro | `$25/month` başlangıç; ilk project dahil; additional project `$10/month` seviyesinden; `$10/month` compute credit | Paid başlangıç maliyetidir; `Micro` compute `$10/month` credit ile karşılanabilir, fakat bu bütün kompozisyonun faturası veya recovery maliyeti değildir. |
| Pro included/overage | 100.000 MAU sonra `$0.00325/MAU`; 8 GB disk sonra `$0.125/GB`; 250 GB egress sonra `$0.09/GB`; 100 GB file storage sonra `$0.0213/GB` | P2/P3 workload gerçek operasyon, media, egress ve object kullanımına göre yeniden hesaplanır. |
| Pro backup/log | Daily database backups, 7 gün; API/DB logs 7 gün; email support | Günlük DB backup Storage object'larını kapsamaz; 7 gün retention RPO/RTO veya exit proof değildir. |
| Team | `$599/month` başlangıç; daily backups 14 gün; log retention 28 gün; platform audit logs/metrics ve daha geniş erişim özellikleri | Otomatik olarak gerekli veya onaylı değildir; yalnızca ileride açık bir assurance/support ihtiyacı doğarsa maliyet çalışmasına girer. |
| Enterprise | Custom | Bu dosyada fiyat veya satın alma varsayımı yapılamaz. |
| PITR | Paid plan add-on; 7 gün yaklaşık `$100/month`, 14 gün yaklaşık `$200/month`, 28 gün yaklaşık `$400/month`; en az `Small` compute gerekir | PITR ayrı bir cost/availability kararıdır; Spend Cap kapsamı dışındadır. Daily backup ile aynı anda çalışmaz; resmi docs'a göre PITR açıldığında daily backup alınmaz. |
| Compute | `Micro $10`, `Small $15`, `Medium $60` gibi saatlik/aylık seviyeler; paid plan compute credit yalnızca $10 | Compute, Spend Cap dışında olabilir. Cap açıkken bile bu kalemde sınırsız fatura varsayımı yapılamaz. |
| Diğer metered kalemler | Örnek resmi snapshot: custom domain `$10/domain/month`; log drain `$60/drain/month` + event/egress; Realtime/Edge/transform/branching ve MFA phone ayrı kalemler | Incident month, audit drain, media transform veya extra project maliyetleri ayrıca ölçülmelidir. Hiçbiri bu dosyada satın alma onayı değildir. |

### 1.3 Spend Cap ve gerçek hard-cap ayrımı

Kaynak: [Control your costs](https://supabase.com/docs/guides/platform/cost-control).

- Pro Spend Cap açıkken belirli kullanım kalemlerinde kota aşımı **engellenir**; kullanım bir sonraki billing cycle'a
  kadar kısıtlanabilir.
- Kapsanan kalemler: disk size, egress, Edge Function invocations, logs ingest/query, MAU, SSO/third-party MAU,
  Realtime messages/peak connections, Storage image transformations ve Storage size.
- **Kapsanmayan** kalemler: compute, branching/read-replica compute, custom domain, ek IOPS/throughput, IPv4, log-drain
  hours/events, MFA phone ve PITR.
- Spend Cap kapatılırsa ilgili kullanım birimi overage olarak ücretlenir. Cap bütün faturayı, bütün service plane'lerini
  veya bütün failure modes'u sınırlayan bir account-level hard ceiling değildir.
- Free plan ücret üretmemekle birlikte quota/fair-use aşımında service restriction yaşayabilir; bu da availability
  veya recovery kanıtı değildir.

**[INFERRED]** Owner-approved spend envelope açısından Aday A'da iki ayrı güvenlik kontrolü gerekir: (1) Supabase'in
Spend Cap'ini kapsanan kalemlerde açık tutmak; (2) kapsam dışı compute/PITR/domain/log/MFA ve ek servisler için bağımsız
stop/hold planı. İkisi de yoksa ilgili capability `HELD` olur; safety/recovery kapatılarak maliyet düşürülmez.

### 1.4 Vergi, kur ve ödeme belirsizliği

- Supabase faturaları USD olarak düzenlenir; kart sağlayıcısı TRY dönüşümü yapar.
- Resmi Billing FAQ, fatura adresine göre VAT/GST/sales tax uygulanabileceğini belirtir; Türkiye vergi, banka/FX,
  withholding ve kart komisyonu **[OPEN]** kalır.
- TRY 2.000–3.000/ay tavanı bu USD kalemlerini onaylamaz ve mağaza ücretlerini içermez. Her paid transition öncesi
  güncel resmi fiyat, vergi, cap kapsamı ve çıkış maliyeti yeniden okunmalıdır.

### 1.5 2026 platform değişikliklerinin fiyat/limit bakım etkisi

Kaynak: [Supabase Changelog](https://supabase.com/changelog).

- 2026-05-01 duyurusu: public schema tablolarının Data API'ye otomatik exposure davranışı yeni projelerde değişmiş,
  tüm projelerde enforcement tarihi 2026-10-30 olarak duyurulmuştur. Exposure/grants/RLS varsayımları release watch'a
  bağlanmalıdır.
- 2026-03-05 duyurusu: anon key ile OpenAPI spec erişimi kaldırılmıştır; secret/service role yalnız server-side
  kalır. API surface'i dokümantasyon export'u ile değil kontrollü contract ile izlemek gerekir.
- 2026-08-12 duyurusu: daily-backup scheduling timeout için retry/fleet isolation düzeltmesi yayınlanmıştır. Bu, backup
  başarı sinyalinin tek başına recovery proof olmadığı kuralını değiştirmez.
- 2026-09-23 için `logs.all` Management API endpoint'inin kaldırılması duyurulmuştur; current date'ten sonraki bu
  değişim nedeniyle observability runbook'ı endpoint/version watch gerektirir.
- 2026-07/08 duyuruları extension version pinning, Realtime schema ve self-host gateway davranışlarında değişiklik
  gösterir. Provider drift sessizce production anlamını değiştiremez; F16 kontrolü zorunludur.

---

## 2. Account, project, region ve billing failure-domain inventory

### 2.1 Supabase control-plane sınırları

Resmi Billing FAQ'ya göre bir Supabase organization tek bir subscription planı taşır; project, Storage/Auth/Functions/
Realtime dahil dedicated instance'tır. Bu, ürünümüzün tüm authority plane'lerinin tek fiziksel trust boundary'de olduğu
anlamına gelmez; tersine account/project control-plane failure tek bir risk sınıfıdır.

| Failure domain | İçerdiği şey | Pozitif etki kesilince hedef durum | Bağımsızlık/boşluk |
|---|---|---|---|
| Organization/billing | Plan, payment method, Spend Cap, project quota, add-ons | `BILLING_HELD`; publication ve privileged mutation durur | Payment/tax/support path Supabase control-plane'ine bağlı; owner repair planı olamaz. |
| Project control plane | Project lifecycle, dashboard, Management API, configuration | `ACCOUNT_HELD` veya `SERVICE_UNAVAILABLE` | Project deletion irreversible; transfer/restore davranışı ayrıca doğrulanır. |
| DB/compute | PostgreSQL current/history/operation data | API positive writes `HELD`; last known safe read policy uygulanır | Backup/PITR ve compute farklı maliyet/availability boundary'leridir. |
| Storage | Object bytes, buckets, signed handles, CDN/cache | New upload/finalization `HELD`; quarantine/orphan state korunur | DB backup object bytes'ı kapsamaz. |
| Auth/session | Session, identity, claims, key rotation | New sensitive operation `HELD`/`DENY` | Auth token fresh-ness ve server policy birlikte değerlendirilir. |
| Edge/worker/Realtime | Relay, package build hint, notification, projection | Rebuildable delivery state; canonical state değişmez | Function/Realtime success authority değildir. |
| Server/API boundary | Contextual authorization, idempotency, generation fence | All sensitive effects `HELD`/`OUTCOME_UNKNOWN` | Runtime/provider **[OPEN]**; bu boundary yoksa Aday A hard reject. |
| Protected audit/floor | Ordered evidence, negative generations, tombstones | High-consequence effect `HELD` | Supabase ordinary table/log'u tek custody olamaz; independent custody **[OPEN]**. |
| Quarantine/preview | Untrusted file/URL intake, scan/render, lineage | Object remains `QUARANTINED` | Supabase Storage upload acceptance bunu sağlamaz. |
| Backup/export/exit custody | Cross-plane manifest, off-site copies, clean-room import | Restore `RESTORE_QUARANTINE` | Fiziksel ürün/provider seçilmedi; evidence pack gerekir. |
| DNS/identity/keys | API hostname, OAuth/email, encryption/signing keys | New authority held; stale signed handles expire/revoke by policy | Credential recovery and legal owner actions **[OPEN]**. |

### 2.2 Region ve data residency

Kaynak: [Supabase Available regions](https://supabase.com/docs/guides/platform/regions).

- Her project bir primary region'da çalışır; primary project data'sının konumunu belirler.
- Resmi listede Frankfurt, Ireland, Paris, Zurich, London, Stockholm, Singapore ve diğer AWS bölgeleri bulunur; bu
  2026-09-18 snapshot'ında Türkiye region'ı listelenmemektedir.
- “Europe” genel region label'ı belirli bir jurisdiction kanıtı değildir; resmi docs London ve Zurich'in EU üyesi
  olmadığını açıkça belirtir. Residency ihtiyacı varsa exact region seçimi gerekir.
- Region seçimi regulatory compliance, lawful-access sonucu, backup/object/audit bölgesinin aynı yerde olduğu veya
  Türkiye'de tutulduğu anlamına gelmez. Bu konular **[OPEN]** kalır.
- Primary region failure, cross-region restore ve region change cutover'ı bu dosyada çözülmüş değildir. Yeni project,
  export/import ve current negative floor reconciliation gerektiren bir recovery event olarak ele alınır.

### 2.3 Billing/quota/account failure states

Server/API ve consumer client aşağıdaki açık durumları gösterebilmelidir; bunlar Supabase SDK hata mesajı ile örtülü
kalamaz:

- `SERVICE_UNAVAILABLE`: provider/API/region erişimi yok.
- `ACCOUNT_HELD`: organization/project veya credential/control-plane erişimi askıda.
- `BILLING_HELD`: payment, quota, Spend Cap kapsamı veya kapsam dışı metered kalem nedeniyle positive mutation yok.
- `OUTCOME_UNKNOWN`: operation server'a ulaşmış olabilir; aynı operation ID ile reconciliation gerekir.
- `RESTORE_QUARANTINE`: restored DB/object/audit/floor/policy henüz authority değil.
- `KEY_COMPROMISED`: secret/session/object handle rotation ve impact graph tamamlanana kadar positive effect hold.

Consumer tarafında güvenli durma, öğretici içerik, mevcut doğrulanmış tarihçe ve düşük riskli local capture policy ile
ayrıştırılır; hiçbir state provider outage'ı başarı gibi göstermez.

---

## 3. Client/API/database/object/worker/admin/provider-console privileged-path matrix

| Yol | İzin verilen rol | Authority kuralı | Supabase savunma katmanı | Deny/hold koşulu |
|---|---|---|---|---|
| Flutter public/publishable/anon key | Login, açıkça kanıtlanmış düşük riskli read veya bounded delivery | Canonical write, approval, publish, recall, role/policy ve audit yapamaz | Grants + RLS + API route boundary | Genel table/object write, ID ile ownership değişimi veya stale client role görülürse `DENY`. |
| Browser Internal Operations | Form ve workflow intent gönderir | UI/cache/hidden button authority değildir; her commit'te server reauthorization | Session + server policy + RLS defense | Stale role, expired session, wrong scope, missing independence/version => `DENY`/`HOLD`. |
| Approved server/API | Sensitive read/mutation, idempotency, contextual policy, generation fence | Aday A'nın zorunlu authority boundary'si | Server-side user context + minimum service identity + DB transaction | Boundary yoksa veya bypass edilebiliyorsa `REJECT-IF-UNMITIGATED`. |
| Data API/PostgREST direct | İleride kanıtlanmış low-risk read surface | High-consequence workflow için kullanılmaz | Explicit grants + RLS; dedicated exposed schema | Direct client canonical authority, exposed internal table veya unchecked RPC => `DENY`. |
| `service_role`/secret key | Dar server/worker işlemleri | Ürün approval/competence yerine geçmez; RLS bypass ettiği için yalnız server | Secret manager, scoped task pack, rotation | Browser, Flutter, repository, logs, AI context veya broad worker => `REJECT`. |
| SQL/RPC/`SECURITY DEFINER` | Internal invariant/helper veya server route | Contextual authorization API'den geçmeden çağrılamaz | Dar `EXECUTE`, schema-qualified relations, safe `search_path` | Public callable definer, broad grant, owner/bypass path => `DENY`/`HOLD`. |
| Supabase Storage private bucket | Server-issued scoped download/upload handle | Object transport; review/activation authority değil | Private default + Storage RLS + short TTL handle | Public bucket, unbounded bearer URL, quarantine bypass => `REJECT`. |
| Supabase Storage public bucket | Sadece açıkça released public derivative için ileride | Orijinal/private/evidence için yasak | URL possession effectively read authority | Private/classified/recalled bytes public olursa `REJECT`. |
| Edge Function/worker | Package builder, relay, isolated helper | Rebuildable work; no independent approval/audit | Narrow identity, operation ID, retry/reconcile | Timeout success, no operation ledger, service key leakage => `HOLD`. |
| Realtime/push/cache | Delivery hint/projection | Recall, eligibility, history veya correctness proof değildir | Version/generation checked at API/foreground | Event order or delivery receipt as authority => `REJECT`. |
| Migration/restore path | AI runbook + independent reviewer/validator | Protected floor and release graph recheck | Management/DB role separation | Owner SSH, direct superuser, old snapshot cutover => `HOLD`/`REJECT`. |
| Provider dashboard/Management API | Provider operation, billing, project lifecycle | Product authority veya approval competence değildir | Separate owner/legal action + audit | AI/ordinary operator unrestricted owner token => `REJECT`. |
| Billing/support/break-glass | Explicit human/legal/account owner action | Must not silently mutate product truth | Attributable, scoped, time-bound, audited | Support console is only recovery path => `HOLD`. |
| Quarantine callback/preview renderer | Untrusted bytes/metadata | No ambient production credentials/network | Isolated origin, lineage/digest | Preview or scan outcome becomes approval => `REJECT`. |

Bu matrix doğrudan `NF-01`, `NF-02`, `NF-03`, `NF-07`, `NF-11` ve `DEBATE-007 D7-16` ile izlenebilir. Matrix'in
gerçek allow/deny sonuçları daha sonra controlled evidence pack ile gösterilene kadar **[HELD]**'dir.

---

## 4. Credential classes, owner/legal actions, AI-access rules ve rotation/recovery

### 4.1 Credential sınıfları

| Credential sınıfı | Kim/neyin kullanımı | Scope | AI ve client kuralı | Rotation/recovery notu |
|---|---|---|---|---|
| Public client key (`anon`/publishable) | Flutter/browser initialization | Yalnız exposed, low-risk surface | Public kabul edilse dahi authority değildir; service key ile karıştırılmaz | Key exposure ürün approval veya canonical DB yetkisi doğurmamalı. |
| User session/access token | Authenticated user intent | Current actor/session | Browser/Flutter'da bulunabilir; server commit'te yeniden doğrulanır | Session revocation/freshness policy **[OPEN]**. |
| Server API execution identity | Approved server/API boundary | Route/task-specific read/write | AI'ya yalnız runbook scoped ephemeral access; browser/mobile'a verilmez | Expiry, rotation, impact graph ve audit gerekir. |
| Supabase `service_role`/secret | Server-side privileged data path | En dar gerekli DB/Storage action | Flutter, browser, repository, logs ve AI context'inde kesinlikle yok | Resmi docs'a göre RLS bypass eder; compromise durumunda positive effect hold, rotate, session/op impact audit. |
| DB migration/restore role | Migration/restore task | Schema/data migration, never end-user request | Independent reviewer; no routine AI broad superuser | Restore sonrası current credentials/custom-role passwords yeniden set edilmelidir. |
| Storage quarantine identity | Upload finalization/scanning worker | Opaque prefix/object generation | No global bucket credential; no public original | Handle expiry/revoke, orphan quarantine and object digest binding. |
| Protected audit writer | Audit custody path | Append-only event/checkpoint | Effect actor cannot rewrite custody; AI cannot erase | Failure/gap/fork => high-consequence `HOLD`. Physical custody **[OPEN]**. |
| Emergency negative authority | Recall/suspension only | Narrow scope, generation increment | Separate role/trust root, not normal publish path | Normal positive operation cannot clear newer negative generation. |
| Supabase Management API/PAT | Provider account administration | Project/backup/config operations | Not product operator credential; no owner token in ordinary task | Expiry, scope, human approval and rotation **[OPEN]**. |
| Billing/legal/account owner | Human external authority | Payment, legal residency, contract, account recovery | AI may prepare a plain-language brief, cannot impersonate | User must not debug provider; explicit human action remains required where unavoidable. |

### 4.2 AI-native operating rule

Every AI task pack must name: allowed operation, forbidden operation, credential class, dry-run/read-only phase,
idempotency key, stop condition, evidence artifact, forward recovery and independent reviewer. AI cannot receive a
service/root key, act as billing/legal owner, self-approve publication/recall, or restore a project directly to authority.

### 4.3 Key compromise ve rotation

`KEY_COMPROMISED` flow:

```text
detect → stop affected positive operations → identify scope/generation
      → revoke/rotate credential and affected sessions/handles
      → invalidate or hold pending operations → record protected impact evidence
      → reconcile DB/object/audit/floor → independent review → controlled re-entry
```

Supabase Storage signed URL'leri time-limited bearer access'tir. Resmi docs'a göre Auth JWT signing key rotation,
Storage'ın ayrı signing key'iyle üretilmiş mevcut signed URL'leri expiry zamanına kadar kendiliğinden geçersiz kılmaz.
Bu yüzden object generation/revocation, short TTL ve classification checks zorunludur; “Auth key'i döndürdük, tüm
dosya erişimleri bitti” iddiası kabul edilmez.

---

## 5. Canonical transaction ve cross-plane partial/unknown/reconcile state machine

### 5.1 Aday A'nın izin verdiği transaction sınırı

PostgreSQL transaction'ı aynı canonical data authority içinde current state, domain history/reference, idempotency
ledger ve outbox intent'i bağlayabilir. Bu, Storage byte finalization, bağımsız protected audit custody, notification
delivery, package artifact veya provider control-plane değişimini aynı ACID transaction yaptığı anlamına gelmez.

Her operation şu anlamları taşır: `operation_id`, actor/session, exact scope, intended effect, payload fingerprint,
expected record version, release/suspension generation, policy version ve classification.

### 5.2 Cross-plane documentary state machine

```text
PREPARED
   ├─ validation/auth failed ───────────────► DENIED
   ├─ DB current + history + idempotency commit
   │       ├─ required audit/object/outbox effects complete ─► COMMITTED
   │       ├─ one or more planes pending/failed ────────────► PARTIAL
   │       └─ client response lost/timeout ─────────────────► OUTCOME_UNKNOWN
   └─ stale version / missing independence / outage ────────► HELD

PARTIAL / OUTCOME_UNKNOWN
   └─ lookup same operation_id + reconcile manifests
          ├─ exact committed result ───────────────────────► COMMITTED
          ├─ safe compensating/forward action ─────────────► RECONCILING
          ├─ irreconcilable or evidence gap ───────────────► HELD
          └─ no domain effect and explicit failure ─────────► FAILED
```

- Browser timeout asla “başarısız, tekrar gönder” veya “başarılı” diye tahmin edilmez.
- Aynı `operation_id` ile lookup yapılır; değişmiş payload aynı ID ile yeniden kullanılamaz.
- Protected audit normal/fallback olarak gerekli minimum evidence'ı sağlayamıyorsa high-consequence effect `HELD` kalır.
- Outbox relay success yalnızca delivery state'tir; canonical authority değildir.
- Cross-plane partial state owner'a teknik hata ayıklattırmaz; AI runbook safe reconciliation veya held escalation
  üretir.

### 5.3 Publish versus emergency suspension race

Normal publish yalnızca mevcut protected suspension/revocation generation'ı okuyup commit anında tekrar kontrol ederse
pozitif etki kurabilir. Emergency negative authority ayrı bir guarded operation ile generation'ı artırır. Daha yeni
negative generation, in-flight eski publish'i geçersiz kılar; normal publish eski değeri yazıp suspension'ı silemez.
Race sonucu `CONFLICT`/`HOLD`, doğru cevap değildir diye zorla publish değildir.

Bu yapı Supabase Postgres transaction primitive'inden **[INFERRED]** çıkar; gerçek concurrency/race evidence'ı henüz
yoktur ve F05/F08/F12 ile birlikte sonradan gösterilmelidir.

---

## 6. Authorization ve negative-test planı (privileged bypass dahil)

### 6.1 Authority kuralı

Server/API her sensitive request'te actor, session, action, exact object/scope, workflow state, classification,
consequence, separation-of-duties/independence, expected version ve current release/suspension generation'ı kontrol
eder. UI role, cached claim, object ID, RLS sonucu veya `service_role` varlığı tek başına business authorization
değildir.

Supabase resmi API güvenlik dokümanı grants'in object'e erişimi, RLS'nin row erişimini belirlediğini; ikisinin exposed
object'ler için birlikte ele alınması gerektiğini söyler. Resmi RLS dokümanı exposed schema'daki her table için RLS,
grants'in ayrıca yönetilmesini ve `service_role`'un RLS bypass ettiğini belirtir. Bu nedenle Aday A'da RLS:

- her exposed table/view için defense-in-depth;
- owner/superuser/`bypassrls` negatif yolu için test yüzeyi;
- server/API policy'nin yerine geçmeyen bir ikinci sınır;
- default privilege ve Data API exposure drift'ine karşı release kontrolü

olarak kullanılır.

Postgres 15+ view'larda `security_invoker = true` konusu ayrıca incelenmelidir; RLS olmayan veya yanlış grant edilen
view, tablo policy'sinin güvenli olduğu izlenimini bozabilir. `UPDATE` için gerekli `SELECT` policy'si, `WITH CHECK`,
security-definer `search_path` ve user-editable metadata claim'lerinin authorization'da kullanılmaması da negatif test
alanıdır.

### 6.2 Zorunlu negative-test matrisi

| Test alanı | Denenecek bypass | Beklenen sonuç | Kanıt durumu |
|---|---|---|---|
| Stale browser role | Role revoke sonrası açık tab ile publish/approve | Commit-time `DENY`/`HOLD`; no side effect; reason/audit | `HELD` — F01 drill yok |
| Direct client write | Flutter/browser anon/authenticated ile internal table, RPC, Storage write | No general canonical mutation; `DENY` veya yalnızca açıkça low-risk contract | `HELD` — boundary test yok |
| Service-role leak | Browser bundle/log/AI context'e secret ekleme denemesi | Secret tespit/rotation; affected scope hold; no client authority | `HELD` — secret scan/rotation evidence yok |
| BOLA/IDOR | Başka owner/object ID ile select/update/export | Server scope + RLS layered deny; object enumeration yok | `HELD` |
| Admin/server bypass | Server SDK veya migration role ile separation-of-duties atlama | Product policy gateway olmadan `DENY`/`HOLD`; bypass audited | `HELD` |
| RLS/grant mismatch | RLS policy eklenmiş fakat anon/authenticated grant kalmış | Explicit grant review ve exposed-schema inventory fail-closed | `HELD` |
| Security-definer | Public callable, broad EXECUTE, unsafe search_path | Function unavailable or held until narrowed and reviewed | `HELD` |
| User reassignment | Update ile `user_id`/ownership/scope değiştirme | `USING` + `WITH CHECK` ve server policy deny | `HELD` |
| View bypass | Exposed view underlying RLS'yi bypass ediyor | `security_invoker`/private schema/deny | `HELD` |
| Public Storage | Private/original bucket'ı public veya guessed URL ile okuma | `DENY`; no original exposure | `HELD` |
| Signed handle | Expired/revoked generation veya wrong classification handle | `DENY`/`HOLD`; expired bearer link no reuse | `HELD` |
| Migration/restore | Old snapshot ile newer role revoke/deletion/suspension'ı geri alma | `RESTORE_QUARANTINE`; floor blocks cutover | `HELD` |
| Billing/provider console | Quota/plan değişikliği product approval gibi kullanma | Product effect yok; owner-readable billing state | `HELD` |
| Bulk/export | Collection/object enumeration veya unscoped export | Separate export authorization + disclosure event | `HELD` |

Bu plan gerçek database testleri değildir; no-code evidence pack'in acceptance criteria'sıdır. Her critical item
kapanmadan Aday A `PASS` değildir.

---

## 7. Offline package builder, local operation ve conflict/retry model

### 7.1 Kapalı package sınırı

Package yalnızca seçili motorcycle + applicable task/variant için hazırlanır ve aşağıdakileri machine-verifiable manifest
ile bağlar:

- exact release/client/schema/base generation ve eligibility/freshness context;
- fit/prerequisite/claim/evidence context;
- compact text, steps, warnings ve required checks;
- task-specific safe-stop, mismatch, recovery ve revalidation closure;
- required/optional media ayrımı;
- object identity, digest, version/generation, classification ve lineage;
- package dependencies tamamlanmadıysa atomik rejection;
- anti-rollback ve current suspension/revocation check.

Full guide library, unrelated motorcycle, large media veya cache snapshot'ı varsayılan offline authority değildir.
`DEC-0023`, `DEC-0024` ve common fixture'taki 12 MB compact transfer, 150 MB optional media, 25 MB cellular
confirmation ve 250 MB content cache değerleri karşılaştırma sabitleridir; final product limitleri değildir.

### 7.2 Supabase primitive'inin sınırı

Supabase Flutter/Dart API'si Database/Auth/Storage/Realtime/Functions erişim yüzeyi sağlar; ancak bu projenin closed
package dependency closure'ını, durable operation log'unu, high-consequence conflict policy'sini veya anti-rollback
manifestini kendiliğinden kanıtlamaz. Realtime delivery veya Storage download receipt package correctness değildir.

Bu nedenle package builder server/API boundary altında çalışır; package acceptance local Flutter boundary'de atomic olur;
foreground/reconnect/high-consequence decision boundary'de current authority ile yeniden reconciliation yapılır.

### 7.3 Local user operation

Flutter cihazı local success göstermeden önce durable identified operation kaydeder:

`operation_id + actor + device/install generation + motorcycle/task context + payload fingerprint + expected version + schema/release`

- Retry aynı ID ile idempotent'tir.
- Lost response `OUTCOME_UNKNOWN`; lookup/reconcile gerekir.
- Safety, provenance, ownership, entitlement, official content ve disputed evidence için sessiz last-write-wins yoktur.
- Low-risk alanlar için ileride explicit merge policy tanımlanabilir; bu universal varsayım değildir.
- Device loss/clone/restore local-only evidence'i server completion gibi gösteremez; truthful `LOCAL_LOSS`/`HELD` state'i
  gerekir.
- Pending operation eviction, cache pressure ve attachment dependency state'i ayrıca kanıtlanmalıdır.

### 7.4 Download/handle kuralları

Private Storage signed URL veya authenticated request yalnız scoped transport'tur. URL TTL, object generation,
classification ve recall state birlikte kontrol edilir. Büyük media on-demand ve beklenen boyutu görünür olmalıdır;
cellular üzerinde büyük arka plan indirmesi varsayılan değildir.

Package closure, cache pressure non-eviction ve incomplete/wrong-base delta red testi kapanana kadar bölüm sonucu
`HELD`'dir.

---

## 8. Protected audit ve non-restorable floor: location/failure independence

### 8.1 Protected audit

Supabase ordinary table, project activity feed, provider log, CDC, timestamp veya same-project admin tarafından
değiştirilebilir audit row protected audit olarak kabul edilmez. Gerekli anlam:

- ordered attributable event;
- actor/session/action/scope/policy/version/generation/result/payload digest;
- independent custody veya aynı yetki sahibinin tek başına silemeyeceği append-only/WORM-equivalent yol;
- checkpoint/fork/sequence-gap detection;
- normal custody unavailable olduğunda sınırlı fallback;
- normal ve fallback evidence yoksa high-consequence action `HELD`;
- privacy/retention/export disclosure kuralları.

Fiziksel audit provider, WORM ürünü, retention süresi ve legal hold **[OPEN]**'dir. Bu belirsizlik Supabase'in
ordinary logging özelliğiyle kapatılamaz.

### 8.2 Non-restorable negative/deletion/accepted-operation floor

Ordinary DB restore'dan bağımsız monotonic floor en az şunları taşır:

- release/suspension/revocation generations;
- security epochs ve role/session revocation;
- deletion/withdrawal/retention tombstones;
- already accepted operation IDs/idempotency ledger;
- migration/schema epochs;
- protected audit checkpoint ve object manifest state.

Floor yoksa veya bağımsız kanıtı restore edilemiyorsa restored project `RESTORE_QUARANTINE` kalır. Eski backup recalled
content'i, revoked role'ü, deleted private payload'ı veya daha önce kabul edilmiş operation'ı yeniden authority yapamaz.

### 8.3 Failure-domain sonucu

Floor ve audit aynı Supabase project/account snapshot'ının içindeyse Supabase restore/account compromise bunları birlikte
geriye sarabilir; bu `HF-BAAS-03`, `HF-BAAS-06` ve `HF-BAAS-08` riskidir. Aday A'nın managed olması, audit/floor
bağımsızlığı sağlamaz. Bu control kapanmadan overall disposition `HELD` kalır.

---

## 9. Media quarantine, object finalization, version/digest/access/delete lifecycle

### 9.1 Supabase Storage resmi mekanizması

Kaynak: [Storage Buckets](https://supabase.com/docs/guides/storage/buckets/fundamentals), [Serving assets from Storage](https://supabase.com/docs/guides/storage/serving/downloads).

- Private bucket varsayılandır; download için user JWT/RLS veya sınırlı süreli signed URL gerekir.
- Public bucket read/serve access control'ü effectively bypass eder; URL'yi bilen kişi okuyabilir.
- Signed URL bearer erişimdir; expiry'den önce Auth JWT key rotation ile otomatik olarak geçersizleşmez.
- Bucket upload size/content type restriction bir transport/validation primitive'idir; malware isolation veya technical
  correctness kanıtı değildir.
- Resmi Pricing snapshot'ta Free max upload 50 MB, Pro max upload 500 GB görünür; Kavriva'nın 150 MB optional media
  karşılaştırma değeri Pro kapasitesine sığsa bile automatic download veya unbounded media kabul edilmez.

### 9.2 Quarantine-first lifecycle

```text
RECEIVED → QUARANTINED → isolated scan/render/URL validation
         → REVIEWABLE / HELD / REJECTED
         → reviewed activation → RELEASED derivative
```

Her object identity şu alanlarla birlikte yaşar: opaque key, generation/version, digest, byte size, type claim,
classification, owner/scope, source lineage, retention/deletion state, package/release references ve access-handle state.

- Orijinal upload doğrudan operations veya public origin'e yazılamaz.
- Preview renderer ambient credentials, private network erişimi veya production session taşıyamaz.
- Scan temiz sonucu yalnızca bir validation signal'dir; technical truth, evidence sufficiency, approval veya publication
  authority vermez.
- DB metadata yazımı, audit intent'i veya object finalization başarısızsa object `QUARANTINED`/`ORPHANED` kalır;
  consumer/operator read path'ine düşmez.
- Delete/withdraw/revoke floor'a yazılır; handles expire/revoke edilir; CDN/cache residual copy policy'si **[OPEN]**.
- Classification private/shared/community/official olarak derivative, preview, package, export, backup ve audit
  references'a yayılır.

### 9.3 Backup/exit etkisi

Supabase DB backup'ının Storage object bytes'ını kapsamadığı resmi olarak belirtilmiştir. Dolayısıyla object lifecycle,
manifest/digest ve backup/export ayrı plane olarak yürütülür; project clone veya successful Storage API upload complete
recovery değildir.

---

## 10. Database, object, audit, identity/policy/config/package backup ve restore closure

### 10.1 Supabase database backup ve PITR kanıtı

Kaynak: [Database Backups](https://supabase.com/docs/guides/platform/backups), [Restore to a new project](https://supabase.com/docs/guides/platform/clone-project).

- Pro/Team/Enterprise günlük DB backup sağlar; Pro 7 gün, Team 14 gün, Enterprise up to 30 gün retention.
- Free plan automatic backup/PITR sağlamaz; resmi docs Free kullanıcıya düzenli `supabase db dump` ve off-site backup
  tutmasını önerir.
- DB backup Storage API object'larını içermez; eski backup restore edilince sonradan silinen object'ler geri gelmez.
- Physical backup süreci günceldir; custom role password'ları daily backup dosyalarında tutulmaz, restore sonrası reset
  gerekir.
- PITR paid add-on'dır; en az Small compute ister; 7/14/28 gün için yaklaşık `$100/$200/$400` aylık seviyeler vardır;
  PITR açılınca daily backup alınmaz.
- Restore sırasında project erişilemez; downtime DB boyutuna ve restore sürecine bağlıdır. Numeric RPO/RTO **[OPEN]**.
- Project silinmesi associated data ve backup'ları kalıcı siler; deletion irreversible olarak dokümante edilmiştir.
- Restore to new project database schema/data/roles/auth data gibi parçaları kopyalayabilir; Storage objects/settings,
  Edge Functions, Auth settings/API keys, Realtime settings, extensions ve read replicas manual reconfiguration ister.
- Restore to new project binary restore'da external-operation yapan extension/job'lar restore sonrası çalışabilir; inspect
  edilmeden authority cutover yapılamaz.

### 10.2 Restore quarantine closure

Restore event şu state machine'i izler:

```text
restore source → RESTORE_QUARANTINE
               → DB/schema/version check
               → object/digest/classification manifest check
               → audit checkpoint/floor/security epoch check
               → policy/identity/role/deletion/accepted-op reconciliation
               → release/suspension generation re-check
               → clean-room negative tests
               → reviewed cutover or HELD
```

Backup/restore manifest şunları birlikte bağlamalıdır:

1. DB current/history/provenance ve schema/migration epoch;
2. Storage object IDs, generations, digests, classification, lineage, deletion tombstones;
3. protected audit checkpoint ve floor reference;
4. identity/session/role/policy mappings ve security epoch;
5. operation/idempotency ledger, outbox cursor ve partial/unknown states;
6. release/config/API/package generations ve suspension/revocation state;
7. key references/rotation epochs; raw secrets export edilmez;
8. import validation results ve residual-risk statement.

### 10.3 Restore proof status

2026-09-18 itibarıyla herhangi bir real restore drill yapılmamıştır. F08 old backup resurrection ve F09 DB/object/audit/
config mismatch senaryoları için yalnızca documentary design vardır. Bu iki kanıt kapanmadan Supabase project restore'u
production authority'ye geçirilemez; `HELD`.

---

## 11. Logical export ve clean-room import outside normal account

### 11.1 Resmi export primitives

Supabase'in self-host restore docs'u `supabase db dump` ile roles, schema ve data'nın ayrı SQL dosyaları olarak dışarı
alınabildiğini ve Postgres sürümleri arasında uyumlu SQL ürettiğini belirtir. Aynı docs Storage objects veya Edge Functions
transferini bu database restore adımının parçası saymaz. [Restore a Platform Project to Self-Hosted](https://supabase.com/docs/guides/self-hosting/restore-from-platform)
ve [Migrating to Supabase](https://supabase.com/docs/guides/platform/migrating-to-supabase) bu portability primitive'lerini
gösterir; bunlar tek başına complete exit proof değildir.

`Restore to a new project` resmi docs'u database-only copy olduğunu ve Storage, Edge Functions, Auth settings/API keys,
Realtime settings, extensions ve replicas için manual reconfiguration gerektiğini açıkça söyler. Bu durum lock-in'i
“sıfır” kabul etmeyi engeller.

### 11.2 Aday A exit dossier içeriği

Clean-room import normal Supabase organization/account'ı dışında (başka provider veya owner-controlled clean runtime)
şunları doğrulamalıdır:

- stable domain IDs, versions, generations, operation IDs;
- current state, domain history, provenance, disputes ve protected audit checkpoint;
- roles/policy/authorization mapping; browser/client negative paths;
- object bytes + manifest/digest/generation/classification/lineage + private access semantics;
- release/suspension/revocation generations, deletion tombstones, security epochs ve accepted-operation floor;
- package manifests, dependency closure, optional media boundary ve cache non-eviction metadata;
- outbox/relay partial states, unknown operations ve reconciliation;
- identity migration, session invalidation ve secret re-encryption plan; raw secret export edilmez;
- API contract, configuration, migration/release graph ve compatibility matrix;
- cost/region/backup/support assumptions ve replacement runbook.

Import cutover öncesi negative tests zorunludur: wrong owner, revoked role, recalled content, deleted private data,
expired/superseded object handle, old package generation, duplicate operation, stale browser role ve concurrent negative
authority. Partial export açıkça `PARTIAL` etiketini taşır; “job succeeded” complete exit sayılmaz.

### 11.3 Lock-in değerlendirmesi

| Katman | Documentary lock-in okuması | Belirsizlik/mitigation |
|---|---|---|
| PostgreSQL domain core | `LOW–MEDIUM` **[INFERRED]**; standard SQL/roles/schema/data dump yolu mevcut | Provider extensions, internal schemas, version/permission differences için clean-room import şart. |
| Auth/session | `MEDIUM–HIGH` **[OPEN/INFERRED]**; auth schema/user data taşınabilir primitive'leri olsa da sessions, identity provider, key/claim semantics ve recovery policy provider-specific olabilir | Provider-neutral identity mapping, session revocation ve re-auth rehearsal. |
| Storage/object | `MEDIUM–HIGH` **[CONFIRMED boundary]**; DB backup/clone object bytes/settings'i kapsamaz | Independent object manifest, digest, classification, clean-room object import ve handle reissue. |
| Edge Functions/Realtime/config | `MEDIUM–HIGH` **[CONFIRMED manual reconfiguration]** | API contract ve release graph provider dışında tutulur; replacement'ta rebuild/revalidate. |
| Backup/PITR/logs/observability | `MEDIUM–HIGH` operational lock-in | Cross-plane consistency manifest, off-site logical export, independent audit/floor, dated changelog watch. |
| Self-host fallback | “Free exit” değildir; Supabase resmi docs self-host'ta server maintenance, hardening, Postgres, HA, backup/DR, monitoring ve uptime sorumluluğunu owner'a verir | Aday A'nın exit path'i owner SSH veya tribal knowledge'a dayanamaz; AI-operable automation ve independent review şart. |

Bu tablo “Supabase'i seç” veya “Supabase'ten kaç” sonucu değildir. Lock-in cost ve recovery riskinin ADR öncesi görünür
kalmasıdır.

### 11.4 Clean-room exit status

Export/import rehearsal, negative behavior verification, object/auth/policy mapping ve external floor evidence henüz yoktur.
Sonuç: **[HELD]**. Aday A, exit kanıtı kapanmadan production-ready sayılamaz.

---

## 12. Observability, incident support, Flutter ve bakım / no-owner-debug AI runbook

### 12.1 Managed operation avantajı ve sınırı

Supabase managed, OS patching, database process, disk provisioning gibi işleri doğrudan teknik olmayan sahibin üzerine
yüklememesi bakımından adaydır. Ancak managed olmak şunları otomatik çözmez:

- domain authorization/separation-of-duties;
- protected audit/floor;
- quarantine/SSRF/preview isolation;
- closed offline package and conflict policy;
- cross-plane object/DB/audit consistency;
- anti-resurrection restore;
- cost cap outside Spend Cap;
- provider account/region/billing/key incident;
- clean-room export/exit.

### 12.2 Observability snapshot

Resmi pricing snapshot'ı API/DB log retention'ı Free `1 day`, Pro `7 days`, Team `28 days` olarak gösterir; platform audit
logs ve metrics endpoint Free/Pro seviyelerinde aynı anlamda dahil değildir. Log drain Pro'da ayrı ücret kalemidir.
Provider logs operational signal'dir; protected audit değildir.

2026 changelog'daki `logs.all` endpoint removal (2026-09-23), backup scheduler fix ve changing dashboard locations,
Management API/CLI contract'larının version watch gerektirdiğini gösterir. AI runbook her operation'da exact endpoint,
CLI version, evidence capture ve stop condition taşır; “latest docs'a göre çalıştır” belirsizliği kabul edilmez.

### 12.3 No-owner-debug AI runbook

Her rutin AI task'ı aşağıdaki biçimde sınırlandırılır:

1. minimum context pack ve exact scope;
2. read-only/dry-run first;
3. least-privilege execution identity;
4. idempotency key ve expected version/generation;
5. machine-readable result (`ALLOW`, `DENY`, `HOLD`, `OUTCOME_UNKNOWN`);
6. evidence digest/checkpoint ve reviewer handoff;
7. safe forward recovery; destructive rollback yok;
8. owner'a teknik hata ayıklama değil, plain-language approval/hold explanation.

AI şu işlemlerde sole authority olamaz: billing/plan switch, account/legal ownership, service-role/PAT creation,
irreversible delete, privilege/key change, migration cutover, restore-to-authority, high-consequence publish/recall.

### 12.4 Flutter/SDK fit ve bakım

Resmi [Supabase Dart/Flutter reference](https://supabase.com/docs/reference/dart/introduction) Database, Auth, Edge
Functions, Realtime ve Storage yüzeyleri sunar. Bu, Flutter/browser için resmi SDK yüzeyinin bulunduğunu doğrular; ancak
projenin package closure, local operation log, offline safety/recovery veya server authority'sini çözmez.

Resmi [Flutter supported deployment platforms](https://docs.flutter.dev/reference/supported-platforms) sayfası
2026-09-14 güncellemesinde Flutter `3.47.2` için Android `24–37` ve iOS `15–27` destek aralıklarını gösterir. Bu
aralıklar Kavriva'nın final minimum OS matrix'i değildir; Android-first/iOS-later real-device release matrix'i ileride
ayrıca sabitlenecektir.

Resmi [Flutter package guidance](https://docs.flutter.dev/packages-and-plugins/using-packages) şu bakım gerçeklerini
belirtir:

- plugin paketleri Android Kotlin/Java, iOS Swift/Objective-C ve diğer platform kodlarını içerebilir;
- native plugin değişiklikleri hot reload/hot restart ile kapanmayabilir ve full restart/build gerektirebilir;
- package resolution, Gradle/CocoaPods veya diğer platform dependency conflict'leri ortaya çıkabilir;
- `pubspec.lock` aynı dependency sürümünü yeniden üretmeye yardım eder.

Bu nedenle Flutter + Supabase için AI-native bakım yüzeyi: Dart client sürümü, native plugin/generated registrant,
Android Gradle/Runner, iOS Runner/Xcode/SwiftPM/CocoaPods, auth/session semantics, Data API grants/RLS, Storage signed
handle ve Supabase changelog birlikte izlenir. Paket sürümleri pinlenmeden ve lockfile/evidence olmadan “kolay bakım”
iddiası yapılmaz.

### 12.5 Bakım riskleri

| Risk | Aday A etkisi | Planlanan tutum |
|---|---|---|
| Supabase API/default drift | Data API exposure, OpenAPI anon access, extension/default, logs endpoint değişebilir | Dated changelog watch; compatibility hold; silent upgrade yok. |
| Flutter plugin/native drift | Android/iOS generated state veya platform build kırılabilir | AI implementer + independent reviewer + real-device validator; owner repair yok. |
| RLS/grant drift | New table/view/function yanlış expose olabilir | Exposed schema inventory, RLS/grant negative tests, release gate. |
| Storage handle drift | Signed URL expiry/cache/revoke semantics yanlış yorumlanabilir | Short TTL, generation check, CDN/cache residual-risk test. |
| Backup drift | Scheduler/retention/PITR behavior değişebilir | Backup evidence, manifest, restore drill; dashboard success yeterli değil. |
| Support/incident drift | Free community, Pro email, Team support differences | Owner-readable escalation matrix; support SLA satın alma varsayılmıyor. |

Overall maintenance fit: **[INFERRED] managed infrastructure burden'ı azaltabilir; application/data safety and AI runbook
burden'ı ortadan kaldırmaz.** Evidence yokken `PASS` değil `HELD`.

---

## 13. P0–P3 staged cost, cap/overage behavior ve safe budget-hold mode

Bu bölüm common fixture'taki P0–P3 horizons için documentary cost envelope'tir. Hiçbir satır satın alma emri değildir.
Mağaza ücretleri, ödeme işlemcisi, domain, email/SMS, cihaz, human operations ve ilerideki AI provider maliyetleri dahil
değildir.

| Horizon | Aynı fixture anlamı | Supabase resmi cost signal | Zorunlu ek iş / hold |
|---|---|---|---|
| P0 | 0 active users; planning/documentary only | `$0` ve provider hesabı olmadan ilerleme | Kod/hesap/abonelik yok. Evidence, contracts ve runbook hazırlanır. |
| P1 | 100 private/internal/closed-test users | Free `$0` keşif yolu; fakat no automatic backup/PITR, pause after inactivity, 1 GB file, 50 MB upload, 1-day logs; Pro `$25` + compute credit/backup path | Safety/recovery/evidence free planla kapanmıyorsa capability `HELD`; “free = production” denmez. |
| P2 | 10.000 active users; first meaningful production checkpoint | Pro starting `$25/month`; `$10` compute credit; 100K MAU included; 250 GB egress, 100 GB file included; PITR optional `$100+`/retention | Actual egress/media/backup/audit/quarantine/API costs measured; cap dışı compute/PITR için stop policy gerekir. |
| P3 | 50.000 active users; growth stress checkpoint | MAU Pro included sınırına yakın ama egress/storage/compute/Realtime/Functions/transform kullanımına bağlı; Team `$599` only if later assurance requires | No forecast as fact. Scale-triggered costs, incident month, export/restore drill and support choice re-approved. |
| Restore drill | One controlled restore | Daily backup/PITR add-on, restore downtime, extra new-project mirrored cost possible | Cross-plane manifest, external floor, audit/object reconciliation; restore-to-authority `HELD` until proof. |
| Exit drill | One clean-room export/import | SQL dump path itself may be low direct cost; object/audit/clean environment, egress, re-encryption and validation are separate | Partial export or failed negative test is `HELD`; no raw secrets export. |
| Incident month | Elevated logs, retries, exports, object operations | Log drain/custom domain/egress/compute/PITR/extra project are separately metered or cap-excluded | Safe budget-hold, no surprise overage, positive high-consequence work held if required plane unavailable. |

### 13.1 Cost classification

- **Mandatory safety work:** server/API policy boundary; RLS/grants negative coverage; protected audit/floor; quarantine;
  backup/export manifest; restore/exit evidence; cost monitoring/stop runbook; region/data map.
- **Deferrable:** longer PITR retention, extra region/read replica, advanced log drain, managed support, broad preview
  fleet, high-resolution transform.
- **Optional:** convenience Realtime, noncritical analytics, dashboard cosmetics, premium AI add-ons.
- **Scale-triggered:** paid compute, MAU, DB disk, egress, Storage size, transforms, Edge invocations, Realtime,
  extra projects, retention, incident support.
- **Separate store cost:** Android/iOS developer accounts and store publication costs remain under `DEC-0030`/`DEC-0032`.

### 13.2 Safe budget-hold mode

Budget/cap/overage or provider-account state uncertainty is not resolved by disabling safety:

1. stop new positive high-consequence mutations, publication and nonessential uploads;
2. mark `BILLING_HELD`/`ACCOUNT_HELD`/`SERVICE_UNAVAILABLE` visibly;
3. preserve already accepted operation IDs, protected audit intent and local pending work;
4. keep only policy-approved safe-stop, teaching, history and recovery closure;
5. use independently evidenced export/negative authority path where available;
6. reconcile after billing/provider state is confirmed; never blind retry or silently spend.

If a candidate plan cannot enforce this state without owner dashboard/SSH repair or unbounded overage, affected capability
is `HELD`. Alert email or budget graph alone is not a hard cap.

---

## 14. Provider replacement ve architecture exit dossier

### 14.1 Provider-neutral invariants to preserve

Supabase-specific convenience cannot leak into canonical product meaning. Replacement dossier must preserve:

- stable IDs, versions, generations and operation identities;
- server/API product contracts independent of Data API/SDK;
- current/history/provenance/protected-audit separation;
- private/shared/community/official classification and derivative propagation;
- object digest/generation/lineage and scoped access semantics;
- selected-motorcycle/task package closure and optional media boundary;
- release/suspension/security/deletion/accepted-operation/migration floor;
- role/policy/identity mapping and session/key rotation epochs;
- outbox/partial/unknown/reconciliation state;
- cost/region/provider failure states and owner-readable runbooks.

### 14.2 Controlled replacement sequence

```text
freeze positive mutations
  → establish coordinated consistency point + manifest
  → export DB current/history/roles/policy
  → export object bytes/metadata/digests/classification
  → export protected audit checkpoint + negative/deletion/accepted-op floor
  → export package/release/config/outbox/operation state
  → import into clean environment with new secrets/handles
  → run negative authorization/deletion/classification/suspension tests
  → reconcile pending/unknown operations
  → independent review and cutover fence
  → re-open only after current negative generation is confirmed
```

### 14.3 Exit proof and residual lock-in

`supabase db dump`/Postgres logical compatibility is a useful portability primitive. It does not prove that Auth,
Storage bytes/settings, Edge Functions, Realtime, keys, logs, protected audit, floor, policy and package behavior moved
correctly. `Restore to a new project` is explicitly database-only with manual reconfiguration. Self-hosting is documented
as an owner responsibility for server provisioning, hardening, updates, Postgres maintenance, HA/scalability, backup/DR,
monitoring and uptime; it is not a no-cost owner-independent recovery shortcut.

Therefore Aday A exit posture is:

- **Relational core:** potentially portable, subject to extension/version/role tests.
- **Integrated operational features:** meaningful operational lock-in unless external contracts/manifests are maintained.
- **Protected audit/floor:** must be independent before production, otherwise restore/exit is not trustworthy.
- **Overall:** `HELD` until clean-room import and negative behavior evidence exists.

No provider replacement or self-host deployment is chosen here.

---

## 15. Result: F01–F16 per-scenario disposition ve overall documentary status

### 15.1 Result rule

`PASS` yalnızca current official evidence ve candidate-specific closure ile documentary olarak verilebilir; gerçek build/
restore/release sonucu değildir. `HELD`, mechanism veya evidence route tanımlı olsa bile critical proof eksikliğini ifade
eder. `REJECT` ise Aday A'nın **unpartitioned/direct-client** kullanımının veya aşağıdaki hard-fail'in telafi edilmeden
önerilmesi halinde geçerlidir. Bu dosyanın current overall result'ı `HELD`'dir.

### 15.2 F01–F16 ortak fixture coverage

| ID | Failure scenario | Aday A'da beklenen invariant | Candidate-specific control | Mevcut sonuç |
|---|---|---|---|---|
| **F01** | Browser role revoked while stale tab remains open | Commit-time reauthorization `DENY`/`HOLD`; cached UI authority değil | Server/API actor/session/action/scope/state/independence/version check; RLS defense; stale-tab audit | **HELD** — documentary boundary var, live negative evidence yok |
| **F02** | Privileged server/admin key leaks | Rotate/revoke, affected sessions/operations/handles invalidate/hold, impact audit; client exposure yok | `service_role` server-only; secret inventory; key-compromise runbook; signed URL TTL/generation | **HELD** — rotation and residual-handle drill yok |
| **F03** | DB commit succeeds, response lost | Same operation ID lookup original result; duplicate effect yok | Postgres current/history/idempotency/outbox intent transaction; `OUTCOME_UNKNOWN` reconciliation | **HELD** — no controlled timeout/retry evidence |
| **F04** | Object upload succeeds, metadata/audit fails | Object remains quarantine/orphan; official availability yok | Private quarantine, digest/generation manifest, cross-plane partial state, orphan reconcile | **HELD** — no object/audit drill |
| **F05** | Publish races emergency suspension | Newer negative generation wins; positive in-flight cannot clear it | Separate negative authority, commit-time generation fence, protected floor, independence check | **HELD** — concurrency race proof yok |
| **F06** | Offline package delta incomplete/wrong base | Atomic reject; complete last-safe package/recovery closure; mixed use yok | Package dependency manifest, digest/anti-rollback, selected task only, fallback complete package | **HELD** — machine-verifiable closure not evidenced |
| **F07** | Offline user op conflicts with newer ownership/provenance | Both evidence preserved; high-consequence conflict reviewed/held | Durable local operation ID, expected version, payload fingerprint, no silent LWW, reconciliation UI/state | **HELD** — device/conflict drill yok |
| **F08** | Old backup after recall/revoke/delete/accepted op | `RESTORE_QUARANTINE`; external floor prevents resurrection/replay | Non-restorable negative/deletion/accepted-op/security/migration floor outside ordinary DB snapshot | **HELD** — no restore drill or independent floor evidence |
| **F09** | DB restore succeeds but objects/audit/config differ | Manifest mismatch; no authority cutover | DB + object + audit + identity/policy/config/package cross-plane manifest; clean-room checks | **HELD** — Supabase DB backup excludes Storage; closure untested |
| **F10** | Provider account/billing/quota suspended | Positive work held, owner-readable state, export/recovery path; surprise overage yok | `BILLING_HELD`, Spend Cap where covered, independent stop for excluded items, no owner repair | **HELD** — full safe-hold path and cap test yok |
| **F11** | Primary provider/region unavailable | Bounded safe/recovery behavior; false availability veya owner repair yok | Local complete safe-stop package, provider state machine, independent negative authority | **HELD** — region failover and external negative path open |
| **F12** | Clean-room exit outside normal account | Stable IDs/policy/objects/audit/floor/negative tests survive before cutover | SQL logical export + object/audit/floor manifest + clean import and deny tests | **HELD** — import rehearsal yok |
| **F13** | AI receives one ordinary task | Minimum context/least privilege; broad secret/owner/whole-project dependence yok | Narrow task pack, read-only/dry-run, operation ID, evidence and reviewer | **HELD** — runbook evidence not executed |
| **F14** | AI operation fails halfway | Machine-readable state, stop/forward recovery, independent review; owner debugging yok | `PARTIAL`/`OUTCOME_UNKNOWN`/`RECONCILING` state, idempotency and evidence capture | **HELD** — failure rehearsal yok |
| **F15** | P2/P3 or incident month exceeds planned quota | Actual cap/overage and safe degraded/held mode; unlimited charge assumption yok | Official USD snapshot, cap inclusion/exclusion map, `BILLING_HELD`, scale cost sheet | **HELD** — workload/incident measurement and excluded-item stop proof yok |
| **F16** | Provider changes API/default/security behavior | Dated changelog impact, compatibility hold, migration/revalidation; silent drift yok | Changelog watch, pinned dependencies, exposed-schema inventory, API contract/release graph | **HELD** — watch/compatibility gate not yet operationalized |

### 15.3 Aday A hard-fail register

The following cues are adapted to Supabase-managed composition from the architecture-fit research. Any unresolved cue
remains `HELD`; the underlying Supabase product is not thereby declared universally unusable.

- **HF-BAAS-01:** General client or AI context contains secret/service role/DB credential/unrestricted Storage capability,
  or RLS is presented as sole contextual authorization.
- **HF-BAAS-02:** Publish/recall share one mutable transition without independent negative authority and monotonic fence.
- **HF-BAAS-03:** Same-project table/log/activity is the only protected audit custody and same admin can rewrite effect and
  evidence.
- **HF-BAAS-04:** One BaaS transaction is claimed to cover Postgres, Storage bytes, independent audit and relay, or
  success returns before operation/audit relation is durable.
- **HF-BAAS-05:** Offline correctness relies on full-library sync, Realtime/push, or mixed/partial Storage package.
- **HF-BAAS-06:** DB backup/project clone is accepted without cross-plane manifest, non-restorable floor and clean-room
  import.
- **HF-BAAS-07:** Storage acceptance, clean scan or public URL is treated as quarantine/technical approval.
- **HF-BAAS-08:** Project restore/clone goes live without object, audit, deletion and authority-floor reconciliation.
- **HF-BAAS-09:** Account/billing/quota failure has no safe hold, enforceable controls for covered usage and owner-independent
  recovery for excluded usage.
- **HF-BAAS-10:** DB dump/project clone is the only export and no clean-room negative behavior import exists.
- **HF-BAAS-11:** AI or owner requires Dashboard owner, unrestricted SQL/service key, SSH or interactive incident repair.
- **HF-BAAS-12:** Schema/function/config/package generation can change meaning or clear suspension outside the release graph.

### 15.4 Overall documentary disposition

**Aday A — `HELD / conditionally eligible component composition; not production-ready; no winner`.**

Documentary strengths:

- PostgreSQL transaction/constraint/role/RLS primitives fit many canonical relational invariants.
- Official Dart/Flutter and JavaScript surfaces reduce ordinary client integration friction.
- Managed platform can reduce routine OS/database-process maintenance relative to raw self-hosting.
- Private Storage, signed handles, daily backups/PITR and SQL dump provide useful primitives.
- Supabase changelog/docs/CLI surface can be watched by bounded AI runbooks.

Unclosed critical controls:

- independent server/API policy boundary and all privileged-path negative evidence;
- RLS/grant/view/function/service-role bypass tests;
- protected audit and non-restorable floor outside ordinary project restore;
- Storage–DB–audit cross-plane consistency and quarantine;
- closed offline package, local operation/reconciliation and cache-pressure proof;
- old-backup restore quarantine and recall/deletion/accepted-operation anti-resurrection drill;
- clean-room export/import outside the normal account/provider;
- region/outage/billing/cap-excluded spend and owner-independent recovery;
- Flutter/native/plugin/dependency and Supabase changelog maintenance evidence;
- current P0–P3 and incident-month cost measurement in USD plus Turkey tax/FX uncertainty.

Bu dosya Aday A'yı teknik olmayan sahibin seçmesi gereken bir satın alma kararı olarak sunmaz. Bir sonraki kontrollü
adım, aynı fixture ile bağımsız review'dan geçmiş no-code ADR evidence pack'tir. O evidence pack tamamlanmadan provider,
plan, region, API runtime, backup product, object store, identity service, subscription, code veya Gate 4 → 5 geçişi
onaylanmış değildir.

---

## Official / primary source ledger (2026-09-18 snapshot)

Supabase kaynakları:

- [Supabase Pricing](https://supabase.com/pricing) — plan, quota, compute, Storage, Realtime, Functions, logs ve add-on fiyatları.
- [Billing FAQ](https://supabase.com/docs/guides/platform/billing-faq) — organization/project billing, quota restriction, USD invoice ve support.
- [Control your costs / Spend Cap](https://supabase.com/docs/guides/platform/cost-control) — covered vs excluded usage ve cap davranışı.
- [Database Backups](https://supabase.com/docs/guides/platform/backups) — daily backup, retention, Storage exclusion, PITR, restore downtime ve pricing.
- [Restore to a new project](https://supabase.com/docs/guides/platform/clone-project) — database-only clone ve manual reconfiguration sınırı.
- [Available regions](https://supabase.com/docs/guides/platform/regions) — primary region, specific/general region ve residency uyarısı.
- [Securing your API](https://supabase.com/docs/guides/api/securing-your-api) — grants, RLS, dedicated schema, pre-request checks ve Data API exposure.
- [Row Level Security](https://supabase.com/docs/guides/database/postgres/row-level-security) — exposed table RLS, grants, service-role bypass ve view guidance.
- [Storage Buckets](https://supabase.com/docs/guides/storage/buckets/fundamentals) — private/public access model ve bucket restrictions.
- [Serving assets from Storage](https://supabase.com/docs/guides/storage/serving/downloads) — private access, signed URL ve key-rotation residual behavior.
- [Supabase Dart/Flutter reference](https://supabase.com/docs/reference/dart/introduction) — official Flutter/Dart API surface.
- [Restore a Platform Project to Self-Hosted](https://supabase.com/docs/guides/self-hosting/restore-from-platform) — roles/schema/data dump ve Storage/Functions scope.
- [Self-Hosting](https://supabase.com/docs/guides/self-hosting) — managed/self-host feature and owner-maintenance differences.
- [Migrating to Supabase](https://supabase.com/docs/guides/platform/migrating-to-supabase) — migration surface inventory.
- [Supabase Changelog](https://supabase.com/changelog) — 2026 Data API exposure, OpenAPI key, backup, logs, extension and platform drift watch.

Flutter sources:

- [Supported deployment platforms](https://docs.flutter.dev/reference/supported-platforms) — Flutter 3.47.2 / 2026-09-14 Android-iOS support snapshot.
- [Using packages](https://docs.flutter.dev/packages-and-plugins/using-packages) — plugin native-code effects, dependency conflicts and lockfile guidance.
- [Flutter release notes](https://docs.flutter.dev/release/release-notes) — stable channel and breaking-change watch.

Repository evidence:

- [[00_CONTROL/DECISION_LOG#DEC-0034 — Data Backbone and Logical Service-Boundary Direction]]
- [[DEBATE-007__DATA_BACKBONE_AND_LOGICAL_BOUNDARIES]]
- [[DEBATE-007__JUDGE_SYNTHESIS]]
- [[DEBATE-008__STACK_CANDIDATES_COST_PRIMARY_RESEARCH]]
- [[DEBATE-008__STACK_ARCHITECTURE_FIT_RESEARCH]]
- [[DEBATE-008__FINALIST_COMMON_FIXTURE]]
- [[DEBATE-007__EXTERNAL_RESEARCH_INTAKE_REVIEW]]
