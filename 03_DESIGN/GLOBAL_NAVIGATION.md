# KAVRIVA GLOBAL NAVIGATION

Status: APPROVED
Approved by: USER — 2026-09-15
Decision: DEC-0017
AI Usta root refinement: DEC-0018 / `REF-AIUSTA-001`
Phase: Phase 3 — Design

## Approved Bottom Navigation

Kavriva'nin working global navigation shell'i **5-item bottom bar** olarak onaylanmistir:

1. **Garaj**
2. **Bakim**
3. **AI Usta** — center / primary-assistance entry
4. **Gecmis**
5. **Topluluk**

Bu karar exact icon, font, spacing, elevation, animation, selected-state treatment veya platform implementation'ini finalize etmez.

## Tab Semantics

### Garaj
Primary meaning:
- selected motorcycle context,
- motorcycle switching / active-inactive management,
- motorcycle-specific lifecycle entry,
- motorcycle identity/context management.

Primary approved contexts informed by:
- `SCR-005`
- `SCR-008`
- `SCR-031`

Garaj bir KPI/dashboard sayfasi degildir. Task, maintenance, history, community ve profile semantics'lerinin hepsini ayni anda buyuk kartlar halinde toplamaz.

### Bakim
Primary meaning:
- maintenance plan,
- due/upcoming/uncertain items,
- reminder detail,
- catch-up / critical maintenance priority.

Primary approved contexts:
- `SCR-022`
- `SCR-023`
- `SCR-024`

Critical safety/correction routine reminder gibi gosterilmez.

### AI Usta
Primary meaning:
- kullanicinin `bir is yapmak istiyorum` ve `motorda bir sorun var` intent'lerinin merkezi giris noktasi,
- known-task discovery ve symptom-first diagnosis'i approved flows'a yonlendiren assistant entry.

Primary approved contexts routed from this tab:
- known task -> `SCR-009` -> `SCR-010` -> readiness/application flow,
- symptom/problem -> `SCR-019` -> `SCR-020` -> `SCR-021` -> supported repair flow when evidence permits.

**Critical authority boundary:**
`AI Usta` bu asamada bir UX role/entry label'idir; technology/LLM/provider/backend architecture karari DEGILDIR.

AI Usta:
- kendi basina technical source-of-truth olamaz,
- verified guide/source/provenance yerine gecemez,
- motorcycle fit, readiness, uncertainty veya safety gates'i bypass edemez,
- unsupported technical value veya definitive diagnosis uyduramaz,
- application instruction'i approved guide/diagnosis/readiness semantics disinda acamaz.

### Approved AI Usta Root Structure

DEC-0018 ile root interaction shape netlestirildi:
**A1 — Guided Split**.

Canonical:
- `AI_USTA_UX_STRUCTURE.md`
- `REF-AIUSTA-001`

Root hierarchy:
- compact selected motorcycle context,
- `Nasil yardimci olayim?`,
- `Bir is yapmak istiyorum`,
- `Motorda bir sorun var`,
- optional low-prominence help,
- bottom bar with AI Usta selected.

A1 root:
- free-form technical-answer chat home degildir,
- chat transcript/history surface degildir,
- root composer gerektirmez,
- two intents bulky card-stack'e donusturulmez.

Natural-language task/symptom capture downstream `SCR-009` / `SCR-019` icinde kullanilabilir; technical authority degismez.

### Gecmis
Primary meaning:
- longitudinal motorcycle history,
- record detail,
- evidence/provenance,
- correction/dispute,
- critical correction reach-back,
- user data export.

Primary approved contexts:
- `SCR-025` — `SCR-030`.

Historical truth entitlement/downgrade nedeniyle kaybolamaz veya gizlenemez.

### Topluluk
Primary meaning:
- community experiences / Q&A reading,
- explicit contribution,
- moderation/review/appeal lifecycle.

Primary approved contexts:
- `SCR-038`
- `SCR-035`
- `SCR-036`.

Community content official numbered guide authority'sini taklit edemez. Permanent social-feed/engagement model bu kararla onaylanmis degildir.

## Motorcycle Context Rule

Selected motorcycle context ilgili tablarda compact ve anlasilir kalmalidir. Motorcycle switching fifth/sixth navigation destination olarak eklenmez; Garaj ve gerekli contextual affordance'lar uzerinden yonetilir.

## Contextual Areas Outside Bottom Bar

Asagidakiler bottom bar item'i degildir; product context'e gore contextual olarak acilir:
- profile/persistence transition,
- migration conflict review,
- collaboration management,
- transfer/archive/delete lifecycle details,
- data export,
- entitlement gate,
- readiness/recovery states.

## Active Physical Work Rule

5-tab shell global navigation modelidir. `SCR-014 Active Guide Step` ve critical recovery/revalidation flows sirasinda bottom bar'in exact visibility/interaction treatment'i henuz final degildir.

Design objective:
- physical task focus bozulmamali,
- accidental navigation active repair state'ini false-complete veya kayip yapmamali,
- current work context safely preserved olmali.

Visual-reference round bu behavior icin PROPOSED treatment uretebilir; user/main-manager review olmadan exact behavior kilitlenmez.

## First-Use Boundary

First-use (`SCR-001` — `SCR-004`) bottom bar'i ilk degerden once zorunlu navigasyon olarak dayatmaz. Motorcycle context yeterince kurulduktan sonra shell devreye girebilir.

Exact first selected tab / landing tab bu kararla kilitlenmemistir.

## Simplicity Rule

Bottom bar'in 5 item olmasi ana sayfalari yeniden dashboard'a cevirmek icin gerekce degildir.

Her root surface tek ana user job'a odaklanir:
- Garaj -> motor baglami,
- Bakim -> ne zaman ne gerekli,
- AI Usta -> ne yapmak / neyi cozmek istiyorum,
- Gecmis -> ne oldu / neye dayaniliyor,
- Topluluk -> diger kullanicilarin ayri-authority deneyimleri.

Core principle:
**Accessible does not mean simultaneously prominent.**

## Approval Boundary

APPROVED:
- five-tab bottom navigation concept,
- tab labels/order,
- center AI Usta role,
- tab-level product responsibility boundaries,
- AI Usta A1 root interaction structure via DEC-0018 / `REF-AIUSTA-001`.

NOT FINALIZED:
- exact icon family,
- visual treatment of A1 intents,
- optional conversational capabilities beyond A1 root,
- active-repair bottom-bar visibility,
- first landing tab,
- platform-specific navigation implementation,
- final component/tokens/animation,
- technology/AI architecture.
