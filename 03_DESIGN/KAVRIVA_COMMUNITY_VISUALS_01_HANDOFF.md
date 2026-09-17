# PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / COMMUNITY VISUALS 01

## A. Source check

**Current phase:** Phase 3 — Design

**Current family:** FAM-09 — Community

**Authority status:** This handoff is for the controlled visual-reference step only. It does **not** write to repository source-of-truth and does **not** declare Gate 3 -> 4 passed.

### Confirmed upstream authorities used

- **Brand:** Kavriva — APPROVED 
- **Logo direction:** L05A — APPROVED working direction 
- **Anchor visual direction:** V10 — APPROVED working direction 
- **Global navigation:** Garaj · Bakım · AI Usta · Geçmiş · Topluluk — APPROVED 
- **Root community screen authority:** `R05 — Topluluk` already exists and was preserved 
- **History / trust reference used for moderation semantics:** `I04 — Correction / Dispute / Evidence Review` 

### This handoff covers

- **L01 — SCR-035 / Community Contribution** 
- **L02 — SCR-036 / Contribution Review / Moderation / Appeal** 

### This handoff does not cover

-  R05 root redesign 
-  Internal data/content operations 
-  Technology / backend / moderation system architecture 
-  Final production tokens / components / routing / backend behavior 

---

## B. Attached reference check

### Required references provided

1. **`Kavriva_L05A.png`**
    Role: working brand / logo-direction anchor 
2. **Selected V10 screenshot**
    Role: visual DNA anchor for near-white canvas, navy/graphite typography, restrained blue accent, readable hierarchy, moderate rounding 
3. **`R05-Topluluk.png`**
    Role: working root authority for community reading/discovery surface 
4. **`I04-SCR-028-Correction-Dispute-Evidence-Review.png`**
    Role: dispute/review/reason/explanation behavior reference 

### Newly accepted outputs

5. **L01 — Community Contribution**
    File: `kavriva_toplulukta_paylaşım_ekranı.png` 
6. **L02 — Contribution Review / Moderation / Appeal**
    File: `kavriva_katkı_i_nceleme_ekranı.png` 

---

## C. User feedback verbatim

### Refinement feedback

> onaylandı fotoğrafları tek tek üretmen lazım ama tek fotoğrafta iki sayfa olarak değil

### Approval to proceed with handoff

> handoff oluşturabilirsin onay verildi

### Interpreted meaning

**CONFIRMED:**

-  Community visual direction is accepted. 
-  User wanted the outputs as **separate individual screens**, not two pages inside one image. 
-  Final accepted set is the separated L01 and L02 screens. 

---

## D. Existing R05 + accepted/refined L01–L02 set

## Working family set

### R05 — SCR-038 / Community Experiences / Q&A

**Existing authority preserved.**

Purpose:

-  read / discover community experiences and Q&A 
-  community root remains distinct from official guide authority 
-  searchable, simple, not an infinite social feed 

### L01 — SCR-035 / Community Contribution

**Accepted final direction.**

**Primary job:**

A user intentionally turns a private/personal experience into a community contribution.

**Accepted working traits**

-  clear title and focused single-job layout 
-  community contribution is explicitly labeled as **community content** 
-  visible explanatory note that contribution does **not** replace official Kavriva guidance 
-  simple text-entry area for what happened / what the user wants to share 
-  optional photo area 
-  explicit distinction between: 
  - **what will be shared** 
  - **what stays private** 
-  one dominant CTA: 
  - **Toplulukla paylaş** 
-  lower-emphasis secondary action: 
  - **Vazgeç** 

**Important semantic success**

-  sharing is opt-in 
-  added photos help explain experience but are not shown as technical verification 
-  private notes / private information are not silently published 

---

### L02 — SCR-036 / Contribution Review / Moderation / Appeal

**Accepted final direction.**

**Primary job:**

User understands why a contribution is not currently publishable and what can be done next.

