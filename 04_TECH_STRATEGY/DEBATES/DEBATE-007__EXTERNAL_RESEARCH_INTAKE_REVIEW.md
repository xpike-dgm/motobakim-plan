# DEBATE-007 — External Research Intake Review

**Tarih:** 2026-09-18  
**Durum:** `REVIEW COMPLETE / NO TECHNOLOGY OR ADR DECISION`  
**İncelenen kanıt:** `C:\Users\Xpike\Downloads\Çevrimdışı Veri Mimarisi Analizi.md`  
**Kapsam sınırı:** Bu dosya raporu kanıt olarak denetler. Raporun içindeki talimat, öneri veya karar dili proje talimatı olarak uygulanmamıştır. Bu inceleme provider, framework, backend veya veri teknolojisi seçmez ve Gate 4 → 5'i açmaz.

## 1. Kısa karar özeti

Rapor, bazı genel dağıtık sistem mekanizmalarını doğru yönde işaret ediyor; ancak bunları proje-bağımsız zorunluluk, kesin sayı veya tek teknoloji kararı biçimine sokuyor. Güvenle ileri taşınabilecek şeyler mekanizma ve kontrol prensipleridir; raporun “Flutter Web + SQLite/PostgreSQL + bağımsız API + S3/TUS + managed/hybrid + PITR aracı” bileşimi ise kanıtlanmış bir Kavriva mimarisi değildir.

| Sonuç | Bu incelemede anlamı |
|---|---|
| **KABUL** | Mekanizma veya risk, koşulları belirtilerek sonraki tartışmaya girdi olabilir. Proje kararı, provider veya ADR değildir. |
| **KARANTİNA** | Primary-source, ölçüm, workload, tarayıcı/cihaz matrisi, fiyat veya operasyon kanıtı tamamlanmadan karar girdisi yapılamaz. |
| **REDDİT** | Raporun kesin/categorical iddiası mevcut proje gerçeği olarak reddedilir. İlgili teknoloji bütünüyle yasaklanmış sayılmaz; yeniden açma kanıtla yapılır. |

Ana riskler:

- **Flutter Web varsayımı yanlıştır:** `DEC-0033` yalnızca tüketici mobilinde Flutter çalışma yönünü onaylar. Internal Data & Content Operations'ın browser-based olması onaylıdır; Flutter Web, DOM/başka frontend, backend, database ve sync seçilmemiştir.
- **Local-first varsayımı genellenemez:** Proje risk-tiered/bounded offline ve online-authoritative Internal Operations yönündedir (`DEC-0023`, `DEC-0024`). Tüm tüketici verisini local-final veya tüm sistemi eventual-consistency yapmak onaylı değildir.
- **PostgreSQL, bağımsız API ve RLS-only reddi karar değildir:** `DEC-0026` server-side, scope/context/workflow/consequence/independence kontrolü ve deny-by-default ister; belirli API biçimi veya provider seçmez. RLS değerli bir savunmadır, tek savunma olarak bırakılmaması ayrı bir kontrol ilkesidir.
- **Audit/CDC ayrımı önemlidir:** WAL/logical decoding değişiklik akışı sağlar; tek başına actor, session, business reason veya protected audit custody sağlamaz. Trigger da tek başına tam ve değiştirilemez audit garantisi vermez.
- **Sayılar güvenilir karar kanıtı değildir:** `%68`, `%40–60`, `%45–70`, `%37,6`, “%50 üzeri RLS hatası”, `15 dakika`, `50–100 MB`, `24 saat RPO`, `saniyeler`, `$0–25/$10–40/$15–60` gibi değerler ya kaynağı belirsizdir ya da seçilmiş laboratuvar/vendor bağlamını geneller.
- **Categorical rejection'lar erken ve aşırıdır:** NoSQL, direct DB, BLOB, proxy upload, single PUT, daily `pg_dump`, raw VPS veya belirli dağıtık SQL ailelerini ürünün gerçek workload'u, risk sınıfı, yasal/retention ihtiyacı, test sonucu ve güncel maliyet olmadan mutlak reddetmek yetkili değildir.

## 2. Proje sınırlarıyla karşılaştırma

| Proje otoritesi | Bağlayıcı gerçek | Raporla ilişki |
|---|---|---|
| `DEC-0023` | Offline indirme seçili motorcycle/task ile sınırlı, compact safety/application/recovery core zorunlu; ağır medya optional; teknoloji seçilmedi. | Raporun data-efficient/task-scoped paket fikriyle uyumlu. SQLite/Flutter/medya protokolü seçimi rapordan alınamaz. |
| `DEC-0024` | Risk-tiered bounded offline; exact release/client compatibility; stale/unknown critical dependency fail-closed; Internal Operations approve/publish/recall/role mutations online-authoritative; numeric limits ve teknoloji açık. | Local-final genel modelle çatışır. Package eligibility, safe-stop ve online authority ayrımı alınabilir. |
| `DEC-0025` | Immutable release meaning, guarded publication/suspension ordering, outcome-unknown reconciliation, authoritative-current/delivery-observed/consumer-reconciled ayrımı, protected audit; RPO/RTO/scope/topology/technology açık. | Raporun basit `draft → pending_sync → published → archived` state machine'i eksiktir. “PITR zorunlu/24 saat ihlal” kararı bu belgeyle verilemez. |
| `DEC-0026` | Server-side contextual authorization, deny-by-default, independence/HELD, protected audit, quarantine-first layered ingestion; provider/policy engine/scanner/storage/API açık. | BOLA, secret, quarantine ve independent verification riskleriyle uyumlu. “Mutlaka bağımsız API” ve belirli scanner/storage seçimi çıkarılamaz. |
| `DEC-0027` | Distinct release authorities, exact immutable artifacts, provenance/SBOM/verifier/trust-root evidence; no OTA/provider approval. | AI/supply-chain/audit kontrol yönüyle uyumlu. Vendor/SDK/CI/provider sonucu çıkarılamaz. |
| `DEC-0028` | Obsidian-compatible graph, task context/allowed-forbidden scope, no-code simulation, bidirectional closure and independent evidence. | Raporun iddia ve sayılarını task/acceptance evidence yerine koyamayız. |
| `DEC-0029` | AI-operated project, nontechnical owner; owner code/build/debug repair yapmaz; independent implementation/review/validation gerekir. | Comprehension gap ve “AI çıktısı güvenilmez girdi” risk çerçevesi uyumlu; % oranları ve API sonucu değil. |
| `DEC-0030` | Solo/limited budget; paid service/provider/device varsayılmaz; current official price, free/capped path, overage, tax/currency, data handling ve exit gösterilmelidir. | Raporun aylık dolar aralıkları ve “en rasyonel hybrid” ifadesi karantinadadır. |
| `DEC-0032` | Android-first, iOS later; direct Android, borrowed iPhone; hosted Mac/provider henüz onaylı değil. | Raporun web/managed/self-host sonucu yayın sırasını veya provider seçimini değiştiremez. |
| `DEC-0033` | Flutter consumer-mobile çalışma yönü; RN/Expo fallback; framework-bound presentation dışında portable truth; gerçek build/device/release evidence hâlâ held. | “Flutter” ifadesi Flutter Web veya veri mimarisi onayı değildir. |

