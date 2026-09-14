# OPEN QUESTIONS

Bu dosya, proje hafizasinda henuz kesinlesmemis konulari, celiskileri ve ileride cevaplanmasi gereken sorulari tutar.

Bir AI burada bulunan bir konuyu kendi varsayimiyla kapatamaz. Kesin cevap kullanicidan veya yetkili karar surecinden gelmelidir.

## Status Values

- `OPEN`
- `BLOCKED`
- `ANSWERED`
- `CANCELLED`

---

## Aktif Sorular

### Q-0004 — High-consequence islemlerde profesyonel yardim / uygulamali stop siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01-03 safety discovery; Q068-Q069 son genisleme  
**Question:** Yuksek gerilim ve diger high-consequence islemlerde kullanici ogrenmeye devam ederken hangi noktada uygulamali adim kesin durmali ve profesyonel yardim/escalation onerisi devreye girmelidir?  
**Impact:** Urun guvenligi ve self-service siniri.  
**Resolution so far:** High-consequence kategoriler otomatik kapsam disi degil; risk, bilgi, ekipman, motosiklete ozel surec ve kritik safety kosullari dogrulanmadan uygulamali ilerleme acilmaz. Fren/direksiyon/yakit/kaldirma/motor-ici icin somut stop kosullari vardir. Profesyonel yardima gecisin kullanici deneyimi ve override siniri aciktir.

### Q-0026 — Ucretli model / paketleme
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q065, Q087-Q088  
**Question:** Ucretsiz core korunurken premium deger abonelik, tekil ozellik/icerik veya baska bir modelle nasil paketlenmesi beklenir; hangi ticari model kullanici icin en adil/anlasilir olur?  
**Impact:** Ticari strateji.  
**Resolution so far:** Motora uygun ayrintili rehber, kritik safety ve temel bakim takibi ucretsiz bekleniyor. Gelismis analiz, ek depolama ve coklu garaj yonetimi ucretli deger ornekleri; sponsor/ticari etki teknik karari degistiremez. Fiyat/paket modeli secilmedi.

### Q-0027 — Kullanici motivasyonlari ve segment farklari
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q089 tek kullanici motivasyon sirasi  
**Question:** Yeni/deneyimli veya farkli kullanim baglamlarindaki hedef kullanicilarin self-service, ogrenme, maliyet, zaman, hobi ve acil ihtiyac motivasyonlari nasil farklasir ve urun beklentisini nasil degistirir?  
**Impact:** User segmentation ve prioritization.  
**Resolution so far:** Mevcut kullanici icin oncelik sirasi: islemi kendi tamamlamak -> ogrenip bagimsizlasmak -> masraf azaltmak -> zaman kazanmak -> keyif. Bunun tum kullanicilara genellenmesi desteklenmiyor.

### Q-0030 — Readiness yanlis engelleme / fazla serbest birakma ve override
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** ASM-016; Q050-Q052  
**Question:** Readiness degerlendirmesi kullaniciyi gereksiz durdurursa veya kullanici kendisini daha yetkin gorurse ne olmasi beklenir; hangi safety kapilari override edilemez?  
**Impact:** Kullanici ozerkligi ve safety gating dengesi.  
**Resolution:**

### Q-0031 — Modifiye motosikletlerde kapsama beklentisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** ASM-015; Q038-Q039, Q075  
**Question:** Yaygin aftermarket degisikliklar ile benzersiz/custom modifikasyonlarda MotoBakim'dan ne kadar rehber, ayristirma ve bakım bilgisi beklenir; hangi durumda `dogrulanmis rehber yok` sonucu yeterlidir?  
**Impact:** Icerik katalogu ve modifiye motosiklet kapsam siniri.  
**Resolution:**

### Q-0032 — Community moderation itiraz ve uyusmazliklari
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q080-Q084  
**Question:** Topluluk katkisi yanlis/tehlikeli diye kaldirildiginda, katki sahibi itiraz ettiginde veya faydali ama dogrulanamamis bilgi bulunduğunda hangi durum/gorunurluk/moderation beklentisi vardir?  
**Impact:** Community trust ve governance.  
**Resolution so far:** Kisisel icerik default-private; community explicit opt-in; topluluk icerigi resmi rehberden ayrilir ve provenance/review durumu gosterilir; tehlikeli icerik gorunumden kaldirilip incelenir.

