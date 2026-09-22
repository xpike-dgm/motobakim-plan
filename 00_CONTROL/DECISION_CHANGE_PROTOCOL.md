# DECISION CHANGE PROTOCOL — Any-Chat Executable Card

Status: ACTIVE OPERATING PROCEDURE
Authority: `DEC-0028`, `DEC-0029`, `DEC-0005` (evidence/synthesis/decision separation), ADR-015 (supersession chain)

## Purpose

Mid-flight owner decisions (mind changes, scope cuts, reversals) must propagate without a fixed manager AI.
Any competent chat — including a brand-new one with no history — can execute this card end to end, because every
step's inputs, tools and outputs are written below. A second, different chat verifies afterwards. The owner only
appears at the two marked touchpoints, in plain language, never with technical content.

## Triggers

- Owner states a product/scope/technology change in plain language in any chat.
- A reversal trigger written in an ADR fires on new evidence.
- A review or gate finds a decision unworkable as written.

## Roles

- **Executing chat:** runs steps 1–5 below. Needs no prior context beyond this card + the cited records.
- **Verifying chat:** a different chat runs step 6. Never the same chat as execution.
- **Owner:** appears only at steps 4 (options) and 5 (approval).

## Procedure

### Step 1 — Capture (no interpretation)

Write the decision as PROPOSED with: verbatim owner quote (or trigger reference), date, and stated reason.
Location: `00_CONTROL/CHANGELOG.md` new entry + a `PROPOSED` note on the affected record (ADR/catalog line).
Do NOT edit, delete or overwrite the old decision. Do NOT infer beyond what was said; quote, don't paraphrase.

### Step 2 — Impact query (mechanical, not judgment)

1. Find the graph/record nodes the decision touches (search IDs, names and linked edges in `DEPENDENCY_GRAPH.md`,
   catalogs, ADR relations; post-Phase-8 use the graph query instead of manual search).
2. Follow `depends_on` / `used_by` edges outward from each touched node, collecting: dependent tasks, tests,
   evidence records, contracts and decisions.
3. List every affected item with its ID and one-line reason. If an edge is ambiguous, list it as
   `UNVERIFIED` and include it — never silently drop a maybe-affected item.
4. Count: affected tasks, affected records, re-review load.
5. Term checklist (do not stop at keyword hits): screen IDs (SCR-xxx), navigation/tab/shell records, REF-xxx
   visual authorities, DEC/TSQ/CON IDs, BR/Q business rules, IDCO-RQ-xxx requirements, community/moderation
   surfaces (SCR-035/036/038, REF-COMMUNITY-001), shell/tab records (DEC-0017, five-tab, bottom-bar rule).
   Splits that share a record (e.g. RQ-046/047 serving both moderation and audit views) must be divided, not
   deleted wholesale.
6. Map BLOCKED/REVIEW outcomes to `TASK_INDEX.md` vocabulary (PROPOSED-only states); order the independent
   re-review (DEC-0052) after re-scoping, not before. Note Path C manual carrying: the executing chat receives
   copy-paste packs, never implicit context.

### Step 3 — Mark (never erase)

- Set every affected task to `BLOCKED (awaiting re-scope)` with a link to the PROPOSED decision. History,
  evidence and prior verdicts stay untouched.
- Mark conflicting older records as candidates for `SUPERSEDED` — do NOT apply the status yet.

### Step 4 — Owner touchpoint 1: options (plain language)

Present, in nontechnical outcome/risk/cost language: what changes, how many tasks are affected, estimated extra
work/delay, and real alternatives including "keep the old decision". Ask for direction. Ask nothing technical.

### Step 5 — Owner touchpoint 2: apply only on explicit approval

Only after explicit owner approval, and only what was approved:
1. Update the affected records; set replaced decisions to `SUPERSEDED` (full old text preserved, never deleted).
2. Re-scope affected tasks (new objective/scope/acceptance deltas), set them to `REVIEW` for re-verification.
3. Record everything in `CHANGELOG.md` with the approval quote.

### Step 6 — Independent verification (different chat)

The verifying chat checks, against this card: decision captured verbatim? Impact list complete (spot-check at
least 3 edges)? History preserved (old text still present as SUPERSEDED)? Affected tasks re-queued, unaffected
tasks untouched? Verdict `PASS` or findings list. Findings return to step 2 (affected rows only).

### Step 7 — Push/commit only with explicit owner authorization

## Conflict Rules

- Newest explicit owner instruction wins; record the override, never hide the conflict.
- Security/emergency changes may fast-track steps 1–3 immediately, but steps 4–6 follow as retrospective
  within the same cycle — no silent permanent exception.
- If this card itself is unclear or contradictory for the case at hand: stop, mark the task BLOCKED, and ask
  the owner for direction. Never invent a new procedure silently.

## What This Card Does Not Cover

- First-time decisions with no precedent (handled by normal phase planning, not this card).
- Account/purchase/production authorizations (still need explicit approval per item, `DEC-0030`).
- Code-writing mechanics (covered by task packs, not here).
