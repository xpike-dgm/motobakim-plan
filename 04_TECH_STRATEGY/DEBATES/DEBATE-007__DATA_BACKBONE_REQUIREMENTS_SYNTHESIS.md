# DEBATE-007 — DATA BACKBONE & LOGICAL SERVICE BOUNDARIES

## REQUIREMENTS SYNTHESIS

Status: DRAFT — PHASE-4 REQUIREMENTS SYNTHESIS / NO-CODE / ADR PENDING  
Date: 2026-09-18  
Decision level: Provider- ve implementation-bağımsız gereksinim sentezi  
Scope: Kavriva consumer mobile + browser-based Internal Data & Content Operations + bunların ortak veri, yetki, release, audit ve recovery omurgası

## 1. Amaç ve karar sınırı

Bu kayıt, Phase-3’te kullanıcı tarafından onaylanan Internal Data & Content Operations gereksinimlerini ve
DEBATE-002, DEBATE-003, DEBATE-004 ve DEBATE-005 yönlerini tek bir veri omurgası ve mantıksal sınırlar
gereksinimi halinde birleştirir. Amaç, sonraki teknoloji karşılaştırmasının yalnızca mobil client veya yalnızca
internal web üzerinden yapılmasını engelleyip bütün ürün sistemini aynı truth, safety ve recovery sözleşmesiyle
değerlendirmektir.

Bu belge:

- veri domainlerinin canonical sorumluluğunu,
- current state ile event/version history ayrımını,
- Internal Operations browser write/review/approve/release/publish yolunu,
- Flutter consumer-mobile read/sync/offline yolunu,
- user history, media, private/shared/community ve official content ayrımını,
- provenance, audit, recall, versioning, conflict ve idempotency gereksinimlerini,
- backup/restore/export/delete sınırlarını,
- authority boundary ve failure-state sözlüğünü,
- AI-operability, data-efficiency ve cost değerlendirme ölçütlerini,
- no-code S1–S36 kabul senaryolarını

tanımlar.

Bu belge bir veritabanı, CMS, API, event/queue, search/index, sync transport, identity provider, cloud,
analytics stack, AI/provider, storage format veya deployment provider seçmez. Mantıksal service boundary, mutlaka
ayrı deploy edilebilir servis demek değildir; ileride seçilecek yapı, bu sınırları ve sözleşmeleri koruyabildiğini
kanıtlamak zorundadır.

## 2. Authority, confirmed direction ve açık sınırlar

### 2.1 Girdiler

Bu sentez aşağıdaki repository truth kayıtlarından türetilmiştir:

- 00_CONTROL/AI_START_HERE.md
- 00_CONTROL/CURRENT_STATE.md
- 00_CONTROL/SOURCE_OF_TRUTH.md
- 00_CONTROL/DECISION_LOG.md
- 00_CONTROL/OPEN_QUESTIONS.md
- 00_CONTROL/PROJECT_CHAT_INSTRUCTIONS.md
- 00_CONTROL/PROJECT_SCOPE_ADDENDUM_INTERNAL_DATA_OPERATIONS.md
- 00_CONTROL/PROJECT_SCOPE_ADDENDUM_AI_NATIVE_EXECUTION_SYSTEM.md
- 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md
- 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REVIEW.md
- 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKFLOW_LIFECYCLE.md
- 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKSPACE_ARCHITECTURE.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-002__OFFLINE_SAFETY_RECALL_CLIENT_COMPATIBILITY.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-004__IDENTITY_AUTHORIZATION_AUDIT_UNTRUSTED_INGESTION.md
- 04_TECH_STRATEGY/DEBATES/DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md
- DEBATE-002, 003, 004 ve 005’in iki bağımsız adversarial review kaydı

### 2.2 Kullanıcı tarafından onaylanmış çalışma yönleri

| Yön | Bu sentezdeki bağlayıcı sonuç |
|---|---|
| Internal Data & Content Operations | Browser-based client formu; authoritative approve, publish, recall, role/policy ve audit mutation’ları online/server-authoritative olmalı. |
| Consumer mobile | Flutter, Phase-4 çalışma yönüdür; Phase-5 ADR, gerçek build/device/release kanıtı ve provider seçimi henüz yoktur. |
| Offline | Risk-tiered, bounded, release-bound; seçili motorcycle/task ile sınırlı; compact safety/application/recovery core zorunlu, ağır media opsiyonel. |
| Approval/publication | Exact immutable approved snapshot + closed release candidate + tek koşullu authoritative transition; partial/failed/unknown görünür. |
| Emergency suspension | Normal yayın yolundan failure-domain seviyesinde bağımsızlığı kanıtlanacak, dar negative authority; replacement technical truth üretemez. |
| Authorization | Understandable base roles + server-authoritative scoped/contextual policy; deny-by-default; commit-time reauthorization; high-consequence separation of duties. |
| Ingestion | Upload/URL materyali quarantine-first, layered validation ve isolated untrusted preview; scan/render/extraction teknik doğruluk değildir. |
| Supply chain | Binary, web, backend/data, migration, content, configuration ve emergency control ayrı release authorities; exact immutable artifact ve artifact-bound evidence. |
| AI-operated project | Obsidian-compatible graph, contract-governed task-addressable boundary, minimum sufficient context pack, no-code simulation ve closure evidence zorunludur. |
| Cost | Tek owner ve limited budget; ücretli servis/provider/device/expert varsayılamaz. Zorunlu güvence karşılanamıyorsa capability/release HELD kalır. |

### 2.3 Açık bırakılan kararlar

Şunlar bu kayıtta bilinçli olarak açık kalır:

- veri modelinin fiziksel temsili, database/CMS/search/index ve media storage seçimi;
- backend/API/sync/event/queue/cache/CDN topolojisi;
- identity/authentication/policy implementation ve exact role/quorum matrix’i;
- numeric freshness/offline windows, risk taxonomy, client support window ve RTO/RPO;
- automatic/manual scheduling, publication transport ve reach-back/notification mekanikleri;
- audit, analytics, retention, legal/privacy, export/delete ve backup implementation;
- AI/LLM/OCR/provider, data boundary, model versioning ve cost;
- browser frontend, Flutter package/plugin ve diğer provider seçimleri;
- herhangi bir OTA/runtime code-update channel.

Bu açıklar bir gereksinim boşluğu olarak gizlenemez; sonraki tartışmada OPEN, HELD veya UNVERIFIED olarak taşınır.

## 3. Sentez tezi: tek bir “current data” tablosu truth değildir

Kavriva’nın veri omurgası, her şeyi tek bir mutable current record’a indirgeyen bir yapı olamaz. En az üç
birbirinden ayrılmış truth plane ve bunlardan türeyen projections bulunur:

1. **Canonical product truth:** motorcycle/model/year/variant/applicability, technical claim, guide/content,
   source/evidence/provenance ve approved/published release anlamı.
2. **User-owned operational truth:** selected motorcycle context, active work, confirmations, notes, photos,
   completed/partial/unresolved history, corrections/disputes ve paylaşım ilişkileri.
3. **Authority/control truth:** identity, scoped policy, competence/delegation, approval/publication operation,
   release/suspension generations, audit ve restore/reconciliation state.
4. **Derived projections:** search/index, coverage/quality analytics, read models, caches, offline packages ve
   UI projections. Bunlar hızlı veya kısmi olabilir fakat canonical truth’i yeniden yazamaz veya authority
   üretemez.

“Single source of truth” bu projede tek fiziksel store anlamına gelmez. Her domain için tek canonical owner,
cross-domain link, version/generation ve audit bağı bulunur. İki domain’in aynı anlamı bağımsızca sahiplenmesine
izin verilmez.

## 4. Canonical truth sözleşmesi

### 4.1 Truth plane matrisi

| Plane | Canonical anlam | Tüketenler | Canonical olmayan şeyler |
|---|---|---|---|
| Scope/applicability | Make/model/year/trim/engine/feature/modification ve hangi claim/guide’ın hangi varyanta uyduğu | Internal research/editor/reviewer, mobile fit/readiness | Yakın varyant adı, generated motorcycle görseli, kullanıcı varsayımı |
| Source/evidence/provenance | Source identity/type, evidence, applicability, date, actor, access/current-evaluation/historical-use ilişkisi | Claim/content/review/recall/audit | Scanner sonucu, OCR çıktısı, community publication tek başına |
| Claim/technical content | Bounded technical statement, current state, uncertainty/dispute ve event history | Guide authoring, review, mobile eligible release | Boş olmayan alan, KPI, AI önerisi, local cache |
| Guide/content version | İnsan-okunur teaching/application adımları, prerequisite/warning/outcome ve claim dependencies | Release, mobile, history/recovery | Draft, unreviewed render, mutable external URL |
| Approval/release/eligibility | Exact reviewed snapshot, release manifest, client capability, freshness, suspension/revocation ve current eligibility | Mobile sync/read, internal release/recall | Store update promptu, push receipt, old signed cache |
| User work/history | Gerçek kullanıcının ne yaptığı/neyi gördüğü, hangi guide version’ını kullandığı, evidence ve outcome | User history, correction reach-back, collaboration | Official technical truth, service role claim, “completed” UI optimism |
| Authority/audit | Kim, hangi scope/role/policy/session ile ne yaptı; ordered protected event chain | Security/audit/investigation/recovery | Client clock, hidden button, mutable log row |
| Projection/cache/analytics | Arama, queue, KPI, read model ve offline erişim için türetilmiş görünüm | Browser/mobile/operations | Positive eligibility, approval, recall, official claim state |

