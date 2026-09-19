# DEBATE-006 — REVIEW B: MOBILE PLATFORM, ACCESSIBILITY, DEPENDENCY AND MAINTENANCE

Status: `COMPLETE — PASS_WITH_CHANGES AS DIRECTION / REJECT AS ADR`
Date: 2026-09-17
Reviewer: independent Luna Max sub-agent

## Verdict

`PASS_WITH_CHANGES` only as a Phase-4 working direction. `REJECT` for an ADR or Gate 4 -> 5.

The draft correctly treats OTA and background/push as non-authoritative, separates KMP-native from KMP-Compose and
requires native ownership. Lifecycle recovery, accessibility, dependency closure, support terminology and exit evidence
needed stronger gates.

## Findings and Disposition

| ID | Severity | Finding | Required correction | Manager disposition |
|---|---|---|---|---|
| B-C1 | Critical | “Exact saved context” could promise process-kill/physical-state restoration. | Restore only the last durable committed checkpoint; uncommitted state is unknown/partial; require atomic/crash recovery and revalidation. | Accepted in S3. |
| B-C2 | Critical | Framework accessibility APIs/stability were too easy to mistake for product evidence. | Critical-flow matrix for both assistive-technology stacks and later real-device acceptance; framework support alone cannot pass. | Accepted. Phase 4 specifies the matrix; execution remains prohibited until authorized. |
| B-C3 | Critical | Native escape/dependency closure was still hypothetical even though camera/files/background/storage are baseline. | Capability-to-owner/dependency/toolchain/lifecycle/accessibility/fallback/EOL/security table; ownerless critical capability rejects. | Accepted as mandatory native/dependency closure. |
| B-M1 | Major | Support-floor table mixed supported, CI-tested, product floor, toolchain and store concepts. | Separate terms, pin version snapshots and hold until product OS/device policy exists. | Accepted; terminology and version-specific matrix added. |
| B-M2 | Major | Expo runtime compatibility could still be confused with release/security authority. | Store/binary release is TCO default; OTA stays disabled unless a future DEBATE-005 authority envelope is approved. | Accepted and preserved. |
| B-M3 | Major | KMP/Compose toolchain coupling was under-modelled. | Track Kotlin/KMP/Compose/compiler/Gradle/AGP/JDK/Xcode/Swift/library compatibility, rehearsals and EOL. | Accepted in TCO. |
| B-M4 | Major | Backup/restore and secure-storage authority classes were incomplete. | Distinguish cache/history/private/profile/trust/key backup rules; test clone/key-loss/replay/quarantine. | Accepted as S15. |
| B-M5 | Major | Native escape was not a measurable framework exit plan. | Add portable/bound assets, data/key continuity, migration and replacement path. | Accepted as exit dossier. |
| B-M6 | Major | TCO/device evidence remained non-decisive. | Preserve benchmark uncertainty; define later acceptance oracles, capacity, patch/upgrade/specialist coverage. | Accepted; no benchmark is invented and decision remains held. |

## Primary Evidence Used by Reviewer

- Android Doze: https://developer.android.com/training/monitoring-device-state/doze-standby
- Android WorkManager: https://developer.android.com/develop/background-work/background-tasks/persistent
- Apple background strategies: https://developer.apple.com/documentation/backgroundtasks/choosing-background-strategies-for-your-app
- Flutter platform channels: https://docs.flutter.dev/platform-integration/platform-channels
- React Native native modules: https://reactnative.dev/docs/turbo-native-modules-introduction
- Expo development builds: https://docs.expo.dev/develop/development-builds/introduction/
- Expo runtime versions: https://docs.expo.dev/eas-update/runtime-versions/
- Compose compatibility: https://kotlinlang.org/docs/multiplatform/compose-compatibility-and-versioning.html
- Android Auto Backup: https://developer.android.com/identity/data/autobackup

## Final Reviewer Position

The corrected text is suitable for continued Phase-4 evaluation only. A framework decision remains held until product
support floors, lifecycle recovery, accessibility, native/dependency ownership, release evidence, actual team/TCO and
exit conditions are complete. Gate 4 -> 5 remains closed.

