# GRAPH METADATA AND IDENTITY STANDARD

Status: PROPOSED (Group 1, reviewed PASS 2026-09-21)

## Identity scheme

- Type prefix + stable slug (e.g. `T-E3-001`): immutable once assigned.
- Rename only through a `supersedes` chain; history is never rewritten.
- Serialization format (YAML-frontmatter / JSON / filename convention) is HELD for Phase-7 detail;
  no format selected here.

## Metadata fields (minimum, verbatim)

`purpose`, `domain/module/owner`, `depends_on` / `used_by`, `implements`, `public_contracts` / `internal_scope`,
`tasks` / `tests` / `evidence`, `supersedes` / `superseded_by`, `status` / `last_verified`.

Records are Markdown/Obsidian-compatible with machine-verifiable metadata.

## Repository topology note

- Planning truth (this repository) vs implementation truth (later code repo/vault, `kavriva-app` deferred to
  Phase 8) linked through stable identities.
- Governed addresses for artifacts, registries, queues and evidence. Addresses/schema are logical;
  filesystem vault layout remains HELD for Phase-8 evidence.

## Task registry address and schema (definition for Phase 8 to build)

- Current registry: `06_DELIVERY_PLANNING/TASK_INDEX.md` — 7 columns
  (Task ID | Flow/Feature | Objective | Depends On | Context Pack | Acceptance | Status), all PROPOSED.
  Frozen as planning truth; READY-lifecycle applies only to the Phase-8 physical registry with an explicit
  migration/supersedes rule. `Evidence` becomes a Phase-8 field, not a current column.
- Physical build (registry software, automation, vault) is deferred to Phase 8. No router/harness/CI/vault
  implementation, tool choice, account/key/purchase/code selected here.