### 4.2 Her canonical object için minimum identity ve state

İlerideki fiziksel modelden bağımsız olarak her önemli object şu anlamları taşıyabilmelidir:

- stable object identity ve object type;
- make/model/year/variant/modification veya user/content scope;
- classification: private, shared, community, official, quarantine veya protected audit;
- current state ve state reason;
- immutable version/revision veya authority generation;
- source/evidence/provenance links;
- dependent/used-by links;
- actor, role/scope, operation ve server-ordered event links;
- freshness/expiry/review condition varsa bunun açık durumu;
- current consumer eligibility ile historical-use ilişkisinin ayrılığı;
- superseded/withdrawn/recalled/deleted/retained anlamı;
- owner, resolver veya next action gereken operasyonel kayıt.

Exact field adları ve serialization formatı ileride kararlaştırılır; anlamlardan biri eksikse model acceptance
barını karşılamaz.

### 4.3 Current state ile history birlikte ama ayrı

Current claim/content meaning, kullanıcının şu an göreceği state’i sağlar. Event/version history ise nasıl ve neden
bu state’e gelindiğini sağlar. Aşağıdaki olaylar silent overwrite değildir:

- source/evidence add, withdrawal, inaccessible veya supersession;
- claim conflict, correction, dispute resolution veya insufficient-evidence;
- edit, request-changes, review, approval, publication, rollback ve recall;
- role/access/delegation/competence change;
- user record correction, transfer, revoke veya delete/retention event’i;
- restore, migration, retry, partial veya outcome-unknown operation.

Bir current view, ayrıntıyı gizlemeyi seçebilir; ancak history/provenance/audit erişimini yok edemez ve current
state’i event history gibi sunamaz.

### 4.4 Multi-axis state kuralı

Tek bir “verified/ready/complete” badge yerine en az şu eksenler bağımsız değerlendirilebilir olmalıdır:

- workflow state: draft, in review, approved, published, changes requested;
- evidence/provenance state: sufficient, incomplete, stale, withdrawn, disputed, inaccessible;
- applicability state: matched, uncertain, unsupported, conflicting, not applicable;
- release state: prepared, current, superseded, partial, failed, outcome unknown;
- eligibility state: eligible, held, suspended/recalled, reference-only, historical-only;
- sync/delivery state: local-only, pending, valid package, stale, mixed/corrupt, reconciled;
- classification/access state: private, shared, community, official, quarantine, protected;
- lifecycle state: active, inactive, transferred, archived, deleted-by-policy.

Unknown, unresolved, not-applicable, partial ve insufficient-evidence gerçek sonuçlardır; form completeness adına
bir değere zorlanamaz.

## 5. Veri domainleri ve canonical sorumluluk

Bu tablo, “hangi domain neyi sahiplenir ve neyi sahiplenemez?” sorusunun Phase-4 minimum cevabıdır. “Owner”
mantıksal sorumluluktur; fiziksel takım/servis/database seçimi değildir.

| ID / domain | Canonical responsibility | Kontrollü writes | Asla authority olmaması gerekenler |
|---|---|---|---|
| D01 Motorcycle scope & applicability | Make/model/year/variant, trim/engine/feature distinction, modification, duplicate/nearby scope, fit uncertainty | Research/refinement, recorded split/merge, applicability decision | Nearby variant inference, generated image, user assertion |
| D02 Coverage & research | Research item, scope/domain gap, reason, consequence, owner, queue/priority, expected evidence | Open/assign/pause/return/prioritize research; gap reason updates | KPI’nin teknik doğruluk kararı, empty=not applicable |
| D03 Source, evidence & provenance | Source identity/type, captured evidence, scope/date/actor, access/status, claim/content/dependent links, provenance events | Add/link/qualify/withdraw/mark stale/inaccessible/disputed; protected lineage | Upload success, scan result, role title, community acceptance |
| D04 Claims & technical records | Bounded technical claims, measurements, prerequisites, warnings, expected outcomes, current claim state and claim history | Draft/change/split/narrow/supersede through controlled workflow | Edit itself, AI extraction, service attribution, metric |
| D05 Guide/content & derived assets | Guide step/content unit, teaching/application meaning, claim dependencies, localized/rendered/media inputs | Draft, validation, versioning, evidence-linked correction | Mutable external URL, unreviewed transform, generated visual as fit/diagnosis proof |
| D06 Review, approval & decision | Review packet, validation/conflict findings, bounded decision, reviewer competence/scope, approval conditions/expiry | Request changes, reject, leave unresolved, approve exact snapshot | Self-approval, publication by edit, approval extension to new scope |
| D07 Release, publication & suspension | Release candidate, exact included snapshots/dependencies, publication operation, current release, suspension/recall generation | Preflight, guarded publish, partial/failure/unknown reconciliation, negative suspend, new rollback/re-entry | Draft/live shortcut, old backup, normal config clearing suspension |
| D08 Consumer capability, sync & offline package | Minimal envelope, client capability, task/motorcycle package manifest, freshness/eligibility/reconciliation state, safe-recovery closure | Read/download/verify/reconcile/evict/refresh; local user-work transfer | Local cache as approval, push as recall truth, full-library mirror |
| D09 User motorcycle/lifecycle/entitlement | User’s selected motorcycle contexts, active/inactive/transfer state, entitlement constraints and historical access rules | User/authorized collaborator context changes with attribution and conflict review | Entitlement deleting history, inactive state blocking safety reach-back |
| D10 User work, history & corrections | Active work, last definite step, notes/evidence references, completion/partial/unresolved/safe-stop outcome, guide version used, corrections/disputes | Local capture, controlled transfer/merge/review, user correction; no silent overwrite | “Saved progress” as current physical proof, internal edit of user event |
| D11 Media & artifact classification | Official instructional media, essential/optional media, user media, community attachments, quarantine originals/derivatives and transformation lineage | Upload/process/classify/link/withdraw/retain under scope; separate optional media path | File name/digest alone as technical truth, public exposure of private media |
| D12 Private/shared/community | Visibility, consent/opt-in, invitation/permission, attribution, moderation, withdrawal and dependent provenance | Share/revoke/moderate/appeal/withdraw with events | Community publication = official verification; revoke = history erasure |
| D13 Identity, policy & competence | Account/session assurance, roles/capabilities, scoped policy version, competence, delegation, security epoch | Versioned policy/access/competence/recovery changes, commit-time reauthorization | Browser role cache, hidden button, admin superpower, service account human approval |
| D14 Audit, incident & operations analytics | Protected ordered events, operation/release/recall impact graph, coverage/quality/workflow metrics and drill-down | Append protected events; derive metrics; open research/correction/incident work | Analytics overwriting claims, unprotected mutable audit, opaque quality score |
| D15 Backup, restore, export, delete & retention | Recovery snapshots, restore/quarantine/reconciliation state, export disclosure records, deletion/retention impact and legal holds | Controlled restore/export/delete/retention operations with scope and audit | Backup as current authority, export link as retractable disclosure, delete of independent provenance |

Domain boundaries must allow bidirectional traversal of relationships without allowing a derived projection to
become an unreviewed writer. Örneğin source/evidence’den dependent claims/guides/active work’e ve recall case’den
affected variants/releases/history’ye gidilebilmelidir.

## 6. Logical service boundaries

### 6.1 Boundary tanımı

Her boundary için public contract; identity, scope, state, version, classification, allowed action, result state,
failure reason ve audit reference anlamlarını taşır. Internal implementation, table split veya network topology
bu belgenin konusu değildir.

