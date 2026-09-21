# USER FLOW CATALOG

Status: PROPOSED (E3 recorded 2026-09-21 after independent review PASS; rest pending)

| Flow ID | Feature | Actor | Trigger | Expected Outcome | Screens | Status |
|---|---|---|---|---|---|---|
| FL3.1.1 | F3.1.1 | Operator/system | Sensitive mutation request | ALLOW/DENY/HELD with reason before commit | — (API surface) | PROPOSED |
| FL3.1.2 | F3.1.2 | Operator | Lost response after submit | OUTCOME_UNKNOWN; same-ID lookup resolves, no blind retry | — (API surface) | PROPOSED |
| FL3.1.3 | F3.1.3 | Operator | State lookup/policy question | Allowed/blocked effects + retry/resolver per dictionary | — (API surface) | PROPOSED |
| FL3.1.4 | F3.1.4 | Security task | Audit sweep | Inventoried surfaces + negative-test results | — (API surface) | PROPOSED |
| FL3.2.1 | F3.2.1 | Operator | Create/version domain record | Versioned authority with stable identity; conflicts held | — (API surface) | PROPOSED |
| FL3.2.2 | F3.2.2 | Investigator | Audit question on an object | Full object-centered chain from protected evidence | — (API surface; investigator UI in E2) | PROPOSED |
| FL3.2.3 | F3.2.3 | Operator | Upload media batch | Quarantined; activated with lineage/digest/classification check | — (API surface) | PROPOSED |
| FL3.3.1 | F3.3.1 | Bounded AI task (no owner/billing/service_role) | Readiness check requested | Gap list + HELD provisioning; no account created | — (provider console, AI-operated) | PROPOSED |
| FL3.3.2 | F3.3.2 | Security task | Scheduled rotation window | Keys rotated/revoked/re-issued + audit event | — (API surface) | PROPOSED |
| FL3.4.1 | F3.4.1 | Operator/system | Long job submitted | ACCEPTED/QUEUED vs effect separated; checkpoint/heartbeat/cancel/drain/backlog/resolver visible | — (API surface) | PROPOSED |
| FL3.5.1 | F3.5.1 | System (commit path) | Any positive-effect commit | Current floors re-read; newer/equal floor wins; ties hold | — (API surface) | PROPOSED |
| FL3.5.2 | F3.5.2 | Security task | Suspected compromise | Epoch incremented; full edge list revoked end-to-end | — (API surface) | PROPOSED |
| FL3.6.1 | F3.6.1 | Recovery task | Scheduled drill | Restore executed; quarantine entered; checklist + evidence closed | — (API surface) | PROPOSED |
| FL3.6.2 | F3.6.2 | Recovery task | Exit rehearsal | Floors/truth preserved; gaps explicit PARTIAL/QUARANTINE | — (API surface) | PROPOSED |
| FL3.7.1 | F3.7.1 | System | HELD threshold policy evaluated (no numeric) | Owner-readable HELD; capability held not weakened | Owner-view | PROPOSED |
| FL3.8.1 | F3.8.1 | Release task | Promote staging artifact to production | Promotion HELD unless E6 artifact checks pass (reference) | — (API surface) | PROPOSED |
|---|---|---|---|---|---|---|
