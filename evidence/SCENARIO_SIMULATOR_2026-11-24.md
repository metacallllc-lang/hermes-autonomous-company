# November 24: scenario simulator and the faults it found

The company's loop code was run through randomized scenarios in an isolated copy, to find faults before buyers do.
**No customer, payment or revenue is claimed.**

## What it is

A seeded simulator runs a copy of the private scheduling, executive-lane, veto and reply code against a simulated
clock, model, marketplace and crashes. A wall inside the process refuses network calls, child processes, reads of the
live company or credentials, and writes outside its folder. All 37 attempted escapes were blocked.

## Results

| Check | Result |
| --- | --- |
| Random scenarios before the repairs | 42 of 120 broke a rule |
| Random scenarios after the repairs (two sets of 60) | 0 broke a rule |
| Larger run, interim: 1,082 of 2,000 scenarios, 62,225 simulated wakes, 3,931 replies | 0 broke a rule |
| Seven known earlier faults, put back one at a time | All seven detected |
| Damaged or unreadable veto records (14 tests) | Veto ignored in 10 before, 0 after |
| Simulated wait for a marketplace reply | Median 90 minutes, 90th percentile 188 |

Most of the reply wait includes the owner's 60-minute veto window, which was not changed.

## What was repaired

- A veto list, policy or queue that could not be read was treated as empty. It now holds the action.
- A send interrupted by a crash could be repeated. It is now recorded before it starts and never repeated.
- Two processes could overwrite each other's queue changes. Changes are now locked per entry.
- A reused process number could hold the wake lock. The process start time is now checked.
- A wake that ended in error could leave no next wake. It is now started again.
- A reply could go out after the owner had answered, and a buyer who wrote again could be held by a duplicate guard. Both are corrected.

## Seen live

The marketplace reply that was still queued in the [earlier November 24 note](RUNTIME_RECOVERY_AND_REPLY_SPEED_2026-11-24.md)
was later recorded as sent and verified in the company's own receipt. An earlier attempt that day failed because the
reply box was not found. A sent reply is not a customer.

## Limits

- The simulator checks the loop's rules, not whether the executives' work is good or a buyer will pay.
- It does not cover model-provider routing, real marketplace pages, gateway freezes, email, social posting or order delivery.
- Zero violations means none of the rules it knows were broken in the scenarios it ran. It is not proof of no faults.
- The larger run was still in progress when this was written.
- The last full guard run (November 23) had 25 of 170 suites failing, and the source of unexplained gateway stops is still unknown.

The simulator and the company's code remain private.
