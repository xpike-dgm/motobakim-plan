# GLOSSARY

Status: APPROVED

Projede kullanilan domain terimlerinin tek anlamli sozlugu. `PROPOSED` terimler discovery sirasinda netlestirilebilir.

**Approved registry by user:** 2026-09-14  
**Important:** Belgenin `APPROVED` olmasi, her `PROPOSED` terimin nihai/LOCKED oldugu anlamina gelmez.

| Term | Canonical Meaning | Source Class | Synonyms / Avoid | Status |
|---|---|---|---|---|
| MotoBakim | Kullanicinin kendi motosikletindeki bakim, mekanik ve elektriksel islemleri anlamasina, uygulamasina ve gecmis/sonraki ihtiyaclarini takip etmesine yardimci olmayi amaclayan urun. | USER | — | PROPOSED |
| Motosiklete Ozel Bilgi | Genel motosiklet bilgisinden farkli olarak, kullanicinin gercek motosiklet konfigurasyonuna ve islemi etkileyen yil/versiyon/donanim farklarina uygun teknik bilgi ve yonlendirme. | USER | `genel bilgi` ile es anlamli kullanma | PROPOSED |
| Dogrulanmis Bilgi | Kullanicinin motosiklet/varyantiyla eslesen guvenilir kaynaga dayanan; kaynak surumu ve ilgili sayfa/bolum kaniti gorulebilen ve kullanici beklentisine gore insan incelemesinden gecmis teknik bilgi. Kritik kaynak celiskisi cozulmemisse tek kesin deger gibi sunulmaz. | USER | `AI tahmini`, `internette cok tekrarlandi`, `yaklasik teknik deger` | PROPOSED |
| Asamali Rehber | Bir islemi hazirliktan tamamlanmasina kadar mantikli adimlarla yonlendiren urun deneyimi. Yeni kullanici icin adim birimi tek hareket + ilgili gorsel + basari kontrolu seviyesine kadar inebilir. | USER | `tek parca makale`, atlamali `sokup geri takin` anlatimi | PROPOSED |
| Gorsel Yonlendirme | Parcayi/konumu tanimak icin gercek/isaretli motosiklet fotografi; gizli baglantida cizim; hareket yonu/sira kritikse kisa video gibi desteklerin genel adi. Tam varyant fotografi yoksa dogrulanmis cizim/isaretli sema fallback olabilir; baska motosiklet gorseli ayniymis gibi sunulamaz. | USER | — | PROPOSED |
| Bakim Gecmisi | Kullanicinin motosikleti uzerinde tamamladigi, yarim biraktigi veya disarida yaptirdigi bakim/ilgili islemlerin durum, kanit ve degisiklik iziyle izlenen kronolojik kaydi. | USER | Yalniz `tamamlanmis isler listesi` | PROPOSED |
| Sonraki Bakim Ihtiyaci | Motosiklet icin ileride yapilmasi gereken bakim/servis ihtiyacinin uretici kilometre/sure araliklari, dogrulanmis tamamlanma kaydi ve dogrulanmis istisnalarla iliskili izlenmesi. | USER | Dogrulanmamis tahmini aralik | PROPOSED |
| Yeni / Az Deneyimli Kullanici | Kendi motosikleti uzerindeki teknik islemlerde sinirli deneyimi olan ve hareket-bazli ayrintili gorsel anlatima ihtiyac duyabilen hedef kullanici grubu. | USER | `yeni motosiklet sahibi`ni otomatik deneyimsiz sayma | PROPOSED |
| Deneyimli Kullanici | Bakim/teknik islemlerde deneyimi bulunan, kisa checklist ve teknik ayrintiya hizla ulasmak isteyen; safety ve kritik dogrulamayi yine koruyan hedef kullanici grubu. | USER | — | PROPOSED |
| Motosiklet-Rehber Eslesmesi | Rehberin kullanicinin gercek motosikletinin yil/versiyon/donanim ve islemi etkileyen diger ozellikleriyle uygunlugunun yeterince kesinlestirilmis olmasi. Modifiye sistemde fabrika rehberi otomatik uygun sayilmaz. | USER + INFERRED | `marka/model benziyor` | PROPOSED |
| Rehber Dali | Ayni islem icin yil, versiyon veya donanima bagli farkli adim yolunun ayri bicimde ele alinmasi. | USER | — | PROPOSED |
| Ilgili Versiyon | Ayni marka/model/yil icinde islem adimini, gerekli malzemeyi veya safety kontrolunu degistiren ozellikler bakimindan kullanicinin motosikletiyle eslesen varyant. | USER | — | PROPOSED |
| Kritik Dogrulama Adimi | Islemin guvenli ve dogru ilerledigini kanitlamak icin deneyim seviyesinden bagimsiz olarak atlanmamasi gereken kontrol. | USER | `opsiyonel kontrol` | PROPOSED |
| Basari Kontrolu | Tek bir islem hareketinden sonra beklenen dogru sonucun gozlem, olcum veya baska kontrolle dogrulanmasi. | INFERRED | — | PROPOSED |
| Durdurma Noktasi | Rehber-gercek motosiklet uyusmazligi, gerekli arac/olcum eksikligi, beklenmeyen fiziksel durum veya kritik sonucun dogrulanamamasi gibi nedenlerle uygulamali ilerlemenin kesilmesi gereken durum. | INFERRED | Sadece `uyari` | PROPOSED |
| Guvenli Esdeger | Alternatif arac/sarf/yardimci ekipmanin gerekli olcu, uyum, dayanim, malzeme, islev ve safety ozelliklerini karsiladiginin dogrulanmis olmasi. | USER | `benzer gorunen alternatif` | PROPOSED |
| Olasi Neden | Bir ariza belirtisini aciklayabilecek ancak gozlem veya olcumle henuz dogrulanmamis teshis adayi. | USER | `kesin teshis` | PROPOSED |
| Neden Dogrulanamadi | Makul ve guvenli ayirt edici kontroller tamamlandigi halde arizanin belirli bir nedeninin yeterli kanitla dogrulanamadigini ifade eden teshis sonucu. | USER | `rastgele parca degistir` sonucu | PROPOSED |
| Rehber Surumu | Kullanicinin bir islemi uygularken kullandigi rehber iceriginin belirli versiyonu; yarim/gecmis islemlerde izlenen referans. | INFERRED | — | PROPOSED |
| Kritik Duzeltme | Mevcut rehber adimlarinin guvenli devamini etkileyebilecek ve eski akisin durdurulmasini gerektirebilecek kaynak/rehber degisikligi. | INFERRED | — | PROPOSED |
| Rehber Askiya Alma | Kritik degisiklik, hata veya cozulmemis belirsizlik degerlendirilene kadar etkilenen uygulamali adimlarin ilerleme icin sunulmamasi. | INFERRED | — | PROPOSED |
| Insan Incelemesi | Ilgili sistemde uygulamali deneyimi olan bir kisinin motosiklet uyumu, kaynaklar, gorseller, araclar, riskler ve son kontrol acisindan rehberi degerlendirmesi. | USER | Belirli sertifika/unvan zorunlulugu varsayma | PROPOSED |
| Bagimsiz Ikinci Inceleme | Kritik rehberde ilk incelemeden ayri ikinci insan degerlendirmesi; kullanici acisindan ek guven sinyali. Tum kritik rehberlerde zorunlu oldugu karar degildir. | USER | `her kritik rehberde zorunlu iki reviewer` | PROPOSED |
| Islem Readiness | Kullanicinin belirli bir is icin benzer deneyim, arac/olcum bilgisi, onceki kayitlar ve on kosul anlayisi acisindan uygulamali adima hazir olma durumu. | INFERRED | Global `deneyimliyim` beyanina indirgeme | PROPOSED |
| Dogrulanmis Tamamlanma Kaydi | Bir bakim/islemin gercekten tamamlandigi ve gerekli son kontrollerinin dogrulandigi kayit; sonraki bakim zamanlamasinin dayandirildigi kayit. | INFERRED | `ertelendi`, `yarim`, `dogrulanamadi` | PROPOSED |
| Dis Islem Kaydi | Servis veya baska biri tarafindan yapilan ve kaynagi belirtilerek motosiklet gecmisine eklenen islem kaydi. | INFERRED | — | PROPOSED |
| Dogrulanmamis Dis Islem | Disarida yapildigi kaydedilen ancak yeterli kanit bulunmadigi icin dogrulanmis tamamlanmis islem gibi gosterilmemesi gereken kayit. | INFERRED | `fatura var = otomatik dogrulanmis` | PROPOSED |
| Bakim Onceligi | Birden fazla gecikmis bakim arasinda safety/kullanim etkisi, gecikme miktari ve dogrulanmis kosullara gore gerekceli siralama. | USER | Sadece `en eski tarih` | PROPOSED |
| Recovery / Guvenli Geri Donus | Hata, uyumsuzluk veya beklenmeyen durumda normal rehber akisini durdurup motosikleti guvenli hale getirme, kanit saklama ve uygun geri donus/profesyonel yardim yoluna ilerleme davranisi. | INFERRED | — | PROPOSED |
| Kanit Duzeyi | Bir gecmis kaydi veya icerik iddiasinin kullanici beyani, belge/fotograf destegi veya inceleme gibi hangi kanit seviyesine dayandigini gorunur ifade eden urun kavrami. | USER | Tum kaynaklari tek `verified/unverified` ikiligine zorlamak | PROPOSED |
| Belirsiz Bakim Takvimi | Guvenilir bakım araligi belirlenemediginde uydurma tarih/mesafe vermek yerine zamanlamanin kesin olmadigini acikca gosteren durum. | USER | Eski/uydurulmus araligi otomatik kullanma | PROPOSED |
| Bakim Istisnasi | Genel bakim planindan belirli motosiklet ozelligi veya dogrulanmis kullanim kosulu nedeniyle gerekceli bicimde ayrilan kural. | USER | Sebepsiz genel `agir kullanim` katsayisi | PROPOSED |
| Degisiklik Izi | Gecmis veya rehber bilgisinde eski/yeni deger, degisiklik zamani ve gerekce gibi tarihsel baglamin korunmasi. | USER | Sessiz overwrite | PROPOSED |
| Topluluk Katkisi | Kullanicinin kisisel alanindan ayri, bilincli secimle diger kullanicilara sunulan bilgi, fotograf, deneyim veya duzeltme onerisi. | USER | Kisisel not/fotografin otomatik yayini | PROPOSED |
| Resmi Rehber | Incelenmis ve urunun teknik yonlendirmesi olarak sunulan; topluluk deneyiminden acikca ayrilan rehber icerigi. | INFERRED | Community yorumu ile karistirma | PROPOSED |
| Ticari Tarafsizlik | Sponsor, odeme veya satis hedefinin teknik uygunluk, rehber icerigi veya alternatiflerin gorunurlugunu degistirmemesi ilkesi. | INFERRED | `sponsorlu = teknik olarak en uygun` | PROPOSED |
| Yol Kenari Kullanim Baglami | Garaj disi/acil durumda hizli belirti taramasi, oncelikli safety kontrolleri, kisa gorsel yonlendirme ve belirsizlik gorunurlugu ihtiyacinin arttigi kullanim durumu. | INFERRED | `safety adimlarini kisaltma modu` | PROPOSED |
| Cevrimdisi Islem Baglami | Baglanti olmadiginda indirilmis rehber, gorsel, safety uyarisi, kalinan adim ve kullanici gecmisi gibi islem surekliligi icin gereken urun baglami. | USER | — | PROPOSED |
| Veri Tasinabilirligi | Kullanicinin kendi motosiklet, tarihli islem, not ve fotograf verilerini anlasilir ve yeniden kullanilabilir bicimde urun disina alabilme beklentisi. | USER | Belirli teknik dosya formatini varsayma | PROPOSED |
| Guven Kirici Davranis / Trust-breaker | Uydurulmus teknik bilgi, gizlenen tehlike, hesaplar arasi veri karismasi, gecmisin sessiz kaybi veya reklam/ticari etkinin rehberi degistirmesi gibi kullanicinin urune teknik guvenini sona erdirebilecek davranis sinifi. | USER + INFERRED | — | PROPOSED |
| Readiness Yeniden Dogrulama | Readiness sonucu kullaniciyi durdurdugunda, salt oz-beyanla gate'i asmak yerine fotograf, olcum veya alternatif kontrol gibi yeni kanitla eksik kosulu yeniden degerlendirme davranisi. | USER | `ben yapabilirim` = override | PROPOSED |
| Override Edilemez Safety Gate | Kullanici kendisini yeterli gorse bile motosiklet/teknik bilgi, ekipman, ortam veya kritik pre-check eksiginde uygulamali ilerlemeyi kapali tutan urun kosulu. | USER | Serbest override | PROPOSED |
| Ogretici Icerik / Teaching-only Content | Bir sistem veya islemi ogrenmeye yarayan fakat belirli motosiklete uygulanabilir talimat olarak sunulmayan bilgi. Uygulamali adim gate'li olsa da erisilebilir kalabilir. | USER | `bu motosiklete uygula` talimati | PROPOSED |
| Profesyonel Escalation | Belirli islemde gerekli kosullar karsilanmadiginda kullaniciyi kalici yetersiz ilan etmeden profesyonel yardim secenegini sunan; ogrenme, belirti kaydi ve hazirlik destegini koruyan urun durumu. | USER + INFERRED | `sen bunu yapamazsin` | PROPOSED |
| Dogrulanmamis Kisisel Deneyim | Belirli motosiklette gozlemlenen fakat teknik olarak dogrulanmadigi icin resmi islem adimi statusu tasimayan community contribution. | USER | Resmi rehber adimi | PROPOSED |
| Contribution On Incelemesi | Tekrarlanan yanlis contribution gecmisinde yeni katkilarin dogrudan yayinlanmak yerine review'dan gecirilmesi durumu. | USER | Otomatik kalici yasak | PROPOSED |
| Kullanici Beyani | Kisinin kendisinin girdigi, ek bagimsiz kanit zorunlulugu tasimayan bilgi seviyesi. | USER | `verified` | PROPOSED |
| Belgeli | Kullanici beyanina ek supporting evidence tasiyan bilgi seviyesi. | USER | `reviewed` ile otomatik ayni sayma | PROPOSED |
| Incelenmis | Sunulan kanitin bir kontrol surecinden gectigini gosteren evidence seviyesi; tek basina motosiklet/islem uygunlugunun teyidi anlamina gelmez. | USER | `verified` ile otomatik ayni sayma | PROPOSED |
| Dogrulanmis — Semantik Rafine | Kaynak, ilgili motosiklet/islem uygunlugu, inceleme zamani ve karar gorunurlugunu iceren; fakat mutlak sonuc garantisi vermeyen guven ifadesi. | USER | `kesin sonuc`, `her versiyonda ayni` | PROPOSED |
| Kritik Safety Ozeti | Acik kritik konulari routine reminder'lardan ayirip zarar/aciliyet, gecikme ve onerilen ilk kontrol baglamiyla gosteren urun davranisi. | USER | Notification spam | PROPOSED |
| Paylasilan Motosiklet / Shared Motorcycle | Ayni motosiklet gecmisine birden fazla yetkili kisinin katkida bulundugu; attribution, edit trail, izin ve private-content sinirlarinin korundugu kullanim baglami. | USER + INFERRED | Anonim ortak kayit | PROPOSED |
| Ownership Transfer | Motosiklet satis/devrinde secilmis bakım history/kanitinin yeni sahibine aktarilmasi ile eski sahibin kisisel iceriginin ayrilmasi sureci. | USER | Tum kisisel icerigin otomatik devri | PROPOSED |
| Arsivlenmis Motosiklet | Aktif garajda olmayan fakat gecmisi korunmus, aranabilir ve yeniden aktive edilebilir motosiklet durumu. | USER | `silinmis motosiklet` | PROPOSED |
| Kritik Rehber Guncellik Siniri | Offline kritik rehberin son dogrulama zamanindan sonra uygulamali ilerlemenin yeniden online kontrol gerektirdigi product-safety esigi kavrami. Sayisal degeri henuz belirlenmemistir. | USER + INFERRED | Sabit gun/hafta varsayma | PROPOSED |
| Progressive First-use | Hesap/izin/uzun profil zorunlulugundan once kullanicinin motosiklet secip rehber deneyiminin degerini hizla gorebilmesi beklentisi. | INFERRED | Zorunlu uzun onboarding | PROPOSED |

## Approval Note

Bu glossary registry Phase 1 icin onaylanmistir. Batch 01-04 kullanici kanitlari terimleri rafine etmistir. Terimler `PROPOSED` kalir; nihai/LOCKED terminoloji karari henuz verilmemistir.
