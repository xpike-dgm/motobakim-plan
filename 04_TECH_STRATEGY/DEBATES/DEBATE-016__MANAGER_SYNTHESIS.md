# DEBATE-016 — AI / LLM / Provider Strategy Manager Synthesis

Status: `USER DECISION PENDING / PHASE-4 WORKING-DIRECTION PROPOSAL / NO PROVIDER OR MODEL WINNER`

## Plain-Language Proposal

Kavriva'da AI şu şekilde çalışsın:

1. Kullanıcı AI Usta'ya kendi cümlesiyle ne olduğunu anlatır.
2. Varsayılan konuşan model mümkün olan **ucuz ve hızlı, ama işi yapmaya yeterli** model olur.
3. AI gerektiğinde doğru açıklayıcı soruları sorar.
4. Ayrı bir **karar/yönlendirme katmanı** eldeki cevaplardan hangi yolun veya rehber ailesinin daha uygun olduğuna dair aday üretir.
5. Kavriva kendi kurallarıyla son kontrolü yapar: doğru motosiklet mi, uygun/onaylı rehber mi, güvenlik şartları tamam mı?
6. Kontrol geçerse kullanıcıya uygun rehber/akış gösterilir; yeterli kanıt yoksa sistem HOLD eder ve daha fazla bilgi ister veya güvenli çıkışa döner.

Bu karar/yönlendirme katmanı bugün Jev olmak zorunda değildir. Başlangıçta basit Kavriva kuralları veya mevcut ucuz/hızlı AI modeli bu görevi yapabilir. Jev veya benzeri bounded-decision modelleri ileride yalnız gerçekten daha iyi/ucuz/hızlı oldukları kanıtlanırsa eklenebilir.

## Core Working Direction

- **Kavriva AI olmadan da kritik işlevlerini sürdürebilmeli.**
- AI yardımcıdır; canonical technical truth veya safety authority değildir.
- Kavriva'nın AI/decision sınırı provider/model-neutral tutulur.
- Model/provider değiştirmek mümkün olduğunca adapter/ayar + yeniden doğrulama işi olmalı; uygulamanın geri kalanına provider-specific bağımlılık yayılmamalı.
- Varsayılan ekonomik ilke: **en ucuz ve hızlı yeterli model**.
- Daha güçlü/pahalı model yalnız görev gerçekten daha fazla muhakeme gerektiriyorsa devreye alınır.
- Model maliyeti düşük diye safety/authority sınırı gevşetilmez.
- Multi-provider, local/open-weight veya ayrı decision-model sağlayıcısı first-release gerekliliği değildir.

## AI Usta — Proposed Flow

### 1. Understand
Ucuz/hızlı konuşan AI kullanıcının serbest metnini anlamaya ve eksik bilgiyi fark etmeye çalışır.

Örnek:
> "Gaz verince motordan garip ses geliyor."

### 2. Clarify
AI gerekirse kontrollü sorular sorar:
- ses ne zaman geliyor?
- devirle artıyor mu?
- motor soğuk/sıcak mı?
- titreşim veya güç kaybı var mı?
- doğru motosiklet bağlamı belli mi?

Bu sorular kullanıcıdan observable evidence toplamak içindir; AI henüz teşhis otoritesi değildir.

### 3. Route / Decide Candidate
Ayrı karar katmanı eldeki bilgiden kontrollü bir aday üretir, örneğin:
- known maintenance task;
- symptom/diagnostic flow;
- more clarification required;
- unsupported/unknown;
- safety hold/escalation.

Bu katman deterministic rules, ucuz structured-output model veya ileride Jev-benzeri bounded-decision model olabilir.

### 4. Kavriva Validate
Kavriva şu soruları kendi canonical sistemleriyle kontrol eder:
- doğru motosiklet/variant belli mi?
- rehber gerçekten bu motosiklete uygulanabilir mi?
- rehber approved/current mı?
- required prerequisites tamam mı?
- safety/readiness koşulları geçildi mi?
- source/provenance yeterli mi?

### 5. Continue or Hold
- kontrol geçerse uygun rehber/akış gösterilir;
- bilgi yetersizse daha fazla soru sorulur;
- yüksek risk veya çelişki varsa HOLD;
- model/provider çalışmasa bile güvenli non-AI/deterministic devam yolu kalır.

## Jev Decision

Reviewed Jev addendum result: `KEEP AS OPTIONAL LATER`.

### Today

Jev'i Kavriva'ya eklemiyoruz.

Bugün:
- TypeSafe hesabı yok;
- Jev API key yok;
- Jev-specific production code/schema/data store yok;
- Jev first-release dependency değil;
- Jev olmadan Kavriva tamamen çalışabilir olmalı.

### Future

Mimari Jev'e veya benzer bir bounded-decision modeline düşman olmayacak.

İleride routing/classification hacmi büyürse ve ölçüm gösterirse Jev-benzeri bir model şu dar işlerde tekrar değerlendirilebilir:
- AI Usta intent routing;
- clarification-needed / ambiguity scoring;
- symptom/task taxonomy suggestion;
- approved-guide candidate ranking;
- Internal Operations triage;
- community moderation flagging;
- project workflow routing;
- pre-approved tool candidate selection.

### Never Jev Authority

