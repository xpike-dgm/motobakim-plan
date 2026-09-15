# KAVRIVA AI USTA UX STRUCTURE 01 — DELEGATED HANDOFF EVIDENCE

Status: EVIDENCE / USER-SELECTION HANDOFF
Date: 2026-09-15
Source package: `PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / AI USTA UX STRUCTURE 01`
Uploaded package SHA-256: `12adaa192aa11038ce7f6f49f8acd0d53f74899453d48d10a9e6e47419be24e5`

Bu belge delegated portable package'in repository-level evidence kaydidir. Canonical approval authority degildir; main-manager QA ve controlled decision ayrica kaydedilir.

## User Selection — Verbatim

> **A1 iyi**

Delegated interpretation:
**A1 — Guided Split** user-selected structure.

## Selected Structure Summary

AI Usta root surface default durumda yalniz:
1. compact `AI Usta` page identity,
2. compact selected motorcycle context (`Motosikletim`),
3. `Nasil yardimci olayim?` prompt'u,
4. `Bir is yapmak istiyorum`,
5. `Motorda bir sorun var`,
6. gerekirse low-prominence/on-demand help,
7. approved bottom navigation

gosterir.

Target:
**1 context + 1 soru + 2 yol.**

Default ekran:
- dashboard degil,
- chat transcript degil,
- technical-answer surface degil,
- feature/card collection degil.

## Known-Task Entry

`AI Usta`
-> `Bir is yapmak istiyorum`
-> `SCR-009 Known Task Find / Select`
-> `SCR-010 Guide Scope / Fit / Selection Preview`
-> `SCR-011 Preparation & Readiness`
-> only when approved fit/readiness/safety conditions allow, application flow.

Task declaration fit/readiness authority degildir.

## Symptom-First Entry

`AI Usta`
-> `Motorda bir sorun var`
-> `SCR-019 Symptom Capture`
-> `SCR-020 Diagnosis Checks`
-> `SCR-021 Diagnosis Outcome / Handoff`.

Symptom input'tan direct parts-replacement recommendation uretilmez. Evidence yetersizse `unresolved` valid result'tir.

## Natural-Language Boundary

A1 root launcher'da free-form composer zorunlu degildir.

Natural language downstream `SCR-009` / `SCR-019` icinde sunlar icin kullanilabilir:
- task'i kendi kelimeleriyle tarif etmek,
- symptom anlatmak,
- clarification,
- observable evidence capture'a yardim.

Natural language sunlar icin authority olamaz:
- unsupported torque/value/specification,
- verified source replacement,
- unsupported definitive diagnosis,
- motorcycle-fit guessing,
- readiness/safety bypass,
- approved guide disi physical instruction,
- self-assertion ile critical gate acma.

## Safety / Trust Tests

- `Fren yaparken ses geliyor, neyi degistireyim?` -> direct replacement yok; symptom-first path.
- `Balata degistirecegim.` -> physical step direct acilmaz; task -> fit -> readiness.
- AI Usta output'u verified guide gibi sunulmaz.
- Safety-critical durum normal hierarchy'yi kesebilir ve reason + immediate action + re-entry gostermelidir.

## Clutter Guardrails

Default root'ta olmamali:
- multiple feature cards,
- maintenance/history/community summaries,
- KPI/statistics,
- chat history,
- popular-question grid,
- technical recommendations,
- multiple equal-weight extra CTAs,
- large decorative brand hero.

Iki intent choice mutual-exclusive top-level paths'tir; visual reference turunda bunlar bulky card stack'e donusturulmemelidir.

## Accessibility

- intent'ler icon-only olamaz,
- text labels korunur,
- sufficiently large tap targets,
- selected motorcycle context meaningful accessible label tasir,
- focus order hierarchy ile uyumlu,
- color tek semantic carrier degildir,
- language/unit/accessibility support profile/account prerequisite olamaz.

## Bottom-Bar Integration

Approved order unchanged:
**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

AI Usta selected state'tedir.

## Input for Next Visual Round

Fixed UX:
- A1 Guided Split,
- compact motorcycle context,
- `Nasil yardimci olayim?`,
- two-entry intent structure,
- five-tab bottom bar,
- no dashboard/card stack,
- no chat transcript,
- no generated technical answer/diagnostic result.

Visual exploration may refine typography, spacing, two-intent treatment, icon character, restrained brand placement, selected-tab treatment and V10 adaptation without changing routing/authority semantics.
