# DEBATE-004 — Identity, Scoped Authorization, Audit and Untrusted Ingestion

Status: `APPROVED WORKING DIRECTION — DEC-0026 / ADR PENDING`
Date: 2026-09-17
Scope: Browser-based Internal Data & Content Operations
Planning constraint: No application code, prototype or executable spike

## 1. Decision question

How should Kavriva determine who may see or perform each internal action, preserve trustworthy evidence of every
high-consequence decision, and safely accept untrusted files/URLs without allowing role labels, stale sessions, hostile
content or administrative access to bypass the approved review/publication model?

This debate selects security and governance properties. It does not select an identity provider, authorization product,
malware scanner, storage system, browser framework, SIEM, cloud or other vendor.

## 2. Existing authority

This debate inherits:

- `DEC-0021`: Internal Operations is browser-based and planning remains no-code.
- `DEC-0022`: only Luna Max sub-agents are pre-authorized.
- `DEC-0025`: approval/publication, suspension generations, protected audit and emergency negative authority are approved
  working directions.
- `IDCO-RQ-009`–`016`: source, evidence, provenance, actor role and current claim meaning remain distinct.
- `IDCO-RQ-029`–`031`: attributable human review and consequence-proportionate independence are required.
- `IDCO-RQ-045`–`051`: material events are auditable; roles are least-privilege, scoped and historically attributable;
  private/shared/community boundaries remain explicit.
- `IDCO-RQ-060`–`064`: failed/blocked states remain honest, recoverable, understandable and accessible.

Primary risks include `TSR-006`, `TSR-014`, `TSR-015`, `TSR-018`, `TSR-021` and `TSR-026`.

## 3. Threat and failure model

The policy must remain safe when:

- credentials are phished, shared or recovered through a weak channel;
- a valid user acts outside competence, motorcycle/domain scope or current assignment;
- one person accumulates author, approver, publisher, administrator and auditor powers;
- a role is revoked while a browser tab, session or long operation remains open;
- the UI hides a button but an API/direct request is attempted;
- a privileged administrator tries to change history or grant themselves approval power;
- an uploaded PDF/image/archive contains malware, scripts, macros, deceptive type, traversal paths or excessive expansion;
- a supplied URL points to private infrastructure, cloud metadata, a redirect chain or a mutable hostile resource;
- document preview leaks cookies, credentials, local network access or active content;
- an export exposes private evidence, personal data, confidential sources or excessive scope;
- automated extraction or malware scanning is mistaken for technical verification;
- logs contain secrets/private content, are incomplete, have unreliable time or can be erased by the actor being audited.

## 4. Non-negotiable invariants

1. Authentication proves an account/session claim; it does not prove technical competence or authorize every action.
2. Human-readable role names are not authority by themselves. Every request is authorized server-side using current
   actor, capability, resource/scope, workflow state, consequence and required independence.
3. Deny is the default. Missing, stale, conflicting or unrecognized policy context never becomes permission.
4. The browser, hidden buttons, cached role state and client-supplied scope are not authorization authorities.
5. A high-consequence proposal cannot be self-approved or self-published; emergency suspension cannot create positive truth.
6. Authorization is re-evaluated at the authoritative mutation, not only at login or when the page opens.
7. Role removal ends future authority but never rewrites past attribution, evidence or historical meaning.
8. Temporary access is scoped, reason-bound, approved, time-bounded, reviewable and automatically expires.
9. Administrators manage access/policy infrastructure but do not automatically inherit technical approval, publication,
   private-content inspection or audit-erasure authority.
10. Audit evidence is attributable, ordered, tamper-evident, separately protected and records denied/failed/unknown as
    well as successful material actions.
11. Untrusted files and URLs never become trusted evidence merely because upload, scanning, parsing or preview succeeds.
12. Untrusted content is quarantined before active parsing/preview; validation is layered and failure is explicit.
13. Remote resources are captured with provenance and stable identity before review; later remote changes cannot silently
    alter approved evidence or content.
14. Private, shared, community and official evidence remain separate scopes through preview, review, export and audit.
15. AI/OCR/extraction output is a proposal linked to its input and transformation context; it is never source truth or approval.
16. Unknown or mixed classification defaults to the most restrictive applicable handling and propagates to derivatives,
    previews, AI processing, audit references and exports until an explicit reviewed classification decision changes it.
