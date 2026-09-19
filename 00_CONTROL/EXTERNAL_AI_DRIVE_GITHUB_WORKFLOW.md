# External AI Drive + GitHub Workflow

Status: `USER-DIRECTED / ACTIVE OPERATING MODEL / NO LOCAL-COMPUTER DEPENDENCY`

## Purpose

Kavriva task work can be handed to external AI systems without sub-agent token usage. External AI workers receive only
Google Drive and GitHub access. They do not receive access to the user's computer, local workspace, desktop, terminal,
open applications or unshared local files.

## Google Drive Root

- [KAVRIVA_AI_WORKSPACE](https://drive.google.com/drive/folders/1EUAtVRdW6TWyQ_GbPTt5hcqs1EttbaK2)

Top-level folders:

- `00_START_HERE` — mandatory protocol and copy-paste prompts;
- `01_SOURCE_OF_TRUTH` — Drive-side decision and authority index;
- `02_TASK_QUEUE` — state-based `TASK-XXX` files;
- `03_CONTEXT_PACKS` — reusable minimum context bundles;
- `04_RESEARCH_INBOX` — external research reports awaiting review;
- `05_REVIEWS` — independent review records;
- `06_DECISIONS` — owner-approved decisions;
- `07_HANDOFFS` — delivery and continuation records;
- `08_GITHUB_COORDINATION` — repository/branch/PR working rules;
- `09_OUTPUTS` — accepted non-code deliverables;
- `98_ARCHIVE` — superseded/closed historical material;
- `99_TEMPLATES` — task, review and handoff templates.

Task queue states:

- `00_READY`
- `01_CLAIMED`
- `02_IN_PROGRESS`
- `03_REVIEW`
- `04_CHANGES_REQUESTED`
- `05_BLOCKED`
- `06_DONE`
- `99_CANCELLED`

## Canonical Drive Documents

- [AI Work Protocol](https://docs.google.com/document/d/1c70SrA6Rsv09xnB-lkvUj1u19mgiC7YV8Sy_7IkBIPk)
- [Copy-Paste Prompt for Any AI](https://docs.google.com/document/d/1yZEMlLUy5CMlaqWxFm0p9j4n0Y8SjqeYPxs-PYRGssg)
- [Source of Truth Index](https://docs.google.com/document/d/1DJACYKLViSRA37K_rqCptpydW8ls5nNA093opXQgR2g)
- [GitHub Work Protocol](https://docs.google.com/document/d/13NKWB6VjlNVqPBYpTlo5p32hY4nvAkzkjCWbb8MDLcE)
- [TASK-XXX Template](https://docs.google.com/document/d/1rTAJB__ix4eJkCjs5tUIlOlEr7t4U8IOU-geXMks0rw)
- [REVIEW-XXX Template](https://docs.google.com/document/d/1OWTrXcV_TSlyRIa_S_yfesMgHlbtLxWbJ_DrTxfv5EA)
- [HANDOFF-XXX Template](https://docs.google.com/document/d/1AOkYol4XULlyo9jOMx46-OCv5XD9_sFFLy6ff_4Olfw)

## Operating Rule

1. Every external-AI assignment has exactly one `TASK-XXX` execution contract.
2. The task lists the minimum sufficient Drive and GitHub context. Project-wide crawling is not the default.
3. Repository, base branch, task branch and writable paths must be explicit; the AI cannot guess them.
4. Local filesystem paths cannot be task dependencies or completion evidence.
5. The worker produces a Drive handoff and GitHub commit/PR evidence, then moves the task to review.
6. The implementer cannot independently mark its own work `PASS` or `DONE`.
7. Unknown authority, conflicting truth or missing access moves the task to `BLOCKED`; it does not authorize improvisation.
8. Merge, release, deployment, account creation, payment, deletion and scope expansion need explicit task authority.

## Parallel Independent AI Rule

- The same canonical TASK or REVIEW brief may be dispatched to any number of external AIs simultaneously.
- Every parallel worker must use the same frozen task/context revision and return a separately named artifact, for
  example `REVIEW-001-A`, `REVIEW-001-B` and `REVIEW-001-C`.
- Parallel workers must not edit the same review/output document or GitHub path. Shared briefs are read-only inputs;
  responses are isolated until manager synthesis.
- Agreement is not counted as a vote. The manager records common findings, contradictions, unique risks and evidence
  quality, then applies the task acceptance rules.
- One worker's PASS cannot erase another worker's supported critical finding. No number of AI opinions replaces required
  user approval, real evidence or a later gate.
- This external-AI permission does not broaden Codex sub-agent model permission under `DEC-0022`.

## Migration Boundary

The Drive workspace is active and the canonical planning package is published in the private GitHub repository
`xpike-dgm/motobakim-plan`. A fresh external AI can bootstrap through `/AGENTS.md` and
`00_CONTROL/MANAGER_START_HERE.md`; Drive evidence is indexed in `00_CONTROL/DRIVE_ARTIFACT_INDEX.md`. A task still
cannot be marked `READY` if any required truth exists only on the user's computer or in unpushed changes.
