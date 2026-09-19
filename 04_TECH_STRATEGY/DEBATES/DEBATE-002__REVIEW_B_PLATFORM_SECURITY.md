# DEBATE-002 — REVIEW B: MOBILE PLATFORM, SECURITY & OPERATIONS

Status: `COMPLETE — PASS_WITH_CHANGES`
Date: 2026-09-17
Reviewer: independent Luna Max adversarial review using primary/official platform sources
Repository edits by reviewer: none

## Verdict

`PASS_WITH_CHANGES` for continuing the direction; `NOT ADR-READY`. Treating C+D as already enforceable would be a
rejection until the critical findings are closed.

## Critical Findings and Disposition

1. **Emergency recall/outage undefined.** APNs/FCM cannot be the sole emergency channel; highest-consequence work
   needs always-online or tightly bounded authority; emergency suspension/out-of-band reach-back is separate work.
   Disposition: incorporated as explicit limitation and unresolved decision.
2. **Safe-stop availability was asserted, not an offline-start precondition.** A package can be missing, evicted,
   incompatible or recalled. Disposition: complete independently reviewed version-pinned recovery coverage is now
   required before offline start; impossible perfect recovery is no longer promised after unexpected device failure.
3. **Release-bound metadata is not replay/downgrade protection.** Disposition: technology-neutral anti-rollback,
   manifest/dependency integrity, authority separation and restore distrust properties added.

## Major Findings and Disposition

- Server/client/last-reconciled recall states separated.
- Highest dependency risk propagates; unknown holds.
- Time is evidence, not authority; normal reboot and restore/clone are distinguished.
- Old-client minimum parseable envelope and pre-use capability negotiation added.
- Partial/mixed packages require complete snapshot/dependency acceptance.
- Browser timeout becomes `outcome unknown` with idempotent result reconciliation.

## Official Evidence

- Apple background pushes: https://developer.apple.com/documentation/usernotifications/pushing-background-updates-to-your-app
- Android Doze/App Standby: https://developer.android.com/training/monitoring-device-state/doze-standby
- Firebase message lifespan: https://firebase.google.com/docs/cloud-messaging/customize-messages/setting-message-lifespan
- Firebase message priority: https://firebase.google.com/docs/cloud-messaging/customize-messages/setting-message-priority
- Apple background downloads: https://developer.apple.com/documentation/foundation/downloading-files-in-the-background
- Android Auto Backup: https://developer.android.com/identity/data/autobackup
- Android SystemClock: https://developer.android.com/reference/android/os/SystemClock.html
- Android in-app updates: https://developer.android.com/guide/playcore/in-app-updates
- Android AtomicFile: https://developer.android.com/reference/android/util/AtomicFile.html

## Claims That Remain Prohibited

- push/background delivery guarantees immediate recall;
- release ID alone prevents replay/downgrade;
- local time alone proves freshness across restart/restore;
- safe recovery is guaranteed when its local package is absent or unusable;
- app-store prompts guarantee old-client elimination;
- online browser mutation has a known result after every network timeout.

Final position: `PASS_WITH_CHANGES`; later decisions need owners and exit criteria before ADR.
