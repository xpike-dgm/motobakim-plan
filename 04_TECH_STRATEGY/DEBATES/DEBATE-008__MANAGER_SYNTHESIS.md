# DEBATE-008 — Manager Synthesis: Physical Data/Backend Working Direction

Status: `USER APPROVED WORKING DIRECTION / DEC-0035 / NO-CODE / NO ACCOUNT / NO PURCHASE / ADR NOT READY`  
Date: 2026-09-18

## Plain-language result

Kavriva için şu aşamada en dengeli başlangıç yönü **Supabase merkezli yönetilen yapı**dır. Bunun nedeni Supabase'in
tek başına daha güvenli veya eksiksiz olması değil; teknik olmayan tek sahibin günlük olarak daha az ayrı hizmet,
fatura, erişim anahtarı ve arıza hattı yönetmesini sağlamasıdır.

Bu öneri “uygulama doğrudan Supabase'e bağlansın” anlamına gelmez. Mobil uygulama ve şirket içi tarayıcı paneli,
hassas işlemleri her zaman Kavriva'nın sunucu/API kapısından geçirir. Supabase'in hazır paneli de Kavriva'nın şirket
içi yönetim paneli değildir.

Modüler Neon + Render + R2 seçeneği veri taşıma ve parça bağımsızlığını daha görünür kılar; fakat ilk günden üç ayrı
sağlayıcı, üç arıza/fatura yüzeyi ve daha fazla erişim anahtarı doğurur. Bu, güvenlik avantajını teknik olmayan tek
sahip için işletme riskine çevirebilir. Bu nedenle modüler seçenek ilk yedek yön olarak korunur.

## Proposed reversible Phase-4 direction

User approval is requested for the following working direction:

1. **Managed Supabase core:** PostgreSQL, Auth and private Storage are the initial physical core candidates.
2. **Mandatory server/API authority:** Supabase Edge Functions or an equivalently bounded server runtime is the initial
   low-operations candidate for the Kavriva API boundary. High-consequence actions never rely on direct client authority.
   The exact runtime remains replaceable until the Phase-5 ADR.
3. **Defense in depth:** RLS and Storage policies remain mandatory defenses, but they are not the sole approval,
   publication, recall, provenance, audit or separation-of-duties authority. `service_role`/secret keys remain server-only.
4. **Bounded offline:** mobile receives only the selected motorcycle/task package and compact safety/recovery closure;
   no full-library download and no provider-native silent last-write-wins authority.
5. **Independent recovery controls:** database backup does not cover Storage object bytes. Object copy/export, protected
   audit and the anti-resurrection floor require custody sufficiently independent from the ordinary Supabase project.
6. **Browser Internal Operations:** the Kavriva panel remains a separate browser product surface. Supabase Studio is
   provider administration only and cannot approve, publish, recall, change roles or replace product audit evidence.
7. **No current purchase:** no account, Pro plan, PITR add-on or external adjunct is authorized by this direction.

This is a reversible Phase-4 planning choice, not a production claim or provider contract.

## Why the two reviewers disagreed

| Review lens | Preferred direction | Sound reason |
|---|---|---|
| Solo-owner / TCO / operability | Candidate A — Supabase-centered | Fewer routine provider surfaces may reduce owner and AI coordination burden. |
| Security / recovery / exit | Candidate B — modular managed | API, database and object boundaries are physically explicit and clean-room exit maps more directly to PostgreSQL/S3-style primitives. |

Both reviewers classified every F01–F16 scenario as `HELD`, because this phase forbids real build, restore and exit
tests. The disagreement is therefore a trade-off, not contradictory evidence. The manager gives greater weight to the
approved nontechnical-solo-owner rule while importing the modular review's safeguards into Candidate A.

## Controls imported from the modular review

Candidate A is retained only with these non-negotiable separations:

- server/API mediation for sensitive reads and all high-consequence mutations;
- private quarantine before object activation;
- database, object bytes, protected audit and negative floor treated as separate recovery planes;
- stable IDs and logical export suitable for clean-room import outside the normal provider account;
- provider/account/billing outage represented by owner-readable `HELD`, `UNKNOWN` or `UNAVAILABLE` states;
- task-scoped AI access without owner, billing, `service_role`, unrestricted SQL or global object credentials;
- dated provider changelog and compatibility hold before changed defaults reach production.

## Cost reading

The only simple current headline is Supabase Pro at roughly USD 25/month before tax/FX and extras. That figure is **not**
the safe total. API compute, independent object backup, protected audit/floor, monitoring, scanning, notification,
restore/exit drills, support and incident usage remain `UNRESOLVED`. PITR starts around USD 100/month and is therefore
not assumed for the early budget. Free service tiers may support later exploration but cannot stand in for production
backup, audit, support or recovery evidence.

The direction is acceptable for planning only because it can begin with fewer mandatory paid surfaces and keep optional
capabilities off. Before any paid account decision, one normalized bill of materials must show minimum-safe closed test,
minimum-safe Android production, P2/P3, incident month, restore drill and exit drill. The owner's TRY 2,000–3,000/month
figure remains a future planning ceiling, not current authorization.

## Reversal triggers

Candidate A is withdrawn and Candidate B is reopened through the same evidence gate if any of these occur:

1. sensitive or high-consequence flows cannot be kept behind the API boundary;
2. required server runtime, independent audit/floor, object backup and monitoring push the minimum-safe recurring total
   outside the owner-approved envelope;
3. service-role, RLS, Storage or provider-console bypass cannot be bounded and negatively tested;
4. old restore can resurrect recall, revoke, deletion, suspension or accepted operations;
5. database + objects + audit + identity/policy/config/package cannot pass a cross-plane restore manifest;
6. stable logical export and clean-room import outside the normal account cannot preserve required negative behavior;
7. provider outage, billing restriction or incident response requires the owner to debug, use SQL/SSH or repair services;
8. Supabase-specific Auth/Storage/Functions coupling makes exit materially less safe than the modular fallback.

Candidate B is not an automatic winner after a reversal. It must still prove that three-provider billing, outage,
credential and support coordination can be operated by bounded AI workflows without owner debugging.

## What remains deliberately open

- exact region and legal/data-transfer assessment;
- exact server/API runtime after the initial low-operations candidate;
- protected audit/floor provider and custody;
- object backup/export destination;
- malware/archive/preview isolation service;
- monitoring, notification and support services;
- recovery objectives, retention periods and numeric service limits;
- final pricing, tax/FX and budget-hold thresholds;
- all real negative, restore, exit, device and load evidence;
- Phase-5 ADR and Gate 4 -> 5.

## Owner decision

The owner approved the following statement on 2026-09-18 with `tamamdır onaylıyorum`:

> Kavriva will continue Phase-4 planning with a managed Supabase-centered backend as the reversible working direction,
> always behind the approved Kavriva server/API authority boundary. Neon + independent API + R2 remains the first
> fallback. This approval does not authorize code, an account, a subscription, PITR, a purchase, a Phase-5 ADR or a
> gate transition.

Decision authority: `DEC-0035`. All reversal triggers, unresolved costs and later evidence gates in this synthesis remain
binding.
