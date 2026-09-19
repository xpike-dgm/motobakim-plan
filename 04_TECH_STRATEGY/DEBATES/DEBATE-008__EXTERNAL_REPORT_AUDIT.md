# DEBATE-008 — Flutter Backend Karşılaştırma Matrisi Dış Raporu Denetimi

Durum: `BAĞIMSIZ KANIT DENETİMİ / NO-CODE / PROVIDER SEÇİMİ YOK`
Tarih: `2026-09-18`
İncelenen belge: `C:\Users\Xpike\Downloads\Flutter Backend Karşılaştırma Matrisi.md`

## 1. Kapsam ve hüküm

Bu dosya dış raporu talimat olarak kabul etmez. Raporun Supabase, Firebase/Firestore,
Appwrite, PocketBase ve Neon + bağımsız API + Cloudflare R2 bileşimi hakkındaki fiyat,
hard-cap, offline, güvenlik, yedek/PITR, bölge, vendor lock-in, hesap kapanması ve yönetim
yükü iddialarını; 2026-09-18 tarihinde erişilebilen resmi/ürün sahibi birincil belgelerle
karşılaştırır. Bu, hukuki görüş, üretim readiness kanıtı veya bir aday seçimi değildir.

Sonuç kısa biçimde:

- Raporun bazı mekanizma çekirdekleri **DOĞRULANDI**: Firestore mobil offline persistence;
  `get()/exists()` kural erişimlerinin maliyeti; Supabase Pro fiyatı, günlük yedek ve
  PITR add-on fiyatı; Appwrite Cloud fiyat/region/budget-cap mekanizmasının varlığı;
  PocketBase API-rule ve snapshot backup yüzeyi; Neon kullanım bazlı Postgres fiyatı ve
  R2’nin doğrudan egress ücreti almaması.
- Bu çekirdekler çoğunlukla kapsam, ürün, tarih veya failure-mode şartları silinerek
  yazılmıştır. `hard cap`, `tam uyum`, `sıfır vendor lock-in`, `sıfır hesap kapanma riski`,
  `dakikalar içinde self-host`, `AI RLS'yi yüksek tutarlılıkla yazar` gibi sonuçlar
  **KISMEN DOĞRU/BAĞLAMA BAĞLI**, **DOĞRULANAMADI** veya **YANLIŞ/YANILTICI**dır.
- Raporun "2026 resmî ve doğrulanmış" metodoloji beyanı **YANLIŞ/YANILTICI**dır. Kaynakça
  birincil vendor belgeleri, vendor blogları, bağımsız bloglar, Stack Overflow, Reddit,
  pub.dev ve aggregator'ları karıştırır. Özellikle `[50]` `https://yippee-bot.com/`
  Firebase/Google Cloud hesap askıya alma kanıtı değildir; `[14]` CheckThat ve `[57]`
  RFP.wiki gibi ikincil sayfalar da olasılık veya lock-in sıralaması kanıtlamaz.
- Dış rapor, onaylı `DEC-0034` veri omurgasını ve `DEBATE-008__FINALIST_COMMON_FIXTURE.md`
  eşit karşılaştırma sözleşmesini uygulamadan doğrudan `Supabase Pro` ve `PocketBase`
  önerilerine gider. Bu nedenle rapor **araştırma girdisi olarak sınırlı kabul**, provider
  kararı olarak **REDDİ** edilmelidir.

### Sınıflandırma anahtarı

| Etiket | Anlam |
|---|---|
| **DOĞRULANDI** | Resmî kaynak, iddianın aynı ürün/plan/kapsam için doğrudan doğrulanabilir çekirdeğini destekliyor. |
| **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Mekanizma doğru; kapsam, istisna, plan, veri modeli, workload veya operasyon şartı eksik. |
| **DOĞRULANAMADI** | Güncel birincil kanıt, ölçüm, sözleşme veya test bulunmadı; “yok” hükmü kurulamıyor. |
| **YANLIŞ / YANILTICI** | Resmî kaynakla çelişiyor veya doğru çekirdekten desteklenmeyen mutlak/hukuki/operasyonel sonuç çıkarıyor. |

## 2. Resmî kaynaklarla hızlı karşılaştırma

| Kontrol alanı | Supabase | Firebase / Firestore | Appwrite Cloud | PocketBase self-hosted | Neon + API + R2 |
|---|---|---|---|---|---|
| Fiyat ve ücretsiz kota | **DOĞRULANDI**, ancak tarihe/plan ve bölgesel vergiye bağlı | **DOĞRULANDI**; Firestore ücretsiz kota günlük ve tek ücretsiz DB ile sınırlı | **DOĞRULANDI**; güncel Free/Pro rakamları raporla büyük ölçüde örtüşüyor | **DOĞRULANAMADI**; PocketBase SaaS fiyatı yok, VPS bedeli provider'a bağlı | **KISMEN DOĞRU**; Neon rakamları güncel sayfada var, API maliyeti bileşime bağlı |
| Mutlak hard cap | **YANLIŞ / YANILTICI**; Spend Cap yalnız belirli usage item'larını kapsar | **KISMEN DOĞRU**; Firestore kullanımında genel hard cap yok; yeni Firebase spend-cap preview yalnız seçili hizmetlerde | **KISMEN DOĞRU**; budget cap otomatik add-on ölçeklemesini sınırlar, recurring plan ücretini kapsamaz | **KISMEN DOĞRU**; PocketBase SaaS overage yok, fakat VPS/host hesabı ve kaynak maliyeti vardır | **YANLIŞ / YANILTICI**; R2 egress-free veya Neon limitleri genel harcama hard cap'i değildir |
| Offline | **KISMEN DOĞRU**; çekirdek SDK tam sync/conflict motoru olarak belgelenmiyor, üçüncü taraf/özel tasarım gerekir | **KISMEN DOĞRU**; mobil persistence yerleşik, fakat cache kapsamı, LWW ve reconnect billing vardır | **DOĞRULANAMADI**; “kesinlikle manual queue gerekir” yokluk iddiası için resmi capability testi yok | **DOĞRULANAMADI**; `pocketbase_drift` topluluk paketidir, safety-grade reconciliation kanıtı değildir | **DOĞRULANDI (mimari sorumluluk)**; sync kodu/API/yerel store bileşimin sahipliğindedir |
| Güvenlik | **KISMEN DOĞRU**; RLS güçlü defense-in-depth, tek yetki kanıtı değil | **KISMEN DOĞRU**; Rules ve dependent reads gerçek; limit/cost nüansı eksik | **KISMEN DOĞRU**; permissions gerçek, fakat API-key/server bypass ve konfigürasyon sorumluluğu var | **KISMEN DOĞRU**; API rules filter'dır, superuser bunları bypass eder; at-rest encryption garantisi yok | **DOĞRULANAMADI**; API middleware/RLS kalitesi provider fiyat sayfasından çıkmaz |
| Backup/PITR | **KISMEN DOĞRU**; DB yedeği Storage nesnelerini içermez; PITR ücret/compute şartlı | **KISMEN DOĞRU**; export/PITR var, export formatı ve restore/migration işi vardır | **KISMEN DOĞRU**; Cloud ve native PostgreSQL ürünleri ayrılmalı; self-host backup manueldir | **KISMEN DOĞRU**; `pb_data` ZIP/S3 snapshot; PITR iddiası yok | **KISMEN DOĞRU**; Neon history/WAL, R2 object ve API/audit/config backup'ını kapsamaz |
| Bölge ve uyum | **Bölge DOĞRULANDI; uyum iddiası YANLIŞ/YANILTICI** | **Bölge DOĞRULANDI; uyum iddiası çıkarılamaz** | Frankfurt bölgesi **DOĞRULANDI**; hukuki uyum/egemenlik otomatik değildir | VPS seçimi **DOĞRULANDI**; mutlak hukuki egemenlik çıkarılamaz | Neon Frankfurt **DOĞRULANDI**; R2 location/jurisdiction seçimine bağlı |
| Vendor lock-in | **KISMEN DOĞRU**, düşük engine lock-in ≠ tam exit | **KISMEN DOĞRU**, proprietary model migration yükü yaratır; “en yüksek” sıralaması kanıtsız | **DOĞRULANAMADI**; open source/container ≠ sıfır migration lock-in | **YANLIŞ / YANILTICI**; dosya taşınabilirliği lock-in'i sıfırlamaz | **YANLIŞ / YANILTICI**; PG/S3 standartları migration'ı kolaylaştırır, sıfırlamaz |
| Hesap kapanması | **DOĞRULANAMADI**; self-host escape DB ve konfigürasyonun tümünü kapsamaz | **KISMEN DOĞRU risk mekanizması; yüksek risk/fiilî son iddiası kanıtsız** | **DOĞRULANAMADI** | **YANLIŞ / YANILTICI**; VPS hesabı/ödeme/host termination riski sıfır değildir | **DOĞRULANAMADI**; provider terms ve exit drill gerekir |
| Yönetim yükü | Cloud düşük işletim yükü **KISMEN DOĞRU**; API/audit/restore yine tasarlanır | Managed yüzey düşük, data-model/rules/cost izleme yükü bağlama bağlı | Cloud ve self-host ayrılmalı; “sıfıra yakın” mutlak değil | Admin UI mevcut, production ops ve upgrade sorumluluğu sürer | Ayrık bileşimde bileşen/operasyon yükü **BAĞLAMA BAĞLI**, tek başına dealbreaker değil |