| Boundary | Public responsibility | Requires/returns | Must not do |
|---|---|---|---|
| LB-01 Identity & Scoped Policy | Authenticate actor/session, evaluate role + exact action/resource/scope/state/consequence/independence, return allow/deny/hold reason | Security epoch, policy/grant version, competence/delegation, release/suspension generation where relevant | Trust client role, grant implicit competence, make history retroactively valid |
| LB-02 Motorcycle Scope & Applicability | Resolve canonical motorcycle/model/year/variant/modification and fit relationships | Scope identity, distinguishing evidence, uncertainty, dependent objects | Merge nearby variant by guess or let a guide bypass unresolved fit |
| LB-03 Source/Evidence & Provenance | Register source/evidence, quarantine status, applicability and dependent lineage | Captured artifact identity, actor/date/status, current-evaluation vs historical-use links | Treat scan/OCR/community as verification or expose untrusted originals through operations origin |
| LB-04 Claim & Content Authoring | Create bounded draft claims, records, guide steps and dependencies with explicit unknown/partial states | Current meaning, proposed diff, evidence, affected dependents, validation findings | Mutate approved snapshot or publish by editing |
| LB-05 Validation/Conflict/Review | Detect gaps/conflicts, present side-by-side evidence and record bounded human decision | Required competence/independence, exact scope/version, rationale, conditions/expiry | Fabricate winner/confidence or force all-or-nothing completeness |
| LB-06 Approval/Release/Publication | Freeze approved meaning, assemble closed release, guarded publish and observe result | Exact snapshot/artifact digests, dependencies, compatibility, generation tuple, operation status | Rebuild/alter approved meaning silently, accept mixed release as current |
| LB-07 Suspension/Recall & Impact | Place narrow negative hold, compute dependency/interaction-depth impact, route correction/re-entry | Scope lattice, reason/severity, affected release/package/work, safe recovery | Create replacement truth, silently unsuspend, let old publish clear a newer hold |
| LB-08 Consumer Read/Sync/Eligibility | Deliver eligible immutable content envelope and reconcile client/package state | Release identity, capability, applicability, freshness, suspension/revocation, recovery closure | Let cache/push/store prompt/local clock grant positive application authority |
| LB-09 User Work/History | Capture user-owned local/server work and preserve used-version/outcome/evidence continuity | User/motorcycle context, event sequence, media classification, transfer/conflict state | Write official technical truth or present saved confirmation as current proof |
| LB-10 Media/Classification | Keep official/private/shared/community/quarantine/protected media separate and trace transformations | Classification, consent, retention, original/derived lineage, size/essentiality | Serve active/untrusted media in privileged origin or infer public consent |
| LB-11 Community | Manage explicit opt-in community contribution, moderation, appeal and withdrawal | Community scope, actor attribution, moderation reason, dependent provenance | Turn publication/photo/moderation into official technical-guide verification |
| LB-12 Audit & Operations Analytics | Record protected events and derive explainable coverage/quality/workflow signals with drill-down | Actor/role/scope, server order, operation/version, reason, old/new state, impact links | Erase own evidence, hide unknown counts, auto-publish from metric |
| LB-13 Recovery/Export/Delete/Retention | Orchestrate restore quarantine, data-preserving migration, authorized disclosure and scoped deletion | Backup generation, revocation floor, audit continuity, classification, recipient/purpose, legal hold | Restore old positive authority, retract copied export, delete independent history |
| LB-14 AI Assistance | Extract/propose/classify/prioritize with complete input/transformation provenance | Input/derived identity, model/config/provider boundary, uncertainty, human review requirement | Invoke tools from hostile content, change policy/classification, approve or verify |

### 6.2 Dependency direction

Minimum logical direction:

- LB-01 guards every sensitive read/export/mutation; UI visibility is never a substitute.
- LB-02 is upstream of applicability decisions in LB-03, LB-04, LB-05, LB-06 ve LB-08.
- LB-03 supplies evidence/provenance to claims/content/review/release and receives withdrawal/correction events.
- LB-04 produces mutable drafts; LB-05 may accept only a bounded, attributable proposal.
- LB-06 consumes approved snapshots and closed dependencies; LB-07 can negatively fence LB-06.
- LB-06/LB-07 supply consumer eligibility context to LB-08; LB-08 cannot write positive authority back.
- LB-09 records the release/version actually used, but cannot change LB-04/LB-06 technical meaning.
- LB-10 classification cuts across every content, user, community, export, AI and audit edge.
- LB-12 observes all material transitions; LB-14 may propose to LB-03/LB-04/LB-05 but never bypasses them.
- LB-13 can restore or disclose data only through current policy, classification, audit and generation checks.

Cycles are only controlled references/events; uncontrolled direct cross-domain writes, hidden shadow truth and
last-write-wins merge are not acceptable.

## 7. Browser-based Internal Operations: authoritative write/review/publish yolu

### 7.1 End-to-end lifecycle

Conceptual path:

Research requested → Research active → Evidence pending veya Draft → Validation → Conflict review (gerekiyorsa)
→ In human review → Approved exact snapshot → Release candidate → Guarded publication → Delivery observed /
Consumer reconciled → Monitor → Correction / Supersession / Rollback / Suspension / Recall → Re-review and re-publish

Her geçişte object scope, current state, reason, owner/role, evidence links, dependency closure ve next action
taşınır. “Workspace’i aç” context handoff değildir; scope/state/provenance/impact kaybolmadan taşınmalıdır.

### 7.2 Mutation contract

Browser, authoritative service’e şu anlamları gönderir:

- actor/session/security epoch ve requested capability;
- exact object/scope/classification/action;
- current resource/version/release/suspension expectation;
- review/approval/dependency generations;
- one durable operation identity;
- intended effect, reason ve request validity context.

Authoritative service:

1. current policy, role, competence, independence, classification ve security epoch’i yeniden değerlendirir;
2. exact version/dependency/release/suspension conditions’ı commit anında yeniden kontrol eder;
3. minimum protected audit evidence’i effect öncesinde hazırlar;
4. sonucu server time/order ile kaydeder;
5. aynı operation identity’nin retry’sinde aynı intended effect/result’ı döndürür;
6. browser response kaybolursa operation status lookup ile reconcile edilmesini sağlar.

Stale tab, revoked session, old approval, changed current release veya changed suspension/revocation generation
mutasyonu deny/hold eder. Browser cache, service worker, optimistic UI veya hidden button hiçbir zaman authority
değildir.

### 7.3 Review ve approval

Review packet en az şu bağlamı içerir:

- exact motorcycle/applicability scope;
- current meaning ve proposed diff;
- source/evidence/provenance ve withdrawal/stale/conflict durumu;
- validation/gap findings;
- dependent guide/record/release/active-work impact;
- consequence tier, required competence ve independence;
- unresolved uncertainty, conditions, expiry/re-review trigger;
- proposer/reviewer/approver identity, role/scope ve audit lineage.

Approval yalnızca exact immutable snapshot, evidence set, applicability, dependency set ve decision record için
geçerlidir. Sonraki edit yeni review gerektirir. Bounded approval, başka bir varyantı, claim’i, safety meaning’i
veya procedure order’ını sessizce kapsayamaz.

High-consequence official content için proposal/edit ≠ domain review ≠ safety/technical approval ≠ publication.
Bağımsız competence yoksa çalışma HELD kalır; shared account, admin abuse veya emergency path self-approval
fallback’i değildir.

### 7.4 Release ve publication

Release candidate closed manifest olarak şunları kapsar:

- exact approved versions/artifact identities;
- claim/content/media/localization/template/transform/default/flag ve external-resource meaning closure;
- source/evidence/provenance/classification;
- API/schema/client capability compatibility;
- migration/data state ve rollback/recovery planı;
- task/motorcycle-scoped offline package ve tüm reachable physical state’ler için safe-stop/recovery closure;
- current release generation + suspension/revocation generation;
- approval, verifier, promotion, signature ve audit operation identities.

Minimum conceptual states:

PREPARED → AUTHORIZED → PUBLISHING → AUTHORITATIVE_CURRENT → DELIVERY_OBSERVED →
CONSUMER_RECONCILED

HELD, FAILED, OUTCOME_UNKNOWN, PARTIAL_PROPAGATION, SUPERSEDED, SUSPENDED ve RECALL_OPEN ayrı state’lerdir.
AUTHORITATIVE_CURRENT anlık global delivery demek değildir; CONSUMER_RECONCILED offline client’in gerçekten
reconciled olduğunu da garanti etmez.

### 7.5 Internal browser için izin verilen/vermeyen işlemler

| İşlem | Baseline |
|---|---|
| Read-only coverage/provenance/history/analytics | Authorized scope ile; stale/cache state açıkça non-authoritative |
| Draft create/edit/save-partial | Scope/policy ile; incomplete/unknown/partial korunur |
| Validation/conflict/review/approve | Online current authorization + version/independence + protected audit |
| Publish/release/rollback/recall/suspend | Online guarded operation + idempotency + current generation fence |
| Role/policy/competence/recovery change | Ayrı protected versioned workflow + step-up/dual-control policy; exact details open |
| Offline approve/publish/recall/role/audit mutation | Baseline olarak yasak; offline draft isteği ayrıca karar gerektirir |
| Network timeout sonrası retry | Blind retry yasak; OUTCOME_UNKNOWN → status lookup/reconciliation |

## 8. Flutter consumer-mobile: read/sync/offline yolu

Flutter, kullanıcı tarafından onaylanan consumer-mobile working direction’dir; data/provenance/release truth
Flutter presentation code içine gömülmemelidir. Bu bölüm Flutter API veya plugin seçmez; herhangi bir client
implementation aynı data contract ve safety semantics’i taşıyabilmelidir.

### 8.1 Read envelope

Mobile’ın content/data kullanmadan önce anlayabildiği minimum immutable envelope:

- release/content identity ve integrity;
- motorcycle/model/year/variant/modification applicability;
- required client capability/contract;
- current eligibility/freshness state;
- suspension/recall/revocation meaning ve monotonic ordering;
- dependencies/recovery closure status;
- last authoritative reconciliation context;
- normal application ile teaching/history/safe-recovery ayrımı;
- classification/visibility ve relevant provenance/evidence level.

Unknown safety-critical field veya unmet capability positive application authority vermez; affected flow fail-closed
olur. Teaching/history/safe recovery yalnızca client critical meaning’i doğru temsil edebiliyorsa devam eder.

