# BATCH 07 SYNTHESIS DELTA

Status: DRAFT
Evidence: `SESSION-007_BATCH_07_Q186_Q215.md`
Purpose: Batch 07'nin canonical synthesis belgelerine eklenecek degisikliklerini izlenebilir bicimde tutar. Ham evidence yerine gecmez. Batch 08/saturation review sonrasi gerekli maddeler `PRODUCT_MASTER`, `USER_JOURNEYS`, `BUSINESS_RULES`, `FEATURE_CANDIDATES`, `NON_GOALS` ve `GLOSSARY` icine konsolide edilir.

## 1. Confirmed product delta

- Evidence withdrawal independent/transferred historical record'i otomatik silmez; source access, provenance, visibility ve current trust ayri product meanings'dir. Q186-Q188.
- Disputed claim new independent evidence ile yeniden review edilir; prior disagreement silent delete edilmez. Resolution ancak evidence yeterli bulunursa olur; correction/extension relation korunabilir. Q189-Q191.
- Historical claim trust icin az sayida current-state semantics + ayrintili event history tercih edilir. Candidate current meanings: accepted, disputed, insufficient evidence, superseded. Withdrawal/resolution history event'i olabilir. Q192-Q194.
- Material guide change old physical action'i kontrolsuz reverse ettirmez. Current physical state capture/revalidation olmadan physical continuation veya reversal verilmez. Safe mapping yoksa teaching/state capture devam eder, application durur. Q195-Q197.
- Long interruption'da saved confirmations current proof degildir. Parts/connections/stability/energy/pressure/temperature/last-critical-result ve state-drift events yeniden kontrol edilir; `degismedi` user assertion'i critical recheck'i kaldirmaz. Q198-Q200.
- Profile migration cancel/failure local data loss yaratamaz. Partial profile state success gibi sunulmaz; source records transfer verified olana kadar korunur ve rollback/correction silent delete yapmaz. Q201-Q203.
- Correction reach-back interaction depth + risk ile artar. Viewer zayif signal; relevant-step interaction, applied confirmation/evidence ve completion daha guclu affected-user signals'dir. Q204-Q206.
- Beginner/experienced adaptation explanation depth/speed'i degistirebilir fakat high-risk source/fit/uncertainty/conflict/safety ve mandatory checks invariant kalir. Q207-Q209.
- Basic shared-bike trust invitation, limited permission, attribution, revoke, personal-content separation ve history integrity'yi korur. Premium collaboration scale/coordination uzerinden ayrisabilir. Q210-Q215.
- Advanced garage value: bulk planning, cross-bike comparison, advanced archive search, richer permissions/roles/coordination. Q211-Q215.

## 2. Monetization proposal — PROPOSED, NOT APPROVED

Batch 07 supplemental user note:

`Free: 1 active motorcycle + 1 invitee + basic history/warnings + user-selected 1 full guide. Additional motorcycles/guides paid; existing records are not locked.`

Bu, kullanicinin guncel **proposal**'idir; APPROVED/LOCKED policy degildir.

Quality-control interpretation:
- Motorcycle isolation/history integrity bir correctness/trust invariant'i olarak kalir.
- Simultaneous active-motorcycle entitlement ayri commercial question'dir.
- One full guide'in safe end-to-end completion'i core-completion principle ile uyumlu olabilir, ancak guide switching/historical/safety access henuz aciktir.
- Existing records'in retroactive kilitlenmemesi guclu trust boundary'dir; read/write/correction/resume detaylari aciktir.
- Potential tensions `02_DISCOVERY/CONFLICTS.md` icinde CONF-001/CONF-002 olarak izlenir.

## 3. Business-rule additions — candidate merge

