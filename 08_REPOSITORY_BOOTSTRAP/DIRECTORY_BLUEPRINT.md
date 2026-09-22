# DIRECTORY BLUEPRINT (DRAFT — Phase-8 Step 1, pending independent review)

Status: REVIEWED PASS (round 1: CHANGES_REQUESTED 6 findings → narrow remediation; round 2: independent
re-review PASS with no open findings, 2026-09-22; installation to `kavriva-app` pending owner approval)

Binding sources (single truth, not copied): `05_ADR/RECORDS/ADR-008` (Flutter consumer app, Android-first
`DEC-0032`); `ADR-002` (managed Supabase PostgreSQL/Auth; server/API boundary "Supabase Edge Functions or an
equivalently bounded runtime as the initial low-operations candidate, replaceable until proven"; RLS/Storage
policies mandatory); `07_AI_ARCHITECTURE/MODULE_BOUNDARIES.md` (capsule
anatomy + binding seam table); `GRAPH_METADATA_AND_IDENTITY_STANDARD.md` (identity + YAML frontmatter +
vault-layout HELD resolved here); `CONTRACTS/CONTRACT_CATALOG.md` (9 contracts); `RULES/README.md` (R-001..R-014);
this folder's `README.md` (templates/registry/CI become real in this phase — existence scope only).

## Resolved HELD item

Phase-7 `GRAPH_METADATA_AND_IDENTITY_STANDARD.md` left the filesystem vault layout HELD for Phase-8 evidence.
This blueprint resolves it: the implementation repository carries ONE Obsidian-compatible vault (`vault/`)
plus engine modules (`modules/`) plus shared templates (`templates/`) plus CI (`.github/workflows/`).
No second vault, no split-brain: planning truth stays in the planning repository (local working copy
`Kavriva-plan`, GitHub remote `motobakim-plan`), implementation truth lives here,
linked through stable identities (`T-…`, `E…`, contract slugs).

## Top-level layout (target: `https://github.com/xpike-dgm/kavriva-app`)

```text
kavriva-app/
  .github/
    workflows/            # ADDRESS RESERVED, contents HELD for Step 4 (CI plan). No file decomposition
                          # selected here; Step 4 decides names, events, fail conditions, merge gates.
  vault/                  # Obsidian-native graph (Markdown + YAML frontmatter; JSON indexes generated only)
    REGISTRY/             # physical task registry — defined-by-reference to TASK_INDEX 7-column schema
                          # (GRAPH_METADATA task-registry section); planning truth stays frozen there.
                          # Migration/supersedes rule (binding): physical rows are NEW records with stable slugs
                          # that `supersedes` the corresponding planning rows; planning rows are never edited or
                          # copied; READY-lifecycle applies only here (R-006, R-010).
    PACKS/                # task context packs (14 fields per PACK_STANDARD.md, defined-by-reference)
    CONTRACTS/            # binding contract records (defined-by-reference to catalog; no copied contents)
    EVIDENCE/             # completion evidence per closure matrix (10 layers)
    INDEX/                # generated JSON indexes only (never hand-edited)
  modules/                # one capsule per epic; anatomy mandatory per MODULE_BOUNDARIES.md
    e01-app/              # E1 consumer mobile (Flutter)
    e02-panel/            # E2 company panel (browser)
    e03-server/           # E3 API + data backbone (Supabase: Edge Functions or equivalently bounded replaceable
                          # runtime; RLS/Storage policies; migrations)
    e04-offline/          # E4 offline package + ledger sync
    e05-identity/         # E5 auth/entitlement/audit-recovery
    e06-release/          # E6 promotion chain + incident brake + signing-custody policy
    e07-build-lane/       # E7 Android lane + store-lane execution (E6 owns policy, E7 executes)
    e08-content/          # E8 content/measurement planes
    e09-ai/               # E9 assistant flow + decision layer + deterministic final verification
    e10-graph/            # E10 registry software, router, checks, closure tooling
  templates/              # existence per this folder's README; contents defined-by-reference ONLY (no copied text):
                          # MANIFEST stub → capsule anatomy (MODULE_BOUNDARIES.md); CONTRACT stub → 07
                          # CONTRACT_TEMPLATE.md conformance-test form; PACK stub → PACK_STANDARD.md 14 fields.
                          # Full authoring belongs to owning steps (2/3/5); Step 1 reserves the addresses.
  README.md               # repo landing: path map + pointers to planning truth (no new truth authored here)
```

## Per-module anatomy (every `modules/eXX-*/` carries ALL of these; R-001)

- `MANIFEST.md` — purpose; public contract surface; internal scope; allowed/forbidden dependencies;
  tests; change/rollback rules; requirement/design/task/test links (capsule anatomy, verbatim).