17. Authorization policy, role/group mapping and privileged recovery are high-consequence controlled objects; their
    authors, approvers and activators cannot silently combine authority or make past actions retroactively valid.
18. If required independent staffing, competence, current policy or minimum protected audit evidence is unavailable,
    the high-consequence action remains `HELD`; operational pressure does not create authority.

## 5. Authorization alternatives

### Option A — Shared administrator access

Everyone trusted to operate the system can perform most actions.

Benefits: simple initial setup.

Failure modes: no meaningful least privilege, self-approval, weak attribution, large compromise radius and impossible
separation of duties.

Result: `REJECT`.

### Option B — Static role-based access only

Each user receives one or more fixed roles such as editor, reviewer or publisher.

Benefits: understandable and auditable; operationally manageable.

Failure modes: role explosion or over-broad access when motorcycle/domain scope, risk, workflow state, assignment,
private-content boundary and independence are ignored.

Result: `USEFUL BASELINE, INSUFFICIENT ALONE`.

### Option C — Attribute/policy rules only

Every decision is derived from actor/resource/context attributes.

Benefits: expressive scope and condition handling.

Failure modes: policy becomes difficult to explain, test and administer; hidden interactions can create accidental access.

Result: `NOT RECOMMENDED AS THE HUMAN GOVERNANCE MODEL ALONE`.

### Option D — Hybrid capability model

Understandable base roles grant candidate capabilities; server-side policy narrows them by resource/domain/motorcycle
scope, workflow state, consequence tier, assignment, independence, session assurance and temporary conditions.

Benefits: combines operational clarity with necessary scope and workflow control; supports precise audit explanations.

Costs: needs policy versioning, simulation, change review and denied-access diagnostics.

Result: `RECOMMENDED DIRECTION`.

## 6. Recommended identity and authorization policy

### 6.1 Capability families

These are separable capabilities, not necessarily one job title per row:

| Capability family | May do within granted scope | Must not imply |
|---|---|---|
| Research/contribution | Open research, collect sources/evidence, propose gaps/claims. | Verification, approval or publication. |
| Editorial/data preparation | Create and edit controlled drafts, link evidence, respond to review. | Self-approval or consumer-live change. |
| Domain review | Evaluate evidence, applicability, conflicts and requested domain meaning. | Universal safety approval or publication. |
| Safety/technical approval | Decide bounded high-consequence packets within demonstrated scope. | Editing after approval or publishing arbitrary content. |
| Release operation | Assemble and execute an eligible approved release; reconcile result. | Technical truth authority or bypass of approval. |
| Emergency suspension | Place narrow negative holds and open recall cases. | Positive approval, content authoring or unsuspension without reviewed re-entry. |
| Quality/operations analysis | Inspect permitted coverage/workflow signals and open follow-up work. | Automatic claim decisions or unrestricted private-data access. |
| Audit/investigation | Inspect protected events/evidence within investigation mandate. | Silent mutation, routine publication or erasure. |
| Access/policy administration | Provision identities/scopes and controlled policy changes. | Automatic content, approval, publisher, auditor or private-evidence authority. |
| Community moderation | Moderate community visibility and process within community scope. | Official technical-guide verification. |

### 6.2 Authoritative decision tuple

Every sensitive read, export or mutation is decided using current server-authoritative context:

- authenticated actor and session assurance;
- requested capability/action;
- target object and exact resource scope;
- motorcycle/model/year/variant and technical/content domain where applicable;
- private/shared/community/official classification;
- current workflow/version/publication/recall state;
- consequence tier and required reviewer competence;
- authorship, prior decision and independence relationships;
- current assignment/delegation and expiry;
- policy version, incident hold and organization context.
- account/session security epoch, grant/delegation identity and expiry;
- current release and suspension/revocation generations where the action can affect consumer authority.

The decision returns allow/deny/hold plus a stable reason category suitable for operator explanation and audit. Sensitive
policy details are not exposed to unauthorized users.

