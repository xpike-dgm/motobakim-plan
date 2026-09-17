# NEW MANAGER CHAT HANDOFF — KAVRIVA / MOTOBakim

Status: ACTIVE TRANSFER GUIDE
Date: 2026-09-17
Purpose: Seamless transfer of the main project-manager / architecture-manager role to a fresh ChatGPT conversation because the prior conversation became too context-heavy.

## 1. Core Transfer Rule

The old conversation is NOT the source of truth.

Persistent project truth is:
`xpike-dgm/motobakim-plan`

The new manager must reconstruct context from repository control files and approved references. Do not ask the user to re-explain the whole project.

## 2. Mandatory Read Order in the New Manager Chat

Read before meaningful work:

1. `00_CONTROL/AI_START_HERE.md`
2. `00_CONTROL/CURRENT_STATE.md`
3. `00_CONTROL/SOURCE_OF_TRUTH.md`
4. `00_CONTROL/DECISION_LOG.md`
5. `00_CONTROL/OPEN_QUESTIONS.md`
6. `00_CONTROL/WORKFLOW_MAP.md`
7. `00_CONTROL/PHASE_GATES.md`
8. `00_CONTROL/DOCUMENT_REGISTRY.md`
9. `00_CONTROL/PROJECT_CHAT_INSTRUCTIONS.md`
10. `00_CONTROL/HANDOFF.md`
11. `00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`
12. `03_DESIGN/README.md`
13. `03_DESIGN/REFERENCE_INDEX.md`
14. only then the minimum task-specific Phase-3 documents needed for the user's next request.

Do not bulk-read the entire repository unless needed.

## 3. Current Project Position

Current phase remains:
**Phase 3 — Design**

Gate 3 -> 4 has NOT passed.

Consumer-mobile design coverage is almost complete.

Approved working visual families now include:
- `REF-SHELL-001` — R01–R05 root shell
- `REF-GUIDE-001` — D01–D05 Guide Discovery / Fit / Preparation
- `REF-ACTIVE-001` — E01–E05 Active Application / Safety / Recovery
- `REF-DIAG-001` — G01–G04 Diagnosis
- `REF-MAINT-001` — H01–H04 Maintenance / Reminder
- `REF-HISTORY-001` — I01–I06 History / Evidence / Trust
- `REF-LIFECYCLE-001` — J01–J05 Motorcycle Lifecycle / Entitlement
- `REF-PROFILE-001` — K01–K03 Profile / Collaboration
- `REF-COMMUNITY-001` — R05 + L01–L02 Community

Upstream approved authorities also include:
- Kavriva brand
- L05A logo direction
- U04 anchor UX
- V10 visual direction
- approved SCR-001–SCR-038 architecture
- five-tab navigation: `Garaj · Bakim · AI Usta · Gecmis · Topluluk`
- A1 Guided Split AI Usta root

## 4. What Was Just Completed

FAM-09 Community was completed.

Final manager-visible screens:
- `L01-SCR-035-Community-Contribution.png`
- `L02-SCR-036-Contribution-Review-Moderation-Appeal.png`

Main-manager QA:
`PASS_WITH_CONSTRAINTS`

Canonical:
- `03_DESIGN/COMMUNITY_VISUAL_REFERENCES.md`
- `03_DESIGN/KAVRIVA_COMMUNITY_VISUALS_01_HANDOFF.md`
- `03_DESIGN/KAVRIVA_COMMUNITY_VISUALS_REVIEW.md`
- `03_DESIGN/REFERENCE_INDEX.md` -> `REF-COMMUNITY-001`

Key constraints:
- community publication != official technical verification,
- optional photos != technical verification,
- private/public share scope remains explicit,
- withdrawal must not silently erase dependent provenance/history,
- L02 example date is fixture-only,
- L02 example request for part brand/model/source details is illustrative moderation feedback, not a universal contribution rule,
- no likes/followers/reputation/ranking/social-marketplace invention.

## 5. CRITICAL PAUSE — DO NOT AUTO-CONTINUE

The user's latest instruction before transfer was effectively:
- this Community step is sufficient,
- DO NOT prepare the next task prompt yet,
- the user has additional things to say first.

Therefore the fresh manager must NOT immediately generate a FAM-01 prompt.

First action after loading repository context:
**listen to and process the user's pending comments.**

Do not invent what those comments are.

Do not ask the user to repeat project history; only ask them to continue with the points they wanted to raise.

## 6. Remaining Consumer-Mobile Visual Coverage

Only 4 new mobile visual contexts remain:

FAM-01 — First Use / Motorcycle Context:
- `SCR-001 First-Value Entry`
- `SCR-002 Add Motorcycle`
- `SCR-003 Motorcycle Identification & Variant Resolution`
- `SCR-004 Fit Confirmation / Missing Distinction`

`SCR-005 Garaj` is already covered by R01 / `REF-SHELL-001`.

These 4 visuals are NOT authorized to start automatically at transfer time because of the pending user comments described above.

## 7. Required Internal Product Scope Before Gate 3 Review

The user explicitly approved an Internal Data & Content Operations capability with:
> `bu kesin yapılacak`

Canonical requirement:
`00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md`

