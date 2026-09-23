# EXTERNAL CHANGE TRIGGERS (OUT-3 B-33 closure, 2026-09-23; DEC-0063)

Status: APPROVED (under DEC-0062 mandate; pending Gate-8 record alignment)

When an external platform changes, the listed gate/decision REOPENS (review-gated); work downstream of it
holds until re-verification PASS. Silence is not consent: an unlisted change opens a change-request first.

| External change | Reopens | First action |
|---|---|---|
| GitHub plan/pricing/permissions change (rulesets, Actions, runners) | DEC-0051 + DEC-0061 + Gate 8 CI clause | Re-verify gates fire on a probe; else rewrite CI_PLAN + new DEC |
| Actions runner image / action version removal (e.g. checkout@v4, Node runtime) | CI quality gates (Step 4) | Pin commit hash; green re-run; record versions here |
| Supabase pricing/limits/Auth/Storage behavior change | ADR-002 + DEC-0035 + E3 C3.7 cost BOM | Re-run cost + custody review; redesigned tasks as needed |
| Flutter/Dart channel, plugin allowlist, device/OS matrix change | TSQ-001-narrow + ADR-008 R6 + DEC-0054 | Re-evaluate matrix; device proof stays HELD until closed |
| Play Console / App Store policy, fee, privacy-label, Data-Safety change | B-09 capabilities (C1.11/C3.9/C5.8/C7.6) + Gate 8 release clause | Re-inventory declarations (T-E7-011); hold submission |
| Apple notarization/signing policy change | C7.2 iOS gates + E7 lane | Re-verify gate evidences 1-by-1; no commitment without owner ask |
| Google Drive loss (review evidence links) | DEC-0040 workflow + review evidence (REVIEW_LOG) | Mirror critical evidence into planning repo; new DEC if workflow changes |
| Model/provider price or retirement (AI path) | C9.2/C9.3 + E9 manifest | Re-evaluate adapters; deterministic fallback carries users |

Accepted-risk note (2026-09-23, OUT-3 B-33): CI emits a Node-20 deprecation warning on `actions/checkout@v4`.
Action pinning needs a verified commit hash the manager does not hold and will not invent; `@v4` stays with
this note until a trustworthy hash arrives (owner-provided or network-verified session). The trigger above
stays armed: runtime removal reopens the CI gates immediately.

## DEC-0063 — External-Change Trigger Rule
**Date:** 2026-09-23
**Status:** APPROVED (under DEC-0062 mandate)

The table above is binding: listed external changes reopen the listed gates/decisions. Unlisted changes open a
change-request (never silent continuation). First owner-visible signal of any trigger is a status line in
`NEXT_ACTION.md`, not a quiet fix.