The authoritative commit binds the evaluated policy version, grant/delegation chain, actor/session security epoch,
resource/workflow version, required competence/independence and operation identity. A material policy, role, competence,
classification or authority-generation change before commit holds or invalidates the pending operation for re-evaluation;
it never retroactively authorizes completed work.

### 6.3 Separation-of-duties rule

For high-consequence official content:

`propose/edit ≠ domain review ≠ safety approval ≠ publication`

At minimum, the same person cannot perform an incompatible pair for the same change packet merely by holding multiple
roles. Independence is evaluated per object/change, not only by role membership.

Emergency suspension is deliberately different: it may stop future use quickly but cannot provide approval, replacement
content or silent re-entry. Exact low-risk role combinations, quorum and staffing fallback remain open.

Small-team fallback is not self-approval: if required independent competence is unavailable, high-consequence work stays
`HELD` with owner, reason, escalation and next action. Only pre-authorized temporary/external reviewers with documented
competence, scope, independence and expiry may fill the gap. Emergency suspension remains negative-only.

### 6.4 Access lifecycle

- Join: identity verified through the organization process; minimum role/scope; manager/owner and reason recorded.
- Change: added scope requires explicit approval; no silent inheritance from job title.
- Temporary/delegated access: exact capability/scope/reason/approver/start/expiry; no transitive delegation by default.
- Review: privileged and dormant access is periodically recertified; unexplained access is removed.
- Revoke: new requests fail immediately; active sessions and queued/in-flight sensitive operations are invalidated or
  forced through commit-time re-authorization; historical attribution remains.
- Depart/incident: sessions, recovery channels and credentials are revoked; owned work is reassigned without changing authorship.

Delegation cannot exceed the issuer, inherit competence automatically, bridge classification, enable self-approval or
combine incompatible capabilities on the same change. Self-delegation and nested/transitive delegation are denied by
default. Every use retains the grant/delegation identity, chain, policy version and expiry in its audit evidence.

Policy changes and access grants are themselves versioned, attributable, testable and auditable. No individual can
silently grant themselves the complete high-consequence chain.

### 6.5 Authorization-policy administration

Authorization policy is treated like a controlled high-consequence artifact:

- author, independent approver and activator/rollout capabilities are distinct for material changes;
- the exact policy version is immutable, attributable, impact-simulated and tested against allow/deny/hold cases;
- role aliases, nested groups, service accounts, delegations and infrastructure-admin paths are included in accumulation checks;
- activation has explicit effective time and cannot retroactively authorize a past action;
- narrowing/widening policy changes define the effect on pending work; high-consequence pending work is held for re-check;
- rollback restores a known policy version through a new event and cannot erase the failed/intervening policy;
- IdP/group, database/storage, deployment, key, backup and policy-engine administrators do not automatically gain data-plane authority;
- direct control-plane/storage changes require detection, protected audit and incident handling.

### 6.6 Classification and competence authority

Unknown/mixed private, shared, community and official classification defaults to the most restrictive input and propagates
to every derived preview, extraction, audit reference and export. Moving private/community material into an official review
packet requires an explicit consent/disclosure/classification decision within policy; community moderation or publication
never creates official verification. Technical verification remains claim-scoped and separately records provenance,
applicability, uncertainty and human decision.

Reviewer/approver competence is a controlled scoped record with issuer, evidence, domain/motorcycle scope, conditions,
start, expiry/recertification and suspension/revocation. Delegation or job title does not copy competence. Material scope
or competence changes hold pending high-consequence work for re-evaluation. Conflicts and independence checks include
authorship, delegation chain, aliases/nested groups, service identities and policy-defined organizational relationships.

## 7. Authentication and browser session properties

- Privileged operators with approval, publication, emergency, access-administration, audit/export or quarantine-release
  authority require phishing-resistant authentication; exact authenticator/provider remains a later choice.
- Recovery and help-desk reset cannot be materially weaker than normal privileged authentication.
- Step-up/re-authentication is required for high-consequence approval, publication, emergency suspension, bulk export,
  privilege change and other later-classified sensitive actions.
