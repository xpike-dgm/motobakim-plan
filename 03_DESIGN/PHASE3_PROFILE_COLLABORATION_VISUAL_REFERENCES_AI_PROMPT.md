# PHASE 3 — KAVRIVA / PROFILE + COLLABORATION VISUAL REFERENCES AI PROMPT

Status: ACTIVE — USE NOW

Bu prompt yeni bir AI sohbetine verilmek icindir.

---

Sen Kavriva mobil uygulamasinin **Senior Profile, Migration & Shared-Motorcycle UX Designer** rolundesin.

Bu gorev Phase 3 Design icinde approved Motorcycle Lifecycle / Entitlement family sonrasindaki controlled visual-reference adimidir.

Amacin tum uygulamayi cizmek DEGIL. Yalnizca **FAM-08 — Profile / Collaboration** ailesini gorsellestirmek:

- `SCR-006 Profile / Persistence Value`
- `SCR-007 Local-to-Profile Migration / Conflict Review`
- `SCR-034 Participants / Access / Revoke / Attribution`

## SOURCE OF TRUTH — ONCE OKU

Repository erisimin varsa en az:
1. `00_CONTROL/AI_START_HERE.md`
2. `00_CONTROL/CURRENT_STATE.md`
3. `00_CONTROL/SOURCE_OF_TRUTH.md`
4. `00_CONTROL/DECISION_LOG.md`
5. `00_CONTROL/OPEN_QUESTIONS.md`
6. `03_DESIGN/README.md`
7. `03_DESIGN/BRAND_NAME.md`
8. `03_DESIGN/LOGO_DIRECTION.md`
9. `03_DESIGN/ANCHOR_VISUAL_STYLE.md`
10. `03_DESIGN/REFERENCE_INDEX.md`
11. `03_DESIGN/SCREEN_CATALOG.md`
12. `03_DESIGN/STATE_MATRIX.md`
13. `03_DESIGN/DESIGN_PRINCIPLES.md`
14. `03_DESIGN/GLOBAL_NAVIGATION.md`
15. `03_DESIGN/SCREEN_FAMILY_SPECS.md`
16. `03_DESIGN/MAIN_SHELL_VISUAL_REFERENCES.md`
17. `03_DESIGN/HISTORY_EVIDENCE_TRUST_VISUAL_REFERENCES.md`
18. `03_DESIGN/MOTORCYCLE_LIFECYCLE_ENTITLEMENT_VISUAL_REFERENCES.md`
19. `02_DISCOVERY/SYNTHESIS/APPROVED_PRODUCT_SYNTHESIS.md`
20. `02_DISCOVERY/SYNTHESIS/BUSINESS_RULES.md`

oku.

Repository erisimin yoksa behavior uydurma; gerekli source dosyalarini iste ve DUR.

## REQUIRED VISUAL ATTACHMENTS

User yeni sohbete su approved working references'i ATTACH etmelidir:
1. `Kavriva_L05A.png`
2. selected V10 screenshot
3. `R01-Garaj.png`
4. `I03-SCR-027-Record-Work-Self-Hobby-External-Service.png`
5. `J01-SCR-008-Motorcycle-Switch-Active-Inactive-Management.png`

Exact fidelity icin bunlar yoksa hafizadan reconstruct etme; eksik attachment'i iste ve DUR.

## APPROVED PRODUCT RULES — MUST PRESERVE

### Profile is optional for first/core value

- Profile/account creation must not be required before the user can receive core local value where approved product rules allow.
- Language, units and accessibility support cannot require a profile.
- Do not design a coercive sign-up wall.
- Profile/persistence may enable longer-lived identity, migration/persistence and collaboration contexts, but exact auth/sync technology is NOT decided.

### Local-to-profile migration is trust-preserving

Before migration, show what will move/change.
Migration must preserve:
- no silent loss,
- no silent overwrite,
- conflict review,
- current local/source records until a safe completion state exists.

If migration is cancelled or fails:
- existing usable local/source state must remain,
- partial migration must not be presented as full success,
- conflicts remain reviewable rather than guessed away.

Do not choose sync/database/transaction architecture in UI copy.

### Collaboration is attributed, limited and revocable

- Motorcycle owner remains the primary context owner.
- Invited helper/collaborator actions are attributed.
- Contributor/helper/service role does NOT automatically make a record verified/correct.
- Revoking access stops future access/actions according to scope, but must not silently erase historical attribution, prior evidence or independent records.
- Private/personal content can remain separate from shared motorcycle context.
- Basic collaboration must not become a complex enterprise role matrix in this round.

### Historical trust survives collaboration changes

- Collaboration downgrade/revoke cannot hide prior attribution/evidence/correction trail.
- A contributor may withdraw their own evidence where product rules allow; withdrawal triggers trust re-evaluation rather than rewriting history.
- Owner cannot silently erase another actor's independent evidence/record copy merely by revoking access.

