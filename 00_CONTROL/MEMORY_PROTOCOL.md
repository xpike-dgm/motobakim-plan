# MEMORY PROTOCOL

Bu protokol ChatGPT'nin Motobakim projesinde oturumlar arasi hafizasini nasil yeniden kuracagini ve nasil guncel tutacagini tanimlar.

## A. Session Bootstrap

Her yeni sohbet veya baglam kaybi sonrasi:

1. `AI_START_HERE.md` oku.
2. `CURRENT_STATE.md` ile nerede kalindigini belirle.
3. `SOURCE_OF_TRUTH.md` ile bilgi otoritesini kontrol et.
4. `DECISION_LOG.md` icindeki aktif `APPROVED` ve `LOCKED` kararlarini yukle.
5. `OPEN_QUESTIONS.md` icindeki aktif belirsizlikleri yukle.
6. `HANDOFF.md` ile son oturumun devir ozetini kontrol et.
7. Yalnizca yapilacak ise gerekli ek belgeleri oku.

Bu adimlardan sonra AI, onceki sohbeti hatirlamasa bile calismaya devam edebilmelidir.

## B. Memory Write Triggers

Asagidaki olaylardan herhangi biri gerceklestiginde hafiza yazma/tazeleme yapilir:

- Kullanici kalici bir karar verir.
- Kullanici onceki bir karari degistirir.
- Yeni bir kapsam siniri belirlenir.
- Bir asama baslar veya tamamlanir.
- Yeni bir belirsizlik ortaya cikar veya kapanir.
- Bir AI tartismasindan resmi sonuc kabul edilir.
- Bir referans/tasarim/teknik karar ileride source-of-truth haline gelir.
- Sonraki oturumun bilmesi gereken anlamli bir durum degisikligi olur.

Kucuk sohbet, fikir egzersizi veya onaylanmamis oneriler kalici hafizaya otomatik olarak karar diye yazilmaz.

## C. Memory Refresh Transaction

Her anlamli guncellemede su sira izlenir:

1. Gelen yeni bilgiyi siniflandir: karar, durum, acik soru veya gecici not.
2. Mevcut kayitlarla celiski kontrolu yap.
3. Gerekliyse `DECISION_LOG.md` guncelle.
4. Gerekliyse `OPEN_QUESTIONS.md` guncelle.
5. `CURRENT_STATE.md` guncelle.
6. `HANDOFF.md` ozetini yenile.
7. `CHANGELOG.md` icine degisiklik izi ekle.
8. Son kez dosyalar arasi tutarlilik kontrolu yap.

Bu adimlar tek bir mantiksal hafiza islemi olarak ele alinir.

## D. Compression Rule

Repository buyudukce `CURRENT_STATE.md` ve `HANDOFF.md` kisa tutulur. Tarihsel ayrintilar karar ve changelog dosyalarinda kalir.

Amaç: Yeni bir AI once 5-10 dakikalik dev bir dokuman okumak zorunda kalmadan mevcut durumu anlayabilsin.

## E. No Hallucinated Memory

AI herhangi bir ayrintiyi hatirladigini dusunse bile repo tarafindan desteklenmiyorsa onu kesin proje bilgisi saymaz. Gerekirse `OPEN_QUESTIONS.md` icine belirsizlik olarak kaydeder.

## F. User Supremacy

Kullanicinin yeni ve acik talimati mevcut kaydi degistirebilir. Degisiklik yapildiginda tarihsel iz korunur; eski karar sessizce yok edilmez.

## G. Session Close Checklist

Anlamli bir calisma bittiginde AI kendine su kontrol listesini uygular:

- Nerede kaldigimiz `CURRENT_STATE.md` icinde acik mi?
- Verilen kalici kararlar `DECISION_LOG.md` icinde mi?
- Cozulmemis konular `OPEN_QUESTIONS.md` icinde mi?
- Sonraki AI sadece `HANDOFF.md` ve temel kontrol dosyalarini okuyarak devam edebilir mi?
- `CHANGELOG.md` bu oturumdaki anlamli degisikligi kaydediyor mu?

Cevaplardan biri hayirsa oturum hafiza bakim islemi tamamlanmis sayilmaz.