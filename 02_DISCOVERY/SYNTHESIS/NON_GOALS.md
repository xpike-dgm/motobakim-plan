# NON-GOALS

Status: DRAFT

Bu belge urunun bilerek yapmamasi gereken davranislari ve henuz non-goal oldugu kanitlanmamis sinirlari ayirir.

## Confirmed non-goal behaviors

### NG-001 — Fabricated technical certainty
**CONFIRMED — Q035, Q041-Q044, Q075-Q079, Q095**
MotoBakim dogrulanmamis teknik deger, bakım araligi veya sahte kesinlik uretmeyecek. Cozulmemis kritik kaynak/varyant/bakım belirsizligini gizleyip tek kesin deger gibi sunmak hedef degildir.

### NG-002 — False definitive diagnosis
**CONFIRMED — Q023-Q024, Q035, Q056-Q058**
Yeterli kanit olmadan ariza nedenini kesin veya `en olasi` gibi sunmak, esit olasilikta rastgele parca degisimine yonlendirmek veya sonucsuz teshisi sahte kesinlikle kapatmak hedef degildir.

### NG-003 — Guaranteeing dangerous-work success / bypassing safety gates
**CONFIRMED — Q035, Q045-Q052, Q068-Q069, Q096-Q101**
Tehlikeli/ileri islemin kesin basariyla tamamlanacagini garanti etmek veya motosiklete ozel safety kosulu dogrulanmadan kritik application adimini acmak hedef degildir. Kullanici `yapabilirim` dese bile varyant, kritik bilgi, ekipman, ortam veya zorunlu pre-check eksigi safety gate'i gecirmez.

### NG-004 — Paywalling core safety / core maintenance guidance / user data portability
**CONFIRMED — Q065, Q087, Q114-Q115**
Kritik safety bilgisini, motora uygun temel rehberi, temel bakım takibini veya kullanicinin kendi verisini alma hakkini ucret arkasinda gizlemek hedef degildir.

### NG-005 — Silent rewrite/loss of historical context
**CONFIRMED — Q042-Q043, Q059-Q060, Q073, Q095**
Rehber update/recall veya kullanici duzeltmesi nedeniyle tarihsel islem/surum/degisiklik baglamini sessizce silmek/overwrite etmek hedef degildir.

### NG-006 — Cross-account data mixing
**CONFIRMED — Q092, Q094-Q095**
Bir hesaba ait motosiklet/gecmis/not/fotograf verisinin baska hesapta gorunmesi veya silme isleminin baska hesabin verisini etkilemesi kabul edilen urun davranisi degildir.

### NG-007 — Commercial influence disguised as technical guidance
**CONFIRMED — Q085-Q088, Q095**
Gizli reklam, ucretli urunu teknik olarak `en uygun` diye gostermek, alternatifleri saklamak, ucretli servis siralamasinin teknik karari etkilemesi veya rehberi satis hedefine gore degistirmek hedef degildir.

### NG-008 — Community content masquerading as official guidance
**CONFIRMED — Q081-Q084, Q107**
Kullanici yorumu/ipuclari/deneyimini resmi rehber adimi gibi sunmak veya community yorumlarini resmi numarali talimatlara karistirmak hedef degildir. `Dogrulanmamis kisisel deneyim` official instruction statune yukselemez.

### NG-009 — Forced technical-identifier scavenger hunt as default variant flow
**CONFIRMED USER EXPECTATION — Q066-Q067**
Kullaniciyi teknik kod/etiket/parca kodu/belge bilgisi aramaya zorlamak varsayilan experience degildir. Observable ozellik/fotograf yetersiz kalirsa dogru davranis yanlis varyanta gecmek degil belirsizligi gostermek ve ilgili application adimini kapatmaktir.

### NG-010 — Daily routine notification spam
**CONFIRMED USER PREFERENCE — Q070-Q072**
Routine/onemli ama acil olmayan ayni uyarinin her gun tekrarlanmasi mevcut kullanici beklentisine aykiridir. Bu, tum kullanicilar icin LOCKED cadence degildir.

