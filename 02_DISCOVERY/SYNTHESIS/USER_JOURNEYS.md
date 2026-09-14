# USER JOURNEYS

Status: DRAFT

Kullanicilarin teknik implementasyon detayindan bagimsiz uc uca urun yolculuklari.

## J-001 — Known task -> prepare -> execute -> verify -> record
**Evidence:** Q006, Q013-Q021, Q029-Q030, Q050-Q053, Q096-Q099
1. Kullanici yapmak istedigi islemi bilir.
2. Motosiklet/rehber eslesmesi ve readiness dogrulanir.
3. Amac, uygunluk, risk, sure/maliyet, arac/parca/ekipman ve kullanilabilirlik gorulur.
4. Zorunlu eksik/kritik beceri eksigi varsa application adimi acilmaz; sebep ve remediation gosterilir.
5. Rehber ihtiyac duyulan ayrinti/hizi sunar; safety/kritik dogrulama degismez.
6. Kritik adimlarda gorsel/olcum/basari kontrolu bulunur.
7. Yeni risk/mismatch olusursa uygulamali progression o noktada durur.
8. Son kontrollerden sonra yalniz dogrulanabilen completion gecmise kaydedilir.

## J-002 — Symptom -> evidence-guided diagnosis -> repair guide
**Evidence:** Q012, Q022-Q024, Q056-Q058
1. Belirti gunluk dil/bolge/gorselle ifade edilir.
2. Tehlike kontrolu yapilir.
3. Guvenli ayirt edici kontroller sunulur.
4. Olasiliklar evidence status ile daralir.
5. `En olasi` icin birden fazla ayirt edici kanit ve alternatiflerin degerlendirilmesi gerekir.
6. Yeterli kanit varsa onarim rehberine gecilir.
7. Sonuc yoksa `Neden dogrulanamadi`, kontrol ozeti ve guvenli kullanim belirsizligiyle kapanabilir; uzman handoff'u mumkundur.

## J-003 — Guide mismatch / modification / variant uncertainty
**Evidence:** Q019, Q025-Q026, Q036-Q039, Q066-Q067, Q102-Q104
1. Rehber-gercek motosiklet uyusmazligi veya modifikasyon ihtimali ortaya cikar.
2. Normal application progression durur.
3. Kullanici-dostu ozellikler, gorunur donanim ve fotograflarla ayrim denenir.
4. Versiyon/modifikasyon yeterince belirlenirse uygun rehber eslesmesi kurulur.
5. Yaygin aftermarket icin verified adapted guide varsa ona gecilir.
6. Unique/custom durumda uygunluk dogrulanamiyorsa eksik evidence aciklanir; teaching-only genel bilgi kalabilir.
7. Zarar verebilecek sokme/baglama/ayar adimlari dogrulanana kadar acilmaz.

## J-004 — User gets stuck on matching guide
**Evidence:** Q025
1. Kullanici adimi anlayamaz/uygulayamaz.
2. Yakin plan, isaretleme, hareket yonu ve sik hatalar acilir.
3. Gerekirse detayli video/aciklama sunulur.
4. Uyum hala yoksa ilerleme durdurulabilir.

## J-005 — Mistake / unexpected behavior -> safe recovery
**Evidence:** Q027
1. Normal ilerleme durur.
2. Guvenliyse motosikleti emniyete alma ve dokunulmaması gereken alanlar aciklanir.
3. Fotograf/not kaniti saklanir.
4. Uygunsa guvenli geri donus; degilse profesyonel yardim yolu gosterilir.

## J-006 — Pause work -> guide changes -> resume safely
**Evidence:** Q028, Q042, Q059
1. Islem baglami ve rehber surumu korunur.
2. Donuste surum farklari gosterilir.
3. Kritik duzeltmede eski akis durur.
4. Mevcut fiziksel durum yeni rehberle yeniden eslestirilir; ilerleme/notlar korunur.
5. `Devam etmeden once` safety kontrolu yapilir.

## J-007 — Maintenance due -> prioritize -> remind -> perform/record/postpone
**Evidence:** Q031-Q033, Q061, Q064, Q070-Q072, Q075-Q077, Q111-Q113
1. Dogrulanmis uretici km/sure plani ve completion kaydi kullanilir.
2. Dogrulanmis istisna/kullanim kosulu varsa gerekcesiyle plan degisir.
3. Veri eksikse belirsizlik gizlenmez.
4. Coklu gecikmis is safety/kullanim etkisi ve gerekceyle onceliklenir.
5. Routine reminders gruplanabilir/ertelenebilir; kritik safety ayri gorunur.
6. Kritik konu uzun sure aciksa app icinde belirgin safety summary ve ilk action gosterilir.
7. Uzun aradan donuste notification flood yerine catch-up summary sunulur.
8. Erteleme completion sayilmaz; verified completion sonraki hesabi ilerletir.

