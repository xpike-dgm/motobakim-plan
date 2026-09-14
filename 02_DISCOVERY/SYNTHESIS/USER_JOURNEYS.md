# USER JOURNEYS

Status: DRAFT

Kullanicilarin teknik implementasyon detayindan bagimsiz uc uca urun yolculuklari.

## J-001 — Known task -> prepare -> execute -> verify -> record
**Evidence:** Q006, Q013-Q021, Q029-Q030, Q050-Q053
1. Kullanici yapmak istedigi islemi bilir.
2. Motosiklet/rehber eslesmesi ve readiness dogrulanir.
3. Amac, uygunluk, risk, sure/maliyet, arac/parca/ekipman ve kullanilabilirlik gorulur.
4. Zorunlu eksik/kritik beceri eksigi varsa uygulama adimi acilmaz.
5. Rehber ihtiyac duyulan ayrinti/hizi sunar; safety/kritik dogrulama degismez.
6. Kritik adimlarda gorsel/olcum/basari kontrolu bulunur.
7. Stop kosulu olusursa ilerleme kesilir.
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
**Evidence:** Q019, Q025-Q026, Q036-Q039, Q066-Q067
1. Rehber-gercek motosiklet uyusmazligi veya modifikasyon ihtimali ortaya cikar.
2. Normal ilerleme durur.
3. Kullanici-dostu ozellikler, gorunur donanim ve farkli acilardan fotograflarla ayrim denenir.
4. Kullanici belge/etiket/parca kodu aramak zorunda birakilmaz.
5. Versiyon/modifikasyon yeterince belirlenirse uygun rehber eslesmesi kurulur.
6. Belirsizlik surerse hangi ayrimin eksik oldugu gosterilir; versiyona bagli uygulamali adim acilmaz.

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
**Evidence:** Q031-Q033, Q061, Q064, Q070-Q072, Q075-Q077
1. Dogrulanmis uretici kilometre/sure plani ve tamamlanma kaydi kullanilir.
2. Dogrulanmis istisna/kullanim kosulu varsa gerekcesiyle plan degisir.
3. Veri eksikse belirsizlik gizlenmez; uygun standart plan varsa conditional gosterilir.
4. Birden fazla gecikmis is safety/kullanim etkisi ve gerekceyle onceliklenir.
5. Rutin reminders gruplanabilir/ertelenebilir; kritik safety ayri gorunur.
6. Erteleme completion sayilmaz.
7. Dogrulanmis completion sonraki bakim hesabini ilerletir.

## J-008 — Review/correct historical work
**Evidence:** Q029-Q030, Q043, Q060, Q073-Q074
1. Kullanici gecmis islemi acar.
2. Islem nedeni, tarih/km, parca/malzeme, olcum/son kontrol, fotograf/not, isi yapan ve rehber surumu gorulur.
3. Hata varsa kayit duzeltilir fakat eski/yeni deger, degisiklik zamani ve nedeni korunur.
4. Duzeltmenin bakım planina etkisi gosterilir.
5. Kullanici beyanı, belgeli ve incelenmis kayit ayni evidence level olarak sunulmaz.
6. Rehber geri cekildiyse tarihsel kayit sessizce yeniden yazilmaz; gerekirse yeniden kontrol uyarisi eklenir.

## J-009 — Content critical error / unresolved source conflict
**Evidence:** Q041-Q044, Q081-Q083
1. Kaynak guncellenir, kritik hata/uyusmazlik bulunur veya community duzeltmesi gelir.
2. Etkilenen uygulamali adim yeniden inceleme bitene kadar askiya alinir/durdurulur.
3. Celismeyen hazirlik/safety bilgisi gosterilebilir.
4. Kaynak/uygunsuzluk aciklanir.
5. Etkilenen kullanicilar gerekli kontrol ve yardim yoluyla uyarilir.
6. Kabul edilen degisiklik gerekcesiyle yeni surum yayimlanir; tarihsel surum korunur.

## J-010 — Task-specific readiness -> learn or stop
**Evidence:** Q050-Q053
1. Kullanici ileri islem acmak ister.
2. Benzer is gecmisi, arac/olcum bilgisi, kayitlar ve on kosul anlayisi degerlendirilir.
3. Guvenle ogrenilebilen eksik beceri hazirlik/ogrenme yoluna gider.
4. Kritik ekipman eksikse islem ertelenir.
5. Ciddi sonuc/uzman dogrulamasi gereken adim acilmaz.