Jev veya başka bir decision model tek başına şunlara karar veremez:
- motorcycle fit/applicability;
- readiness/safety;
- definitive diagnosis;
- canonical technical truth/specification;
- source/provenance verification;
- physical-action authorization;
- publish/recall/suspension;
- privileged authorization;
- protected audit;
- release/signing/deployment;
- legal/privacy conclusion;
- billing/purchase;
- retention/deletion;
- high-impact self-PASS.

Confidence/probability score bu sınırı değiştirmez.

## Cost Strategy

Kavriva AI ekonomisi şu prensiple ilerlesin:

> **Use the cheapest/fastest model that is good enough for the task. Escalate only when necessary.**

Practical meaning:
- routine intent understanding, short clarification, simple classification and low-risk summaries -> low-cost fast model;
- harder reasoning within allowed AI scope -> stronger model only when required;
- deterministic rule can solve the task reliably -> do not pay an AI model unnecessarily;
- a second provider/decision model such as Jev -> add only when measured benefit exceeds extra dependency/eval/privacy/operations cost.

No specific provider/model is selected by this principle.

## Provider / Model Changeability

Changing a model should be easy where the capability is equivalent, but provider changes can differ in:
- structured outputs;
- tools/function calling;
- context limits;
- errors/rate limits;
- privacy/retention;
- files/vision/search;
- lifecycle/versioning.

Therefore Kavriva should not scatter provider-specific calls throughout the product.

The working direction is one Kavriva-owned AI/decision boundary with replaceable provider/model adapters behind it.

This does **not** mean building a complex universal router in first release. It means keeping product logic, taxonomy, allowed routes, safety rules, guide eligibility and authorization outside the provider-specific layer.

## AI May Help With

- understand intent/task/symptom language;
- ask clarification questions;
- normalize language;
- form retrieval queries;
- summarize/explain approved content;
- rank or classify already-eligible candidates;
- draft and translate;
- Internal Operations triage;
- project/company research/drafting/review preparation;
- propose a route or tool from a bounded allowed set.

## AI Must Not Be Sole Authority For

- unsupported torque/spec/value;
- canonical technical truth;
- final motorcycle fit/applicability;
- readiness/safety gate;
- definitive high-risk diagnosis;
- physical action outside approved guide/state;
- source/guide verification;
- approve/publish/recall/suspend;
- privileged role/policy changes;
- protected audit truth;
- release/signing/deployment;
- legal/privacy conclusions;
- billing/purchase;
- deletion/retention policy;
- high-impact self-review/self-PASS.

## Mandatory Safety/Operating Boundaries If AI Is Enabled

- canonical/approved-source truth remains outside AI;
- safe HOLD for ambiguity/high-risk/divergence;
- correct motorcycle/task context must be isolated;
- structured output is semantically re-validated;
- least privilege / no uncontrolled write tools;
- untrusted retrieval/web/community/document/tool content cannot rewrite policy;
- data minimization by class;
- model/provider/version identity is observable;
- model/version changes trigger re-evaluation;
- bounded retries/outage handling;
- spend/cost observability;
- critical journeys retain non-AI continuation;
- high-impact project/company AI work gets independent review.

## First-Release Simplification

Not required for first release unless new evidence changes the decision:
- Jev;
- multi-provider router;
- hot failover;
- self-host/open-weight;
- persistent consumer AI memory;
- autonomous multi-agent workflows;
- large vector infrastructure;
- provider-native agent stacks;
- dedicated inference capacity.

This prevents "future flexibility" from becoming present-day complexity.

## Research / Review Closure

Core DEBATE-016:
- TASK-004 completed four-family research;
- REVIEW-007 -> CHANGES_REQUESTED;
- remediation completed;
- REVIEW-008 -> residual M-1;
- seven-row residual remediation completed;
- REVIEW-009 -> PASS / no findings;
- TASK-004 -> DONE.

Jev addendum:
- TASK-005 compared 10 candidate uses across deterministic rules, normal managed LLM, Jev and hybrid;
- all 12 required Jev failure scenarios were completed;
- research conclusion -> `KEEP AS OPTIONAL LATER`;
- REVIEW-010 -> PASS / no Critical, Major or Minor findings;
- manager closure -> TASK-005 DONE.

## Owner Decision Requested

Approve or change this Phase-4 working direction:

> Kavriva'nın kullanıcıyla konuşan AI'sı varsayılan olarak ucuz ve hızlı yeterli bir model kullansın. AI doğru soruları sorup bilgi toplasın. Ayrı provider/model-neutral karar katmanı uygun yol veya rehber adayını önerebilsin. Kavriva kendi deterministic/canonical kurallarıyla son kontrolü yapmadan kritik sonuç kullanılmasın. Jev şimdi eklenmesin; ama ileride düşük riskli routing/classification için gerçekten avantaj sağlarsa aynı karar katmanına takılabilsin. Daha güçlü/pahalı modeller yalnız gerektiğinde kullanılsın.

## Boundary

This proposal does not approve:
- OpenAI, Anthropic, Google, TypeSafe/Jev or another provider/model/plan;
- account, API key, trial, credit, purchase or payment;
- production prompt/tool schema/agent workflow;
- vector database/fine-tune/deployment/integration;
- final legal/privacy conclusion;
- final recurring budget;
- Phase-5 ADR;
- Gate 4 -> 5 transition.