- `public/` — ONLY the declared public surface; cross-boundary users may touch nothing else.
- `internal/` — storage layout, caches, helpers, in-flight state; invisible outside the capsule.
- `tests/` — conformance tests with IDs + evidence links (R-013).
- New cross-module seam use without a manifest declaration + review = violation. Binding seam table
  (MODULE_BOUNDARIES.md, quoted by pointer — the table there is the single truth, not this line): E9 proposes /
  E1 renders / E3 verifies (no E1↔E9 cycle); E2 consumes E8 outputs (E8 derives, E2 renders); E6 ← E3,E5,
  E7 ← E3,E6 (E6 decides, E7 executes); E4 ← E3, consumed by E1; E5 identity-plane calls E3 runtime edges
  (single end-to-end owner: E3); E1/E5 entitlement render/authorize split (E1 renders, E3 serves, E5 authorizes).

## Identity + metadata (R-004, enforced at review; semi-auto check in Step 5)

- Every record/layout node: Type prefix + stable slug, immutable once assigned; first claim wins,
  collisions rejected never merged; rename only via `supersedes` chain (R-010: supersede, never erase).
- Markdown + YAML frontmatter minimum fields: `purpose`, `domain/module/owner`, `depends_on`/`used_by`,
  `implements`, `public_contracts`/`internal_scope`, `tasks`/`tests`/`evidence`,
  `supersedes`/`superseded_by`, `status`/`last_verified`.

## Explicit non-goals of this blueprint

- No stack/tool re-selection (Flutter + Supabase locked by ADR-002/ADR-008); no account/key/purchase;
- no product feature code; no CI implementation (reserved addresses only — Step 4);
- `BOOTSTRAP_PLAN.md`, `CI_PLAN.md`, `QUALITY_GATES.md` stay EMPTY until their steps.

## Path → source mapping (auditable; every Step-1 path has exactly one row)

| Blueprint path | Single binding source | Step-1 content limit |
|---|---|---|
| `.github/workflows/` | this folder's `README.md` (CI becomes real this phase) + `RULES/README.md` R-002/R-003 (auto, HELD) | address reservation only; contents HELD for Step 4 |
| `vault/` + subfolders | `GRAPH_METADATA_AND_IDENTITY_STANDARD.md` (vault layout, identity, frontmatter, registry definition) | addresses + defined-by-reference; no records authored |
| `modules/e01-app/` | `EPIC_CATALOG.md` E1 + `ADR-008` (Flutter, Android-first) | address only; manifest authored in Step 2 |
| `modules/e02-panel/` | `EPIC_CATALOG.md` E2 | address only; manifest authored in Step 2 |
| `modules/e03-server/` | `EPIC_CATALOG.md` E3 + `ADR-002` (Supabase; replaceable runtime wording above) | address only; manifest authored in Step 2 |
| `modules/e04-offline/` | `EPIC_CATALOG.md` E4 + `ADR-009` (via Package/Ledger contracts) | address only; manifest authored in Step 2 |
| `modules/e05-identity/` | `EPIC_CATALOG.md` E5 + `ADR-005`/`ADR-004` (via Audit contract) | address only; manifest authored in Step 2 |
| `modules/e06-release/` | `EPIC_CATALOG.md` E6 + `ADR-003`/`ADR-007` (via Release contract) | address only; manifest authored in Step 2 |
| `modules/e07-build-lane/` | `EPIC_CATALOG.md` E7 (E6 owns policy, E7 executes) | address only; manifest authored in Step 2 |
| `modules/e08-content/` | `EPIC_CATALOG.md` E8 | address only; manifest authored in Step 2 |
| `modules/e09-ai/` | `EPIC_CATALOG.md` E9 | address only; manifest authored in Step 2 |
| `modules/e10-graph/` | `EPIC_CATALOG.md` E10 + `PACK_STANDARD.md` (via Task-pack contract) | address only; manifest authored in Step 2 |
| `templates/` | this folder's `README.md` (existence) + respective 07 sources (contents, by reference) | stubs by reference only; full authoring in owning steps |
| `README.md` (repo landing) | Step-1 scaffolding: map + pointers, no new truth | map + pointers only |

## Acceptance of THIS draft (review gate)

1. Mapping-table completeness: every top-level path appears exactly once above (manual check against the
   tree; R-002 auto-check itself is HELD until Step 4 — this criterion does NOT claim it).
2. Capsule coverage: E1..E10 each own exactly one module address (manual check against `EPIC_CATALOG.md`);
   cross-cutting notes (Turkish/a11y, entitlement split, notifications, E1/E9 interface) recorded as
   manifest constraints for Step 2, not as folders (manual check — manifests themselves are Step 2).
3. Single-truth check: no paragraph in this draft copies binding-source content; every normative sentence
   cites its source row above (manual check; seam lines quote-by-pointer).
4. Reviewer verdict PASS with zero open findings, by a different context (R-007); agreement is not approval.
