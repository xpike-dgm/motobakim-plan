# KAVRIVA AI USTA UX STRUCTURE

Status: APPROVED WORKING UX STRUCTURE
Approved by: USER selection + main-manager QA — 2026-09-15
Decision: DEC-0018
Reference: `REF-AIUSTA-001`
Source evidence: `KAVRIVA_AI_USTA_UX_STRUCTURE_01_HANDOFF.md`
Review: `KAVRIVA_AI_USTA_UX_STRUCTURE_REVIEW.md`

## Approved Direction

**A1 — Guided Split**

User selection — verbatim:
> A1 iyi

## Core Interaction

AI Usta root surface bir technical-answer/chat-home degildir. Approved role:
**controlled intent router / guided assistance entry**.

Default hierarchy:
1. compact `AI Usta` page identity,
2. compact selected motorcycle context,
3. short prompt: `Nasil yardimci olayim?`,
4. `Bir is yapmak istiyorum`,
5. `Motorda bir sorun var`,
6. optional low-prominence help/explanation,
7. approved global bottom bar with `AI Usta` selected.

Target:
**1 context + 1 prompt + 2 paths.**

## Known-Task Path

`AI Usta`
-> `Bir is yapmak istiyorum`
-> `SCR-009 Known Task Find / Select`
-> `SCR-010 Guide Scope / Fit / Selection Preview`
-> `SCR-011 Preparation & Readiness`
-> only if approved conditions allow, application flow.

Task declaration alone:
- fit confirmation degildir,
- readiness proof degildir,
- physical application authorization degildir.

## Symptom-First Path

`AI Usta`
-> `Motorda bir sorun var`
-> `SCR-019 Symptom Capture`
-> `SCR-020 Diagnosis Checks`
-> `SCR-021 Diagnosis Outcome / Handoff`.

Symptom input direct part replacement veya unsupported definitive diagnosis uretmez. Evidence yetersizse unresolved valid outcome'dur.

## Natural-Language Boundary

Root launcher free-form composer gerektirmez.

Natural language downstream task/symptom capture'da kullanilabilir:
- task'i user's own words ile tarif etmek,
- symptom anlatmak,
- clarification,
- observable evidence capture.

Natural language authority olamaz:
- unsupported torque/value/specification,
- verified source replacement,
- unsupported definitive diagnosis,
- motorcycle-fit guessing,
- readiness/safety bypass,
- approved guide disi physical instruction,
- self-assertion ile critical gate acma.

## Safety / Trust

- Safety-critical condition normal flow'u durdurabilir.
- Stop state reason + consequence + immediate action + re-entry vermelidir.
- AI Usta output'u verified guide gibi sunulmaz.
- Generic shield/check certification semantics kullanilmaz.
- Technical guidance authority downstream approved guide/provenance/state architecture'dadir.

## Clutter Rules

Default root'ta olmamali:
- maintenance/history/community summaries,
- feature grids,
- KPI/statistics,
- chat transcript/history,
- popular-question grids,
- technical recommendations,
- generated diagnosis/result,
- multiple extra equal-weight CTAs,
- large decorative logo hero.

Two intents large accessible targets olabilir; fakat bulky card-stack veya nested-card treatment'e donusmemelidir.

## Selected Motorcycle Context

Motorcycle context compact ve anlasilir kalir. AI Usta task intent'i ile rekabet etmez.

Motorcycle switching/lifecycle authority Garaj'dadir; AI Usta yalniz current context'i gosterir ve gerekiyorsa controlled context change affordance'i sunabilir.

## Accessibility

- intent'ler text label tasir; icon-only degildir,
- tap targets yeterince buyuk,
- focus order hierarchy ile ayni,
- color tek semantic carrier degil,
- Dynamic Type / larger text iki path'i anlasilmaz hale getiremez,
- language/unit/accessibility support profile/account prerequisite degildir.

## Global Navigation Integration

Approved order:
**Garaj · Bakim · AI Usta · Gecmis · Topluluk**

AI Usta selected state'tedir.

AI Usta diger tabs'in responsibilities'ini yeniden kendi root'unda toplamaz.

## Visual Reference Authority Boundary

Next visual-reference work must preserve:
- A1 two-path structure,
- compact motorcycle context,
- `Nasil yardimci olayim?`,
- bottom-bar labels/order,
- known-task -> `SCR-009`,
- symptom-first -> `SCR-019`,
- safety/fit/readiness/trust authority boundaries.

May vary/refine:
- typography,
- spacing,
- two-intent visual treatment,
- icon character,
- restrained L05A presence,
- V10 adaptation,
- selected-tab treatment,
- responsive/accessibility-conscious density.

## Not Finalized

- exact production icons,
- exact color/font/spacing/radius tokens,
- optional conversational features beyond A1 root,
- active physical-work bottom-bar visibility,
- first post-onboarding landing tab,
- technology/LLM/provider/backend architecture.
