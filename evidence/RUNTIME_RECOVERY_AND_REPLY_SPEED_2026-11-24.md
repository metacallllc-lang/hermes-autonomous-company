# November 23–24: stalled executives, killed wakes and slow marketplace replies

The owner reported the CEO and CRO stuck, and marketplace buyers waiting too long for a reply. Both were true.
This note records the causes, the repairs, what was seen working live, and what was not.
**No customer, payment or revenue is claimed.**

## Causes and repairs

| Symptom | Measured cause | Repair |
| --- | --- | --- |
| Nearly every CEO wake failed for about 2.5 hours (November 23) | Each model call allowed one inference provider only; that provider was rate-limited while others served the same model | The same model may be served by another provider, cheapest first. Switching to a different model stays off |
| CRO marked failed, every new CRO turn refused (November 23) | The gateway was killed under a CRO turn; its session never recorded an end, so cleanup raised an error on every wake and the lane stayed occupied | An interrupted turn whose process is gone, with no remaining worker or claim, can be closed as failed |
| A seat hidden for 45 minutes | A wake chose a turn, ended without dispatching it, and its reservation outlived it | A reservation holds only while the wake that made it is running |
| CEO loop stopped (November 24, 18:13 UTC) | A failed operating-system shutdown or restart attempt ended the gateway, a CRO turn and the CEO wake. The next wake is scheduled only when a wake finishes | A wake that started, never finished and has no process left is started again, at most three times an hour, behind the owner's pause and hold controls |
| A killed executive turn was lost | Failed work identities are permanently fenced against replay | A turn killed with its gateway gets one new turn in the same slot, or in the next slot. Other failures are not re-run this way |
| Buyers waited hours | The CRO looked at the inbox only in its 3-hour slot, and a failed send was dropped | A waiting message opens its own CRO turn, once per message. A send that failed before anything was typed is tried again, up to three attempts, re-checking the veto and whether the thread was answered |
| Marketplace reads failed or hung | A wake's inbox check and the CRO drove the same browser tab at the same time | One task at a time holds the tab; a lost browser reply times out after 60 seconds |
| Dashboard showed "Stagnation" for a stopped loop and for a quiet one | One label covered both | It now reads "No verified effect" with the wake count and the time of the last wake, and "CEO loop not firing" after an hour without one |

The owner's veto window was not changed. It is now the largest fixed delay on a marketplace reply.

## Seen live

- After the provider change, the next wake completed and delegated. After the lane repair, the stuck CRO turn closed and the CRO's next turn succeeded.
- On November 24 the interrupted CRO turn closed at 18:32 UTC, its same-slot re-run was dispatched at 18:40 UTC, and that turn queued a reply to the waiting buyer under the veto window.

## Not yet seen live

- Automatic restart of a killed wake, a message-opened CRO turn, a retried send, and the tab lock under real overlap. Each passed targeted tests only.
- The queued reply had not been sent when this was written. The re-run's own marketplace read hung on the tab overlap that the lock now addresses.

## Checks

Suites run after the November 24 changes: event loop, CRO capability, seat action queue, cycle invocation, order desk, marketplace
monitor and delivery boundary all pass; the failure-lifecycle suite passed after the lane repair. Seat action
carry-over passed before the browser-tab change. One wake-lifecycle test fails, as it did before these changes. The inference-guard suite fails 10 of 14 tests, the same ones before and after the provider
change. The last full guard run (November 23) had 25 of 170 suites failing.

## Corrections

- The first retry, on November 23, covered every kind of failure. It now covers only turns killed with their gateway.
- That day's account said a failed turn was already re-offered in its own slot. It was not.
- The lane repair uses a narrower idle check than the one elsewhere in the failure lifecycle: it does not require the whole gateway to be idle.
- Allowing other providers loosens the spending guard: a dearer provider could exceed the reserved estimate. Measured daily spend was in line with before.

## Open

- What triggered the shutdown attempt is unknown. The gateway also stalls and restarts every day or two, and executive turns run inside it.
- Over the last seven days, 227 of 321 executive assignments passed verification (71%); the CRO's standing turns passed 11 of 24.
- One cycle on November 24 ended in a database read error during a gateway restart; its delegated turn continued.
- The private code now has version history and a private backup. Code, credentials and business data remain private.
