# NEW MANAGER CHAT HANDOFF — KAVRIVA / MOTOBakim

Status: ACTIVE TRANSFER GUIDE
Date: 2026-09-17
Purpose: Seamless transfer of the main project-manager / architecture-manager role to a fresh ChatGPT conversation.

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
14. `03_DESIGN/KAVRIVA_FIRST_USE_VISUALS_01_REVIEW.md`
15. only then the minimum task-specific Phase-3 documents needed for the user's next request.

Do not bulk-read the entire repository unless needed.

## 3. Current Project Position

Current phase remains:
**Phase 3 — Design**

Gate 3 -> 4 has NOT passed.

Consumer-mobile design coverage is almost complete.

Approved working visual families include:
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

The user accepted the current working FAM-01 visual directions for:
- `SCR-001 First-Value Entry` — `Bugün ne yapmak istiyorsun?`
- `SCR-002 Add Motorcycle` — `Motosikletini ekle`
- `SCR-003 Motorcycle Identification & Variant Resolution` — `Bir ayrımı netleştirelim`

Canonical review record:
- `03_DESIGN/KAVRIVA_FIRST_USE_VISUALS_01_REVIEW.md`

Review status:
`PASS_PARTIAL / USER-ACCEPTED PARTIAL SET`

The review file records exact manager-chat image provenance and SHA-256 hashes for the three accepted screenshots.

Two Community-family screenshots were also shown in the same batch:
- `Toplulukla paylaş`
- `Katkın incelendi`

Per explicit user instruction, those screens were excluded from FAM-01 repository processing. Existing Community authority remains unchanged under `REF-COMMUNITY-001`.

## 5. Remaining Consumer-Mobile Visual Coverage

Only one new mobile visual context remains:

- `SCR-004 Fit Confirmation / Missing Distinction`

Already accepted as working FAM-01 directions:
- `SCR-001 First-Value Entry`
- `SCR-002 Add Motorcycle`
- `SCR-003 Motorcycle Identification & Variant Resolution`

`SCR-005 Garaj` is already covered by R01 / `REF-SHELL-001`.

A full FAM-01 reference must NOT be created until `SCR-004` is sufficiently covered and reviewed.

## 6. Required Internal Product Scope Before Gate 3 Review

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
1. complete remaining `SCR-004` consumer-mobile visual coverage,
2. targeted internal-operations requirements,
3. workflows / lifecycle,
4. platform-independent screen/workspace architecture,
5. Gate 3 readiness review,
6. Phase 4 technology-strategy comparison including mobile + internal operations,
7. only after platform strategy is selected should final platform-specific internal visual design be finalized.

## 7. User UX Preferences Learned During Phase 3

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

## 8. Core Product Safety / Trust Invariants to Preserve

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

## 9. Phase / Technology Boundary

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

## 10. Repository Write Discipline for the New Manager

When repository writes are authorized/appropriate:
- fetch the target file immediately before update,
- use the current blob SHA,
- never parallel-write the same path,
- update control documents after meaningful changes,
- do not silently alter APPROVED/LOCKED decisions,
- preserve raw handoff/evidence separately from manager synthesis/review,
- update `CURRENT_STATE`, `HANDOFF`, `REFERENCE_INDEX`, `SOURCE_OF_TRUTH`, `CHANGELOG`, `DOCUMENT_REGISTRY` only as warranted by the actual change.

## 11. Visual Attachment Reality

Many approved PNGs are not repository binaries. Repository documents preserve their semantic authority, but exact visual comparison may require the user to attach the relevant PNGs to the fresh conversation.

Do not claim to have visually inspected an image merely because a markdown handoff describes it.

For the current partial FAM-01 set, exact accepted-image identity is preserved through image dimensions + SHA-256 in `KAVRIVA_FIRST_USE_VISUALS_01_REVIEW.md`.

## 12. First Response Expected From the New Manager

After reading the required repository context, the new manager should respond briefly in Turkish along these lines:

- confirm the repository source-of-truth has been loaded,
- state that Phase 3 is still active,
- state that Community/FAM-09 is complete,
- state that FAM-01 has partial user acceptance for SCR-001–SCR-003 and only `SCR-004` remains,
- state that Internal Data & Content Operations remains a required pre-Gate-3 work item,
- do not start Gate 3 review or Phase 4 automatically.

The next task should follow the user's latest instruction. Do not ask them to restate the whole project.