It must eventually cover, at minimum:
- new motorcycle/model/year/variant research,
- missing/incomplete/stale/conflicting/not-reviewed data visibility,
- source/provenance management,
- controlled motorcycle/content editing,
- review/approval/versioning/rollback/recall,
- publishing approved content/data to the product data source used by mobile,
- coverage/data-quality/freshness visibility,
- operational analytics,
- audit/change history,
- requirement-level role/permission needs.

Important: exact implementation form is NOT decided.

Still OPEN:
- web app vs desktop app vs hybrid,
- database/CMS/search/index,
- API/sync/event architecture,
- exact roles/permissions implementation,
- automatic/manual publishing mechanics,
- analytics stack,
- AI/LLM/provider inside internal operations.

Do NOT design final internal UI based on an assumed platform yet.

Correct sequence is:
1. targeted internal-operations requirements,
2. workflows / lifecycle,
3. platform-independent screen/workspace architecture,
4. Gate 3 readiness review,
5. Phase 4 technology-strategy comparison including mobile + internal operations,
6. only after platform strategy is selected should final platform-specific internal visual design be finalized.

## 8. Planned Sequence After the User's Pending Comments

Unless the user's new comments change the plan:

1. Process pending user feedback / corrections.
2. If still appropriate, complete FAM-01 remaining 4 mobile visuals.
3. Complete Internal Data & Content Operations requirements + workflow + screen/workspace architecture addendum.
4. Perform Gate 3 -> 4 readiness review.
5. Move to Phase 4 only if the gate is explicitly satisfied/authorized.

Do not skip directly to technology selection.

## 9. User UX Preferences Learned During Phase 3

Treat these as strong design evidence, not universal immutable law:

- User strongly dislikes cluttered dashboard/card-stack layouts.
- `Accessible does not mean simultaneously prominent.`
- Text must be comfortably readable; do not use tiny/minimal type for aesthetic reasons.
- Avoid excessive explanation in the top third of the screen.
- Prefer one clear primary job and one dominant action.
- Progressive disclosure is preferred over showing every trust/safety/provenance detail at once.
- Avoid separate large cards for every semantic meaning.
- Do not make logo/brand art compete with the user's actual task.
- When generating multiple screen references, produce each screen as a separate image, not multiple phone pages inside one image.
- If a decorative/illustrative image area does not add task value, remove it.
- User prefers simple Turkish explanations rather than overly technical project-management language.

## 10. Core Product Safety / Trust Invariants to Preserve

Do not silently weaken these:

- No fabricated motorcycle-specific technical values.
- Correct task-relevant motorcycle/variant context must be established before variant-specific physical application.
- Unresolved critical fit/readiness/source conflict can block physical application while learning/reference may remain available.
- Diagnosis must support unresolved outcomes; no parts-cannon or fake certainty.
- Saved UI progress is not proof of current physical state.
- Material guide changes require physical-state remapping/revalidation.
- History preserves provenance, corrections, disputes and truthful partial/unresolved outcomes.
- Service/helper role is not verification authority.
- Basic historical truth/provenance/corrections/export/safety recovery cannot be retroactively locked by entitlement changes.
- Community experience remains separate from official guidance.
- Internal data/content publishing cannot be uncontrolled `edit -> instantly live`; review/version/recall rules must be respected.

## 11. Phase / Technology Boundary

Current Phase 3 must NOT decide:
- backend architecture,
- database technology,
- API/sync implementation,
- auth framework,
- mobile framework,
- AI model/provider,
- internal tool platform,
- final pricing/tier/quota,
- analytics stack.

These belong to controlled later work, especially Phase 4 and Phase 5 ADR.

## 12. Repository Write Discipline for the New Manager

When repository writes are authorized/appropriate:
- fetch the target file immediately before update,
- use the current blob SHA,
- never parallel-write the same path,
- update control documents after meaningful changes,
- do not silently alter APPROVED/LOCKED decisions,
- preserve raw handoff/evidence separately from manager synthesis/review,
- update `CURRENT_STATE`, `HANDOFF`, `REFERENCE_INDEX`, `SOURCE_OF_TRUTH`, `CHANGELOG`, `DOCUMENT_REGISTRY` only as warranted by the actual change.

## 13. Visual Attachment Reality

Many approved PNGs are not repository binaries. Repository documents preserve their semantic authority, but exact visual comparison may require the user to attach the relevant PNGs to the fresh conversation.

Do not claim to have visually inspected an image merely because a markdown handoff describes it.

If future visual work needs fidelity to L05A/V10/R01/etc., ask only for the minimum exact images required by that task.

## 14. First Response Expected From the New Manager

After reading the required repository context, the new manager should respond briefly in Turkish along these lines:

- confirm the repository source-of-truth has been loaded,
- state that Phase 3 is still active,
- state that Community/FAM-09 is complete and only four consumer-mobile First Use visuals remain,
- state that Internal Data & Content Operations remains a required pre-Gate-3 work item,
- explicitly say no new prompt will be generated yet because the user said they have points to discuss,
- invite the user to continue with those points.

Do NOT start FAM-01, Internal Operations design, Gate 3 review or Phase 4 in that first response.
