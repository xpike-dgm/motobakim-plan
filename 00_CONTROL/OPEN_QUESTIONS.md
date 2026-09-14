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

### Q-0002 — Motosiklete ozellik icin gerekli kimlik bilgileri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Motosiklete ozel rehber hedefi; Batch 01 Q008-Q009 kismi cevap  
**Question:** Marka, model, uretim yili ve islemi degistiren ABS benzeri ozelliklere ek olarak motor tipi/kodu, pazar varyanti, uretim donemi, fabrika opsiyonu veya sonradan yapilan modifikasyonlardan hangileri rehber eslesmesi icin gerekir?  
**Impact:** Onboarding, icerik esleme ve rehber guvenligi.  
**Resolution:** Batch 01 minimum olarak marka, model, uretim yili ve islemi degistiren ozellikleri CONFIRMED etti; eksiksiz kimlik seti henuz acik.

### Q-0003 — Teknik mudahale kapsaminin ust ve alt siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Rutin bakim disinda mekanik/elektriksel/genis mudahale hedefi; Batch 01 Q020, Q034  
**Question:** Hangi islem kategorileri kosullu olarak rehberlenebilir, hangileri sadece bilgilendirilebilir ve varsa hangileri uygulamali rehberlik disinda tutulmalidir?  
**Impact:** Urun kapsami, icerik katalogu ve guvenlik modeli.  
**Resolution:** Batch 01, uygunluk/kritik deger/sonuc dogrulamasi eksikse uygulamali rehberligin durmasini CONFIRMED etti; kategori bazli kesin sinir henuz acik.

### Q-0004 — Tehlikeli veya uzmanlik gerektiren islemler
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q018-Q021, Q034  
**Question:** Fren, direksiyon, yuksek gerilim, yakit, kaldirma/destekleme, motor ici islemler gibi yuksek-sonuclu alanlarda gerekli beceri, ekipman, on kosul ve durdurma kurallari nasil farklasmali?  
**Impact:** Urun guvenligi ve kapsam politikasi.  
**Resolution:** Tehlikeli icerigin tamamen saklanmamasi, fakat kosullar yetersizse uygulamali ilerlemenin durmasi CONFIRMED; kategori bazli politika acik.

### Q-0010 — Hatirlatma davranisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q032-Q033  
**Question:** Hatirlatma yogunlugu/islem onceligi bakim turu, risk, gecikme suresi veya birden fazla gecikmis islem durumuna gore nasil farklasmali?  
**Impact:** Notification UX ve product rules.  
**Resolution:** Yaklasan/due/overdue genel davranisi ve kullanici ayari CONFIRMED; kategori/oncelik kurallari acik.

### Q-0013 — Icerik governance ve insan incelemesi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q010-Q011  
**Question:** `Insan incelemesi` kullanici icin ne anlama gelmeli; kaynak onceligi, guncelligin takibi, duzeltme/geri cekme ve cozulmeyen kaynak celiskilerinde urun hangi kurallari izlemeli?  
**Impact:** Icerik guveni ve operasyonel kalite modeli.  
**Resolution:**

### Q-0014 — Modifikasyon ve fabrika disi degisikliklerin etkisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q-0002'nin derinlesmesi  
**Question:** Sonradan yapilan modifikasyonlar, aksesuarlar veya parca degisiklikleri rehber eslesmesini nasil etkilemeli ve kullanici bunlari nasil belirtmeli?  
**Impact:** Rehber dogrulugu ve safety gate.  
**Resolution:**

### Q-0015 — Gorsel icerik bulunamadiginda fallback
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q015, Q025  
**Question:** Gercek motosiklet/varyantina ait uygun fotograf veya video yoksa hangi alternatif anlatim bicimleri kabul edilebilir ve hangi durumda rehber ilerlememeli?  
**Impact:** Icerik kapsami ve rehber guvenilirligi.  
**Resolution:**

### Q-0016 — Guvenli esdeger arac/malzeme kriteri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q017  
**Question:** Bir arac, sarf veya malzeme hangi kosullarda `guvenli esdeger` kabul edilebilir; hangi tur kalemlerde alternatif kesinlikle onerilmemeli?  
**Impact:** Readiness ve guvenlik kurallari.  
**Resolution:**

### Q-0017 — Teshiste yeterli kanit esigi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q022-Q024  
**Question:** Bir teshis yolculugunda onarim rehberine gecmek veya `henuz yeterli kanit yok` demek icin kullanici acisindan hangi kanit esigi bekleniyor; esit olasiliklar ve sonucsuz testlerde ne olmali?  
**Impact:** Diagnosis guveni ve yanlis parca degisimi riski.  
**Resolution:**

### Q-0018 — Kullanici beceri/readiness degerlendirmesi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q020-Q021, Q034  
**Question:** Kullanici belirli bir islem icin gerekli beceriye sahip olup olmadigini nasil anlamali; uygulama hangi on kosullari sormalı veya gostermeli?  
**Impact:** Tehlikeli/ileri islem guvenligi.  
**Resolution:**

