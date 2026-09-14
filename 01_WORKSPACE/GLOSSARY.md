# GLOSSARY

Status: APPROVED

Projede kullanilan domain terimlerinin tek anlamli sozlugu. `PROPOSED` terimler discovery sirasinda netlestirilebilir.

**Approved registry by user:** 2026-09-14  
**Important:** Belgenin `APPROVED` olmasi, her `PROPOSED` terimin nihai/LOCKED oldugu anlamina gelmez.

| Term | Canonical Meaning | Source Class | Synonyms / Avoid | Status |
|---|---|---|---|---|
| MotoBakim | Kullanicinin kendi motosikletindeki bakim, mekanik ve elektriksel islemleri anlamasina, uygulamasina ve gecmis/sonraki ihtiyaclarini takip etmesine yardimci olmayi amaclayan urun. | USER | — | PROPOSED |
| Motosiklete Ozel Bilgi | Genel motosiklet bilgisinden farkli olarak, kullanicinin gercek motosiklet konfigurasyonuna ve islemi etkileyen yil/versiyon/donanim farklarina uygun teknik bilgi ve yonlendirme. | USER | `genel bilgi` ile es anlamli kullanma | PROPOSED |
| Dogrulanmis Bilgi | Kullanicinin motosiklet/varyantiyla eslesen guvenilir kaynaga dayanan; kaynak surumu ve ilgili sayfa/bolum kaniti gorulebilen ve insan incelemesinden gecmis teknik bilgi. Kritik source conflict cozulmemisse tek kesin deger gibi sunulmaz. | USER | `AI tahmini`, `internette cok tekrarlandi` | PROPOSED |
| Asamali Rehber | Bir islemi hazirliktan tamamlanmasina kadar mantikli adimlarla yonlendiren urun deneyimi; yeni kullanici icin tek hareket + ilgili gorsel + basari kontrolu seviyesine inebilir. | USER | Atlamali anlatim | PROPOSED |
| Gorsel Yonlendirme | Parcayi/konumu tanimak icin gercek/isaretli fotograf; gizli baglantida cizim; hareket/sira kritikse video gibi desteklerin genel adi. | USER | — | PROPOSED |
| Bakim Gecmisi | Tamamlanan, yarim birakilan veya disarida yaptirilan bakım/islemlerin durum, kanit ve degisiklik iziyle kronolojik kaydi. | USER | Yalniz `tamamlanmis isler listesi` | PROPOSED |
| Sonraki Bakim Ihtiyaci | Uretici km/sure araliklari, dogrulanmis completion kaydi ve verified exceptions ile iliskili gelecek bakım ihtiyaci. | USER | Uydurma tahmini aralik | PROPOSED |
| Yeni / Az Deneyimli Kullanici | Teknik islemlerde sinirli deneyimi olan ve hareket-bazli ayrintili gorsel anlatima ihtiyac duyabilen hedef kullanici. | USER | `yeni motosiklet sahibi`ni otomatik deneyimsiz sayma | PROPOSED |
| Deneyimli Kullanici | Kisa checklist ve technical detail'e hizli ulasmak isteyen; safety/kritik dogrulamayi yine koruyan kullanici. | USER | — | PROPOSED |
| Motosiklet-Rehber Eslesmesi | Rehberin kullanicinin gercek motosikletinin yil/versiyon/donanim ve islemi etkileyen diger ozellikleriyle yeterli uygunlukta olmasi. | USER + INFERRED | `marka/model benziyor` | PROPOSED |
| Rehber Dali | Ayni islem icin yil/versiyon/donanima bagli farkli adim yolunun ayri ele alinmasi. | USER | — | PROPOSED |
| Ilgili Versiyon | Islem adimi, gerekli malzeme veya safety kontrolunu degistiren ozellikler acisindan gercek motosikletle eslesen varyant. | USER | — | PROPOSED |
| Kritik Dogrulama Adimi | Islemin guvenli/dogru ilerledigini kanitlamak icin deneyim seviyesinden bagimsiz atlanmamasi gereken kontrol. | USER | Opsiyonel kontrol | PROPOSED |
| Basari Kontrolu | Tek bir islem hareketi sonrasi beklenen dogru sonucun gozlem/olcum/baska kontrolle teyidi. | INFERRED | — | PROPOSED |
| Durdurma Noktasi | Mismatch, kritik arac/olcum eksigi veya sonucun dogrulanamamasi gibi nedenlerle application progression'in kesildigi durum. | INFERRED | Sadece `uyari` | PROPOSED |
| Guvenli Esdeger | Alternatif arac/sarf/ekipmanin gerekli olcu, uyum, dayanim, malzeme, islev ve safety ozelliklerini karsiladigi dogrulanmis secenek. | USER | Benzer gorunen alternatif | PROPOSED |
| Olasi Neden | Ariza belirtisini aciklayabilecek fakat henuz kanitla dogrulanmamis diagnosis candidate. | USER | Kesin teshis | PROPOSED |
| Neden Dogrulanamadi | Makul guvenli kontroller sonunda belirli neden yeterli kanitla dogrulanamadiginda kullanilan diagnosis sonucu. | USER | Rastgele parca degisimi | PROPOSED |
| Rehber Surumu | Bir islemin uygulandigi belirli guide version; yarim/gecmis iste referans. | INFERRED | — | PROPOSED |
| Kritik Duzeltme | Mevcut guide progression'ini guvenli bicimde etkileyip eski akisin durmasini gerektirebilecek degisiklik. | INFERRED | — | PROPOSED |
| Rehber Askiya Alma | Kritik degisiklik/hata/belirsizlik incelenene kadar etkilenen application adimlarinin sunulmamasi. | INFERRED | — | PROPOSED |
| Insan Incelemesi | Ilgili sistemde uygulamali deneyimi olan kisinin uyum/kaynak/gorsel/arac/risk/son-kontrol acilarindan rehberi degerlendirmesi. | USER | Sertifika/unvan zorunlulugu varsayma | PROPOSED |
| Bagimsiz Ikinci Inceleme | Ilk review'dan ayri ikinci insan degerlendirmesi; ek guven sinyali, evrensel zorunluluk degil. | USER | Her kritik rehberde zorunlu iki reviewer | PROPOSED |
| Islem Readiness | Kullanicinin belirli is icin deneyim, arac/olcum bilgisi ve on-kosul anlayisi acisindan application'a hazir olma durumu. | INFERRED | Global `deneyimliyim` | PROPOSED |
| Dogrulanmis Tamamlanma Kaydi | Islemin gercekten tamamlandigina ve gerekli son kontrollerin yapildigina dayanak olan history kaydi. | INFERRED | `ertelendi`, `yarim` | PROPOSED |
| Dis Islem Kaydi | Servis veya baska biri tarafindan yapilan ve provenance ile history'ye eklenen islem kaydi. | INFERRED | — | PROPOSED |
| Dogrulanmamis Dis Islem | Yapildigi bildirilen fakat yeterli kanit olmadigi icin verified completion gibi sunulmayan dis islem. | INFERRED | `fatura = verified` | PROPOSED |
| Bakim Onceligi | Gecikmis islemleri safety/kullanim etkisi, gecikme ve verified conditions ile gerekceli siralama. | USER | Sadece `en eski tarih` | PROPOSED |
| Recovery / Guvenli Geri Donus | Hata/mismatch/beklenmeyen durumda normal akisi durdurup motosikleti guvenli hale getirme ve uygun yardim yoluna ilerleme. | INFERRED | — | PROPOSED |
| Kanit Duzeyi | Bir kayit veya content claim'in kullanici beyani, belge/fotograf veya review gibi hangi kanita dayandigini anlatan product concept. | USER | Tek `verified/unverified` ikiligi | PROPOSED |
| Belirsiz Bakim Takvimi | Reliable interval bulunamadiginda uydurma tarih/mesafe yerine uncertainty'nin acik gosterildigi durum. | USER | Eski/uydurulmus interval | PROPOSED |
| Bakim Istisnasi | Genel planin verified motorcycle feature veya usage condition nedeniyle gerekceli olarak degistigi kural. | USER | Sebepsiz `agir kullanim` katsayisi | PROPOSED |
| Degisiklik Izi | Eski/yeni deger, degisiklik zamani ve gerekce gibi tarihsel audit context. | USER | Sessiz overwrite | PROPOSED |
| Topluluk Katkisi | Kisisel alandan ayri, explicit secimle diger kullanicilara sunulan bilgi/fotograf/deneyim/duzeltme. | USER | Kisisel notun otomatik yayini | PROPOSED |
| Resmi Rehber | Incelenmis ve urunun technical guidance'i olarak sunulan; community deneyiminden ayrilan rehber. | INFERRED | Community yorumu | PROPOSED |
| Ticari Tarafsizlik | Sponsor/odeme/satis hedefinin technical fit, guide content veya alternatives visibility'yi degistirmemesi ilkesi. | INFERRED | `sponsorlu = en uygun` | PROPOSED |
| Yol Kenari Kullanim Baglami | Garaj disinda hizli diagnosis, safety-first kontrol ve belirsizlik gorunurlugu ihtiyacinin arttigi context. | INFERRED | Safety'yi kisaltma modu | PROPOSED |
| Cevrimdisi Islem Baglami | Baglanti yokken indirilmis guide/gorsel/safety/progress/history ile islem surekliligi. | USER | — | PROPOSED |
| Veri Tasinabilirligi | Kullanicinin kendi motorcycle/history/note/photo verisini anlasilir ve yeniden kullanilabilir bicimde disari alma beklentisi. | USER | Belirli teknik format varsayma | PROPOSED |
| Guven Kirici Davranis / Trust-breaker | Uydurma bilgi, gizlenen risk, cross-account data mix, silent history loss veya commercial influence gibi trust'i bozan davranis sinifi. | USER + INFERRED | — | PROPOSED |
| Readiness Yeniden Dogrulama | Readiness blokajini salt oz-beyanla degil yeni fotograf/olcum/alternatif kontrol kanitiyla yeniden degerlendirme. | USER | `ben yapabilirim` = override | PROPOSED |
| Override Edilemez Safety Gate | Critical match/info/equipment/environment/pre-check eksiginde user self-assertion'dan bagimsiz application'i kapali tutan kosul. | USER | Serbest override | PROPOSED |
| Ogretici Icerik / Teaching-only Content | Sistemi/konuyu ogreten fakat belirli motosiklete current application instruction olarak sunulmayan bilgi. | USER | `bu motosiklete uygula` | PROPOSED |
| Profesyonel Escalation | Belirli islemde dis yardimi secenek olarak sunan fakat kullaniciyi kalici yetersiz ilan etmeyen product state. | USER + INFERRED | `sen yapamazsin` | PROPOSED |
| Dogrulanmamis Kisisel Deneyim | Teknik olarak verify edilmedigi icin official step statusu tasimayan community experience. | USER | Resmi rehber adimi | PROPOSED |
| Contribution On Incelemesi | Tekrarlanan yanlis contribution sonrasi yeni katkilarin publish oncesi review'a alinmasi. | USER | Otomatik permanent ban | PROPOSED |
| Kullanici Beyani | Kisinin kendisinin girdigi, ek bagimsiz kanit zorunlulugu tasimayan evidence level. | USER | Verified | PROPOSED |
| Belgeli | Kullanici beyanina supporting evidence eklenmis level. | USER | Reviewed ile otomatik ayni | PROPOSED |
| Incelenmis | Sunulan kanitin bir review surecinden gectigini gosteren level; tek basina motorcycle/application fit teyidi degil. | USER | Verified ile ayni | PROPOSED |
| Dogrulanmis — Semantik Rafine | Hangi claim'in kaynak/evidence/review ile teyit edildigini anlatan; mutlak sonuc garantisi vermeyen ifade. | USER | `kesin sonuc`, `her versiyonda ayni` | PROPOSED |
| Kritik Safety Ozeti | Kritik acik konulari routine reminders'dan ayirip zarar/aciliyet, gecikme ve ilk action ile gosteren davranis. | USER | Notification spam | PROPOSED |
| Paylasilan Motosiklet / Shared Motorcycle | Birden fazla yetkili kisinin katkida bulundugu; attribution/edit trail/permission/private-content sinirlari korunan context. | USER + INFERRED | Anonim ortak kayit | PROPOSED |
| Ownership Transfer | Motosiklet devrinde secilmis vehicle history ile eski owner personal content'inin ayrildigi surec. | USER | Tum personal content'in otomatik devri | PROPOSED |
| Arsivlenmis Motosiklet | Active garage'da olmayan fakat history'si korunmus ve yeniden active edilebilir motorcycle state. | USER | Silinmis motosiklet | PROPOSED |
| Kritik Rehber Guncellik Siniri | Application-critical guide claim'inin yeniden online check gerektirdigi freshness gate kavrami; numeric degeri belirlenmemis. | USER + INFERRED | Sabit gun/hafta varsayma | PROPOSED |
| Progressive First-use | Account/permission/long-profile zorunlulugundan once segmentin kendi ilk product value'sunu gorebilmesi. | INFERRED | Zorunlu uzun onboarding | PROPOSED |
| Self-remediation | Blocked readiness sonrasi external help'ten once eksik kosulu learning/preparation/equipment/new evidence ile giderme yolu. | USER | Professional help tek cikis | PROPOSED |
| Re-entry Validation | Daha once stop edilmis application'a geri donmeden ilgili equipment/match/critical checks'in yeniden dogrulanmasi. | USER | Onceki stop'u sadece beyanla silme | PROPOSED |
| Professional Recommendation | Mandatory closure olmayan, kullanicinin degerlendirebilecegi external-help onerisi. | USER | `application kesin kapali` ile ayni | PROPOSED |
| Mandatory Application Closure | Unverified critical condition nedeniyle motorcycle-facing application steps'in acilamadigi safety state. | USER | Tavsiye seviyesi | PROPOSED |
| Independent Transferred Record | Kaynak owner kopyasindan ayri olarak baskasina aktarilmis ve kaynak deletion'dan otomatik etkilenmemesi beklenen record. | USER + INFERRED | Kaynakla ayni mutable kopya | PROPOSED |
| De-identified Review Trace | Contribution withdrawal sonrasi contributor identity olmadan safety/review history amaciyla korunabilecek inceleme izi. | USER | Public contribution'in aynen tutulmasi | PROPOSED |
| Context-specific Evidence Semantics | Ortak evidence vocabulary korunurken hangi claim'in verify edildiginin domain'e gore ayrilmasi. | USER + INFERRED | Tek global `verified` anlami | PROPOSED |
| Partial-history Disclosure | Ownership transfer'da aktarilan kayitlarin complete history olmadigini, covered period ve gaps ile aciklama. | USER | `tam history` izlenimi | PROPOSED |
| Historical Correction Proposal | Transfer sonrasi record'u silent overwrite etmek yerine attributed/reviewable duzeltme veya yeni bilgi onerisi. | USER | Sessiz degistirme | PROPOSED |
| Record-only Owner | Ana degeri guide uygulamak yerine history, maintenance schedule ve reminder tracking'den alan owner context'i. | USER | Self-service kullanmak zorunda | PROPOSED |
| Hobby Helper | Baskasinin motosikletinde owner izniyle yardim eden fakat paid professional service rolu tasimayan contributor. | USER | Professional ile ayni rol | PROPOSED |
| Paid Service Record | Actor/evidence yaninda service/document information da tasiyan ucretli islem kaydi. | USER | Rol = otomatik verified | PROPOSED |
| Core Completion Boundary | Free user'in temel islemi guvenli bicimde bastan sona tamamlamasi icin paywall disinda kalmasi gereken product-value siniri. | USER + INFERRED | Dolayli paywall | PROPOSED |
| Reasonable History | Core kullanimin longitudinal trust'ini koruyan motorcycle, work, date/km, actor, outcome, safety notes, evidence level ve correction history kapsamidir; exact numeric quota degildir. | USER | Sadece `bir miktar kayit` | PROPOSED |
| Critical Freshness Scope | Eski kalmasi application safety/accuracy'yi etkiledigi icin re-check gerektiren claim kategorileri. | USER + INFERRED | Tum eski icerigi ayni gate'lemek | PROPOSED |
| Stale Teaching-only Reference | Current application instruction olmayan fakat learning/risk/history icin erisilebilir kalan eski guide content. | USER | Current instruction gibi sunma | PROPOSED |
| Reviewable Critical Confirmation | Voice/easy interaction yanlis anlasilsa bile explicit ve sonradan incelenebilir safety-critical teyit. | USER + INFERRED | Tek voice input | PROPOSED |
| Account-light Preview | Persistence/collaboration baslamadan once product value'nun account zorunlulugu olmadan sinirli deneyimi. | INFERRED | Unlimited accountless usage | PROPOSED |
| Expanded Evidence Archive | Islemi anlamak/dogrulamak icin gereken temel kanitin otesindeki high-volume/high-resolution photo, long video ve genis document archive degeri. | USER + INFERRED | Basic history ile ayni sayma | PROPOSED |
| Motorcycle Isolation | Bir motosikletin history, mileage, reminders ve active-work state'inin diger motosikleti etkilememesi ilkesi. | USER + INFERRED | Cross-bike state karismasi | PROPOSED |
| Advanced Garage | Basic motorcycle isolation'in otesindeki cross-bike analysis, bulk planning, richer collaboration ve large-archive search degeri. | USER | Basit multi-bike ayrimi | PROPOSED |
| Disputed Historical Claim | Ayni tarihsel olay hakkinda provenance'i korunan ve unresolved bicimde yan yana bulunan celisen iddialar. | USER + INFERRED | Tek tarafi sessizce truth yapmak | PROPOSED |
| Transfer Coverage | Ownership transfer ile gelen history'nin hangi owner/donem/kayitlari kapsadigini ve hangi donemlerin bilinmedigini gosteren kapsam. | USER + INFERRED | Partial history'yi complete gostermek | PROPOSED |
| Evidence Withdrawal Trace | Supporting evidence geri cekildiginde historical claim ile withdrawal arasindaki baglantinin gorunur kalmasi. | USER + INFERRED | Kanit yokken eski verified statusu gizlice koruma | PROPOSED |
| Risk-Adaptive Evidence Explanation | Evidence/provenance ayrintisinin risk, safety impact ve dispute seviyesine gore farkli derinlikte sunulmasi. | USER + INFERRED | Her yerde ayni uzunlukta trust metni | PROPOSED |
| Physical-State Remapping | Interrupted veya materially changed guide durumunda motosikletin mevcut fiziksel halinin devamdan once guvenli bir guide noktasina yeniden eslestirilmesi. | USER + INFERRED | Sadece son gorulen step'e donmek | PROPOSED |
| Resume Revalidation | Active-repair interruption sonrasi current safety/physical conditions ve last completed step'in yeniden dogrulanmasi. | USER + INFERRED | Onceki confirmation'i otomatik tasimak | PROPOSED |
| Disputed Service Completion | Service document ile owner evidence/observation celistigi icin islemin gercekten tamamlanip tamamlanmadiginin unresolved kaldigi history state. | USER + INFERRED | Belge var = kesin tamamlandi | PROPOSED |

## Approval Note

Bu glossary registry Phase 1 icin onaylanmistir. Batch 01-06 kullanici kanitlari terimleri rafine etmistir. Terimler `PROPOSED` kalir; nihai/LOCKED terminoloji karari henuz verilmemistir.
