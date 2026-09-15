# Kavriva — V10 Signature Kavriva

## Karar

V10, Kavriva’nın ana görsel yönü olarak seçildi. Referans ekran:

[Kavriva_V10_Signature-Kavriva.png](Kavriva_V10_Signature-Kavriva.png)

Bu paket, V10’un marka karakterini koruyarak U04 akışının uygulamaya aktarılması için başlangıç kararlarını içerir.

## Görsel yön

- **Marka karakteri:** L05A “Precision Fit”; kontrollü açılar, net hizalama, ölçülü geometrik ikonlar.
- **Zemin:** Beyaza yakın, temiz ve ferah yüzey.
- **Ana metin:** Derin lacivert-siyah / graphite.
- **Vurgu:** Elektrik mavisi; ilerleme, annotation, güven işareti ve birincil CTA’da kontrollü kullanılır.
- **Fotoğraf:** Gerçekçi, keskin, inceleme odaklı; metal yüzey detayları korunur.
- **Yüzey dili:** Orta derecede yuvarlatılmış köşeler, düşük dekorasyon, güçlü tipografik hiyerarşi.
- **Logo kullanımı:** L05A markası header’da görünür ve nettir. Logo geometrisi kart, pattern veya arka plan süsü olarak tekrarlanmaz.

## U04 kilitleri

Aşağıdaki sıra ve görünür durum korunur:

1. Header: **Kavriva** ve `Örnek Motosiklet • 2021 • ABS`
2. Progress: `Adım 4 / 9`
3. Başlık: `Kaliper kontrolü`
4. Alt başlık: `Ön fren balatası değişimi`
5. Trust satırı: `Doğrulanmış rehber • Motosiklete özel`
6. Tek dominant görev görseli ve `Burayı kontrol et` annotation’ı
7. Talimat metni
8. Görünür fakat sakin güvenlik satırı
9. Kapalı ve düz `Detaylar` satırı
10. Tek dominant CTA: `Kontrolü tamamladım`
11. İkincil kurtarma bağlantısı: `Sorun var`

## Uygulama ilkeleri

- Birincil CTA en güçlü eylem olarak kalır.
- `Sorun var` görünür, ancak CTA ile rekabet etmez.
- Güvenlik mesajı görünür olur; alarm bandına dönüşmez.
- Trust satırı kompakt kalır.
- Yeni kart, panel, tab, chip, timeline, dashboard, KPI veya ikinci eş-ağırlıklı CTA eklenmez.
- Türkçe karakterler, satır kırılımları ve küçük metinlerde okunabilirlik kontrol edilir.
- Mavi vurgu, marka imzası olarak sınırlı ve tutarlı kullanılır; her öğe mavi yapılmaz.

## Başlangıç tasarım token’ları

| Token | Başlangıç değeri | Kullanım |
|---|---|---|
| Canvas | `#F8FAFC` | Ana ekran zemini |
| Ink | `#101827` | Başlıklar ve ana metin |
| Secondary | `#5C6B84` | Meta, trust ve recovery |
| Kavriva Blue | `#1268F3` | Progress, annotation, CTA vurgusu |
| Rule | `#D7DEE8` | Detaylar satırı ayırıcıları |
| CTA surface | `#0E5BD8` | Birincil eylem yüzeyi |

Bu değerler üretim renk sistemi değil, V10’un ilk uygulama turu için görsel başlangıç noktalarıdır.

## Kabul kriterleri

- Ekran ilk bakışta U04 olarak tanınır.
- L05A marka işareti header’da net ve dengeli görünür.
- Fotoğraf, talimat ve annotation birlikte tek bir görev odağı oluşturur.
- CTA, recovery link ve güvenlik satırı arasında doğru ağırlık korunur.
- Ekran yeni navigasyon veya bilgi mimarisi katmanı eklemeden karakter kazanır.
- Açık temada yüksek kontrast ve saha koşullarında okunabilirlik korunur.

## Kapsam notu

Bu turda repo kaynak dosyaları değiştirilmedi; paket ve referans görsel çıktı klasöründe tutuluyor. Fontun kesin seçimi, responsive ölçüler ve üretim kodu sonraki uygulama turunun kararlarıdır.
