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

## Neden bu yeterli

AI `git log`, `git branch`, `gh pr list` ile gerçek durumu okur. Senin görev/dal adı bilmene
gerek yoktur. Rapor geldikten sonra "devam et" demen yeterlidir.