## J-011 — Multi-motorcycle context switching
**Evidence:** Q062
1. Her motosikletin bilgisi/gecmisi/rehberi/hatirlatmasi ayri kalir.
2. Kullanici motorlar arasinda kolay gecer.
3. Aktif motosiklet her zaman anlasilir olur.
4. Kayitlar birbirine karismaz.

## J-012 — Add external/service work to history
**Evidence:** Q063, Q074
1. Kullanici serviste/baska biri tarafindan yapilan isi ekler.
2. Provenance belirtilir.
3. Tarih/km/islem/fatura/fotograf/not gibi destekler eklenebilir.
4. Evidence level gorunur olur; kanit yoksa verified completion gibi sunulmaz.
5. Nihai `verified/reviewed` etiket siniri discovery'de aciktir.

## J-013 — High-consequence learning -> conditional application
**Evidence:** Q068-Q069
1. Kullanici yuksek gerilim/basincli/yuksek sicaklik vb. islemi ogrenmek ister.
2. Riskler, gerekli bilgi, ekipman, hazirlik ve kritik kontroller ogretilir.
3. Motosiklete ozel surec ve safety kosullari dogrulanir.
4. Kosul dogrulanamiyorsa uygulamali adim acilmaz; ogrenme/hazirlik bilgisi kalabilir.
5. Profesyonel escalation siniri hala discovery konusudur.

## J-014 — Community contribution -> review -> publish/hold
**Evidence:** Q080-Q084
1. Kisisel not/fotograf default-private kalir.
2. Kullanici ayri explicit secimle community katkisi yapar; kisisel bilgi ayiklanir.
3. Katki resmi rehberden ayri provenance/review status ile tutulur.
4. Duzeltme onerisi resmi rehbere girmeden kaynak/uygunluk/safety acisindan incelenir.
5. Kabul edilirse degisen adim/gerekce yeni surumde gorunur.
6. Tehlikeli icerik gorunumden kaldirilir ve etkisi resmi rehbere uzaniyorsa ilgili adim/etkilenen kullanicilar icin safety response uygulanir.

## J-015 — Commercial support without technical influence
**Evidence:** Q085-Q088
1. Kullanici teknik uygunluk kriterini gorur.
2. Servis/usta veya satin alma secenekleri core rehberin ardindan destek yuzeyi olarak gorulebilir.
3. Sponsorlu teklif acikca isaretlenir.
4. Odeme/sponsorluk teknik uygunluk kararini, alternatiflerin gorunurlugunu veya rehber adimlarini degistiremez.

## J-016 — Roadside / offline continuity
**Evidence:** Q090-Q091
1. Kullanici garaj disinda sorun yasar.
2. Hizli belirti taramasi ve oncelikli safety kontrolleriyle baslar.
3. Indirilmis motosiklete ozel rehber/gorsel/safety uyarisi offline acilir.
4. Kaldigi adim ve kisisel gecmisi erisilebilir kalir.
5. Icerik surumu/guncellik durumu gorulur.
6. Suruse devam karari belirsizse bu saklanmaz.
7. Offline iken rehberin sonradan recall edilmis olmasi edge case'i aciktir.

## J-017 — User data view/edit/export/delete
**Evidence:** Q092-Q094
1. Kullanici motosiklet/kayit/not/fotograf verisini gorur ve duzeltebilir.
2. Not/fotograf ekleyebilir veya silebilir.
3. Kendi motosiklet/tarihli islem/not/fotograf verisini anlasilir, yeniden kullanilabilir bicimde export edebilir; export premium olmaz.
4. Silme oncesi kapsam ve geri alinmazlik aciklanir.
5. Sonrasinda silinen/bekleyen durum anlasilir olur.
6. Baska hesap verileri etkilenemez.

## Open journey gaps

- Readiness degerlendirmesine itiraz/override ve profesyonel escalation
- Modifiye motosiklette dogrulanmis rehber yoksa uzun vadeli user path
- Community moderation itirazi / faydali ama dogrulanamamis contribution
- Kritik bildirim uzun sure gormezden gelindiginde escalation
- Paylasilan motosiklet / birden fazla kisinin ayni kayda katkisi
- Motosiklet satma/devretme/arsivleme
- Ilk kullanim/onboarding ve hesap zorunlulugu
- Offline stale/recall icerik davranisi
- Premium paket secimi (model henuz belirlenmedi)