### Q-0033 — Kanit duzeyi ve `incelenmis/dogrulanmis` dilinin siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q074, Q082  
**Question:** Kullanici beyanı, belge/fotograf, kaynak/provenance ve insan incelemesi arasinda hangi seviyelerde hangi dil kullanilmali; `dogrulanmis` veya `incelenmis` etiketi ne zaman hak edilir?  
**Impact:** Gecmis, community ve teknik icerik guveni.  
**Resolution so far:** Fatura/fotograf gibi kanitlar destekleyicidir fakat tek basina otomatik verified statuye donusturulmedi; farkli kanit seviyeleri gorunur olmalidir.

### Q-0034 — Kritik bildirimlerde istisnai tekrar/escalation
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q070-Q072  
**Question:** Kullanici kritik safety konusunu uzun sure gormezden gelirse, birden fazla kritik konu birikirse veya uygulamaya uzun sure girmezse bildirim/uyari davranisi nasil olmali?  
**Impact:** Safety communication ve notification UX.  
**Resolution so far:** Rutinler gruplanabilir, kapatilabilir/ertelenebilir; kritik safety bilgisi telefon bildirimi susturulsa bile uygulama icinde ve ilgili islem oncesi gorunur kalir.

### Q-0035 — Veri lifecycle edge case'leri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q092-Q094, Q080 community sharing  
**Question:** Motosiklet kaydi silindiginde bagli gecmis ne olmali; community'ye paylasilan katki sonradan geri cekilebilir mi; disa aktarimda kanit/degisiklik izi ne kadar korunmali?  
**Impact:** User ownership ve tarihsel guven.  
**Resolution so far:** Kullanici goruntuleme/duzeltme/ekleme-silme/disa aktarma kontrolu ister; export ucretli olmamali; silme kapsami ve geri alinmazlik onceden aciklanmali.

### Q-0036 — Profesyonel/servis kullanicilari hedef kullanici mi?
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Mevcut hedef kullanici kendi motosikletinde islem yapan owner; servis kaydi ve uzman handoff ortaya cikti  
**Question:** Profesyonel usta/servis, bir baskasinin motosikletinde calisan kisi veya yalniz kayit tutan owner MotoBakim'in hedef kullanicisi mi; degilse hangi sinirda desteklenir?  
**Impact:** User types ve scope.  
**Resolution:**

### Q-0037 — Paylasilan motosiklet / ortak calisma
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Multi-motorcycle ve dis islem kaydi var; ayni motosikletin birden fazla kisi tarafindan yonetimi sorulmadi  
**Question:** Ayni motosiklet sahibi, aile uyesi, arkadas veya usta tarafindan birlikte takip edilecekse kayit/gorunurluk/katki beklentisi nedir?  
**Impact:** User journeys ve ownership model beklentisi.  
**Resolution:**

### Q-0038 — Dil, olcu birimi ve erisilebilirlik beklentileri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Design oncesi product discovery coverage boslugu  
**Question:** Kullanici teknik anlatim dili, olcu birimleri, metin/gorsel erisilebilirligi ve farkli okuma/algilama ihtiyaclarinda ne bekler?  
**Impact:** Product inclusivity ve ilerideki design requirements.  
**Resolution:**

### Q-0039 — Motosiklet satma/devretme/arsivleme
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Zengin motosiklet gecmisi ve data ownership  
**Question:** Kullanici motosikleti sattiginda veya artik kullanmadiginda kayit arsivlenmeli mi, devredilmeli mi, nasil gorunmeli; kullanicinin kisisel not/fotograflari ne olmali?  
**Impact:** Long-term history and ownership journey.  
**Resolution:**

### Q-0040 — Offline stale/recall durumunda guvenli davranis
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q090-Q091  
**Question:** Indirilmis rehber sonradan guncellenmis/geri cekilmis olabilirken kullanici offline ise eski icerigin guvenilirlik/guncellik belirsizligi nasil davranmali; kullanici hangi uyariyi bekler?  
**Impact:** Offline safety continuity.  
**Resolution so far:** Indirilmis rehber/gorsel/safety/ilerleme/gecmis offline erisilebilir olmali ve surum/guncellik durumu gorunmelidir.

### Q-0041 — Ilk kullanim / onboarding ve hesap beklentisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Ana urun akislari derinlesti ancak ilk kullanim deneyimi sorulmadi  
**Question:** Kullanici ilk acilista neyi minimum olarak yapmak ister; motosiklet ekleme, hesabı olusturma veya rehberi deneme hangi sirada/zirki zorunlulukta olmalidir?  
**Impact:** Core journey girisi ve design oncesi screen inventory.  
**Resolution:**

---

## Answered Questions

