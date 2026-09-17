# KAVRIVA PROFILE + COLLABORATION VISUAL REFERENCES

Status: `APPROVED WORKING REFERENCE — WITH CONSTRAINTS`
Date: 2026-09-17
Family: FAM-08 — Profile / Collaboration
Coverage: SCR-006, SCR-007, SCR-034
Reference ID: `REF-PROFILE-001`

## Authority

This file is the canonical working visual-reference authority for FAM-08.

Evidence / handoff:
- `03_DESIGN/KAVRIVA_PROFILE_COLLABORATION_VISUALS_01_HANDOFF.md`

Main-manager QA:
- `03_DESIGN/KAVRIVA_PROFILE_COLLABORATION_VISUALS_REVIEW.md`

Approved upstream authorities remain:
- L05A / `REF-BRAND-001`
- V10 / `REF-VISUAL-001`
- screen/state architecture / `REF-ARCH-001`
- screen-family specs / `REF-SPEC-001`
- lifecycle/history visual families where applicable

## Accepted Set

### K01 — SCR-006 Profile / Persistence Value

Working intent:
- profile is optional, not a coercive sign-up wall,
- current local/core use remains available,
- profile value is framed around persistence/continuity and collaboration at product level,
- one dominant `Profil oluştur` action,
- clear lower-emphasis `Şimdilik yerel devam et` path,
- user-requested simplification removed hero imagery and unnecessary upper explanatory blocks.

Visual QA result: `PASS_WITH_COPY_AND_ICON_CONSTRAINTS`.

Required constraints:
- the literal generated phrases `Verilerini güvenle sakla` and `hiçbir şey kaybolmaz` are NOT production claims; final copy must express no-silent-loss + local-state preservation during safe migration without implying absolute security or zero-loss guarantee,
- shield/check artwork is NOT approved as a generic trust/security/certification semantic,
- the rendered device-frame presentation is a mockup artifact, not required production screen chrome,
- readable proportional typography and calm density are part of the accepted direction.

### K02 — SCR-007 Local-to-Profile Migration / Conflict Review

Working intent:
- user sees transfer scope before proceeding,
- migration is not shown as ready while a conflict still needs review,
- local usable/source data remains preserved until safe completion,
- conflicting records remain separate and no automatic overwrite winner is selected,
- cancel/back is non-destructive,
- primary action is review/continue, not blind migration.

Visual QA result: `PASS_WITH_RESTRAINT`.

Required constraints:
- do not expand this into a technical sync diff wall,
- partial/failure state must never look like completed migration,
- exact sync/conflict algorithm remains outside Phase-3 authority.

### K03 — SCR-034 Collaboration & Permissions

Working intent:
- owner is visually distinct from invited helper/collaborator,
- collaborator access is limited and understandable,
- actions remain attributed to the actor,
- helper/service role does not create verification authority,
- revoke stops future access while preserving prior attribution/evidence/history,
- private/personal content remains separate from shared motorcycle context,
- invite action exists without turning the screen into an enterprise permission console.

Visual QA result: `PASS_WITH_CONSTRAINTS`.

Required constraints:
- permission detail should remain progressive and simple,
- `Erişimi kaldır` must not imply deletion of historical contribution/evidence,
- participant/service/helper badges must not imply verified truth.

## Cross-Screen Product Protections

- Profile is optional for current approved core/local value.
- Language, units and accessibility support cannot require profile/account creation.
- Migration must preserve no-silent-loss / no-silent-overwrite semantics.
- Cancel/failure preserves usable local/source state.
- Collaboration is attributed, limited and revocable.
- Revoke changes future access, not historical provenance.
- Private/personal content can remain separate from shared motorcycle context.
- No auth provider, cloud/sync architecture, backend/API/database, pricing/tier/quota or implementation choice is approved by these visuals.

## Visual-System Boundary

The accepted family continues the calm Kavriva visual direction:
- near-white canvas,
- graphite/navy hierarchy,
- restrained electric-blue,
- moderate rounding,
- low decorative noise,
- restrained L05A presence.

Exact production font, spacing, color, icon, component, route/sheet behavior, dark mode and responsive rules remain non-final.

## User Feedback Preserved

The delegated handoff preserves the user's explicit UX refinement feedback, including:
- unreadably minimal text should be avoided,
- upper-third density should be reduced,
- unnecessary explanatory content should be removed,
- K01 hero/visual area should be removed for a simpler screen.

## Downstream Use

`REF-PROFILE-001` may be used as working visual authority for FAM-08 only. It does not finalize authentication, synchronization, account infrastructure or implementation technology.
