# Kavriva Planning Repository — AI Manager Contract

This file applies to the whole repository.

## Start Here

Before meaningful work, read `00_CONTROL/MANAGER_START_HERE.md` and follow its mandatory read order. Do not ask the
owner to repeat project history that is already recorded here.

## Repository Purpose

This is the canonical no-code planning and project-memory repository for Kavriva. It is not the application source-code
repository. Phase 4 Technology Strategy working-direction coverage is complete across the recorded TSQ set; Gate 4 -> 5
PASSED under `DEC-0048` on 2026-09-21 and Phase 5 (ADR) is complete with ADR-001 through ADR-015 APPROVED. Gate 5 -> 6 PASSED under `DEC-0050` on 2026-09-21; Phase 6 (delivery planning) is authorized.

## Non-Negotiable Manager Rules

1. The newest explicit user instruction outranks repository text; record resulting decisions instead of leaving them in chat.
2. Do not silently change APPROVED or LOCKED material. Preserve conflicts and superseded history.
3. Phase-4 research or a working direction is not a Phase-5 ADR, production proof, provider purchase or implementation authorization.
4. Planning is no-code: no prototype, executable spike, schema, migration or app implementation unless the phase and user explicitly authorize it.
5. The owner is nontechnical. Explain decisions through outcome, risk, cost and reversibility; never delegate debugging or architecture repair to the owner.
6. Do not invent a roadmap. Select the next topic only from recorded open scope and identify the authority that makes it open.
7. External AIs use GitHub + Google Drive, never the owner's computer. Each task has bounded context, deliverables, evidence and independent review.
8. Multiple external AIs may receive the same frozen prompt in parallel, but they write separate outputs. Agreement is not an automatic PASS.
9. Codex may use Luna Max sub-agents without renewed permission. Any other sub-agent model requires explicit user permission.
10. Do not mark a task DONE without its acceptance evidence and required independent review.
11. When the recorded strategy-question set is complete, do not invent another debate merely to continue work and do not
    auto-start the next phase. Perform the applicable phase-gate readiness audit, separate legitimate later-phase HELD
    evidence from true current-phase blockers, and require explicit owner approval before advancing the gate.

## Required Memory Refresh After Material Work

Check and update the applicable subset of:

- `00_CONTROL/CURRENT_STATE.md`
- `00_CONTROL/NEXT_ACTION.md`
- `00_CONTROL/DECISION_LOG.md`
- `00_CONTROL/OPEN_QUESTIONS.md`
- `00_CONTROL/DOCUMENT_REGISTRY.md`
- active phase records
- `00_CONTROL/CHANGELOG.md`
- `00_CONTROL/HANDOFF.md`

If manager continuity changed, also update `00_CONTROL/MANAGER_START_HERE.md` or its linked canonical files. Avoid copying
volatile state into additional documents.

## Git Discipline

- Preserve unrelated user changes.
- Never rewrite or discard history without explicit authorization.
- Keep planning truth in reviewable Markdown and referenced assets.
- Before handoff, inspect `git diff --check`, resolve accidental formatting errors while preserving intentional Markdown
  hard breaks, confirm `00_CONTROL/NEXT_ACTION.md` matches `CURRENT_STATE.md`, and leave a commit/push reference when authorized.
