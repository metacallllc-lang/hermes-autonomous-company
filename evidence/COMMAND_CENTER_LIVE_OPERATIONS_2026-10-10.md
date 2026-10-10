# Live company operations view — verified 2026-10-10

The existing Command Center now has a read-only Server-Sent Events (SSE) projection over canonical company state and operational ledgers. Hermes remains the single authoritative CEO loop; the owner retains root authority and veto. Bot Chat remains a bounded deliberation surface.

Verified in production:

- Company Pulse, C-Suite Live, Live Company Timeline, missions/work and structured evidence drill-down render against the running company.
- The feed normalizes recorded cycles, scheduled wakes, work, delegation, worker results, verification and external-effect metadata. Evidence carries source/record hashes; missing measurements stay UNKNOWN.
- Scheduled fire and terminal cycle outcome are distinct. The live production stream automatically updated a pending terminal-record reason to a missing terminal-record reason when the existing recorded cycle bound elapsed.
- Operational summaries exclude source prompts, thought traces, correspondence, recipient details, banking identifiers and raw sensitive tool output. The new evidence view returns structured metadata rather than raw artifacts.
- The dashboard does not trigger work, tools, health regeneration, external effects or a second CEO loop. Browser observation produced no non-GET requests; watched canonical action/governance hashes remained unchanged during the production observation window.
- 124 relevant checks passed: 21 live-operations checks, 33 existing projection checks, 23 existing render checks, 17 state-projection checks and 30 back-to-top checks. Real HTTP SSE reconnect/cleanup/capacity were tested; browser error/recovery handlers were tested with simulated events, separately from transport tests.

Proof limits:

- The observed company projection is BLOCKED. A newer native scheduled wake has no persisted terminal cycle record. This release does not claim that autonomous unresolved-work re-drive completed successfully.
- C-Suite thread state has conflicting convergence/open-work markers. The dashboard exposes an explicit degraded reason.
- Native current worker/executive activity and measured model costs remain incomplete. Recorded historical results are not presented as current activity or measured zero cost.
- Read-only hashes and event deduplication demonstrate the observer's behavior in the tested windows; they do not prove zero historical company duplicate actions.
- No new claim of delivery, reading, contract acceptance, revenue or customer cash collection is made. Existing outbound proof remains SEND ACCEPTED + SENT-FOLDER VERIFIED where source evidence supports it.

This verifies the live observation surface, including truthful failure visibility. Full autonomous company continuity after a bounded discussion remains an open runtime proof requirement.