**Accepted illustrative state**

- **Düzeltme gerekiyor** 
-  contribution is **not currently published** 
-  reason is concise and visible 
-  user gets a repair path rather than an opaque rejection wall 

**Accepted working traits**

-  visible moderation status without alarm-wall intensity 
-  short, understandable explanation of the issue 
-  specific human-readable correction list 
-  clear next-step actions: 
  - **Düzenle ve yeniden gönder** (dominant) 
  - **İtiraz et** 
  - **Katkıyı geri çek** 
-  reminder that publication does **not** mean official Kavriva verification 

**Important semantic success**

-  moderation status is understandable in a few seconds 
-  repair / resubmit path is clear 
-  appeal and withdrawal are available without implying silent erasure of history 

---

## E. Community-vs-official authority separation

This family preserves the required authority boundary.

### Preserved rules

-  Community content is visibly separate from official Kavriva guidance. 
-  Community content does **not** appear as numbered official repair steps. 
-  Publication / acceptance does **not** mean: 
  -  technical verification 
  -  official approval 
  -  guaranteed correctness 

### In L01

This is enforced by the explicit message:

-  “Bu bir topluluk deneyimidir.” 
-  shared content does not replace official Kavriva guides or approved technical steps 

### In L02

This is reinforced by the reminder block:

-  publication in the community does not mean the content is an official or approved technical instruction 

### Result

**CONFIRMED outcome:**

The set visually protects users from mistaking personal experience for official repair authority.

---

## F. Contribution opt-in / private-content behavior

### Preserved behavior

-  Community sharing is a deliberate user action. 
-  Private/personal content is **not** silently converted into public community content. 
-  User understands scope before sharing. 

### L01 behavior model

The screen explains:

-  what is being shared publicly 
-  what remains private 

This is the correct direction for:

-  personal notes staying private 
-  community contribution requiring explicit publish intent 
-  optional media attachment not automatically becoming “verified evidence” 

### Important preserved product meaning

-  attachment ≠ verification 
-  sharing ≠ official guide contribution 
-  personal/private content remains separable 

---

## G. Moderation / revise / resubmit / appeal / withdraw behavior

### Preserved moderation behavior

The accepted L02 reflects the approved product rules:

1. **Reason is shown** 
2. **Repair path exists** 
3. **Resubmission path exists** 
4. **Appeal path exists where supported** 
5. **Withdrawal path exists where allowed** 

### Accepted action hierarchy

- **Primary:** Düzenle ve yeniden gönder 
- **Secondary:** İtiraz et 
- **Secondary:** Katkıyı geri çek 

### Preserved meaning

-  Moderation is not a technical-truth score. 
-  Rejection / hold does not become a dead end. 
-  User can act on the decision. 
-  Withdrawal is available without implying that dependent provenance/history silently disappears. 

### Conceptual trace preservation

A full technical event log wall was intentionally avoided, but the screen still preserves the concept that:

-  there was a submission 
-  it was reviewed 
-  it needs correction 
-  further action is available 

This is aligned with the family goal and clutter constraints.

---

## H. Provenance / trust semantic QA

### QA result: PASS

### What was preserved correctly

-  community status is separate from official guidance 
-  moderation state is separate from technical verification 
-  uploaded photos are not presented as proof of correctness 
-  contribution status is understandable without fake confidence/ranking 
-  no creator reputation / likes / follower / marketplace mechanics were introduced 

### What was intentionally avoided

-  no “verified creator” badge 
-  no community popularity score 
-  no engagement counters 
-  no feed-rank semantics 
-  no fake moderator identity 
-  no invented SLA / review timer 
-  no permanent reputation system 

### Trust-language quality

The accepted screens support:

-  understandable contribution provenance 
-  understandable moderation state 
-  clear non-equivalence between publication and official verification 

---

## I. Clutter QA

### QA result: PASS

### L01

