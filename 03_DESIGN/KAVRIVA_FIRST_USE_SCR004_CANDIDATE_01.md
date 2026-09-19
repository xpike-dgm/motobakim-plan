# KAVRIVA SCR-004 VISUAL CANDIDATE 01

Status: `APPROVED WORKING SCR-004 REFERENCE`
Date: 2026-09-17
Family: `FAM-01 — First Use / Motorcycle Context`
Context: `SCR-004 — Fit Confirmation / Missing Distinction`

## Purpose

This record preserves the controlled visual candidate accepted by the user as the SCR-004 working reference.

Two separate images represent two mutually exclusive states of the same screen context. The product shows only the state supported by current evidence; the states are not simultaneous choices.

## Candidate Images

| Candidate | State | File | Size | SHA-256 |
|---|---|---|---:|---|
| `F01` | Fit confirmed | `refernces/F01-SCR-004-Fit-Confirmed-candidate-v1.png` | 941x1672 | `bd210a743f9afe74da3de78f116be7e70d2462a8422fd9dd3a2d8aa79779953a` |
| `F02` | Missing distinction | `refernces/F02-SCR-004-Missing-Distinction-candidate-v1.png` | 941x1672 | `c9b9683e37bde524ce79fe37a287a0e7ad1bcff9e5601bcd5e26a12eb4d3b902` |

The files were generated with the built-in image-generation workflow using the local L05A, V10, D02 and D04 references. Generated imagery and fixture text are visual-design evidence only; they are not motorcycle-fit or technical evidence.

Exact generation prompt evidence:
- `03_DESIGN/KAVRIVA_FIRST_USE_SCR004_IMAGEGEN_PROMPTS.md`

## Shared Context

- restrained L05A/Kavriva header,
- compact `Motosikletim` context,
- illustrative task fixture: `Ön fren balatası kontrolü`,
- text-led state explanation,
- one dominant action,
- no bottom navigation in this first-use decision context.

The absence of bottom navigation is a candidate treatment only and does not change `REF-NAV-001`.

## F01 — Fit Confirmed

Working meaning:
- current evidence is sufficient for the selected motorcycle/guide context,
- applicability does not guarantee success,
- preparation and safety checks still follow,
- the dominant action routes to `SCR-011 Preparation & Readiness`, not directly to physical application.

Candidate actions:
- `Hazırlığı görüntüle`,
- `Ayrımı yeniden gözden geçir`.

## F02 — Missing Distinction

Working meaning:
- current evidence is insufficient to confirm motorcycle-specific applicability,
- variant-specific application remains closed,
- uncertainty remains explicit and is not converted into a positive match.

Candidate actions:
- `Ayrımı yeniden çöz` -> `SCR-003`,
- `Öğrenme görünümünü aç` -> `SCR-013`,
- `Motosiklet bilgilerini düzenle` -> motorcycle-context correction.

No `Rehberi başlat`, `Uygulamaya geç`, `Hazırım` or continue-anyway action is authorized in this state.

## Manager QA

Result: `PASS_WITH_CONSTRAINTS / USER APPROVED`

The pair preserves the approved V10 visual DNA, uses the L05A direction rather than the rejected blue-K drift, keeps status meaning readable without color alone, avoids generated mechanical imagery as evidence and preserves the fit/application gate.

Exact copy, typography, icons, spacing, tokens, surface modality and navigation visibility remain non-final.

## User Acceptance

Verbatim:
> şuan 3 bitti mi onları onaylıyorum

The accepted candidate now participates in `REF-FIRSTUSE-001`. Exact copy, tokens, modality and implementation details remain non-final.
