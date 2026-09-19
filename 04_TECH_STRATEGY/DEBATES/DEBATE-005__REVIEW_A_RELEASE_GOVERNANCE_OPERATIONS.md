# DEBATE-005 — Review A: Release Governance, Operations and Product Safety

Date: 2026-09-17
Reviewer: Independent Luna Max adversarial reviewer
Mode: Read-only, no code
Verdict: `PASS_WITH_CHANGES — NOT ADR-READY`

## Sound direction

- immutable artifact identity and exact provenance/SBOM binding;
- promotion of the same verified artifact rather than production rebuild;
- separate release domains and scoped signing/deployment identities;
- explicit partial/failed/unknown outcomes;
- CI cannot approve technical truth;
- rollback only to still-trusted compatible artifacts;
- browser state never grants authority;
- emergency suspension remains negative-only;
- no OTA channel is silently approved.

## Findings and incorporated corrections

### Separate credentials did not ensure human independence

Incorporated: consequence-tier human-independence is mandatory for high-consequence releases. Alias/service-account paths
cannot collapse incompatible roles; absent independent reviewer/promoter/custodian leaves a visible `HELD` release with
owner/escalation and pre-authorized scoped backup procedures.

### Cross-domain compatibility was only a declaration

Incorporated: one closed release-meaning graph binds client capability, API/schema, content, configuration, migration,
external resources, offline task package/recovery closure and release/suspension generations. Old clients that cannot
represent critical semantics receive no positive application authority.

### Feature flags could mutate approved meaning

Incorporated: exact effective values, defaults, audience, scope, expiry, templates/transforms/resources and config digest
belong to release closure. Meaning-changing changes require new appropriate review and current suspension-generation check.

### Migration rollback was too similar to binary rollback

Incorporated: migration has planned/started/partial/failed/reconciling/reconciled states, checkpoints, compatibility,
concurrent-write/idempotence rules, partial-region handling and data-preserving forward correction. Unsafe recovery holds.

### Emergency fencing did not cover every release domain

Incorporated: binary, web, backend, migration, config, content and restore promotions all bind the current protected
suspension/revocation generation. Containment patches cannot silently clear suspension.

### Offline/data-efficiency evidence was missing

Incorporated: task/motorcycle-scoped offline manifest, complete reachable-state recovery closure, optional-media boundary,
active-work pinning, integrity and size class are release evidence. Incidents traverse dormant/offline bundles and active work.

### Privacy classification was absent from the manifest

Incorporated: classification/disclosure scope and derivative propagation are release closure; unknown/mixed uses the most
restrictive handling. Community acceptance never becomes official verification.

### Small-team ceremony could cause shadow release paths

Incorporated: release-tier ceremony and visible hold behavior; exact staffing/availability and low-risk combinations remain open.

## Conclusion

The corrected direction is suitable for user working-direction review. Exact staffing, numeric objectives, formats and
providers remain unresolved; no ADR/Gate 4 → 5 passage is justified.
