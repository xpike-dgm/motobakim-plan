# ADR-011 — CMS Role and Controlled Publishing Mechanics

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-013, user-approved under `DEC-0042`) asked whether Kavriva's controlled content workflow
should live inside the canonical backend, use a separate open-source or managed headless CMS, or use a hybrid.
Drive research (TASK-001), remediation of REVIEW-001's Major M-1, independent REVIEW-002 PASS and manager synthesis
concluded: Kavriva retains all technical authority; a CMS may later serve only as a bounded, replaceable authoring
adjunct. This ADR locks that boundary. It selects no CMS product, provider, account, plan, trial or purchase, and
authorizes no schema, code, deployment or integration.

## Decision Drivers

- Safety-critical content control must stay inside Kavriva: approval, release, recall, package eligibility and
  publication authority cannot be delegated to an editorial tool.
- Authoring convenience (writing, organizing, localization, media handling) is real work and may later justify a
  helper system — but only if its cost and integration risk earn it.
- Editorial labels (versioning, workflow states in a CMS) must never be mistaken for Kavriva approval, recall or
  safety semantics.
- Anything Kavriva adopts must be removable without changing technical truth or safety behavior.

## Options Considered

### Option A — Kavriva-owned workflow only, no CMS (current position)

All authoring happens in Kavriva-owned surfaces under ADR-003 publication and ADR-004 authorization semantics.
No second system to integrate, secure, pay for or exit. Cost: authoring UX, localization and media workflows must
be built as Kavriva product work.

### Option B — Open-source headless CMS as authoring adjunct (held candidate)

Self-hostable CMS (Directus, Strapi or equivalent as reference mechanisms, not selections) for bounded authoring.
Reduces Kavriva authoring UI work but adds hosting, upgrade, backup, security and support burden onto the project —
burden the solo-owner model cannot silently absorb.

### Option C — Managed headless CMS as authoring adjunct (held candidate)

Managed CMS (Contentful, Sanity or equivalent as reference mechanisms) removes hosting burden but adds
subscription cost, provider coupling for the authoring path, and an exit dependency that must be proven removable.

### Option D — Controlled hybrid with Kavriva-retained authority (locked as the boundary rule)

Whichever adjunct (if any) is later chosen, it operates strictly inside this ADR's boundary: authoring convenience
in, technical authority out. This option locks the relationship, not the product.

## Decision

Kavriva adopts Option A today inside the Option D boundary rule for any future adjunct:

1. **Kavriva owns:** source/evidence/claim relationships, motorcycle/variant applicability, human approval over
   exact immutable snapshots, final release transition and release identity, recall/suspension generations,
   mobile/offline package eligibility and dependency closure, and final publication authority.
2. **A CMS (if ever adopted) is authoring-only:** drafting, organizing, localization support and media handling
   for bounded content. It cannot approve, release, recall, suspend, confer package eligibility or publish.
3. **No bypass path creates live state:** CMS publish actions, provider consoles, webhooks, direct database
   writes, cache/CDN states and provider restores cannot create Kavriva-approved technical live state. Anything
   reaching consumers passes the ADR-003 publication transition with ADR-004 authorization.
4. **Search, cache, CDN and CMS projections are rebuildable and non-authoritative**, consistent with ADR-001.
5. **Removability gate:** any CMS candidate must prove provider-bypass behavior, failure/reconciliation handling,
   safe TCO, owner-operability without technical repair, and source-untouched clean-room replacement that leaves
   technical truth and safety behavior unchanged. No CMS is required for first release merely for editorial
   convenience.
6. **Reconsideration trigger (not automatic adoption):** a CMS re-enters evaluation only when real authoring
   volume, localization/media workload or operator burden demonstrably outweighs its cost and integration risk.

## Rationale

The research showed CMS products offer genuine authoring value but none of their labels proves Kavriva's approval,
recall, offline-safety, audit or bypass requirements. Keeping the safety boundary in Kavriva costs more authoring
UI work but removes an entire class of silent-authority failures; the removability gate keeps future convenience
honest.

## Consequences

### Positive

- One unambiguous technical authority: no parallel "published in CMS vs approved in Kavriva" truth.
- No CMS subscription, hosting, upgrade or exit burden until volume justifies it.
- Authoring workflows stay inside the same authorization, audit and quarantine rules as everything else.

### Negative / Trade-offs

- Authoring, localization and media-management UX must be built as Kavriva scope (covered by Phase-3 workspace
  architecture and ADR-010).
- If content operations scale faster than expected, the lack of a CMS becomes an operator-burden bottleneck until
  re-evaluation — the trigger above exists for exactly this case.

## Prohibited / Constrained Alternatives

- CMS (or any external tool) holding approval, release, recall, suspension, package-eligibility or publication
  authority.
- CMS publish buttons, webhooks, console actions or direct database writes treated as publication events.
- Cached, searched or CDN-projected content presented as approved current truth.
- Adopting a CMS for convenience without passing the removability gate.
- Any CMS product/provider, account, plan, trial, purchase, schema, integration, code or deployment — none
  authorized by this ADR.

## Revisit Triggers

- Measured authoring/localization/media workload proves the adjunct's value exceeds its total cost and risk, with
  the removability gate proven — resolved by superseding ADR naming the product and its bounded role.
- Exact adjunct scope, candidate shortlist and integration design remain HELD until that trigger fires.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0042` (binding working direction)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md`
- `05_ADR/RECORDS/ADR-004__IDENTITY_AUTHORIZATION_SESSION_RECOVERY_AND_PRIVILEGED_ACTIVATION.md`
- `05_ADR/RECORDS/ADR-010__INTERNAL_WEB_FRAMEWORK_RENDER_AND_HOSTING.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-013__MANAGER_SYNTHESIS.md`
- `00_CONTROL/DRIVE_ARTIFACT_INDEX.md` (TASK-001 / REVIEW-001 / REVIEW-002 links)
- Downstream: Phase-6 authoring-task scope; ADR-015 (authoring module boundaries if a CMS is ever adopted)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
