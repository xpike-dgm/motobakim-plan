# KAVRIVA SCREEN FAMILY + SPECIFICATIONS

Status: APPROVED WORKING SPECS
Approved by controlled main-manager integration after USER navigation decision — 2026-09-15
Decision: DEC-0017; AI Usta root refinement: DEC-0018
Review: `SCREEN_FAMILY_SPEC_REVIEW.md`
Source package: `PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / SCREEN FAMILY + SPECS 01`

## Approval Semantics

Bu belge approved `SCR-001` — `SCR-038` screen architecture'ini screen families ve UX specifications seviyesinde rafine eder.

Approval:
- family grouping'i,
- per-context primary user job / hierarchy / safety-trust behavior'i,
- default simplicity rules'ini,
- cross-family consistency'yi
working Phase-3 authority yapar.

Approval su konulari final yapmaz:
- exact full-screen/sheet/modal/inline mapping,
- production components/tokens,
- AI Usta A1 root disindaki optional conversational capability'ler,
- pricing/technology/backend/AI implementation,
- Gate 3 -> 4.

## Main-Manager Refinement

Language/unit preferences ve accessibility support profile/account prerequisite olamaz. Account-light/local use bu presentation/accessibility behavior'larindan yararlanabilmelidir. Profile varsa persistence saglayabilir; access prerequisite olamaz.

Global navigation authority: `GLOBAL_NAVIGATION.md`.
AI Usta root authority: `AI_USTA_UX_STRUCTURE.md` / `REF-AIUSTA-001`.

## Screen Families

| Family | Name | Included SCR IDs | Core user job |
|---|---|---|---|
| `FAM-01` | First Use / Motorcycle Context | `001-005` | Intent ve dogru motorcycle context'i kurmak |
| `FAM-02` | Guide Discovery / Fit / Preparation | `009-013` | Dogru isi/rehberi bulmak ve uygulamaya hazirligi kurmak |
| `FAM-03` | Active Application / Safety / Recovery | `014-018` | Gercek motosiklette tek physical objective ile guvenli ilerlemek |
| `FAM-04` | Diagnosis | `019-021` | Belirtiden evidence ile supported/unresolved sonuca gitmek |
| `FAM-05` | Maintenance / Reminder | `022-024` | Due/upcoming/uncertain bakimi anlamak ve onceliklendirmek |
| `FAM-06` | History / Evidence / Trust | `025-030` | Gecmisi, claim state'i, provenance'i ve correction/dispute'i anlamak |
| `FAM-07` | Motorcycle Lifecycle / Entitlement | `008,031-033,037` | Active/inactive/archive/transfer/delete ve new-activity access sinirlarini yonetmek |
| `FAM-08` | Profile / Collaboration | `006,007,034` | Persistence/migration ve attributed collaboration'i yonetmek |
| `FAM-09` | Community | `035,036,038` | Community experience'i official guide'dan ayri okumak/paylasmak |

## Family-Level Principles

### FAM-01
Intent + motorcycle context first. Profile veya advanced features first value'in onune gecmez. Unresolved fit varsa application authority implied edilmez.

### FAM-02
Ana soru: **Bu dogru is/rehber mi ve bunu simdi uygulayabilir miyim?** Fit/readiness/freshness application'dan once gelir. Stop her zaman reason + remediation + recheck tasir.

### FAM-03
Tek baskin physical objective. `SCR-014` icin U04 DIRECT authority'dir. Safety consequence gerektiginde normal hierarchy'yi devralabilir. Recovery visible secondary entry'dir; detailed recovery normal ekrani permanent kaplamaz.

### FAM-04
Symptom -> evidence -> supported result veya explicit unresolved. Random replacement / false certainty yok.

### FAM-05
Once gercekten gerekli/urgent olan, sonra routine detail. Invented maintenance interval yok. Critical correction routine reminder gibi gosterilmez.

### FAM-06
Once current usable claim meaning; sonra provenance/event history. Silent overwrite yok. Risk arttikca trust detail daha explicit olur.

### FAM-07
Once action consequence/scope; sonra confirmation. Archive != delete, transfer != delete, inactive != history lock. Entitlement gates action/capacity, not truth/safety/recovery.

### FAM-08
Ne degisecek / kim neye erisecek once aciklanir. Migration failure local usable state'i yok etmez. Contributor role verification authority yaratmaz.

### FAM-09
Community authority ilk bakista official guide'dan ayri okunur. Unverified experience official numbered step olamaz. Permanent social-feed mechanics bu spec'in parcasi degildir.

## Per-Screen Working Specifications

