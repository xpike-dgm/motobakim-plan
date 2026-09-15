# DESIGN PRINCIPLES

Status: REVIEW
Scope: Phase-3 screen/state architecture candidate
Source: approved Phase-2 product truth + approved L05A/U04/V10 references + screen-inventory QA

Bu ilkeler screen-level design principles adaylaridir. Final component system, exact visual tokens veya implementation kararları değildir. Explicit user approval olmadan APPROVED/LOCKED olmaz.

## DP-01 — Context Determines Prominence

Safety, trust, evidence, recovery ve progress her zaman erisilebilir kalir; fakat prominence current consequence/task'e gore degisir. Her semantic ayni anda buyuk ayri panel olmak zorunda degildir.

## DP-02 — Information Access != Application Authorization

Kavriva ayni anda:
- `bunu okuyabilirsin/ogrenebilirsin`,
- `bunu su anda bu motosiklete uygulayamazsin`

diyebilmelidir.

Teaching-only, stale content ve readiness hold bu ayrimi korur.

## DP-03 — Gates Close Actions, Not Historical Truth

Inactive motorcycle, downgrade veya entitlement limitation new activity'yi kisitlayabilir; history, provenance, corrections, dispute context, critical safety reach-back, user export ve started-work safe recovery'yi degraded/disabled gostermemelidir.

## DP-04 — Every Stop Explains Re-entry

Safety/readiness/mismatch stop'u sunlari gostermelidir:
1. ne blokluyor,
2. neden onemli,
3. hangi evidence/condition degistirebilir,
4. su anda ne yapilabilir,
5. nasil geri donulur.

Dead-end error yeterli degildir.

## DP-05 — Physical State Outranks Route Continuity

Interruption veya guide change sonrasinda `UI'da nerede kalindi` yerine `motosiklet simdi hangi fiziksel durumda` daha onemlidir. Resume = last visible step'e donmek degil, current safe reality'yi yeniden kurmaktir.

## DP-06 — Trust Depth Is Risk-Adaptive

Low-risk context concise trust label + on-demand provenance kullanabilir. High-risk/disputed context claim, motorcycle applicability, source/evidence, review state ve unresolved uncertainty'yi daha explicit gostermelidir.

## DP-07 — Current Claim State Leads; Event History Explains

Historical record ilk bakista current usable trust meaning'i okunabilir yapmali; correction/dispute/withdrawal/supersession history deeper detail'de current state'in nasil olustugunu gostermelidir.

## DP-08 — Active Application Keeps One Dominant Physical Objective

`SCR-014 Active Guide Step` icin U04 principle authoritative'dir:
- Ne yapacagim?
- Nereye bakacagim?
- Bitirince neye basacagim?

Diger semantics consequence gerektirmedikce primary physical action ile rekabet etmez.

## DP-09 — Recovery Is Visible Before Entry, Detailed After Entry

Normal application calm `Sorun var` affordance'i tasir. Detailed recovery content normal task alanini permanent kaplamaz; entry sonrasi prominence kazanir.

## DP-10 — Critical Corrections Override Routine Hierarchy

Previously applied safety-critical guidance'i etkileyen correction normal maintenance reminder gibi sunulamaz. Prominence impact + prior user interaction depth'e gore artar.

## DP-11 — Attribution Is Record Meaning, Not Decoration

Shared/service/transferred/community contexts `kim neyi hangi evidence/status ile ekledi` bilgisini record meaning'in parcasi olarak korur.

## DP-12 — Destructive / Trust-Changing Actions Show Scope First

Transfer, delete, evidence withdrawal ve profile migration gibi lifecycle/trust-changing actions consequence/scope'u confirmation'dan once gostermelidir.

## DP-13 — Uncertainty Is a Product State

`Unresolved`, `insufficient evidence`, `disputed`, `teaching-only`, `cannot safely map current state` durumlari gizlenecek UX hatalari degil legitimate product states'tir.

## DP-14 — Brand Supports Technical Comprehension

L05A/V10 precision character identity saglar; fiziksel instruction, safety meaning veya provenance'in onune gecmez. V10 layout'u universal template degildir.

## DP-15 — Community Content Must Stay Semantically Separate

Published community Q&A/experience, official numbered guide adimlariyla ayni authority treatment'ini kullanamaz. Source/motorcycle/review status/date ve unverified status gerektiğinde anlasilir olmali; user community content'i official instruction sanmamalidir.

## DP-16 — Do Not Invent a Settings Megascreen by Convention

Notification control, language/units ve accessibility preference placement'i source ve screen-family needs'e gore tasarlanmalidir. `Normal app'te settings olur` gerekcesi tek basina new screen authority degildir.

## Known Visual Constraints

- Shield/check mark generic verified/safe/certified badge olarak kullanilmaz.
- Trust/provenance ve safety/attention icon semantics ayrilir.
- V10 handoff HEX values final token degildir.
- Generated mechanical photo verified motorcycle-specific evidence degildir.
- U04 only anchor/task hierarchy authority'dir; History/Transfer/Migration/Collaboration gibi screens farkli structures gerektirebilir.

## Approval Boundary

Status `REVIEW`. These principles may inform the next specification proposal only after explicit user approval of the screen inventory architecture.
