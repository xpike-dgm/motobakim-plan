# USER TYPES

Status: DRAFT

| ID | User Type | Goals | Needs | Restrictions | Evidence |
|---|---|---|---|---|---|
| UT-001 | Yeni / az deneyimli self-service owner | Islemi ogrenerek ve ne yaptigini anlayarak guvenli tamamlamak; zamanla bagimsizlasmak | Ayrintili hareket+gorsel+basari kontrolu, preparation, recovery, terminology help | Safety/kritik dogrulama atlanamaz; readiness/match belirsizse application kapanir | Q006-Q007, Q014-Q021, Q050-Q052, Q089, Q141-Q143 |
| UT-002 | Deneyimli self-service owner | Dogru technical info ve kontrollere hizla ulasip islemi verimli tamamlamak | Kisa verified steps/checklist, technical detail, provenance, critical measurements | Speed safety ve critical confirmation'i azaltamaz; oz-beyan readiness kaniti degildir | Q007, Q010-Q011, Q014, Q051-Q052, Q141-Q143 |
| UT-003 | Record-only owner | Kendi tamirini yapmasa da history, docs/photos, upcoming maintenance ve reminders'i duzenli tutmak | Easy record entry, maintenance schedule/history, evidence/provenance, later optional guide transition | Guide kullanmak zorunda degildir; history trust ve data control korunur | Q117, Q141-Q143, Q153 |
| UT-004 | Multi-bike owner | Birden fazla motosikleti karistirmadan takip etmek | Ayrik motorcycle contexts, history/reminders, active bike clarity | Birkaç motosikleti basic ayirmak core expectation'dir | Q062, Q116, Q141, Q146, Q154 |
| UT-005 | Shared-family participant | Ayni motosiklette yetkili ve izlenebilir katkida bulunmak | Owner permission, attribution, edit trail, private-note isolation | Baskasinin kaydi sessizce degistirilemez; access revocable | Q116, Q118-Q119, Q141, Q154 |
| UT-006 | Hobby helper | Baska owner'in motosikletinde izinli sekilde yardim edip kayit katkisi yapmak | Actor attribution, evidence, owner-controlled collaboration | Professional rol ile ayni sayilmaz; rol verified status yaratmaz | Q116, Q118-Q119, Q138-Q141 |
| UT-007 | Paid service / professional contributor | Owner'in davetiyle service record/evidence katkisi yapmak | Service/document context, attribution, evidence | Initial direct target degildir; professional forms/terms owner-first experience'i domine etmemeli; rol automatic verified degildir | Q138-Q140 |

## Core Priority

**CONFIRMED — Q141-Q143**

Ilk product priority:
1. UT-001 yeni/az deneyimli self-service owner,
2. UT-002 deneyimli self-service owner,
3. temel record/history tracking.

UT-003–UT-007 desteklenen adjacent context'lerdir. Advanced shared/work-on-behalf-of-others management daha sonra derinlestirilebilir. Ayrı professional business-management product gelecekte dusunulebilir; ilk owner-first product scope'u degistirmemelidir.

## Segment Minimum Value

**CONFIRMED — Q141-Q142**

- Beginner: learning + safe application.
- Experienced: speed + accuracy.
- Record-only: reliable history/schedule.
- Multi-bike: data/context separation.
- Shared-family: authorized/attributed records.
- Hobby helper: named contribution.
- Paid service: actor + service/document evidence context.

Cost advantage hicbir grupta technical accuracy'nin onune gecmemelidir.

## Cross-cutting States / Contexts

Bunlar ayri persona olmak zorunda degildir:

- **Known-task** — Q006.
- **Symptom-first** — Q006, Q012, Q022.
- **Interrupted-work** — Q028, Q059.
- **Mismatch/modification** — Q026, Q038-Q039, Q066-Q067, Q102-Q104.
- **Recovery** — Q025-Q027.
- **Task-specific readiness** — Q050-Q052.
- **Readiness challenged / re-validation** — Q096-Q098, Q126-Q128.
- **Professional recommendation / mandatory closure** — Q100-Q101, Q126-Q128.
- **Roadside/offline** — Q090-Q091, Q147-Q149.
- **Community contributor** — Q080-Q084, Q105-Q108, Q130.
- **Data-owner** — Q092-Q094, Q129-Q131.
- **Ownership-transfer** — Q120, Q135-Q137.
- **Archived motorcycle** — Q121.
- **Active-repair accessibility** — Q125, Q150-Q152.
- **Account-light first-use -> persistence trigger** — Q123, Q153-Q155.

## Current User Motivation Evidence

**CONFIRMED FOR CURRENT USER — Q089:**
1. Islemi kendi tamamlamak
2. Ogrenip bagimsizlasmak
3. Masrafi azaltmak
4. Zaman kazanmak
5. Surecten keyif almak

Batch 05 segment refinement bu siralamanin tum user types'a aynen uygulanmadigini CONFIRMED etti.

## Current Segmentation Interpretation

**INFERRED, NOT FINAL:** Global `beginner/experienced` etiketi tek basina yeterli olmayabilir. Task-specific readiness, current context, ownership/collaboration state ve user's first-value intent ayni kisinin product experience'ini degistirebilir.

## Open Segmentation / Validation Questions

Product-level priority yeterince net. Market size, willingness-to-pay, segment frequency ve acquisition potential bu discovery kullanici cevabindan cikmaz; ileride ayri research/validation gerekir.