- Sessions have explicit inactivity/absolute bounds, rotation and server-side revocation; numeric durations remain open.
- The operator can inspect and terminate active sessions; security can revoke all sessions during compromise response.
- Browser storage never contains reusable long-lived authority beyond the selected security design.
- Cross-site request protections, trusted origins and server-side transaction binding are required properties.
- A stale or offline Internal Operations page is read-only/non-authoritative and cannot queue an approval/publish/role change.

Privileged compromise/recovery is an explicit state transition. It increments an account/session security epoch, revokes
all relying-party browser sessions, refresh/recovery artifacts and pending high-consequence transaction authorizations,
then requires fresh phishing-resistant authentication and transaction-bound step-up. Independent notification and
security review are required. Help-desk/last-admin recovery uses dual control or a separately governed time-limited
break-glass path and cannot itself approve or publish content. If authoritative revocation state is unavailable, privileged
positive actions fail closed.

Human and workload/service identities are distinct. Service/worker accounts receive explicit non-interactive
capabilities, scoped credentials, rotation/revocation and no implicit human approval authority; their actions remain
attributable to the initiating operation and service identity.

## 8. Audit policy

### 8.1 Events

Audit covers at least:

- authentication, recovery, session creation/revocation and step-up;
- access request/grant/deny/change/expiry and policy change;
- sensitive read, private evidence access, search and export;
- source/evidence upload, URL retrieval, quarantine, scan, parse, preview, release and deletion/retention action;
- draft/edit/link/unlink, review, approval, rejection, publication, rollback, suspension, recall and restore;
- denied, failed, partial and outcome-unknown operations;
- audit inspection/export and emergency/break-glass attempts.

### 8.2 Minimum event meaning

Events preserve actor, effective role/scope, session/assurance context, server time plus ordered sequence, action, object,
version/state, reason, policy version/decision, operation identity, old/new meaning and result. Logs exclude credentials,
session secrets and unnecessary sensitive payloads; sensitive details use protected references where possible.

### 8.3 Integrity and access

- ordinary publishers/admins cannot erase or rewrite evidence of their own actions;
- audit storage/evidence is append-only or equivalently tamper-evident, separately protected and recoverable;
- access to audit/private evidence is itself scoped and audited;
- alerting detects missing sequence, policy bypass, privilege escalation, repeated denial, unusual export and ingestion anomalies;
- retention, legal hold, privacy redaction and export periods remain explicit later policy choices;
- audit failure follows DEBATE-003 protected fallback/quarantine rules and never creates false success.

Before a high-consequence mutation can take effect, minimum protected evidence is durably recorded with actor/effective
authority, operation identity, object/version, policy/grant version, ordered server time/sequence, intended transition and
result linkage. Custody is independent from ordinary publisher/access administration; audit administration is write-only,
read-only or dual-controlled according to function. Integrity checkpoints, monotonic order, gap/fork/replay detection and
restore reconciliation are required properties.

If the normal sink fails, a bounded separately protected buffer records the same minimum evidence. If neither normal nor
fallback evidence can be durably recorded, normal high-consequence action remains `HELD`; emergency negative action follows
the separately approved DEBATE-003 exception policy and remains quarantined/unknown until reconciled. A successful state
change followed by uncertain audit persistence cannot be reported as ordinary success.

Audit investigation must provide a readable object-centered chain:

`current state → operation → actor/effective grant/delegation → policy version → artifact/version → decision/result → dependent impact`

Protected references preserve proof of sensitive exposure without broadly duplicating private payloads. Audit search,
retrieval, redaction, retention change and export are themselves audited.

Audit supports accountability and investigation; it is not surveillance by default and cannot substitute for authorization.

## 9. Untrusted file ingestion policy

### 9.1 State model

`RECEIVED_UNTRUSTED → QUARANTINED → IDENTIFIED → VALIDATED → SCANNED → RENDERED_UNTRUSTED_PREVIEW → HUMAN_CLASSIFIED → SAFE_FOR_HUMAN_REVIEW`

Branches remain explicit:

- `REJECTED`: forbidden/invalid type, size, structure or policy;
- `SCAN_FAILED/UNKNOWN`: scanning unavailable, failed or inconclusive; never treated as clean;
- `PARSING_FAILED`: no fabricated extracted value;
- `MALICIOUS/SUSPICIOUS`: isolated, access restricted, incident workflow opened;
- `EXPIRED/DELETED_BY_POLICY`: provenance and permitted audit meaning retained without pretending the source never existed.