### Q-0001 — Dogrulanmis teknik bilgi standardi
**Status:** ANSWERED  
**Evidence:** Q010-Q011  
**Resolution:** Motosiklet/varyantla uyumlu guvenilir teknik kaynak, belge surumu/sayfa-bolum kaniti ve insan incelemesi beklenir; internet tekrar sayisi yeterli degildir; kritik kaynak celiskisi cozulmeden tek deger secilmez.

### Q-0002 — Kullanici acisindan motosiklet varyanti kimlik kaniti
**Status:** ANSWERED  
**Evidence:** Q036-Q039, Q066-Q067  
**Resolution:** Kullanici teknik kimlikleri, etiketleri veya parca kodlarini ezbere/belge arayarak vermek zorunda birakilmak istemiyor. Urun marka/model/yil, anlasilir ozellikler, gorunur donanim ve farkli acilardan fotograflarla ilgili versiyonu ayristirmaya calismali. Bu kanitlar yetmezse hangi ayrimin eksik oldugu gorunur olmali ve versiyona ozel uygulamali adimlar baslamamalidir. Bu cevap, fotograflarin gercek dunyada her modeli ayirabilecegi feasibility gercegi degildir; ASM-013 aciktir.

### Q-0003 — Teknik mudahale kapsaminin ust ve alt siniri
**Status:** ANSWERED  
**Evidence:** Q020, Q034, Q045-Q052  
**Resolution:** Kullanici kategori bazinda butun sistemleri ogrenebilmek ister. Genel urun siniri mutlak kategori yasagindan cok motosiklet uyumu, gerekli ekipman/beceri/calisma kosulu ve sonucun dogrulanabilirligine dayanir. Kritik kosul eksikse uygulamali rehberlik durur veya hazirlik/ogrenme duzeyinde kalir.

### Q-0005 — Deneyim seviyesine gore rehber farkliligi
**Status:** ANSWERED  
**Evidence:** Q007, Q014  
**Resolution:** Yeni kullanici ayrintili gorsel/hareket anlatimi; deneyimli kullanici kisa checklist/teknik detay ister. Guvenlik ve kritik dogrulama ikisinde de ayni kalmali.

### Q-0006 — `Guvenle yapilabilir` olcutu
**Status:** ANSWERED  
**Evidence:** Q017-Q021, Q034  
**Resolution:** Dogru motosiklet-rehber eslesmesi, dogrulanmis kaynak, hazir arac/parca/ekipman, anlasilmis riskler ve kritik sonucun dogrulanabilir olmasi gerekir; bu kosullar kaybolursa ilerleme durmalidir.

### Q-0007 — Gorsel anlatim gereksinimleri
**Status:** ANSWERED  
**Evidence:** Q014-Q015, Q025  
**Resolution:** Parcayi bulmak icin gercek/isaretli fotograf; gizli baglantida cizim; hareket yonu/sira kritikse kisa video; guvenlik/olcum/kontrol icin acik metin ve temel adimlarda basari kontrolu beklenir.

### Q-0008 — Bakim zamanlamasi kriterleri
**Status:** ANSWERED  
**Evidence:** Q031, Q033  
**Resolution:** Motosiklete uygun uretici kilometre ve sure araliklari temel alinmali, hangisi once dolarsa izlenmeli; onceki dogrulanmis tamamlanma tarihi ve gerekcelendirilebilen kullanim kosullari etkili olabilir; dogrulanmamis aralik uretilmemeli.

### Q-0009 — Bakim gecmisi veri beklentisi
**Status:** ANSWERED  
**Evidence:** Q029-Q030  
**Resolution:** Motor, islem/neden, tarih, kilometre, parca/malzeme, olcum/son kontroller, fotograflar, notlar, sorun, isi yapan kisi ve rehber surumu saklanmak istenir; yarim/dogrulanamayan is tamamlandi sayilmaz.

### Q-0010 — Hatirlatma cadence, grouping ve kullanici kontrolu
**Status:** ANSWERED  
**Evidence:** Q032-Q033, Q064, Q070-Q072  
**Resolution:** Yaklasan/due/overdue davranisi korunur. Onemli fakat acil olmayan konu ilk gorunmede ve yaklasirken hatirlatilabilir; gecikince kullanici haftada en fazla bir ozet tercih eder ve gunluk tekrar istemez. Rutin bakim/kayit bildirimleri gruplanabilir, kapatilabilir/ertelenebilir. Surus guvenligini etkileyen acil uyarilar ayri/belirgin olmali; kritik safety bilgisi telefon bildirimi susturulsa bile uygulama icinde ve ilgili islem oncesinde gorunur kalmalidir. Istisnai escalation Q-0034'te aciktir.

