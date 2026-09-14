# BUSINESS RULES

Status: DRAFT

Bu kurallar kullanici kanitindan turetilen teknik olmayan urun davranis kurallaridir. Kesin teknik implementasyon degildir.

| ID | Rule | Applies To | Exceptions / Notes | Source | Status |
|---|---|---|---|---|---|
| BR-001 | Motosiklete ozel bir rehber, kullanicinin gercek motosiklet konfigurasyonuyla yeterli eslesme kurulmadan motosiklete ozelmis gibi sunulamaz. | Rehber secimi / ilerleme | Evrensel sabit kimlik seti yok; islemi etkileyen versiyon farki esastir | Q008-Q009, Q026, Q036-Q039 | CONFIRMED |
| BR-002 | Yil, versiyon veya donanim islemi degistiriyorsa farkli adimlar ayri rehber dallari olarak ele alinmalidir. | Rehber varyantlari | — | Q009, Q037 | CONFIRMED |
| BR-003 | Eslesme belirsizse yakin yil veya varyantin adimlari dogruymus gibi kullanilarak ilerlenemez. | Rehber guvenligi | — | Q009, Q026, Q037 | CONFIRMED |
| BR-004 | Dogrulanmis teknik bilgi, kullanicinin motosiklet/varyantina uygun guvenilir kaynaga dayanmalidir; internet tekrar sayisi tek basina dogrulama degildir. | Teknik icerik | Kaynak turleri amac/guncellik/uygulanabilirlikle degerlendirilir | Q010, Q041 | CONFIRMED |
| BR-005 | Kullanici kaynak surumu ve ilgili sayfa/bolum kanitini gorebilmelidir. | Icerik provenance | Gosterim seviyesi tasarim asamasinda | Q010 | CONFIRMED |
| BR-006 | Kritik kaynak celiskisi cozulmemisse sistem tek bir teknik degeri secip kullaniciyi uygulamali ilerlemeye zorlayamaz. | Kaynak celiskisi | Celismeyen hazirlik/guvenlik bilgisi gosterilebilir | Q011, Q044 | CONFIRMED |
| BR-007 | Deneyim seviyesi rehberin ayrinti/hizini degistirebilir fakat guvenlik uyarilari ve kritik dogrulama adimlarini kaldiramaz. | Rehber sunumu | — | Q007, Q014 | CONFIRMED |
| BR-008 | Yeni/az deneyimli kullanici icin temel adim, atlanan ara hareket birakmadan uygulanabilir ayrintida olmalidir. | Rehber adimlari | Ayrinti standardi islem turune gore derinlesebilir | Q014 | CONFIRMED |
| BR-009 | Islem oncesi zorunlu arac/parca/ekipman eksikligi, kullanici motosikleti yari sokulmus durumda birakmadan once gorunur olmalidir. | Readiness | — | Q016-Q017 | CONFIRMED |
| BR-010 | Zorunlu ozel arac veya parca yoksa ilgili uygulamali adima gecilmemelidir. | Readiness / ilerleme | Dogrulanmis guvenli esdeger basit yardimci araclarda mumkun olabilir | Q017, Q053 | CONFIRMED |
| BR-011 | Kritik guvenlik riski islem baslamadan once ve ilgili adimdan hemen once gosterilmelidir. | Safety warnings | Genel uyari spam'i kritik uyarilari golgelememeli | Q018 | CONFIRMED |
| BR-012 | Guvenlik uyarisi riskin ne oldugunu, nasil onlenecegini ve hangi kosulda durulacagini somut olarak aciklamalidir. | Safety warnings | — | Q018 | CONFIRMED |
| BR-013 | Rehber-varyant uyusmazligi, hasarli parca, gerekli olcum/arac eksikligi, beklenmeyen baglanti veya kritik sonucun dogrulanamamasi ilerlemeyi durdurma nedenidir. | Stop-gate | Islem sinifi bazli ek kurallar olabilir | Q019, Q034, Q045-Q050 | CONFIRMED |
| BR-014 | Yuksek-sonuclu alanlarda belirsizlikle ilerleme onerilmemelidir; kategoriye ozel on kosullar ve stop-gate kurallari uygulanmalidir. | High-consequence work | Fren, direksiyon/on takim, yakit, kaldirma ve motor ici icin Batch 02 kaniti var; yuksek gerilim detaylari acik | Q019, Q046-Q050 | CONFIRMED |
| BR-015 | Olasi ariza nedeni kesin teshis olarak sunulamaz; dogrulanma durumu acikca belirtilmelidir. | Diagnosis | — | Q023-Q024 | CONFIRMED |
| BR-016 | Teshis olasiligi, onu destekleyen belirti/kontrol/beklenen sonucla ilerlemeli ve yeni kanita gore daralmalidir. | Diagnosis | Sabit nicel test sayisi varsayilmaz | Q022-Q024, Q056-Q058 | CONFIRMED |
| BR-017 | Kanit olmadan parca degisimi veya motosikletin guvenle kullanilabilecegi onerilmemelidir. | Diagnosis / safety | — | Q024, Q057-Q058 | CONFIRMED |
| BR-018 | Rehber gercek motosikletle uyusmuyorsa normal ilerleme durmali, fark kaydedilebilmeli ve varyant/eslesme yeniden belirlenmelidir. | Mismatch recovery | Modifiye sistemler de ayni ilkeye tabidir | Q026, Q038-Q039 | CONFIRMED |
| BR-019 | Hata veya beklenmeyen davranista normal ilerleme durmali; guvenliyse emniyete alma ve dokunulmaması gereken alanlar gosterilmelidir. | Recovery | — | Q027 | CONFIRMED |
| BR-020 | Yarim kalan islem, son tamamlanan adimla birlikte sokulu parcalar, olcumler, fotograflar/notlar ve rehber surumu gibi baglamini korumalidir. | Interrupted work | — | Q028, Q059 | CONFIRMED |
| BR-021 | Degismis rehber, devam eden yarim isleme sessizce uygulanmamalidir. | Guide versioning | Kritik duzeltmede eski akis durmali; fiziksel mevcut durum yeni rehberle yeniden eslestirilmelidir | Q028, Q059 | CONFIRMED |
| BR-022 | Yarim kalan veya sonucu dogrulanamayan islem tamamlanmis olarak isaretlenemez. | History / completion | — | Q029 | CONFIRMED |
| BR-023 | Disarida yaptirilan islem kaydedilebilir; erteleme ise tamamlanma olarak kabul edilmez. | Maintenance history | Kanitsiz dis islem dogrulanmis gibi gosterilmez | Q033, Q063 | CONFIRMED |
| BR-024 | Sonraki bakim hesabi dogrulanmis tamamlanma kaydindan devam etmelidir. | Maintenance tracking | Dis kaydin dogrulanma standardi acik | Q033, Q063 | CONFIRMED |
| BR-025 | Bakim zamanlamasinda motosiklete uygun uretici kilometre/sure araliklari temel alinmali ve hangisi once dolarsa o izlenmelidir. | Maintenance tracking | Kullanim kosulu ancak motosiklete uygun dogrulanmis bilgi varsa araligi degistirebilir | Q031, Q061 | CONFIRMED |
| BR-026 | Dogrulanmamis bakim araligi uretilmemelidir. | Maintenance tracking | Genel agir-kullanim katsayisi uydurulamaz | Q031, Q061 | CONFIRMED |
| BR-027 | Hatirlatma ertelemesi yeni tarih/gerekceyle saklanabilir ancak islemi yapilmis sayamaz. | Reminders | — | Q033 | CONFIRMED |
| BR-028 | Urun dogrulanmamis teknik deger uyduramaz, belirsiz arizayi kesin teshis gibi sunamaz veya tehlikeli isin basarisini garanti edemez. | Tum urun | — | Q035 | CONFIRMED |
| BR-029 | Modifiye bir sistem icin fabrika rehberinin uygun oldugu otomatik varsayilamaz. | Rehber eslesmesi | Modifikasyon kullanicidan/gorselden ayristirilmaya calisilir | Q038-Q039 | CONFIRMED |
| BR-030 | Bir fark islem adimini, gerekli malzemeyi veya guvenlik kontrolunu degistiriyorsa ilgili versiyon kesinlesmeden rehber baslamamalidir. | Rehber gating | Kullanici teknik kodlari ezbere bilmek zorunda degildir | Q036-Q037 | CONFIRMED |
| BR-031 | Insan incelemesi ilgili sistemde uygulamali deneyim ve rehberin uyum/kaynak/gorsel/arac/risk/son-kontrol acilarindan degerlendirilmesini icermelidir. | Content governance | Belirli sertifika/unvan zorunlulugu kanitlanmadi | Q040 | CONFIRMED |
| BR-032 | Kritik rehberde bagimsiz ikinci inceleme ek guven sinyalidir; tum kritik rehberlerde zorunlu oldugu henuz kesin karar degildir. | Content governance | PROPOSED operational implication degil, kullanici beklentisi siniri | Q040 | CONFIRMED |
| BR-033 | Kaynak guncellemesi veya yeni uretici duzeltmesi kritik degisiklik yaratabiliyorsa rehber yeniden incelenmeli ve etkilenen uygulamali adimlar degerlendirme bitene kadar askiya alinmalidir. | Content lifecycle | — | Q042 | CONFIRMED |
| BR-034 | Kritik rehber hatasi bulunursa rehber durdurulmali, etkilenen kullanicilar etkilenen adim/gerekli kontrol/yardim yolu ile uyarilmali ve gecmis kayitlar silinmemelidir. | Content recall | Bildirim teknigi sonraki asamalar | Q043 | CONFIRMED |
| BR-035 | Yeni rehber surumu degisiklik gerekcesiyle yayimlanmali; eski surum tarihsel kayitlarda korunmalidir. | Versioning / provenance | — | Q042, Q059-Q060 | CONFIRMED |
| BR-036 | Readiness yalniz kullanicinin `deneyimliyim` beyanina dayanamaz; benzer is gecmisi, arac/olcum bilgisi, onceki kayitlar ve on kosul anlayisi dikkate alinmalidir. | Readiness | Degerlendirme modelinin tasarimi sonraki asamalara ait | Q051 | CONFIRMED |
| BR-037 | Eksik beceri guvenli bicimde ogrenilebiliyorsa temel hazirliga yonlendirme yapilabilir; ciddi sonuclu veya uzman dogrulamasi gerektiren kritik adim acilmamalidir. | Readiness / learning | — | Q052 | CONFIRMED |
| BR-038 | Guvenli esdeger, olcu/uyum/dayanim/malzeme/islev/guvenlik gereklilikleri dogrulanmadan onerilemez. | Tools/materials | Hassas olcum, dogru sikma, guvenli kaldirma zorunlu ekipmanlarinda alternatif olmayabilir | Q053, Q055 | CONFIRMED |
| BR-039 | Tam varyant fotografi yoksa dogrulanmis cizim/isaretli sema kullanilabilir; baska motosiklet fotografi ayniymis gibi sunulamaz ve fark belirsizse gorsele dayali adim baslatilamaz. | Visual guidance | — | Q054 | CONFIRMED |
| BR-040 | Bir neden `en olasi` diye one cikmadan once birden fazla ayirt edici kanit onu desteklemeli ve alternatifler degerlendirilmis olmalidir. | Diagnosis confidence | Sabit sayisal esik degildir | Q056 | CONFIRMED |
| BR-041 | Esit/benzer guclu teshis olasiliklari ayri tutulmali; ayristirici guvenli kontrol yoksa rastgele parca degisimi onerilmemelidir. | Diagnosis | — | Q057 | CONFIRMED |
| BR-042 | Makul kontroller sonrasinda neden dogrulanamazsa `Neden dogrulanamadi` sonucu kabul edilebilir; kontroller ve guvenli kullanim belirsizligi ozetlenebilmelidir. | Diagnosis / escalation | Uzman aktarim sekli tasarim konusu | Q058 | CONFIRMED |
| BR-043 | Tamamlanmis gecmis islem, rehber sonradan degistigi/geri cekildigi icin sessizce yeniden yazilamaz; kullanilan surum korunmalidir. | History/versioning | Gerekirse yeniden kontrol uyarisi eklenebilir | Q060 | CONFIRMED |
| BR-044 | Kullanim kosulu bakim araligini ancak motosiklete uygun dogrulanmis bilgi bunu destekliyorsa degistirebilir; degisiklik gerekcesi gorunur olmalidir. | Maintenance exceptions | Kosul bilgisi istege bagli toplanabilir | Q061 | CONFIRMED |
| BR-045 | Birden fazla motosikletin gecmis, rehber ve hatirlatma baglamlari ayrilmalidir; aktif motosiklet her zaman anlasilir olmalidir. | Multi-motorcycle | — | Q062 | CONFIRMED |
| BR-046 | Dis islem kaydi provenance ile saklanmali; kanit yoksa dogrulanmis islem gibi gosterilmemelidir. | History trust | Fatura tek basina otomatik dogrulama sayilmaz | Q063 | CONFIRMED |
| BR-047 | Birden fazla gecikmis bakimda guvenlik/kullanim etkisi, sonra gecikme ve ilgili kullanim kosullari dikkate alinmali; oncelik gerekcesi aciklanmalidir. | Maintenance priority | Sadece en eski tarih en onemli sayilamaz | Q064 | CONFIRMED |
| BR-048 | Kritik guvenlik bilgisi ucret duvarinin arkasina saklanmamalidir. | Monetization trust boundary | Fiyatlandirma/paket modeli karari degildir | Q065 | CONFIRMED |
| BR-049 | Temel dogrulanmis rehberler, bakim kaydi ve temel hatirlatmalar kullanici beklentisine gore ucretsiz temel yeteneklerdir. | Monetization baseline | `Temel rehber` kapsam ayrintisi daha sonra netlesebilir | Q065 | CONFIRMED |

## Rules needing more discovery

- Kullanici-dostu kimlik/fotograf yetersiz kalirsa ek varyant kaniti ve kullanici akisi
- Yuksek gerilim ve diger kapsanmayan yuksek-sonuclu kategorilerin ozel stop-gate kosullari
- Notification cadence'in bakim onceligine/riskine gore nasil degisecegi
- Yanlis/eksik gecmis kaydi duzeltme ve edit history
- Dis islemi `dogrulanmis` saydiran kanit dereceleri
- Degistirilmis parca / uretici ozel istisnalarinin bakim zamanlamasina etkisi
- Kullanici/topluluk katkisi ve moderation kurallari
- Sosyal/ticari ozelliklerin urun siniri
- Yaklasik sure ve maliyet bilgisinin guvenilir sunum siniri
- Monetization model/paket tercihi; sponsor/ticari etkinin teknik guvene etkisi