`SCANNED`, `RENDERED_UNTRUSTED_PREVIEW` and `SAFE_FOR_HUMAN_REVIEW` are cybersecurity/processing states only. They do
not mean technically correct, applicable, sufficient, verified or approved.

### 9.2 Layered controls

- allow only business-required file families; deny executable/active types by default;
- validate claimed extension, declared content type, file signature and parsed structure; disagreement is rejected/quarantined;
- assign server-generated storage identity/name; never trust paths or filenames for storage/execution;
- enforce compressed and expanded size, file count, nesting, recursion, parse time and resource limits;
- defend against archive traversal, symlinks/special files, polyglots, malformed parsers and decompression/resource bombs;
- scan in isolated infrastructure with no unnecessary secrets/network and record engine/policy/result context;
- remove or neutralize active content for preview where policy permits, while preserving the original/evidence lineage;
- render previews on an isolated origin/sandbox without application cookies, privileged browser APIs or arbitrary network access;
- treat embedded links, attachments, macros, scripts, fonts and media as separate untrusted dependencies;
- inspect/redact sensitive metadata such as location/device/author fields according to explicit evidence/privacy policy;
- store quarantined originals outside consumer/public delivery paths with restricted access and retention;
- re-scan/re-evaluate when detection policy, parser risk or source status materially changes.

Each quarantine item has an owner/queue, immutable original digest, classification, current reason, permitted viewers,
next action, escalation and retention state. Original and sanitized/derived artifacts are distinct and linked by exact
transformation provenance. Scan/parser/CDR results bind the exact digest and policy/tool context; replacement bytes require
a fresh pipeline. High-consequence upload and quarantine release cannot be completed by one person where independence is
required. Inconclusive results remain blocked; a false-positive challenge creates a new attributable review, not an override.

Quarantined originals are never served from the authenticated operations origin. The preview boundary has no application
cookies, privileged browser APIs, arbitrary network, active-content execution, attachment opening, implicit download,
native-viewer handoff, print or unrestricted navigation. Ordinary operators do not receive original-file access merely
because scanning passed. Renderer/isolation uncertainty remains blocked.

No single scanner, content-disarm step or sandbox provides proof of safety. Layered validation narrows risk.

## 10. Untrusted URL/source retrieval policy

The operator browser and main application server do not blindly fetch arbitrary supplied URLs with ambient credentials.
A controlled retrieval boundary must:

- allow only required schemes/protocols and normalized URLs;
- resolve and validate every destination and redirect hop;
- block loopback, private, link-local, reserved, internal service and cloud-metadata destinations unless a separately
  approved source class has an isolated connector;
- defend against DNS rebinding and address changes between validation and connection;
- use no operator cookies, browser session, cloud credentials or implicit internal trust;
- enforce redirect count, timeout, response size, decompression and content-type limits;
- isolate egress, parsing and storage; retrieved content enters the same quarantine pipeline as uploads;
- record submitted URL, retrieval time, resolved/final location, redirects, response identity/digest and source context;
- freeze the reviewed evidence artifact so remote mutation cannot change approved meaning;
- clearly distinguish unavailable source, changed source and historically captured evidence.

The retrieval contract rejects credential-bearing/userinfo URLs, parser disagreement, non-approved schemes, alternate
or ambiguous address encoding, private-address forms including IPv4-mapped IPv6, insecure protocol downgrade and
unapproved ports. Network egress policy enforces the same boundary. DNS is re-resolved and the actual connection address
validated; every redirect is a new decision. Raw URLs are treated as sensitive input: credentials/tokens/query secrets are
redacted from broad logs, UI and exports while a protected provenance record retains only policy-approved detail.

Allowing a URL is not endorsement of the source, and a successful fetch is not evidence sufficiency.

## 11. Export and sensitive-read policy

- Export is a distinct capability, not implied by ordinary screen access.
- Scope, purpose, classification, fields and recipient/destination policy are evaluated before generation.
- Unknown/mixed content uses the most restrictive classification. Private notes, sensitive photos and private/community
  metadata are default-deny fields unless explicitly included by an authorized reviewed decision.