### 8.2 Package boundary ve layer’lar

Default offline package yalnızca:

- selected motorcycle/model/year/variant ve applicable modifications;
- selected guide/task;
- exact approved release/client capability;
- guide’ın oluşturabileceği reachable physical states;
- minimum complete task-specific safe-stop/recovery closure

için hazırlanır. Unrelated motorcycles, full catalog, unrelated guides ve unused media pakete girmez.

| Layer | Kural |
|---|---|
| Safety/application core | Zorunlu: fit/version/status, compact steps/text, critical warnings/checks, outcome states ve complete safe-stop/recovery |
| Essential instructional media | Guide güvenli anlaşılmak için gerçekten zorunluysa; step-linked, verified minimum media |
| Enhanced media | Optional/on-demand: high-resolution, galleries, video ve nonessential teaching; boyut önceden görünür |
| Personal work context | Küçük/persistent: progress, definite step, notes, evidence refs, used guide version; user media ayrı policy |

Small but incomplete, mixed-version veya dependency’si eksik package “data-efficient success” değildir; ineligible
sayılır.

### 8.3 Eligibility, sync ve resume

- Risk unknown/unclassified ise high-consequence varsayılır; low-risk’e sessizce düşürülemez.
- Guide/package, dependent claim/step/prerequisite’ların en yüksek consequence’ını taşır.
- Freshness expired, critical status unknown, fit/readiness unresolved, recall known veya capability missing ise
  normal new/next physical progression hold/closed olur.
- Teaching, provenance, history, evidence capture ve task-specific safe-stop/recovery, güvenli olduğu ölçüde
  korunur; safe recovery unrelated/new task’a gizli bypass olamaz.
- App launch, foreground return, network return, new application ve gerekli resume boundary’lerinde authoritative
  reconciliation yapılır. Push/background delivery yalnız hint’tir.
- Resume, motorcycle/guide version/last definite step/notes/photos/context’i geri getirir; old confirmation’ı
  current physical proof yapmaz.
- Material guide change: stop → reason/change explanation → current physical-state capture/revalidation → safe
  remap varsa continue, yoksa recovery/teaching/safe-stop.
- Known recall/suspension, unexpired local cache’in positive authority’sini override eder.
- Restored/cloned cache/reference, current eligibility kurulana kadar derived/non-authoritative’tir.
- Wall-clock rollback/forward, local monotonic clock across reboot/restore veya store update prompt eligibility
  uzatamaz.

### 8.4 User-owned offline writes

User active work/history/evidence capture account-light/local use ile başlayabilir. Bu write’lar official
technical truth’e dönüşmez. Transfer/sync contract en az şu state’leri ifade eder:

local-only → pending-transfer → accepted/synced veya conflict-review / failed / outcome-unknown

Conflict, last-write-wins ile sessizce çözülmez. User actor, used guide version, event order, old/new meaning,
media/provenance ve transfer attempt korunur. Profile’a geçişte scope preview, no-silent-loss, no-silent-overwrite
ve conflict review gerekir. Exact local/server authority split ve merge policy sonraki karardır.

## 9. User history, media ve private/shared/community ayrımı

### 9.1 Classification matrisi

| Sınıf | Default owner/visibility | Resmî truth’e etkisi | Withdrawal/delete etkisi |
|---|---|---|---|
| Official technical/content | Controlled product/review authority; consumer-eligible only after release | Human review + approved release olmadan etkilemez | Recall/correction current use’ı kısıtlar; history/provenance silinmez |
| User private | User; default private | User experience/evidence context olabilir; official claim değildir | User control/export/delete policy ile; independent official provenance silinmez |
| Shared motorcycle | Explicit invitation/permission; actor attribution | Shared history/collaboration context; official verification değildir | Revoke future access’i etkiler; prior attribution/evidence/history korunur |
| Community | Explicit opt-in public/private scope; moderation status | Community visibility/source input olabilir; publication/acceptance official guide değildir | Withdrawal dependent claim review’i tetikler; history/provenance silinmez |
| Quarantine/untrusted | Restricted operations/security scope | Scan/render/extract yalnız processing state; technical truth değildir | Original/derived lineage, owner, reason, retention korunur |
| Protected audit | Authorized investigator/security scope | Accountability/control truth | Retention/legal hold ve protected custody ile; actor kendi event’ini silemez |

Unknown/mixed classification, derivative preview/extraction/AI/audit reference/export dahil, en restrictive
handling’i miras alır. Private/community content official review packet’e girecekse explicit classification,
consent/disclosure ve provenance decision gerekir.

### 9.2 History invariants

History record en az motorcycle context, work/guide identity, used version/release, date/time evidence, actor,
observed/completed/partial/unresolved/safe-stop outcome, safety/recovery implication, attached evidence ve
correction/dispute links’i korur. “Completed” bir UI action’ı değil, product’ın kayıtlı outcome anlamıdır;
published guide veya service role bunu otomatik verified workmanship yapmaz.

- Inactive motorcycle, entitlement change, role revoke veya downgrade required history/trust/correction/recovery
  erişimini silemez veya paywall arkasına taşıyamaz.
- Critical correction/recall, user interaction depth’i (view, opened, active step, evidence, completion) biliniyorsa
  reach-back priority’sine bağlar.
- History current technical claim değildir; current claim change olduğunda historical version used ilişkisi sabit kalır.
- Shared transfer, revoke, correction ve delete bağımlı actor/provenance kayıtlarını silent overwrite yapamaz.

### 9.3 Media

- Official instructional media, user evidence media, community attachment ve quarantined original/derived artifact
  ayrı classification ve retention policy taşır.
- Essential media package closure’a dahil olabilir; heavy/high-resolution/video default offline zorunlu değildir.
- User photo/attachment teknik verification değildir; context/evidence olarak source, scope, actor ve review state
  ile bağlanır.
- Original artifact digest/name, scan result veya generated image identity/fit/diagnosis proof değildir.
- Active work safe-stop/recovery için gerekli media eviction ile çıkarılamaz; local storage failure’da impossible
  recovery promise edilmez, safest available do-not-proceed/preserve-state/support path gösterilir.

## 10. Provenance, audit, recall ve versioning

### 10.1 Provenance graph

Minimum traversable graph:

Research item → Source → Evidence → Claim/content assertion → Record/guide version → Approved release →
Consumer package/current eligibility → User interaction/history

Bir source birden fazla claim’i, claim birden fazla guide elementini, release birden fazla approved snapshot’ı
destekleyebilir. Ters ve ileri traversal zorunludur:

- variant → coverage/evidence/claims/guides/releases;
- source/evidence → dependent claims/content/active work;
- version/release → reviewer, approval, publication, package, historical use;
- recall/correction → affected variant, dependent guide/record/release/package/interaction/recovery.

Source access, evidence availability, current evaluation visibility ve historical provenance ayrı state’lerdir.
Withdrawal current evaluation’dan çıkarabilir; historical link ve prior use’i silemez. Unrelated claims otomatik
invalid olmaz; her dependent claim bağımsız re-evaluate edilir.

### 10.2 Minimum audit event

Material event şu anlamları bağlayabilmelidir:

- actor, effective role/scope, session assurance/security epoch;
- server timestamp + monotonic ordered sequence;
- action, exact object/scope/classification;
- old/new state or version meaning;
- policy/grant/delegation/competence version;
- operation identity and expected/current generations;
- reason, evidence/decision links;
- result: success, denied, failed, partial, held, outcome unknown;
- dependent impact ve recovery/reconciliation owner.

Audit, ordinary publisher/admin tarafından silinemez veya rewrite edilemez; protected custody, fallback buffer,
gap/fork/replay detection ve restore reconciliation gerekir. Minimum evidence effect öncesi durable değilse
normal high-consequence action HELD kalır. Emergency exception varsa ayrıca quarantine/reconciliation ve exact
outcome-unknown kuralı vardır.

### 10.3 Approval, release ve recall integrity

Approval exact snapshot, applicability, evidence, dependencies, transformations/localization/configuration/media
ve conditions’i bağlar. Release, tüm served meaning’i kapatır; mutable runtime substitution veya external URL
değişimi approved meaning’i değiştiremez.

Current release ile suspension/revocation tuple’ı commit/read sırasında fenced olur:

- publish older suspension generation ile hazırlanmışsa reject/hold;
- newer suspension in-flight/committed publish tarafından temizlenemez;
- overlapping scopes’ta most restrictive negative authority wins;
- re-entry/unsuspend yalnız yeni reviewed controlled event ile olur;
- release/suspension generation backward movement fatal authority error’dur.

SUSPENDED, immediate negative authority’dir. RECALL_OPEN ise impact/reach-back/correction/re-entry case’idir.
Suspension/recall normal future application’ı kısıtlar; completed history, used-version, provenance ve task-specific
safe closure/recovery’yi sessizce silmez.

Rollback yalnız exact still-approved, still-compatible, not-recalled known-good predecessor’a yeni controlled
publication event’i olarak yapılır. Böyle bir predecessor yoksa guessed rollback değil suspension + correction/
re-research uygulanır.