### Q-0019 — Rehber surumu degistiginde davranis
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q028-Q030  
**Question:** Yarim kalan veya gecmiste tamamlanmis bir islemin rehberi daha sonra degisirse kullaniciya hangi farklar gosterilmeli ve devam eden islemde eski/yeni rehber arasinda nasil karar verilmeli?  
**Impact:** Guvenli resume ve gecmisin anlamlandirilmasi.  
**Resolution:**

### Q-0020 — Monetization beklentisi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 saturation: LOW  
**Question:** Kullanici hangi degerler icin odeme yapmaya acik olabilir, nelerin ucretsiz olmasini bekler ve ticari model teknik guvene nasil zarar vermemeli?  
**Impact:** Urun stratejisi ve ticari sinirlar.  
**Resolution:**

### Q-0021 — Kullanici katkisi / moderation / content governance
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 saturation: LOW  
**Question:** Kullanici notu, fotografi, yorum, duzeltme veya topluluk katkisi urunde yer alacaksa hangi iceriklerin diger kullanicilara gorunmesi ve nasil denetlenmesi bekleniyor?  
**Impact:** Icerik guveni, moderation ve urun kapsami.  
**Resolution:**

### Q-0022 — Birden fazla motosiklet ve gecmis duzeltme
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q028-Q033  
**Question:** Kullanici birden fazla motosikleti nasil yonetmek ister; yanlis/eksik eski kayit nasil duzeltilmeli ve disarida yapilan isin dogrulanma seviyesi ne olmalidir?  
**Impact:** Gecmis guveni ve bakım takibi.  
**Resolution:**

### Q-0023 — Sosyal/ticari ozelliklerin urun siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q035  
**Question:** Topluluk, servis bulma, parca satin alma veya benzeri sosyal/ticari ozelliklerden hangileri urunun temel teknik rehberligini destekleyebilir; hangileri dikkat dagitici veya guven bozucu olur?  
**Impact:** Non-goals ve urun kapsam siniri.  
**Resolution:**

### Q-0024 — Bakim istisnalari ve agir kullanim
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Batch 01 Q031  
**Question:** Agir kullanim, uzun sure kullanmama, farkli iklim/kosul, degismis parca veya uretici istisnalari bakim zamanlamasina nasil yansimasi beklenir?  
**Impact:** Bakim kurallari ve reminder dogrulugu.  
**Resolution:**

---

## Answered Questions

### Q-0001 — Dogrulanmis teknik bilgi standardi
**Status:** ANSWERED  
**Evidence:** Batch 01 Q010-Q011  
**Resolution:** Kullanici; motosiklet/varyantla uyumlu uretici servis kilavuzu, parca katalogu veya teknik bulten gibi kaynaklar, belge surumu ve sayfa/bolum kaniti ile insan incelemesi bekliyor. Internet tekrarini tek basina yeterli saymiyor. Guvenilir kaynaklar celisirse kaynaklar yan yana gorulmeli ve kritik fark cozulmeden tek deger secilmemeli.

### Q-0005 — Deneyim seviyesine gore rehber farkliligi
**Status:** ANSWERED  
**Evidence:** Q007, Q014  
**Resolution:** Yeni kullanici her hareketi gorsel/aciklamayla; deneyimli kullanici kisa checklist ve teknik detaya hizli erisimle gormek istiyor. Guvenlik ve kritik dogrulama ikisinde de ayni kalmali.

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
**Resolution:** Motor, islem/neden, tarih, kilometre, parca/malzeme, olcum ve son kontroller, fotograflar, notlar, yasanan sorun, isi yapan kisi ve rehber surumu saklanmak istenir; yarim/doğrulanamayan is tamamlandi sayilmaz.

### Q-0011 — Ariza teshisi ve onarim rehberligi ayrimi
**Status:** ANSWERED  
**Evidence:** Q012, Q022-Q024  
**Resolution:** Teshis belirtiden baslayip tehlike kontrolu ve ayirt edici kontrollerle kanit toplayan bir surectir; yeterli kanit olustugunda onarim rehberine baglanir. Olası neden kesin teshis gibi sunulmaz.

### Q-0012 — Islem sirasinda beklenmeyen durum
**Status:** ANSWERED  
**Evidence:** Q025-Q028  
**Resolution:** Takilma/uyumsuzluk/hata durumunda daha ayrintili destek saglanir, gerekirse normal ilerleme durur; emniyete alma, dokunmama bilgisi, kanit kaydi, guvenli geri donus/profesyonel yardim yolu ve yarim islem baglaminin korunmasi beklenir.

---

## Kullanim Kurali

Yeni bir belirsizlik ortaya ciktiginda ayni format kullanilir. Soru ancak kullanici cevabi veya yetkili karar sureciyle `ANSWERED` yapilir. Genis bir soru cevaplandiginda daha dar yeni sorular acilabilir; eski cevap sessizce silinmez.
