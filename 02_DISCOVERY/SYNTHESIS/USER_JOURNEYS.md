# USER JOURNEYS

Status: DRAFT

Kullanicilarin teknik implementasyon detayindan bagimsiz uc uca urun yolculuklari.

## J-001 — Known task -> prepare -> execute -> verify -> record

**Evidence:** Q006, Q013-Q021, Q029-Q030, Q050-Q053

1. Kullanici yapmak istedigi islemi bilir.
2. Urun motosiklet/referans rehber eslesmesini dogrular.
3. Kullanici amac, uygunluk, zorluk/risk, sure, maliyet, arac/parca/ekipman ve motosikletin kullanilabilirlik durumunu gorur.
4. Hazirlik ve islem-bazli readiness degerlendirilir; zorunlu eksik veya kritik beceri eksigi varsa uygulama adimi acilmaz.
5. Rehber kullanicinin ihtiyac duydugu ayrinti/hiz seviyesini sunar; kritik guvenlik ve dogrulama degismez.
6. Her kritik adimda ilgili gorsel, olcum veya basari kontrolu bulunur.
7. Durdurma kosulu olusursa normal ilerleme kesilir.
8. Islem tamamlandiginda gerekli son kontroller yapilir.
9. Yalniz dogrulanabilen tamamlanma durumu gecmise kaydedilir.

## J-002 — Symptom -> evidence-guided diagnosis -> repair guide

**Evidence:** Q012, Q022-Q024, Q056-Q058

1. Kullanici belirtiyi gunluk dille, motosiklet bolgesiyle veya gorsel uzerinden ifade eder.
2. Ne zaman/hangi kosulda ortaya ciktigi belirtilir.
3. Tehlike kontrolu yapilir.
4. Kolay, guvenli ve ayirt edici kontroller sunulur.
5. Olasiliklar kesin teshis gibi degil, kanit durumu ile gosterilir.
6. Bir nedenin `en olasi` denebilmesi icin birden fazla ayirt edici kanit onu desteklemeli ve alternatifler degerlendirilmis olmalidir.
7. Benzer guclu olasiliklar kalirsa ayristirici guvenli kontroller onerilir; rastgele parca degisimi onerilmez.
8. Yeterli kanit olusursa uygun onarim/islem rehberine baglanir.
9. Makul kontroller sonucu neden dogrulanamazsa `Neden dogrulanamadi` sonucu, yapilan kontroller ve guvenli kullanim belirsizligiyle kapanir; ozet uzmana aktarilabilir.

## J-003 — Guide mismatch / modification / unexpected physical state

**Evidence:** Q019, Q025-Q026, Q036-Q039

1. Kullanici rehberdeki durumla motosiklette gordugu durumun uyusmadigini fark eder veya modifikasyon olabilecegi ortaya cikar.
2. Normal rehber ilerlemesi durur.
3. Kullanici-dostu ozellikler ve gerekirse gorsel sorularla ilgili versiyon/modifikasyon ayristirilmaya calisilir.
4. Fark fotograf/not gibi kanitla kaydedilebilir.
5. Uygun rehber eslesmesi yeniden belirlenir.
6. Uygunluk kanitlanmadan bu farka bagli kritik uygulamali adim gosterilmez.
7. Gerekirse guvenli geri donus veya profesyonel yardim yolu sunulur.

## J-004 — User gets stuck on an otherwise matching guide

**Evidence:** Q025

1. Kullanici adimi anlayamaz veya uygulayamaz.
2. Yakin plan fotograf, isaretlenmis parca, hareket yonu ve sik hatalar acilir.
3. Gerekirse daha ayrintili video/aciklama sunulur.
4. Hala uyusmazlik varsa kullanici ilerlemeyi durdurabilir.

## J-005 — Mistake / unexpected behavior -> safe recovery

**Evidence:** Q027

1. Kullanici yanlis bir sey yaptigini veya beklenmeyen davranisi fark eder.
2. Normal ilerleme hemen durur.
3. Guvenliyse motosikleti emniyete alma ve dokunulmaması gereken parcalar aciklanir.
4. Hata kaniti fotograf/not ile saklanir.
5. Uygunsa guvenli geri donus; degilse profesyonel yardim yolu gosterilir.

## J-006 — Pause work -> guide changes -> resume safely

**Evidence:** Q028, Q042, Q059

1. Kullanici islemi yarida birakir.
2. Motosiklet, rehber surumu, son tamamlanan adim, sokulu parcalar, olcumler, fotograflar ve notlar korunur.
3. Donuste rehber surumu degismisse farklar devamdan once gosterilir.
4. Kritik duzeltme varsa eski akista ilerleme durur.
5. Motosikletin mevcut fiziksel durumu yeni rehberle yeniden eslestirilir; kullanicinin ilerleme/notlari korunur.
6. `Devam etmeden once` guvenlik kontrolu yapilir.
7. Kullanici guvenli sekilde devam eder veya yeniden degerlendirme/yardim yoluna gecer.

