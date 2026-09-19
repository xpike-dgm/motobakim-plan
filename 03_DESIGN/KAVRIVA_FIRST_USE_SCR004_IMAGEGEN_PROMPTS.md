# KAVRIVA SCR-004 — IMAGEGEN PROMPTS

Date: 2026-09-17
Mode: built-in image generation
Use case: `ui-mockup`
Status: EVIDENCE FOR `KAVRIVA_FIRST_USE_SCR004_CANDIDATE_01.md`

## Input References

- `refernces/Kavriva_L05A.png` — canonical working logo-direction reference
- `refernces/Kavriva_V10_Signature-Kavriva.png` — visual-DNA reference
- `refernces/D02-SCR-010-Guide-Scope-Fit.png` — fit/scope continuity reference
- `refernces/D04-SCR-012-Readiness-Hold-Recheck.png` — hold-state continuity reference

## Prompt F01 — Fit Confirmed

```text
Use case: ui-mockup
Asset type: portrait 9:16 mobile app screen, Phase-3 working visual reference
Primary request: Create the Kavriva SCR-004 Fit Confirmation screen in the FIT-CONFIRMED state.
Input images: Image 1 is the canonical L05A logo reference and must be followed faithfully as the only brand mark. Image 2 supplies V10 visual DNA only. Image 3 supplies guide/fit layout continuity. Image 4 supplies state clarity and spacing continuity.
Style/medium: polished realistic mobile product UI, not concept art; near-white canvas, deep navy/graphite typography, restrained electric-blue accent, moderate corner rounding, thin separators, calm technical precision, low visual noise.
Composition/framing: one complete smartphone screen only, portrait, no device mockup frame, clear readable Turkish typography, large tap targets. Header with back arrow and small faithful L05A Kavriva mark. Compact context "Motosikletim". Small illustrative task label "Ön fren balatası kontrolü". Main title "Bu rehber senin motosikletin için uygun mu?"
Text (verbatim): "Eşleşme doğrulandı"; "Bu rehber, seçtiğin motosiklet bağlamıyla mevcut kanıta göre eşleşiyor."; "Bu durum başarı garantisi değildir. Hazırlık ve güvenlik koşulları ayrıca kontrol edilir."; "Eşleşmeyi destekleyen bilgiler"; "Kaynak ve güncellik"; primary button "Hazırlığı görüntüle"; secondary action "Ayrımı yeniden gözden geçir".
Constraints: Render the Turkish copy verbatim and exactly once. Use a simple blue status line or dot, never a shield/check certification badge. Do not imply guaranteed success. Do not show motorcycle/mechanical hero imagery. No bottom navigation. One dominant CTA. No dashboard, KPI, card stack, confetti, AI sparkle, invented technical codes/values/part numbers/prices. Do not reuse or invent the blue K-like logo from supporting references. Working reference, not production-final UI.
```

## Prompt F02 — Missing Distinction

```text
Use case: ui-mockup
Asset type: portrait 9:16 mobile app screen, Phase-3 working visual reference
Primary request: Create the Kavriva SCR-004 Fit Confirmation screen in the MISSING-DISTINCTION state.
Input images: Image 1 is the canonical L05A logo reference and must be followed faithfully as the only brand mark. Image 2 supplies V10 visual DNA only. Image 3 supplies guide/fit layout continuity. Image 4 supplies hold-state clarity and spacing continuity.
Style/medium: polished realistic mobile product UI, not concept art; near-white canvas, deep navy/graphite typography, restrained electric-blue accent, a restrained amber attention accent, moderate corner rounding, thin separators, calm technical precision, low visual noise.
Composition/framing: one complete smartphone screen only, portrait, no device mockup frame, clear readable Turkish typography, large tap targets. Use the exact same shared geometry and context as the confirmed state. Header with back arrow and small faithful L05A Kavriva mark. Compact context "Motosikletim". Small illustrative task label "Ön fren balatası kontrolü". Main title "Bu rehber senin motosikletin için uygun mu?"
Text (verbatim): "Bir ayrım daha gerekli"; "Bu rehberin senin motosikletin için uygun olduğunu henüz yeterli kanıtla doğrulayamıyoruz."; "Motosiklete özel uygulama, eşleşme netleşene kadar açılmaz."; "Gerekli ayrım henüz net değil."; primary button "Ayrımı yeniden çöz"; secondary action "Öğrenme görünümünü aç"; tertiary action "Motosiklet bilgilerini düzenle".
Constraints: Render the Turkish copy verbatim and exactly once. Use an amber attention icon plus text; do not use a red failure treatment. Do not show "Rehberi başlat", "Uygulamaya geç", "Hazırım", or any bypass CTA. Do not show motorcycle/mechanical hero imagery. No bottom navigation. One dominant CTA. No dashboard, KPI, card stack, shield/check certification badge, confetti, AI sparkle, invented technical codes/values/part numbers/prices. Do not reuse or invent the blue K-like logo from supporting references. Working reference, not production-final UI.
```

