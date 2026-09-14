# USER TYPES

Status: DRAFT

| ID | User Type | Goals | Needs | Restrictions | Evidence |
|---|---|---|---|---|---|
| UT-001 | Yeni / az deneyimli kendi-bakimini-yapan kullanici | Islemi neyi/neden yaptigini anlayarak guvenle tamamlamak; parca/adimlari dogru tanimak; zamanla bagimsizlasmak | Her hareket icin aciklama, gercek/isaretli gorsel, basari kontrolu, acilabilir ileri ayrinti, hazirlik, recovery ve gerekirse sesli/kolay etkileşim destegi | Safety/kritik dogrulama atlanamaz; rehber eslesmesi veya readiness belirsizse kritik application acilmaz | Q006-Q007, Q014-Q021, Q025-Q027, Q050-Q052, Q089, Q096-Q101, Q125 |
| UT-002 | Deneyimli kendi-bakimini-yapan kullanici | Dogru teknik bilgiye ve islem kontrolune hizla ulasmak; gereksiz anlatimla yavaslamamak; islemi kendisi tamamlamak | Kisa checklist, teknik ayrintiya hizli erisim, kaynak/provenance, kritik olcum ve kontroller | Hizlandirilmis deneyim safety veya kritik dogrulamayi kaldiramaz; yalniz `deneyimliyim` beyanı belirli is icin readiness kaniti degildir | Q007, Q010-Q011, Q014, Q021, Q051-Q052, Q096-Q098 |
| UT-003 | Kayit / takip odakli motosiklet sahibi | Kendi tamirini yapmasa da bakım gecmisini, belgeleri, fotograflari, yaklaşan islemleri ve reminders'i duzenli tutmak | Zengin history, next-maintenance tracking, belge/fotograf saklama, reminders, motosikletler arasi ayrim ve isterse sonradan guided repair'e gecis | Uygulamali rehberi kullanmak zorunda degildir; history/provenance guveni korunmalidir | Q117 |
| UT-004 | Paylasilan motosiklet katilimcisi / hobby helper | Aile/arkadas/baska owner motosikletinde izinli sekilde islem veya kayit katkisi yapmak | Owner-granted access, actor attribution, edit trail, private-note isolation, revocable access | Baskasinin kaydini sessizce degistiremez; personal content izinsiz acilmaz | Q116, Q118-Q119 |

## Core-priority note

**CONFIRMED — Q116:** MotoBakim'in ana odağı bireysel surucunun kendi motosikletindeki islemi ogrenip yapmasidir. UT-003 ve UT-004 anlamli supported user types/context'lerdir; core priority'de UT-001/UT-002 ile otomatik esitlenmezler.

Profesyonel usta/servisin dogrudan target user olup olmadigi henuz belirlenmemistir.

## Cross-cutting user states / contexts

Bunlar ayri persona olmak zorunda degildir; ayni kullanicinin farkli yolculuk anlari olabilir:

- **Known-task state — CONFIRMED (Q006):** Yapmak istedigi islemi bilir ama parca adi, hazirlik veya sira konusunda yardim ister.
- **Symptom-first state — CONFIRMED (Q006, Q012, Q022):** Yalniz belirtiyi bilir ve kanit-temelli teshis yoluyla uygun isleme ulasmak ister.
- **Interrupted-work state — CONFIRMED (Q028, Q059):** Islem yarida kalmistir; baglam ve rehber surumu korunarak guvenli devam beklenir.
- **Mismatch/modification state — CONFIRMED (Q026, Q038-Q039, Q066-Q067, Q102-Q104):** Rehber, gercek motosiklet veya modifiye durumla eslesmez; application uygunluk yeniden kurulana kadar durabilir, teaching-only bilgi kalabilir.
- **Recovery state — CONFIRMED (Q025-Q027):** Kullanici takilir, hata yapar veya beklenmeyen durum olusur; guvenli geri donus/yardim yoluna ihtiyac duyar.
- **Task-specific readiness state — CONFIRMED (Q050-Q052):** Ayni kullanici bir is icin hazir, baska is icin hazir olmayabilir.
- **Readiness challenged / re-validation state — CONFIRMED (Q096-Q098):** Kullanici blokajı yanlis bulabilir; serbest override yerine yeni kanitla re-validation bekler.
- **Professional-escalation state — CONFIRMED (Q100-Q101):** Belirli islemde kosullar karsilanmadigi icin profesyonel yardim dusunulebilir; kullanici yine teaching, diagnosis capture, preparation ve result-check degeri almaya devam eder.
- **Multi-motorcycle owner state — CONFIRMED (Q062, Q116):** Birden fazla motosikletin gecmis/rehber/reminder baglami ayri tutulur.
- **Roadside / constrained-context state — CONFIRMED (Q090-Q091):** Garaj disinda hizli tarama, oncelikli safety kontrolu, kisa gorsel anlatim ve offline sureklilik degeri artar.
- **Community contributor state — CONFIRMED AS POSSIBLE PRODUCT BEHAVIOR (Q080-Q084, Q105-Q108):** Kullanici kisisel icerigi ozel tutabilir veya bilincli secimle community katkisi yapabilir; moderation/appeal/review statuleri olabilir.
- **Data-owner state — CONFIRMED (Q092-Q094):** Kullanici kendi motosiklet/gecmis/not/fotograf verisini goruntuleme, duzeltme, silme ve export kontrolu bekler.
- **Ownership-transfer state — CONFIRMED (Q120):** Kullanici motosiklet satis/devrinde secili vehicle history'yi aktarirken personal content'i ayirmak ister.
- **Archived-motorcycle state — CONFIRMED (Q121):** Motosiklet aktif garajdan cikmistir fakat history korunur ve yeniden aktive edilebilir.

## Current user motivation evidence

**CONFIRMED FOR CURRENT USER — Q089:**
1. Islemi kendi tamamlamak
2. Ogrenip bagimsizlasmak
3. Masrafi azaltmak
4. Zaman kazanmak
5. Surecten keyif almak

Bu siralama tum hedef kullanicilara genellenemez.

## Current segmentation interpretation

**INFERRED, NOT FINAL:** Deneyim seviyesi tek global `acemi/deneyimli` etiketinden ibaret olmayabilir. Readiness islem bazli degisebilir. Normal garaj, roadside/offline, record-only, collaboration, community contribution ve ownership lifecycle gibi baglamlar ayni kisinin urunden beklentisini degistirebilir.

## Open segmentation questions

- Core self-service owner, record-only owner, shared-family/hobby helper ve multi-bike owner motivasyon/first-use farklari nasil olmalidir?
- Profesyonel usta/servis dogrudan target user mi yoksa collaboration participant mi?
- Adjacent user types core owner deneyimini hangi noktada degistirmemelidir?