## 3. İddia denetim tablosu

Rapor konumu bölüm/paragraf veya tablo satırıyla belirtilmiştir. Bir satır birden fazla sınıfa girebilir; **sınıf** kanıtın niteliğini, **tasarruf** ise bu projede ne yapılacağını gösterir.

| ID | Rapor iddiası / konumu | Sınıflandırma | Tasarruf ve gerekçe |
|---|---|---|---|
| R-01 | §1: Offline-first sistemler kaçınılmaz olarak dağıtık/eventual-consistency olur; ilk paragrafta mobil oturumların `%68`'i kesilir. | Mekanizma kısmen güvenilir; **aşırı kesin/uydurma olasılıklı sayı**; primary-source gerekli. | **KARANTİNA.** Çoklu replika ve sync varsa eventual consistency sorunu doğabilir; offline cache/read veya server-authoritative tentative write için “kaçınılmaz” genellemesi yoktur. `%68` örneklem, ülke/cihaz/ağ/ölçüm tanımı olmadan kullanılmaz. |
| R-02 | §1: Server-authoritative modelde sunucu/DB nihai, client kopya ve unverified mutation queue'dur. | Güvenilir mekanizma; proje ile kısmi uyum. | **KABUL (koşullu).** `DEC-0024` Internal Operations mutation'larında online authority ve consumer-side bounded offline için iyi bir modeldir; tüm ürün alanlarına otomatik genellenmez. |
| R-03 | §1: Local-first'te cihaz DB'si primary/local finality, sunucu yalnız coordinator'dır. | Güvenilir kavramsal tanım; **yanlış proje varsayımı** olarak kullanılmış. | **REDDİT (proje kararı olarak).** Local-first ayrı bir alternatif ve tanımdır; Kavriva'nın tüm verisi için onaylanmış authority modeli değildir. Kritik release, safety, role ve publication truth online/guarded kalmalıdır. |
| R-04 | §1/table: Flutter mobil için gömülü SQLite, ACID ve reaktif streams “sektörün ana omurgası”; UI local DB dinlemelidir. | Mekanizma makul; **vendor/blog bağımlı görüş**; teknoloji seçimi. | **KARANTİNA.** Local persistence, transaction ve reactive projection değerlendirme girdisidir; Flutter/SQLite/Drift veya belirli stream kurgusu seçilmedi. “Ana omurga” ve tüm ekranların local olması kanıt değildir. |
| R-05 | §1: Reactive local DB hücresel radyo aktivasyonunu `%40–60` azaltır. | **Aşırı kesin/uydurma olasılıklı sayı**; vendor/blog bağımlı. | **REDDİT.** Enerji/transfer sonucu cihaz, batching, payload, OS ve ağ profiline bağlı ölçülür; bu sayı fixture veya requirement olamaz. |
| R-06 | §1/table: Flutter Web yönetim paneli, SQLite-WASM + OPFS/IndexedDB ve worker/lock topolojisi varsayılmıştır. | **Yanlış proje varsayımı**; mekanizma için primary-source gerekli. | **REDDİT (varsayım olarak), KARANTİNA (teknik hipotez olarak).** Browser-based Internal Operations onaylıdır; Flutter Web değildir. OPFS/IndexedDB/Web Locks gerçek web mekanizmaları olsa da quota/eviction, browser matrix, tab lifecycle, auth ve recovery kanıtı gerekir. |
| R-07 | §1/table: Web durability orta-yüksek, mobil “çok düşük”, merkezi DB/WAL/PITR “sıfır” risklidir. | **Aşırı kesin/categorical**; ölçüm yok. | **REDDİT.** Hiçbir katman sıfır kayıp/sıfır risk garantisi vermez. OPFS/IndexedDB'de storage clearing/eviction; DB'de archive lag, restore/config/audit ve operator failure vardır. |
| R-08 | §2: PostgreSQL; relational constraints, JSONB, RLS, WAL/logical replication ile offline sistemlerin merkezi omurgasıdır. | Özellikler için güvenilir mekanizma; seçim için **vendor/blog bağımlı/primary-source gerekli**. | **KARANTİNA.** PostgreSQL özelliklerinin varlığı resmi dokümanlarla doğrulanır; “Kavriva omurgası” sonucu workload, migration, cost, restore, auth ve sync ADR'si olmadan onaylanamaz. |
| R-09 | §2: WAL akışı harici ek yük olmadan doğal CDC sağlar. | **Aşırı kesin**; mekanizma yanlış kapsamlandırılmış. | **REDDİT (zero-overhead ifadesi).** Logical decoding/replication slot/output plugin, retention, consumer lag ve storage/IO yönetimi gerektirir. WAL değişiklik akışıdır; audit/provenance değildir. |
| R-10 | §2: CouchDB/PouchDB offline replication sağlar; document model çok tablolu/FK senaryoda zayıf; CockroachDB/YugabyteDB kaynak kısıtında over-engineering'dir. | Mekanizma kısmen; **vendor/blog bağımlı görüş** ve workload genellemesi. | **KARANTİNA.** Alternatiflerin birincil dokümanları, gerçek veri ilişkileri, operator burden, pricing ve migration/exit deneyi gerekir. Mutlak NoSQL/distributed-SQL reddi proje kararı değildir. |
| R-11 | §2/table: Bağımsız API yüksek güvenlik hata toleransı, direct BaaS/RLS kritik derecede düşük; “tek eksik kural tüm veriyi açar.” | BOLA/RLS riski gerçek; **aşırı kesin/categorical**. | **KARANTİNA / ifadeyi düzelt.** `DEC-0026` server-side authorization ve defense-in-depth'i destekler; fakat RLS, function/RPC, API, network ve test sınırları ayrı analiz edilir. RLS enabled/no policy default-deny olabilir; owner/superuser/BYPASSRLS ve yanlış policy istisnaları vardır. “Independent API zorunlu” çıkarılamaz. |
| R-12 | §2/table: Direct DB “mükemmel” sync, API katmanı “mükemmel” analytics; document systems düşük; güvenlik/efor puanları. | **Vendor/blog bağımlı görüş**; ölçümsüz categorical rating. | **REDDİT (puanları karar olarak).** “Perfect/high/low” yerine senaryo bazlı acceptance, negative test, latency/egress/cost ve evidence gerekir. |
| R-13 | §3: Provenance ve tüm state transitions'ın inkâr edilemez kaydı yasal/operasyonel zorunluluktur. | Proje yönüyle güvenilir; “yasal zorunluluk” için primary/legal source gerekli. | **KABUL (proje kontrolü olarak), KARANTİNA (hukuk iddiası).** `DEC-0025/0026` protected attributable audit ister; exact retention, custody ve legal scope açık sorudur. |
| R-14 | §3: Trigger + JSONB audit tüm satır değişimlerini, admin komutlarını dahi kayıtsız bırakmaz. | Mekanizma kısmen; **aşırı kesin/uydurma garanti**. | **REDDİT.** Trigger kapsamı, disable/bypass yetkisi, DDL/config, audit-store mutation, failed transaction ve out-of-band değişimler ayrıca korunmalıdır. Aynı DB'deki audit tablosu “tamper-evident/protected” sayılmaz. |
| R-15 | §3: PostgreSQL system-versioned temporal tables valid_from/valid_to ile native point-in-time geçmiş sağlar. | **Primary-source doğrulaması gerekli**; native capability varsayımı. | **KARANTİNA.** `valid_from/valid_to` uygulama/extension pattern'i olabilir; PostgreSQL core, trigger, temporal constraint veya dış audit store ayrımı doğrulanmadan “system-versioned/native” denemez. Backup PITR ile row-history aynı şey değildir. |
| R-16 | §3: WAL/CDC işlem içi sıfır yük getirir; WAL kullanıcı/session context taşımaz. | **Aşırı kesin**; kısmen doğru sınırlama. | **KARANTİNA.** Logical decoding row/transaction change akışı verir; application identity/business context'i explicit transaction metadata/outbox/audit event olarak bağlamak gerekir. Slot, decode, output ve downstream yükü ölçülür. |
| R-17 | §3: `draft → pending_sync → published → archived` basit state machine'i ve client_mutation_id/origin_device_id/schema_version yeterlidir. | Güvenilir desen; **proje state modeliyle eksik/uyumsuz**. | **KARANTİNA.** `DEC-0025` authoritative-current, delivery-observed, consumer-reconciled, outcome-unknown, suspension/revocation ve restore quarantine ayrımını ister. Metadata iyi adaydır; yeterli state closure değildir. |
| R-18 | §3: Hard delete offline replika habersiz kalır; her yerde tombstone, sonra background physical cleanup zorunludur. | Dağıtık sync mekanizması güvenilir; global zorunluluk değil. | **KABUL (koşullu).** Tombstone/delete event ve no-silent-loss için iyi aday; retention, privacy erasure, legal hold, shared/private/history sınırları ve compaction kanıtı gerekir. “Her yerde yalnızca tombstone” kararı yoktur. |
| R-19 | §3/table: Trigger/temporal/CDC için işlem maliyeti, migration, context güvenilirliği ve history puanları kesin verilmiştir. | **Vendor/blog bağımlı görüş**; **aşırı kesin puan**. | **REDDİT.** Workload/row size/transaction mix/extension/provider/restore test olmadan kıyaslama yapılmaz. |
| R-20 | §4: Delta/cursor/time-since sync, ETag/If-None-Match ve 304 bodyless yanıt data tüketimini sıfırlar. | Delta/conditional GET güvenilir mekanizma; “sıfır” **aşırı kesin**. | **KABUL (düzeltilmiş).** Cursor/monotonic change token ve conditional GET payload'ı azaltır; request, headers, auth, validation ve 304 response yine byte/CPU tüketir. Timestamp cursor clock/order gap yaratabilir. |
| R-21 | §4: UI write ile local row ve transactional outbox aynı SQLite transaction'ında; cihaz kapansa da sırayla gönderim garanti. | Güvenilir pattern; **primary-source/implementation evidence gerekli**. | **KABUL (aday mekanizma).** Local mutation + outbox atomikliği kayıp penceresini azaltır; scheduler, retry/poison state, cancellation, eviction, app kill, duplicate, ordering ve server rejection ayrıca kapanmalıdır. Internal Operations approve/publish/role mutation'ları offline outbox ile yetkili hale getirilemez. |
| R-22 | §4: Her mutation'a idempotency_key verilir; server duplicate'i engeller. | Güvenilir kontrol; standardizasyon kısmen açık. | **KABUL (koşullu).** Key + payload fingerprint/scope/TTL/result replay/actor binding ve unknown outcome reconciliation gerekir. Key tek başına duplicate, authorization veya conflict çözmez. IETF `Idempotency-Key` metni 2026-09-18 itibarıyla Internet-Draft'tır; RFC diye sunulamaz. |
| R-23 | §4: Dağıtık primary key standardı mutlaka UUIDv4 olmalıdır. | **Categorical rejection**; primary-source bunu desteklemiyor. | **REDDİT.** UUIDv4 geçerli random identifier'dır; UUIDv7 veya başka collision/ordering/storage stratejileri de değerlendirilebilir. ID seçimi schema/index, privacy, offline generation ve migration testidir. |
| R-24 | §4/table: LWW en basit/en yaygın, belirli kullanımda uygundur; clock skew veri kaybettirir. | Mekanizma ve risk güvenilir; “en yaygın” vendor görüşü. | **KABUL (sınırlı).** Low-consequence/settings/telemetry için aday olabilir; safety, provenance, entitlement, official content ve critical history için sessiz overwrite kabul edilmez. Server version/causal metadata gerekir. |
| R-25 | §4: Field-level merge farklı alanları kayıpsız birleştirir; aynı alan için timestamp kuralı yeterlidir. | Mekanizma makul; **aşırı kesin**. | **KARANTİNA.** Alanlar arası invariant, derived value, delete-vs-update, authorization ve causality nedeniyle “kayıpsız” garanti edilemez. Her field/operation conflict policy, review ve rollback ile tanımlanır. |
| R-26 | §4: CRDT merkezi kararı gerektirmez, text/counter'da kusursuz ve table'da veri kaybı sıfırdır. | CRDT convergence mekanizması güvenilir; **aşırı kesin/categorical**. | **KARANTİNA / “sıfır-kayıp/kusursuz” reddedilir.** CRDT semantik/domain invariant, authorization, deletion, retention, metadata bloat ve human meaning conflict'lerini çözmez. Relational integration için task-specific proof gerekir. |
| R-27 | §4: Kritik mali/idari veriler manual conflict queue'da iki sürüm saklanıp insan tarafından çözülmelidir. | Proje yönüyle güvenilir risk kontrolü. | **KABUL (koşullu).** `DEC-0024/0026` high-consequence uncertainty → fail-closed/HELD ve independent human review ile uyumludur; reviewer competence, quorum, stale version ve audit evidence açık kalır. |
| R-28 | §4/table: LWW high, field low-medium, CRDT zero, manual zero data-loss riskidir. | **Aşırı kesin/categorical**. | **REDDİT.** Hiçbir merge stratejisi zero-risk değildir; doğru ifade “risk sınıfına ve domain policy'ye göre test edilecek aday”dır. |
| R-29 | §5: PostgreSQL BYTEA/BLOB her zaman tablo şişmesi/cache/backup/sync kilitlenmesi yaratır; object storage temel kuraldır. | BLOB trade-off'u gerçek; **vendor/blog bağımlı**, mutlak öneri yanlış. | **KARANTİNA.** PostgreSQL TOAST ve large-object mekanizmaları binary veri destekler. Küçük immutable attachment ile büyük video aynı değildir; object metadata, backup, access, retention ve egress workload ile seçilir. |
| R-30 | §5: Presigned URL backend'i payload trafiği/CPU'dan muaf eder; 15 dakika geçerli olmalıdır; single PUT 50–100 MB altındadır. | Presigned upload mekanizması güvenilir; **aşırı kesin sayı**; provider-specific. | **KABUL (aday pattern), KARANTİNA (TTL/size).** Scope/content-type/checksum/expiry/replay/revocation/ownership ve provider semantics gerekir. Payload path backend'i azaltabilir; “sıfır” kaynak maliyeti değildir. Boyut/TTL ağ ve threat-model testidir. |
| R-31 | §5: TUS/multipart bağlantı kesintisini tamamen engeller ve başarısızlığı ortadan kaldırır. | Resumable mechanism güvenilir; **aşırı kesin**. | **KABUL (koşullu).** TUS offset/HEAD/PATCH ve multipart retry wastage azaltır; auth, checksum, expiry, orphan cleanup, finalization, event idempotency ve storage limitleri yine failure üretir. |
| R-32 | §5: Upload sonrası webhook + magic bytes + AV scan ile dosya `active` yapılır; global storage key asla client'a verilmez. | Quarantine-first güvenlik mekanizması; proje ile uyumlu. | **KABUL (kontrol prensibi).** `DEC-0026` quarantine-first layered validation bunu destekler. Event authentication, race, scanner verdict/timeout, decompression bomb, content policy, lineage ve failed/held state eklenmelidir; scan teknik doğruluk/approval değildir. Global secret'ın client'a verilmemesi güçlü guardrail'dir. |
| R-33 | §5: Egress-free S3 veya katı CDN ile maliyet kontrol edilir. | **Vendor/blog bağımlı görüş**; güncel maliyet iddiası. | **KARANTİNA.** “Egress-free” plan/region/route/volume/terms'e bağlıdır; `DEC-0030` gereği resmi fiyat, cap/overage, tax/currency, retention ve exit sheet gerekir. S3 compatibility lock-in'i yok etmez. |
| R-34 | §5/table/§9: DB BLOB ve backend proxy kesin reddedilmeli; 50 MB üstü single-request URL kesin reddedilmeli. | **Categorical rejection**, unsupported threshold. | **REDDİT (karar olarak).** Büyük/high-risk upload için direct/resumable aday olabilir; küçük/sensitive/scan/transaction-bound upload için proxy veya DB storage bazı durumlarda makul olabilir. Her iki yol threat-model ve workload ile test edilir. |
| R-35 | §5: Standart S3 API ve PG syntax/protocol provider exit'i güvenceye alır; proprietary SDK client/server'a sızmamalı. | Exit prensibi güvenilir; garanti değil. | **KABUL (koşullu).** Portability için open formats, export/import, schema/extension inventory, object metadata/version/ACL semantics, keys, restore test ve migration rehearsal de gerekir. “S3-compatible” eşdeğer davranış garantisi değildir. |
| R-36 | §6: RPO/RTO iki temel süre metriğidir; RPO'yu saniyelere indirmek yalnız base backup + continuous WAL/PITR ile mümkündür. | RPO/RTO tanımı güvenilir; **only/seconds** ifadesi aşırı. | **KABUL (tanım), KARANTİNA (hedef/only).** PITR iyi bir adaydır; gerçek RPO archive lag, commit/replication mode, backup health ve restore testine bağlıdır. RPO/RTO sayıları `DEC-0025` altında açık sorudur. |
| R-37 | §6: pgBackRest endüstri standardı, değişen 8 KB blokları kopyalar; WAL-G daha basit/hızlı; Barman kurumsal ve tek DB'de gereksizdir. | **Vendor/blog bağımlı görüş**; benchmark yok. | **KARANTİNA.** Araç özellikleri resmi project docs, sürüm, storage backend, operator skill, restore drill ve cost ile karşılaştırılmalıdır. “Standard/fast/simple/unnecessary” universal facts değildir. |
| R-38 | §6/table: `pg_dump` evrensel taşınabilir, 24 saat RPO; PITR saniye ve çok hızlı; physical backup yalnız aynı major PG sürümüdür. | Kısmen güvenilir backup mekanizması; **aşırı kesin sayılar/categorical**. | **KARANTİNA.** `pg_dump` logical export'tur ve WAL replay/PITR değildir; portability extension/collation/version/privilege ile sınırlanır. Restore süreleri ve version support test edilir; `24 saat`, `saniyeler`, “çok hızlı” fixture değildir. |
| R-39 | §9/table: Güvenlik-kritik sistemde yalnız günlük `pg_dump` kabul edilemez; 24 saat RPO legal/security ihlalidir; PITR zorunludur. | **Yanlış proje kararı / categorical rejection**; numeric target open. | **REDDİT (şimdiki karar olarak).** `DEC-0025` RTO/RPO hedeflerini açık bırakır. PITR/continuous archive bir değerlendirilecek control olabilir; legal requirement ve mandatory technology ancak scope, data classification, impact analysis ve restore evidence ile kararlaştırılır. `pg_dump` tek başına yeterli olmayabilir, fakat bunun sayısal sonucu rapordan çıkmaz. |
| R-40 | §7: Managed BaaS/DBaaS OS patch/PITR/connection pooling'i transparan yapar; self-host VPS sabit/öngörülebilir ve lock-in sıfır; hybrid dengeli ve rasyoneldir. | **Vendor/blog bağımlı görüş**, **aşırı kesin maliyet/lock-in**, provider/architecture selection. | **KARANTİNA.** Managed kapsamı plan/provider'a göre değişir; backup restore/retention/egress/limits/SLA doğrulanır. Self-host provider, hardware, operator ve incident cost taşır; lock-in sıfır değildir. Hybrid önerisi provider ve paid-service kararıdır, onaylanmadı. |
| R-41 | §7/table: Managed `$0–25/ay`, VPS `$10–40/ay`, hybrid `$15–60/ay`; kota aşımı “logaritmik”; managed “tek tık” PITR. | **Aşırı kesin/uydurma olasılıklı sayı**; vendor/pricing bağımlı. | **REDDİT.** Güncel resmi pricing/region/tax/currency/free cap/overage/egress/backup/storage/restore ve exit olmadan bütçe kanıtı değildir. `DEC-0030` bu aralıkları pre-approve etmez. |
| R-42 | §7/§9: Sistem yöneticisi olmayan solo projede raw VPS PostgreSQL kesin reddedilmeli; insan hatası kaçınılmaz felakettir. | Risk mekanizması makul; **categorical/duygusal genelleme**, proje kararı değil. | **KARANTİNA / rejection olarak reddedilir.** Operator burden ciddi bir ölçüttür; self-host ancak görev sınırı, otomasyon, restore drill, monitoring, security ownership ve bütçe ile kıyaslanır. Yönetilen servis de failure/lock-in/cost riskini ortadan kaldırmaz. |
| R-43 | §8: AI-generated code'un `%45–70`'i OWASP Top 10 zaafiyetini doğrudan production'a taşır. | **Aşırı kesin/uydurma olasılıklı sayı**; source/vendor aggregation. | **REDDİT.** Controlled task failure, generated snippet, repository scan, production incident ve OWASP category aynı ölçü değildir. Sayı genellenemez. AI çıktısı untrusted input kabulü yine geçerlidir. |
| R-44 | §8: AI auth kurar ama authorization/BOLA'yı sistematik atlar; RLS'yi gevşetir/devre dışı bırakır; public key + RLS gap tüm DB'yi açar. | BOLA/RLS risk mekanizması güvenilir; AI genellemesi için primary-source gerekli. | **KABUL (risk kontrolü), KARANTİNA (AI prevalence).** OWASP object-level authorization'ın her ID kullanan endpoint'te kontrol edilmesini önerir. RLS/public key sonucu schema, role, policy ve endpoint'e bağlıdır; secret/public key ayrımı doğru kurulmalıdır. RLS/API defense-in-depth test edilir. |
| R-45 | §8: Beş AI düzeltme turunda kritik açıklar `%37,6` artar; modeller security block'larını sessizce silmeye eğilimlidir. | **Aşırı kesin/uydurma olasılıklı sayı**; secondary/vendor citation. | **KARANTİNA.** Iterative degradation makul threat hypothesis'tir; model, prompt, task, diff, test suite ve security metric belirtilen tekrarlanabilir primary study olmadan project constant olmaz. Her change için diff/contract/security regression evidence daha güvenli kontroldür. |
| R-46 | §8/table: Secrets, dependency hallucination, SAST/SCA/secret scanning ve visual sync queue zorunludur. | Mekanizma/risk güvenilir; tool/provider seçimi açık. | **KABUL (kontrol hedefi olarak).** `DEC-0027–0029` provenance/SBOM, independent review, task evidence ve owner'ın debug etmemesi yönüyle uyumludur. Static scan runtime authorization/configuration kanıtı değildir; adversarial behavior test ve protected audit de gerekir. Belirli tool/vault satın alma kararı yoktur. |
| R-47 | §8/table: Nontechnical owner karmaşık sync motorunu debug edemez; aylarca sessiz data loss fark edilmeyebilir. | Proje operating model ile uyumlu risk senaryosu; sayı/olay kanıtı yok. | **KABUL (risk çerçevesi).** `DEC-0029` owner'ı repair/debug bağımlılığına sokmaz. Queue status, retry cap, dead-letter/HELD, reconciliation, alert/evidence ve restore drill requirement olarak tasarlanabilir; “aylarca” iddiası kanıt değildir. |
| R-48 | §9/table: NoSQL ve distributed SQL, direct RLS-only BaaS, KV store, experimental web storage, DB BLOB/proxy, >50 MB single PUT, daily pg_dump, raw VPS kesin reddedilmelidir. | Toplu **categorical rejection**; proje otoritesiyle çatışma. | **REDDİT (toplu karar olarak).** Rapor teknoloji/ADR seçme yetkisine sahip değildir. Her adayın risk, semantics, cost, operator, exit ve test evidence'ı aynı rubric ile kıyaslanır; yalnız approved product controls ve negative gates binding'dir. |
| R-49 | §10: “En rasyonel” çözüm managed DB + app VPS hybrid; standard PG/S3 ile tam manevra kabiliyeti. | **Vendor/blog bağımlı görüş**; architecture/provider decision; aşırı kesin exit iddiası. | **REDDİT (karar olarak), KARANTİNA (alternatif hipotez).** Bu seçim `DEC-0030` cost sheet, capability/restore evidence, provider terms ve ADR gerektirir. Standart arayüzler migration'ı kolaylaştırır ama tam portability/operational freedom kanıtlamaz. |

