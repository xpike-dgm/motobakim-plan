# EVALUATION CRITERIA

Status: `ACTIVE WORKING CRITERIA — PHASE-4`

Bu kriterler onayli urun sentezi, Phase-3 ekran/state mimarisi ve Internal Data & Content
Operations gereksinimlerinden turetilmistir. Puanlar karar degil, karsilastirma aracidir.

## Mandatory Gates

Bir alternatif toplam puani yuksek olsa bile asagidaki kapilardan birini gecemiyorsa elenir veya
ancak ilgili eksigi kapatan acik bir mimari kosulla aday kalir:

1. **Safety/trust semantics:** fit, provenance, uncertainty, review, version, recall ve safe-recovery
   durumlari veri modelinde ve UI'da kayipsiz temsil edilebilmelidir.
2. **Offline correctness:** indirilen rehber/gorsel/guvenlik/progress/history yerelde kullanilabilmeli;
   stale/critical durum online re-check gerektirdiginde eski veri sessizce guncel sayilmamalidir.
3. **Non-destructive persistence:** account-light yerel kullanim ve local-to-profile gecisi silent
   loss/overwrite olmadan, conflict review ile yapilabilmelidir.
4. **Controlled publication:** Internal Operations icindeki edit/review/approval/publish ayrimi
   korunmali; `edit -> instantly live` yolu olmamalidir.
5. **Audit and least privilege:** onerme, inceleme, onay, yayin, rollback/recall ve rol degisikligi
   izlenebilir ve yetki kapsamli olmalidir.
6. **Platform viability:** Android ve iOS tuketici uygulamasi gercek cihazlarda, erisilebilirlik ve
   gerekli native yeteneklerle dagitilabilir olmalidir.

## Weighted Criteria — Consumer Mobile (100)

| Criterion | Weight | What must be demonstrated |
|---|---:|---|
| Offline data integrity and sync control | 20 | Local database, versioned content, retry/idempotency, conflict handling, stale/recall enforcement and testability. |
| Safety/trust product fidelity | 15 | Complex states, progressive disclosure, fit/readiness gates and no false-success behavior. |
| Native capability and lifecycle fit | 15 | File/media/camera/notifications/background transfer, secure storage, deep links and platform lifecycle escape hatches. |
| UX fidelity, accessibility and localization | 10 | Approved visual system, VoiceOver/TalkBack semantics, dynamic text, Turkish-first copy/units and platform conventions. |
| Maintainability and testability | 15 | Clear modular boundaries, deterministic state testing, migration testing, native integration tests and upgrade discipline. |
| Delivery capability and staffing risk | 10 | Learnability, hiring/ecosystem, debugging, CI/build/signing and AI-assisted implementation quality. |
| Performance and resource behavior | 5 | Startup, scroll/media behavior, storage, battery/network impact and low/mid device behavior. |
| Security and privacy | 5 | Secret/key handling, local sensitive data, dependency exposure and platform security controls. |
| Evolvability and lock-in | 5 | Native escape route, dependency portability, framework lifecycle and replacement cost. |

## Weighted Criteria — Internal Operations Surface (100)

| Criterion | Weight | What must be demonstrated |
|---|---:|---|
| Workflow and information-density fit | 20 | Dense tables, diffs, provenance graphs, queues, filters, bulk actions and multi-pane review. |
| Security, RBAC and auditability | 20 | Server-enforced authorization, separation of duties, attributable decisions, export/access audit and session controls. |
| Controlled release and recovery | 15 | Exact version review, publish status, partial failure, rollback/recall and impact traversal. |
| Deployment and operational simplicity | 15 | Central updates, observability, browser compatibility, incident response and low client drift. |
| Accessibility and operator efficiency | 10 | Keyboard/focus, assistive tech, non-color status, stable context and responsive practical layouts. |
| Data/tool integration | 10 | Document/media handling, import/export, search, analytics drill-through and API/event integration. |
| Maintainability and delivery capability | 5 | Testability, shared competencies, dependency/update burden and onboarding. |
| Cost, lock-in and future packaging | 5 | Hosting/distribution cost, optional desktop packaging and reversible architecture. |

## Scoring Discipline

- `1`: material mismatch or unmitigated critical risk.
- `2`: feasible only with high custom work/operational burden.
- `3`: viable with explicit trade-offs and normal mitigation.
- `4`: strong fit with bounded risks.
- `5`: demonstrated excellent fit; evidence required.

Scores are hypotheses until supported by a no-code evidence dossier against Kavriva acceptance scenarios. The dossier
uses official documentation, architecture/failure walkthroughs, known platform constraints, maintenance/TCO evidence
and independent review. Unknowns remain unknown; lack of evidence is not scored as strength. No executable prototype
or spike is permitted during this planning process.
