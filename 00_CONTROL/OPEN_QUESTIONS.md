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
**Context:** Batch 01-04 safety discovery; Q068-Q069, Q096-Q101  
**Question:** Uygulamali akis safety/readiness nedeniyle durdugunda hangi durumda once kullaniciya self-remediation + re-validation yolu sunulmali, hangi durumda profesyonel yardim ozellikle onerilmeli ve profesyonel yardimdan sonra self-service'e geri donus nasil beklenir?  
**Impact:** Urun guvenligi ve self-service siniri.  
**Resolution so far:** Ilk fiziksel mudahaleden once zorunlu kosullar dogrulanmali; yeni risk/uyusmazlik cikarsa akis durmali. Teaching/preparation erisilebilir kalir. Profesyonel yardim `sen yapamazsin` diliyle degil eksik kosulla gerekcelendirilmeli; fakat exact escalation trigger hala aciktir.

### Q-0026 — Ucretli model / paketleme
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q065, Q087-Q088, Q114-Q115  
**Question:** Ucretsiz core korunurken recurring degerler ile tek-seferlik degerler nasil ayrilmali; abonelik, one-time veya hybrid paket kullanici acisindan hangi kosullarda makul olur?  
**Impact:** Ticari strateji.  
**Resolution so far:** Motora uygun ayrintili rehber, kritik safety, temel bakım takibi ve kullanicinin kendi verisini almasi ucretsiz olmali. Gelismis analiz, ek depolama, coklu garaj, kisilestirme premium adayi; yazdirilabilir detayli arsiv veya kisilestirilmis ogrenme araci gibi surekli maliyet yaratmayan optional value icin one-time odeme makul olabilir. Final model secilmedi.

### Q-0027 — Kullanici motivasyonlari ve segment farklari
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q089, Q116-Q117  
**Question:** Core self-service owner, record-only owner, shared-family user, multi-bike owner ve hobby helper gibi desteklenen baglamlarda ana motivasyonlar ve first-use beklentileri nasil farklasmali; hangi segment product priority'de merkezde kalmali?  
**Impact:** User segmentation ve prioritization.  
**Resolution so far:** Core odak bireysel surucunun kendi islemini ogrenip yapmasidir. Multi-bike, shared-family, baskasinin motorunda calisan hobby user ve record-only owner anlamli adjacent context'lerdir. Mevcut kullanici motivasyon sirasi tum segmentlere genellenemez.

### Q-0035 — Veri lifecycle edge case'leri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q080, Q092-Q094, Q120-Q121  
**Question:** Bir motosiklet gercekten silindiginde bagli history ne olmali; community'ye yayinlanan katki sonradan geri cekilebilir mi; export'ta evidence/provenance/edit trail ne kadar korunmali?  
**Impact:** User ownership ve tarihsel guven.  
**Resolution so far:** Archive silmeden ayridir ve reversible'dir. Transferde personal content default-private kalir. Silme kapsam/geri alinmazlik onceden aciklanmali; export ucretsiz ve yeniden kullanilabilir olmalidir. Bu edge case'lerin detaylari aciktir.

### Q-0036 — Profesyonel/servis kullanicilarinin hedef kapsam siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q116-Q119  
**Question:** Profesyonel usta/servis MotoBakim'in dogrudan target user'i mi, yoksa owner/hobby user deneyimini destekleyen collaboration participant mi; profesyonel ihtiyaclar core owner urununu hangi noktada degistirmemeli?  
**Impact:** User types ve scope.  
**Resolution so far:** Baskasinin motosikletinde calisan hobby user ve record-only owner anlamli supported context'lerdir. Shared bike icin owner permission, attribution ve revocable access beklenir. Profesyonel servis target statusu hala aciktir.