## 4. Özellikle incelenen karar alanları

### 4.1 Flutter Web ve browser persistence

Resmi Flutter dokümanı browser hedefinin mümkün olduğunu ve Flutter Web'in browser-based SPA/interactive apps için kullanılabildiğini; aynı zamanda her HTML senaryosunun Flutter için ideal olmadığını söyler. Bu, **Flutter Web'in mümkün bir aday** olduğunu gösterir; `DEC-0033` veya Internal Operations'ın “browser-based” yönünü Flutter Web'e çevirmeye yetmez.

OPFS, IndexedDB ve Web Locks resmi web-platform belgelerinde gerçek mekanizmalardır: OPFS origin-private storage ve worker içi sync access sunabilir; IndexedDB transaction/asynchronous storage sağlar; quota/eviction browser'a göre değişir; Web Locks same-origin tab/worker koordinasyonu sağlayabilir. Bunların hiçbiri browser storage'ın kullanıcı verisi için kalıcı, sınırsız, backup'lı veya audit-authoritative olduğu anlamına gelmez. Gizli pencere, storage clearing, quota pressure, tab crash, browser/version/accessibility ve authentication lifecycle matrisi ölçülmeden “Flutter Web dayanıklılığı” puanı verilemez.

**Sonuç:** Flutter Web varsayımı `REDDİT`; browser persistence mekanizmaları `KARANTİNA`; Internal Operations online-first davranışı bir product/operations control olarak sonraki web-client tartışmasına taşınabilir. Bu inceleme web frontend seçmez.

