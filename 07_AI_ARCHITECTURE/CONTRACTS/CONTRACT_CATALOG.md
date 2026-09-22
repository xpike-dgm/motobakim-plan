# CONTRACT CATALOG

Status: PROPOSED (Group 2 names + Group 6 content pointers, reviewed PASS 2026-09-21; no contents authored here — each entry points at its binding source, which is the single truth)

Candidate cross-boundary interfaces. Names + owners fixed in Group 2; contents defined-by-reference below.
No contents, mechanisms, accounts, keys, purchases or code are selected here.

| Contract | Owner | Content defined by (single truth, not copied) |
|---|---|---|
| API authorization tuple contract | E3 | ADR-006 Decision 2 + F3.1.1 (reference, not redefinition) |
| Operation identity contract | E3 | ADR-006 Decision 4 + F3.1.2 |
| State-dictionary / negative-floor / epoch contract | E3 | ADR-006 Decisions 6–8 + F3.1.3/F3.5.1/F3.5.2 |
| Package manifest contract | E4 | ADR-009 R1/R2 + F4.1.1/F4.2.1 |
| Ledger operation contract | E4 | ADR-009 R5 + F4.5.1 |
| Audit event contract | E5 | ADR-005 event/meaning rules + F5.5.1/F5.5.3 |
| Release/promotion contract | E6 | ADR-003 R1–R4 + ADR-007 release rules + F6.2.1 |
| Task-pack contract | E10 | PACK_STANDARD.md 14 fields + F10.3.1 |
| Design-token contract | E10 | DESIGN_CONSISTENCY_AND_CHANGE.md + V10/REF-VISUAL-001 (tokens finalized per design gate) |

Recorded seam dispositions (references, not definitions): E9 proposes / E1 renders / E3 verifies (no E1↔E9
cycle); E2 consumes E8 outputs (E8 derives, E2 renders); E7 executes lane work vs E6 owns custody policy.