### Q-0042 — Evidence taxonomy'nin baglama gore ayrismasi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q074, Q082, Q109-Q110  
**Question:** `Kullanici beyani / belgeli / incelenmis / dogrulanmis` etiketleri bakım kaydi, dis servis kaydi, community icerigi ve resmi teknik rehberde ayni semantigi mi tasimali; hangi baglamlarda farkli guven dili gerekir?  
**Impact:** Trust language ve provenance consistency.  
**Resolution so far:** Etiketlerin temel kullanici anlamlari netlesti. `Dogrulanmis`, kaynak + ilgili motosiklet/islem uygunlugu + inceleme tarihi/karar gorunurlugu bekler ve mutlak garanti degildir. Global tek taxonomy henuz kilitlenmedi.

### Q-0043 — Selective ownership transfer ve history butunlugu
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q120  
**Question:** Kullanici yeni sahibe yalniz sectigi bakım kayitlarini aktarabiliyorsa, yeni sahibin eksik history'yi tam history sanmamasi icin urun hangi seffafligi saglamali?  
**Impact:** Ownership transfer trust.  
**Resolution so far:** Kisisel notlar/kimlik veya konum iceren fotograflar default-private; transfer oncesi preview beklenir. Parsiyel transferin completeness semantigi aciktir.

### Q-0044 — Kritik rehber freshness semantigi
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q091, Q122; ASM-023  
**Question:** Hangi tur kritik rehberlerde freshness expiry mantigi beklenir; stale fakat teaching-only icerik nasil davranmali ve online re-check mumkun olmadiginda kullaniciya hangi secenek/belirsizlik sunulmalidir?  
**Impact:** Offline safety continuity.  
**Resolution so far:** Kritik rehberde son dogrulama zamani gorunmeli; guncellik siniri asildiysa application steps online kontrol edilene kadar kapanabilir. Belirli sure/esik henuz yok.

### Q-0045 — Aktif tamirde erisilebilirlik ve alternatif etkileşim safety siniri
**Status:** OPEN  
**Opened:** 2026-09-14  
**Context:** Q125; ASM-025  
**Question:** Sesli/minimum-dokunuslu rehber, eldiven/kirli el, gurultu veya ekrana bakamama durumunda nasil yardim etmeli; hangi safety-critical teyitler alternatif etkileşimde de atlanamamali?  
**Impact:** Product accessibility ve active-repair usability.  
**Resolution so far:** Buyuk yazi/dugme, yuksek kontrast, renk-disinda uyari, gorsel aciklama, altyazi, sesli adim ve kolay dokunus beklentileri CONFIRMED. Kritik confirmation edge case'i acik.

---

## Answered Questions

### Q-0001 — Dogrulanmis teknik bilgi standardi
**Status:** ANSWERED  
**Evidence:** Q010-Q011  
**Resolution:** Motosiklet/varyantla uyumlu guvenilir teknik kaynak, belge surumu/sayfa-bolum kaniti ve insan incelemesi beklenir; kritik kaynak celiskisi cozulmeden tek deger secilmez.

### Q-0002 — Kullanici acisindan motosiklet varyanti kimlik kaniti
**Status:** ANSWERED  
**Evidence:** Q036-Q039, Q066-Q067  
**Resolution:** Kullanici teknik kod/belge avina zorlanmamalidir. Observable ozellik ve fotograflarla ayrim denenir; yetmezse eksik ayrim gorunur olur ve versiyona ozel application acilmaz. Bu feasibility garantisi degildir.

### Q-0003 — Teknik mudahale kapsaminin ust ve alt siniri
**Status:** ANSWERED  
**Evidence:** Q020, Q034, Q045-Q052  
**Resolution:** Kullanici tum sistemleri ogrenebilmek ister; urun siniri mutlak kategori yasagindan cok motosiklet uyumu, ekipman/beceri/calisma kosulu ve sonucun dogrulanabilirligine dayanir.

### Q-0005 — Deneyim seviyesine gore rehber farkliligi
**Status:** ANSWERED  
**Evidence:** Q007, Q014  
**Resolution:** Yeni kullanici ayrintili gorsel/hareket anlatimi; deneyimli kullanici kisa checklist/teknik detay ister. Safety ve kritik dogrulama ayni kalir.