## J-007 — Maintenance due -> prioritize -> remind -> perform/record/postpone

**Evidence:** Q031-Q033, Q061, Q064

1. Ureticinin motosiklete uygun kilometre/sure araliklari ve dogrulanmis son tamamlanma kaydi kullanilir.
2. Dogrulanmis motosiklete ozel bilgi varsa kullanim kosulu zamanlamayi gerekcesiyle etkileyebilir.
3. Birden fazla gecikmis bakim varsa guvenlik/kullanim etkisi, gecikme ve uygun kullanim kosullariyla gerekceli oncelik belirlenir.
4. Kullanici yaklasan/due/overdue hatirlatmalarini gorur; tam cadence kurallari hala discovery konusudur.
5. Kullanici islemi erteleyebilir; erteleme tamamlanma sayilmaz.
6. Islemi kendi yapabilir veya disarida yaptirabilir.
7. Dogrulanmis tamamlanma bilgisi girildiginde sonraki bakim hesabi buradan devam eder.

## J-008 — Review historical work after guide changed/was recalled

**Evidence:** Q029-Q030, Q043, Q060

1. Kullanici gecmis islemi acar.
2. Islemin nedeni, parca/malzeme, tarih/kilometre, olcumler, son kontroller, fotograflar, notlar, isi yapan kisi ve kullanilan rehber surumu gorulur.
3. Rehber sonradan degismis veya geri cekilmisse tarihsel kayit sessizce yeniden yazilmaz.
4. Geri cekilme/duzeltme nedeni ve gerekiyorsa yeniden kontrol uyarisi kayda eklenir.
5. Kullanici onceki durumla bugunku durumu karsilastirabilir ve gerekiyorsa kontrol/yardim aksiyonuna gecer.

## J-009 — Content critical error / unresolved source conflict

**Evidence:** Q041-Q044

1. Rehberin kaynagi guncellenir, kritik hata bulunur veya guvenilir kaynaklar cozulmeden celisir.
2. Etkilenen uygulamali adimlar yeniden inceleme sonuclanana kadar askiya alinir/durdurulur.
3. Celismeyen hazirlik ve guvenlik bilgileri gosterilebilir.
4. Belirsizlik ve ilgili kaynaklar aciklanir.
5. Kritik hata varsa etkilenmis kullaniciya etkilenen adim, gerekli kontrol ve yardim yolu ile uyari verilir.
6. Yeni surum degisiklik gerekcesiyle yayimlanir; eski surum tarihsel kayitlar icin korunur.

## J-010 — Task-specific readiness -> learn or stop

**Evidence:** Q050-Q053

1. Kullanici ileri bir islemi acmak ister.
2. Benzer is gecmisi, arac/olcum bilgisi, onceki kayitlar ve on kosul anlayisi degerlendirilir.
3. Eksik beceri guvenli bicimde ogrenilebiliyorsa temel hazirlik/ogrenme yoluna yonlendirilir.
4. Hassas olcum, dogru sikma, guvenli kaldirma gibi zorunlu ekipman eksikse islem ertelenir.
5. Hatanin sonucu ciddi veya dogrulamasi uzmanlik gerektiriyorsa kritik uygulama adimi acilmaz.

## J-011 — Multi-motorcycle context switching

**Evidence:** Q062

1. Kullanici birden fazla motosiklet kaydina sahiptir.
2. Her motosikletin bilgisi, gecmisi, rehberleri ve hatirlatmalari ayri kalir.
3. Kullanici motosikletler arasinda kolayca gecer.
4. Aktif motosiklet baglami her zaman gorunur olur.
5. Bir motosikletin kaydi/davranisi digerine karismaz.

## J-012 — Add external/service work to history

**Evidence:** Q063

1. Kullanici serviste veya baska biri tarafindan yapilan islemi ekler.
2. Kaynagi `serviste yapildi` / `baskasi yapti` gibi belirtilir.
3. Tarih, kilometre, yapilan is, fatura ve not eklenebilir.
4. Kanit yoksa kayit dogrulanmis tamamlanma gibi gosterilmez.
5. Hangi kanitin hangi guven seviyesine yol actigi ve eski kaydin nasil duzeltilecegi hala aciktir.

## Open journey gaps

- Kullanici-dostu kimlik/fotograf yeterli olmadiginda ek varyant kaniti alma yolculugu
- Yanlis/eksik gecmis kaydini duzeltme ve duzeltme izini koruma
- Kullanici/topluluk katkisi, moderation ve duzeltme onerisi yolculugu
- Sosyal/ticari destek ozellikleri varsa rehberlikle iliskisi
- Ucretli deger varsa satin alma/paketleme deneyimi (model henuz secilmedi)
- Notification onceligi belli olduktan sonra coklu gecikmede cadence ve kullanici kontrolu