- High-risk/bulk/private export requires step-up and, where consequence warrants, independent approval.
- Exports minimize data, preserve necessary provenance/status, carry generation context and expire where appropriate.
- Generation, download/access, failure, regeneration and revocation are audited.
- Spreadsheet/formula injection and active-content risks are handled by output-format policy.
- Audit export does not give the exporter authority to modify source audit evidence.

Before generation, the operator sees an included/excluded field and scope preview plus intended recipient/destination.
Each export has an immutable generation identity, classification/field manifest, recipient/purpose context and residual-copy
warning. Revoking or expiring an online link prevents future system access only; it cannot retract a file already downloaded,
printed, copied, forwarded or captured. Export is therefore recorded as a disclosure event, not a reversible view.

Exact legal basis, retention, watermarking, download controls and approved destinations remain later decisions.

## 12. AI/OCR/extraction boundary

Automated systems may suggest classification, extract candidate text/fields, flag conflicts or prioritize review only if:

- the original source and transformation provenance remain linked;
- confidence does not become a verification badge or fabricated certainty;
- unsupported/failed extraction is explicit;
- sensitive material is not sent outside approved data boundaries;
- human review appropriate to consequence remains required;
- prompt/document active-content or instruction text cannot alter system authority or policy.
- exact input/derived digest, model/provider/version/configuration and transformation result remain attributable;
- provider telemetry, cross-scope reuse and network/tool access comply with an approved data boundary;
- document instructions cannot invoke tools, fetch resources, change classification or perform policy/workflow actions;
- model outage, uncertainty or version change remains explicit and can trigger re-review where meaning changed.

AI/provider/model selection is not part of this debate.

## 13. No-code acceptance scenarios

Every candidate architecture must walk through:

1. An editor calls the approval API directly although the button is hidden.
2. One user holds reviewer and publisher roles and attempts to approve their own high-risk change.
3. A role is revoked after a page opens but before commit.
4. A temporary delegation expires during review/publication.
5. An administrator grants themselves approver/publisher/auditor powers.
6. A compromised reviewer credential approved content that has not yet published.
7. A password/recovery reset occurs during an active privileged session.
8. A PDF has a valid header but contains active or malformed content.
9. An image/PDF/archive expands far beyond its uploaded size or exhausts a parser.
10. An archive contains traversal paths, links or unexpected executables.
11. Malware scanning is unavailable or returns inconclusive.
12. A preview attempts script execution, cookie access or internal-network requests.
13. A supplied URL redirects to loopback/private/cloud-metadata space or changes DNS answer.
14. A remote source changes after review but before approval/publication.
15. A private evidence item is included in a broad export or audit search.
16. An export is opened as a spreadsheet and contains formula-like attacker data.
17. Audit storage is unavailable during access change, export or ingestion release.
18. AI extraction proposes a plausible but unsupported measurement.
19. A help-desk recovery adds a new authenticator while old privileged sessions remain open.
20. An IdP/group/policy/database administrator uses aliases, nested groups or a service account to assemble the full authority chain.
21. Normal and fallback audit paths fail, or a restored audit snapshot has a sequence gap/fork.
22. Required independent reviewer competence is unavailable in a small team.
23. Unknown/mixed private/community material flows into preview, AI processing or export.
24. A renderer/native viewer is compromised or an attachment attempts to escape preview isolation.
25. An online export link is revoked after the recipient has already downloaded/forwarded the file.
26. A hostile document attempts prompt injection, tool use or cross-scope data extraction through AI/OCR.

Each walkthrough must define the expected allow/deny/hold decision, resulting state, absence/presence of side effects,
minimum audit evidence, user-facing reason/next action and recovery/incident path. Merely demonstrating a blocked button
or error screen is not sufficient.

## 14. Open decisions

