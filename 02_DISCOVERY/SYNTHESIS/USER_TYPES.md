# USER TYPES

Status: DRAFT

| ID | User Type | Goals | Needs | Restrictions | Evidence |
|---|---|---|---|---|---|
| UT-001 | Yeni / az deneyimli kendi-bakimini-yapan kullanici | Islemi neyi/neden yaptigini anlayarak guvenle tamamlamak; parca ve adimlari dogru tanimak | Her hareket icin aciklama, gercek/isaretli gorsel, basari kontrolu, acilabilir ileri ayrinti, hazirlik ve recovery destegi | Guvenlik ve kritik dogrulama adimlari atlanamaz; rehber eslesmesi belirsizse ilerlememeli | Q006-Q007, Q014-Q021, Q025-Q027 |
| UT-002 | Deneyimli kendi-bakimini-yapan kullanici | Dogru teknik bilgiye ve islem kontrolune hizla ulasmak; gereksiz anlatimla yavaslamamak | Kisa kontrol listesi, teknik ayrintiya hizli erisim, kaynak/provenance, kritik olcum ve kontroller | Hizlandirilmis deneyim guvenlik uyarilarini veya kritik dogrulamayi kaldirmamali | Q007, Q010-Q011, Q014, Q021 |

## Cross-cutting user states

Bunlar ayri persona olarak CONFIRMED degildir; ayni kullanicinin farkli yolculuk anlaridir:

- **Known-task state — CONFIRMED (Q006):** Kullanici yapmak istedigi islemi bilir ama parca adi, hazirlik veya sira konusunda yardim ister.
- **Symptom-first state — CONFIRMED (Q006, Q012, Q022):** Kullanici yalniz belirtiyi bilir ve teshis yoluyla uygun isleme ulasmak ister.
- **Interrupted-work state — CONFIRMED (Q028):** Islem yarida kalmistir ve kullanici guvenli sekilde devam etmek ister.
- **Mismatch/recovery state — CONFIRMED (Q025-Q027):** Rehber ile gercek motosiklet uyusmaz, kullanici takilir veya beklenmeyen durum olusur.

## Open segmentation questions

- Deneyim seviyesi ikili mi yoksa islem bazli degisen bir yeterlilik profili mi olmalidir?
- Bir kullanici farkli islem kategorilerinde farkli deneyim seviyesine sahip olabilir mi?
- Profesyonel/servis kullanicilari, ekip halinde calisanlar veya yalniz motosiklet sahibi ama islemi kendi yapmayan kisiler hedef kullanici midir?

Bu sorular Batch 01 tarafindan cevaplanmamistir.