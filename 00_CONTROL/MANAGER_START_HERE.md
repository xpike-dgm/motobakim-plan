# Manager Start Here — Canonical Bootstrap

Status: `ACTIVE / CANONICAL NEW-MANAGER ENTRYPOINT`
Repository: `https://github.com/xpike-dgm/motobakim-plan`
Project: Kavriva

## Purpose

A fresh manager AI must be able to continue without the old chat and without access to the owner's computer. GitHub is
the persistent planning truth; Google Drive carries external task/research/review/handoff artifacts. Chat history is not
authority.

## Mandatory Read Order

Read these files before doing meaningful work:

1. `/AGENTS.md`
2. `00_CONTROL/NEXT_ACTION.md`
3. `00_CONTROL/CURRENT_STATE.md`
4. `00_CONTROL/SOURCE_OF_TRUTH.md`
5. `00_CONTROL/DECISION_LOG.md`
6. `00_CONTROL/OPEN_QUESTIONS.md`
7. `00_CONTROL/PHASE_GATES.md`
8. `00_CONTROL/DOCUMENT_REGISTRY.md`
9. `00_CONTROL/PROJECT_CHAT_INSTRUCTIONS.md`
10. `00_CONTROL/HANDOFF.md`
11. `00_CONTROL/DRIVE_ARTIFACT_INDEX.md`
12. the active phase `README.md` and only the task-specific documents named by `NEXT_ACTION.md`

Do not bulk-read all 300+ artifacts unless a repository-wide audit specifically requires it.

## Current Snapshot

- Phase 1, Phase 2 and Phase 3 are complete.
- Gate 3 -> 4 passed. Phase 4 Technology Strategy is active. Gate 4 -> 5 is closed.
- Planning remains no-code.
- Consumer mobile working direction: Flutter (`DEC-0033`); Android-first, iOS later (`DEC-0032`).
- Managed Supabase-centered data direction behind the Kavriva API: `DEC-0035`; no purchased plan/account is authorized.
- Offline direction: SQLite/Drift + compact complete selected-task packages + durable API operation path (`DEC-0036`).
- Consumer identity direction: Supabase Auth + local-first account-light (`DEC-0037`); privileged identity is still held.
- API runtime: short DB-near Edge is a reversible hypothesis; managed container + worker remains equal-evidence (`DEC-0038`).
- Internal Operations: browser-based, CSR-first static artifact/CDN + Kavriva API direction (`DEC-0039`); framework held.
- CMS/publishing: Kavriva retains technical truth, approval, immutable release, recall/suspension, package eligibility and
  publication authority; a CMS may later be evaluated only as a replaceable authoring adjunct (`DEC-0042`). No CMS/provider is selected.
- External AI work uses Drive + GitHub, not the owner's computer (`DEC-0040`); parallel independent external AI work is allowed (`DEC-0041`).

## Owner and Communication Contract

The owner is a nontechnical solo founder with limited budget. Default to Turkish. Present technical choices in plain
language with consequences, risks, cost classes and reversibility. The owner is not expected to code, debug, inspect raw
logs or repair providers. Paid assumptions require explicit approval.

## Manager Session Protocol

1. Bootstrap from this repository; do not rely on remembered chat.
2. Read `NEXT_ACTION.md` and verify it against `CURRENT_STATE.md`, `OPEN_QUESTIONS.md` and the latest decisions.
3. State the current phase, last approved direction and immediate next action briefly.
4. Work only within the active task/phase and preserve HELD boundaries.
5. Use Drive tasks for external research/review. Keep each parallel output isolated.
6. After material progress, refresh the memory files listed in `/AGENTS.md`.
7. Before ending or changing manager, update `NEXT_ACTION.md`, `HANDOFF.md` and `CHANGELOG.md`, then commit and push when authorized.

## Authority Order

1. newest explicit user instruction;
2. APPROVED/LOCKED decisions in `DECISION_LOG.md` and phase authorities;
3. `SOURCE_OF_TRUTH.md`;
4. `CURRENT_STATE.md` and `NEXT_ACTION.md`;
5. approved phase documents and registry;
6. reviewed external evidence;
7. chat history and AI inference.

If two canonical files conflict, stop the affected decision, identify the conflict and repair the memory set. Never
silently choose the convenient version.

## Completion Meaning

`TASK-XXX DONE` proves only that task's acceptance checks. It does not prove a phase, product or project complete. Phase
completion requires its gate evidence; project completion later requires feature/flow/design/architecture/data/release
closure, not merely a list of finished tasks.

