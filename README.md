# Motobakim Plan — AI-Native Planning Repository

Bu repository Motobakim mobil uygulamasinin kod deposu degildir. Uygulama kodlanmadan once urun bilgisini, tasarimi, teknoloji kararlarini, teslimat planini ve AI-native gelistirme mimarisini kontrollu bicimde olusturmak icin kullanilan kalici planlama ve proje-hafiza deposudur.

## Degismez Ilke

Sohbet gecmisi source-of-truth degildir. Yeni bir AI oturumu proje baglamini bu repository'den yeniden kurar.

Ilk okunacak belge: `00_CONTROL/AI_START_HERE.md`.

## 8 Asamali Surec

1. `01_WORKSPACE/` — AI calisma sistemi, vizyon, kisit, varsayim ve ortak dil
2. `02_DISCOVERY/` — teknik olmayan iteratif urun kesfi
3. `03_DESIGN/` — ekran/state envanteri ve onayli referans tasarimlar
4. `04_TECH_STRATEGY/` — uzman AI teknoloji tartismasi ve judge sentezi
5. `05_ADR/` — teknoloji/mimari kararlarinin gerekceleriyle kilitlenmesi
6. `06_DELIVERY_PLANNING/` — Epic -> Capability -> Feature -> User Flow -> Task
7. `07_AI_ARCHITECTURE/` — yeni AI'nin guvenli task uygulamasini saglayan gelistirme mimarisi
8. `08_REPOSITORY_BOOTSTRAP/` — kesinlesen mimarinin gercek uygulama repository'sine kurulmasi

Destek klasorleri:
- `00_CONTROL/` — kalici hafiza, durum, karar, phase gate ve source-of-truth yonetimi
- `90_TEMPLATES/` — standardize belge sablonlari
- `99_ARCHIVE/` — aktif otorite olmayan tarihsel belgeler

## Phase Gate Modeli

Bir klasorun mevcut olmasi o asamanin tamamlandigi anlamina gelmez. Gecis kosullari `00_CONTROL/PHASE_GATES.md`, belge durumlari `00_CONTROL/DOCUMENT_REGISTRY.md` tarafindan izlenir.

## Mevcut Durum

8 asamanin calisma iskeleti kuruldu. Urun kesfi, tasarim, teknoloji secimi, ADR, task parcala(ma), nihai mimari ve uygulama kodlama henuz yapilmadi.
