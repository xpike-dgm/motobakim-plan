# GLOSSARY

Status: APPROVED

Projede kullanilan domain terimlerinin tek anlamli sozlugu. `PROPOSED` terimler discovery sirasinda netlestirilebilir.

**Approved registry by user:** 2026-09-14  
**Important:** Belgenin `APPROVED` olmasi, her `PROPOSED` terimin nihai/LOCKED oldugu anlamina gelmez.

| Term | Canonical Meaning | Source Class | Synonyms / Avoid | Status |
|---|---|---|---|---|
| MotoBakim | Kullanicinin kendi motosikletindeki bakim, mekanik ve elektriksel islemleri anlamasina, uygulamasina ve gecmis/sonraki ihtiyaclarini takip etmesine yardimci olmayi amaclayan urun. | USER | — | PROPOSED |
| Motosiklete Ozel Bilgi | Genel motosiklet bilgisinden farkli olarak, kullanicinin gercek motosiklet konfigurasyonuna ve islemi etkileyen yil/versiyon/donanim farklarina uygun teknik bilgi ve yonlendirme. | USER | `genel bilgi` ile es anlamli kullanma | PROPOSED |
| Dogrulanmis Bilgi | Kullanicinin motosiklet/varyantiyla eslesen guvenilir kaynaga dayanan; kaynak surumu ve ilgili sayfa/bolum kaniti gorulebilen ve kullanici beklentisine gore insan incelemesinden gecmis teknik bilgi. Kritik kaynak celiskisi cozulmemisse tek kesin deger gibi sunulmaz. | USER | `AI tahmini`, `internette cok tekrarlandi`, `yaklasik teknik deger` ile es anlamli kullanma | PROPOSED |
| Asamali Rehber | Bir islemi hazirliktan tamamlanmasina kadar mantikli adimlarla yonlendiren urun deneyimi. Yeni kullanici icin adim birimi tek hareket + ilgili gorsel + basari kontrolu seviyesine kadar inebilir. | USER | `tek parca makale`, `sokup geri takin` gibi atlamali anlatim | PROPOSED |
| Gorsel Yonlendirme | Parcayi/konumu tanimak icin gercek ve isaretli motosiklet fotografi; gizli baglantilarda cizim; hareket yonu/sira kritikse kisa video gibi gorsel desteklerin genel adi. Tam varyant fotografi yoksa dogrulanmis cizim/isaretli sema fallback olabilir; baska motosiklet gorseli ayniymis gibi sunulamaz. | USER | — | PROPOSED |
| Bakim Gecmisi | Kullanicinin motosikleti uzerinde tamamladigi, yarim biraktigi veya disarida yaptirdigi bakim/ilgili islemlerin durum ve kanitlariyla izlenen kronolojik kaydi. | USER | Yalniz `tamamlanmis isler listesi` olarak daraltma | PROPOSED |
| Sonraki Bakim Ihtiyaci | Motosiklet icin ileride yapilmasi gereken bakim/servis ihtiyacinin uretici kilometre/sure araliklari ve dogrulanmis tamamlanma kaydiyla iliskili olarak izlenmesi. | USER | Dogrulanmamis tahmini aralik | PROPOSED |
| Yeni / Az Deneyimli Kullanici | Kendi motosikleti uzerindeki teknik islemlerde sinirli deneyimi olan ve hareket-bazli ayrintili gorsel anlatima ihtiyac duyabilen hedef kullanici grubu. | USER | `yeni motosiklet sahibi` ifadesini otomatik olarak deneyimsiz kabul etme | PROPOSED |
| Deneyimli Kullanici | Bakim veya teknik islemlerde deneyimi bulunan, kisa kontrol listesine ve teknik ayrintiya hizla ulasmak isteyen; ancak guvenlik ve kritik dogrulamayi yine koruyan hedef kullanici grubu. | USER | — | PROPOSED |
| Motosiklet-Rehber Eslesmesi | Rehberin kullanicinin gercek motosikletinin yil/versiyon/donanim ve islemi etkileyen diger ozellikleriyle uygunlugunun yeterince kesinlestirilmis olmasi. Modifiye sistemde fabrika rehberi otomatik uygun sayilmaz. | USER + INFERRED | `marka/model benziyor` ile es anlamli kullanma | PROPOSED |
| Rehber Dali | Ayni islem icin yil, versiyon veya donanima bagli farkli adim yolunun ayri bicimde ele alinmasi. | USER | — | PROPOSED |
| Ilgili Versiyon | Ayni marka/model/yil icinde islem adimini, gerekli malzemeyi veya guvenlik kontrolunu degistiren ozellikler bakimindan kullanicinin motosikletiyle eslesen varyant. | USER | — | PROPOSED |
| Kritik Dogrulama Adimi | Islemin guvenli ve dogru ilerledigini kanitlamak icin deneyim seviyesinden bagimsiz olarak atlanmamasi gereken kontrol. | USER | `opsiyonel kontrol` ile karistirma | PROPOSED |
| Basari Kontrolu | Tek bir islem hareketinden sonra beklenen dogru sonucun gozlem, olcum veya baska kontrolle dogrulanmasi. | INFERRED | — | PROPOSED |
| Durdurma Noktasi | Rehber-gercek motosiklet uyusmazligi, gerekli arac/olcum eksikligi, beklenmeyen fiziksel durum veya kritik sonucun dogrulanamamasi gibi nedenlerle uygulamali ilerlemenin kesilmesi gereken durum. | INFERRED | Sadece `uyari` olarak kullanma | PROPOSED |
| Guvenli Esdeger | Alternatif arac, sarf veya yardimci ekipmanin gerekli olcu, uyum, dayanim, malzeme, islev ve guvenlik ozelliklerini karsiladiginin dogrulanmis olmasi. Hassas olcum, dogru sikma veya guvenli kaldirma icin zorunlu ekipman eksikliginde alternatif varsayilmaz. | USER | `benzer gorunen alternatif` | PROPOSED |
| Olasi Neden | Bir ariza belirtisini aciklayabilecek ancak gozlem veya olcumle henuz dogrulanmamis teshis adayi. | USER | `kesin teshis` ile karistirma | PROPOSED |
| Neden Dogrulanamadi | Makul ve guvenli ayirt edici kontroller tamamlandigi halde arizanin belirli bir nedeninin yeterli kanitla dogrulanamadigini ifade eden teshis sonucu. | USER | `teshis basarisiz, rastgele parca degistir` anlamina gelmez | PROPOSED |
| Rehber Surumu | Kullanicinin bir islemi uygularken kullandigi rehber iceriginin belirli versiyonu; yarim ve gecmis islemlerde izlenmesi beklenen referans. | INFERRED | — | PROPOSED |
| Kritik Duzeltme | Mevcut rehber adimlarinin guvenli bicimde uygulanmaya devam edilmesini etkileyebilecek ve eski akisin durdurulmasini gerektirebilecek kaynak/rehber degisikligi. | INFERRED | — | PROPOSED |
| Rehber Askiya Alma | Kritik degisiklik, hata veya cozulmemis belirsizlik degerlendirilene kadar etkilenen uygulamali adimlarin ilerleme icin sunulmamasi. | INFERRED | — | PROPOSED |
| Insan Incelemesi | Ilgili sistemde uygulamali deneyimi olan bir kisinin motosiklet uyumu, kaynaklar, gorseller, araclar, riskler ve son kontrol acisindan rehberi degerlendirmesi. | USER | Belirli sertifika/unvan zorunlulugu varsayma | PROPOSED |
| Bagimsiz Ikinci Inceleme | Kritik rehberde ilk incelemeden ayri ikinci bir insan degerlendirmesi; kullanici acisindan ek guven sinyali. Tum kritik rehberlerde zorunlu oldugu henuz karar degildir. | USER | `zorunlu her durumda iki reviewer` olarak genelleme | PROPOSED |
| Islem Readiness | Kullanicinin belirli bir is icin benzer deneyim, arac/olcum bilgisi, onceki kayitlar ve on kosul anlayisi acisindan uygulamali adima hazir olma durumu. | INFERRED | Genel `deneyimliyim` beyanina indirgeme | PROPOSED |
| Dogrulanmis Tamamlanma Kaydi | Bir bakim/islemin gercekten tamamlandigi ve gerekli son kontrollerinin dogrulandigi kayit; sonraki bakim zamanlamasinin dayandirildigi kayit. | INFERRED | `ertelendi`, `yarim`, `dogrulanamadi` durumlariyla karistirma | PROPOSED |
| Dis Islem Kaydi | Servis veya baska biri tarafindan yapilan ve kaynagi belirtilerek motosiklet gecmisine eklenen islem kaydi. | INFERRED | — | PROPOSED |
| Dogrulanmamis Dis Islem | Disarida yapildigi kaydedilen ancak yeterli kanit bulunmadigi icin dogrulanmis tamamlanmis islem statüsunde gosterilmemesi gereken kayit. | INFERRED | `fatura var = otomatik dogrulanmis` olarak kullanma | PROPOSED |
| Bakim Onceligi | Birden fazla gecikmis bakim arasinda guvenlik/kullanim etkisi, gecikme miktari ve kullanilabilir dogrulanmis kosullara gore gerekceli siralama. | USER | Sadece `en eski tarih` olarak siralama | PROPOSED |
| Recovery / Guvenli Geri Donus | Hata, uyumsuzluk veya beklenmeyen durumda normal rehber akisini durdurup motosikleti guvenli hale getirme, kanit saklama ve uygun geri donus/profesyonel yardim yoluna ilerleme davranisi. | INFERRED | — | PROPOSED |

## Approval Note

Bu glossary registry Phase 1 icin onaylanmistir. Batch 01 ve Batch 02 kullanici kanitlari terimleri rafine etmistir. Terimler `PROPOSED` kalir; nihai/LOCKED terminoloji karari henuz verilmemistir.
