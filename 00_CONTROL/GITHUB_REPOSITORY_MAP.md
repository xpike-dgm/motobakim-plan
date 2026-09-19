# GitHub Repository Map

## Canonical Entry Layer

- `/AGENTS.md` — repository-wide AI behavior contract.
- `00_CONTROL/MANAGER_START_HERE.md` — canonical new-manager bootstrap.
- `00_CONTROL/NEXT_ACTION.md` — single volatile pointer to what happens next.
- `00_CONTROL/CURRENT_STATE.md` — detailed current phase/state.
- `00_CONTROL/SOURCE_OF_TRUTH.md` — authority map.

## Control and Audit Layer

- `DECISION_LOG.md` — user-approved decisions and boundaries.
- `OPEN_QUESTIONS.md` — unresolved and direction-level answered questions.
- `PHASE_GATES.md` — phase transition conditions.
- `DOCUMENT_REGISTRY.md` — important artifact status.
- `CHANGELOG.md` — append-only memory trail.
- `HANDOFF.md` — detailed continuation record.
- `DRIVE_ARTIFACT_INDEX.md` — Drive evidence links and lifecycle state.

## Phase Layers

- `01_WORKSPACE/` — project system, vision, constraints and vocabulary.
- `02_DISCOVERY/` — raw discovery sessions and approved synthesis.
- `03_DESIGN/` — design requirements, flows, screen/state architecture and approved reference index.
- `04_TECH_STRATEGY/` — no-code comparisons, reviews and working-direction syntheses.
- `05_ADR/` — future approved/locked architecture decisions; Phase 4 material does not automatically enter here.
- `06_DELIVERY_PLANNING/` — future epic/capability/feature/flow/task closure planning.
- `07_AI_ARCHITECTURE/` — future task routing, contracts, validation and Obsidian-compatible graph rules.
- `08_REPOSITORY_BOOTSTRAP/` — future application-repository bootstrap after gates permit it.

## Support Layers

- `90_TEMPLATES/` — reusable project templates.
- `99_ARCHIVE/` — superseded/non-authoritative material.
- `refernces/` — existing visual reference assets. The legacy misspelling is retained to avoid breaking recorded links;
  treat it as the visual-asset directory until a separately reviewed migration renames it.
- `.github/` — GitHub-native AI and contribution guidance.

## Volatility Rule

Volatile state belongs in `NEXT_ACTION.md` and `CURRENT_STATE.md`. Do not copy the entire current snapshot into prompts,
READMEs or templates. Stable rules belong in `/AGENTS.md`, `PROJECT_CHAT_INSTRUCTIONS.md` and decision records.

