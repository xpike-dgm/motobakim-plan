# ADR-016 — Yönetim çalışma alanı istemcisi için sınırlı seçim önerisi

Status: PROPOSED
Date: 2026-10-18
Owners: Kavriva yöneticisi (öneri); görev sonu bağımsız inceleme bekleniyor
Task: T-E2-001 / C2.1 / F2.1.1 / FL2.1.1

## Bağlam ve kararın durumu

ADR-010 dört aile için eşit kanıt olmadan kazanan seçilmesini yasaklar. Kendi yeniden değerlendirme maddesi, gerçek uygulama denemesiyle bir ardıl karar hazırlanmasını açar. Bu belge o öneridir; APPROVED değildir ve ADR-010un hiçbir hükmünü henüz değiştirmez. Geliştirme yetkisi DEC-0067, tek görev PRı ve görev sonunda inceleme DEC-0068 kapsamındadır. Sahibin sürekli devam talimatı rutin yeniden izin döngüsünü kaldırır; yapılmamış inceleme, yeşil CI veya ürün kabulü yaratmaz.

Uygulamanın kabul edilmiş tabanı PR126 / `972622acb2a9e3ea2f6b696a2b368bfeb11fba70`. Dört adayın tam karşılaştırma başlığı `bc057850192d8f27e9f22e22bfd87ac9542c5edd`; dokuz iş akışı başarılı. Ayrı kapalı ürün kabuğu `35525c004508f7a6cf1dfab5225a46c3298fb586` yerel sekiz tarayıcı testini geçti, ancak kendi Linux okuyucu kurulumu CI39086356023te başarısız oldu. Onarım başlığı `2564b06bbf9f46803d8d1eb81b654125d65eb411` / CI39126947518 ürün okuyucusu dahil dokuz iş akışıyla başarılı.13 konuşma/ses dosyası,22 alt komut ve46 kaynak özeti gerçek baytlarıyla doğrulandı. Anguların ilk/eski tur konuşmasındaki birleşik240/0 caption açık gözlem olarak ayrıldı; neden/etki henüz çözülmedi. İlk hata korunur; CI başarısı kusursuzluk veya bağımsız kabul değildir.

## Önerilen karar

Yalnız E2 masaüstü yönetim çalışma alanının istemci kabuğu için React19.3.1 / ReactDOM19.3.1 + TypeScript6.0.3 + Vite8.3.4 ve React eklentisi6.1.2 statik bileşimini öner. Tam paketler ve kilitler uygulama deposundadır; üretim tedarik ve bağımlılık incelemesi bu sürüm etiketlerinden çıkarılmaz. Bu karar sürümleri süresiz dondurmaz; yükseltme de normal PR, eşleşen kilit ve gerileme kanıtı gerektirir.

Bu öneri kabul edilirse ADR-010un yalnız Decision4 içindeki gelecekte yapılacak çatı seçimi boşluğu ve buna bağlı “hiçbir framework seçilmedi” sınırı E2 kabuğu kapsamında kısmen ardıllanır. Decision1 masaüstü tarayıcı, Decision2 koşullu statik+API, Decision3 ürün yetkisi ve Decision5 tasarım/AI tutarlılığı aynen korunur. Diğer ekranlar mevcut sözleşme ve kendi kabul kanıtlarıyla ilerler. Yeni BFF, SSR, edge, sunucu, servis çalışanı, bileşen kütüphanesi, host, CDN, alan adı, hesap, ücretli hizmet veya dağıtım seçilmez.

## Seçenekler ve ödünleşimler

Aynı dondurulmuş 240 kayıt/20 sayfa örneği, model, stil, yirmi ilk okuma sorusu ve gerçek tarayıcı senaryoları dört yerel bileşende sınandı. Aşağıdaki yerel R3 ölçümleri performans veya üretim fiyatı değildir: kilit paket sayısı ile derleme klasöründeki bütün dosyaların baytları; gzip her dosyanın ayrı sıkıştırılmasının toplamıdır.