## 11. Conflict, idempotency ve consistency

### 11.1 Conflict policy

- High-trust content, release, authority, policy, history ve provenance için last-write-wins kabul edilemez.
- Concurrent draft/edit, source conflict, variant ambiguity, user transfer veya migration collision explicit
  conflict/review state üretir.
- Conflict view competing values/sources, scope, dates, evidence, prior decisions ve affected dependents’i gösterir.
- Bounded claim kabul edilebilir; diğer claim disputed/insufficient/unresolved kalabilir.
- Current value değişse bile prior disagreement, correction reason ve reviewer decision event history’de kalır.
- Error, stale, unavailable veya partial outcome, “new value” ile overwrite edilemez.

### 11.2 Operation identity ve retry

Her sensitive operation identity action type, actor/authority, exact payload/scope, expected versions/generations,
intended effect ve validity context’e bağlıdır. Aynı identity farklı anlamla yeniden kullanılırsa reject edilir.

- Browser/network timeout sonrası result success/failure diye tahmin edilemez.
- OUTCOME_UNKNOWN operation status lookup ve one resolver/escalation owner ile çözülür.
- Blind duplicate approval/publish/recall/role change yasaktır.
- Partial publication/sync/migration, affected scope/result/next action ile açık kalır; retry aynı operation veya
  controlled supersession üzerinden yapılır.
- Idempotency retention, cross-region uniqueness, unknown-age escalation ve numeric timeouts sonraki karardır;
  semantic requirement değişmez.

### 11.3 Consistency hierarchy

1. Authority/control truth (current policy, release/suspension generation, audit continuity)
2. Canonical product truth (scope, claim/content, approved release)
3. User-owned history/work (used-version ve outcome continuity)
4. Derived projection/cache/analytics

Üst katmanın unknown/held olması alt katmana olumlu authority vermez. Alt katmanın stale olması üst katmanı
değiştiremez. Safe teaching/history/reference, normal application eligibility’den bilerek ayrı tutulur.

## 12. Backup, restore, export ve delete

### 12.1 Backup ve restore

Backup sınıfları birbirine karıştırılmaz:

- canonical product snapshots ve version lineage;
- user history/work/media;
- release/artifact/package/provenance evidence;
- protected audit/policy/authority generations;
- derived cache/search/index/analytics.

Backup existence rollback veya current authority kanıtı değildir. Restore/failover:

1. restored state’i quarantine/reconciliation durumuna alır;
2. current release identity, latest suspension/revocation floor, policy/security epoch, audit continuity,
   content/provenance integrity ve classification’i doğrular;
3. missing/older/conflicting authority’de positive eligibility ve normal publication’ı durdurur;
4. yeni controlled reconciliation event’i sonrasında authoritative olabilir.

Old database/cache/backup, newer suspension/revocation knowledge’ını aşağı çekemez; old client/cache restored
content’i current application authority yapamaz. Migration binary rollback değildir: new valid data, history,
revocation ve audit truth korunmadan automatic restore kabul edilmez. Migration state’leri PLANNED, STARTED,
PARTIAL, FAILED, RECONCILING ve RECONCILED anlamlarını taşımalıdır.

### 12.2 Export

Export ayrı authorization ve disclosure event’idir:

- before generation scope, classification, fields, recipient/destination ve purpose preview;
- private notes/photos/community metadata default-deny;
- high-risk/bulk/private export için step-up ve gerekirse independent approval;
- immutable export generation identity + field/scope manifest + provenance/status context;
- generation, access/download, failure, regeneration, revoke/expiry audit;
- formula/active-content/output risk policy;
- link revoke gelecekteki system access’i keser; downloaded/copied/printed/forwarded/captured data’yı geri alamaz.

Export, view değildir ve “revoke edildi, data yok oldu” izlenimi veremez.

### 12.3 Delete, withdrawal ve retention

Delete request şu sınıfları ayrı değerlendirir:

- user private local/server data ve optional media;
- shared motorcycle data ve başka actor’ların independent contributions;
- community contribution ve dependent provenance/history;
- official claims/content/release/audit/protected records;
- legal hold, safety/incident, retention ve investigation evidence.

User data control baseline korunur; ancak delete/withdrawal, başka actor’un independent history/provenance/audit
anlamını silent erase yapamaz. Official truth, release lineage ve protected audit için exact deletion/retention/legal
policy açık bir sonraki karardır. Sistem delete’i success diye sunmadan önce dependency/visibility/retention
sonucunu açıkça göstermeli; copied export için residual disclosure warning vermelidir.

## 13. Authority boundaries

| Authority | Positive action yapabilir | Yapamaz |
|---|---|---|
| Research/contributor | Scope, source/evidence, gap ve draft proposal | Verify, approve, publish, emergency unsuspend |
| Editor/data preparer | Bounded draft ve dependency hazırlığı | High-consequence self-approval, live edit |
| Domain reviewer | Evidence/applicability/conflict review, bounded decision | Publication veya universal safety guarantee |
| Safety/technical approver | Scoped high-consequence approval | Edit sonrası approval’ı korumak, arbitrary publish |
| Release/publishing operator | Eligible approved candidate’ı guarded publish/reconcile | Technical truth üretmek, recall’ı temizlemek |
| Emergency suspension authority | Narrow negative suspension/recall case başlatma | Replacement content, positive approval, silent unsuspend |
| User/owner | Kendi context/history/evidence/correction/consent kararları | Official guide verification veya başka actor data erase |
| Shared collaborator | Granted scope’ta attributable work | Private notes/official truth/other scope |
| Community moderator | Community visibility/moderation/revise/appeal/withdraw | Official technical verification |
| Quality/operations analyst | Metric inspect, drill-down, research/correction follow-up açma | KPI’den claim/release/approval değiştirme |
| Auditor/investigator | Protected history/evidence inspect/export within mandate | Silent mutation/erasure/routine publish |
| Access/policy administrator | Identity/scope/policy lifecycle through controlled workflow | Automatic technical approval/private/audit erasure |
| AI/OCR/extraction | Attributable proposal, extraction, classification suggestion, prioritization | Source truth, verification, policy/tool invocation, approval |
| Browser/UI/cache/backup | Presentation, local persistence, reconciliation request | Authorization, current eligibility, recall or release authority |

Provider, framework veya storage layer bu tablodaki authority’lerden hiçbirini kendiliğinden devralamaz.

## 14. Failure-state sözlüğü

Her boundary aynı state’i aynı anlama gelecek şekilde taşımalı; UI, API veya cache state isimlerini farklı anlamlara
çekemez.

| State | Truthful meaning | Required behavior |
|---|---|---|
| HELD | Gerekli policy, competence, evidence, audit, generation veya recovery koşulu kapanmadı | Positive action blocked; owner, reason, escalation ve next action görünür |
| UNKNOWN / OUTCOME_UNKNOWN | Commit olmuş olabilir veya authority sonucu doğrulanamıyor | Blind retry/success claim yok; operation lookup/resolver |
| FAILED | Authoritative evidence operation’ın commit etmediğini gösteriyor | State recoverable; reason ve safe retry/rollback path |
| PARTIAL / PARTIAL_PROPAGATION | Scope’un yalnız bir kısmı uygulandı veya delivery kanıtı eksik | Exact affected scope/result; mixed meaning current diye sunulmaz |
| STALE / FRESHNESS_HOLD | Age veya authoritative freshness koşulu geçersiz | Critical application hold; teaching/history/reference açık olabilir |
| CONFLICT / DISPUTED | Birden fazla claim/source/merge sonucu yarışıyor | Side-by-side review; winner uydurma |
| EVIDENCE_PENDING / INSUFFICIENT | Gerekli evidence/source access yok | Gap reason, owner ve research path; guess yasak |
| WITHDRAWN / INACCESSIBLE | Source/evidence current evaluation’dan çekildi veya erişilemiyor | Historical trace korunur; dependents re-evaluate |
| SUSPENDED / RECALLED | Normal future application negative authority ile kısıtlandı | Reason/scope/impact/safe-recovery/re-entry görünür |
| MIXED / CORRUPT | Package/release/cache/data snapshot complete ve coherent değil | Reject/hold; last valid safe context ve recovery |
| UNSUPPORTED_CLIENT | Client required safety semantic’i anlayamıyor | Affected application fail-closed; supported teaching/history/recovery if representable |
| RESTORE_QUARANTINE | Backup/failover state current authority/audit/lineage ile reconcile edilmedi | Positive eligibility/publication yok |
| ACCESS_DENIED / REVOKED | Future action scope/session/role/recovery nedeniyle izinli değil | Clear reason/escalation; historical attribution korunur |
| SERVICE_UNAVAILABLE / OFFLINE | Authority’ye erişim yok; freshness/success çıkarılamaz | Preserve context; retry/recovery; no false recall/success |
| SAFE_STOP / PARTIAL / UNRESOLVED | Physical work safe closure/revalidation tamamlanmadı | Truthful history; safe stop/recovery; false completion yok |
| HISTORICAL_ONLY | Read/provenance/correction/audit erişimi var; new routine application yok | Explain boundary; current eligibility’den ayır |

