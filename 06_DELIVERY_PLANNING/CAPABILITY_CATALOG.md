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
|---|---|---|---|---|---|