### Q-0011 — Ariza teshisi ve onarim rehberligi ayrimi
**Status:** ANSWERED  
**Evidence:** Q012, Q022-Q024  
**Resolution:** Teshis belirtiden baslayip tehlike kontrolu ve ayirt edici kontrollerle kanit toplayan bir surectir; yeterli kanit olustugunda onarim rehberine baglanir. Olasi neden kesin teshis gibi sunulmaz.

### Q-0012 — Islem sirasinda beklenmeyen durum
**Status:** ANSWERED  
**Evidence:** Q025-Q028  
**Resolution:** Takilma/uyumsuzluk/hata durumunda daha ayrintili destek saglanir, gerekirse normal ilerleme durur; emniyete alma, dokunmama bilgisi, kanit kaydi, guvenli geri donus/profesyonel yardim yolu ve yarim islem baglaminin korunmasi beklenir.

### Q-0013 — Icerik governance ve insan incelemesi
**Status:** ANSWERED  
**Evidence:** Q040-Q044  
**Resolution:** Insan incelemesinde ilgili sistemde uygulamali deneyim ve uyum/kaynak/gorsel/arac/risk/son-kontrol degerlendirmesi beklenir. Kritik rehberde bagimsiz ikinci inceleme ek guven verir fakat tum kritik rehberlerde zorunlu politika olarak kanitlanmamistir. Kritik update/hata/celiski durumunda yeniden inceleme, askiya alma/durdurma, uyari ve tarihsel surumun korunmasi beklenir.

### Q-0014 — Modifikasyon ve fabrika disi degisikliklerin etkisi
**Status:** ANSWERED  
**Evidence:** Q038-Q039  
**Resolution:** Modifiye sistemde fabrika rehberi otomatik uygun sayilamaz. Degisiklik kullaniciya sorulur/gorselle ayristirilmaya calisilir; uygunluk belirlenemezse ilgili kritik adimlar baslamaz.

### Q-0015 — Gorsel icerik bulunamadiginda fallback
**Status:** ANSWERED  
**Evidence:** Q054  
**Resolution:** Gercek varyant fotografi yoksa tam motosiklete ait dogrulanmis cizim veya isaretli sema kabul edilebilir. Baska motosiklet fotografi ayniymis gibi kullanilamaz; fark belirsizse gorsele dayali adim baslatilmaz.

### Q-0016 — Guvenli esdeger arac/malzeme kriteri
**Status:** ANSWERED  
**Evidence:** Q053, Q055  
**Resolution:** Esdeger olcu, uyum, dayanim, malzeme, islev ve guvenlik gerekliliklerini karsilamali. Hassas olcum, dogru sikma veya guvenli kaldirma icin zorunlu ekipman yoksa islem ertelenmelidir.

### Q-0017 — Teshiste yeterli kanit esigi
**Status:** ANSWERED  
**Evidence:** Q056-Q058  
**Resolution:** En olasi neden icin birden fazla ayirt edici belirti/guvenli kontrol ayni nedeni desteklemeli ve alternatifler degerlendirilmelidir. Esit olasiliklarda ayristirici kontroller surer; sonuc yine belirsizse `Neden dogrulanamadi` olarak kapanir. Sabit nicel test sayisi degildir.

### Q-0018 — Kullanici beceri/readiness degerlendirmesi
**Status:** ANSWERED  
**Evidence:** Q050-Q052  
**Resolution:** Benzer is gecmisi, arac/olcum bilgisi, onceki kayitlar ve on kosul anlayisi degerlendirilir; oz-beyan tek basina yeterli degildir. Guvenle ogrenilebilir eksik beceri hazirliga yonlendirilebilir; ciddi sonuclu/uzman dogrulamasi gerektiren kritik adim acilmaz.

### Q-0019 — Rehber surumu degistiginde davranis
**Status:** ANSWERED  
**Evidence:** Q059-Q060  
**Resolution:** Yarim iste surum farklari devamdan once gosterilir; kritik duzeltmede eski akis durur ve mevcut fiziksel durum yeni rehberle eslestirilirken ilerleme/notlar korunur. Tamamlanmis tarihsel kayit sessizce degistirilmez.

### Q-0020 — Monetization baseline
**Status:** ANSWERED  
**Evidence:** Q065  
**Resolution:** Ileri/zengin icerik ve kolayliklar ucretli deger adayi olabilir. Temel dogrulanmis rehber, kritik safety, bakim kaydi ve temel hatirlatmalar ucretsiz beklenir. Guvenlik bilgisini ucretle gizlemek guven bozucudur.

