# AI START HERE

Bu dosya Motobakim projesine ilk kez giren veya yeni bir sohbet/agent oturumunda calisan her AI icin zorunlu baslangic protokoludur.

## 1. Temel kural

Sohbet gecmisi, model hafizasi veya varsayimlar **source of truth degildir**. Proje gercegi bu repodaki kontrollu dokumanlardan okunur.

Bir bilgi sohbet ile repo arasinda celisiyorsa, kullanicidan gelen en yeni acik talep disinda repo kaydi esas alinir ve celiski `00_CONTROL/OPEN_QUESTIONS.md` veya `00_CONTROL/DECISION_LOG.md` icinde gorunur hale getirilir.

## 2. Her yeni oturumda zorunlu okuma sirasi

1. `00_CONTROL/CURRENT_STATE.md`
2. `00_CONTROL/SOURCE_OF_TRUTH.md`
3. `00_CONTROL/DECISION_LOG.md`
4. `00_CONTROL/OPEN_QUESTIONS.md`
5. Yurutulecek isin ilgili klasor README/protokol dosyalari
6. Yalnizca gerekliyse ilgili urun, tasarim, teknoloji, mimari veya task belgeleri

Tum repository'yi refleks olarak okumak yerine **minimum yeterli baglam** ilkesi uygulanir.

## 3. Calismaya baslamadan once

AI su sorularin cevabini repo icinden belirlemelidir:

- Su an hangi fazdayiz?
- Bu oturumun amaci nedir?
- Hangi kararlar `LOCKED`, hangileri `APPROVED`, `PROPOSED`, `SUPERSEDED` veya `DEPRECATED`?
- Bu is hangi dosyalari degistirebilir?
- Hangi bilgiler henuz bilinmiyor?
- Mevcut bir karari sessizce gecersiz kilacak miyim?

Bu sorulardan biri cevapsizsa AI tahminde bulunup bunu gercek gibi yazmamalidir.

## 4. Karar durumlari

Projede kararlar su durumlarla izlenir:

- `PROPOSED` — onerilmis, henuz kabul edilmemis
- `APPROVED` — kullanilmasi onaylanmis, fakat ileride kontrollu degisebilir
- `LOCKED` — acik karar olmadan degistirilemez
- `SUPERSEDED` — daha yeni bir karar tarafindan gecersiz kilinmis
- `DEPRECATED` — artik kullanilmamali, tarihsel kayit olarak tutulur

AI, `LOCKED` bir karari kullanicinin acik onayi olmadan degistiremez.

## 5. Celiski protokolu

Yeni bilgi mevcut bilgiyle celisirse:

1. Eski bilgiyi sessizce silme.
2. Celiskinin kaynagini tespit et.
3. Gerekirse `OPEN_QUESTIONS.md` icine kaydet.
4. Kullanici net karar verdiginde `DECISION_LOG.md` guncelle.
5. Etkilenen source-of-truth dosyalarini guncelle.
6. Eski karari `SUPERSEDED` olarak isaretle.
7. `CHANGELOG.md` kaydi ekle.

## 6. Her anlamli calisma sonunda zorunlu hafiza tazeleme

Bir faz, discovery batch'i, tasarim onayi, teknik karar, planlama karari veya mimari degisiklik tamamlandiginda AI en az su kontrolleri yapmalidir:

- `CURRENT_STATE.md` guncel mi?
- Yeni karar `DECISION_LOG.md` icinde mi?
- Yeni belirsizlik `OPEN_QUESTIONS.md` icinde mi?
- Kalici urun bilgisi ilgili source-of-truth dosyasina islendi mi?
- `CHANGELOG.md` guncellendi mi?
- Sonraki AI'nin bilmesi gereken baglam acik mi?

## 7. Yasak davranislar

- Onaylanmamis teknik tercihi kesin karar gibi yazmak
- Ayni bilginin birden fazla dosyada farkli versiyonlarini yasatmak
- Kullanici cevabini yorumlayarak kapsam genisletmek ve bunu onayli karar gibi kaydetmek
- Eski kararlari iz birakmadan silmek
- 300+ discovery cevabini her task icin ham baglam olarak kullanmak
- Bir tasarim referansini onay almadan `LOCKED` yapmak
- Uygulama kodu yazmaya, teknoloji secimleri kesinlesmeden baslamak

## 8. Proje yonetim modeli

ChatGPT bu surecte proje mimari muhendisi ve yoneticisi rolunu yurutecek; diger AI'lar uzman, tartisma katilimcisi, reviewer veya implementer olarak kullanilabilecek. Nihai proje gercegi sohbetlerde degil bu repository'de tutulacaktir.