1. Exact role combinations permitted for low-consequence work and the consequence taxonomy that controls them.
2. Reviewer competence/scope evidence and who may grant or recertify it.
3. Numeric session, re-authentication, temporary-access and access-review periods.
4. Exact privileged authentication, recovery and break-glass mechanisms.
5. Private/community/official data classification, retention, legal hold and export rules.
6. Allowed upload/source types, size/expansion limits and exceptional-source process.
7. Whether and how encrypted/password-protected archives/documents may be accepted.
8. Original-versus-sanitized evidence retention and who may inspect quarantined originals.
9. URL allow/deny/source-class rules and any isolated internal-source connectors.
10. Audit retention, redaction, independent custody, investigation access and alert thresholds.
11. Exact policy-model implementation and administrative UX.
12. AI/extraction provider/data-boundary policy.

## 15. Manager working direction

Proceed provisionally with:

- hybrid understandable roles + server-authoritative scoped/contextual policy;
- deny-by-default and commit-time re-authorization;
- per-change separation of duties for high-consequence official content;
- organization-bound strong authentication, step-up for sensitive actions and revocable browser sessions;
- time-bounded attributable delegation and non-destructive revocation;
- protected, ordered and separately controlled audit evidence;
- quarantine-first layered upload/URL processing and isolated preview;
- separate export authority and preserved private/community/official boundaries;
- automation only as attributable proposals, never verification or authority.

The user approved this reviewed working direction under `DEC-0026`. It is not an ADR and does not pass Gate 4 → 5.
Numeric policy, detailed governance and implementation technology remain open.

## 16. Research basis

The following official/primary sources establish requirements and limitations, not technology selections:

- [NIST SP 800-63B-4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63b-4.pdf): AAL2 replay
  resistance, protected channels, phishing-resistant option and periodic reauthentication; the relying party remains
  responsible for its own session controls. Its timeout values are benchmarks for later numeric policy, not selected here.
- [CISA — Implementing Phishing-Resistant MFA](https://www.cisa.gov/sites/default/files/2023-01/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf):
  phishing-resistant MFA is recommended especially for privileged accounts.
- [NIST SP 800-162](https://csrc.nist.gov/pubs/sp/800/162/upd2/final): authorization can evaluate subject, object,
  operation and environmental attributes, supporting the hybrid scoped/contextual direction.
- [NIST SP 800-53 Rev. 5 official publication](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final):
  AC-5/AC-6 separation of duties and least privilege; AU-9/AU-10/AU-11/AU-12 audit protection, attribution, retention
  and generation.
- [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html):
  deny-by-default, least privilege, per-request authorization and server-side enforcement.
- [OWASP Session Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html):
  full-session HTTPS, protected cookies, idle/absolute bounds, rotation and high-risk reauthentication.
- [OWASP Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html): security event
  coverage, who/what/when/where context, untrusted client data and protection against modification/deletion.
- [OWASP File Upload Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html) and
  [OWASP ASVS 5 file handling](https://cornucopia.owasp.org/taxonomy/asvs-5.0/05-file-handling): allowlisted types,
  layered content validation, generated storage identity, archive limits, path/symlink controls, isolated storage and
  scanning before untrusted content is served.
- [OWASP HTML5 Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/HTML5_Security_Cheat_Sheet.html) and
  [Content Security Policy Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html):
  sandboxed frames and restrictive resource policy support—but do not alone guarantee—preview isolation.
- [MDN iframe security reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/iframe): combining
  same-origin and script permissions can defeat sandbox intent; native document viewers require separate treatment.
- [OWASP SSRF Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html):
  scheme/domain policy, redirect control, address validation, DNS rebinding defense and deny-by-default egress.
- [NIST Privacy Framework](https://csrc.nist.gov/pubs/cswp/10/nist-privacy-framework-version-10/final) and
  [NIST minimization definition](https://csrc.nist.gov/glossary/term/minimization): risk-based privacy management and
  collection/use/storage/disclosure limited to necessary scope.
- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final): preparation, detection, response, recovery
  and lessons learned are integrated risk-management activities.

Research limitations preserved by this debate:

- MFA does not neutralize a stolen active session;
- a clean MIME header, scanner result, sandbox or content-disarm result does not prove universal safety;
- URL allowlisting alone does not prevent redirects, parser differences or DNS rebinding;
- encryption does not remove sensitive metadata;
- application-database log rows are not automatically tamper-evident;
- successful extraction does not establish technical correctness.