Failure state’in reason, owner/resolver, timestamp/order, affected scope ve safe next action’ı olmalıdır. Renk,
ikon veya tek badge bu anlamların tek taşıyıcısı olamaz.

## 15. AI-operability ve project graph gereksinimleri

### 15.1 Contract-governed backbone

Her logical boundary için graph’ta en az:

- purpose;
- domain/module/owner;
- depends_on ve used_by;
- implements (requirement, business rule, screen/state, ADR/contract);
- public_contracts ve internal_scope;
- tasks, tests, evidence;
- status, last_verified;
- supersedes/superseded_by

ilişkileri bulunur. Yetim boundary, sahipsiz public contract, forbidden dependency, cycle, testsiz critical behavior
ve stale context pack kalite kapısında görünmelidir.

### 15.2 Minimum sufficient context pack

Bir AI task’ı bütün repository’yi okumadan güvenle çalışabilmek için:

- tek ölçülebilir amaç ve kullanıcı outcome’u;
- dependency ve prerequisite;
- okunacak ADR/contract/rule/domain/state/design kayıtları;
- allowed path/module ve forbidden scope;
- expected artifact changes;
- acceptance + negative/failure scenarios;
- migration/rollback/data-protection requirement;
- validation/architecture/traceability commands veya kanıt planı;
- completion evidence, graph updates ve handoff formatı

taşır. Görev boundary dışına çıkarsa silent expansion değil BLOCKED/change-request üretilir.

### 15.3 Data backbone için no-code task simulation

Development başlamadan önce data/migration/offline/restore/release/permission task DAG’i üzerinde:

- dependency sırası;
- iki AI task’ının aynı contract/manifest/state’e çarpışması;
- old/new contract compatibility;
- partial/failed/retry/rollback;
- missing task gap;
- requirement → task → test/evidence ve ters yön closure;
- bütün task’lar DONE iken data/release/product scenario closure

masaüstü walkthrough ile kontrol edilir. Implementer kendi sonucunu yüksek etkili işte tek başına doğrulayamaz;
reviewer ve validation/adversarial kanıtı ayrı tutulur.

### 15.4 AI boundary

AI/OCR/extraction:

- exact input/derived artifact identity, model/provider/version/configuration ve transformation context’i
  provenance’e bağlar;
- uncertainty/unsupported extraction’i açık tutar;
- private/community/official classification boundary’sini aşamaz;
- hostile document instruction’larından tool, network, policy veya workflow authority alamaz;
- human review requirement’ı kaldıramaz;
- provider outage/version change’de result’i current technical truth sayamaz.

Provider seçimi bu kaydın kapsamı değildir; future option, data export/portability, cross-scope reuse, telemetry,
retention ve cost açısından acceptance kanıtı sunmak zorundadır.

## 16. Data-efficiency ve cost constraints

### 16.1 Data-efficiency

DEC-0023 ve DEC-0031 doğrultusunda:

- full-library/full-catalog download yok;
- default package selected motorcycle + selected task + exact release/capability + reachable states ile sınırlı;
- safety/application/recovery core compact ve complete;
- essential media yalnız güvenli anlaşılma için gerekliyse zorunlu;
- enhanced media explicit optional/on-demand ve boyutu önceden görünür;
- active work safe-stop/recovery content cache cleanup ile evict edilemez;
- duplicate assets avoid edilir; integrity kanıtlanabiliyorsa changed/required asset incremental güncellenebilir;
- interrupted/resumable transfer, package integrity/mixed rejection ve cellular/Wi-Fi preference görünür;
- user media official package’tan ayrıdır;
- cache limit/expiry/cleanup kullanıcıya anlaşılır; safety closure düşük byte uğruna zayıflatılamaz.

DEBATE-006 karşılaştırma fixture’ındaki 12 MB compact transfer, optional media için 150 MB, 25 MB cellular
confirmation ve 250 MB content cache değerleri yalnız eşit no-code karşılaştırma sabitleridir; production/commercial
limit olarak kilitlenmemiştir. Nihai limitler later evidence, safety closure ve owner approval ister.

### 16.2 Cost governance

Her architecture alternative şu maliyet sınıflarını açıkça göstermelidir:

- mandatory now;
- mandatory later / release-window deferred;
- deferrable;
- optional;
- scale-triggered;
- free/local/open-source/capped path;
- billing, tax/currency exposure, hard cap/overage;
- credential/data handling;
- export/exit path ve provider lock-in;
- one-owner operasyon yükü ve AI-operability etkisi.

Google Play Console ve Apple Developer Program ücretleri store release maliyeti olarak owner-approved/deferred’dır;
başka paid service/provider/device/expert varsayılmaz. TRY 2,000–3,000/month non-store planning ceiling gelecekteki
harcama planı için tavandır; hemen harcama yetkisi değildir.

Düşük maliyet safety, privacy, accessibility, data continuity, audit veya release evidence’ı azaltamaz. Zorunlu
güvence karşılanamıyorsa capability HELD kalır. Uncapped recurring cost, non-exportable dependency veya provider
outage’da güvenli çıkış yolu olmayan bir seçenek acceptance’ta reject/held olur.

## 17. Backbone architecture option acceptance criteria

Bu kriterler bir provider/technology seçmez; sonraki seçeneklerin aynı no-code bar üzerinden karşılaştırılmasını
sağlar.

### 17.1 MUST acceptance criteria

| ID | Acceptance criterion | Required no-code evidence |
|---|---|---|
| DB-AC-001 | Her domain için tek canonical owner, allowed writer ve forbidden authority görünür | Domain/authority map + dependency graph |
| DB-AC-002 | Variant/applicability, claim/content ve dependent guide scope’u silent merge olmadan taşınır | S1, scope/data contract ve coverage state matrix |
| DB-AC-003 | Source/evidence/provenance current evaluation ve historical use ile bidirectional traversable | Provenance graph + S3/S4 evidence |
| DB-AC-004 | Current state, event/version history ve correction/withdrawal/recall lineage ayrı kalır | Object timeline walkthrough + version contract |
| DB-AC-005 | Edit→live shortcut yok; review, approval, release ve publish distinct guarded transitions | Browser lifecycle walkthrough + S6/S7 |
| DB-AC-006 | Exact approved meaning derived artifacts/config/media/localization dahil kapatılır | Closed release-meaning graph + S33 |
| DB-AC-007 | Publish/suspend race fenced; generation backward movement reject edilir | S14 race + S21 restore drill |
| DB-AC-008 | Browser mutation current server policy/version/independence ile reauthorize edilir | S11–S17 authorization/outage matrix |
| DB-AC-009 | Operation idempotency, OUTCOME_UNKNOWN ve partial result blind retry olmadan çözülebilir | Operation contract + S12/S13/S17 |
| DB-AC-010 | Emergency suspension narrow negative authority olarak normal path failure’larını kapsayabildiğini gösterir | Failure-domain matrix + S14–S17 |
| DB-AC-011 | Consumer envelope capability/freshness/eligibility/revocation/provenance/recovery semantics’i taşıyabilir | Mobile contract + S18–S24 |
| DB-AC-012 | Offline package selected motorcycle/task scope’unda complete safe-recovery closure ile bounded olur | Package manifest walkthrough + S19/S23/S25 |
| DB-AC-013 | Old client, stale/recalled/mixed/restored content positive application authority alamaz | S18–S24 fail-closed matrix |
| DB-AC-014 | User history used-version/outcome/provenance continuity ve local-to-profile conflict’i korur | S26 + history contract |
| DB-AC-015 | Private/shared/community/official/quarantine/audit sınırları derivative/export/AI boyunca korunur | Classification flow + S5/S27–S32 |
| DB-AC-016 | Role, competence, delegation, security epoch ve separation-of-duties server-side enforce edilir | Role matrix + S11/S13 |
| DB-AC-017 | Audit event minimum meaning’i protected, ordered, independently recoverable ve inspectable’dır | Audit chain + S16/S21/S34 restore walkthrough |
| DB-AC-018 | Backup/restore/migration old authority resurrect etmez ve valid new data/history kaybetmez | Restore/migration state machine + S21/S34 |
| DB-AC-019 | Export separate disclosure; delete/withdrawal independent provenance/history’yi silemez | S28/S29 + retention/deletion impact matrix |
| DB-AC-020 | Analytics coverage/quality/workflow signal’ini underlying records/evidence/audit’a drill-down yapar; write authority vermez | Metric dictionary + S35 |
| DB-AC-021 | AI output attributable proposal’dır; hostile input policy/tool/verification authority yaratamaz | AI boundary contract + S32 |
| DB-AC-022 | Graph metadata, task context pack, no-code simulation ve closure audit ile AI-operated execution desteklenir | Sample task pack + S36 |
| DB-AC-023 | Data/package/compute/storage/operational cost bounded, free/capped/exit path görünür ve safety downgrade yoktur | Staged cost sheet + S25/S36 |
| DB-AC-024 | Data contracts provider/framework değişiminde product truth’i kaybetmeden taşınabilir | Export/import boundary + reversibility report |

### 17.2 Reject / hard-fail koşulları