### NG-011 — Treating teaching content as verified application instruction
**CONFIRMED — Q099, Q103-Q104**
Genel/ogretici bilgi, belirli motosiklet icin application talimati olarak maskelenmemelidir. Teaching erisilebilir kalabilir fakat zarar verebilecek sokme/baglama/ayar adimlari uygunluk dogrulanmadan acilmaz.

### NG-012 — Permanent incompetence framing in professional escalation
**CONFIRMED — Q100-Q101**
Professional help onerisi `sen bunu yapamazsin` veya kullanicinin kalici yetersizligi olarak sunulmamalidir. Eksik kosul, yeniden deneme yolu ve devam eden learning/preparation destegi korunmalidir.

### NG-013 — Opaque or non-appealable moderation
**CONFIRMED — Q105-Q108**
Community contribution'i gerekcesiz kaldirmak, sorunlu bolumu gostermemek veya correction/appeal yolunu tamamen kapatmak hedef degildir. Kademeli enforcement beklenir.

### NG-014 — Treating `verified` as absolute guarantee
**CONFIRMED — Q109-Q110**
`Dogrulanmis` etiketi `kesin sonuc verir`, `her versiyonda aynidir` veya risksiz garanti anlamina gelmemelidir.

### NG-015 — Critical notification flooding or burying
**CONFIRMED — Q111-Q113**
Kritik safety konularini routine reminders arasinda kaybetmek veya uzun aradan donuste eski bildirimleri tek tek yagdirarak anlamli onceligi gizlemek hedef degildir.

### NG-016 — Anonymous overwrite in shared motorcycle history
**CONFIRMED — Q118-Q119**
Paylasilan motosiklette kimin ne eklediginin kaybolmasi, baskasinin kaydinin sessizce degistirilmesi veya private notes'un izinsiz acilmasi hedef degildir.

### NG-017 — Treating archive as delete
**CONFIRMED — Q121**
Motosikleti aktif garajdan kaldirmak history'yi yok etmek anlamina gelmemelidir. `Archive` ve `delete` ayni davranis degildir.

### NG-018 — Running stale critical application without required re-check
**CONFIRMED — Q122**
Critical guide product freshness limitini astigi halde online re-check gerektigini gizleyip application steps'i sonsuza kadar acik tutmak beklenen guven modeli degildir. Exact limit henuz belirlenmemistir.

### NG-019 — Forcing account/permissions/long profile before first product value
**CONFIRMED USER EXPECTATION — Q123**
Mevcut kullanici icin account creation, notification permission veya uzun profil formunu rehber deneyimini gormeden once zorunlu gate yapmak istenen first-use davranisi degildir. Bu teknik identity karari degildir.

## Boundaries, not confirmed non-goals

### Community / social layer
Community tumden kapsam disi degildir. Ayrı provenance/review statuslu, moderate edilen ve itiraz/re-submit yolu olan ikincil bilgi katmani olabilir. Ne kadar genis olacagi final karar degildir.

### Service / marketplace / commercial support
Servis bulma veya parca/arac satin alma tumden non-goal degildir; core self-service rehberin yerini almamali ve teknik uygunlugu ticari etkiden bagimsiz tutmalidir.

### Paid product model
Gelismis analysis, ek storage, multi-garage, personalization ve bazi non-recurring optional tools premium aday olabilir. Abonelik/one-time/hybrid/fiyat/tier modeli secilmemistir.

### Professional/service users
Professional/service kullanicilarinin target persona olup olmadigi henuz cevaplanmamistir. Professional escalation ile profesyoneli hedef kullanici yapmak ayni sey degildir.

### International scope
Turkiye-first Turkce/birim/terminoloji beklentisi kanitlidir; bunun urunu sonsuza kadar yalniz Turkiye'yle sinirladigi sonucu cikarilamaz.

## Still unknown

- Professional escalation exact trigger ve self-service'e donus
- Professional/service target statusu ve segment motivasyon farklari
- Final premium paket/model tercihi
- Gercek delete, community withdrawal ve export provenance lifecycle
- Context-specific evidence taxonomy
- Selective ownership transfer completeness/trust semantigi
- Critical freshness expiry kapsam/semantigi
- Active-repair voice/easy-touch safety confirmation edge case'leri