### 4.2 Server-authoritative ve local-first ayrımı

Local-first literatürü local copy'yi primary copy olarak tanımlar; bu, rapordaki tanımın kavramsal olarak tutarlı olduğunu gösterir. Fakat bu projenin approved direction'ı şu ayrımı korur:

| Alan | İnceleme sonucu |
|---|---|
| Consumer offline reads/task package | Selected motorcycle/task scope, compact safety/application/recovery closure ve release/client compatibility ile bounded olabilir. |
| Consumer local mutation | Tentative/local pending olabilir; server reconciliation, conflict ve unknown outcome görünür kalmalıdır. Local-final ürün authority'si değildir. |
| Internal Operations approve/publish/recall/role mutation | `DEC-0024` gereği authoritative online sonuç; local-first/local-outbox bunu bypass edemez. |
| Release/content/audit truth | `DEC-0025–0027` immutable meaning, protected audit, current revocation/suspension ve separate observed/reconciled states ile taşınır. |

Bu nedenle raporun iki modeli açıklaması `KABUL (terminology)`, local-first'i Kavriva'nın varsayılanı yapması `REDDİT`tir.

### 4.3 PostgreSQL, API ve RLS

PostgreSQL resmi dokümanı RLS'nin tablo satırlarına user/role bazlı erişim politikaları uyguladığını; RLS açık ve policy yoksa normal erişimin default-deny olabildiğini, ancak table owner/superuser/BYPASSRLS gibi istisnalar ve policy tasarım/race riskleri bulunduğunu gösterir. Bu, raporun “authorization must be tested and defense-in-depth” kaygısını destekler; `%50 üzeri AI RLS hatası` veya direct BaaS'ın **mutlak** reddini desteklemez.

