# BUSINESS RULES

Status: DRAFT

Bu kurallar Batch 01 kullanici kanitindan turetilen teknik olmayan urun davranis kurallaridir. Kesin teknik implementasyon degildir.

| ID | Rule | Applies To | Exceptions / Notes | Source | Status |
|---|---|---|---|---|---|
| BR-001 | Motosiklete ozel bir rehber, kullanicinin gercek motosiklet konfigürasyonuyla yeterli eslesme kurulmadan motosiklete ozelmis gibi sunulamaz. | Rehber secimi / ilerleme | Gerekli kimlik alanlarinin tam seti henuz acik | Q008-Q009, Q026 | CONFIRMED |
| BR-002 | Yil, versiyon veya donanim islemi degistiriyorsa farkli adimlar ayri rehber dallari olarak ele alinmalidir. | Rehber varyantlari | Dal kirilim kriterleri sonraki discovery'de netlesecek | Q009 | CONFIRMED |
| BR-003 | Eslesme belirsizse yakin yil veya varyantin adimlari dogruymus gibi kullanilarak ilerlenemez. | Rehber guvenligi | — | Q009, Q026 | CONFIRMED |
| BR-004 | Dogrulanmis teknik bilgi, kullanicinin motosiklet/varyantina uygun guvenilir kaynaga dayanmalidir; internet tekrar sayisi tek basina dogrulama degildir. | Teknik icerik | Kaynak onceligi/governance henuz tam degil | Q010 | CONFIRMED |
| BR-005 | Kullanici kaynak surumu ve ilgili sayfa/bolum kanitini gorebilmelidir. | Icerik provenance | Gosterim seviyesi tasarim asamasinda | Q010 | CONFIRMED |
| BR-006 | Kritik kaynak celiskisi cozulmemisse sistem tek bir teknik degeri secip kullaniciyi uygulamali ilerlemeye zorlayamaz. | Kaynak celiskisi | — | Q011 | CONFIRMED |
| BR-007 | Deneyim seviyesi rehberin ayrinti/hizini degistirebilir fakat guvenlik uyarilari ve kritik dogrulama adimlarini kaldiramaz. | Rehber sunumu | — | Q007, Q014 | CONFIRMED |
| BR-008 | Yeni/az deneyimli kullanici icin temel adim, atlanan ara hareket birakmadan uygulanabilir ayrintida olmalidir. | Rehber adimlari | Ayrinti standardi islem turune gore derinlesebilir | Q014 | CONFIRMED |
| BR-009 | Islem oncesi zorunlu arac/parca/ekipman eksikligi, kullanici motosikleti yari sokulmus durumda birakmadan once gorunur olmalidir. | Readiness | — | Q016-Q017 | CONFIRMED |
| BR-010 | Zorunlu ozel arac veya parca yoksa ilgili uygulamali adima gecilmemelidir. | Readiness / ilerleme | Guvenli esdeger kurali acik | Q017 | CONFIRMED |
| BR-011 | Kritik guvenlik riski islem baslamadan once ve ilgili adimdan hemen once gosterilmelidir. | Safety warnings | Genel uyari spam'i kritik uyarilari golgelememeli | Q018 | CONFIRMED |
| BR-012 | Guvenlik uyarisi riskin ne oldugunu, nasil onlenecegini ve hangi kosulda durulacagini somut olarak aciklamalidir. | Safety warnings | — | Q018 | CONFIRMED |
| BR-013 | Rehber-varyant uyusmazligi, hasarli parca, gerekli olcum/arac eksikligi, beklenmeyen baglanti veya kritik sonucun dogrulanamamasi ilerlemeyi durdurma nedenidir. | Stop-gate | Islem sinifi bazli ek kurallar acik | Q019, Q034 | CONFIRMED |
| BR-014 | Fren, direksiyon ve yuksek gerilim gibi kritik alanlarda belirsizlikle ilerleme onerilmemelidir. | High-consequence work | Tam kategori listesi acik | Q019 | CONFIRMED |
| BR-015 | Olası ariza nedeni kesin teshis olarak sunulamaz; dogrulanma durumu acikca belirtilmelidir. | Diagnosis | — | Q023-Q024 | CONFIRMED |
| BR-016 | Teshis olasiligi, onu destekleyen belirti/kontrol/beklenen sonucla ilerlemeli ve yeni kanita gore daralmalidir. | Diagnosis | Yeterli kanit esigi acik | Q022-Q024 | CONFIRMED |
| BR-017 | Kanit olmadan parca degisimi veya motosikletin guvenle kullanilabilecegi onerilmemelidir. | Diagnosis / safety | — | Q024 | CONFIRMED |
| BR-018 | Rehber gercek motosikletle uyusmuyorsa normal ilerleme durmali, fark kaydedilebilmeli ve varyant/eslesme yeniden belirlenmelidir. | Mismatch recovery | — | Q026 | CONFIRMED |
| BR-019 | Hata veya beklenmeyen davranista normal ilerleme durmali; guvenliyse emniyete alma ve dokunulmaması gereken alanlar gosterilmelidir. | Recovery | — | Q027 | CONFIRMED |
| BR-020 | Yarim kalan islem, son tamamlanan adimla birlikte sokulu parcalar, olcumler, fotograflar/notlar ve rehber surumu gibi baglamini korumalidir. | Interrupted work | — | Q028 | CONFIRMED |
| BR-021 | Degismis rehber, devam eden yarim isleme sessizce uygulanmamalidir. | Guide versioning | Kullaniciya nasil sunulacagi acik | Q028 | CONFIRMED |
| BR-022 | Yarim kalan veya sonucu dogrulanamayan islem tamamlanmis olarak isaretlenemez. | History / completion | — | Q029 | CONFIRMED |
| BR-023 | Disarida yaptirilan islem kaydedilebilir; erteleme ise tamamlanma olarak kabul edilmez. | Maintenance history | Dis kaydin dogrulama seviyesi acik | Q033 | CONFIRMED |
| BR-024 | Sonraki bakim hesabi dogrulanmis tamamlanma kaydindan devam etmelidir. | Maintenance tracking | `dogrulanmis tamamlanma` standardi derinlesebilir | Q033 | CONFIRMED |
| BR-025 | Bakim zamanlamasinda motosiklete uygun uretici kilometre/sure araliklari temel alinmali ve hangisi once dolarsa o izlenmelidir. | Maintenance tracking | Agir kullanim/istisna kurallari acik | Q031 | CONFIRMED |
| BR-026 | Dogrulanmamis bakim araligi uretilmemelidir. | Maintenance tracking | — | Q031 | CONFIRMED |
| BR-027 | Hatirlatma ertelemesi yeni tarih/gerekceyle saklanabilir ancak islemi yapilmis sayamaz. | Reminders | — | Q033 | CONFIRMED |
| BR-028 | Urun dogrulanmamis teknik deger uyduramaz, belirsiz arizayi kesin teshis gibi sunamaz veya tehlikeli isin basarisini garanti edemez. | Tum urun | — | Q035 | CONFIRMED |

## Rules needing more discovery

- Guvenli esdeger arac/malzemenin hangi kosullarda kabul edilecegi
- Kullanici beceri/readiness seviyesinin nasil degerlendirilecegi
- Teshiste `yeterli kanit` esigi
- Islem kategorisi bazli mutlak/koşullu safety stop kurallari
- Disarida yapilan islem kaydinin dogrulanma derecesi
- Rehber surum degisikliginin devam eden isleme nasil uygulanacagi
