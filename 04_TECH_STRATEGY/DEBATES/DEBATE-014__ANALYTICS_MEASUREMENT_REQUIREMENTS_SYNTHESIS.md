# DEBATE-014 — Analytics and Measurement Requirements Synthesis

Status: `ACTIVE / PRIMARY RESEARCH READY / NO-CODE / NO PROVIDER WINNER`

## Decision Question

Kavriva first release hangi ölçümleri gerçekten toplamalı, hangi verileri toplamamalı ve consumer product analytics,
Internal Operations operational analytics, reliability/observability ve protected audit sınırlarını nasıl ayırmalıdır?

Bu debate bir analytics provider seçmez. Amaç minimum measurement baseline, privacy/minimization sınırı, failure behavior,
owner-operability, safe cost ve clean-room exit gereksinimlerini eşit kanıtla araştırmaktır.

## Authority and Existing Directions

This topic is opened from already-recorded unresolved Phase-4 scope:
- `00_CONTROL/NEXT_ACTION.md` explicitly leaves analytics/measurement open;
- `00_CONTROL/CURRENT_STATE.md` leaves the analytics stack open;
- Phase-3 Internal Data & Content Operations requires coverage/data-quality/operational analytics;
- the user explicitly chose Analytics / Measurement Strategy as the next Phase-4 topic.

Existing working directions remain unchanged:
- planning is no-code;
- consumer mobile direction is Flutter, Android-first;
- Internal Operations is browser-based and online-authoritative;
- sensitive authority stays behind the Kavriva API;
- managed Supabase-centered backend is reversible Phase-4 direction only;
- consumer identity is local-first/account-light;
- selected-task compact offline packages remain the baseline;
- Kavriva owns technical truth, approval, immutable release, recall/suspension, package eligibility and final publication authority.

## Non-Negotiable Measurement Boundary

Measurement is an observation layer, not product authority.

Analytics events or telemetry must not become:
- technical truth or evidence of claim correctness;
- human approval;
- proof of physical task completion or safety readiness;
- protected security/audit receipt;
- entitlement authority;
- recall/suspension authority;
- canonical user/history/content state.

Analytics loss, delay, provider outage, quota exhaustion or consent denial must not disable the safe core path or the
negative safety path.

## Measurement Planes That Must Stay Distinct

1. Consumer product analytics: feature usage, funnel and experience measurement.
2. Internal Operations analytics: coverage, data quality, workflow and publication operations.
3. Reliability/observability: crash, performance and operational health.
4. Protected audit/security evidence: authoritative immutable evidence for privileged effects.
5. Store/platform aggregate signals: supporting release/distribution evidence.
6. Future business/entitlement measurement: commercial signals only when product policy later authorizes them.

One vendor may technically carry multiple planes, but semantic authority, retention and access boundaries must remain
explicit.

## Privacy and Data-Minimization Requirements

Research must cover:
- anonymous/account-light use before profile creation;
- purpose limitation and minimum-data collection;
- consent/opt-out and mobile platform tracking constraints;
- pseudonymous identifiers and identity merge/split;
- retention, deletion, export and derived aggregates;
- IP/location/device identifiers;
- motorcycle/variant context;
- free text, photos, media and high-cardinality payload risk;
- avoiding VIN/raw evidence/media collection merely for analytics convenience.

No legal conclusion is authorized in this debate; legal/privacy obligations must be sourced and any jurisdictional
uncertainty left explicit.

## Offline and Identity Requirements

The consumer app may work offline. Measurement options must address:
- delayed delivery;
- duplicate/retry and idempotency;
- clock skew;
- process death;
- versioned event semantics and old-client events;
- anonymous-to-profile transition;
- motorcycle switch/inactive motorcycle;
- partial upload and reconciliation.

Telemetry reconciliation must never rewrite canonical product records.

## Owner and Cost Requirements

The project is operated by one nontechnical owner with limited budget.

Every candidate must expose:
- free/capped path;
- mandatory adjunct cost;
- event-volume/cardinality/retention overage;
- incident and support burden;
- export cost and friction;
- clean-room replacement path;
- no-owner-debug recovery path.

Lower cost cannot weaken privacy, safety, audit, recovery or exit requirements.

## Equal Architecture Families

Research must compare at least:

A. Minimal Kavriva-owned first-party event/aggregate measurement.
B. Managed dedicated product analytics service.
C. Self-hostable/open-source analytics stack.
D. Split/hybrid: Kavriva-owned operational metrics + replaceable product analytics + provider-neutral observability.

Store/platform analytics may be treated as supporting reference signals, not canonical authority.

## Required Failure Scenarios

The research must apply all families to at least these scenarios:

1. Anonymous first use before account.
2. Anonymous measurements later linked to a profile without silent over-merge.
3. Motorcycle switch or inactive-motorcycle context.
4. Offline session uploads late with duplicate events and clock skew.
5. Analytics consent denied or revoked.
6. Analytics SDK/provider outage during active repair.
7. Critical recall while telemetry is unavailable.
8. Old client sends deprecated event semantics.
9. Provider quota or billing hold.
10. User export/delete request where derived aggregates exist.
11. Internal privileged action where analytics must not replace protected audit.
12. Coverage/data-quality metric derived from canonical records versus client events.
13. Cost spike caused by cardinality/log volume.
14. SDK causes startup, crash or performance regression.
15. Clean-room provider replacement.
16. Nontechnical owner incident path.

Each scenario/family row must state:
- expected state;
- safe hold;
- evidence;
- recovery owner;
- next action;
- privacy impact;
- cost impact;
- exit impact.

Unknown evidence remains `HELD`.

## Research Deliverable

Drive task:
- `CTX-P4-014 — ANALYTICS AND MEASUREMENT STRATEGY`
- `TASK-002 — DEBATE-014 ANALYTICS AND MEASUREMENT PRIMARY RESEARCH`

Expected research output must include:
- nontechnical executive summary;
- requirements trace;
- measurement-plane separation;
- data-minimization matrix;
- official-primary source ledger;
- equal candidate/family matrix;
- common failure matrix;
- retention/delete/export analysis;
- safe TCO;
- clean-room exit;
- unresolved evidence;
- mandatory / deferrable / optional / scale-triggered first-release measurement capabilities.

## Boundary

No code, pseudocode, event implementation schema, SDK install, provider account, trial, plan, purchase, deployment,
production setting, final KPI target, provider winner, ADR or Gate 4 -> 5 transition is authorized.

A research PASS later would mean only that the evidence package is sufficient for manager synthesis; it would not be a
production proof or owner approval.