### Q-0006 — `Guvenle yapilabilir` olcutu
**Status:** ANSWERED  
**Evidence:** Q017-Q021, Q034  
**Resolution:** Dogru motosiklet-rehber eslesmesi, dogrulanmis kaynak, hazir arac/parca/ekipman, anlasilmis riskler ve kritik sonucun dogrulanabilirligi gerekir.

### Q-0007 — Gorsel anlatim gereksinimleri
**Status:** ANSWERED  
**Evidence:** Q014-Q015, Q025  
**Resolution:** Gercek/isaretli fotograf, uygun yerde cizim/video, acik safety/olcum metni ve basari kontrolu beklenir.

### Q-0008 — Bakim zamanlamasi kriterleri
**Status:** ANSWERED  
**Evidence:** Q031, Q033  
**Resolution:** Motosiklete uygun uretici km/sure araliklari ve dogrulanmis completion kaydi temel alinmali; dogrulanmamis aralik uretilmemeli.

### Q-0009 — Bakim gecmisi veri beklentisi
**Status:** ANSWERED  
**Evidence:** Q029-Q030  
**Resolution:** Islem/neden, tarih/km, parca/malzeme, olcum/kontroller, fotograf/not, sorun, yapan kisi ve rehber surumu gibi zengin history beklenir.

### Q-0010 — Hatirlatma cadence, grouping ve kullanici kontrolu
**Status:** ANSWERED  
**Evidence:** Q032-Q033, Q064, Q070-Q072  
**Resolution:** Rutinler gruplanabilir/kapatilabilir/ertelenebilir; acil safety ayrilir ve app icinde korunur. Mevcut kullanici gecikmis routine konuda haftada en fazla bir ozet tercih eder.

### Q-0011 — Ariza teshisi ve onarim rehberligi ayrimi
**Status:** ANSWERED  
**Evidence:** Q012, Q022-Q024  
**Resolution:** Teshis kanit toplar; yeterli kanitla repair guide'a gecer, olasi neden kesin teshis gibi sunulmaz.

### Q-0012 — Islem sirasinda beklenmeyen durum
**Status:** ANSWERED  
**Evidence:** Q025-Q028  
**Resolution:** Takilma/uyumsuzluk/hata normal ilerlemeyi durdurabilir; recovery, kanit kaydi ve profesyonel yardim yolu beklenir.

### Q-0013 — Icerik governance ve insan incelemesi
**Status:** ANSWERED  
**Evidence:** Q040-Q044  
**Resolution:** Uygulamali deneyimli insan incelemesi, content lifecycle re-review/hold/recall ve tarihsel surum korunmasi beklenir; ikinci review ek guvendir fakat evrensel zorunluluk degildir.

### Q-0014 — Modifikasyon ve fabrika disi degisikliklerin etkisi
**Status:** ANSWERED  
**Evidence:** Q038-Q039  
**Resolution:** Modifiye sistemde fabrika rehberi otomatik uygun sayilamaz; uygunluk belirlenmeden kritik adim baslamaz.

### Q-0015 — Gorsel icerik bulunamadiginda fallback
**Status:** ANSWERED  
**Evidence:** Q054  
**Resolution:** Dogrulanmis cizim/sema fallback olabilir; baska motosiklet gorseli ayniymis gibi sunulamaz.

### Q-0016 — Guvenli esdeger arac/malzeme kriteri
**Status:** ANSWERED  
**Evidence:** Q053, Q055  
**Resolution:** Esdeger olcu/uyum/dayanim/malzeme/islev/safety gerekliliklerini karsilamali; kritik ekipman eksiginde islem ertelenebilir.

### Q-0017 — Teshiste yeterli kanit esigi
**Status:** ANSWERED  
**Evidence:** Q056-Q058  
**Resolution:** Birden fazla ayirt edici kanit ve alternatif degerlendirmesi gerekir; belirsizlik surerse `Neden dogrulanamadi` ile kapanabilir.