Aşağıdaki sonuçlar option’ı reject eder veya zorunlu düzeltme kanıtı gelene kadar HELD bırakır:

- mutable current record, UI button, cache, backup veya push notification’ın approval/recall/eligibility authority
  olarak kullanılması;
- direct database/API/browser path ile review/publication/audit bypass edilebilmesi;
- high-consequence content’te self-approval, role accumulation veya unavailable competence’in hidden downgrade
  ile aşılması;
- source withdrawal, role revoke, delete, recall veya correction’ın provenance/history’yi silent erase etmesi;
- last-write-wins’in critical claim, release, authority, history veya provenance’e uygulanması;
- network timeout’un otomatik success/failure sayılması veya blind duplicate operation;
- partial/mixed/unknown release’in current coherent release gibi sunulması;
- restore’ın newer suspension/revocation/audit truth’ünü aşağı çekebilmesi;
- old client/incompatible package’ın critical safety semantic’i anlayamadan physical application’a devam etmesi;
- full-catalog download veya heavy media’nın safety closure için zorunlu yapılması;
- scan/render/OCR/AI/community publication’ın technical verification olarak etiketlenmesi;
- untrusted original’ın privileged operations origin/cookie/network/native viewer ile açılması;
- private/shared/community classification’ın derivative, export veya AI processing’de kaybolması;
- analytics/KPI’nin underlying uncertainty/conflict/unknown count’larını gizlemesi veya technical truth yazması;
- gerekli safety/audit/recovery evidence’ın yalnızca AI, simulator, green build, signature veya provider claim’i
  ile varsayılması;
- unbounded/unapproved paid dependency, non-exportable provider veya owner’ın kod/debug/technical repair yapmasına
  dayanan operating model;
- application code/prototype/executable spike’ın “no-code evidence” diye kullanılması.

### 17.3 Acceptance sonucu

- Tüm MUST criteria ve critical S senaryoları authoritative evidence ile kapanırsa seçenek Phase-5 ADR adayı olur.
- Bir critical criterion için evidence yoksa sonuç ACCEPT değildir; HELD/UNVERIFIED yazılır.
- Numeric policy, staffing, provider, legal/retention veya physical failure-domain kanıtı eksikse ADR’ye geçilmez.
- SHOULD seviyesindeki verim/maliyet/operability trade-off’ları açıkça puanlanır; safety/privacy/data continuity
  MUST’ları puan ortalamasıyla telafi edilemez.
- Bu belge kendisi bir ADR veya technology approval değildir.

## 18. No-code S1–S36 acceptance senaryoları

Her senaryo için sonraki architecture comparison en az şu beş çıktıyı vermelidir: expected allow/deny/hold,
visible state, side effect yokluğu/varlığı, protected evidence ve recovery/reconciliation owner. “Buton gizlendi”
veya genel error ekranı acceptance kanıtı değildir.

### A. Canonical scope, evidence, content

| ID | No-code durum | Beklenen sonuç / evidence | Reject sinyali |
|---|---|---|---|
| S1 | Yeni model/year/variant açılırken yakın varyant ve duplicate adayları vardır | Scope unresolved/duplicate-review; distinguishing evidence, owner, affected dependents ve audit event; guess ile canonical merge yok | Yakın varyant otomatik fit olur veya empty field complete sayılır |
| S2 | Coverage view aynı variant için missing, incomplete, stale, conflict, unreviewed ve not-applicable kayıtlarını gösterir | Her state reason/owner/next action ile ayrı; analytics count’ları gizlemez; research queue açılır | Tek opaque score veya boş değer not-applicable diye görünür |
| S3 | Bir source/evidence withdrawn/inaccessible olur | Historical link/use korunur; dependent claim/content’ler bağımsız impact listesine düşer; current evaluation re-run | Bütün claim’ler otomatik silinir veya withdrawal history kaybolur |
| S4 | İki source ölçümde çatışır; reviewer yalnız bir bounded claim’i destekleyebilir | Competing claims, scope/date/evidence/prior decision yan yana; accepted/disputed/insufficient bounded sonuçları; rationale audit’te | Automatic winner/confidence veya all-or-nothing completion |
| S5 | Private user photo veya community post official guide review packet’e kaynak olarak eklenmek istenir | Explicit consent/classification/disclosure + provenance; community status official verification değildir | Publication/photo/moderation official technical truth’a dönüşür |
| S6 | Approved snapshot’tan sonra editor warning’i değiştirir | Old approval immutable kalır; new diff/review need; mobile current release değişmez | In-place approved change veya edit→live |
| S7 | Release candidate’da bir dependency unresolved/recalled/stale bulunur | Preflight HELD; candidate scope/exclusion/reason; unblocked units ayrıca açıkça listelenir | Candidate mixed current olur veya unresolved dependency gizlenir |
| S8 | Rollback için predecessor imzalıdır fakat artık compatible/recalled değildir | Rollback reject/hold; suspension/correction path; bad release ve use history korunur | Signature/hash tek başına rollback authority |
| S9 | Published guide material olarak değişir, kullanıcı active physical step’tedir | Normal next-step stop; physical-state remap/re-check/safe-stop; interaction-depth reach-back ve used version history | Old continuation veya false completed record |
| S10 | Broad variant recall ile unrelated variant aynı release ailesindedir | Dependency-aware most-restrictive hold; unrelated variant’ın bağımsız eligible state’i korunur; overlap graph görünür | Broad stop unrelated truth’i sebepsiz bloke eder veya narrow publish broad recall’ı temizler |

### B. Browser authority, publication ve audit

| ID | No-code durum | Beklenen sonuç / evidence | Reject sinyali |
|---|---|---|---|
| S11 | Browser tab açıldıktan sonra role veya policy revokasyonu gelir | Commit-time reauthorization deny/hold; stale tab read-only; security epoch/policy version audit | Hidden button veya cached role mutation’a izin verir |
| S12 | İki tab aynı current release’e karşı farklı publish candidate gönderir | Expected-current check; yalnız bir guarded transition; diğer operation conflict/held; durable identities/status | Last-write-wins veya iki açıklamasız current release |
| S13 | Temporary delegation review/publish sırasında expire olur | Pending operation re-evaluate/hold; issuer/chain/expiry event; self/nested delegation bypass yok | Expired delegation commit’i tamamlar |
| S14 | Normal publish preflight yapar; overlapping emergency suspension publish commit’inden önce gerçekleşir | Suspension generation fence eski publish’i reject/hold eder; newer negative authority temizlenmez | Older/in-flight publish recall’ı override eder |
| S15 | Primary identity provider veya publication data plane outage sırasında safety incident oluşur | Normal positive action HELD; independent emergency path scope/reason ile suspend etmeyi dener; outage recall diye etiketlenmez | Emergency path aynı tek failure domain’una bağlı veya outage success varsayılır |
| S16 | Protected audit sink high-consequence mutation sırasında unavailable olur | Minimum protected fallback evidence varsa controlled path; ikisi de yoksa normal action HELD; later reconcile | Action audit kanıtı olmadan success |
| S17 | Emergency suspend request timeout olur; commit olmuş olabilir | OUTCOME_UNKNOWN, durable emergency operation identity, lookup/resolver/escalation; affected critical eligibility conservative hold | Blind second suspend veya success/failure tahmini |

### C. Flutter read/sync/offline ve active work

| ID | No-code durum | Beklenen sonuç / evidence | Reject sinyali |
|---|---|---|---|
| S18 | Cihaz uzun süre offline iken high-consequence package kullanılır | Release-bound package, risk/freshness/fit/recovery closure kontrolü; bounded policy içinde değilse application hold; teaching/history/safe recovery ayrılır | Downloaded once indefinitely current application |
| S19 | Recall push/background job ile ulaşmaz, cihaz foreground’a döner | Push yalnız hint; authoritative reconciliation yapılır; known recall normal application’ı kapatır | Push receipt/absence recall truth sayılır |
| S20 | Freshness boundary sırasında wall clock ileri/geri alınır, sonra reboot olur | Local clock eligibility uzatmaz; trust anchor yoksa critical hold/re-check; normal intact reboot gereksiz evrensel block değildir | Clock manipulation veya same-boot monotonic time cross-restore authority olur |
| S21 | Old backup/clone restored cache ve progress getirir | Progress/used version historical context olarak tutulur; content cache current eligibility olmadan non-authoritative; identity conflict quarantine | Old backup newer suspension’ı geri alır veya silent merge |
| S22 | Client yeni safety-critical envelope field’ını parse edemez | Affected physical application fail-closed; client compatible update/explanation; representable teaching/history/recovery varsa korunur | Unknown critical field yok sayılıp devam edilir |
| S23 | Download interrupted, partial dependency veya mixed release oluşur | Package reject/ineligible; retry/reconcile; last valid safe context; no partial package application | Küçük olduğu için incomplete package usable sayılır |
| S24 | Normal guide recall active work’ün safe closure’ını etkiler | Normal progression stop; pinned task-specific safe-stop/recovery closure açık; correction/remap/recheck state; false completion yok | Recall safe closure materyalini de siler veya recovery’yi unrelated bypass yapar |
| S25 | Cache pressure optional high-res/video media’yı evict eder, active task açık kalır | Optional media yeniden indirilebilir; safety/application/recovery core ve active-work context evict edilemez; size/cleanup görünür | Data-efficiency için required closure evict edilir |
| S26 | Account-light user local history’yi profile’a taşır; server’da farklı event vardır | Scope preview, used-version/actor/event lineage, no-silent-loss/overwrite; conflict-review veya explicit resolution | Silent merge veya local record’un official claim’e dönüşmesi |

