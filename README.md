# Motobakim Plan

Bu repository su anda yalnizca Motobakim projesinin **kalici AI hafiza yonetimi** icin kullaniliyor.

## Amac

Yeni bir ChatGPT veya AI oturumu onceki sohbetleri bilmese bile repository icindeki kontrol dosyalarini okuyarak:

- projenin nerede kaldigini,
- hangi kararlarin kesinlestigini,
- hangi konularin henuz acik oldugunu,
- bir onceki oturumdan ne devralmasi gerektigini

yeniden anlayabilmelidir.

## Temel ilke

> Sohbet hafizasi source of truth degildir. Kalici proje hafizasi GitHub repository icinde tutulur.

## Yeni oturum baslangici

Her yeni oturum once su dosyadan baslamalidir:

`00_CONTROL/AI_START_HERE.md`

## Hafiza cekirdegi

- `00_CONTROL/AI_START_HERE.md`
- `00_CONTROL/CURRENT_STATE.md`
- `00_CONTROL/SOURCE_OF_TRUTH.md`
- `00_CONTROL/DECISION_LOG.md`
- `00_CONTROL/OPEN_QUESTIONS.md`
- `00_CONTROL/HANDOFF.md`
- `00_CONTROL/MEMORY_PROTOCOL.md`
- `00_CONTROL/CHANGELOG.md`

## Mevcut kapsam

`PHASE-0 / MEMORY SYSTEM READY`

Su anda urun kesfi, UI tasarimi, teknoloji secimi, uygulama mimarisi, task planlama veya kodlama yapilmiyor. Bu calismalar ancak kullanicinin sonraki acik talimatiyla baslatilacak.
