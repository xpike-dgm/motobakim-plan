# PACK STANDARD — 14 Mandatory Fields

Status: PROPOSED (Group 3, reviewed PASS 2026-09-21; per-field detail enrichment in Phase 7)

Every task pack carries exactly these fields (reconciled from ADR-015 Decision 5 + Addendum §4 + F10.3.1/C10.3;
T-E10-007 detail now closed):

1. objective (single, measurable);
2. outcome-link (user result it serves);
3. preconditions + completed dependencies;
4. mandatory reads (ADRs, contracts, rules, screens, modules);
5. allowed paths;
6. forbidden areas;
7. expected artifact changes;
8. acceptance + negative cases;
9. validation / architecture / integration checks to run;
10. migration / rollback needs;
11. responsive / accessibility rules;
12. evidence + handoff format;
13. graph-update records the task must write;
14. escalation rules.

Minimum-sufficient size discipline: resolve linked reads, never whole-project reads. Out-of-scope attempt
forces BLOCKED / change-request, never silent expansion.

## Field validity rules (what counts as present/valid)

1. objective: one measurable sentence; no "and/or" bundling.
2. outcome-link: names the user result + its requirement ID.
3. preconditions + completed deps: every Depends On ID listed with DONE status required.
4. mandatory reads: ID list + versions; no "whole project" entries.
5. allowed paths: explicit module/file scope, nothing implied.
6. forbidden areas: explicit; silence means forbidden by default.
7. expected changes: file/artifact list with change verbs.
8. acceptance + negative cases: at least one negative case per task.
9. validation/architecture/integration checks: named checks from Group-4 lists.
10. migration/rollback needs: stated even if "none", with reason.
11. responsive/accessibility rules: applicable rules cited or marked N/A with reason.
12. evidence + handoff format: evidence types + handoff template ID.
13. graph-update records: node IDs the task must write.
14. escalation rules: BLOCKED trigger + owner-option format reference.