| SCR | Family | Primary user job / default focus | Working surface status | Primary action / key rule |
|---|---|---|---|---|
| `001` | FAM-01 | Known-task / symptom / record-first baslangic intent'i secmek | Full screen working candidate | Intent ile devam; profile/promo ikinci seviye |
| `002` | FAM-01 | Motorcycle temel context'ini eklemek | Full screen working candidate | Devam; user-entered identity verified variant degil |
| `003` | FAM-01 | Observable evidence ile relevant variant'i ayirmak | Full screen working candidate | Evidence sagla; uncertainty false certainty'ye cevrilmez |
| `004` | FAM-01 | Fit yeterli mi / ne eksik anlamak | Surface modality PROPOSED | Resolve fit veya teaching-only; unresolved fit application acmaz |
| `005` | FAM-01 | Selected motorcycle context'ini anlamak | Root/context surface | Global nav sonrasinda Garaj responsibility ile uyumlu; dashboard/KPI/card-stack olamaz |
| `006` | FAM-08 | Profile/persistence nedenini ve local data etkisini anlamak | Sheet/modal PROPOSED | Continue veya local kal; coercive account gating yok |
| `007` | FAM-08 | Migration scope/conflict review | Full screen working candidate | Review/complete; no silent loss/overwrite |
| `008` | FAM-07 | Active/inactive motorcycle secmek | Switch surface PROPOSED | Switch/select; inactive history korunur |
| `009` | FAM-02 | Known task'i plain language ile bulmak | Full screen working candidate | Task sec; selection fit authority degil |
| `010` | FAM-02 | Guide scope/fit/freshness/application statusunu anlamak | Full screen working candidate | Preparation'a gec veya fit/teaching path |
| `011` | FAM-02 | Tools/parts/risks/prerequisites hazir mi anlamak | Full screen working candidate | Ready ise basla; mandatory vs optional clear |
| `012` | FAM-02 | Readiness hold nedenini cozmeye odaklanmak | Contextual hold PROPOSED | Remediate + recheck; assertion critical gate'i acmaz |
| `013` | FAM-02 | Application kapaliyken teaching/reference okumak | Full content working candidate | Learn / revalidation; active-instruction gibi gorunmez |
| `014` | FAM-03 | Tek physical step'i uygulamak | Full screen; U04 DIRECT | Step completion; critical safety visible; `Sorun var` secondary |
| `015` | FAM-03 | Unexpected/mismatch durumda safe state kurmak | Recovery surface PROPOSED | Re-establish/recheck; ignore-and-continue yok |
| `016` | FAM-03 | Interruption sonrasi current physical state'i revalidate etmek | Full screen working candidate | Recheck; saved UI progress current proof degil |
| `017` | FAM-03 | Material guide change sonrasi physical state'i remap etmek | Full screen exceptional flow | Map/revalidate; guessed continuation/reversal yok |
| `018` | FAM-03 | Completed vs partial/unresolved/safe closure sonucunu belirlemek | Full screen outcome boundary | Confirm actual outcome; safe closure paywall olamaz |
| `019` | FAM-04 | Belirtiyi technical term gerektirmeden anlatmak | Full screen working candidate | Evidence ile devam; danger first |
| `020` | FAM-04 | Tek ayirici diagnostic check yapmak | Sequential full screen | Check result; full tree simultaneously visible degil |
| `021` | FAM-04 | Supported veya unresolved sonucu anlamak | Full screen result | Supported repair -> guide preview; unsupported repair uydurulmaz |
| `022` | FAM-05 | Due/upcoming/uncertain maintenance'i gormek | Full screen / Bakim root | Maintenance item ac; generic score/charts yok |
| `023` | FAM-05 | Bir reminder'in neden geldiğini ve ne yapilacagini anlamak | Detail surface PROPOSED | Perform/record/snooze where allowed; postpone != completion |
| `024` | FAM-05 | Long absence backlog'i safety-first siralamak | Full screen summary | Highest priority action; notification flood yok |
| `025` | FAM-06 | Longitudinal history'yi gezmek/aramak | Full screen / Gecmis root | Record detail; KPI analytics default degil |
| `026` | FAM-06 | Bir record'un bugunku claim/trust meaning'ini anlamak | Full screen detail | Review/correct; event history progressive |
| `027` | FAM-06 | Guided flow disi self/hobby/service work kaydetmek | Full screen record flow | Save actual outcome; actor role verification yaratmaz |
| `028` | FAM-06 | Competing claims/evidence'i review etmek | Review flow PROPOSED | Correct/review/withdraw; silent winner yok |
| `029` | FAM-06 | Critical historical correction'in user'a etkisini anlamak | Dedicated action context | Required recheck/remap; routine UI'dan daha prominent olabilir |
| `030` | FAM-06 | Export scope/provenance'i anlamak | Export surface PROPOSED | Export; basic data portability premium degil |
| `031` | FAM-07 | Archive/reactivate/transfer/delete farkini anlamak | Full screen lifecycle | Selected action; destructive actions separated |
| `032` | FAM-07 | Transfer scope/coverage/gaps'i review etmek | Full screen scoped flow | Confirm/revise scope; partial != complete history |
| `033` | FAM-07 | Delete scope/irreversibility'i anlamak | Blocking confirmation PROPOSED | Confirm/cancel; independent data boundary explicit |
| `034` | FAM-08 | Participants/access/revoke/attribution'i yonetmek | Full screen collaboration | Invite/manage/revoke; revoke past attribution'i silmez |
| `035` | FAM-09 | Private content'ten explicit community contribution yapmak | Full screen contribution flow | Submit/revise; sharing opt-in |
| `036` | FAM-09 | Moderation status/reason/repair path'i anlamak | Status/modal-flow PROPOSED | Repair/resubmit/appeal/withdraw; acceptance != official verification |
| `037` | FAM-07 | New activity neden gated / neyin korunmus oldugunu anlamak | Contextual state family PROPOSED | Resolve new activity or return preserved access; permanent paywall route degil |
| `038` | FAM-09 | Community experiences/Q&A okumak | Topluluk root / list+detail family | Read/contribute/report; official guide appearance taklit edilmez |

