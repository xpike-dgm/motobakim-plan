# BUSINESS RULES

Status: DRAFT

Bu kurallar kullanici kanitindan turetilen teknik olmayan urun davranis kurallaridir. Kesin teknik implementasyon degildir.

| ID | Rule | Applies To | Exceptions / Notes | Source | Status |
|---|---|---|---|---|---|
| BR-001 | Motosiklete ozel rehber, gercek motosiklet konfigurasyonuyla yeterli eslesme kurulmadan motosiklete ozelmis gibi sunulamaz. | Rehber secimi / ilerleme | Sabit evrensel kimlik seti yok | Q008-Q009, Q026, Q036-Q039 | CONFIRMED |
| BR-002 | Yil/versiyon/donanim islemi degistiriyorsa farkli adimlar ayri rehber dallari olarak ele alinmalidir. | Rehber varyantlari | — | Q009, Q037 | CONFIRMED |
| BR-003 | Eslesme belirsizse yakin yil/varyant adimlari dogruymus gibi kullanilarak ilerlenemez. | Rehber guvenligi | — | Q009, Q026, Q037 | CONFIRMED |
| BR-004 | Dogrulanmis teknik bilgi motosiklet/varyanta uygun guvenilir kaynaga dayanmalidir; internet tekrar sayisi tek basina dogrulama degildir. | Teknik icerik | Kaynaklar amac/guncellik/uygulanabilirlikle degerlendirilir | Q010, Q041 | CONFIRMED |
| BR-005 | Kullanici kaynak surumu ve ilgili sayfa/bolum kanitini gorebilmelidir. | Icerik provenance | Gosterim tasarimi sonraki asama | Q010 | CONFIRMED |
| BR-006 | Cozulmemis kritik kaynak celiskisinde tek bir deger secilip uygulamali ilerleme yaptirilamaz. | Kaynak celiskisi | Celismeyen hazirlik/safety bilgisi gosterilebilir | Q011, Q044 | CONFIRMED |
| BR-007 | Deneyim seviyesi rehber ayrinti/hizini degistirebilir fakat safety ve kritik dogrulamayi kaldiramaz. | Rehber sunumu | — | Q007, Q014 | CONFIRMED |
| BR-008 | Yeni/az deneyimli kullanici icin temel adim atlanan ara hareket birakmadan uygulanabilir ayrintida olmalidir. | Rehber adimlari | — | Q014 | CONFIRMED |
| BR-009 | Zorunlu arac/parca/ekipman eksigi motosiklet yari sokulmeden once gorunur olmalidir. | Readiness | — | Q016-Q017 | CONFIRMED |
| BR-010 | Zorunlu ozel arac/parca yoksa ilgili uygulamali adima gecilmez. | Readiness | Dogrulanmis guvenli esdeger basit yardimci araclarda mumkun olabilir | Q017, Q053 | CONFIRMED |
| BR-011 | Kritik safety riski islem basinda ve ilgili adimdan hemen once gosterilmelidir. | Safety warnings | Genel uyari spam'i kritik uyariyi golgelememeli | Q018 | CONFIRMED |
| BR-012 | Safety uyarisi risk, onleme ve stop kosulunu somut aciklamalidir. | Safety warnings | — | Q018 | CONFIRMED |
| BR-013 | Varyant uyusmazligi, hasar, gerekli olcum/arac eksigi, beklenmeyen baglanti veya kritik sonucun dogrulanamamasi stop nedenidir. | Stop-gate | Kategoriye ozel ek kurallar olabilir | Q019, Q034, Q045-Q050 | CONFIRMED |
| BR-014 | High-consequence alanlarda belirsizlikle ilerleme onerilmemeli; kategoriye ozel on kosul/stop-gate uygulanmalidir. | High-consequence work | — | Q019, Q046-Q050 | CONFIRMED |
| BR-015 | Olasi ariza nedeni kesin teshis gibi sunulamaz. | Diagnosis | — | Q023-Q024 | CONFIRMED |
| BR-016 | Teshis olasiligi belirti/kontrol/beklenen sonuc kanitiyla ilerlemeli ve yeni kanita gore daralmalidir. | Diagnosis | Sabit nicel test sayisi yok | Q022-Q024, Q056-Q058 | CONFIRMED |
| BR-017 | Kanit olmadan parca degisimi veya guvenli kullanim onerilmemelidir. | Diagnosis / safety | — | Q024, Q057-Q058 | CONFIRMED |
| BR-018 | Rehber gercek motosiklet/modifikasyonla uyusmuyorsa normal ilerleme durup uygunluk yeniden kurulmalidir. | Mismatch recovery | — | Q026, Q038-Q039 | CONFIRMED |
| BR-019 | Hata/beklenmeyen davranista normal ilerleme durmali; guvenliyse emniyete alma/dokunmama bilgisi sunulmalidir. | Recovery | — | Q027 | CONFIRMED |
| BR-020 | Yarim islem; adim, sokulu parca, olcum, fotograf/not ve rehber surumu baglamini korumalidir. | Interrupted work | — | Q028, Q059 | CONFIRMED |
| BR-021 | Degismis rehber devam eden isleme sessizce uygulanamaz. | Guide versioning | Kritik duzeltmede eski akis durur | Q028, Q059 | CONFIRMED |
| BR-022 | Yarim veya sonucu dogrulanamayan islem tamamlandi olarak isaretlenemez. | History / completion | — | Q029 | CONFIRMED |
| BR-023 | Disarida yaptirilan islem kaydedilebilir; erteleme completion degildir. | History | Kanitsiz dis islem verified gibi sunulmaz | Q033, Q063 | CONFIRMED |
| BR-024 | Sonraki bakım hesabi dogrulanmis completion kaydindan devam etmelidir. | Maintenance | — | Q033, Q063 | CONFIRMED |
| BR-025 | Bakimda motosiklete uygun uretici km/sure araliklari temel alinmali ve once dolan izlenmelidir. | Maintenance | Dogrulanmis istisnalar ayrica uygulanabilir | Q031, Q061 | CONFIRMED |
| BR-026 | Dogrulanmamis bakım araligi uretilmemelidir. | Maintenance | Genel agir-kullanim katsayisi uydurulamaz | Q031, Q061 | CONFIRMED |
| BR-027 | Reminder ertelemesi saklanabilir fakat islemi yapilmis sayamaz. | Reminders | — | Q033 | CONFIRMED |
| BR-028 | Urun teknik deger uyduramaz, belirsiz arizayi kesin teshis sunamaz veya tehlikeli isin basarisini garanti edemez. | Tum urun | — | Q035 | CONFIRMED |
| BR-029 | Modifiye sistemde fabrika rehberi otomatik uygun sayilamaz. | Rehber eslesmesi | — | Q038-Q039 | CONFIRMED |
| BR-030 | Islem/malzeme/safety kontrolunu degistiren versiyon farki kesinlesmeden rehber baslamamalidir. | Rehber gating | — | Q036-Q037 | CONFIRMED |
| BR-031 | Insan incelemesi ilgili sistemde uygulamali deneyim ve uyum/kaynak/gorsel/arac/risk/son-kontrol degerlendirmesini icermelidir. | Content governance | Sertifika/unvan varsayilmaz | Q040 | CONFIRMED |
| BR-032 | Bagimsiz ikinci inceleme kritik rehberde ek guven sinyalidir; tum kritik rehberlerde zorunlu oldugu karar degildir. | Content governance | — | Q040 | CONFIRMED |
| BR-033 | Kritik kaynak update'i rehber yeniden incelenene kadar ilgili adimlari askiya almayi gerektirebilir. | Content lifecycle | — | Q042 | CONFIRMED |
| BR-034 | Kritik rehber hatasinda rehber durdurulmali, etkilenenler gerekli kontrol/yardim yoluyla uyarilmali, gecmis silinmemelidir. | Content recall | — | Q043 | CONFIRMED |
| BR-035 | Yeni rehber surumu degisiklik gerekcesiyle yayimlanmali; eski surum tarihsel kayitlarda korunmalidir. | Versioning | — | Q042, Q059-Q060 | CONFIRMED |
| BR-036 | Readiness yalniz `deneyimliyim` beyanina dayanamaz. | Readiness | — | Q051 | CONFIRMED |
| BR-037 | Guvenle ogrenilebilir beceri eksigi hazirliga yonlendirilebilir; ciddi/uzman dogrulamali kritik adim acilmaz. | Readiness / learning | — | Q052 | CONFIRMED |
| BR-038 | Guvenli esdeger olcu/uyum/dayanim/malzeme/islev/safety gereklilikleri dogrulanmadan onerilemez. | Tools/materials | — | Q053, Q055 | CONFIRMED |
| BR-039 | Tam varyant fotografi yoksa dogrulanmis cizim/sema kullanilabilir; baska motosiklet gorseli ayniymis gibi sunulamaz. | Visual guidance | Belirsizlikte adim baslamaz | Q054 | CONFIRMED |
| BR-040 | `En olasi` neden icin birden fazla ayirt edici kanit ve alternatiflerin degerlendirilmesi gerekir. | Diagnosis confidence | Sabit sayisal esik degildir | Q056 | CONFIRMED |
| BR-041 | Esit teshis olasiliklari ayri tutulmali; rastgele parca degisimi onerilmemelidir. | Diagnosis | — | Q057 | CONFIRMED |
| BR-042 | Makul kontroller sonrasinda neden dogrulanamazsa `Neden dogrulanamadi` sonucu kabul edilebilir. | Diagnosis / escalation | — | Q058 | CONFIRMED |
| BR-043 | Gecmis islem rehber update/recall nedeniyle sessizce yeniden yazilamaz; kullanilan surum korunur. | History/versioning | — | Q060 | CONFIRMED |
| BR-044 | Kullanim kosulu bakım araligini sadece motosiklete uygun dogrulanmis bilgi destekliyorsa degistirebilir; gerekce gorunur olmalidir. | Maintenance exceptions | — | Q061 | CONFIRMED |
| BR-045 | Coklu motosikletlerin gecmis/rehber/reminder baglamlari ayrilmalidir; aktif motosiklet anlasilir olmalidir. | Multi-motorcycle | — | Q062 | CONFIRMED |
| BR-046 | Dis islem provenance ile saklanmali; kanit yoksa verified gibi gosterilmemelidir. | History trust | Fatura tek basina otomatik verified degil | Q063 | CONFIRMED |
| BR-047 | Coklu gecikmis bakimda safety/kullanim etkisi, sonra gecikme ve dogrulanmis kosullar dikkate alinmali; gerekce gosterilmelidir. | Maintenance priority | — | Q064 | CONFIRMED |
| BR-048 | Kritik safety bilgisi paywall arkasina saklanmamalidir. | Monetization trust | — | Q065 | CONFIRMED |
| BR-049 | Temel dogrulanmis rehber, bakim kaydi ve temel reminder kullanici beklentisine gore ucretsiz core'dur. | Monetization baseline | — | Q065 | CONFIRMED |
| BR-050 | Kullanici ek teknik kimlik/etiket/parca kodu aramak zorunda birakilmadan observable ozellikler ve fotograflarla varyant ayristirma denenmelidir. | Variant identification | Feasibility garantisi degildir | Q066-Q067 | CONFIRMED |
| BR-051 | Observable kanitla varyant kesinlesmezse eksik ayrim gosterilmeli ve versiyona ozel uygulamali adim acilmamalidir. | Variant stop-gate | — | Q066-Q067 | CONFIRMED |
| BR-052 | Yuksek gerilim uygulamali adimi acilmadan risk, gerekli bilgi/ekipman/kontroller ve motosiklete ozel safety kosullari dogrulanmalidir. | High voltage | Kategori otomatik kapsam disi degildir | Q068 | CONFIRMED |
| BR-053 | Basincli/yuksek sicaklik/benzeri high-consequence sistemlerde de dogrulanmayan safety kosulu atlanarak ilerlenemez. | High-consequence work | — | Q069 | CONFIRMED |
| BR-054 | Rutin/onemli fakat acil olmayan reminders kullanici tercihi olarak gruplanabilir ve gecikmede gunluk spam yerine seyrek ozetlenmelidir. | Notifications | Q070 cadence'i mevcut kullanici tercihidir, evrensel LOCKED kural degildir | Q070-Q071 | CONFIRMED |
| BR-055 | Surus safety'sini etkileyen acil uyari diger reminders arasinda kaybolmamalidir. | Notifications | — | Q071 | CONFIRMED |
| BR-056 | Rutin notifications kapatilabilir/ertelenebilir; kritik safety bilgisi telefon bildirimi kapali olsa bile uygulama icinde ve ilgili islem oncesi gorunur kalmalidir. | Notification controls | — | Q072 | CONFIRMED |
| BR-057 | Gecmis kayit duzeltmesinde eski/yeni deger, zaman ve neden korunmalidir. | History audit | — | Q073 | CONFIRMED |
| BR-058 | Gecmis duzeltmesi bakım planini degistiriyorsa etkisi kullaniciya aciklanmalidir. | Maintenance/history | — | Q073 | CONFIRMED |
| BR-059 | Kullanici beyanı, belgeli islem ve ayrica incelenmis kayit ayni evidence level gibi sunulamaz. | Evidence/provenance | Nihai taxonomy acik | Q074 | CONFIRMED |
| BR-060 | Modifiye parcanin guvenilir bakım araligi bilinmiyorsa eski aralik otomatik kullanilamaz veya yeni sure uydurulamaz; takvim belirsiz gosterilmelidir. | Maintenance uncertainty | — | Q075 | CONFIRMED |
| BR-061 | Dogrulanmis bakım istisnasi genel planla birlikte ve neden gecerli olduguyla gosterilmelidir. | Maintenance exceptions | — | Q076 | CONFIRMED |
| BR-062 | Kullanim kosulu bilinmiyorsa eksiklik gizlenmemeli; gecerli standart plan varsa gosterilip eksik bilgi sorulmali ve cevapla plan yeniden degerlendirilmelidir. | Maintenance uncertainty | Gecerli standart plan yoksa uydurulamaz | Q077 | CONFIRMED |
| BR-063 | Islem suresi kesin bitis vaadi yerine deneyime bagli aralik olarak sunulmali; hasar/sikisma/ek sokme belirsizligi gorunur olmalidir. | Pre-task estimate | — | Q078 | CONFIRMED |
| BR-064 | Maliyet tahmini parca/sarf/arac/varsa isciligi ayirmali; haric kalem, fiyat tarihi ve varsayimlar gorunur olmalidir. | Cost estimate | — | Q079 | CONFIRMED |
| BR-065 | Kisisel not/fotograf default-private kalmali; community paylasimi ayri explicit secim olmali ve kisisel bilgi paylasim oncesi ayiklanmalidir. | Community/privacy | — | Q080 | CONFIRMED |
| BR-066 | Community duzeltmesi resmi rehbere dogrudan giremez; kaynak, motosiklet uygunlugu ve safety etkisi incelenmelidir. | Content governance | — | Q081 | CONFIRMED |
| BR-067 | Community iceriginde kaynak, uygulandigi motosiklet, inceleme durumu ve tarih gorunur olmali; resmi rehberden ayrilmalidir. | Community provenance | — | Q082 | CONFIRMED |
| BR-068 | Tehlikeli community icerigi gorunumden kaldirilip incelenmeli; resmi rehberi etkiliyorsa ilgili adim durdurulup etkilenenler uyarilmalidir. | Moderation / safety | Sayisal SLA karari degildir | Q083 | CONFIRMED |
| BR-069 | Community soru-cevap/deneyim resmi rehberin numarali adimlarina karismamalidir. | Content separation | — | Q084 | CONFIRMED |
| BR-070 | Servis/usta listeleme core self-service rehberin yerini almamali; ucretli siralama teknik karari etkilememelidir. | Commercial support | — | Q085 | CONFIRMED |
| BR-071 | Satin alma seceneklerinden once teknik uygunluk kriterleri gosterilmeli; sponsorlu teklif isaretlenmeli ve odeme teknik uygunlugu degistirmemelidir. | Commerce neutrality | — | Q086 | CONFIRMED |
| BR-072 | Motora uygun ayrintili rehber, safety bilgisi ve temel bakım takibi ucretsiz core beklentisidir. | Monetization | Premium ornekler final paket degildir | Q087 | CONFIRMED |
| BR-073 | Gizli reklam, ucretli urunu `en uygun` gostermek, alternatif saklamak veya rehberi satis hedefine gore degistirmek kabul edilen guven modeline aykiridir. | Commercial neutrality | — | Q088 | CONFIRMED |
| BR-074 | Yol-kenari deneyimi hizli/kisa olabilir fakat suruse devam belirsizligi ve kritik safety gizlenemez. | Roadside use | — | Q090 | CONFIRMED |
| BR-075 | Indirilmis motosiklete ozel rehber/gorsel/safety uyarisi, kalinan adim ve kisisel gecmis offline erisilebilir kalmali; surum/guncellik gorunmelidir. | Offline continuity | Recall edge case acik | Q091 | CONFIRMED |
| BR-076 | Kullanici kendi motosiklet/kayit/not/fotograf verisini goruntuleme, duzeltme, ekleme ve silme kontrolune sahip olmalidir. | Data ownership | — | Q092 | CONFIRMED |
| BR-077 | Bir hesabin verisi baska hesapta gorunmemelidir. | Account isolation expectation | Teknik implementasyon karari degildir | Q092, Q095 | CONFIRMED |
| BR-078 | Kullanicinin kendi motosiklet/tarihli islem/not/fotograf verisini anlasilir ve yeniden kullanilabilir bicimde export etmesi premium'a baglanmamalidir. | Data portability | Format secilmedi | Q093 | CONFIRMED |
| BR-079 | Silme oncesi kapsam/geri alinmazlik aciklanmali; silme sonrasinda silinen ve bekleyen durum anlasilir olmalidir. | Data deletion expectation | Retention/sure secilmedi | Q094 | CONFIRMED |
| BR-080 | Uydurulmus teknik bilgi, gizlenen tehlike, cross-account veri karismasi, gecmisin sessiz kaybi veya reklam etkili rehber trust-breaker'dir. | Tum urun | — | Q095 | CONFIRMED |

## Rules needing more discovery

- High-consequence islemlerde profesyonel yardima gecis ve override edilemeyen safety kapilari
- Readiness false-positive/false-negative ve kullanici override beklentisi
- Modifiye motosikletlerde beklenen katalog kapsami
- Community moderation itiraz/uyusmazlik ve faydali ama dogrulanamamis icerik statusu
- Nihai evidence-level / `reviewed` / `verified` dil sinirlari
- Kritik notification uzun sure gormezden gelinirse escalation davranisi
- Premium paket/model tercihi
- Farkli user segmentlerinin motivasyon ve ihtiyac farklari
- Paylasilan motosiklet/ortak kayit davranisi
- Motosiklet satma/devretme/arsivleme
- Offline stale/recall icerik davranisi
- Ilk kullanim/onboarding ve hesap zorunlulugu
