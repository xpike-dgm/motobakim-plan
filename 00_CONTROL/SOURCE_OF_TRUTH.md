# SOURCE OF TRUTH

Bu dosya, proje hafizasinda hangi bilginin hangi otorite seviyesinde kabul edilecegini tanimlar.

## Authority Order

Bir bilgi birbiriyle celisirse su oncelik sirasi kullanilir:

1. Kullanicinin en yeni ve acik talimati
2. `LOCKED` durumundaki karar kayitlari
3. `APPROVED` source-of-truth dokumanlari
4. `CURRENT_STATE.md`
5. Diger repository dokumanlari
6. Gecmis sohbetler
7. AI'nin kendi hatirladigi veya cikarsadigi bilgiler

## Memory Rule

ChatGPT kendi dahili hafizasini kalici proje gercegi olarak kabul etmez. Yeni sohbetlerde proje durumu repository uzerinden yeniden kurulur.

## Canonical Memory Files

- `00_CONTROL/AI_START_HERE.md` — yeni oturum protokolu
- `00_CONTROL/CURRENT_STATE.md` — en guncel proje durumu
- `00_CONTROL/DECISION_LOG.md` — kalici kararlar
- `00_CONTROL/OPEN_QUESTIONS.md` — cozulmemis belirsizlikler ve celiskiler
- `00_CONTROL/CHANGELOG.md` — hafiza ve karar degisikliklerinin kronolojik izi
- `00_CONTROL/HANDOFF.md` — yeni sohbet/AI icin kisa devir ozeti

## Mutation Rule

Yeni bilgi geldiginde sadece ilgili source-of-truth dosyasi guncellenir. Ayni gercegin farkli dosyalarda bagimsiz ve celisebilecek kopyalari olusturulmaz.

## Refresh Rule

Her anlamli kilometre tasinda `CURRENT_STATE.md`, `DECISION_LOG.md`, `OPEN_QUESTIONS.md`, `CHANGELOG.md` ve gerekiyorsa `HANDOFF.md` kontrol edilip guncellenir.

## No Silent Rewrite

Daha once kabul edilmis bir bilgi degisiyorsa eski kayit iz birakmadan silinmez. Karar gecmisi korunur ve yeni karar tarafindan gecersiz kilindigi belirtilir.