# DEBATE-013 — CMS and Controlled Publishing Manager Synthesis

Status: `USER-APPROVED PHASE-4 WORKING DIRECTION / DEC-0042 / NO PROVIDER WINNER`

## Nontechnical Decision

Kavriva will keep safety-critical content control inside Kavriva. A separate CMS may later be used only to make writing
and organizing bounded content easier. It cannot become the authority that decides which technical information is true,
approved, released, recalled or available in an offline package.

## Binding Working Direction

- Kavriva owns source/evidence/claim relationships and motorcycle/variant applicability.
- Human approval binds an exact immutable Kavriva snapshot.
- Kavriva owns the final release transition and release identity.
- Recall/suspension is a newer negative authority that must beat older releases, caches, restores and offline packages.
- Kavriva owns mobile/offline package eligibility and dependency closure.
- Search, cache, CDN and any CMS projection are rebuildable and non-authoritative.
- CMS publish, provider console, webhook, direct database action or provider restore cannot create approved Kavriva
  technical live state.
- A future CMS candidate must be removable through a clean-room replacement without changing technical truth or safety behavior.

## Why

The reviewed research found that CMS products can provide useful authoring, localization, version and editorial tools,
but none of those labels alone proves Kavriva's approval, recall, offline safety, protected audit or provider-bypass
requirements. Keeping the safety boundary in Kavriva prevents editorial convenience from silently becoming technical authority.

## Deferred Selection

No product is selected. Directus, Strapi, Contentful, Sanity and a product-owned workflow remain evidence/reference
mechanisms. A CMS should be reconsidered only when real authoring volume, localization/media workload or operator burden
shows that the additional system is worth its cost and integration risk.

## Evidence

- Drive TASK-001 research package and handoff.
- REVIEW-001: CHANGES_REQUESTED for incomplete failure-row detail.
- Revised 48-row S1–S12 × A–D matrix.
- REVIEW-002: PASS with no Critical, Major or Minor findings.
- Exact links: `00_CONTROL/DRIVE_ARTIFACT_INDEX.md`.

## Boundary

This is a reversible Phase-4 working direction. It does not approve a CMS/provider, account, plan, trial, purchase,
schema, code, deployment, Phase-5 ADR or Gate 4 -> 5 transition.

