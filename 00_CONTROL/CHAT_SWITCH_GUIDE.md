# Sohbet Değişimi Kılavuzu (sahip için)

Yeni bir sohbete geçtiğinde bilmen gereken tek şey aşağıdaki promptu kopyalamaktır.
Köşeli parantez YOK, doldurulacak alan YOK. AI durumu kendisi bulur.

## Evrensel devam promptu (her zaman bunu yapıştır)

---

Kavriva projesine devam ediyoruz. Önce durumu kendin bul, bana sorarak değil:

1. İki depoda (`motobakim-plan`, `kavriva-app`) `main` dalının son 3 commit'ini, açık dalları ve açık PR'ları listele.
2. Yarım kalan görev/dal/PR varsa: hangisi, nerede kalmış, diske bakarak söyle (tahmin etme).
3. Hiçbir şey yoksa: "başlayan iş yok" de ve baştan-başlatma düzenine geç (önce `00_CONTROL/AI_START_HERE.md` + `07_AI_ARCHITECTURE/TASK_EXECUTION_PROTOCOL.md` oku, CI yeşilini doğrula, ilk 3 görevi öner, onayımı bekle).

Kurallar her zaman geçerli: `main`'e doğrudan push yasak (PR + yeşil CI), T3 ikinci-göz, kanıtsız "bitti" yok.
Durum raporunu ver, devam etmeden önce onayımı bekle.

---

## Evrensel inceleme promptu (bunu da aynen yapıştır, boşluk yok)

---

Kavriva'da bağımsız incelemecisin. Kod yazma, dosyaya dokunma — yalnız oku ve hüküm ver.

1. App deposunda (`kavriva-app`) son birleşmiş PR'ı bul (`gh pr list`), hangi göreve ait olduğunu ve
   birleştirme commit'ini diske bakarak tespit et (tahmin etme).
2. O görevin satırını plan deposu `06_DELIVERY_PLANNING/TASK_INDEX.md` dosyasından oku; PR'daki
   değişikliğin kabul kriterini gerçekten karşılayıp karşılamadığına bak.
3. `vault/EVIDENCE/` altındaki ilgili kanıt kaydını bul; kanıtın yeterli olup olmadığını değerlendir.
   T3 sınıfı işse (para/yayın/kimlik etkisi) ikinci-göz şartını ayrıca kontrol et.

Sonunda tek hüküm ver: ONAYLANDI veya REDDEDİLDİ (gerekçesiyle). Reddedersen eksikleri maddeler
halinde yaz. Hükmü vermeden önce başka iş yapma.

---

## Neden bu yeterli

AI `git log`, `git branch`, `gh pr list` ile gerçek durumu okur. Senin görev/dal adı bilmene
gerek yoktur. Rapor geldikten sonra "devam et" demen yeterlidir.
