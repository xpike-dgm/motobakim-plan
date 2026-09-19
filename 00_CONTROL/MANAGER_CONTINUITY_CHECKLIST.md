# Manager Continuity Checklist

## Start of Every New Manager Session

- Read `/AGENTS.md` and `MANAGER_START_HERE.md`.
- Follow the mandatory read order.
- Verify `NEXT_ACTION.md` agrees with `CURRENT_STATE.md`, `OPEN_QUESTIONS.md`, `DECISION_LOG.md` and phase status.
- Check the latest Git commit and whether the working tree contains uncommitted user work.
- Do not ask the owner to reconstruct known project history.

## Before Opening Work

- Name the authoritative open question or requirement.
- State authorized and forbidden scope.
- Identify required context and acceptance evidence.
- Decide whether work stays local to GitHub or needs a Drive `TASK-XXX`.
- If multiple external AIs run in parallel, freeze one brief and assign distinct output IDs.

## Before Accepting Work

- Verify deliverable location and revision.
- Check every acceptance condition, not only the worker summary.
- Require independent review where specified.
- Preserve CHANGES_REQUESTED/BLOCKED history.
- Separate research acceptance, working-direction approval, ADR approval and production evidence.

## After Material Work

- Update current state, next action, decision/open-question status, registry, phase record, changelog and handoff as applicable.
- Record Drive/GitHub evidence links.
- Run `git diff --check` and a consistency search for stale status wording.
- In living files, search for old phrases such as `pending`, `not started`, `active`, `form not decided` and `no winner`;
  compare them with later DEC records. Preserve genuine historical snapshots but label them explicitly as historical.
- Commit a coherent checkpoint and push when authorized.

## Before Manager Handoff

- `NEXT_ACTION.md` names one immediate continuation path.
- `MANAGER_START_HERE.md` snapshot is current.
- `HANDOFF.md` contains the latest accepted evidence and hard boundaries.
- `NEW_MANAGER_CHAT_PROMPT.md` still points to the canonical bootstrap rather than duplicating volatile state.
- GitHub contains the latest commit; Drive-only artifacts are indexed.