PostgreSQL logical replication/logical decoding değişiklikleri publication/slot/output plugin ile dış tüketicilere aktarabilir. Değişiklik akışı transaction/row seviyesinde useful CDC olabilir; actor, session, approval reason, competence veya protected audit custody otomatik olarak tamamlanmış değildir. API, database function, RLS, service boundary veya başka bir combination seçimi sonraki ADR'nin konusudur.

**Güvenli intake:**

- RLS, object/function/property authorization, network/service identity ve adversarial negative tests ayrı kontrol yüzeyleri olarak değerlendirilir.
- “Client authenticated” ≠ “requested object/action/scope authorized.”
- Direct DB/BaaS varsa bile RLS-only assumption yapılamaz; bağımsız API varsa da API'nin doğru authorization yaptığını kanıtlamak gerekir.
- PostgreSQL provider veya başka DB seçimi bu dosyada yapılmaz.

### 4.4 Audit ve CDC

`DEC-0025` ve `DEC-0026` ile uyumlu güvenli çekirdek: attributable, ordered, tamper-evident/protected audit; normal ve emergency action'lar; fallback/hold; release/current/delivery/reconciliation state ayrımı; quarantine-first ingestion. Trigger, temporal history ve CDC **tamamlayıcı teknik adaylardır**, audit authority değildir. WAL/CDC'nin “sıfır yük” veya trigger'ın “hiçbir değişiklik kaybolmaz” iddiası reddedilmiştir.

