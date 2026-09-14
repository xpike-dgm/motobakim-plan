# CONSTRAINTS

Status: REVIEW

Bu dosya, degistirilmesi zor veya proje boyunca korunmasi gereken yuksek seviye sinirlari tutar. Normal feature gereksinimleri burada listelenmez.

| ID | Constraint | Source | Status | Notes |
|---|---|---|---|---|
| CON-001 | Sunulan teknik bilgi kullanicinin gercek motosiklet konfigurasyonuna yeterince uygun olmalidir; genel bilgi motosiklete ozel bilgi gibi sunulamaz. | USER | CONFIRMED | Hangi motosiklet kimlik/variant bilgilerinin gerekli oldugu discovery'de netlesecek. |
| CON-002 | Teknik degerler ve motosiklete ozel bilgiler uydurulamaz; urun dogrulanmis/güvenilir bilgi hedefini korumalidir. | USER | CONFIRMED | `Dogrulanmis bilgi` standardinin kaynagi ve seviyesi henuz tanimli degildir. |
| CON-003 | Rehber deneyimi, ilgili risk ve guvenlik uyarilarini kullanicidan saklamamalidir. | USER | CONFIRMED | Uyari seviyeleri ve durdurma kosullari discovery/sonraki guvenlik planlamasinda netlesecek. |
| CON-004 | Urunun ana rehber deneyimi, hic bilmeyen veya az deneyimli bir kullanicinin neyi neden yaptigini anlayabilecegi aciklik hedefini korumalidir. | USER | CONFIRMED | Bu hedef her islem turunun gercekte tek basina yapilabilir oldugu anlamina gelmez. |

## Classification Note

Delegated AI ciktisindaki su maddeler constraint olarak kabul edilmedi; bunlar urun kapsami veya fonksiyonel gereksinim niteligindedir ve ilgili discovery/synthesis belgelerinde ele alinacaktir:

- Islem oncesi arac/malzeme listesi
- Asamali ve gorsel rehber sunumu
- Rutin bakim disindaki mekanik/elektriksel kapsam
- Bakim/islem gecmisinin tutulmasi
- Yaklasan bakim ve hatirlatmalar
- Uzmanlik gerektiren/tehlikeli islemlerin kapsama alinmasi istegi

Son madde ayrica acik bir guvenlik/kapsam sorusu olarak izlenmektedir; henuz kosulsuz urun politikasi degildir.
