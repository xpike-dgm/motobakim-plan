# ADR-010 — Internal Operations Web Framework, Render and Hosting

Status: APPROVED
Date: 2026-09-21
Owners: Kavriva AI manager (draft) / product owner (approval pending)

## Context

Phase-4 strategy (DEBATE-012, user-approved under `DEC-0039`, on the browser-based form locked by `DEC-0021`)
compared React/Next, Angular, Vue/Nuxt and Svelte/SvelteKit through requirements, official research, failure/TCO
analysis, two independent reviews, common task simulation, equivalence audit and component/render tie-breaks. All
four families stayed `0 PASS / 0 REJECT / 4 HELD` with no winner; the initial React-leader ordering was withdrawn
after review. CSR-first static artifact/CDN + Kavriva API stands as the conditional render/hosting hypothesis.
This ADR locks the render hypothesis, the product contract and the equal-evidence framework selection gate. It
selects no framework, version, component library, host, provider, account, plan or deployment, and authorizes no
code, purchase or production activation.

## Decision Drivers

- The internal surface needs no public SEO; a second web server, SSR cache, secrets, runtime and incident surface
  must earn its place instead of being assumed.
- Dense operational UI (queues, tables, diffs, provenance graphs, forms) must work for keyboard, screen readers,
  zoom, Turkish labels and degraded views — framework marketing never substitutes.
- Multi-AI screen production must stay visually and semantically consistent regardless of framework.
- Session/security, stale-state honesty, quarantine handling and clean exit decide before developer convenience.

## Options Considered

### Framework families (all HELD, none selected)

- **React + TypeScript (Vite/static, or Next where justified):** held on exact composition, component closure,
  cache/server boundary, upgrade and exit evidence. Early "conditional leader" language withdrawn — AI familiarity
  and popularity are not selection evidence.
- **Angular:** held on dense-component closure, toolchain/RxJS/major-upgrade behavior, AI task consistency and exit.
- **Vue + Nuxt:** held on module/support closure, render/cache boundary, dense/a11y package BOM and exit.
- **Svelte + SvelteKit:** held on support/major/adapter closure, dense package BOM, AI maintenance and exit.

### Render/hosting shapes

- **CSR-first static artifact/CDN + Kavriva API (conditional starting hypothesis, HELD):** smallest initial
  surface for an internal app without SEO — no second server, SSR cache or extra secret/runtime/incident plane.
  Opens only if session/CSRF/CORS/origin/XSS/CSP, private-cache behavior, stale/epoch/outcome handling,
  quarantine flow, artifact/API compatibility, privacy-safe logging, owner-readable incidents, bounded cost and
  clean-room exit all close; otherwise it holds without auto-promoting an alternative.
- **Same-origin server shell/BFF (need-specific):** only as an allowlisted transport/DTO adapter, never product
  authority or a second data owner.
- **Serverless/edge SSR, managed/portable Node container (need-specific):** route- or capability-specific
  exceptions and operational/exit challengers, opened only on concrete proven need.

## Decision

Kavriva locks the following for the Internal Operations web surface:

1. **Browser-based desktop-class workspace** (from `DEC-0021`); desktop packaging stays out unless the owner
   explicitly reopens it.
2. **Render hypothesis:** CSR-first static artifact/CDN + Kavriva API is the conditional default subject to the
   gate list above. BFF, SSR/edge, container and privileged service-worker behaviors are need-specific and held.
   A service worker is never by default a mutation, role, audit, recalled-data or status authority.
3. **Product contract (framework-independent):** browser, route guards, hidden buttons, framework server actions,
   caches, service workers and provider consoles are never product authority; every sensitive effect re-authorizes
   at the API on actor/session/epoch, tenant/scope, role/grant, exact resource version, operation fingerprint,
   idempotency and audit conditions; timeouts/loss yield `OUTCOME_UNKNOWN` with same-ID status lookup; files and
   external content enter only through private quarantine with digest/classification/lineage/scoped handles; dense
   views require bounded data plus keyboard/screen-reader paths and textual equivalents; the owner never repairs
   SQL, SSH, logs, queues, secrets, DNS/TLS or consoles.