### 4.5 Delta, outbox, idempotency ve conflict

HTTP conditional request/ETag, delta/cursor, outbox ve idempotency ağ kesintisi/data-efficiency tasarımına yararlı yapı taşlarıdır. Ancak:

- 304 gövdeyi kaldırır; request/header/CPU/authorization maliyetini sıfırlamaz.
- Timestamp cursor yerine ordering/monotonic cursor, gap/replay ve retention davranışı test edilir.
- Outbox atomik local commit'i destekler; delivery, retry, poison, duplicate, revocation ve app-kill closure ayrıca gerekir.
- Idempotency key duplicate retry'yi sınırlayabilir; key scope, payload mismatch, TTL, result replay, actor binding ve `outcome unknown` reconciliation gerekir.
- LWW/field merge/CRDT/manual queue, domain consequence'a göre seçilecek adaylardır. “zero data loss”, “lossless”, “perfect” denemez.
- High-consequence disagreement `HELD`/manual review olabilir; local client otomatik winner değildir.

### 4.6 Object storage ve uploads

Object storage, presigned URL, multipart veya TUS; büyük/kararsız ağ upload'ında aday mekanizmalardır. TUS primary protocol specification offset/HEAD/PATCH resume ve auth'ın implementation'a bırakıldığını açıkça tanımlar; bu, “resume vardır” iddiasını destekler, “failure tamamen engellenir” iddiasını değil. PostgreSQL TOAST ve large objects ise DB'nin binary depolayabildiğini gösterir; DB BLOB/proxy'nin evrensel olarak yasak olduğunu göstermez.

`DEC-0026` ile alınabilecek çekirdek, storage teknoloji seçimi değil yaşam döngüsüdür: untrusted upload → quarantine → layered validation (type/magic bytes/limits/malware/policy) → attributable status → review/active veya held/rejected; original/derived lineage korunur; client'a global secret verilmez. Scope, expiry, checksum, event authentication, orphan cleanup, privacy/retention ve egress/cost sonraki tartışmadır.