## J-008 — Review/correct historical work
**Evidence:** Q029-Q030, Q043, Q060, Q073-Q074, Q109-Q110
1. Kullanici gecmis islemi acar.
2. Islem nedeni, tarih/km, parca/malzeme, olcum/son kontrol, fotograf/not, yapan kisi ve rehber surumu gorulur.
3. Hata varsa kayit duzeltilir fakat eski/yeni deger, zaman ve neden korunur.
4. Duzeltmenin bakım planina etkisi gosterilir.
5. Evidence level gorunur olur; `verified` mutlak garanti gibi sunulmaz.
6. Rehber geri cekildiyse tarihsel kayit sessizce yeniden yazilmaz.

## J-009 — Content critical error / unresolved source conflict
**Evidence:** Q041-Q044, Q081-Q083
1. Kaynak guncellenir, kritik hata/uyusmazlik bulunur veya community duzeltmesi gelir.
2. Etkilenen application adimi yeniden inceleme bitene kadar askiya alinir/durdurulur.
3. Celismeyen teaching/preparation/safety bilgisi gosterilebilir.
4. Belirsizlik ve kaynak baglami aciklanir.
5. Etkilenen kullanicilar gerekli kontrol/yardim yoluyla uyarilir.
6. Kabul edilen degisiklik gerekcesiyle yeni surum yayimlanir; tarihsel surum korunur.

## J-010 — Task-specific readiness -> re-validate -> learn/stop/resume
**Evidence:** Q050-Q053, Q096-Q099
1. Kullanici ileri bir islem acmak ister.
2. Goreve ozel readiness sinyalleri ve zorunlu safety kosullari degerlendirilir.
3. Eksik kosul varsa neden, nasil tamamlanacagi ve nasil yeniden kontrol edilecegi gosterilir.
4. Kullanici sonucu yanlis bulursa fotograf/olcum/alternatif kontrolle re-validation isteyebilir.
5. Salt `yapabilirim` beyani safety gate'i kaldirmaz.
6. Guvenle ogrenilebilen eksiklik teaching/preparation yoluna gider.
7. Kosul tamamlaninca kullanici onceki rehber baglamina geri donebilir.

## J-011 — Multi-motorcycle context switching
**Evidence:** Q062
1. Her motosikletin bilgisi/gecmisi/rehberi/reminder baglami ayri kalir.
2. Kullanici motorlar arasinda kolay gecer.
3. Aktif motosiklet her zaman anlasilir olur.
4. Kayitlar birbirine karismaz.

## J-012 — Add external/service work to history
**Evidence:** Q063, Q074, Q109-Q110
1. Kullanici serviste/baska biri tarafindan yapilan isi ekler.
2. Provenance belirtilir.
3. Tarih/km/islem/fatura/fotograf/not gibi destekler eklenebilir.
4. Evidence level gorunur olur; kanit yoksa verified completion gibi sunulmaz.
5. Context-specific evidence taxonomy hala discovery konusudur.

## J-013 — High-consequence learning -> conditional application -> professional option
**Evidence:** Q068-Q069, Q099-Q101
1. Kullanici high-consequence sistemi ogrenmek ister.
2. Riskler, gerekli bilgi, ekipman, hazirlik ve kritik kontroller teaching katmaninda aciklanir.
3. Ilk fiziksel mudahaleden once application kosullari dogrulanir.
4. Kosul dogrulanamiyorsa application kapanir; teaching/preparation devam eder.
5. Profesyonel yardim gerekiyorsa eksik kosulla gerekcelendirilir; `sen yapamazsin` dili kullanilmaz.
6. Diagnosis capture, fotograf, preparation ve result-check destegi profesyonel yolda da kalir.
7. Exact escalation trigger aciktir.

## J-014 — Community contribution -> review -> publish/hold -> appeal
**Evidence:** Q080-Q084, Q105-Q108
1. Kisisel not/fotograf default-private kalir.
2. Kullanici explicit secimle community katkisi yapar; personal info ayiklanir.
3. Katki resmi rehberden ayri provenance/review status ile tutulur.
4. Kaldirma varsa somut gerekce, ilgili kural ve sorunlu bolum gosterilir.
5. Kullanici duzeltip yeniden gonderebilir veya itiraz edebilir.
6. Tekrarlanan yanlista contribution pre-review'a alinabilir; kasitli/surekli tehlikeli tekrarda paylasim yetkisi kisitlanabilir.
7. Faydalı ama teknik olarak dogrulanamayan deneyim `dogrulanmamis kisisel deneyim` olarak kalabilir.
8. Tehlikeli icerige maruz kalan kullanicilar gerekiyorsa uyarilir.