### Q-0018 — Kullanici beceri/readiness degerlendirmesi
**Status:** ANSWERED  
**Evidence:** Q050-Q052  
**Resolution:** Oz-beyan tek basina yeterli degildir; gorev bazli deneyim/arac/olcum/on-kosul anlayisi dikkate alinir.

### Q-0019 — Rehber surumu degistiginde davranis
**Status:** ANSWERED  
**Evidence:** Q059-Q060  
**Resolution:** Yarim iste surum farklari gosterilir, kritik duzeltmede eski akis durur; tarihsel kayit sessizce yeniden yazilmaz.

### Q-0020 — Monetization baseline
**Status:** ANSWERED  
**Evidence:** Q065  
**Resolution:** Ileri kolayliklar premium olabilir; temel dogrulanmis rehber, kritik safety, bakım kaydi ve temel reminders ucretsiz beklenir.

### Q-0021 — Kullanici katkisi / moderation baseline
**Status:** ANSWERED  
**Evidence:** Q080-Q084  
**Resolution:** Community explicit opt-in, provenance/review statuslu ve resmi rehberden ayridir; tehlikeli icerik kaldirilip etkisi yonetilir.

### Q-0022 — Gecmis duzeltme ve dis islem kanit baseline
**Status:** ANSWERED  
**Evidence:** Q073-Q074  
**Resolution:** Edit trail korunur; farkli evidence seviyeleri ayni guven statusu gibi sunulmaz.

### Q-0023 — Sosyal/ticari ozelliklerin urun siniri
**Status:** ANSWERED  
**Evidence:** Q084-Q086, Q088  
**Resolution:** Community/resmi rehber ayrilir; servis/satin alma self-service core'un yerini almaz ve ticari etki teknik uygunlugu degistiremez.

### Q-0024 — Bakim istisnalari ve eksik kosul bilgisi
**Status:** ANSWERED  
**Evidence:** Q061, Q075-Q077  
**Resolution:** Dogrulanmamis modifiye-parca araligi uydurulmaz; verified istisna gerekcesiyle uygulanir; eksik kullanim kosulu gizlenmez.

### Q-0025 — Islem suresi ve maliyet tahmininin guven siniri
**Status:** ANSWERED  
**Evidence:** Q078-Q079  
**Resolution:** Sure aralik ve belirsizlikle, maliyet kalem/tarih/varsayim gorunurlugu ile sunulmalidir.

### Q-0028 — Kullanici verisi uzerinde kontrol
**Status:** ANSWERED  
**Evidence:** Q092-Q094  
**Resolution:** Kullanici kendi verisini gorur/duzeltir/ekler/siler/export eder; export premium degildir ve cross-account veri karismasi kabul edilmez.

### Q-0029 — Zayif/olmayan baglanti durumunda temel deneyim
**Status:** ANSWERED  
**Evidence:** Q090-Q091  
**Resolution:** Indirilmis rehber/gorsel/safety/progress/history offline erisilebilir; surum/guncellik gorunur ve roadside belirsizlik gizlenmez.

### Q-0030 — Readiness yanlis engelleme ve override siniri
**Status:** ANSWERED  
**Evidence:** Q096-Q098  
**Resolution:** False-positive durumunda eksik kosul ve gerekce gorunur olur, kullanici fotograf/olcum/alternatif kontrol gibi yeni kanitla re-validation yapabilir. Salt `yapabilirim` beyanı safety gate'i gecemez; varyant, kritik bilgi, ekipman, guvenli ortam ve zorunlu pre-check eksigi override edilemez.

### Q-0031 — Modifiye motosikletlerde kapsama beklentisi
**Status:** ANSWERED  
**Evidence:** Q102-Q104  
**Resolution:** Yaygin aftermarket degisikliklar uygunluk dogrulanirsa uyarlanmis rehbere dahil edilebilir. Nadir/custom durumda hangi kanitin eksik oldugu aciklanir; teaching-only guvenilir genel bilgi kalabilir, zarar verebilecek application adimlari dogrulanana kadar acilmaz.

