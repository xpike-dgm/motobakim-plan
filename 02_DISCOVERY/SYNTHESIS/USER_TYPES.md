# USER TYPES

Status: DRAFT

| ID | User Type | Goals | Needs | Restrictions | Evidence |
|---|---|---|---|---|---|
| UT-001 | Yeni / az deneyimli kendi-bakimini-yapan kullanici | Islemi neyi/neden yaptigini anlayarak guvenle tamamlamak; parca ve adimlari dogru tanimak | Her hareket icin aciklama, gercek/isaretli gorsel, basari kontrolu, acilabilir ileri ayrinti, hazirlik ve recovery destegi | Guvenlik ve kritik dogrulama adimlari atlanamaz; rehber eslesmesi veya gerekli readiness belirsizse kritik uygulama adimi acilmamali | Q006-Q007, Q014-Q021, Q025-Q027, Q050-Q052 |
| UT-002 | Deneyimli kendi-bakimini-yapan kullanici | Dogru teknik bilgiye ve islem kontrolune hizla ulasmak; gereksiz anlatimla yavaslamamak | Kisa kontrol listesi, teknik ayrintiya hizli erisim, kaynak/provenance, kritik olcum ve kontroller | Hizlandirilmis deneyim guvenlik uyarilarini veya kritik dogrulamayi kaldirmamali; yalniz `deneyimliyim` oz-beyani belirli bir is icin readiness kaniti sayilmamali | Q007, Q010-Q011, Q014, Q021, Q051-Q052 |

## Cross-cutting user states

Bunlar ayri persona olarak CONFIRMED degildir; ayni kullanicinin farkli yolculuk anlaridir:

- **Known-task state — CONFIRMED (Q006):** Kullanici yapmak istedigi islemi bilir ama parca adi, hazirlik veya sira konusunda yardim ister.
- **Symptom-first state — CONFIRMED (Q006, Q012, Q022):** Kullanici yalniz belirtiyi bilir ve teshis yoluyla uygun isleme ulasmak ister.
- **Interrupted-work state — CONFIRMED (Q028, Q059):** Islem yarida kalmistir ve kullanici guvenli sekilde devam etmek ister; rehber surumu degismisse farklar gorulmelidir.
- **Mismatch/modification state — CONFIRMED (Q026, Q038-Q039):** Rehber, gercek motosiklet veya modifiye durumla eslesmez; kritik ilerleme uygunluk yeniden kurulana kadar durur.
- **Recovery state — CONFIRMED (Q025-Q027):** Kullanici takilir, hata yapar veya beklenmeyen durum olusur ve guvenli geri donus/yardim yoluna ihtiyac duyar.
- **Task-specific readiness state — CONFIRMED (Q050-Q052):** Ayni kullanici belirli bir is icin hazir, baska bir is icin hazir olmayabilir; benzer is gecmisi, arac/olcum bilgisi ve on kosul anlayisi gorev bazli degerlendirilir.
- **Multi-motorcycle owner state — CONFIRMED (Q062):** Ayni kullanici birden fazla motosikleti yonetebilir; aktif motosiklet ve ona ait gecmis/rehber/hatirlatma baglami karismamalidir.

## Current segmentation interpretation

**INFERRED, NOT FINAL:** Deneyim seviyesi tek bir global `acemi/deneyimli` etiketten ibaret olmayabilir. Batch 02 kaniti readiness'in islem bazli olmasini guclendiriyor. Bu, yeni bir persona karari degil; ileride urun modelinde kullanici yeterliliginin nasil temsil edilecegine dair discovery bulgusudur.

## Open segmentation questions

- Farkli motivasyonlara sahip kullanicilar (maliyet dusurme, ogrenme, uzak lokasyonda kendi isini gorme, hobi vb.) farkli urun beklentileri tasiyor mu?
- Profesyonel/servis kullanicilari, ekip halinde calisanlar veya yalniz motosiklet sahibi ama islemi kendi yapmayan kisiler hedef kullanici midir?
- Readiness sinyalleri kullaniciyi gereksiz yere engellemeden nasil kullanilmasi beklenir; kullanici itiraz/override ister mi?