## Global Navigation Refinement

User-approved 5-tab shell:
**Garaj · Bakim · AI Usta · Gecmis · Topluluk**.

Detailed authority: `GLOBAL_NAVIGATION.md`.

### Controlled refinement of SCR-005

`SCR-005` approved architecture'de task/symptom/maintenance/history/lifecycle entry hub olarak tanimlanmisti. 5-tab navigation selection sonrasinda controlled refinement:
- `SCR-005` Garaj / selected-motorcycle context responsibility'sine daralir,
- known-task + symptom primary entry `AI Usta` shell responsibility'sine tasinir,
- maintenance primary entry `Bakim` tab'ina,
- history primary entry `Gecmis` tab'ina,
- community primary entry `Topluluk` tab'ina tasinir,
- lifecycle/motorcycle switching Garaj/contextual kalir.

Bu refinement product capability'yi silmez; ayni approved contexts'i daha sade global navigation'a dagitir ve previous dashboard/card-stack riskini azaltir.

## AI Usta Root Refinement — DEC-0018

AI Usta root UX structure separately approved:
**A1 — Guided Split**.

Canonical authority:
- `AI_USTA_UX_STRUCTURE.md`
- `REF-AIUSTA-001`

Root target:
**1 context + 1 prompt + 2 paths.**

- compact selected motorcycle context,
- `Nasil yardimci olayim?`,
- `Bir is yapmak istiyorum` -> `SCR-009`,
- `Motorda bir sorun var` -> `SCR-019`,
- optional low-prominence help,
- fixed five-tab nav.

A1 root free-form technical-answer chat home degildir ve two-intent choices bulky card-stack'e donusturulmez.

## Cross-Cutting Control Placement

Working guidance:
- routine notification mute/snooze: contextual + broader maintenance control if needed,
- language/units: app-level accessible without profile prerequisite,
- accessibility modalities: system-first + app/context affordance; profile prerequisite degil,
- motorcycle switching: Garaj + compact contextual control,
- data export: Gecmis/profile/lifecycle context,
- collaboration: motorcycle/profile context.

Generic Settings megascreen bu spec ile onaylanmis degildir.

## Trust / Safety Semantic Separation

Separate semantics required:
- safety warning/stop,
- trust/provenance,
- evidence level,
- unresolved/uncertain,
- disputed,
- community/unverified,
- completion/safe closure.

Rules:
- shield/check generic verified/safe badge olarak kullanilmaz,
- trust != safety,
- evidence level != current claim state,
- verified != guaranteed success,
- community status official trust treatment'ini taklit etmez,
- color critical meaning'in tek tasiyicisi olamaz.

## Visual Application Boundary

- U04 DIRECT only for `SCR-014`; other contexts use principle-level adaptation where relevant.
- V10 is visual DNA, not universal layout.
- Garaj/Bakim/Gecmis/Topluluk roots can require different density and composition.
- AI Usta root A1 hierarchy fixed by `AI_USTA_UX_STRUCTURE.md`; visual treatment can refine typography/spacing/intent presentation without changing routing/authority.

## Open Design Decisions Carried Forward

Still open for visual-reference / later controlled work:
- exact ambiguous surface modalities,
- active-repair bottom-bar visibility,
- first post-onboarding landing tab,
- optional AI Usta conversational capabilities beyond A1 root,
- exact claim/evidence visual vocabulary,
- final iconography,
- notification preference detail,
- collaboration exact role matrix,
- task-specific safe-closure criteria,
- responsive behavior,
- production fonts/colors/spacing/radii/dark mode/components.