### D. Privacy, shared/community, ingestion ve AI

| ID | No-code durum | Beklenen sonuç / evidence | Reject sinyali |
|---|---|---|---|
| S27 | Shared motorcycle permission revoke edilir; community contribution withdraw edilir | Future access/public visibility değişir; prior attribution/evidence/history/provenance korunur; dependent review açılır | Revoke/withdrawal independent record’ı siler |
| S28 | Operator private photo/community metadata içeren bulk export ister | Field/scope/recipient/purpose preview; default-deny/step-up/independent approval; immutable disclosure event ve residual-copy warning | Screen access export authority sayılır veya link revoke copied data’yı geri alır |
| S29 | User private delete ister; record shared/community/official/audit dependents’e bağlıdır | Dependency/retention/legal-hold outcome ayrı; permitted private deletion non-independent history’yi bozmaz; deletion audit | “Delete all” ile provenance/audit/other actor history silent erase |
| S30 | PDF/image/archive valid header taşır fakat active content, traversal veya decompression bomb içerir | Received→Quarantined→layered validate/scan/render-untrusted; failure/suspicious/unknown blocked; original/derived lineage protected | Scan/render success technical evidence veya privileged preview authority olur |
| S31 | Supplied URL private address/metadata/redirect/private cloud endpoint’e yönlenir veya review sonrası değişir | Scheme/address/redirect/DNS/size policy deny/quarantine; captured digest/provenance freeze; no ambient cookies/credentials | Browser/server blind fetch veya mutable remote content approved meaning’i değiştirir |
| S32 | AI/OCR plausible measurement önerir; hostile document tool/policy instruction içerir | Attributable proposal + input/model/config provenance + human review; hostile text authority’siz; uncertainty açık | Extraction verified claim olur veya document tool/network/policy çağırır |

### E. Release graph, migration, analytics, graph ve cost

| ID | No-code durum | Beklenen sonuç / evidence | Reject sinyali |
|---|---|---|---|
| S33 | Binary/web/backend/content/config/migration/offline package farklı generations taşır | Closed release-meaning graph compatibility/revocation/recovery closure kontrol eder; mismatch HOLD; old/in-flight release suspension’ı temizleyemez | Valid binary + stale config/partial migration/incompatible package current olur |
| S34 | Migration bir region’da başarılı, diğerinde partial; yeni valid user data oluşmuş | PLANNED/STARTED/PARTIAL/RECONCILING state; data-preserving forward recovery; binary rollback data loss yapamaz | Old backup/binary rollback new data veya revocation history’yi atar |
| S35 | Dashboard stale critical content sayısını quality score içine gömer | Metric dictionary denominator/unknown/unreviewed count’larını açıklar; drill-down exact record/evidence/audit’a gider; write yok | Opaque score uncertainty/conflict’i gizler veya auto-prioritize/auto-publish eder |
| S36 | İki AI task aynı content/release contract’ına dokunmak ister; biri required task çıkarılmış gibi simüle edilir | Context pack allowed/forbidden scope ve dependency collision’ı gösterir; missing task gap olarak kalır; implementer/reviewer/validation closure kanıtlanır | AI bütün repo’yu okuduğunu varsayar, silent path expansion veya all tasks DONE ile product closure varsayılır |

## 19. Sonraki controlled work için açık kararlar

Bu sentezden sonra Phase-4/Phase-5’e taşınması gereken karar grupları:

1. Canonical identity, object/version/generation ve scope lattice’in ayrıntılı modeli.
2. Claim, technical record, guide content, derived asset ve release manifest sınırlarının kesinleşmesi.
3. Physical data/API/event/sync topology ve consistency guarantees.
4. Internal browser read/write contract, stale-session ve operation status contract.
5. User local-first/history-to-profile transfer ve conflict-resolution semantics.
6. Consumer capability envelope, supported client window ve dormant-client policy.
7. Risk taxonomy, exact offline eligibility windows, highest-consequence always-online kararı ve safe decision boundary authoring.
8. Recall/suspension failure-domain independence, emergency quorum/single-actor exception ve reach-back SLA.
9. Role, competence, delegation, policy administration ve low-risk role combinations.
10. Provenance/evidence schema, source withdrawal/dependent re-review ve community/private disclosure rules.
11. Media essentiality, transforms, user-photo retention, cache/storage and upload/download policies.
12. Audit custody, sequence/fork/replay detection, retention/legal hold and investigation access.
13. Backup/restore/migration RTO/RPO, data-loss boundary and anti-resurrection evidence.
14. Export/delete/redaction/retention legal policy and residual copied-data treatment.
15. Analytics event taxonomy, metric denominators, drill-down/retention and alert ownership.
16. AI/OCR data boundary, model/config provenance, human-review tiers, provider portability and cost.
17. Data/package size classes, cellular confirmation threshold, cache budget and incremental update evidence.
18. Free/local/capped architecture route, staged cost plan, overage/exit and owner operational load.
19. Flutter platform/plugin/native boundary contract and browser deployment boundary, without bypassing portable truth.
20. ADR entry criteria, independent review owners and no-code scenario evidence custody.

No item burada teknoloji/provider seçilerek kapatılmamalıdır. Critical unresolved item, ilgili capability’nin
HELD veya evidence-required durumunda kalmasına neden olabilir.

## 20. DEBATE-007 completion ve ADR handoff barı

Bu requirements synthesis ancak aşağıdaki kanıtlarla sonraki ADR çalışmasına hazır sayılır:

- D01–D15 domain/canonical ownership map’i ve LB-01–LB-14 logical boundary contract inventory’si;
- current/history/provenance/release/eligibility/audit state matrix’i;
- browser mutation, consumer read/sync/offline, user-history transfer ve backup/restore/export/delete context
  contract’ları;
- authority/failure-domain/negative emergency matrix’i;
- DB-AC-001–024’e karşı her aday için no-code mapping;
- S1–S36 expected state, side effect, evidence ve recovery walkthrough’ları;
- data-efficiency/package-layer ve staged cost/exit planı;
- requirement → boundary/contract → task → test/evidence ve ters yönde orphan/gap audit’i;
- unresolved/open decisions, owner, next action ve HELD/UNVERIFIED gerekçeleri;
- en az iki bağımsız adversarial review ve manager/Judge synthesis.

Bu kayıt uygulama kodu, prototype, proof-of-concept, executable spike, provider approval veya ADR değildir.
Sonraki teknoloji seçimi ancak bu barın üstünde, açık maliyet/risk/geri dönüş koşulları ve ayrı Phase-5 ADR ile
yapılabilir.

## 21. Kaynak ve izlenebilirlik özeti

Ana ürün/operasyon gereksinimleri:

- 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REQUIREMENTS.md — IDCO-RQ-001–064
- 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKFLOW_LIFECYCLE.md — W-01–W-13
- 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_WORKSPACE_ARCHITECTURE.md — WS-01–WS-12
- 03_DESIGN/INTERNAL_DATA_CONTENT_OPERATIONS_REVIEW.md

Bağlayıcı teknoloji-strategy yönleri:

- 04_TECH_STRATEGY/DEBATES/DEBATE-002__OFFLINE_SAFETY_RECALL_CLIENT_COMPATIBILITY.md — bounded offline,
  release-bound context, fail-closed critical uncertainty, online authoritative Internal Operations
- 04_TECH_STRATEGY/DEBATES/DEBATE-003__APPROVAL_PUBLICATION_EMERGENCY_SUSPENSION.md — immutable snapshot,
  fenced publication/suspension, idempotent operation, protected audit, restore quarantine
- 04_TECH_STRATEGY/DEBATES/DEBATE-004__IDENTITY_AUTHORIZATION_AUDIT_UNTRUSTED_INGESTION.md — scoped policy,
  commit-time reauthorization, separation of duties, quarantine-first ingestion, export disclosure
- 04_TECH_STRATEGY/DEBATES/DEBATE-005__SOFTWARE_CONTENT_SUPPLY_CHAIN_RELEASE_GOVERNANCE.md — distinct release
  authorities, artifact-bound provenance/SBOM, cross-domain release graph, migration/revocation controls

Project execution constraints:

- DEC-0021 — browser-based Internal Operations + no-code Phase-4 boundary
- DEC-0023/DEC-0024 — data-efficient risk-tiered offline direction
- DEC-0025 — approval/publication/emergency suspension direction
- DEC-0026 — identity/authorization/audit/ingestion direction
- DEC-0027 — federated release/supply-chain direction
- DEC-0028/DEC-0029 — AI-native graph/context/closure and nontechnical owner
- DEC-0030 — solo ownership, limited budget and staged-cost rule
- DEC-0031/DEC-0033 — equal no-code fixture and Flutter working direction