| Delta ID | Candidate Rule | Evidence |
|---|---|---|
| D07-BR-01 | Contributor evidence withdrawal independent/transferred record'i otomatik silemez; withdrawn source evaluation'dan cikarilir ve claim remaining evidence ile yeniden review edilir. | Q186-Q188 |
| D07-BR-02 | Source access, provenance history, evidence visibility ve current trust status birbirine es anlamli degildir. | Q187 |
| D07-BR-03 | Dispute new evidence geldi diye otomatik resolved olmaz; evidence review edilip yeterli bulunmali, prior dispute/history korunmalidir. | Q189-Q191 |
| D07-BR-04 | Historical claim current state ile event history ayrilmalidir; event gecmisi current trust anlamini sessizce overwrite etmemelidir. | Q192-Q194 |
| D07-BR-05 | Material guide change'de old physical action automatic reversal yapilamaz; current state verify edilmeden physical next/reverse step verilmez. | Q195-Q197 |
| D07-BR-06 | Long interruption sonrasi critical physical/safety confirmations automatic carry-forward edilemez; relevant current state yeniden kontrol edilmelidir. | Q198-Q200 |
| D07-BR-07 | Profile migration cancel/failure local source data'yi kaybetmemeli; partial transfer success gibi sunulmamali ve rollback non-destructive olmalidir. | Q201-Q203 |
| D07-BR-08 | Correction reach-back severity user interaction depth + correction risk ile orantilanmalidir. | Q204-Q206 |
| D07-BR-09 | Experience adaptation trust-critical source/fit/uncertainty/conflict/safety facts'i veya mandatory checks'i gizleyemez. | Q207-Q209 |
| D07-BR-10 | Basic collaboration trust controls payment statusuna baglanmamali; premium value scale/roles/tasks/approvals/bulk coordination'da baslamalidir. | Q210-Q215 |
| D07-BR-11 | Erisilebilir existing record icin attribution/provenance/withdrawal-impact/safety trust bilgisi premium'a kapatilamaz. | Q212, Q214-Q215 |

## 4. Journey additions — candidate merge

### D07-J1 — Withdraw evidence -> re-evaluate dependent claim
1. Contributor source evidence'i geri ceker.
2. Independent/transferred record automatic silinmez.
3. Withdrawal provenance/event history'ye islenir.
4. Withdrawn evidence current evaluation'dan cikarilir.
5. Remaining evidence claim'i yeniden support edip etmedigi review edilir.
6. Current trust state update edilir; history preserved kalir.

### D07-J2 — New evidence -> resolve or refine disputed history
1. Disputed claim'e new independent evidence gelir.
2. Evidence'in hangi claim'i destekledigi ve remaining uncertainty gorulur.
3. Review yeterliyse current claim state degisebilir.
4. Prior disagreement/resolution reason event history'de kalir.
5. New claim correction veya extension olarak prior claim'e baglanabilir.

### D07-J3 — Material guide change after physical action
1. Current work durur.
2. Changed step/risk aciklanir.
3. Current physical state capture/revalidate edilir.
4. Safe mapping/recovery path varsa ilerlenir.
5. Mapping yoksa application physical action tahmin etmez; teaching/state capture devam eder.

### D07-J4 — Long interruption -> state-drift revalidation
1. Saved context acilir.
2. Potential state-drift events kontrol edilir.
3. Critical current facts revalidate edilir.
4. User `degismedi` beyanı tek basina yeterli sayilmaz.
5. Current safe state establish edilirse resume edilir; aksi halde application durur.

### D07-J5 — Profile migration cancel/failure
1. Migration baslar.
2. Partial/local/profile states explicit izlenir.
3. Cancel/failure olursa local source data usable kalir.
4. Partial profile records completed migration gibi sunulmaz.
5. Conflict old/new comparison + non-destructive rollback/correction ile yonetilir.

### D07-J6 — Correction reach-back by impact depth
1. Correction/withdrawal severity belirlenir.
2. User interaction depth belirlenir.
3. Viewer update-info seviyesinde kalabilir.
4. Relevant-step/active-work user prominent warning + recheck alir.
5. Completed-work user retrospective impact + result recheck guidance alir.

## 5. Feature-candidate additions — candidate merge

