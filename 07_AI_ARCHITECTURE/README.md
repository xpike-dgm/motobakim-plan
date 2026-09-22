# 07 — AI-NATIVE DEVELOPMENT ARCHITECTURE

Amac: Yeni bir AI oturumunun yalnizca ilgili context'i okuyup belirli bir task'i sistemin geri kalanini bozmadan uygulayabilmesini saglayacak gelistirme mimarisini tasarlamak.

Bu asama klasor yapisindan fazlasidir: context routing, modul sinirlari, public contracts, dependency rules, validation, migration, rollback, AI protokolleri ve architecture tests tanimlanir.

`DEC-0028` geregi mimari Obsidian-compatible, machine-verifiable proje graph'i; contract-governed task-addressable
modul kapsulleri; minimum yeterli context pack; allowed/forbidden change scope; canonical design rules ve cok katmanli
completion evidence tasarlamak zorundadir. Hedef rastgele dosya kucultmek degil, kucuk degisiklik yuzeyi ve enforce
edilen sinirlardir.

Status: PROPOSED (Groups 1–5 recorded 2026-09-21; Group 6 audit pending)

## Document map (all PROPOSED unless noted)

- Group 1: `ARCHITECTURE_PRINCIPLES.md`, `MODULE_BOUNDARIES.md`, `DEPENDENCY_RULES.md`,
  `GRAPH_METADATA_AND_IDENTITY_STANDARD.md` (identity, metadata, topology, registry definition).
- Group 2: `CONTRACTS/CONTRACT_TEMPLATE.md`, `PUBLIC_CONTRACTS.md`, `CONTRACTS/CONTRACT_CATALOG.md`
  (contents defined-by-reference, no longer EMPTY), `CONTRACTS/README.md`, `CONTEXT_PACKS/README.md`
  (both mapped here; authoritative template is the Group-2 one).
- Group 3: `CONTEXT_ROUTING.md`, `CONTEXT_PACKS/PACK_STANDARD.md`, `AI_CODING_PROTOCOL.md`,
  `TASK_EXECUTION_PROTOCOL.md`, `OWNER_STATUS_AND_ESCALATION.md`, `DRY_RUN_WALKTHROUGH.md`.
- Group 4: `VALIDATION_STRATEGY.md`, `ARCHITECTURE_TESTS.md`,
  `COMPLETION_EVIDENCE_AND_CLOSURE_MATRIX.md`, `RULES/README.md` (R-001..R-014).
- Group 5: `CHANGE_CONTROL.md`, `DESIGN_CONSISTENCY_AND_CHANGE.md`, `MIGRATION_POLICY.md`,
  `ROLLBACK_STRATEGY.md`.
- Group 6 (this loop): this refresh + Gate 7 → 8 readiness audit. Physical construction belongs to Phase 8.
