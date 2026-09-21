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
- Gate 3 -> 4 passed.
- Phase 4 Technology Strategy working-direction coverage is complete for the recorded `TSQ-001`–`TSQ-018` set.
- Gate 4 -> 5 is **CLOSED / readiness audit pending**. Phase 5 has not started.
- Planning remains no-code.
- Consumer mobile: Android-first / iOS-later; Flutter working direction (`DEC-0032`, `DEC-0033`).
- Data/backend/offline: canonical data boundary + managed Supabase-centered backend + SQLite/Drift local direction
  (`DEC-0034`–`DEC-0036`).
- Identity/API/Internal Ops: consumer Supabase Auth/local-first direction; privileged identity remains held; API runtime has
  no final winner; Internal Operations is CSR-first browser/static+API at direction level (`DEC-0037`–`DEC-0039`).
- External AI project work uses Drive + GitHub and supports isolated parallel research/review (`DEC-0040`, `DEC-0041`).
- CMS/publishing authority remains Kavriva-owned with optional replaceable authoring adjunct (`DEC-0042`).
- Analytics/measurement uses a split/hybrid, minimized, non-authoritative and replaceable analytics direction
  (`DEC-0044`).
- Mobile build/release uses the split/hybrid Android-continuity direction; iOS/macOS activation remains HELD on real
  access/custody/recovery/clean-room evidence (`DEC-0045`).
- AI/LLM direction: cheapest/fastest adequate conversational model by default; provider/model-neutral decision layer;
  deterministic/canonical final validation; Jev optional-later only (`DEC-0046`).
- Download/storage direction: one verified required compact core containing all required-safety-media; no
  cellular/roaming/byte-threshold confirmation; safety-nonrequired media may be on-demand; adaptive eviction protects
  active/durable/protected truth; exact MB/GB/% limits remain HELD (`DEC-0047`).
- No provider/model/plan/account/purchase/code/deployment/production proof is authorized merely by these Phase-4 working
  directions.

## Manager Transition — Immediate Duty

This file is being handed to a fresh manager after `DEC-0047`.

The next manager must **not**:
- invent a new Phase-4 technology topic;
- treat HELD later-phase numeric/provider/device evidence as automatically requiring another debate;
- start Phase 5 or create ADRs;
- mark Gate 4 -> 5 passed without owner approval.

The next manager must first perform the closure/readiness audit named in `00_CONTROL/NEXT_ACTION.md`:

1. reconcile `TSQ-001`–`TSQ-018`, user decisions, research/review/judge evidence and registries;
2. verify the Gate 4 -> 5 criterion in `PHASE_GATES.md`;
3. classify each remaining HELD item as legitimate later-phase evidence or a real missing Phase-4 blocker;
4. repair only canonical-memory drift found by the audit;
5. if blockers remain, keep Gate 4 -> 5 CLOSED and state the exact missing evidence;
6. if ready, explain the closure evidence to the nontechnical owner and request explicit Gate 4 -> 5 approval;
7. only after explicit owner approval may Phase 5 / ADR work begin.

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