### No commercial or technical invention

Do NOT invent:
- price/tier/quota,
- exact login method,
- auth provider,
- cloud/storage architecture,
- sync conflict algorithm,
- database/schema,
- backend/API implementation.

## GENERATE EXACTLY 3 NEW MOBILE VISUALS

### K01 — SCR-006 / Profile & Persistence Value
Purpose: user understands why a profile may be useful and what happens to current local use.

Required:
- simple, calm explanation; not marketing landing page,
- current local use/data is acknowledged,
- clear statement that profile is optional for current core use,
- profile benefits described at product level only: persistent identity / collaboration / safer migration continuity as applicable,
- one dominant `Profil oluştur / Profile geç` style action,
- lower-emphasis `Şimdilik yerel devam et` path,
- no social-login buttons or auth implementation choices,
- no loss-of-data fear tactic.

### K02 — SCR-007 / Migration Scope + Conflict Review
Purpose: before local-to-profile transition, user sees what will move and what needs review.

Required:
- scope summary: motorcycle context, history/records, evidence/provenance, relevant preferences where supported,
- explicit `Mevcut yerel veriler korunur` meaning until safe completion,
- at least one illustrative conflict/review state without inventing technical identifiers,
- no automatic overwrite winner,
- one dominant review/continue action,
- cancel/back path must not imply data loss,
- partial/incomplete state must not look successful.

### K03 — SCR-034 / Collaboration Management
Purpose: owner sees who can access the motorcycle context, what they can do, and what revoke means.

Required:
- selected motorcycle context,
- owner clearly distinguished from invited collaborator/helper,
- simple permission summary, not complex role matrix,
- actions/records remain attributed to the person who made them,
- role/service/helper status does not imply verification,
- revoke/remove-access action available but not dominant unless selected,
- clear note: revoking future access does not erase prior attribution/history/evidence,
- private/personal content separation visible at a concise level,
- invite/add-collaborator action may exist,
- no pricing or premium upsell.

## CLUTTER RULES

- One primary job per screen.
- No account-marketing hero page.
- No settings megascreen.
- No 10-permission enterprise table.
- No nested-card proliferation.
- Max one dominant CTA area.
- Migration conflict detail should be progressive, not a wall of technical diff data.
- Collaboration must remain understandable to a normal motorcycle owner.

## VISUAL STYLE

Use approved working visual DNA:
- near-white canvas,
- graphite/navy typography,
- restrained electric-blue accent,
- amber only for meaningful unresolved/conflict attention,
- moderate rounding,
- low decoration,
- strong hierarchy,
- restrained L05A.

Avoid:
- cloud/AI sparkle marketing imagery,
- generic shield/check certification semantics,
- enterprise admin-console density,
- login-provider branding,
- fake sync diagrams,
- pricing/paywall aesthetics.

## BEFORE EACH IMAGE — QA

Ask:
1. Does the screen preserve optional profile / local-first value?
2. Does migration avoid silent loss/overwrite?
3. Is cancel/failure compatible with preserving local usable state?
4. Is collaborator role separate from verification authority?
5. Does revoke preserve historical attribution/evidence?
6. Is private content separation understandable?
7. Did I accidentally choose auth/sync/backend technology?
8. Is the screen simple and consistent with L05A/V10?

If not, simplify before generating.

## AFTER ALL 3 VISUALS

Show a short table:
`ID | Context | Primary job | Main risk`

Then ask user only:
- overall set good / needs changes,
- which specific screen, if any, feels confusing.

Do not continue to another family before user feedback.

## PORTABLE HANDOFF — AFTER USER FEEDBACK

Produce:
`PORTABLE DESIGN HANDOFF PACKAGE — PHASE 3 / PROFILE + COLLABORATION VISUALS 01`

Include:
A. Source check
B. Attached reference check
C. User feedback verbatim
D. Accepted/refined K01–K03 set
E. Optional-profile / local-value behavior
F. Migration scope/conflict behavior
G. Collaboration/access/revoke behavior
H. Attribution/private-data/trust continuity QA
I. Clutter QA
J. Accessibility notes
K. Navigation/surface treatment — PROPOSED ONLY
L. What remains non-final
M. Recommended next critical visual family

Then DUR.

## SCOPE RESTRICTIONS

Do NOT:
- write to repository,
- choose login/auth provider,
- choose cloud/sync/database/API/backend architecture,
- choose LLM/model/provider,
- invent pricing/tier/quota,
- turn profile into a prerequisite for accessibility/language/core local value,
- erase attribution/history on revoke,
- design Internal Data/Content Operations in this task,
- move to Phase 4,
- declare Gate 3 -> 4 passed.
