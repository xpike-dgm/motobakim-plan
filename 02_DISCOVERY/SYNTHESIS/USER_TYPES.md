# USER TYPES

Status: DRAFT

| ID | User Type | Goals | Needs | Restrictions | Evidence |
|---|---|---|---|---|---|
| UT-001 | Yeni / az deneyimli kendi-bakimini-yapan kullanici | Islemi neyi/neden yaptigini anlayarak guvenle tamamlamak; parca/adimlari dogru tanimak; zamanla bagimsizlasmak | Her hareket icin aciklama, gercek/isaretli gorsel, basari kontrolu, acilabilir ileri ayrinti, hazirlik ve recovery destegi | Safety/kritik dogrulama atlanamaz; rehber eslesmesi veya gerekli readiness belirsizse kritik uygulama adimi acilmaz | Q006-Q007, Q014-Q021, Q025-Q027, Q050-Q052, Q089 |
| UT-002 | Deneyimli kendi-bakimini-yapan kullanici | Dogru teknik bilgiye ve islem kontrolune hizla ulasmak; gereksiz anlatimla yavaslamamak; islemi kendisi tamamlamak | Kisa checklist, teknik ayrintiya hizli erisim, kaynak/provenance, kritik olcum ve kontroller | Hizlandirilmis deneyim safety veya kritik dogrulamayi kaldiramaz; yalniz `deneyimliyim` beyanı belirli is icin readiness kaniti degildir | Q007, Q010-Q011, Q014, Q021, Q051-Q052 |

## Cross-cutting user states / contexts

Bunlar ayri persona olarak CONFIRMED degildir; ayni kullanicinin farkli yolculuk anlari olabilir:

- **Known-task state — CONFIRMED (Q006):** Yapmak istedigi islemi bilir ama parca adi, hazirlik veya sira konusunda yardim ister.
- **Symptom-first state — CONFIRMED (Q006, Q012, Q022):** Yalniz belirtiyi bilir ve kanit-temelli teshis yoluyla uygun isleme ulasmak ister.
- **Interrupted-work state — CONFIRMED (Q028, Q059):** Islem yarida kalmistir; baglam ve rehber surumu korunarak guvenli devam beklenir.
- **Mismatch/modification state — CONFIRMED (Q026, Q038-Q039, Q066-Q067):** Rehber, gercek motosiklet veya modifiye durumla eslesmez; observable evidence de yetersizse kritik ilerleme durur.
- **Recovery state — CONFIRMED (Q025-Q027):** Kullanici takilir, hata yapar veya beklenmeyen durum olusur; guvenli geri donus/yardim yoluna ihtiyac duyar.
- **Task-specific readiness state — CONFIRMED (Q050-Q052):** Ayni kullanici bir is icin hazir, baska is icin hazir olmayabilir.
- **Multi-motorcycle owner state — CONFIRMED (Q062):** Birden fazla motosikletin gecmis/rehber/hatirlatma baglami ayri tutulur.
- **Roadside / constrained-context state — CONFIRMED (Q090-Q091):** Garaj disinda hizli tarama, oncelikli safety kontrolu, kisa gorsel anlatim ve offline sureklilik degeri artar.
- **Community contributor state — CONFIRMED AS POSSIBLE PRODUCT BEHAVIOR (Q080-Q084):** Kullanici kisisel icerigi ozel tutabilir veya bilincli secimle community katkisi yapabilir; katkisi resmi rehberle ayni statude degildir.
- **Data-owner state — CONFIRMED (Q092-Q094):** Kullanici kendi motosiklet/gecmis/not/fotograf verisini goruntuleme, duzeltme, silme ve disa aktarma kontrolu bekler.

## Current user motivation evidence

**CONFIRMED FOR CURRENT USER — Q089:**
1. Islemi kendi tamamlamak
2. Ogrenip bagimsizlasmak
3. Masrafi azaltmak
4. Zaman kazanmak
5. Surecten keyif almak

Bu siralama tum hedef kullanicilara genellenemez.

## Current segmentation interpretation

**INFERRED, NOT FINAL:** Deneyim seviyesi tek global `acemi/deneyimli` etiketinden ibaret olmayabilir. Readiness islem bazli degisebilir. Ayrica normal garaj, yol-kenari/offline ve community katkisi gibi kullanim baglamlari ayni kisinin urunden beklentisini degistirebilir.

## Open segmentation questions

- Farkli hedef kullanicilarda motivasyon sirasi nasil degisir?
- Profesyonel/servis kullanicisi, baska birinin motosikletinde calisan kisi veya yalniz kayit tutan owner hedef kullanici midir?
- Ayni motosikleti birden fazla kisi birlikte yonetmek ister mi?
- Readiness yanlis engelleme durumunda kullanici itiraz/override ister mi; hangi safety kapilari override edilemez?
