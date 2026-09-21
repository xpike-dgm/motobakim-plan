# CAPABILITY CATALOG

Status: PROPOSED (E3 + E10 owner-approved 2026-09-21; remaining epics pending)

| Capability ID | Epic | Name | User/Product Outcome | Dependencies | Status |
|---|---|---|---|---|---|
| C3.1 | E3 | API yetki kapısı | Her hassas işlem kapıdan geçer; ortak durum sözlüğü çalışır | — | PROPOSED |
| C3.2 | E3 | Kanonik veri otoriteleri | Alan başına tek doğru kaynak; geçmiş/denetim/medya düzlemleri ayrı | — | PROPOSED |
| C3.3 | E3 | Fiziksel platform kurulumu | Supabase merkezli çekirdek, savunma katmanları, gizli anahtar emaneti | C3.2 | PROPOSED |
| C3.4 | E3 | Uzun iş kuyruğu | Paket/tarama/dışa aktarma işleri dayanıklı kuyrukla yürür | C3.1 | PROPOSED |
| C3.5 | E3 | Negatif zemin + epoch | Yasak/geri çekme katmanları ve tüm uçlara yayılan iptal çalışır | C3.1, C3.2 | PROPOSED |
| C3.6 | E3 | Yedekleme/geri yükleme/çıkış | Karantinalı geri yükleme ve temiz oda çıkışı tatbikatları yapılır | C3.3, C3.5 | PROPOSED |
| C3.7 | E3 | Maliyet kalemleri + durdurma | Kalem kalem fatura görünür; tavan aşımında güvenli duruş olur | — | PROPOSED |
| C3.8 | E3 | Ortamlar | Geliştirme/test/canlı ayrılığı ve terfi disiplini çalışır | C3.3 | PROPOSED |
| C10.1 | E10 | Graf şeması + kimlik | Kart türleri, ilişki tipleri, denetlenebilir künye standardı yayında | — | PROPOSED |
| C10.2 | E10 | Kapsül topolojisi | Modül sınırları, public sözleşmeler, bağımlılık yön kuralları kilitli | C10.1 | PROPOSED |
| C10.3 | E10 | Görev zarfı + kayıt defteri | Zarf şeması ve görev durumları (READY→DONE) işler | C10.2 | PROPOSED |
| C10.4 | E10 | Kapanış matrisi | 10 katman takibi ve çift yönlü izlenebilirlik denetimi çalışır | C10.3 | PROPOSED |
| C10.5 | E10 | Kodsuz simülasyon seti | Sıra/çakışma/arıza/geri alma tatbikat senaryoları hazır | C10.4 | PROPOSED |
| C10.6 | E10 | Tasarım tutarlılık kapısı | Katalog zorunluluğu ve görsel+anlamsal regresyon kanıtı işler | — | PROPOSED |
| C10.7 | E10 | Rol ayrılığı protokolü | Uygulayıcı/inceleyici ayrımı ve bağımsız inceleme kuralları çalışır | C10.3 | PROPOSED |
| C5.1 | E5 | Tüketici kimliği | Hesapsız başlangıç, profiller, çakışmasız geçiş; Supabase yönü, satın alma yok | E3 | PROPOSED |
| C5.2 | E5 | Hibrit yetkilendirme | Sunucuda her istekte karar; yayın yolunda da görev ayrılığı | E3 | PROPOSED |
| C5.3 | E5 | Doğrulama + oturum + epoch | Oltalamaya dayanıklı giriş, ikinci doğrulama; epoch tüm uçları kapatır, indirilen kopya geri alınamaz (dürüst) | E3 | PROPOSED |
| C5.4 | E5 | Kurtarma (yalnız) | İptal + taze giriş, çift kontrol/son-yönetici; kurtarma asla onay/yayın/yetki vermez | E3 | PROPOSED |
| C5.5 | E5 | Denetim kasası (detaylı) | Olay kapsamı, asgari anlam, etki-öncesi bağ, bütünlük/uyarı, soruşturma zinciri, yönetim ayrılığı | E3 | PROPOSED |
| C5.6 | E5 | Karantina + dışa aktarma + AI önerisi | Karantina hattı; dışa aktarma geri alınamaz kayıt; AI çıktısı öneri, asla onay değil | E3 | PROPOSED |
| C5.7 | E5 | Ayrıcalıklı aktivasyon kapısı | 11 maddelik kanıt paketi geçilmeden kritik iç üretim açılmaz | E3 | PROPOSED |
| C6.1 | E6 | Sürüm otoriteleri + çökmeme | 8 otorite ayrı; rol birleşemez, personel yoksa görünür BEKLEME | E3, E5 | PROPOSED |
| C6.2 | E6 | Onay→yayın + çit kuralı | Mühürlü paket, tek kapı; yayın askı kuşağına bağlı, geri gidiş ölümcül hata; istemcide sözleşme denetlenebilir | E3, E5 | PROPOSED |
| C6.3 | E6 | Acil fren + negatif kullanım | Normal yol çökse de durdurma; cam-kırma kullanımı, tatbikatlar | E3, E5 | PROPOSED |
| C6.4 | E6 | Köken/SBOM/imza + yeniden-derleme-yok | Soy, doğrulama, kasa; üretime aynen terfi, sabit bağımlılıklar | E3, E5 | PROPOSED |
| C6.5 | E6 | Ayar/bayrak/geçiş sürümleri | Yapılandırma ve veritabanı geçişleri sürüm disiplininde | E3, E5 | PROPOSED |
| C6.6 | E6 | Kademeli dağıtım + geri alma + karantina | Kontrollü yayılım, yeni-olay geri dönüş; geri yüklenen sistem karantinada | E3, E5 | PROPOSED |
| C6.7 | E6 | Olay müdahalesi + etki grafiği | Sızıntı haritası, müdahale yolu, kanıt koruma | E3, E5 | PROPOSED |
| C6.8 | E6 | OTA ret kararı | Uzaktan kod kanalı kapalı; ilerde ayrı yetki ister | E3, E5 | PROPOSED |
| C4.1 | E4 | Komple paket bileşimi | Doğrulanmış gerekli-kompakt çekirdek + iç içe güvenlik medyası; zorunlu-olmayan medya dışarıda (ayrı/açık/iptal edilebilir/temizlenebilir/yeniden alınabilir, boyut önceden gösterilir); kapsam seçili motosiklet/görev, veri-verimli, tam-kütüphane yok | E3 | PROPOSED |
| C4.2 | E4 | Paket kabul | Aşamala → doğrula → atomik yükselt; bozuk/karışık/eski paket kullanılamaz; eksik delta tam pakete düşer; zirve alan kuralı | E3 | PROPOSED |
| C4.3 | E4 | Otomatik transfer (CON-005) | Gerekli içerik Wi-Fi/hücresel/roaming'de onaysız başlar; ağ-türü/MB eşiği diyaloğu yok; desteklenen yerde sürdürülebilir tekrar (değerler HELD) | E3 | PROPOSED |
| C4.4 | E4 | Adaptif depolama | Geçici → gereksiz medya → eski önbellek sırası; aktif paket/kullanıcı verisi/denetim/zemin asla otomatik silinmez | E3 | PROPOSED |
| C4.5 | E4 | Kullanıcı defteri | Kimlikli işlem + parmak izi + sürüm; API ile gönderim/sorgu; sessiz son-yazan-kazanır yok (kritik veri); geri yükleme karantinada, yasaklıyı diriltemez | E3 | PROPOSED |
| C4.6 | E4 | Risk kademeli uygunluk | Bilinmeyen/eski kritik bağımlılık kapalı kalır, en ağır sonuç miras alınır; kurtarma kapanışı tam olmadan çevrimdışı başlangıç yok | E3 | PROPOSED |
| C4.7 | E4 | Şifreleme | Mekanizma/anahtar emaneti ayrı karar; düz-metin yedeği yasak | E3 | PROPOSED |
| C4.8 | E4 | Sayısal politika HELD | Aday noktalar (5–100MB paket, %5–20 alan vb.) HELD; gerçek ölçümle seçilecek | E3 | PROPOSED |
| C9.1 | E9 | Asistan akışı | Anla → sor → 5 seçenekten aday öner → 6 boyutta doğrula → göster/sor/beklet; E9 önerir, E1 gösterir, E3 doğrular | E3, E1 | PROPOSED |
| C9.2 | E9 | Ekonomik ilke | En ucuz/yeterli hızlı model önce; gerekince yükselt; kural çözen işte deterministik kazanır | E3, E1 | PROPOSED |
| C9.3 | E9 | Değiştirilebilir sınır | Sağlayıcı detayı adaptörde; sürüm/değişim gözlemlenir, yeniden değerlendirilir | E3, E1 | PROPOSED |
| C9.4 | E9 | Asgari yetki araçları | İçerik asla politika değil; araç yetkisi model çıktısının dışında; AI-dışı güvenli devam yolu | E3, E1 | PROPOSED |
| C9.5 | E9 | İzinli AI yardımları | Anlama/soru/normalleştirme/sorgu/özet/sıralama/taslak/triyaj/proje-araştırma/sınırlı öneri (10 kalem) | E3, E1 | PROPOSED |
| C9.6 | E9 | Asla-tek-yetki listesi | 15 kalem (nitelikli): desteksiz değer, kanonik gerçek, kesin teşhis, onay/yayın/geri alma, imza, faturalama vb. AI'ya ait değil | E3, E1 | PROPOSED |
| C9.7 | E9 | Proje AI disiplini | Uygulayıcı/inceleyici ayrımı, kanıt, taklit yasağı (DEC-0028/0029) | E3, E1 | PROPOSED |
| C1.0 | E1 | Uygulama kabuğu + sekmeler | 5 sekme (Garaj·Bakım·AI Usta·Geçmiş·Topluluk), aktif-iş korunumu, SCR-005 daraltılmış; Türkçe/birim/erişilebilirlik temeli (sunum katmanı; taşınabilir gerçeklik çerçeve dışında; derleme/cihaz kanıtı yok) | E3, E5, E4 | PROPOSED |
| C1.1 | E1 | İlk kullanım + motosiklet bağlamı | SCR-001..005: giriş, motor ekleme, varyant ayrımı, uygunluk halleri | E3, E5, E4 | PROPOSED |
| C1.2 | E1 | Rehber bulma/uygunluk/hazırlık | SCR-009..013; hazırlık kapısı, engelli-hazırlık atlaması yok | E3, E5, E4 | PROPOSED |
| C1.3 | E1 | Aktif uygulama/güvenlik/kurtarma | SCR-014..018; dürüst kısmi/çözümsüz/güvenli-duruş sonuçları, devam-et-yok | E3, E5, E4 | PROPOSED |
| C1.4 | E1 | Tanı akışları | SCR-019..021; tehlike-öncelikli, tek ayırt edici kontrol, E9 yönlendirmeli | E3, E5, E4 | PROPOSED |
| C1.5 | E1 | Bakım/hatırlatıcı | SCR-022..024; uydurma aralık yok, erteleme≠tamamlama, yetişme özeti | E3, E5, E4 | PROPOSED |
| C1.6 | E1 | Geçmiş/kanıt/güven + dışa aktarma | SCR-025..030; E1 gösterir, E3 sunar, E5 yetkilendirir/denetler; dışa aktarma paralı olamaz | E3, E5, E4 | PROPOSED |
| C1.7 | E1 | Yaşam döngüsü + hak kapıları | SCR-008 + SCR-031..033 + SCR-037; pasif≠silme, transfer kapsamı; saklama politikası ertelendi, hak sunucuda denetlenir | E3, E5, E4 | PROPOSED |
| C1.8 | E1 | Profil/işbirliği/geçiş | SCR-006/007/034; zorlamasız geçiş, sessiz kayıpsız çakışma incelemesi, ayrılabilir işbirliği | E3, E5, E4 | PROPOSED |
| C1.9 | E1 | Topluluk yüzeyi (tüketici) | SCR-035/036/038; opt-in katkı, durum/sebep/düzeltme/itiraz yolları; karar E2'de | E3, E5, E4 | PROPOSED |
| C1.10 | E1 | AI Usta girişi | A1 (1 bağlam + 1 soru + 2 yol); üçüncü yol/yazışma yok; uygunluk atlaması yok; E9 önerir, E1 gösterir, E3 doğrular | E3, E5, E4 | PROPOSED |
| C2.1 | E2 | Çalışma alanı kabuğu | Yoğun masaüstü tarayıcı alanı + gezinme; erişilebilirlik temeli (duyarlı tasarım ertelendi); çatı seçimi yok, her hassas iş API'de yeniden yetkilendirilir | E3, E5 | PROPOSED |
| C2.2 | E2 | İnceleme/onay kuyrukları | Kanıtlı paketler; WS-06 inceleme/onay + WS-05 açık/çakışma; bağımsızlık arayüzde zorlanır | E3, E5 | PROPOSED |
| C2.3 | E2 | Yayın/geri çağırma operasyonu | WS-07 sürüm/yayın + WS-11 düzeltme/geri çağırma yürütme yüzeyi | E3, E5 | PROPOSED |
| C2.4 | E2 | Kaynak/kanıt + karantina görünümü | WS-03 kaynak/köken; özel karantina (özet/soy/sınıf); etkinleşme yalnız API yetkisiyle | E3, E5 | PROPOSED |
| C2.5 | E2 | Kapsama/kalite görünürlüğü (yalnız) | WS-01 araştırma + WS-09 kalite; kayıt-türevi ölçümler (RQ-052..058); E8 düzlemlerini tüketir, yığın seçmez | E3, E5 | PROPOSED |
| C2.6 | E2 | Erişim yönetimi görünümü | WS-12: rol/kapsam, temsil, yeniden onay, iptal yüzeyleri; kendine-yetki yolu yok | E3, E5 | PROPOSED |
| C2.7 | E2 | Topluluk moderasyonu (karar) | SCR-036 arkası iç karar: sebepli işlem + denetim izi; tüketici akışı yok | E3, E5 | PROPOSED |
| C2.8 | E2 | Yazarlık taslağı | WS-04 sınırlı Kavriva-içi taslak (RQ-017..024); taslak-asla-canlı, kendi başına yayınlamaz | E3, E5 | PROPOSED |
| C2.9 | E2 | Varyant/uygulanabilirlik sınırı | WS-02: motosiklet/varyant kapsam çiti | E3, E5 | PROPOSED |
| C2.10 | E2 | Sürüm geçmişi/soy | WS-08: sürüm zinciri ve türeme soyu görünürlüğü | E3, E5 | PROPOSED |
| C2.11 | E2 | Denetim/değişim geçmişi | WS-10: denetim izi görünürlüğü (kasa E5'te) | E3, E5 | PROPOSED |
| C7.1 | E7 | Android şeridi sürekliliği | Bağımsız düşük maliyetli şerit; kaynak dışarıda; derleme≠onay; imza/mağaza CI'dan ayrı; köken bağlama (E6 politikasının şerit uygulaması); harcama görünürlüğü + çıkış koşu kitabı (YÜRÜTME; politika E6'da) | E3, E6 | PROPOSED |
| C7.2 | E7 | iOS aktivasyon kapısı | 5 kanıt ayrı ayrı (gerçek Mac, Apple emaneti, bağımsız geçmiş, sahipsiz-kurtarma, temiz oda); kapılar istemeden sabit/barındırma/ücretli taahhüt yok | E3, E6 | PROPOSED |
| C7.3 | E7 | Yetki ayrılığı | Derleme/imza/köken/onay/mağaza/taşıma/doğrulama ayrı; sağlayıcı çalıştırır ama sahip olamaz; anahtar kaybı = iptal/değiştir/yeniden kur (YÜRÜTME; politika E6'da) | E3, E6 | PROPOSED |
| C7.4 | E7 | Kabiliyet sınıflandırması | Zorunlu/ertelenebilir/opsiyonel/ölçek-tetikli listeler | E3, E6 | PROPOSED |
| C7.5 | E7 | Maliyet okuması | Linux ucuz; macOS dar bantta uyar; sabit donanım uzun vadede; TRY plan bağlamı, alım yetkisi değil; mağaza ücreti ayrı | E3, E6 | PROPOSED |
| C8.1 | E8 | Kavriva teknik otoritesi (birebir) | Kaynak/iddia ilişkileri, varyant uygulanabilirliği, değişmez anlık-görüntü onayı, sürüm kimliği, askı kuşakları, paket uygunluğu + bağımlılık kapanışı, son yayın yetkisi (sahiplik E3/E6'da; E8 tanımlamaz); baypas listesi kapalı, CMS dahil projeksiyonlar yeniden-üretilebilir | E3 | PROPOSED |
| C8.2 | E8 | Yazarlık-sınırlı ek | Sınırlı yazım/düzen/çeviri/medya; onay/yayın/geri alma/yetki veremez; çıkarılabilirlik kapısı; ölçülen yükte yeniden değerlendirme; ilk sürümde CMS yok | E3 | PROPOSED |
| C8.3 | E8 | Ölçüm düzlem ayrılığı | Kayıt-türevi sayaçlar; denetim analitik dışında; gözlem ayrı; mağaza sinyali destek (kayıt/şema E3'te; E8 türetir; E2 yalnız gösterir) | E3 | PROPOSED |
| C8.4 | E8 | Analitik disiplini + azaltma (birebir) | Amaçlı/en-az/anonim/değiştirilebilir; geç yükleme/kota/faturalama/silme güvenli yolu bozamaz; sağlayıcı değişimi kayıt/denetim/sayaçları taşıyamaz; yasak listesi birebir; sınıf başına amaçlı saklama | E3 | PROPOSED |
| C8.5 | E8 | İlk-sürüm ölçüm yeteneği | İç operasyon görünürlüğü, en-az kullanım, çökme sinyalleri, rıza denetimi, telemetri sağlığı, eski-istemci uyumu, saklama yolu, kesinti bağımsızlığı | E3 | PROPOSED |
| C8.6 | E8 | Yedek kural + çıkış dürüstlüğü | Gizlilik/işletilebilirlik/maliyet/çevrimdışı/çıkış kapısı geçemezse küçük öz tabana dön, zayıflatma yok; ham dışa aktarma çıkış kanıtı değil | E3 | PROPOSED |
|---|---|---|---|---|---|