-  one primary job only: share intentionally 
-  no feed/dashboard composition 
-  no card-per-semantic overload 
-  one dominant CTA 
-  readable text sizing 
-  progressive disclosure used where needed 

### L02

-  one primary job only: understand review outcome and next step 
-  no alarm-wall composition 
-  moderation reason readable in a few seconds 
-  actions grouped clearly 
-  no unnecessary visual noise 
-  no technical moderation console feel 

### User preference alignment

**CONFIRMED:** previous project feedback strongly preferred:

-  readable text 
-  less clutter 
-  no tiny/minimal text that hurts comprehension 

Accepted L01–L02 are consistent with that preference.

---

## J. Accessibility notes

### Positive alignment

-  high contrast dark text on light canvas 
-  restrained use of blue accent for action and emphasis 
-  amber reserved for meaningful review/attention state 
-  readable title hierarchy 
-  actions are clearly separated and finger-sized 
-  screen purpose is easy to identify quickly 

### Notes to preserve downstream

-  icon meaning should not carry the whole semantic load alone 
-  privacy / review / publication distinctions should remain legible in copy, not only color 
-  production implementation should later validate: 
  -  contrast ratios 
  -  dynamic type scaling 
  -  Turkish copy wrap behavior 
  -  touch-target sizing 
  -  screen-reader labels 
  -  focus order 

### Boundary

These visuals are accessibility-aware references, **not** final audited accessibility sign-off.

---

## K. Navigation / surface treatment — PROPOSED ONLY

## Important scope note

These are **PROPOSED ONLY** implications from the visual set, not final route or implementation decisions.

### Proposed entry relationships

- **R05 Topluluk** acts as the root reading/discovery surface 
-  user can move from Topluluk root into: 
  -  contribution flow (`SCR-035`) 
  -  review/moderation state (`SCR-036`) when relevant 

### Proposed surface behavior

- `SCR-035` works well as a **full-screen contribution flow** 
- `SCR-036` works well as a **full-screen status/review screen** for clarity and repairability 

### Proposed back-stack logic

- `SCR-035` can be launched from: 
  -  community root 
  -  a contextual share/contribute action 
- `SCR-036` can be reached from: 
  -  post-submission state 
  -  moderation event / status 
  -  contribution history context 

### Not finalized

-  exact routing 
-  whether any part becomes sheet/modal in certain contexts 
-  notification entry behavior 
-  contribution history indexing 
-  report / moderation escalation mechanics 

---

## L. What remains non-final

The accepted set is a **working visual-reference approval**, not a production lock.

### Still non-final

-  exact production copy 
-  final icon family 
-  final font family / type scale 
-  exact spacing / radii / tokens 
-  dark mode 
-  responsive behavior 
-  exact route structure 
-  final community information architecture 
-  moderation backend/provider/model 
-  reviewer tooling / internal operations 
-  privacy implementation details 
-  contribution storage / provenance data model 
-  appeal workflow mechanics 
-  withdrawal edge-case behavior in implementation 
-  notification cadence / messaging logic 

### Important product boundaries still preserved

-  no social-feed invention 
-  no reputation or ranking model 
-  no community content treated as official guidance 
-  no technology or architecture decisions implied by these visuals 

---

## M. Recommended next critical visual family

### Recommended next family

**FAM-01 — First Use / Motorcycle Context**

### Remaining target screens

- `SCR-001 First-Value Entry` 
- `SCR-002 Add Motorcycle` 
- `SCR-003 Motorcycle Identification & Variant Resolution` 
- `SCR-004 Fit Confirmation / Missing Distinction` 

### Existing authority already available

- `SCR-005 Garaj` is already covered by **R01** 

### Why this is the correct next step

Because after FAM-09, the remaining uncovered mobile critical visual set in Phase 3 is FAM-01. Completing it closes the remaining end-user mobile visual coverage before the required internal operations addendum and Gate 3 readiness review.