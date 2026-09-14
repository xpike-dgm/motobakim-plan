# Motobakim Plan

Bu depo, Motobakim mobil uygulamasinin kod deposu degil; kodlamaya baslamadan once urun bilgisini, tasarim referanslarini, teknik kararlari, teslimat planini ve AI-native gelistirme mimarisini olusturmak icin kullanilan **kalici proje beyni (Project Brain)** deposudur.

## Ana hedef

Herhangi bir AI, onceki sohbetleri bilmese dahi bu depodaki source-of-truth dosyalarini okuyarak projenin guncel durumunu yeniden kurabilmeli; ileride `TASK-105'i uygula` gibi atomik bir talebi, gerekli baglami kendisi bulup mevcut sistemi bozmadan tamamlayabilmelidir.

## Degismez ilke

> Sohbet hafizasi otorite degildir. Depodaki onayli source-of-truth dosyalari otoritedir.

AI'lar onceki sohbetlere veya kendi hatirladiklarina guvenmek yerine depoyu okumali, kararlar arasindaki celiskileri kaydetmeli ve her onemli asama sonunda proje beynini guncellemelidir.

## Planlanan surec

1. Planning workspace ve kalici proje hafizasi sistemi
2. Teknik olmayan kapsamli urun kesfi (iteratif soru/cevap)
3. Ekran envanteri ve her ekran/durum icin onayli referans tasarimlar
4. Coklu AI ile teknoloji, altyapi, guvenlik ve operasyon kararlarinin tartisilmasi
5. Projenin Epic -> Capability -> Feature -> Flow -> Task seklinde parcalanmasi
6. AI-native gelistirme mimarisinin ve proje-koruma kurallarinin tasarlanmasi
7. Kesinlesen mimarinin repository seviyesinde kurulmasi ve task-bazli gelistirmeye gecis

## Yeni bir AI nereden baslamali?

Her yeni AI oturumunda ilk okunacak dosya:

`00_CONTROL/AI_START_HERE.md`

Ardindan yalnizca o dosyanin yonlendirdigi gerekli baglam okunmalidir.

## Klasorler

- `00_CONTROL/` — otorite, durum, karar, handoff ve degisiklik kayitlari
- `01_PRODUCT/` — teknik olmayan urun bilgisi ve domain dili
- `02_DISCOVERY/` — iteratif urun kesfi oturumlari
- `03_DESIGN/` — ekran envanteri ve onayli gorsel referanslar
- `04_TECH/` — teknoloji degerlendirmeleri ve ADR'ler
- `05_PLANNING/` — epic/feature/task parcala(ma) ve bagimlilik plani
- `06_ARCHITECTURE/` — nihai AI-native sistem ve mimari kurallari
- `07_TASKS/` — atomik gorev tanimlari
- `99_TEMPLATES/` — standardize dokuman sablonlari

## Durum

Su anda **Phase 0 — Project Brain Bootstrap** asamasindayiz. Uygulama teknolojisi veya kod mimarisi henuz secilmemistir.