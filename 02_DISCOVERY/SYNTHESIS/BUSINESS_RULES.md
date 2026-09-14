# BUSINESS RULES

Status: DRAFT

Bu kurallar kullanici kanitindan turetilen teknik olmayan urun davranis kurallaridir. Kesin teknik implementasyon degildir.

| ID | Rule | Applies To | Exceptions / Notes | Source | Status |
|---|---|---|---|---|---|
| BR-001 | Motosiklete ozel rehber, gercek motosiklet konfigurasyonuyla yeterli eslesme kurulmadan motosiklete ozelmis gibi sunulamaz. | Rehber secimi | Sabit evrensel kimlik seti yok | Q008-Q009, Q026, Q036-Q039 | CONFIRMED |
| BR-002 | Yil/versiyon/donanim islemi degistiriyorsa farkli adimlar ayri rehber dallari olarak ele alinmalidir. | Rehber varyantlari | — | Q009, Q037 | CONFIRMED |
| BR-003 | Eslesme belirsizse yakin yil/varyant adimlari dogruymus gibi kullanilarak ilerlenemez. | Rehber guvenligi | — | Q009, Q026, Q037 | CONFIRMED |
| BR-004 | Dogrulanmis teknik bilgi motosiklet/varyanta uygun guvenilir kaynaga dayanmalidir. | Teknik icerik | Internet tekrar sayisi tek basina dogrulama degil | Q010, Q041 | CONFIRMED |
| BR-005 | Kullanici kaynak surumu ve ilgili sayfa/bolum kanitini gorebilmelidir. | Provenance | Gosterim tasarimi sonraki asama | Q010 | CONFIRMED |
| BR-006 | Cozulmemis kritik kaynak celiskisinde tek deger secilip application progression yaptirilamaz. | Kaynak celiskisi | Celismeyen preparation/safety bilgisi kalabilir | Q011, Q044 | CONFIRMED |
| BR-007 | Deneyim seviyesi rehber ayrinti/hizini degistirebilir fakat safety ve kritik dogrulamayi kaldiramaz. | Rehber sunumu | — | Q007, Q014 | CONFIRMED |
| BR-008 | Yeni/az deneyimli kullanici icin temel adim atlanan ara hareket birakmadan uygulanabilir ayrintida olmalidir. | Rehber adimlari | — | Q014 | CONFIRMED |
| BR-009 | Zorunlu arac/parca/ekipman eksigi motosiklet yari sokulmeden once gorunur olmalidir. | Readiness | — | Q016-Q017 | CONFIRMED |
| BR-010 | Zorunlu ozel arac/parca yoksa ilgili application adimina gecilmez. | Readiness | Dogrulanmis guvenli esdeger bazi basit yardimci araclarda olabilir | Q017, Q053 | CONFIRMED |
| BR-011 | Kritik safety riski islem basinda ve ilgili adimdan hemen once gosterilmelidir. | Safety | — | Q018 | CONFIRMED |
| BR-012 | Safety uyarisi risk, onleme ve stop kosulunu somut aciklamalidir. | Safety | — | Q018 | CONFIRMED |
| BR-013 | Varyant uyusmazligi, hasar, gerekli olcum/arac eksigi, beklenmeyen baglanti veya kritik sonucun dogrulanamamasi stop nedenidir. | Stop-gate | — | Q019, Q034, Q045-Q050 | CONFIRMED |
| BR-014 | High-consequence alanlarda belirsizlikle ilerleme onerilmemeli; kategoriye ozel on kosul/stop-gate uygulanmalidir. | High-consequence | — | Q019, Q046-Q050 | CONFIRMED |
| BR-015 | Olasi ariza nedeni kesin teshis gibi sunulamaz. | Diagnosis | — | Q023-Q024 | CONFIRMED |
| BR-016 | Teshis olasiligi kanitla ilerlemeli ve yeni kanita gore daralmalidir. | Diagnosis | Sabit nicel test sayisi yok | Q022-Q024, Q056-Q058 | CONFIRMED |
| BR-017 | Kanit olmadan parca degisimi veya guvenli kullanim onerilmemelidir. | Diagnosis/safety | — | Q024, Q057-Q058 | CONFIRMED |
| BR-018 | Rehber gercek motosiklet/modifikasyonla uyusmuyorsa normal ilerleme durup uygunluk yeniden kurulmalidir. | Mismatch recovery | — | Q026, Q038-Q039 | CONFIRMED |
| BR-019 | Hata/beklenmeyen davranista normal ilerleme durmali; guvenliyse emniyete alma/dokunmama bilgisi sunulmalidir. | Recovery | — | Q027 | CONFIRMED |
| BR-020 | Yarim islem; adim, sokulu parca, olcum, fotograf/not ve rehber surumu baglamini korumalidir. | Interrupted work | — | Q028, Q059 | CONFIRMED |
| BR-021 | Degismis rehber devam eden isleme sessizce uygulanamaz. | Versioning | Kritik duzeltmede eski akis durur | Q028, Q059 | CONFIRMED |
| BR-022 | Yarim veya sonucu dogrulanamayan islem tamamlandi olarak isaretlenemez. | Completion | — | Q029 | CONFIRMED |
| BR-023 | Disarida yaptirilan islem kaydedilebilir; erteleme completion degildir. | History | Kanitsiz dis islem verified gibi sunulmaz | Q033, Q063 | CONFIRMED |
| BR-024 | Sonraki bakım hesabi dogrulanmis completion kaydindan devam etmelidir. | Maintenance | — | Q033, Q063 | CONFIRMED |
| BR-025 | Bakimda motosiklete uygun uretici km/sure araliklari temel alinmali ve once dolan izlenmelidir. | Maintenance | Dogrulanmis istisnalar olabilir | Q031, Q061 | CONFIRMED |
| BR-026 | Dogrulanmamis bakım araligi uretilmemelidir. | Maintenance | — | Q031, Q061 | CONFIRMED |
| BR-027 | Reminder ertelemesi saklanabilir fakat islemi yapilmis sayamaz. | Reminders | — | Q033 | CONFIRMED |
| BR-028 | Urun teknik deger uyduramaz, belirsiz arizayi kesin teshis sunamaz veya tehlikeli isin basarisini garanti edemez. | Tum urun | — | Q035 | CONFIRMED |
| BR-029 | Modifiye sistemde fabrika rehberi otomatik uygun sayilamaz. | Rehber eslesmesi | — | Q038-Q039 | CONFIRMED |
| BR-030 | Islem/malzeme/safety kontrolunu degistiren versiyon farki kesinlesmeden rehber baslamamalidir. | Rehber gating | — | Q036-Q037 | CONFIRMED |
| BR-031 | Insan incelemesi ilgili sistemde uygulamali deneyim ve uyum/kaynak/gorsel/arac/risk/son-kontrol degerlendirmesini icermelidir. | Governance | Sertifika/unvan varsayilmaz | Q040 | CONFIRMED |
| BR-032 | Bagimsiz ikinci inceleme kritik rehberde ek guven sinyalidir; evrensel zorunluluk degildir. | Governance | — | Q040 | CONFIRMED |
| BR-033 | Kritik kaynak update'i rehber yeniden incelenene kadar ilgili adimlari askiya almayi gerektirebilir. | Content lifecycle | — | Q042 | CONFIRMED |
| BR-034 | Kritik rehber hatasinda rehber durdurulmali, etkilenenler gerekli kontrol/yardim yoluyla uyarilmali, gecmis silinmemelidir. | Recall | — | Q043 | CONFIRMED |
| BR-035 | Yeni rehber surumu degisiklik gerekcesiyle yayimlanmali; eski surum tarihsel kayitlarda korunmalidir. | Versioning | — | Q042, Q059-Q060 | CONFIRMED |
| BR-036 | Readiness yalniz `deneyimliyim` beyanina dayanamaz. | Readiness | — | Q051 | CONFIRMED |
| BR-037 | Guvenle ogrenilebilir beceri eksigi hazirliga yonlendirilebilir; ciddi/uzman dogrulamali kritik adim acilmaz. | Readiness/learning | — | Q052 | CONFIRMED |
| BR-038 | Guvenli esdeger olcu/uyum/dayanim/malzeme/islev/safety gereklilikleri dogrulanmadan onerilemez. | Tools/materials | — | Q053, Q055 | CONFIRMED |
| BR-039 | Tam varyant fotografi yoksa dogrulanmis cizim/sema kullanilabilir; baska motosiklet gorseli ayniymis gibi sunulamaz. | Visual guidance | Belirsizlikte adim baslamaz | Q054 | CONFIRMED |
| BR-040 | `En olasi` neden icin birden fazla ayirt edici kanit ve alternatiflerin degerlendirilmesi gerekir. | Diagnosis | Sabit sayisal esik degil | Q056 | CONFIRMED |
| BR-041 | Esit teshis olasiliklari ayri tutulmali; rastgele parca degisimi onerilmemelidir. | Diagnosis | — | Q057 | CONFIRMED |
| BR-042 | Makul kontroller sonrasinda neden dogrulanamazsa `Neden dogrulanamadi` sonucu kabul edilebilir. | Diagnosis/escalation | — | Q058 | CONFIRMED |
| BR-043 | Gecmis islem rehber update/recall nedeniyle sessizce yeniden yazilamaz; kullanilan surum korunur. | History/versioning | — | Q060 | CONFIRMED |
| BR-044 | Kullanim kosulu bakım araligini sadece motosiklete uygun dogrulanmis bilgi destekliyorsa degistirebilir; gerekce gorunur olmalidir. | Maintenance exceptions | — | Q061 | CONFIRMED |
| BR-045 | Coklu motosikletlerin gecmis/rehber/reminder baglamlari ayrilmalidir; aktif motosiklet anlasilir olmalidir. | Multi-motorcycle | — | Q062 | CONFIRMED |
| BR-046 | Dis islem provenance ile saklanmali; kanit yoksa verified gibi gosterilmemelidir. | History trust | Fatura tek basina otomatik verified degil | Q063 | CONFIRMED |
| BR-047 | Coklu gecikmis bakimda safety/kullanim etkisi, sonra gecikme ve dogrulanmis kosullar dikkate alinmali; gerekce gosterilmelidir. | Maintenance priority | — | Q064 | CONFIRMED |
| BR-048 | Kritik safety bilgisi paywall arkasina saklanmamalidir. | Monetization trust | — | Q065 | CONFIRMED |
| BR-049 | Temel dogrulanmis rehber, bakım kaydi ve temel reminder kullanici beklentisine gore ucretsiz core'dur. | Monetization | — | Q065 | CONFIRMED |
| BR-050 | Kullanici teknik kimlik/etiket/parca kodu aramak zorunda birakilmadan observable ozellikler ve fotograflarla varyant ayristirma denenmelidir. | Variant identification | Feasibility garantisi degil | Q066-Q067 | CONFIRMED |
| BR-051 | Observable kanitla varyant kesinlesmezse eksik ayrim gosterilmeli ve versiyona ozel application acilmamalidir. | Variant gate | — | Q066-Q067 | CONFIRMED |
| BR-052 | Yuksek gerilim application'i acilmadan risk, gerekli bilgi/ekipman/kontroller ve motosiklete ozel safety kosullari dogrulanmalidir. | High voltage | Kategori otomatik dislanmaz | Q068 | CONFIRMED |
| BR-053 | Basincli/yuksek sicaklik/benzeri high-consequence sistemlerde dogrulanmayan safety kosulu atlanarak ilerlenemez. | High-consequence | — | Q069 | CONFIRMED |
| BR-054 | Routine/onemli fakat acil olmayan reminders gruplanabilir ve gunluk spam yerine seyrek ozetlenebilir. | Notifications | Q070 mevcut kullanici tercihi | Q070-Q071 | CONFIRMED |
| BR-055 | Surus safety'sini etkileyen acil uyari diger reminders arasinda kaybolmamalidir. | Notifications | — | Q071 | CONFIRMED |
| BR-056 | Routine notifications kapatilabilir/ertelenebilir; kritik safety app icinde ve ilgili islem oncesi gorunur kalmalidir. | Notifications | — | Q072 | CONFIRMED |
| BR-057 | History duzeltmesinde eski/yeni deger, zaman ve neden korunmalidir. | History audit | — | Q073 | CONFIRMED |
| BR-058 | History duzeltmesi bakım planini degistiriyorsa etkisi kullaniciya aciklanmalidir. | Maintenance/history | — | Q073 | CONFIRMED |
| BR-059 | Kullanici beyani, belgeli islem ve incelenmis kayit ayni evidence level gibi sunulamaz. | Evidence | Global taxonomy acik | Q074 | CONFIRMED |
| BR-060 | Modifiye parcanin guvenilir bakım araligi bilinmiyorsa eski aralik otomatik kullanilamaz veya yeni sure uydurulamaz. | Maintenance uncertainty | — | Q075 | CONFIRMED |
| BR-061 | Dogrulanmis bakım istisnasi genel planla birlikte ve neden gecerli olduguyla gosterilmelidir. | Maintenance exceptions | — | Q076 | CONFIRMED |
| BR-062 | Kullanim kosulu bilinmiyorsa eksiklik gizlenmemeli; gecerli standart plan varsa gosterilip eksik bilgi sorulmalidir. | Maintenance uncertainty | — | Q077 | CONFIRMED |
| BR-063 | Islem suresi kesin bitis vaadi yerine deneyime bagli aralik olarak sunulmali; belirsizlik gorunur olmalidir. | Estimate | — | Q078 | CONFIRMED |
| BR-064 | Maliyet tahmini parca/sarf/arac/varsa isciligi ayirmali; haric kalem, fiyat tarihi ve varsayimlar gorunur olmalidir. | Estimate | — | Q079 | CONFIRMED |
| BR-065 | Kisisel not/fotograf default-private kalmali; community paylasimi explicit secim olmali ve personal info ayiklanmalidir. | Community/privacy | — | Q080 | CONFIRMED |
| BR-066 | Community duzeltmesi resmi rehbere dogrudan giremez; kaynak, motosiklet uygunlugu ve safety etkisi incelenmelidir. | Governance | — | Q081 | CONFIRMED |
| BR-067 | Community iceriginde kaynak, uygulandigi motosiklet, review status ve tarih gorunur olmali; resmi rehberden ayrilmalidir. | Community provenance | — | Q082 | CONFIRMED |
| BR-068 | Tehlikeli community icerigi gorunumden kaldirilip incelenmeli; resmi rehberi etkiliyorsa ilgili adim durdurulup etkilenenler uyarilmalidir. | Moderation/safety | Sayisal SLA degil | Q083 | CONFIRMED |
| BR-069 | Community soru-cevap/deneyim resmi rehberin numarali adimlarina karismamalidir. | Content separation | — | Q084 | CONFIRMED |
| BR-070 | Servis/usta listeleme core self-service rehberin yerini almamali; ucretli siralama teknik karari etkilememelidir. | Commercial support | — | Q085 | CONFIRMED |
| BR-071 | Satin alma seceneklerinden once teknik uygunluk kriterleri gosterilmeli; sponsorlu teklif isaretlenmeli ve odeme teknik uygunlugu degistirmemelidir. | Commerce neutrality | — | Q086 | CONFIRMED |
| BR-072 | Motora uygun ayrintili rehber, safety ve temel bakım takibi ucretsiz core beklentisidir. | Monetization | — | Q087 | CONFIRMED |
| BR-073 | Gizli reklam, ucretli urunu `en uygun` gostermek, alternatif saklamak veya rehberi satis hedefine gore degistirmek guven modeline aykiridir. | Commercial neutrality | — | Q088 | CONFIRMED |
| BR-074 | Roadside deneyim hizli/kisa olabilir fakat suruse devam belirsizligi ve kritik safety gizlenemez. | Roadside | — | Q090 | CONFIRMED |
| BR-075 | Indirilmis rehber/gorsel/safety/progress/history offline erisilebilir kalmali; surum/guncellik gorunmelidir. | Offline | Recall edge case sonraki rules ile derinlesti | Q091 | CONFIRMED |
| BR-076 | Kullanici kendi motosiklet/kayit/not/fotograf verisini goruntuleme, duzeltme, ekleme ve silme kontrolune sahip olmalidir. | Data ownership | — | Q092 | CONFIRMED |
| BR-077 | Bir hesabin verisi baska hesapta gorunmemelidir. | Data isolation expectation | Teknik implementasyon karari degil | Q092, Q095 | CONFIRMED |
| BR-078 | Kullanicinin kendi verisini yeniden kullanilabilir export etmesi premium'a baglanmamalidir. | Data portability | Format secilmedi | Q093 | CONFIRMED |
| BR-079 | Silme oncesi kapsam/geri alinmazlik aciklanmali; silme sonrasinda silinen/bekleyen durum anlasilir olmalidir. | Data deletion | Retention/sure secilmedi | Q094 | CONFIRMED |
| BR-080 | Uydurulmus teknik bilgi, gizlenen tehlike, cross-account veri karismasi, gecmisin sessiz kaybi veya reklam etkili rehber trust-breaker'dir. | Tum urun | — | Q095 | CONFIRMED |
| BR-081 | Readiness blokajinda eksik kosul, neden gerektigi, nasil saglanacagi ve nasil yeniden kontrol edilecegi aciklanmalidir. | Readiness UX | — | Q096-Q098 | CONFIRMED |
| BR-082 | Kullanici readiness sonucuna yeni fotograf/olcum/alternatif kontrol kanitiyla re-validation isteyebilmelidir; salt oz-beyan gate'i gecemez. | Readiness re-validation | — | Q096 | CONFIRMED |
| BR-083 | Varyant, kritik teknik bilgi, gerekli ekipman, guvenli ortam veya zorunlu pre-check eksigi self-declared override ile gecilemez. | Safety gates | — | Q097 | CONFIRMED |
| BR-084 | Teaching content erisilebilir kalabilir; gercek motosiklete ilk mudahaleden once zorunlu kosullar dogrulanmali ve yeni risk/mismatch'te application durmalidir. | Teaching/application separation | — | Q099 | CONFIRMED |
| BR-085 | Professional escalation kullaniciyi kalici yetersiz ilan eden dille degil, dogrulanmamis kosul ve yeniden deneme yoluyla aciklanmalidir. | Escalation | Exact trigger acik | Q100 | CONFIRMED |
| BR-086 | Professional path secilse bile symptom capture, fotograf, preparation, islemi anlama ve result-check destegi devam etmelidir. | Escalation/support | — | Q101 | CONFIRMED |
| BR-087 | Yaygin aftermarket degisiklik verified uygunsa rehbere dahil edilebilir; fabrika ve modifiye sokme/takma farklari ayrilmalidir. | Modification coverage | Feasibility garantisi degil | Q102 | CONFIRMED |
| BR-088 | Custom/nadir modifikasyonda verified guide yoksa evidence gap aciklanabilir ve teaching-only bilgi kalabilir; riskli application dogrulanana kadar acilmaz. | Modification fallback | — | Q103-Q104 | CONFIRMED |
| BR-089 | Moderation removal reason somut/saygili olmali; kural ve sorunlu bolum gosterilmeli, correction/re-submit veya appeal yolu bulunmalidir. | Community moderation | — | Q105 | CONFIRMED |
| BR-090 | Tekrarlanan yanlis contribution pre-review'a alinabilir; kasitli/surekli tehlikeli tekrarda contribution yetkisi kisitlanabilir. | Community enforcement | Final ban policy degil | Q106, Q108 | CONFIRMED |
| BR-091 | Faydalı fakat teknik olarak dogrulanamayan deneyim `dogrulanmamis kisisel deneyim` olarak motosiklet/gozlem baglamiyla sunulabilir; official step olamaz. | Community trust | Riskli oneriler review bitmeden yayinlanmaz | Q107 | CONFIRMED |
| BR-092 | Kasitli tehlikeli contribution hizla gizlenmeli, olay kaydedilmeli ve gerekiyorsa icerige maruz kalan kullanicilar uyarilmalidir. | Moderation/safety | Sayisal SLA degil | Q108 | CONFIRMED |
| BR-093 | Evidence labels temel olarak kullanici beyani -> belgeli -> incelenmis -> dogrulanmis farklarini kullaniciya anlatmalidir. | Evidence language | Global tek taxonomy henuz karar degil | Q109 | CONFIRMED |
| BR-094 | `Dogrulanmis` kaynak, ilgili motosiklet/islem uygunlugu, inceleme tarihi ve karar gorunurlugunu gerektirir; mutlak garanti dili kullanilamaz. | Evidence language | — | Q110 | CONFIRMED |
| BR-095 | Uzun sure ertelenen kritik konu routine reminders arasinda kaybolmamali; app icinde safety summary, gecikme sonucu ve ilgili action'a yol bulunmalidir. | Critical reminders | — | Q111 | CONFIRMED |
| BR-096 | Coklu kritik konu olasi zarar/aciliyete gore siralanmali; neden oncelikli, ne zamandir acik ve simdi hangi kontrol gerekli bilgisi gorunmelidir. | Critical priority | — | Q112 | CONFIRMED |
| BR-097 | Uzun aradan donuste eski bildirimler tek tek yagmak yerine kritik safety -> geciken bakım -> kayitlar sirali catch-up summary sunulmalidir. | Re-engagement | — | Q113 | CONFIRMED |
| BR-098 | Guvenli islem icin gerekli core bilgi ve kullanicinin kendi verisini alma hakki premium'a baglanmamalidir. | Monetization boundary | Ek storage/analysis premium olabilir | Q114-Q115 | CONFIRMED |
| BR-099 | Surekli hizmet maliyeti yaratmayan optional value'larda one-time payment mevcut kullanici icin makul olabilir. | Monetization preference | Final paket/model degil | Q115 | CONFIRMED |
| BR-100 | Core target bireysel self-service rider'dir; multi-bike, shared-family, hobby helper ve record-only owner supported adjacent context olabilir. | User scope | Professional/service status acik | Q116-Q117 | CONFIRMED |
| BR-101 | Shared motorcycle'da owner access verir; contributor attribution, zaman/edit trail, revocable permission ve private-note isolation korunmalidir. | Collaboration | Teknik permission modeli secilmedi | Q118-Q119 | CONFIRMED |
| BR-102 | Ownership transfer'da kullanici sectigi vehicle-history kayitlarini aktarabilir; personal notes ve kimlik/konum iceren fotograflar default-private kalmali ve transfer preview olmalidir. | Ownership transfer | Parsiyel history completeness acik | Q120 | CONFIRMED |
| BR-103 | Archive motosikleti aktif garajdan cikarmali ama history'yi korumali ve yeniden aktivasyona izin vermeli; delete ile ayni degildir. | Lifecycle | — | Q121 | CONFIRMED |
| BR-104 | Kritik offline rehberde son dogrulama zamani gorunmeli; product freshness limiti asildiginda application online re-check'e kadar kapanabilmelidir. | Offline safety | Sayisal threshold belirlenmedi | Q122 | CONFIRMED |
| BR-105 | First-use'ta guide value account creation, notification permission veya uzun profile zorlanmadan once gorulebilmelidir. | Onboarding | Teknik auth karari degil | Q123 | CONFIRMED |
| BR-106 | Turkiye icin acik Turkce, alisilmis olcu birimleri ve deneyime gore terminoloji derinligi beklenir. | Localization | Global expansion karari degil | Q124 | CONFIRMED |
| BR-107 | Buyuk yazi/dugme, high contrast, non-color-only warning, image description, video caption, voice steps ve kolay dokunus erisilebilirlik ihtiyaclaridir. | Accessibility | Belirli implementation secilmedi | Q125 | CONFIRMED |

## Rules needing more discovery

- Professional escalation exact trigger ve self-service'e geri donus
- Premium recurring/one-time/hybrid paket tercihi
- Segment motivasyon/first-use farklari ve professional/service target statusu
- Gercek delete, community withdrawal ve export provenance lifecycle
- Evidence labels'in technical guide/history/community/external service baglamlarinda ayrisma ihtiyaci
- Selective ownership transfer'da history completeness semantigi
- Critical freshness expiry'nin hangi rehberlerde ve hangi semantikle uygulanacagi
- Active-repair voice/easy-touch etkileşimde safety-critical confirmation davranisi