4. **Equal-evidence framework gate:** the winner is chosen in implementation planning by running all four families
   through the identical fixture — exact dependency/lock/SBOM/license/support BOM; same heavy queue/table/diff/
   graph/form workload; real browser/keyboard/screen-reader/zoom/Turkish/degraded passes; session/role/epoch,
   CSRF/XSS/CSP, direct-path/BOLA/IDOR and response-loss fixtures; upload/quarantine/preview/archive/restore;
   major-upgrade, artifact, compatibility and guarded-recovery behavior; AI collision/design-consistency/no-owner
   handoff; normal/incident/upgrade/restore/exit cost; untouched-source clean-room rebuild with
   anti-resurrection. One candidate's hard fail never auto-crowns another; bypass, inaccessibility, stale
   authority, false success, quarantine bypass, effect-before-audit, incompatible rollback, owner repair,
   unbounded spend or unsafe exit marks the combination rejected-until-mitigated.
5. **Design/AI consistency gate:** framework choice never substitutes the canonical system — Phase-3
   workspace/screen architecture, shared design tokens and component contracts, state/copy/focus/density rules,
   file ownership, traceability graph, reviewers and visual-plus-semantic regression evidence bind every later web
   task through minimum context packs. An AI works from its task file plus explicit dependency/context packs only.

## Rationale

Choosing the smallest sufficient render shape first minimizes servers, secrets and incident planes for an audience
of one team's operators, while the equal-evidence gate prevents popularity or AI-familiarity from masquerading as
engineering proof. Locking the product contract independently of framework keeps all four candidates honestly
comparable later.

## Consequences

### Positive

- Minimal initial attack/operations surface if the static hypothesis passes its gates.
- Dense-UI, accessibility, security and exit requirements are specified before any framework commitment.
- Multi-AI visual/semantic consistency is enforced by contract, not by framework hope.

### Negative / Trade-offs

- No framework decision today: every web task waits on the later evidence fixture — schedule honesty over speed.
- CSR-first may fail its gates (session handling, stale-state, quarantine flow), forcing need-specific modes with
  their own evidence burden.
- Four-family fixture work costs planning effort until one candidate passes.

## Prohibited / Constrained Alternatives

- Framework selection by popularity, AI familiarity, component count or support-label marketing.
- BFF/SSR/edge/container/service-worker as defaults or automatic fallbacks.
- Service-worker offline mutation, role/audit/recalled-data/status caching.
- Cacheable mutation/status responses; stale/mixed frontend assets treated as success.
- Owner debugging of web stack, secrets, DNS or provider consoles.
- Any framework version, component library, host/provider, domain, plan, account, purchase, code, deployment or
  production activation — none authorized by this ADR.

## Revisit Triggers

- Real fixture evidence crowns a framework or disqualifies the static hypothesis — recorded by superseding ADR.
- Exact dependency BOMs, workload results, accessibility passes, security fixtures, upgrade behavior, cost lines
  and clean-room rebuild proof remain HELD for later implementation evidence.

## Related Documents

- `00_CONTROL/DECISION_LOG.md` — `DEC-0021`, `DEC-0039` (binding directions)
- `05_ADR/RECORDS/ADR-001__CANONICAL_DATA_AUTHORITY_AND_LOGICAL_BOUNDARIES.md`
- `05_ADR/RECORDS/ADR-002__PHYSICAL_BACKEND_PLATFORM_AND_API_AUTHORITY.md`
- `05_ADR/RECORDS/ADR-004__IDENTITY_AUTHORIZATION_SESSION_RECOVERY_AND_PRIVILEGED_ACTIVATION.md`
- `05_ADR/RECORDS/ADR-006__KAVRIVA_API_RUNTIME_AND_DURABLE_LONG_JOBS.md`
- `04_TECH_STRATEGY/DEBATES/DEBATE-012__JUDGE_SYNTHESIS.md`
- Downstream: ADR-011 (CMS authoring surface), ADR-012 (analytics instrumentation), ADR-015 (web task topology)

## Supersedes

None.

## Superseded By

None (APPROVED — owner approval 2026-09-21, see CHANGELOG).
