# AI START HERE

Bu dosya Motobakim projesine ilk kez giren veya yeni bir sohbet/agent oturumunda calisan her AI icin zorunlu baslangic protokoludur.

## 1. Temel Kural

Sohbet gecmisi, model hafizasi veya AI varsayimlari source-of-truth degildir. Proje gercegi bu repository'deki kontrollu belgelerden okunur.

## 2. Her Yeni Oturumda Zorunlu Okuma Sirasi

1. `/AGENTS.md`
2. `00_CONTROL/MANAGER_START_HERE.md`
3. `00_CONTROL/NEXT_ACTION.md`
4. `00_CONTROL/CURRENT_STATE.md`
5. `00_CONTROL/SOURCE_OF_TRUTH.md`
6. `00_CONTROL/DECISION_LOG.md`
7. `00_CONTROL/OPEN_QUESTIONS.md`
8. `00_CONTROL/WORKFLOW_MAP.md`
9. `00_CONTROL/PHASE_GATES.md`
10. `00_CONTROL/DOCUMENT_REGISTRY.md`
11. Aktif asamanin `README.md` ve yalniz mevcut is icin gereken detay belgeleri

Tum repository'yi refleks olarak okumak yerine minimum yeterli baglam ilkesi uygulanir.

## 3. Calismaya Baslamadan Once

AI repo icinden sunlari belirlemelidir:
- Su an hangi asamadayiz?
- Bu oturumun amaci nedir?
- Bir sonraki phase gate nedir?
- Hangi belgeler APPROVED/LOCKED, hangileri EMPTY/DRAFT/REVIEW?
- Hangi dosyalar bu isin girdisi, hangileri ciktisi?
- Hangi bilgiler bilinmiyor veya celiskili?

Cevabi bilinmeyen konu tahmin edilip gercek gibi yazilamaz.

## 4. Belge / Karar Durumlari

`EMPTY` — yapisi var, henuz bilgi yok.
`DRAFT` — calisma halinde.
`REVIEW` — kontrol/onay bekliyor.
`PROPOSED` — karar adayi.
`APPROVED` — kullanilmasi onaylandi.
`LOCKED` — acik degisiklik karari olmadan degistirilemez.
`SUPERSEDED` — daha yeni kayit tarafindan gecersiz kilindi.
`ARCHIVED` / `DEPRECATED` — aktif kaynak degil.

## 5. Kanit ile Karari Karistirma

- `02_DISCOVERY/SESSIONS/` ham soru-cevap kanitidir; urun source-of-truth'u `02_DISCOVERY/SYNTHESIS/` belgeleridir.
- `04_TECH_STRATEGY/` arguman ve oneridir; teknoloji karari ancak `05_ADR/` ile APPROVED/LOCKED olur.
- Tasarim adaylari otorite degildir; `03_DESIGN/REFERENCE_INDEX.md` icinde APPROVED/LOCKED referanslar otoritedir.
- Planlama task'i kod degisikligi yetkisi vermez; task execution kurallari 07. asamada kesinlesir.

## 6. Celiski Protokolu

Yeni bilgi mevcut bilgiyle celisirse eski bilgiyi sessizce silme. Celiski kaydedilir, kaynaklar karsilastirilir, gerekirse `OPEN_QUESTIONS.md` acilir. Kullanici veya yetkili karar mekanizmasi netlestirdikten sonra source-of-truth guncellenir, eski kayit SUPERSEDED yapilir ve `CHANGELOG.md` guncellenir.

## 7. Phase Disiplini

AI bir sonraki asamaya kendiliginden gecemez. `PHASE_GATES.md` kosullari saglanmali ve mevcut talimat o asamayi kapsamalidir. Ornegin urun kesfi devam ederken framework secilmez; teknoloji tartismasi sirasinda ADR kilitlenmis varsayilmaz; bootstrap tamamlanmadan feature kodlamaya baslanmaz.

## 8. Her Anlamli Calisma Sonunda Hafiza Tazeleme

En az su belgeler kontrol edilir:
- `CURRENT_STATE.md`
- `NEXT_ACTION.md`
- `DECISION_LOG.md`
- `OPEN_QUESTIONS.md`
- `DOCUMENT_REGISTRY.md`
- Ilgili asamanin source-of-truth belgeleri
- `CHANGELOG.md`
- `HANDOFF.md`

## 9. Proje Yonetim Modeli

ChatGPT proje mimari muhendisi ve yoneticisi olarak sureci koordine eder. Diger AI'lar uzman, tartisma katilimcisi, reviewer veya implementer olabilir. Nihai proje gercegi sohbetlerde degil bu repository'de tutulur.

Alt ajan model yetkisi `PROJECT_CHAT_INSTRUCTIONS.md` ve `DEC-0022` tarafindan sinirlanir. Yalnizca Luna Max
(`gpt-5.6-luna`, `max`) onceden ek kullanici izni olmadan calistirilabilir. Diger modeller icin her kullanimdan once
acik kullanici izni gerekir.

AI-native execution hedefi `DEC-0028` ve `PROJECT_SCOPE_ADDENDUM_AI_NATIVE_EXECUTION_SYSTEM.md` ile baglayicidir.
Phase 5–8 ve Development'da yeni bir AI'nin tum projeyi okumasi varsayilmaz; gorev secimi, minimum yeterli context pack,
izinli degisiklik alani, Obsidian-compatible iliski graph'i, contract/boundary kurallari ve completion evidence sistemi
tarafindan yonlendirilmelidir. `All tasks DONE` tek basina proje tamamlanmasi degildir.

`DEC-0029` geregi kullanici nontechnical product/decision owner'dir ve proje AI-operated tasarlanir. AI kullanicidan kod,
debugging, build tamiri veya aciklanmamis mimari tercih bekleyemez. Teknik kararlar outcome/risk/cost/reversibility diline
cevrilir; AI sonucu independent review ve evidence olmadan dogru sayilmaz.