### 4.7 Backup/PITR ve managed/self-host

PostgreSQL resmi backup dokümanı base backup + continuous WAL archiving ile PITR yapılabildiğini, `pg_dump`/`pg_dumpall` logical dump'larının WAL replay için filesystem backup olmadığını ve archive lag/monitoring/restore testinin önemli olduğunu doğrular. Bu, PITR'i **değerlendirilecek bir control** yapar; belirli saniye RPO, `24 saat legal violation`, belirli araç, provider veya managed plan zorunluluğu çıkarmaz.

Managed hizmette responsibility shared'dir; planın backup retention, PITR granularity, restore authority, network/egress, quota, incident support, region, export ve deletion terms'i okunmadan “otomatik/tek tık/sıfır bakım” denemez. Self-host'ta operator burden ve failure-domain artabilir; bu, `DEC-0030` bağlamında önemli bir criterion'dur ama bu intake'ı provider kararına dönüştürmez.

## 5. Kabul / karantina / reddetme özeti

| Karar | Güvenle alınabilecek veya alınamayacak içerik |
|---|---|
| **KABUL — mekanizma/guardrail** | Task-scoped data-efficient offline package; compact safety/recovery closure; explicit compatibility/freshness; separate authoritative/delivery/reconciled states; server-side contextual authorization; RLS/defense-in-depth and BOLA negative tests; protected attributable audit; quarantine-first upload; no client global storage secret; delta/cursor and conditional request as candidates; transactional outbox as candidate; idempotency + unknown-outcome reconciliation; manual/HELD conflict for high consequence; restore/PITR/backup drill as evaluated control; AI output as untrusted input; independent review, SAST/SCA/secret/supply-chain and behavioral security evidence; nontechnical owner must not debug/repair. |
| **KARANTİNA — kanıt tamamlanana kadar** | Flutter Web; browser OPFS/IndexedDB/SQLite-WASM architecture; PostgreSQL as selected DB; independent API as mandatory shape; temporal tables; WAL CDC performance/context; SQLite/Drift and reactive design; object storage/presigned/multipart/TUS implementation; pgBackRest/WAL-G/Barman ranking; managed/self-host/hybrid topology; S3 exit claim; exact risk/role/storage/retention/cost limits; all vendor/blog-derived comparison scores. |
| **REDDİT — bu rapordan proje kararı yapılamaz** | Local-first as universal authority; “zero risk/zero overhead/zero loss/perfect”; `%68`, `%40–60`, `%45–70`, `%37,6`, `%50+` and similar AI/security numbers as project constants; UUIDv4 mandatory; BLOB/proxy/single PUT/NoSQL/distributed SQL/direct RLS-only/raw VPS/daily pg_dump categorical bans; `24h RPO legal violation`; managed DB + app VPS as “most rational”; `$0–25/$10–40/$15–60` prices; Flutter Web as Internal Operations frontend. |

## 6. Araştırmadan güvenle taşınabilecek çalışma girdileri

Bu maddeler yeni karar değildir; sonraki debate/ADR hazırlığına ölçülebilir acceptance/evidence olarak taşınabilir:

1. **Offline package contract:** selected motorcycle + applicable task + release/client compatibility + compact text/steps/warnings/checks/safe-stop/recovery; heavy media optional; expected size/network preference visible.
2. **Authority/state contract:** tentative local, server accepted, authoritative-current, delivery-observed, consumer-reconciled, outcome-unknown, suspended/revoked and restored-quarantine states cannot collapse into one `published` flag.
3. **Mutation contract:** client mutation identity, origin/device context, schema/release context, server idempotency scope, replay/duplicate semantics, retry/poison/HELD and reconciliation evidence.
4. **Conflict contract:** no silent overwrite for safety/provenance/entitlement/official content; low-consequence auto policy only if explicitly bounded; high-consequence conflict preserves both evidence and requires reviewed resolution.
5. **Authorization/audit contract:** every sensitive action is checked server-side against actor/session/action/scope/state/classification/consequence/independence; audit remains ordered, attributable, protected and recoverable; UI/cache/role badge is never authority.
6. **Ingestion contract:** original and derived artifact lineage; quarantine before preview/parse/scan; file type/size/content/malware/URL policy; scan result does not equal technical correctness or approval; unknown/mixed classification follows restrictive handling.
7. **Storage/upload contract:** compare DB, proxy, presigned, multipart and resumable options by confidentiality, integrity, availability, metadata consistency, cleanup, egress and exit. No fixed byte/TTL threshold without fixture and test evidence.
8. **Backup/continuity contract:** explicit RPO/RTO candidates, archive lag, protected backup custody, config/secret coverage, restore quarantine, restore rehearsal and evidence. `pg_dump`/PITR/tool/provider selection remains open.
9. **AI-native delivery contract:** generated code/config/schema/migration is untrusted until independent static, dependency, secret, authorization-behavior, adversarial and release/provenance checks pass. “AI wrote it” is not a security metric; a study number is not product evidence.
10. **Cost/exit contract:** every paid or recurring candidate shows current official price, free/capped path, tax/currency uncertainty, overage/egress, credential/data handling, restore/export path and deferral. Unaffordable mandatory assurance remains `HELD`.

## 7. Primary/official spot-check register

Bu kaynaklar raporun vendor/blog listesini “doğru” ilan etmez; yalnızca belirli mekanizmaların sınırlarını kontrol etmek için kullanılmıştır. Provider dokümanları mekanizmanın o provider'daki davranışı için birincildir, pazar bağımsız seçim kanıtı değildir.