### Q-0021 — Kullanici katkisi / moderation baseline
**Status:** ANSWERED  
**Evidence:** Q080-Q084  
**Resolution:** Kisisel not/fotograf default-private kalir; community paylasimi explicit secimdir ve kisisel bilgiler ayiklanmalidir. Duzeltme onerisi resmi rehbere dogrudan girmez; kaynak/uygunluk/safety etkisi incelenir. Community icerigi kaynak, motosiklet, inceleme durumu ve tarihle resmi rehberden ayrilir. Tehlikeli icerik gorunumden kaldirilip incelenir; resmi rehberi etkilerse ilgili adim durdurulup etkilenenler uyarilir. Moderation edge case'leri Q-0032'de aciktir.

### Q-0022 — Gecmis duzeltme ve dis islem kanit baseline
**Status:** ANSWERED  
**Evidence:** Q073-Q074  
**Resolution:** Hatalı kayit duzeltilebilir; eski/yeni bilgi, degisiklik zamani ve nedeni korunur ve bakim planina etkisi gosterilir. Kullanici beyanı, belgeli islem ve ayrica incelenmis kayit ayni guven seviyesinde gosterilmez; kanit duzeyi gorunur olmalidir. Nihai evidence taxonomy Q-0033'te aciktir.

### Q-0023 — Sosyal/ticari ozelliklerin urun siniri
**Status:** ANSWERED  
**Evidence:** Q084-Q086, Q088  
**Resolution:** Community alani resmi rehberden ayri olmalidir. Servis/usta listesi self-service rehberin yerini almamali. Satin alma seceneklerinden once teknik uygunluk olcutleri gelmeli; sponsorlu teklifler acikca isaretlenmeli. Gizli reklam, ucretli urunu teknik olarak `en uygun` gostermek, alternatif saklamak veya rehberi satis hedefiyle degistirmek guven bozucudur.

### Q-0024 — Bakim istisnalari ve eksik kosul bilgisi
**Status:** ANSWERED  
**Evidence:** Q061, Q075-Q077  
**Resolution:** Degistirilmis parcanin guvenilir araligi bilinmiyorsa sure uydurulmaz/eski aralik otomatik kullanilmaz; takvim belirsiz isaretlenir. Dogrulanmis istisna genel planla birlikte gerekcesiyle gosterilir. Kullanim kosulu bilinmiyorsa bu gizlenmez; gecerli standart plan varsa gosterilir, eksik bilgi sorulur ve cevapla takvim yeniden degerlendirilir.

### Q-0025 — Islem suresi ve maliyet tahmininin guven siniri
**Status:** ANSWERED  
**Evidence:** Q078-Q079  
**Resolution:** Sure hazirlik/gun planlamasi icin deneyime gore aralik olarak faydalidir; sikismis baglanti/hasar/ek sokme ihtimalinde kesin bitis vaadi verilmez. Maliyet parca/sarf/arac/varsa iscilik olarak ayrilir; dahil olmayan kalemler, fiyat tarihi ve varsayimlar gorunur olmalidir.

### Q-0028 — Kullanici verisi uzerinde kontrol
**Status:** ANSWERED  
**Evidence:** Q092-Q094  
**Resolution:** Kullanici kendi motosiklet/kayitlarini gorebilmeli ve duzeltebilmeli; not/fotograf ekleyip silebilmelidir. Hesaplar arasi veri karismasi kabul edilmez. Motosiklet/tarihli islem/not/fotograf verileri anlasilir ve yeniden kullanilabilir bicimde disa aktarilabilmeli ve bu export ucretli olmamalidir. Silme oncesi kapsam/geri alinmazlik aciklanmali ve sonrasinda silinen/bekleyen durum gorunmelidir.

### Q-0029 — Zayif/olmayan baglanti durumunda temel deneyim
**Status:** ANSWERED  
**Evidence:** Q090-Q091  
**Resolution:** Yol kenarinda hizli belirti taramasi, oncelikli safety kontrolleri, kisa gorsel adimlar ve offline erisim beklenir; suruse devam belirsizligi gizlenmez. Indirilmis motosiklete ozel rehber/gorsel/safety uyarisi, kalinan adim ve kisisel gecmis offline acilabilmeli; surum ve guncellik durumu gorunmelidir. Stale/recall edge case Q-0040'ta aciktir.

---

## Kullanim Kurali

Yeni bir belirsizlik ortaya ciktiginda ayni format kullanilir. Soru ancak kullanici cevabi veya yetkili karar sureciyle `ANSWERED` yapilir. Genis bir soru cevaplandiginda daha dar yeni sorular acilabilir; eski cevap sessizce silinmez.
