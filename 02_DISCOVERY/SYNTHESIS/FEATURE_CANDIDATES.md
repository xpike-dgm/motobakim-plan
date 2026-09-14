# FEATURE CANDIDATES

Status: DRAFT

Discovery sirasinda ortaya cikan kullanici degeri odakli ozellik adaylari. Bunlar henuz kesin kapsam, teknik task veya mimari karar degildir.

| ID | Candidate | User Value | Evidence | Status |
|---|---|---|---|---|
| FC-001 | Motosiklet/varyant tanimlama ve rehber eslesme kontrolu | Yanlis yil/versiyon/donanim adimlarinin dogruymus gibi sunulmasini engellemek | Q008-Q009, Q026, Q036-Q039 | CANDIDATE |
| FC-002 | Rehber varyant dallari | Ayni islemde yil/versiyon/donanim farklarini dogru adimlarla ele almak | Q009, Q037 | CANDIDATE |
| FC-003 | Kaynak/provenance goruntuleme | Teknik bilginin hangi belge/surum/bolume dayandigini gorebilmek | Q010-Q011, Q041-Q044 | CANDIDATE |
| FC-004 | Kaynak celiskisi gorunumu ve critical hold | Celisen teknik bilgileri kaynaklariyla karsilastirabilmek ve cozulmeyen kritik farkta uygulamali ilerlemeyi durdurmak | Q011, Q044 | CANDIDATE |
| FC-005 | Gunluk dille belirti arama + motosiklet bolgesi/gorsel uzerinden bulma | Parca veya islem adini bilmeden dogru yolculuga girebilmek | Q012 | CANDIDATE |
| FC-006 | Islem karar karti / onizleme | Baslamadan amac, uygunluk, zorluk, risk, sure, maliyet, arac/parca ve kullanilabilirlik bilgisini gormek | Q013 | CANDIDATE |
| FC-007 | Deneyim seviyesine gore rehber gorunumu | Yeni kullaniciya ayrintili, deneyimli kullaniciya hizli anlatim sunarken guvenlik standardini korumak | Q007, Q014 | CANDIDATE |
| FC-008 | Tek hareket + gorsel + basari kontrolu adim modeli | Her adimda ne yapilacagini ve dogru sonucunun ne oldugunu anlamak | Q014-Q015 | CANDIDATE |
| FC-009 | Readiness kontrol listeleri | Isleme baslamadan arac/parca/sarf/PPE eksikligini fark etmek ve yari sokulmus durumda kalmamak | Q016-Q017 | CANDIDATE |
| FC-010 | Risk ve stop-gate sistemi | Kritik kosullarda kullaniciyi sadece uyarmak yerine ilerlemeyi durdurmak | Q018-Q021, Q034, Q045-Q053 | CANDIDATE |
| FC-011 | Kanit-temelli teshis akisi | Belirtiden kesinlik taklidi yapmadan guvenli kontrollerle olasiliklari daraltmak | Q022-Q024, Q056-Q058 | CANDIDATE |
| FC-012 | Adim ici yardim katmani | Takilinan adimda yakin plan, hareket yonu, sik hata ve detayli video/aciklama acmak | Q025 | CANDIDATE |
| FC-013 | `Benim motorum farkli` mismatch akisi | Rehber-gercek motosiklet uyusmazliginda ilerlemeyi durdurup dogru varyanta donmek | Q026, Q038-Q039 | CANDIDATE |
| FC-014 | Recovery / guvenli geri donus akisi | Hata veya beklenmeyen durumda motosikleti emniyete almak, kanit saklamak ve yardim yoluna gecmek | Q027 | CANDIDATE |
| FC-015 | Devam eden islem oturumu | Yarim kalan islemin adim, sokulu parca, olcum, fotograf, not ve rehber surumu baglamini korumak | Q028, Q059 | CANDIDATE |
| FC-016 | Zengin bakim/islem gecmisi | Aylar sonra ne yapildigini, neden yapildigini ve sonucunu kanitlarla gorebilmek | Q029-Q030 | CANDIDATE |
| FC-017 | Dogrulanmis tamamlanma ve provenance durumlari | Yarim/doğrulanamayan/ertelenen/disarida yapilan islemleri tamamlandi durumundan ayirmak | Q029, Q033, Q063 | CANDIDATE |
| FC-018 | Uretici tabanli sonraki bakim takibi | Kilometre/sure ve dogrulanmis tamamlanma kaydina gore siradaki bakimi izlemek | Q031, Q033, Q061 | CANDIDATE |
| FC-019 | Aciklanabilir ve ayarlanabilir hatirlatmalar | Hangi motosiklet/islem icin neden bildirim geldigini bilmek ve sikligini kontrol etmek | Q032-Q033, Q064 | CANDIDATE |
| FC-020 | Gecmis rehber surumu iliskisi | Gecmis/yarim islemin hangi rehber surumuyle yapildigini korumak | Q028-Q030, Q059-Q060 | CANDIDATE |
| FC-021 | Kullanici-dostu varyant ayristirma | Teknik kodlari ezbere istemeden motor hacmi/donanim/ilgili ozellik ve gerekirse gorselle dogru versiyona ulasmak | Q036-Q039 | CANDIDATE |
| FC-022 | Modifikasyon profili / uygunluk kontrolu | Sonradan degistirilmis sistemde fabrika rehberini yanlislikla uygulamamak | Q038-Q039 | CANDIDATE |
| FC-023 | Icerik review / yeniden inceleme / recall yasam dongusu | Guncellenen kaynak, kritik hata veya celiski durumunda guvenli icerik davranisi saglamak | Q040-Q044 | CANDIDATE |
| FC-024 | Reviewer guven/provenance gostergeleri | Rehberin hangi insan inceleme kapsamindan gectigini kullanici guveninin parcasi yapmak | Q040 | CANDIDATE |
| FC-025 | Kategoriye ozel high-consequence readiness | Fren, direksiyon, yakit, kaldirma, motor ici vb. islemlerde ozel on kosul ve stop-gate uygulamak | Q046-Q050 | CANDIDATE |
| FC-026 | Islem-bazli beceri/readiness degerlendirmesi | Sadece genel deneyim beyanina degil, is gecmisi/arac/olcum/on-kosul anlayisina gore uygun rehber seviyesine gecmek | Q051-Q052 | CANDIDATE |
| FC-027 | Ogrenme/hazirlik fallback yolu | Eksik beceri guvenli bicimde ogrenilebiliyorsa kritik uygulama yerine hazirlik egitimine donmek | Q050-Q052 | CANDIDATE |
| FC-028 | Dogrulanmis gorsel fallback | Tam varyant fotografi yoksa dogrulanmis cizim/isaretli sema kullanmak, belirsizlikte gorsel adimi kapatmak | Q054 | CANDIDATE |
| FC-029 | Guvenli esdeger kontrolu | Alternatif arac/sarf/ekipmanin gerekli fonksiyonel ve guvenlik kriterlerini karsiladigini aciklamak | Q053-Q055 | CANDIDATE |
| FC-030 | `Neden dogrulanamadi` teshis sonucu ve uzman handoff ozeti | Sonucsuz teshiste sahte kesinlik yerine yapilan kontrolleri ve belirsizligi tasinabilir ozetlemek | Q056-Q058 | CANDIDATE |
| FC-031 | Rehber surumu fark karsilastirmasi | Yarim iste yeni surum geldiyse kritik degisiklikleri devamdan once gormek | Q059 | CANDIDATE |
| FC-032 | Rehber geri cekme / yeniden kontrol uyarisi | Gecmis islem kullanilan rehber sonradan hatali bulunursa tarihsel kaydi koruyup gerekli kontrolu bildirmek | Q043, Q060 | CANDIDATE |
| FC-033 | Kullanim kosulu tabanli dogrulanmis bakim istisnalari | Yalniz motosiklete ozel kaynak destekliyorsa agir kullanim vb. kosullar nedeniyle bakimi gerekceli one almak | Q061 | CANDIDATE |
| FC-034 | Coklu motosiklet yonetimi | Her motosikletin gecmis/rehber/hatirlatmalarini ayri ve aktif baglami belirgin tutmak | Q062 | CANDIDATE |
| FC-035 | Dis servis/islem kaydi ve guven seviyesi | Baska biri tarafindan yapilan isi provenance ve kanitlarla kaydetmek, kanitsiz kaydi dogrulanmis gibi gostermemek | Q063 | CANDIDATE |
| FC-036 | Gecikmis bakim onceliklendirme | Birden fazla gecikmis isi guvenlik/kullanim etkisi ve gerekceyle siralamak | Q064 | CANDIDATE |
| FC-037 | Ucretsiz temel + premium zenginlestirme siniri | Kritik guvenlik ve temel bakim yeteneklerini ucretsiz korurken lisansli/zengin icerik ve kolayliklari ucretli deger adayi yapmak | Q065 | CANDIDATE |

## Important non-commitment

Bu adaylar kullanici ihtiyacini temsil eder. Hangi ozelliklerin MVP/sonraki faz oldugu, ekran yapisi, premium model veya teknik uygulanma bicimi bu asamada kararlastirilmaz.
