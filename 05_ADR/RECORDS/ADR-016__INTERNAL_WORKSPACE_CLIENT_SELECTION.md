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

Resmi kaynaklar: [React sürüm politikası](https://react.dev/community/versioning-policy), [Angular destek tablosu](https://angular.dev/reference/releases), [Nuxt yol haritası](https://nuxt.com/docs/4.x/community/roadmap/), [SvelteKit3 göçü](https://svelte.dev/docs/kit/migrating-to-sveltekit-3). Okuma tarihi18Ekim2026. Nuxt5 Q4 tahmini yayımlanma kanıtı değildir; Nuxt3ün31Temmuz2026 destek sonu yalnız göç girdisinin riskidir.

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
