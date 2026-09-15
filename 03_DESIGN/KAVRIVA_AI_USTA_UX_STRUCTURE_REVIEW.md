# KAVRIVA AI USTA UX STRUCTURE — MAIN-MANAGER REVIEW

Status: APPROVED REVIEW RECORD
Date: 2026-09-15
Source evidence: `KAVRIVA_AI_USTA_UX_STRUCTURE_01_HANDOFF.md`
Source package SHA-256: `12adaa192aa11038ce7f6f49f8acd0d53f74899453d48d10a9e6e47419be24e5`
User selection: `A1 iyi`

## Result

`PASS_WITH_CONSTRAINTS`

A1 — Guided Split, approved five-tab navigation ve working screen-family specs ile uyumludur. AI Usta'yi free-form technical authority yerine controlled intent-router olarak tutar ve onceki clutter/card-stack problemini azaltir.

## Why It Passes

- Root interaction tek bir question + two intents seviyesinde kalir.
- Known-task journey approved `SCR-009` flow'una controlled handoff yapar.
- Symptom-first journey approved `SCR-019` flow'una controlled handoff yapar.
- Fit/readiness/freshness/safety gates bypass edilmez.
- Natural language technical source-of-truth gibi konumlandirilmaz.
- Symptom'dan direct replacement / unsupported diagnosis uretilmez.
- Bottom bar responsibilities yeniden AI Usta icine toplanmaz.
- No dashboard, no chat-history surface, no feature-grid requirement.
- Novice user AI'ya ne yazacagini dusunmeden intent secebilir; experienced user iki interaction path'inden hizla ilerleyebilir.

## Constraint 01 — Two Intents Must Not Become a Card Stack

A1 iki top-level intent gerektirir, fakat production visual'da bunlar iki buyuk content-card + supporting cards + examples seklinde sisirilmemelidir.

Target:
**1 context + 1 prompt + 2 clear choices.**

Intent treatment large tap targets olabilir; fakat visual hierarchy sade, flat ve low-decoration kalmalidir.

## Constraint 02 — Selected Motorcycle Context Is Compact

Selected motorcycle context AI Usta'nin ana content'i degildir. Kullanici hangi motorcycle context'te oldugunu anlamalidir; lifecycle/switch management Garaj responsibility'sinde kalir.

Context affordance compact olmalidir ve AI Usta task intent'i ile rekabet etmemelidir.

## Constraint 03 — No Root Free-Form Technical Chat Requirement

A1 approval root'ta free-form composer gerektirmez.

Natural-language input downstream task/symptom capture'da kullanilabilir. Gelecekte optional assistant input eklenmek istenirse A1'i sessizce A2/A3'e ceviremez; controlled refinement gerekir.

## Constraint 04 — Ambiguous User Needs Need a Quiet Escape

Iki intent yeterince ayrik olsa da kararsiz kullanici icin low-prominence `Hangisini secmeliyim?` / brief explanation gibi accessibility/help affordance'i olabilir.

Bu third equal-weight path degildir ve default hierarchy'yi buyutmez.

## Constraint 05 — AI Authority Must Stay Visually Honest

- AI Usta generated technical answer paneli root'ta bulunmaz.
- `verified`, safety-certified veya guaranteed-repair izlenimi veren badge/icon kullanilmaz.
- Technical guidance authority downstream verified guide/provenance/state architecture'dadir.

## Visual Reference Implications

Next visual round A1 hierarchy'yi freeze etmelidir:
- compact motorcycle context,
- `Nasil yardimci olayim?`,
- two intent choices,
- fixed five-tab nav with AI Usta selected,
- no visible chat transcript,
- no technical answer/result.

V10 visual DNA uygulanabilir fakat U04 layout literal olarak kopyalanmaz.

## Approval Boundary

Bu review A1'i working AI Usta UX structure olarak downstream visual-reference work icin kabul eder.

Bu approval:
- LLM/provider/backend secmez,
- conversational AI architecture kilitlemez,
- exact icons/colors/spacing/animation finalize etmez,
- active physical work'te bottom-bar behavior'i resolve etmez,
- first post-onboarding landing tab'i resolve etmez,
- Phase 4'e gecmez.
