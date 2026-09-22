# CONTRACT TEMPLATE

Status: PROPOSED (Group 2, reviewed PASS 2026-09-21; conformance-test formats and evidence formats defined in Group 4)

Every module contract instantiates ALL of the following fields. A contract missing a mandatory field fails
gate review. This template defines field names and rules only — no contract contents, mechanisms, accounts,
keys, purchases or code.

## Mandatory fields (verbatim)

- `owner`
- `allowed_dependencies` / `forbidden_dependencies` + `allowed-edge ID`
- `implements`
- `depends_on` / `used_by`
- `requirement` / `design` / `task` / `test links`
- `status` / `last_verified`
- `classification` / `authority propagation note`

## Surface and parties

- Provider capsule and consumer scope.
- Surface inventory: functions, data and events with exact signatures.
- Pre-conditions and post-conditions, with commit-time authorization-tuple reference (never duplicated logic —
  reference ADR-006, do not copy field lists here).
- Negative cases: what the contract explicitly does NOT guarantee.

## Identity and version (split rule)

- Contract ID is stable per `GRAPH_METADATA_AND_IDENTITY_STANDARD.md` Identity scheme and immutable.
- Monotonic `version` with `supersedes_version` pointer carries routine changes.
- Graph `supersedes` / `superseded_by` is reserved strictly for Contract-ID replacement/rename with preserved
  history. History is never rewritten.
- Untested-critical or ownerless contract = gate FAIL (see `DEPENDENCY_RULES.md` detections).

## Change, deprecation, emergency (pointers only)

- Change history is recorded; no silent edits.
- Emergency contract change = new version + mandatory retrospective via Change Control (pointer only;
  `CHANGE_CONTROL.md` is PROPOSED). The ADR-003 emergency path is negative-only and is NOT invoked here.
- Deprecation/migration pointers (policy defined under Change Control / Migration Policy, both PROPOSED).
- Support window + owner-readable impact note stated per contract; runtime dual-support is a per-capability
  implementation decision, not mandated here. No numeric window is set by this template.

## Evidence (pointer only)

- `conformance-test IDs` + `evidence links` (format defined in Group 4). No format defined here.
