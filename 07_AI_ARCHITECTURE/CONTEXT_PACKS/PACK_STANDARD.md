# PACK STANDARD — 14 Mandatory Fields

Status: PROPOSED (Group 3, reviewed PASS 2026-09-21; per-field detail enrichment in Phase 7)

Every task pack carries exactly these fields (reconciled from ADR-015 Rule 5 + Addendum §4 + F10.3.1/C10.3;
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