- `Historical claim current-state + event-history view`
- `Independent evidence withdrawal + trust re-evaluation`
- `Dispute resolution / correction-extension linkage`
- `Physical-state recovery after material guide change`
- `State-drift resume checklist`
- `Migration partial-state / rollback transparency`
- `Risk + interaction-depth correction reach-back`
- `Experience-adaptive trust explanation with invariant critical facts`
- `Basic shared-bike trust package`
- `Advanced coordination / advanced garage package candidate`
- `Entitlement-safe existing-record access`

## 6. Non-goal additions — candidate merge

- Independent/transferred history'yi source withdrawal nedeniyle sessizce silmek.
- New evidence geldigi icin prior dispute'i history'den yok etmek.
- Material guide change'de current physical state'i verify etmeden nearest-step/automatic reversal tahmin etmek.
- Long interruption'da old confirmations'i current safety proof saymak.
- Migration partial/failure state'ini basarili migration gibi sunmak veya local source data'yi sessizce kaybetmek.
- Experienced user mode'da trust-critical source/fit/uncertainty/safety facts'i gizlemek.
- Attribution/revoke/history-integrity gibi basic trust controls'u premium kolaylik gibi kilitlemek.
- Entitlement downgrade ile existing history/provenance/safety trust bilgisini retroactive kilitlemek.

## 7. Glossary candidates — PROPOSED

| Term | Proposed meaning |
|---|---|
| Current Claim State | Bir historical claim icin bugun hangi bilgiye ne olcude dayanilabilecegini anlatan mevcut trust durumu. |
| Claim Event History | Dispute, withdrawal, correction, resolution ve supersession gibi claim'in bugunku duruma nasil geldigini gosteren tarihce. |
| Evidence Withdrawal | Contributor'in evidence paylasimini/availability'sini sona erdirmesi; past provenance'i automatic silmeyen ve dependent trust re-review tetikleyen event. |
| Independent Evidence Continuity | Bir source evidence withdrawn olsa bile remaining independent evidence yeterliyse claim/history'nin review sonrasi yasayabilmesi. |
| Superseded Claim | Daha yeni/daha dogru bilgi nedeniyle current primary reference olmayan fakat history'de korunan eski claim. |
| Physical-State Recovery | Material guide change veya interruption sonrasinda physical action'dan once current motorcycle state'i yeniden belirleme sureci. |
| State Drift | Saved repair context ile current physical reality arasinda intervention/movement/missing parts/energy/temperature/pressure nedeniyle olusabilecek fark. |
| Affected-User Depth | Correction/withdrawal etkisinin user'in view/step/application/evidence/completion seviyesine gore degisen product signal'i. |
| Trust Invariant | Experience/payment status degisse de gizlenmemesi veya zayiflatilmamasi gereken source/fit/uncertainty/safety/attribution/history-integrity bilgisi. |
| Basic Shared-Bike Trust | Owner + invited contributor ortak kaydinda attribution, limited permission, revoke, private-content separation ve history integrity davranislarinin temel paketi. |

## 8. User types delta

Yeni direct user type ortaya cikmadi. Batch 07, mevcut shared-family/helper/multi-bike context'lerinde **entitlement ve trust** ayrimini rafine etti.

## 9. Open entitlement gaps after Batch 07

Aktif source-of-truth: `00_CONTROL/OPEN_QUESTIONS.md` Q-0065 — Q-0069.

- 1 active motorcycle lifecycle
- 1 selected full guide lifecycle
- active repair continuity under entitlement change
- `existing records unlocked` minimum semantics
- inactive/shared collaboration lifecycle

## 10. Saturation signal

Batch 07 intended trust/recovery areasinda HIGH saturation'a ulasti. Yeni substantive gaps esas olarak supplemental monetization proposalindan dogdu. Batch 08 bu entitlement lifecycle'i kapatmaya odaklanmalidir; ayni trust/recovery sorulari farkli kelimelerle tekrar edilmemelidir.