### Q-0032 — Community moderation itiraz ve uyusmazliklari
**Status:** ANSWERED  
**Evidence:** Q105-Q108  
**Resolution:** Kaldirma gerekceli/saygili ve itiraz edilebilir olmali; correction/re-submit yolu bulunmali. Tekrarlanan yanlista pre-review, kasitli/surekli tehlikeli tekrarda contribution restriction olabilir. Faydalı ama dogrulanamamis deneyim `dogrulanmamis kisisel deneyim` olarak resmi rehberden ayri kalabilir.

### Q-0033 — Kanit duzeyi etiketlerinin temel semantigi
**Status:** ANSWERED  
**Evidence:** Q109-Q110  
**Resolution:** `Kullanici beyani` kullanicinin girdisidir; `belgeli` destekleyici kanit tasir; `incelenmis` kanitin kontrol edildigini; `dogrulanmis` ise kaynak + ilgili motosiklet/islem uygunlugu + inceleme tarihi/karar gorunurlugunu ifade etmelidir. Mutlak garanti degildir. Baglamsal taxonomy Q-0042'de aciktir.

### Q-0034 — Kritik bildirimlerde istisnai escalation
**Status:** ANSWERED  
**Evidence:** Q111-Q113  
**Resolution:** Kritik konu routine reminders arasinda kaybolmaz; app acilisinda safety ozeti ve gecikmenin sonucu gorunur. Birden cok kritik konu zarar/aciliyetle siralanir; uzun aradan donuste notification flood yerine kritik safety -> geciken bakım -> kayitlar sirali catch-up summary beklenir.

### Q-0037 — Paylasilan motosiklet / ortak calisma
**Status:** ANSWERED  
**Evidence:** Q118-Q119  
**Resolution:** Owner access izni verir; contributor kendi kimligiyle kayit ekler; attribution, zaman ve edit trail gorunur; izin geri alinabilir; baskasinin kaydi sessizce degistirilemez ve private notes izinsiz acilmaz.

### Q-0038 — Dil, olcu birimi ve erisilebilirlik beklentileri
**Status:** ANSWERED  
**Evidence:** Q124-Q125  
**Resolution:** Turkiye odakli acik Turkce, alisilmis olcu birimleri, deneyime gore terminoloji derinligi; buyuk yazi/dugme, yuksek kontrast, non-color-only warning, image description, caption, voice steps ve kolay dokunus beklentileri vardir. Global expansion karari degildir.

### Q-0039 — Motosiklet satma/devretme/arsivleme
**Status:** ANSWERED  
**Evidence:** Q120-Q121  
**Resolution:** Secili bakım history/kanit transfer edilebilir; personal note ve kimlik/konum iceren fotograflar default-private ve transfer preview'lu olmalidir. Archive aktif garajdan cikarir fakat history'yi korur ve reversible'dir; delete ile ayni degildir.

### Q-0040 — Offline stale/recall durumunda temel guvenli davranis
**Status:** ANSWERED  
**Evidence:** Q122  
**Resolution:** Kritik offline rehberde son dogrulama zamani gorunmeli; guncellik siniri asildiysa application adimlari baglanti kurulup re-check edilene kadar acilmayabilir. Sayisal freshness policy Q-0044'te aciktir.

### Q-0041 — Ilk kullanim / onboarding ve hesap beklentisi
**Status:** ANSWERED  
**Evidence:** Q123  
**Resolution:** Kullanici ilk acilista motosikletini secip rehber deneyimini hizla gormek ister; account creation, notification permission ve uzun profil ilk degerden once zorunlu olmamali, kayit/sync ihtiyacinda istenmelidir. Teknik auth modeli secilmemistir.

---

## Kullanim Kurali

Yeni bir belirsizlik ortaya ciktiginda ayni format kullanilir. Soru ancak kullanici cevabi veya yetkili karar sureciyle `ANSWERED` yapilir. Genis bir soru cevaplandiginda daha dar yeni sorular acilabilir; eski cevap sessizce silinmez.