| Aile | Güncel kilit paketi | Statik bayt / ayrı gzip toplamı | Destek ve bakım farkı |
|---|---:|---:|---|
| React | 48 | 232033 / 72588 | En küçük bağımlılık ağacı; tarihli LTS garantisi doğrulanmadı. Vite/TS ayrıca izlenir. |
| Angular | 347 | 124303 / 42417 | v22 yıllık major ve tipik24ay destek; LTS sonu yaklaşık Haziran2028. Core/CLI/TS uyumu birlikte korunur. |
| Nuxt | 712 | 163615 / 63760 | v4 kararlı; destek v5 yayımlandıktan6ay sonra biter. Mevcut kilitte11 yüksek bağlı bulgu / iki kök açık. |
| SvelteKit | 80 | 100635 / 39822 | En küçük çıktı; Kit3 config/adapter geçişi ve announcer sabit CSP stil hashinin bakımı gerekiyor. Tarihli LTS doğrulanmadı. |

React önerisinin gerekçesi aynı işlevi daha küçük bağımlılık ağacı ve özel framework sunucusu/adapteri gerektirmeyen doğrudan bileşen sınırıyla karşılamasıdır. En küçük çıktıyı verdiği, en uzun destek garantisinin olduğu veya çoklu AI üretimini kendiliğinden güvenli yaptığı iddia edilmez. Anguların daha açık destek takvimi ve SvelteKitin daha küçük çıktısı gerçek avantajlardır. Nuxtun açıkları başka adayı otomatik kazandırmaz. Dört adayda lisans alanı eksikliği sıfır; bu hukuki onay değildir. React/Angular/SvelteKit güncel yerel audit sonucu sıfır bulgudur; açık bulunmadığına dair sürekli garanti değildir.