## 3. Sağlayıcı bazında iddia denetimi

### 3.1 Supabase

Resmî karşılaştırma kaynakları: [Pricing](https://supabase.com/pricing), [Cost Control / Spend Cap](https://supabase.com/docs/guides/platform/cost-control), [Billing FAQ](https://supabase.com/docs/guides/platform/billing-faq), [Database Backups](https://supabase.com/docs/guides/platform/backups), [Available Regions](https://supabase.com/docs/guides/platform/regions), [RLS](https://supabase.com/docs/guides/database/postgres/row-level-security), [Storage Access Control](https://supabase.com/docs/guides/storage/security/access-control), [Self-Hosting](https://supabase.com/docs/guides/self-hosting).

| Rapor referansı | İddia özeti | Sınıf | Denetim |
|---|---|---|---|
| §Finans, L9; tablo L83-84 | Free: 2 aktif proje, 500 MB DB, 1 GB file, 50K MAU, 5 GB egress; Pro $25; Micro için $10 kredi | **DOĞRULANDI** | Güncel Supabase fiyat sayfası 2 aktif Free proje, 500 MB DB, 1 GB file, 5 GB egress, 50K MAU ve Pro $25/ay ile 8 GB/project, 250 GB egress, 7 günlük günlük backup'ı gösterir. Kullanım günlüğü olarak saklanmalı; vergi/FX ve ek proje/compute ayrıca hesaplanmalıdır. |
| §Finans, L9; tablo L85; dealbreaker L107 | Pro Spend Cap açıksa kota aşımında operasyon durur ve bütçe kesin korunur | **YANLIŞ / YANILTICI** | Spend Cap yalnız `Disk Size`, egress, Edge Function, logs, MAU, Realtime ve Storage gibi listelenen usage item'larını kapsar. Compute, custom domain, extra IOPS/throughput, IPv4 ve PITR kapsam dışıdır. Cap kapatılırsa overage işler; açıkken de genel servis restriction/Fair Use uygulanabilir. “Tüm fatura için hard cap” denemez. |
| §Finans, L9 | Spend Cap varsayılan açık | **DOĞRULANDI (dar kapsam)** | Pro planında varsayılan açık olduğu resmî sayfada yazılıdır; bu, kapsam dışı kalemlerin de capped olduğu anlamına gelmez. |
| §Offline, L25; tablo L87; dealbreaker L110 | Çekirdek Flutter SDK tam çift yönlü, çatışma çözen offline sync sağlamaz; PowerSync/Drift gerekir | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Supabase çekirdek Data API/Flutter belgeleri, Kavriva'nın bounded package + durable reconciliation sözleşmesini hazır bir ürün özelliği olarak kanıtlamaz. PowerSync gibi ticari/harici bir katman veya özel local store/sync olasıdır; “yalnızca HTTP cache” ve her workload'da “şu protokol şart” ifadeleri rapor kaynaklarıyla birincil olarak kanıtlanmıyor. |
| §Güvenlik, L37; tablo L88 | PostgreSQL RLS ve `auth.uid()` satır erişimini korur | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | RLS policy'leri gerçekten DB içinde çalışır ve `auth.uid()` örneği resmîdir. Ancak exposed schema'da RLS/grant yanlışlığı, service/secret key, owner/bypass rolleri, function ve object authorization istisnaları vardır. Supabase kendi rehberinde RLS'yi defense-in-depth olarak anlatır; “hiçbir istemci hiçbir durumda satır okuyamaz” koşulsuz bir sonuç değildir. |
| §Güvenlik, L37; L65; tablo L94 | AI SQL'i iyi anlar, RLS'yi “yüksek tutarlılıkla” üretip doğrular; hata asgaridir | **DOĞRULANAMADI** | Supabase veya PostgreSQL birincil belgeleri model doğruluk oranı vermez. Generated policy, grant, JWT claim, privileged bypass ve negative test birlikte incelenmeden bu güvenlik sonucu çıkarılamaz. AI çıktısı proje kuralı gereği untrusted input'tur. |
| §Güvenlik, L37; tablo L92 | Frankfurt/AWS eu-central-1 seçimi GDPR ve KVKK'ya tam uyumludur | **YANLIŞ / YANILTICI** | Frankfurt `eu-central-1` resmî region olarak mevcuttur. Supabase ayrıca region seçiminin data-location control olduğunu, **regulatory compliance proof olmadığını** açıkça söyler. Supabase security/DPA belgeleri GDPR-related controls ve DPA'yı anlatır; KVKK için veri sorumlusu, aktarım, teknik/idari tedbir, sözleşme ve operasyon yükümlülükleri ayrıca değerlendirilmelidir. Region = full GDPR/KVKK compliance değildir. |
| §DR, L51; tablo L90 | Pro'da 7 günlük günlük yedek; `pg_dump` ile bağımsız PostgreSQL'e taşınır | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Pro günlük DB yedeği ve 7 gün retention doğrudur. Ancak resmî backup dokümanı veritabanı backup'larının Storage API object'lerini **içermediğini** ve silinen object'leri geri getirmediğini söyler. Auth ayarları, Storage, Edge Functions, Realtime, extensions, secrets/config ve protected audit için ayrı export/backup/restore closure gerekir. `pg_dump` portability'yi artırır; “eksiksiz proje” portability'si değildir. |
| §DR, L51; tablo L90; dealbreaker L111 | Supabase PITR $100/aydan başlar | **DOĞRULANDI (planlı kapsam)** | 7 günlük PITR için yaklaşık $100/ay resmi fiyat sayfasında var; PITR için en az Small compute add-on şartı ve retention'a göre $200/$400 seviyeleri de belgelenir. Rakamı tüm restore maliyeti veya tüm workload'ların zorunlu fiyatı gibi kullanmak yanıltıcıdır. |
| §DR, L51; tablo L97; kaynak [48] | Açık kaynak sayesinde Docker Compose ile dakikalar içinde VPS'e dönülür | **YANLIŞ / YANILTICI** | Self-host Docker kurulumu hızlı başlangıç için belgelenmiş olsa da resmî kurulum Linux/Docker/networking bilgisi, en az 4 GB RAM/40 GB SSD (küçük-orta workload varsayımı), TLS, secrets, OS/service patching, backup/DR, HA/scaling, monitoring ve incident sorumluluğunu sahibine verir. Managed backups/PITR ve platform API self-hosted'da yoktur. Platformdan self-host restore rehberi DB'yi taşır; Storage object ve Edge Function redeploy'ını kapsamaz. “Dakikalar içinde tam sistem” kanıtlanmamıştır. |
| §DR, L51; tablo L93 | Standart PostgreSQL olduğu için vendor lock-in çok düşük | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Engine-level lock-in görece düşük olabilir. Auth schema, Storage metadata/object lifecycle, Realtime, Edge Functions, RLS/helper conventions, secrets, region, backup/restore ve audit/config state ayrıdır. Resmî restore-to-self-host sayfası bile Storage/Functions yeniden kurulumunun ayrıca gerektiğini belirtir. “Düşük engine lock-in” ≠ “tam exit”. |
| §Yönetim, L65; tablo L95-96 | Studio mükemmel, SDK stabil, bakım çok düşük | **DOĞRULANAMADI / KISMEN DOĞRU** | Studio ve hosted DB'nin OS bakımını azaltması gözlenebilir mekanizmalardır; “mükemmel”, “stabil”, “AI hata payı asgari” ölçümsüz sıfatlardır. API boundary, authorization, audit, object quarantine, restore drill ve no-owner-debug runbook hâlâ Kavriva kapsamındadır. |

### 3.2 Firebase / Cloud Firestore

Resmî karşılaştırma kaynakları: [Firebase Pricing](https://firebase.google.com/pricing), [Firestore Billing](https://firebase.google.com/docs/firestore/pricing), [Firebase Spend Caps](https://firebase.google.com/docs/projects/billing/spend-caps), [Offline persistence](https://firebase.google.com/docs/firestore/manage-data/enable-offline), [Rules conditions](https://firebase.google.com/docs/firestore/security/rules-conditions), [Export/import](https://firebase.google.com/docs/firestore/manage-data/export-import), [Firestore locations](https://docs.cloud.google.com/firestore/docs/locations), [Google Cloud billing disable behavior](https://docs.cloud.google.com/billing/docs/how-to/modify-project), [Google Cloud terms/suspension](https://cloud.google.com/terms/index).

| Rapor referansı | İddia özeti | Sınıf | Denetim |
|---|---|---|---|
| §Finans, L11; tablo L83-84 | Spark: 50K reads/day, 20K writes/day, 1 GiB, 10 GiB/month; Blaze pay-as-you-go | **DOĞRULANDI** | Firestore'un güncel free quota tablosu 50K document reads/day, 20K writes/day, 20K deletes/day, 1 GiB stored data ve 10 GiB outbound/month verir; tek ücretsiz DB/project şartı vardır. Bu tablo bütün Firebase ürünlerini veya Functions/Storage maliyetini temsil etmez. |
| §Finans, L11; tablo L85; dealbreaker L107 | Blaze'de yerel hard cap yok; budget alert yalnızca e-posta/webhook, operasyonu kesmez | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Firestore kullanımında genel parasal hard cap iddiası hâlâ desteklenmiyor; alerts-only bütçeler hizmeti durdurmaz. Ancak güncel Firebase spend-cap preview, Firebase AI Logic, App Hosting, Cloud Functions ve Extensions gibi seçili hizmetleri kapsayabilir; Firestore'u kapsamaz ve raporlama gecikmesi nedeniyle “hard cap” olarak tanımlanmaz. Raporun “Firebase genelinde hard cap yok” cümlesi artık fazla geniştir; Firestore için “uygulanabilir genel cap yok” denmelidir. |
| §Offline, L23; tablo L87 | SDK otomatik cache/queue ile offline çalışır; reconnect metadata/read maliyetini artırır | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Resmî docs mobilde offline persistence'ın yerleşik olduğunu, cache'lenen aktif verinin okunup yazılabildiğini ve local changes'ın online olduğunda senkronize edildiğini söyler. Aynı belgeler web'de persistence'ın varsayılan kapalı olduğunu, cache'in aktif kullanılan veriyi kapsadığını ve aynı document çatışmasında last-write-wins olduğunu belirtir. Billing docs, offline listener 30 dakikadan uzun koparsa yeni query gibi read/index charge doğabileceğini açıklar; her reconnect'in daima “metadata ve belge maliyeti patlaması” olduğu söylenemez. |
| §Güvenlik, L39; tablo L89; dealbreaker L108 | `get()/exists()` dependent document reads olarak faturalıdır; reddedilen request'te de maliyet vardır | **DOĞRULANDI** | Firebase Rules Conditions ve Firestore pricing bunu doğrudan belirtir. Bu, rule tasarımının cost/security review gerektirdiğini gösterir; tek başına Firestore'un bütün workload'larda elenmesini göstermez. |
| §Güvenlik, L39; tablo L89 | Her istekte en fazla 10 dynamic read vardır | **KISMEN DOĞRU** | Tek document request/operation için 10 access-call limiti vardır; transaction/batched write için operation başına 10'a ek olarak atomic request toplamında 20 limit vardır. Rapor 20 sınırını ve rule evaluation ayrıntısını atlıyor. |
| §Güvenlik, L39; tablo L92 | Frankfurt `europe-west3` desteklenir | **DOĞRULANDI (region)** | Google Cloud Firestore locations sayfası `europe-west3`'ü Frankfurt olarak listeler. `eur3` multi-region ise Belçika/Hollanda/Finlandiya bileşimidir; “Frankfurt” ve “EU multi-region” aynı veri-location iddiası değildir. |
| §Güvenlik, L39 | AI rules yazarken cost multiplier'ları sıkça unutur | **DOĞRULANAMADI** | Raporun kaynakları (Cloudwebschool, Stack Overflow, MakerKit) ürün mekanizmasını veya kişisel deneyimi gösterebilir; AI hata prevalansı/“sıkça” oranı için kontrollü çalışma yoktur. |
| §DR, L53; tablo L90 | GCS export binary formatta; 7 günlük PITR $0.03/GB-ay | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Resmî export docs çıktının **LevelDB log formatı** olduğunu, export'un exact start-time snapshot olmadığını ve export'un document read maliyeti doğurduğunu söyler; “binary” teknik olarak eksik/yanıltıcıdır. PITR en fazla 7 gün ve GB-month üzerinden ücretlidir, ancak tam güncel birim fiyat location/SKU'ya göre resmî storage pricing'den alınmalıdır; rapordaki `$0.03` tüm bölgeler için sabit kanıt değildir. |
| §DR, L53 | Firestore proprietary olduğundan en yüksek lock-in; migration karmaşık | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Doküman/collection/subcollection/rules/index/trigger modelini PostgreSQL'e map etmek ciddi migration çalışması gerektirebilir. Ancak Firestore export/import başka Firestore DB'ye, BigQuery'ye ve Cloud Storage'a desteklenir. “Pazardaki en yüksek” sıralaması veya her hedefe aynı zorluk birincil kanıt değildir. |
| §DR, L53; tablo L97; kaynak [50] | Google algoritmaları hesabı aniden ve insan desteği olmadan askıya alabilir; kilitlenme projenin sonudur | **YANLIŞ / YANILTICI** | Google Cloud şartları abuse, law, unauthorized access veya non-payment gibi hallerde suspension yetkisi tanır; bu, riskin sıfır olmadığına kanıttır. Fakat raporda bu iddiayı taşıyan `[50] https://yippee-bot.com/` ilgisizdir; `[14]` de birincil değildir. Süspansiyon olasılığı, “otomatik/no human support” ve “erişim kaybı fiilen irrecoverable” sonucu kanıtlanmamıştır. Export/Cloud Storage yedeği ve başka proje import'u, **erişim sürerken veya yedek önceden bağımsız tutulmuşsa**, bir çıkış yolu olabilir. Google Cloud'un 30 günlük project-recovery penceresi kullanıcı tarafından başlatılan project shutdown için geçerlidir; suspension için genel kurtarma garantisi değildir. |
| §Yönetim, L67; tablo L95-96 | Firebase yönetimi düşük; ilişkisel raporlama/toplu düzeltme her zaman Function ister | **KISMEN DOĞRU / YANILTICI** | Managed Console işletim sistemi yükünü azaltır. Firestore document modeli ilişkisel raporlamayı zorlaştırabilir; fakat export/BigQuery/Admin APIs/transactional operations gibi yollar vardır. “Her işlem Function ister” mutlaklığı desteklenmiyor. |

### 3.3 Appwrite Cloud ve self-hosted Appwrite

Resmî karşılaştırma kaynakları: [Pricing](https://appwrite.io/pricing), [Manage billing / budget cap](https://appwrite.io/docs/advanced/billing/payments), [Regions](https://appwrite.io/docs/products/network/regions), [Cloud backups](https://appwrite.io/docs/advanced/security/backups), [Managed PostgreSQL](https://appwrite.io/docs/products/databases/postgresql), [self-hosted backups](https://appwrite.io/docs/advanced/self-hosting/production/backups), [self-hosting](https://appwrite.io/docs/advanced/self-hosting), [database permissions](https://appwrite.io/docs/products/databases/permissions).

| Rapor referansı | İddia özeti | Sınıf | Denetim |
|---|---|---|---|
| §Finans, L13; tablo L83-84 | Free 2 proje/75K MAU/2 GB/5 GB/500K read; Pro $25, 200K MAU/150 GB/2 TB; $10 DB credit | **DOĞRULANDI (ürün snapshot'ı)** | Appwrite fiyat sayfasındaki güncel Free/Pro kaynakları büyük ölçüde bu rakamları doğrular. Free/Pro'da proje, database, function, execution, storage ve pay-as-you-go satırları birlikte değerlendirilmelidir; yalnız headline rakamla total cost çıkarılamaz. |
| §Finans, L13; tablo L85 | Budget cap kota aşımında ek masrafı engeller ve service stop yapar | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Appwrite budget cap otomatik add-on ölçeklemesini sınırlar ve beklenmeyen faturayı azaltır; resmî billing docs bunun recurring plan ücretini **kapsamadığını** söyler. “Tüm quota/overage ve tüm service stop garantisi” rapordan çıkmaz. |
| §Offline, L27; tablo L87; dealbreaker L112 | Flutter SDK'da yerel cache yoktur; mutlaka Hive/Isar/Drift + özel queue gerekir | **DOĞRULANAMADI** | Resmî dokümanlarda offline-first/conflict contract'ın yokluğu, tüm Flutter sürümleri için kapsamlı bir capability matrix veya “mutlaka şu paket” şartı gösterilmemiştir. Cihaz yerel store ve queue'nun ürün gereksinimi olabileceği ayrı bir tasarım sonucudur; yokluk iddiası resmi test olmadan kesinleştirilemez. |
| §Güvenlik, L41; tablo L88 | Permission/Role user düzeyinde erişimi sağlar; “mantıksal açık bırakmayan, katı ve güvenli” erişim matrisi | **KISMEN DOĞRU / YANILTICI** | Appwrite permissions table/row/bucket/file seviyesinde grant-based modeldir ve varsayılan boş permission deny eder. Ancak permission konfigürasyonu uygulama doğruluğunun yerine geçmez; Server SDK API key kullanırken permissions ignored olabilir. “Açıklara izin vermez” bir ürün garantisi değildir. |
| §Güvenlik, L41; tablo L92 | Cloud Frankfurt seçilebilir | **DOĞRULANDI (region)** | Frankfurt `FRA` güncel Cloud region listesinde vardır. Region seçimi data residency/latency girdisidir; controller obligations, DPA, transfer, retention veya KVKK/GDPR uyumunu tek başına kanıtlamaz. |
| §DR, L55; tablo L90 | Pro günlük yedek/7 gün; dedicated DB PITR +%20 | **KISMEN DOĞRU / ÜRÜN-SCOPE BAĞIMLI** | Pro fiyatı daily backup/7-day retention gösterir. Native managed PostgreSQL dokümanı tier fiyatının %20'si PITR add-on ve 1–35 gün window bilgisini verir. Bu, Appwrite TablesDB/DocumentDB, Cloud platform backup ve self-hosted backup davranışlarının aynı şey olduğu anlamına gelmez; rapor ürünleri karıştırıyor. |
| §DR, L55 | Appwrite verileri açık şema ve self-hosted ile %100 uyumludur; CLI JSON ile tüm altyapı taşınır | **YANLIŞ / YANILTICI** | Appwrite self-hosted open source ve Cloud ile aynı ürün ailesidir; fakat self-hosted backup prosedürü manueldir, update/migration/scaling operatöre aittir. Native PostgreSQL, TablesDB/DocumentDB, Storage, Functions, secrets, policy/audit/config ve region/account state için clean-room export/import kanıtı gerekir. “%100 uyumluluk” veya “tüm altyapı JSON” birincil kaynakla gösterilmemiştir. |
| §Yönetim, L69; tablo L96 | Cloud bakım yükü sıfıra yakın; self-host orta | **KISMEN DOĞRU / YANILTICI** | Cloud managed olması OS/container yükünü azaltır. Self-host dokümanı manual setup, updates, scaling, TLS, rate limits, monitoring ve regular backup sorumluluğunu açıkça listeler. Cloud'da da API/policy/audit/restore/exit yükü sıfır değildir. |
| tablo L97 | Hesap kapanma riski düşük, self-host yedeğe dönülebilir | **DOĞRULANAMADI** | Bir olasılık/ölçek iddiası için incident/terms/support/exit drill kanıtı yoktur. Self-host backup bulunduğu anlamına “Cloud hesabı kapanınca tüm hizmet ve state otomatik hazır” anlamı yüklenemez. |

### 3.4 PocketBase self-hosted

Resmî karşılaştırma kaynakları: [PocketBase docs](https://pocketbase.io/docs/), [Going to production](https://pocketbase.io/docs/going-to-production/), [API rules and filters](https://pocketbase.io/docs/api-rules-and-filters/), [Backup API](https://pocketbase.io/docs/api-backups/), [How to use / Flutter persistence](https://pocketbase.io/docs/how-to-use/).

| Rapor referansı | İddia özeti | Sınıf | Denetim |
|---|---|---|---|
| §Finans, L15; tablo L83-84 | Open-source single binary; SaaS kullanım faturası yok; VPS €3–6/ay; hiçbir zaman overage yok | **KISMEN DOĞRU / DOĞRULANAMADI** | PocketBase yazılımı SaaS planı olmadan self-host edilir ve host edilen binary/SQLite yaklaşımı gerçektir. Ancak €3–6 rakamı PocketBase resmi fiyatı değildir; VPS provider, disk/snapshot/egress/backup, ödeme ve kaynak yükseltme maliyetleri değişir. PocketBase uygulama faturası üretmese de “mutlak sabit maliyet/sıfır aşım” tüm host sözleşmelerine genellenemez. |
| §Offline, L29; tablo L87 | `pocketbase_drift` ile cache-and-network ve background sync yalın biçimde çözülür | **DOĞRULANAMADI** | Paket topluluk/üçüncü taraf niteliğindedir; PocketBase çekirdek docs safety-grade conflict resolution, idempotency, reconnect, revoke/recall veya reconciliation garantisi vermez. Package varlığı, Kavriva offline contract'ının kanıtı değildir. |
| §Güvenlik, L43; tablo L88 | API rules SQLite WHERE koşuluna dönüşür | **DOĞRULANDI (mekanizma)** | PocketBase docs API Rules'ın access control ve record filter olduğunu, `@request.auth.id` benzeri filtreleri ve locked/superuser istisnasını açıklar. Bu nedenle rule audit, superuser/backup key koruması ve negative tests gerekir; “kural yazıldı = güvenlik tamam” denemez. |
| §Güvenlik, L43 | Hassas veri local DB'de şifrelenir; VPS ülkesini seçince veri egemenliği ve hukuki kontrol mutlak kurucudadır | **YANLIŞ / YANILTICI** | Resmî production docs `pb_data` ayarlarının varsayılan olarak plain JSON saklanabildiğini, settings encryption'ın ayrıca açılabildiğini ve dosya/backup/server erişim modelini anlatır; uygulama verisinin tümü için otomatik at-rest encryption garantisi yoktur. VPS lokasyonu, host sağlayıcısının erişim/terms/jurisdiction'ını veya KVKK/GDPR yükümlülüklerini yok etmez. |
| §DR, L57; tablo L90 | `data.db` tek dosya; panelden ZIP/S3 snapshot; PITR yok | **KISMEN DOĞRU** | Resmî docs backup'ın çalışan uygulama durdurularak `pb_data` dizini üzerinden alınmasını, full ZIP snapshot'ın uploaded files'ı da kapsadığını ve local/S3 backup desteklediğini söyler. Güncel docs `pb_data` içinde `data.db` yanında auxiliary metadata ve dosyalar bulunduğunu belirtir; “tüm sistem yalnız data.db” eksiktir. Resmî belgelerde PostgreSQL-style PITR yok; snapshot backup'ı PITR yerine koymamak gerekir. |
| §DR, L57; tablo L93 | Satıcı bağımlılığı tamamen sıfır; ZIP/binary kopyası anında başka host'ta çalışır | **YANLIŞ / YANILTICI** | SQLite/ZIP taşınabilirliği migration maliyetini azaltır; fakat PocketBase version/migration, hooks, auth token/permission semantics, file backend, S3 credentials, reverse proxy/TLS, host OS ve restore ordering'e bağımlılık vardır. Resmî docs PocketBase'i production-critical için changelog ve manual migration takibi olmadan önermediğini söyler. “Sıfır lock-in” veya “anında” kanıtlanmamıştır. |
| §Yönetim, L71; tablo L95-96 | Admin UI mükemmel; temel Linux/DNS/servis yükü var | **KISMEN DOĞRU** | Dahili dashboard/collection yönetimi ve tek binary operasyonu vardır; Linux, TLS/reverse proxy, process supervision, update/migration, backup/monitoring ve incident sorumluluğu yine kurucudadır. “Mükemmel” ölçümsüzdür. |
| tablo L97; §Karar, L125 | Müstakil VPS nedeniyle hesap kapanma riski sıfır; bütçe değişkenliği tamamen yok | **YANLIŞ / YANILTICI** | VPS hesabı, ödeme, abuse/terms, DNS, object storage ve host provider failure domain'leri devam eder. PocketBase'in kendi hesabı olmaması host/provider hesabı riskini sıfırlamaz. |

### 3.5 Neon + bağımsız API + Cloudflare R2

Resmî karşılaştırma kaynakları: [Neon Pricing](https://neon.com/pricing), [Neon usage-based pricing](https://neon.com/blog/new-usage-based-pricing), [Neon regional latency/regions](https://neon.com/demos/regional-latency), [Cloudflare R2 Pricing](https://developers.cloudflare.com/r2/pricing/), [R2 Data Location](https://developers.cloudflare.com/r2/reference/data-location/), [R2 Data Security](https://developers.cloudflare.com/r2/reference/data-security/).

| Rapor referansı | İddia özeti | Sınıf | Denetim |
|---|---|---|---|
| §Finans, L17; tablo L83-84 | Neon Free 0.5 GB + 100 CU-hour; Launch $0.106/CU-hour + $0.35/GB-month; scale-to-zero | **DOĞRULANDI (güncel snapshot)** | Güncel Neon pricing sayfası 0.5 GB/project, 100 CU-hour/project, Free'de 100 project, Launch $0.106/CU-hour ve $0.35/GB-month değerlerini gösterir; idle compute scale-to-zero'dur. Free quota proje başına ve paid plan usage sıfırdan metered olur; rapor bunları ve plan geçişindeki maliyet farkını eksik anlatıyor. |
| §Finans, L17 | API katmanı $5/ay ile toplam kontrol altında | **DOĞRULANAMADI** | API runtime/provider, logs, egress, secrets, monitoring, background worker, incident support ve domain maliyetleri verilmeden `$5` veya `$5–15` hesabı karşılaştırılabilir kanıt değildir. Bu bileşimde API zorunlu boundary'dir; maliyeti “küçük VPS” varsayımıyla gizleyemez. |
| §DR, L59; tablo L90 | Neon 7 günlük PITR $0.20/GB-ay | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Current Neon pricing'te Launch instant-restore history window up to 7 days ve `$0.20/GB-month` data-change history vardır; Scale 30 güne kadar çıkabilir, Free pencere/byte sınırları farklıdır. Bu WAL history bir database-plane özelliğidir; API, object, audit, identity, policy, config, package manifest ve non-restorable negative floor backup'ı değildir. |
| §DR, L59; tablo L93 | Standart SQL dump ve S3 API ile vendor lock-in sıfır | **YANLIŞ / YANILTICI** | PostgreSQL wire protocol ve S3-compatible API exit maliyetini azaltır. Neon branching/history, connection/pooling, provider IAM; R2 metadata, lifecycle, jurisdiction, access token; API code, audit ve cross-plane contracts yine migration/clean-room import gerektirir. “Sıfır” iddiası için restore/exit drill yoktur. |
| §Finans, L17; tablo L85/L91; §Karar L127 | R2 10 GB ücretsiz ve egress $0; bu bütçeyi korur | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | R2 Standard için 10 GB-month, Class A/B operation kotaları ve doğrudan R2 egress'inin ücretsiz olduğu resmîdir. Storage, Class A/B operations, Infrequent Access retrieval, Workers/API/origin gibi bağlı hizmetler yine ücret doğurabilir. “$0 egress = hard cap/zero bill” yanlıştır. |
| §Güvenlik/DR, tablo L92 | Neon Frankfurt + R2 küresel Anycast bölge modelidir | **KISMEN DOĞRU / YANILTICI** | Neon Frankfurt endpoint'i vardır. R2'de default `Automatic` location closest-available-region için seçimdir; Location Hint best-effort'tur. EU data residency gerekiyorsa bucket oluşturulurken `eu` jurisdiction seçilmelidir; global Anycast/egress-free ifade, object storage residency ve processing'i tek başına açıklamaz. |
| tablo L97 | Hesap kapanma riski düşük, DB taşınabilir | **DOĞRULANAMADI** | Taşınabilir Postgres exit evidence sağlar, risk olasılığı veya account continuity garantisi sağlamaz. Neon, API host ve Cloudflare hesap/terms/billing failure domain'leri için F10/F12 senaryoları ve clean-room drill gerekir. |
| §Yönetim L73; tablo L95-96 | Birleşik admin panel yok; üç sistemin orkestrasyonu çok yüksek efor | **KISMEN DOĞRU / BAĞLAMA BAĞLI** | Bileşenlerin kendi console'ları ayrı olabilir; bu solo owner için gerçek operating-model riski yaratır. Ancak approved fixture, browser-based Internal Operations panelinin zaten sistem boundary'si olduğunu söyler; “hazır panel yok = aday otomatik elenir” değil, owner-readable runbook, API-mediated authority, observability ve no-owner-debug kanıtı ölçütüdür. |

## 4. Çapraz iddia denetimi

### 4.1 Hard cap, budget alert ve “sıfır fatura” aynı şey değildir

Rapor, üç farklı kontrolü tek bir `Harcama Koruması` hücresinde birleştiriyor:

1. Ücretsiz plan quota aşımında servisin kısıtlanması (ör. Free Supabase/Firestore).
2. Belirli usage item'larında overage'ı durduran provider cap (Supabase Spend Cap,
   Appwrite add-on budget cap).
3. Genel aylık parasal hard cap veya billing'i kapatan otomasyon.

Bunlar eşdeğer değildir. Supabase Spend Cap kapsam dışı kalemler içerir; Appwrite cap
recurring plan bedelini içermez; Firebase alerts-only bütçe servisi durdurmaz, spend-cap
preview ise seçili Firebase hizmetleriyle sınırlıdır ve gecikmeli enforcement'a sahiptir;
Neon usage-based paid plan ve R2 egress-free olmasına rağmen storage/compute/operations
faturası üretebilir. Kavriva için kabul edilebilir kanıt, her P0–P3 horizon ve incident
month için item-by-item cap/overage/degraded/held davranışıdır; tek bir “hard cap var/yok”
etiketi değildir.

### 4.2 “Frankfurt = GDPR/KVKK” sonucu çıkarılamaz

Supabase, Appwrite ve Firestore için Frankfurt/europe-west3 region seçimi gerçek bir
deployment/data-location seçeneğidir. Ancak:

- Supabase kendi region docs'unda location seçiminin regulatory compliance proof olmadığını
  açıkça söyler.
- Google Cloud/Firestore'da regional ve multi-region seçeneklerinin data replication ve
  location semantiği farklıdır.
- Appwrite region docs, hukuki gerekliliklerin ayrıca değerlendirilmesini ister.
- Cloudflare R2'de location hint garanti değildir; jurisdiction restriction ayrı seçilir.
- KVKK'nın resmi guidance'ı veri sorumlusuna teknik/idari güvenlik tedbirleri ve yurt dışına
  aktarım için uygun güvence/sözleşme/bildirim yükümlülükleri yükler.

Bu nedenle raporun Supabase için “tam GDPR ve KVKK uyumu”, PocketBase için “hukuki denetim
mutlak kurucunun elinde”, diğerleri için bölge satırından uyum sonucu üretmesi
**YANLIŞ/YANILTICI**dır. Ürün, veri kategorisi, controller/processor rolü, DPA/SCC/standart
sözleşme, alt işleyenler, retention/deletion, DSAR ve incident süreçleri ayrı kanıtlanır.

Resmî KVKK referansları: [Veri güvenliği yükümlülükleri](https://www.kvkk.gov.tr/Icerik/2040/Veri-Guvenligine-Iliskin-Yukumlulukler),
[yurt dışına aktarım](https://www.kvkk.gov.tr/Icerik/2053/Yurtdisina-Aktarim) ve
[standart sözleşmeler](https://www.kvkk.gov.tr/Icerik/7929/Standart-Sozlesmeler).

### 4.3 AI'nin RLS/rule yazması güvenlik kanıtı değildir

Raporun Supabase için “AI SQL'i çok iyi anlar / RLS'yi yüksek tutarlılıkla doğrular” ve
Firebase için “AI dependent-read maliyetlerini sıklıkla unutur” iddiaları aynı sorunu iki
taraftan taşıyor: kontrollü ölçüm yerine model hakkında genelleme. RLS/Rules doğruluğu;
policy semantics, grant, JWT/session claims, service/admin bypass, object/function access,
race/conflict, tenant isolation ve adversarial negative test ile gösterilir. AI yazmış
olması da AI yazmadığı anlamına gelmesi de güvenlik metriği değildir. Bu iddialar
**DOĞRULANAMADI**dır ve yüksek sonuçlu karar kanıtı olamaz.

### 4.4 Backup yalnız veritabanı backup'ı değildir

Supabase resmî docs'unda database backup'ın Storage API object'lerini kapsamadığı açıkça
belirtilir. Firestore export exact snapshot değildir ve LevelDB log formatındadır. Appwrite
Cloud backup, Appwrite self-host manual backup ve native PostgreSQL PITR farklı ürün
yüzeyleridir. PocketBase ZIP `pb_data` snapshot'ıdır. Neon instant restore WAL history'sidir;
R2 object'leri, API image/build/config, identity/policy, protected audit, package manifest
ve negative floor ayrı kalır.

Dolayısıyla raporun “DB taşınır, sistem taşınır” veya “docker/ZIP ile hesap kapanmasına
dönülür” cümleleri cross-plane restore, anti-resurrection floor, object/audit/config
manifest ve clean-room import olmadan **KISMEN DOĞRU** bile sayılamaz; en iyi ihtimalle
database-plane portability hipotezidir.

### 4.5 Vendor lock-in ve hesap kapanması sıfırlanamaz

Lock-in en az şu katmanlarda ölçülmelidir: canonical data/schema, identity/session,
authorization policy, object metadata/files, functions/workers, realtime/events,
protected audit, backups/keys/config, region/legal terms, observability ve migration
tooling. Standard PostgreSQL/S3 yalnızca bazı katmanların taşıma maliyetini azaltır.

“Hesap kapanma riski” de provider hesabı, billing account, abuse/terms, region, DNS,
SMTP/notification, object storage ve API runtime failure domain'lerinin bileşimidir. Bir
VPS hesabı kendi başına kapanmayabilir; host, ödeme, abuse veya disk sağlayıcısı kapanabilir.
Google Cloud şartlarının suspension olanağını tanıması da kapanma olasılığı veya
irrecoverability kanıtı değildir. Mutlak `sıfır` ve `en yüksek` etiketleri **kanıtsız**dır.

## 5. `DEC-0034` ve common fixture ile çelişkiler

### 5.1 `DEC-0034` sınırları

`00_CONTROL/SOURCE_OF_TRUTH.md:209-212` provider-neutral yönü açıkça onaylar: canonical
authority per domain; server/API-mediated sensitive access; online-authoritative Internal
Operations; bounded closed mobile packages; durable reconciliation; current/history/
protected-audit ve object/media ayrımı; cross-plane anti-resurrection recovery/exit.
Aynı karar hiçbir engine, PostgreSQL/provider, BaaS, paid plan veya physical architecture
seçmez.

Dış raporla görülen çatışmalar:

| Onaylı sınır | Dış raporun çatışan varsayımı/sonucu | Hüküm |
|---|---|---|
| Hassas erişim server/API boundary'sinden geçer; RLS/IAM/storage defense layer'dır. | Supabase güvenliği doğrudan client + RLS olarak sunulur; RLS tek başına güvenlik sonucu gibi yazılır. | **REDDİ** — RLS defense-in-depth olmalıdır; yüksek sonuçlu mutation direct client'a bırakılamaz. |
| Internal Operations approve/publish/recall/role/policy/protected-audit işlemlerinde online-authoritative'dir. | Offline queue/local DB ve provider SDK kolaylığı genel offline çözüm gibi sunulur. | **REDDİ** — local pending olabilir; accepted/authoritative/unknown/reconciled ayrımı zorunlu. |
| Mobile offline package seçili motorcycle/task scoped; compact safety/application/recovery closure; heavy media optional. | “Offline için local DB ve delta sync zorunlu”, cache/sync motoru adayın ana avantajı gibi kıyaslanır; full database semantics ima edilir. | **KARANTİNA** — local store aday mekanizmadır; bounded package completeness, freshness/recall ve safe recovery asıl ölçüttür. |
| Current, history/evidence, publication control, files/media, phone package ve convenience projections ayrıdır. | Tek DB backup'ı veya tek `data.db`/ZIP'i tüm sistem truth'u gibi ele alınır. | **REDDİ** — cross-plane manifest, object/audit/config/identity/key backup ve restore quarantine gerekir. |
| Restore sonrası negative/deletion/accepted-operation floor ile anti-resurrection gerekir. | PITR/snapshot/DB dump “kurtarma” olarak yazılır; recall, revoke, delete ve accepted operation floor yoktur. | **REDDİ** — database recovery ürün truth recovery değildir. |
| Provider/account/billing failure ve bounded AI operations senaryoya dahil. | “Hesap riski düşük/sıfır”, “AI SDK'yi eksiksiz anlar”, “hard cap var” gibi puan/etiketler verilir. | **REDDİ** — F02/F10/F12/F13/F14/F15/F16 kanıtı yoksa karar verilemez. |

### 5.2 `DEBATE-008__FINALIST_COMMON_FIXTURE.md` ile karşılaştırma

`04_TECH_STRATEGY/DEBATES/DEBATE-008__FINALIST_COMMON_FIXTURE.md:8-18` iki bileşimi eşit
koşullarda karşılaştırır: Candidate A Supabase-managed composition olsa bile yüksek
sonuçlu mutation'lar approved API boundary arkasındadır ve RLS sole authority değildir;
Candidate B Neon + independent API + R2 yalnızca current representative components'tir.
İkisi de identity, protected audit, quarantine/scanning, monitoring, notification, backup,
export ve emergency negative authority eklerini göstermelidir. Dış rapor bu şartları
sağlamadan BaaS/direct-client kolaylığı üzerinden sonuç üretir.

`...FINALIST_COMMON_FIXTURE.md:49-74` eşit workload/cost horizon ister:

- P0 = 0, P1 = 100, P2 = 10,000, P3 = 50,000 active-user fixture;
- 12 MB compact transfer, optional media up to 150 MB, 25 MB cellular confirmation,
  250 MB content cache (comparison values, final product limits değil);
- planning/free, safe closed test, Android production, iOS addition, P2/P3 pressure,
  restore drill, provider-exit drill ve incident month;
- her cost kalemi `mandatory now/later`, `deferrable`, `optional`, `scale-triggered` veya
  `contingency`; bilinmeyen `UNRESOLVED`.

Dış rapor bu fixture ile aynı scenario/cost sheet'i kullanmıyor. Free tier headline'ları,
tek bir aylık estimate ve genel “$3–6/$5–15” aralıkları; P0–P3, 12/150/25/250 MB,
restore/exit/incident workload ve unknown/cap/held davranışının yerine geçemez.

`...FINALIST_COMMON_FIXTURE.md:96-115` F01–F16 failure seti de kapsanmıyor: stale browser
role, leaked key, lost response, object/audit partial failure, publish/recall race, wrong
offline base, provenance conflict, old backup resurrection, cross-plane mismatch, provider
suspension, region outage, clean-room exit, least-privilege AI task, half-failed AI operation,
quota incident ve provider behavior drift. Bu boşluklar “yönetim yükü” puanı veya account-risk
etiketiyle telafi edilemez.

## 6. Kaynak kalitesi denetimi

Raporun bibliyografyasındaki aşağıdaki kaynaklar fikir keşfi için kullanılabilir; belirtilen
iddialar için birincil kanıt değildir:

| Rapor kaynağı | Sorun | Kullanılabilecek dar kapsam |
|---|---|---|
| `[50] https://yippee-bot.com/` | Firebase/Google Cloud hesabı, billing veya suspension ile ilgisiz; açıkça alakasız. | Hiçbir hesap-kapanması sonucu için kullanılamaz. |
| `[14] https://checkthat.ai/brands/firebase/pricing` | Vendor/ürün şartı veya incident istatistiği için birincil Google kaynağı değil. | En fazla keşif; suspension olasılığı kanıtı değil. |
| `[1]-[2], [4]-[8], [10], [12]-[13], [15], [18], [23], [27], [29]-[31], [41]-[44], [47]-[49], [57]` | Blog, aggregator, vendor-adjacent, Stack Overflow, Reddit, Medium, host satış sayfası veya wiki. | Belirti/hipotez keşfi; fiyat, hukuk, güvenlik oranı, hard cap ve categorical rejection için değil. |
| `[32]-[34]` PowerSync | Ürünün kendi offline çözümünü anlatır; Supabase çekirdek capability'si veya Kavriva readiness'i için bağımsız kanıt değildir. | PowerSync'in ne sunduğunu anlamak. |
| `[40]` `pocketbase_drift` ve `[55]` Mintlify mirror | Topluluk/ayna dokümantasyonu; core PocketBase desteği ve recovery/conflict garantisi değil. | Paket/backup API keşfi; safety-grade sync veya exit kanıtı değil. |
| `[3], [9], [11], [17], [19], [24]-[26], [28], [46], [53], [56]` | Birincil/resmî sayfalar olsa da yalnız ilgili mekanizma, plan veya ürün davranışını doğrular. | Dated product fact; legal compliance, total TCO, migration success veya provider risk sıralaması değil. |

Resmî belgeler de kendiliğinden “güvenli seçim” anlamına gelmez. Fiyat ve limitler zamanla
değişebilir; terms, DPA, subprocessor, retention, deletion ve support koşulları ayrıca
okunmalıdır. Resmî mekanizma + aynı fixture üzerinde restore/exit/negative test kanıtı,
karar için gereken minimum pakettir.

## 7. Karar ve güvenli taşıma sınırı

### KABUL — yalnız mekanizma/guardrail olarak

- Firestore mobile offline persistence'in gerçek bir SDK capability'si olduğu; bunun
  cache scope, LWW, freshness/recall ve listener billing sınırlarıyla birlikte ele alınması.
- Supabase RLS, Firebase Rules, Appwrite permissions ve PocketBase API Rules'ın gerçek
  authorization mekanizmaları olduğu; hiçbirinin Kavriva high-consequence server/API
  authority'sinin otomatik yerine geçmemesi.
- Supabase Pro günlük DB backup/PITR seçenekleri, Appwrite Cloud/native PG backup/PITR,
  PocketBase ZIP/S3 snapshot, Neon instant-restore history ve R2 object storage'ın ayrı
  plane'ler olduğu.
- Supabase Spend Cap, Appwrite budget cap, Firebase quota/budget, Neon usage metering ve
  R2 egress semantics'in her usage item için ayrı maliyet kanıtı olarak incelenmesi.
- Frankfurt region, Neon Frankfurt ve R2 jurisdiction gibi seçeneklerin latency/data
  location girdileri olduğu; bunların tam GDPR/KVKK uyum kanıtı olmadığı.

### KARANTİNA — eşit dossier/evidence tamamlanana kadar

- Her sağlayıcının güncel fiyat/limit/cap snapshot'ı ve P0–P3 + incident month TCO'su.
- Offline package builder, release/client compatibility, stale/recall, conflict, retry,
  idempotency, outcome-unknown ve reconciliation davranışı.
- API-mediated authorization, privileged bypass, object/media quarantine, protected audit,
  identity/session recovery ve no-owner-debug operating model.
- Database + object + audit + identity/policy/config/package backup/restore; restore
  quarantine; negative/deletion/accepted-operation floor; clean-room import/cutover.
- Dated region/subprocessor/DPA/KVKK transfer, deletion/retention ve account/billing
  suspension terms; actual provider support/appeal path.

### REDDİ — bu dış rapordan proje kararı olarak alınamaz

- “Supabase Pro en dengeli/en rasyonel”, “PocketBase en yalın”, “Firebase doğrudan elenir”
  veya herhangi bir aggregate winner/dealbreaker sonucu.
- “Hard cap kesin bütçeyi korur”, “R2 egress $0 olduğundan sıfır aşım”, “VPS ile sıfır
  hesap kapanma”, “vendor lock-in sıfır”, “tam GDPR/KVKK uyumu”.
- “Dakikalar içinde tam Supabase self-host/restore”, “tek ZIP/data.db ile sistem anında
  taşınır”, “Neon + S3 ile tam exit”.
- “AI RLS/rules'i yüksek tutarlılıkla yazar/doğrular” veya AI kaynaklı güvenlik/cost
  yüzdeleri ve olasılıkları.
- Dış raporun direct-client/RLS-only, full-local-first veya generic offline-sync
  varsayımını `DEC-0034` authority modeline dönüştürmek.

Bu audit hiçbir provider, plan, engine, API runtime, offline library, region, paid service,
ADR veya code/build/release readiness seçmez. Sonraki tartışmanın ölçülebilir girdisi,
provider-neutral `DEC-0034` sınırları ve aynı `DEBATE-008` fixture'ıdır.