## J-015 — Commercial support without technical influence
**Evidence:** Q085-Q088, Q114-Q115
1. Kullanici teknik uygunluk kriterini gorur.
2. Servis/usta veya satin alma secenekleri core rehberin ardindan destek yuzeyi olarak gorulebilir.
3. Sponsorlu teklif acikca isaretlenir.
4. Odeme/sponsorluk teknik uygunluk kararini veya alternatifleri degistiremez.
5. Premium deger core safety/guide/data portability disinda convenience/analysis/capacity etrafinda kalir.
6. Final recurring/one-time/hybrid model aciktir.

## J-016 — Roadside / offline continuity -> stale critical hold
**Evidence:** Q090-Q091, Q122
1. Kullanici garaj disinda sorun yasar.
2. Hizli belirti taramasi ve oncelikli safety kontrolleriyle baslar.
3. Indirilmis rehber/gorsel/safety/progress/history offline acilir.
4. Icerik surumu ve son dogrulama zamani gorulur.
5. Critical freshness limit asilmissa teaching/reference erisimi kalabilir ancak application online re-check'e kadar kapanabilir.
6. Suruse devam belirsizligi saklanmaz.

## J-017 — User data view/edit/export/delete
**Evidence:** Q092-Q094
1. Kullanici motosiklet/kayit/not/fotograf verisini gorur ve duzeltebilir.
2. Not/fotograf ekleyebilir veya silebilir.
3. Kendi verisini anlasilir, yeniden kullanilabilir bicimde export eder; export premium olmaz.
4. Silme oncesi kapsam ve geri alinmazlik aciklanir.
5. Silinen/bekleyen durum anlasilir olur.
6. Baska hesap verileri etkilenemez.

## J-018 — Shared motorcycle collaboration
**Evidence:** Q116, Q118-Q119
1. Owner baska bir kisiye motosiklet kaydina katkida bulunma izni verir.
2. Islem yapan kisi kendi attribution'i ile kayit ekler.
3. Yapan kisi, zaman ve edit trail gorunur olur.
4. Baskasinin kaydi sessizce overwrite edilemez.
5. Private notes diger katilimcilara otomatik acilmaz.
6. Owner izinleri geri alabilir.

## J-019 — Record-only owner -> later guided repair
**Evidence:** Q117
1. Kullanici kendi tamirini yapmak istemeden history/reminder odakli baslar.
2. Belge/fotograf, yaklaşan bakım ve motosiklet ayrimi degeri alir.
3. Daha sonra belirli bir kayit veya ihtiyaçtan guided repair'e gecmek isterse mevcut motorcycle/history context'i kullanilir.

## J-020 — Ownership transfer
**Evidence:** Q120
1. Owner motosikleti satar/devreder.
2. Aktarilacak vehicle-history kayitlarini ve kanitlari secer.
3. Personal notes ve kimlik/konum iceren fotograflar default-private kalir.
4. Transfer oncesi preview yapilir.
5. Parsiyel transferin yeni sahibine completeness olarak nasil anlatilacagi aciktir.

## J-021 — Archive motorcycle -> restore later
**Evidence:** Q121
1. Kullanici motosikleti aktif garajdan kaldirmak ister ama history'yi silmek istemez.
2. `Archive` motosikleti aktif listeden cikarir, history'yi korur.
3. Kullanici daha sonra arayip acabilir.
4. Isterse yeniden active hale getirir.
5. Archive delete ile karistirilmaz.

## J-022 — First use -> experience guide value -> defer account/permissions
**Evidence:** Q123
1. Kullanici ilk acilista motosikletini secer.
2. Rehber deneyiminin nasil calistigini hizla gorur.
3. Account creation, notification permission ve uzun profil ilk degerden once zorunlu olmaz.
4. Kayit/esitleme veya ilgili ihtiyac ortaya ciktiginda gerekli commitment istenir.

## J-023 — Accessible active-repair consumption
**Evidence:** Q124-Q125
1. Kullanici acik Turkce, alisilmis birimler ve deneyimine uygun terminoloji derinligiyle rehberi okur.
2. Buyuk yazi/dugme, high contrast ve non-color-only warnings bilgi erisimini destekler.
3. Image descriptions ve video captions alternatif bilgi kanali saglar.
4. Kirli/mesgul ellerde voice/easy-touch adim ilerleme degeri vardir.
5. Safety-critical confirmation'in alternatif etkileşimde nasil korunacagi aciktir.

## Open journey gaps

- Professional escalation exact trigger, self-remediation ile professional path arasindaki ayrim ve self-service'e geri donus
- Professional/servis kullanicisinin target user mi collaboration participant mi oldugu
- Gercek delete, community contribution withdrawal ve export provenance lifecycle
- Selective ownership transfer'da eksik history'nin yeni sahibe nasil anlatilacagi
- Evidence labels'in technical guide / history / community / external service baglamlarinda ayrisma ihtiyaci
- Critical freshness expiry'nin hangi rehberlerde ve hangi product semantigiyle uygulanacagi
- Active-repair voice/easy-touch safety confirmations
- Premium packaging (model henuz secilmedi)