| Kaynak | Spot-check sonucu |
|---|---|
| [Flutter Web resmi dokümanı](https://docs.flutter.dev/platform-integration/web) | Browser target/SPA mümkün; her HTML senaryosu ideal değil. Flutter Web proje seçimi değildir. |
| [MDN: OPFS](https://developer.mozilla.org/en-US/docs/Web/API/File_System_API/Origin_private_file_system), [MDN: IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API), [W3C Web Locks](https://www.w3.org/TR/web-locks/) | OPFS/IndexedDB/lock mekanizmaları mevcut; quota/eviction, origin scope, worker/tab lifecycle ve storage clearing sınırları vardır. Durability/backup/authority garantisi yoktur. |
| [PostgreSQL RLS](https://www.postgresql.org/docs/current/ddl-rowsecurity.html) | Row policy per-user access control sağlar; default-deny ve owner/superuser/BYPASSRLS istisnaları vardır; policy'ler test edilmelidir. AI `%50+` sonucu yoktur. |
| [PostgreSQL logical replication](https://www.postgresql.org/docs/current/logical-replication.html), [logical decoding](https://www.postgresql.org/docs/current/logicaldecoding.html) | Transaction/row changes external consumer'a akabilir; publication/slot/output plugin/replica identity ve operational lag vardır. Bu otomatik protected audit/provenance değildir. |
| [PostgreSQL TOAST](https://www.postgresql.org/docs/current/storage-toast.html), [large objects](https://www.postgresql.org/docs/current/largeobjects.html) | `bytea`/large value/stream-style large object desteklenir. BLOB'un her workload'da yasak olduğu sonucunu desteklemez. |
| [PostgreSQL continuous archiving/PITR](https://www.postgresql.org/docs/current/continuous-archiving.html), [pg_dump](https://www.postgresql.org/docs/current/app-pgdump.html) | Base backup + WAL archive PITR sağlayabilir; logical dump WAL replay değildir; archive/restore monitoring ve test gerekir. Numeric RPO/mandatory tool seçmez. |
| [RFC 9110 conditional requests](https://www.rfc-editor.org/rfc/rfc9110.html#name-if-none-match) | `If-None-Match` uygun durumda 304 ve body transferini önleyebilir; toplam veri/CPU tüketimi sıfır değildir. HTTP idempotence da method semantics'e bağlıdır. |
| [RFC 9562 UUID](https://www.rfc-editor.org/rfc/rfc9562.html) | UUIDv4 random UUID'dir; RFC ayrıca v6/v7/v8 gibi biçimleri tanımlar. UUIDv4 zorunluluğu yoktur. |
| [TUS resumable upload protocol](https://tus.io/protocols/resumable-upload) | HEAD ile offset ve PATCH ile resume core mekanizmadır; auth/authorization server implementation'a bırakılır; protocol failure'ı tamamen yok etmez. |
| [OWASP API1:2023 BOLA](https://api-security.owasp.org/editions/2023/en/0xa1-broken-object-level-authorization/) | User-controlled object ID için every relevant function'da object-level authorization ve tests önerilir; BOLA riskini destekler, AI prevalence yüzdesini değil. |
| [NIST SP 800-218A](https://csrc.nist.gov/pubs/sp/800/218/a/final) | GenAI/dual-use geliştirmede SSDF practices/tasks'e ekler; güvenli lifecycle/validation desteğidir, rapordaki oranları doğrulayan bir istatistik değildir. |
| [Pearce et al., IEEE S&P / arXiv](https://arxiv.org/abs/2108.09293), [Fu et al., empirical study](https://arxiv.org/abs/2310.02059) | Kontrollü Copilot senaryosunda yaklaşık `%40`; GitHub proje snippet'lerinde Python `%29,5`, JavaScript `%24,2` raporlanmıştır. Bunlar model/sürüm/dil/task/ölçüm bağlamına özgüdür; “tüm AI code production'da `%45–70`” değildir. |
| [Local-first paper/essay](https://www.inkandswitch.com/essay/local-first/) | Local-first local copy'yi primary olarak tanımlar; kavramsal bir alternatifdir, Kavriva için authority kararı değildir. |

## 8. Kaynak kalitesi ve raporun bibliyografyası

Raporun `[1]–[46]` listesinde Sci-bot, Medium, bağımsız bloglar, Stackademic, CSS Author, Hacker News, Reddit, vendor blog/docs ve aggregator'lar birlikte kullanılmıştır. Bunlar fikir keşfi veya ürün dokümanı olarak okunabilir; bağımsız güvenlik oranı, evrensel performans, legal zorunluluk, “industry standard”, maliyet ve categorical rejection için yeterli primary evidence değildir.

Özellikle:

- `[19]` OX Security blogu vendor içerik/marketing bağlamındadır; ürünün risk anlatısı bağımsız prevalans ölçümü değildir.
- `[20]` CSA research note, farklı vendor/secondary çalışmalardan `%45–70` gibi metodolojileri bir araya getirir; bu aralık “tüm AI-generated production code” population estimate değildir.
- `[14]–[15]`, `[42]–[45]` backup comparison ve fiyat/performance ifadeleri independent benchmark veya resmi product capability matrix yerine blog/secondary içeriklere dayanır.
- `[31]`, `[35]`, `[41]` object upload/storage provider belgeleri kendi ürünlerinin davranışını doğrulayabilir; tüm S3/object-storage pazarının maliyet/çıkış garantisi değildir.
- `[7]–[10]`, `[24]`, `[30]` library/vendor docs gerçek API/issue durumunu gösterebilir; Kavriva'nın browser/client teknoloji kararını veya release readiness'ini kanıtlamaz.

Primary/official spot-check'ler, raporun faydalı mekanizma çekirdeğini korurken “zero/perfect/mandatory” ve oranların karar kanıtı olamayacağını doğrulamaktadır.

## 9. Sonuç ve sonraki tartışma sınırı

Bu intake'ın güvenli sonucu **provider-independent control setidir**, belirli stack değil. Sonraki tartışma ancak şu kanıt paketleriyle ilerlemelidir: görev/veri/risk sınıfları; consumer vs Internal Operations authority matrix; target browsers/devices; offline package size/content fixture; conflict/retry/unknown scenarios; audit custody; upload threat model; backup/restore RPO-RTO experiments; current staged cost/exit sheet; AI task graph and independent validation evidence.

Bu dosya şu kararları **vermez**: Flutter Web; PostgreSQL; independent API; RLS-only veya RLS+API; SQLite/Drift; object storage/S3/TUS; UUIDv4; pgBackRest/WAL-G/Barman; managed DB, VPS veya hybrid; herhangi bir vendor, auth, CDN, scanner, AI provider, OTA channel, subscription, ADR veya code/build/device/release readiness.

`DEBATE-007` burada kapanır: mekanizmalar kontrollü araştırma girdisi olarak kabul edilmiş, unsupported numbers/vendor opinions/categorical technology conclusions karantinaya alınmış veya reddedilmiş, proje kararları değiştirilmemiştir.