Resmi kaynaklar: [React sürüm politikası](https://react.dev/community/versioning-policy), [Angular destek tablosu](https://angular.dev/reference/releases), [Nuxt yol haritası](https://nuxt.com/docs/4.x/community/roadmap/), [SvelteKit3 göçü](https://svelte.dev/docs/kit/migrating-to-sveltekit-3). Okuma tarihi18Ekim2026. Nuxt5 için Q4 2026 tahmini yayımlanma kanıtı değildir; Nuxt3ün31Temmuz2026 destek sonu yalnız göç girdisinin riskidir.

## Kanıt matrisi ve gerçek sınırlar

Uygulama `vault/PACKS/P-E2-001.md`, `vault/PROFILES/workspace-framework-gate.md`, `vault/PROFILES/workspace-shell.md` ve `vault/EVIDENCE/E-DEV-125.md` tam yolları, sürümleri, olumsuzları ve önceki başarısızlıkları taşır.

| Boyut | Gerçek kanıt | Bu kanıttan çıkarılmayan sonuç |
|---|---|---|
| Eşit iş yükü | Dört native bileşen; aynı liste/ayrıntı/fark/metin eşli grafik/taslak;76 tarayıcı ve10 HTTP kontrolü | Gerçek ürün kuyruğu, yayın veya rol yönetimi tamamlanmış değildir. |
| Erişilebilirlik | bc05785te gerçek klavye/axe/zoom ve Linux Orca/AT-SPI; iki major dahil12 konuşma ve12 sessiz olmayan WAV | İnsan telaffuz/kullanılabilirlik onayı değildir; yeni ürünün okuyucusu ayrıca gerekir. |
| Oturum ve etki | Aynı loopback fixture içinde epoch/CSRF/özel kapsam/kaynak sürümü/audit/yanıt kaybı ve aynı kimlikle sonuç sorgusu | Üretim E3/E5 bağlantısının kanıtı değildir. |
| Dosya güvenliği | Aynı özel karantina, digest, kapalı aktif önizleme ve arşiv geri dönüş olumsuzları | Üretim dosya servisi veya yayın onayı değildir. |
| Major ve dönüş | Eski/güncel fazlar;22 alt komut exit0;46 kaynak özeti;16 native eşlik; dört eski artifact geri dönüşü | Kit2→3, Svelte4→5 değildir. Eski Nuxt3 veya açık eski sürümlere ürün kurulmaz. |
| Temiz oda | Güncel sürüm ilk temiz CI checkout ve beş tam kilit; güncel helper fazı önceki çalışma dizininde gerçek yükseltme | Yükseltme fazı tamamen boş kurulum diye yazılmaz. |
| Yetkinin dirilmemesi | API uyumsuzluğu/iptal birlikte kapalı; sonra uyumlu APIde eski epoch403, yazım/audit sıfır | İlk birleşik olumsuz tek başına yalnız API mismatch nedenini ayırmaz. |
| AI ve tasarım | Sabit brief/yol sahipliği; dört gerçek kaynakta iki ayrı sentetik öneriye gerçek Git çakışması; doğal PNG okuma ve byte eşlikleri | İki bağımsız AI implementasyonu veya otomatik dosya kilidi çalıştırılmış değildir. Görev sonu ayrı inceleme beklenir. |
| Ürün kabuğu | Ayrı paket/kilit/static sunucu; örnek model/kimlik ithali yok; yerel8 browser/klavye/axe/gerçek zoom | Üretim operatörü girişi veya gerçek kayıt incelemesi değildir. 2564b06 ürün8 browser/zoom/Orca CI başarılı; bağımsız kabul bekleniyor. |

İlk çalışmayan npm/peer, eski Kit yapılandırması, kesilen zoom görüntüleri, sunucu kapanışı ve ürün okuyucu kurulumu korunmuş retlerdir. Ölçüm veya test düzeltmesi ürün kabulü yerine geçmez. Eski olumlu kanıt yalnız kendi exact-head kaynağını kapsar.

## Ürün kabuğunun kapalı çalışma sözleşmesi

Üç panel Çalışma listesi / Kayıt bağlamı / İşlem durumu ve yerel bağlantılar gösterilir. Gerçek bağlantı ve izin doğrulanmadığı açıkça yazılır. Sahte aktör/rol, örnek özel satır, boş kuyruk veya başarılı işlem iddiası, onay/yayın düğmesi bulunmaz. Query veya localStorage erişim açamaz. JavaScript yoksa açık açıklama görünür. E2 doğrudan kanonik kayıt, audit veya E6 yazamaz; hassas etki yalnız Kavriva APIde güncel yetkiyle olabilir. Ürün bağlı değilken fixture ALLOW yolu açılamaz.

1440x900 kabul tabanı; gerçek200% zoom ve klavye sınanır. Tam responsive, final marka/token kütüphanesi ve sonraki görevlerin kuyruk/kaynak/yetki akışları bu kararda tamamlanmaz. Basit kabuk bir nihai görsel tasarım onayı değildir.

## İşletim maliyeti, olay ve çıkış

Gerçek komut süreleri/paketler/çıktılar deney maliyetidir. bc05785 Linux major fazlarında build toplamı eski19.870 / güncel16.419 saniye, gerçek Orca71.474 /69.274 saniyeydi; bunlar bir adayın hız veya üretim fatura tahmini değildir. CI işi25dakika ile sınırlı, ham artifact14gün saklanır; Gitte kaynak/tam kilit/testler ve makbuz özetleri kalır. Kanıt yeniden üretilebilir olmalıdır. Üretim trafik/host/ücret/cap kararı açık; belirsiz veya sınırsız harcama yetkisi yok.

Olaylarda örneğin kapalı durum/same-ID sorgusu teknik davranışı gösterir; üretimde kullanıcıya olayın etkisi ve güvenli yol gerçek APIyle ayrıca bağlanır. Sahibe SQL/SSH/log/console onarımı yüklenmez. Kabuk geri dönüşü normal PR revert; veri veya oturum yaratmaz. Başka native istemciye geçişte ürün authority sözleşmesi korunur; mevcut dört örnek eşitlik ve yeniden derleme test girdisidir. Üretim çıkış/göç güvencesi ayrı gerçek veriler olmadan varsayılmaz.

## Kabul için kalan kapılar

1. Kaynak2564b06 için ürün dahil dokuz CI ve gerçek ürün Orca kanıtı tamamlandı. Son metadata başlığında normal PR CI ayrıca gerekir.35525c0 FAILi ve Angular konuşma gözlemi korunur.
2. Aynı tam görev/plan önerisi/20 soru/kanıtın geçmişsiz gpt-6-luna/max bağımsız incelemesi; gerçek bulguların giderilmesi ve yeniden hüküm. Model talebi çalıştırılmış inceleme değildir.
3. Normal PR + yeşil plan CI ile bağlayıcı karar kaydı; ADR010un kısmi ardıllığı ancak o sırada açıkça güncellenir. İncelemesiz veya yönetici atlatmasıyla birleştirme yok.
4. Ürün görevinin yalnız kendi kabul ölçütleri için kanıt ve sınırlı durum güncellemesi. Bu belge tek başına T-E2-001i DONE yapmaz.

Üretim kimlik/yetki/oturum, gerçek veri/karantina/yayın, host/capacity/harcama ve genel ürün hazır olma kapıları açık kalır; bu taskın dar kabuk kabulüne sessizce taşınmaz veya tamamlandı diye kapatılmaz.

## Yeniden değerlendirme nedenleri

Seçilen kilitte güvenlik açığı, destek politikasının değişmesi, gerçek workload/erişilebilirlik kaybı, CSP/adapter zorunluluğu, sahibin onarım yapması gereği, işletim/çıkış maliyetinin sınırlandırılamaması veya gerçek API sözleşmesinin statik istemciyi karşılamaması yeni kayıtlı inceleme gerektirir. Başka framework, SSR veya BFF otomatik devreye girmez.

## Supersedes

Şu anda None (PROPOSED). Kabul edilirse yalnız ADR-010 Decision4 çatı seçimi boşluğu ve ilgili no-framework seçimi, yukarıdaki dar E2 kapsamıyla kısmen ardıllanır. Diğer bütün ADR010 ürün/üretim/tasarım sınırları korunur.

## Superseded By

None.


## Bağımsız R1 bulguları ve kaynak yeniden doğrulaması — 2026-10-18

Geçmişsiz `/root/e2001_whole_luna_max_r1` (istenen gpt-6-luna/max profili) APPc7f571a /PLAN7a1b2d5 için CHANGES_REQUIRED/HOLD verdi. İki P1 fixture bulgusu aynı-IDnin normal yenileme/tam reload ile kaybı ve doğrulanmamış çıkışa başarı denmesidir. Angular gerçek okuyucu240/0 farkı P2dir. Tam özgün rapor uygulama EDEV125te22.469bayt /SHA256 637cb5b8ed7f6bdc8fad31039b4bc1b08a6b213783a9bd30b1ed002e38056c22 olarak korunur. Yeni onarımın yerel build/92browser/11HTTP sonucu tek başına bağımsız kapanış değildir; yeni gerçek LinuxCI ve yeniden hüküm gerekir. Bu ADR PROPOSED kalır.

R1in diğer P2si resmi Nuxt görünümündeki Q1/4.6.0 ile buradaki Q4 ifadesinin uyuşmadığı yönündeydi. 18Ekim2026 12:56:54UTCde resmi yol haritası yeniden gerçek HTTP ile okundu: [resmi yönlenen Markdown](https://nuxt.com/raw/docs/4.x/community/roadmap.md),8.853bayt /SHA256 66cb5a6fa9b7a149b5c8064abc5b8418c728b170eea7fb56f71966bb80267d1d. Yanıt5.x için Q4 2026 estimated/scheduled;4.x stable ve5.x yayımlandıktan6ay sonra destek sonu diyor. [Resmi v4.6.2 kaydı](https://github.com/nuxt/nuxt/releases/tag/v4.6.2) ve GitHub releaseAPI published_at2026-10-16T17:21:23Z ile4.6.2 latest döndü. Böylece bu tekrar okumanın yılı/tarihi/kaynağı görünürdür; Q1/4.6.0 eski inceleme gözlemi silinmez. Yeni delille bulgunun kapanması veya geri çekilmesi bağımsız yeniden incelemede değerlendirilecektir. Q4 tahmini kesin yayın tarihi değildir ve Nuxt5 yayımlandı sonucu çıkarılmaz.

## R2 bağımsız inceleme ve güncel onarım — 2026-10-18

APP35723cc /PLAN0cef604 bütün görev R2 hükmü CHANGES_REQUIRED/HOLD. Önceki iki P1, eski240/0 ve Nuxt kaynak uyuşmazlığı kapandı; iki yeni P2 açık: tek t gezinmesinde güncel240ın iki ayrı konuşma satırında tekrarı ve çıkış takip kaydının geçici yazım hatasından sonra yenilemenin özel satır açması. Özgün R2 uygulama EDEV125te16410bayt /SHA256 e06b254750dfa5844338efbaed2395c798a6ede317a77c2fe0f6d09b77115bde; R1 değiştirilmedi.

Kod öncesi f2577b2 ve onarım c202241723b95c37b7577f2d8720714d269dc1f9 aynı73adresi/130pini korur. Dört build,104browser ve11HTTP yerel başarılı. Görsel40/37 tam bayt eş; Root üç yeni özgünü açtı. Yeni gerçek Linux E2 [CI39132829963](https://github.com/xpike-dgm/kavriva-app/actions/runs/39132829963) ve diğer iş akışları bekleniyor; tamamlandığı varsayılmaz. Sonraki adım gerçek olay başına tek konuşma/çıkış onarımının CI ve bütün görev bağımsız yeniden hükmüdür. ADR016 PROPOSED, ADR010 değişmedi, T-E2-001 IN_PROGRESS;113/93/206 ve117 fiziksel kayıt aynı. Aşağıdaki önceki inceleme/kaynak durumları kendi tarihsel başlıklarını kapsar.

Yerel takip arızasında yalnız mevcut fixture oturumunu kapatan istek sunucuya gönderilir; yeni kayıt/komutun kalıcı aynı-ID önkoşulu kaldırılmaz. Bellekte çıkış niyeti açıkken veri açılmaz. Çıkış niyeti takip kaydı tek-seferlik veya sürekli yazım hatasıyla hiç kaydedilmemiş, istek sunucuya ulaşmamış ve güvenli yeniden denemeden önce sayfa tamamen kapatılmış veya yenilenmişse yeni sayfada niyetin korunacağı garanti edilmez; hâlâ geçerli sunucu oturumundan satır açılabilir. Bu güvenli tam-yenileme PASSi veya üretim oturum güvenliği değildir. Sayı görsel olarak ve erişilebilir tablo adında korunur; yinelenen caption AXden çıkar ve gerçek Orcada her t olayında tam bir240 istenir. Yeni Linux kanıtı ve bağımsız kapanış beklenir.

## Güncel çıkış kabulünün kesin sınırı

Bu açıklama R1 kod öncesi bölümündeki “Reload doğrulanmamış çıkışta veriyi yeniden açmaz” cümlesinin genel okunmasını düzeltir. Özgün R1/R2 hükümleri ve testleri kendi başlıklarının tarihçesi olarak korunur. Bugünkü örnek için kabul edilen güvence şudur:

- Çıkış niyeti tarayıcıya başarıyla kaydedilmişse, sunucu yanıtı kaybolsa da tam sayfa yenilemesi özel görünümü kapalı tutar. Gerçek browser testleri sunucuya ulaşmadan kesilme ve sunucu kapattıktan sonraki yanıt kaybını ayrı sınar.
- Çıkış niyeti kaydı tek-seferlik veya sürekli bir yazım hatasıyla kaydedilemese de, aynı sayfada bellek kilidi veri, komut ve dosya yolunu açmaz. Sunucuya oturumu kapatma isteği gönderilir; güvenli yeniden deneme gerçek sunucu yanıtı ve takip kaydıyla çözülür.
- Çıkış niyeti **hiç kaydedilmemiş**, istek **sunucuya ulaşmamış** ve kullanıcı güvenli yeniden denemeden **sayfayı tamamen kapatmış veya yenilemişse**, yeni sayfa için çıkış niyetini koruma garantisi yoktur. Bu sınır yazım hatasının yalnız kalıcı olmasına bağlı değildir; **tek-seferlik yazım hatası da dahildir**. Sunucu oturumu hâlâ geçerliyse yeni sayfada kayıt açılabilir. Bu durum başarılı çıkış veya güvenli tam-yenileme olarak kabul edilmez.

Gerçek Chromium karşı örneği `logout-combined-boundary-probe.json`: tek yazım hatası + sunucu öncesi bağlantı kesilmesi; aynı sayfada0 satır/0 veri isteği, tam yenileme sonrasında aktif oturumdan20 satır. Sonuç `KNOWN_UNGUARANTEED_BOUNDARY_REPRODUCED`; PASS değildir. Makbuz üretim oturum sisteminin testi değildir. Üretim kimlik/oturum akışı bu örneğe bağlanmış değildir; üretimde güvenli çıkış bu kayıtla kapanmaz.

Kalıcı işlem kimliği ve komut yetkisi için mevcut önkoşullar değişmez. Bu sınırlı karar üretimde kimlik güvenliğini onaylamaz; özel veri veya giriş işlemi sunmayan kapalı kabuğun kabulünü ve dört örneğin eşit karşılaştırmasını kapsar. API tarafından kapatılmış/iptal edilmiş oturumun yeniden yetkilendirilmesine izin verilmez. Bu uç durum, iptal edilmiş oturumun dirilmediği ayrı olumsuzların yerine geçmez.


## R3 kaynak CI ve gerçek kanıt — yeni kayıt başlığının CI sonucu değildir

ad5fee396885b11d1154345599c5195ea9b3ab7b başlığında dokuz kaynak push iş akışı gerçek SUCCESS. E2 [39133278603](https://github.com/xpike-dgm/kavriva-app/actions/runs/39133278603), ham268199bayt /SHA256 1ff23019145627cd3c26ec5ff576f01d17ad717d2243e390575b73a21930aec0. İlk/eski/güncel turların her birinde104browser, toplam36 gerçek t olayında tek240 ve eski0 yok.13 gerçek ses/konuşma SHA ve sessiz olmayan PCM,22 alt komut rawlog/exit/byteSHA,46 Git kaynak özeti,16 native eşlik ve4eskiartifact dönüşünde0yazım gerçek dosyalarda doğrulandı. Ayrı kapalı ürün8browser/zoom/SSIP/Orca ve audit0. Root36 olayın gerçek konuşma sırasını ve13 transcriptteki61 benzersiz prefixin tamamını okudu; bütün WAVı dinlediği veya insan telaffuz/kullanılabilirlik onayı verdiği söylenmez. Tablo boyutu/bağlamı farklı yapısal aşamalarda tekrarlanabilir; dar kabul yalnız240 sayısının her t olayında tek anılmasıdır.

R3 bağımsız hükmü CHANGES_REQUIRED/HOLD; açık P1 yok, tek P2 kabul metni/sınır tutarsızlığı. Önceki kod bulguları bağımsız olarak kapandı. Bu değişiklik yalnız metin/kanıt uyumudur; runtime, kilit, test veya checker değişmedi. Yeni kaynak başlığı için eski CI aynı-head CI diye sunulmaz. Tek P2nin bağımsız kapanışı, normal PR/CI ve kanonik çatı kararı beklenir. Görev IN_PROGRESS;113/93/206 değişmedi.
