# Hermes v0.22.1 production migration — October 15, 2026

**Runtime cutover: PASS / PROVEN-SCOPED. Architectural convergence: outstanding.**

This sanitized summary records the production verification window ending October 15, 2026, 10:05 America/Guatemala. Sources reviewed: private `FINAL_MIGRATION_RESULT.md`, `PRODUCTION_CUTOVER_LOG.md`, `PRODUCTION_VERIFICATION.md` and `GATE_RESULTS.md`. Raw reports and operational paths remain private. This is a dated evidence summary, not a live health claim or a fresh rerun of the migration tests.

## Verified milestone

| Observation | Evidence and boundary |
|---|---|
| Exact production pin | Migrated from `b23600860f82bd66d345c0a1baefd0f264605955` to tag `v0.22.1`, detached at `297552a9d646119871391d202509822cd86330df`; git HEAD and runtime `code_sha` agree. Worktree clean at hand-back. |
| Target selection | During the migration window, update-channel checking selected stable v0.22.2 (`d923a5eb487a`), not the tested target. Normal update was not run; verified tag resolution, exact checkout and target-supported dependency synchronization were used. |
| Rollback readiness | Independently verified SQLite backup-API copies: 8/8 integrity checks passed; git bundle and HEAD matched; 23,622 manifest entries, zero missing files or hash mismatches. An initial broken backup attempt was rejected, fixed and re-made before cutover. Rollback remained available and unused. |
| Dependency/config migration | Supported dependency sync completed; root home and all 18 executive profiles migrated from schema 50 to 51. |
| Isolated safety gates | Gate A, Gate B and governance negative matrix passed in a redirected staged home with a loopback mock provider. Deny-before-effect and hook error/timeout fail-closed behavior were measured there. This was host isolation, not a VM boundary; epoch/generation/lineage assertions retained partial coverage and delegated subagents were not exercised. |
| Production verification | The reported Phase 8 probe passed 12/12 checks: one gateway owner, no idle-exit gateway debris, governance plugin loaded with hook evidence during the synthetic session, durable cron admission, company-state integrity and reachable Command Center. These are the probe's checks, not a claim that every architecture acceptance criterion passed. |
| Scoped restart recovery | Idle restart observed one owner → zero → one. In-flight synthetic work retained one execution row through `claimed → running → unknown`, with no replay or duplicate row and one owner after recovery. Supervisor honored the operator pause and recovered. UNKNOWN remained UNKNOWN. |
| Model policy correction | A pre-existing automatic fallback chain to two paid models was found in root + six profile configs and cleared after backups. Free routes and the explicit `escalate` alias remained; paid escalation stays deliberate. This does not measure total model cost or prove universal budget enforcement. |

The existing CEO adapter already used native cron admission; compatibility checks did not constitute a served-profile migration. Company execution resumed and synthetic jobs were removed. Wrapper `rc=0` and `idle_refused` do not independently establish useful work or correct idle eligibility.

## Outstanding work and explicit limits

- **Served-profile convergence is not complete.** The 18 executives remain in v0.22.1's "standalone by config (temporary compatibility shim)" arrangement. No profile was switched to served execution during cutover. Absence of idle-exit gateway debris does not establish that architecture move.
- **Command Center execution identity remains partial.** It already reads canonical execution and session stores; its adapter is not absent. Its payload lacks `execution_id`, `owner_epoch`, `generation` and receipt fields, so stale/current execution discrimination by identity remains unverified. The surface was not modified during cutover.
- **Receipt settlement is UNKNOWN.** No canonical receipt was observed settling an attempt in this window. Production DENY cases against business tools were not re-exercised; isolated-stage governance proof is not production business-tool coverage. Model-call hooks are not budget-deny gates; route controls remain load-bearing.
- **Install metadata drift remains recorded.** The install stamp still names the old commit; git and runtime identity establish the pinned version. Metadata was not manually rewritten to conceal drift.
- **Recovery proof is scoped.** Synthetic restart tests do not establish full 24/7 operation, universal exactly-once effects, or retirement/continuation of the specific older October 14 restart child. Earlier dated failures and open boundaries remain preserved.
- **No economic outcome is claimed.** No mail, social, payment or customer/prospect action was taken to prove cutover. Runtime health establishes no delivery, reply, customer, revenue, cash, conversion or sponsor award. Those measurements remain separate; UNKNOWN is not zero.

The governing architecture remains one CEO, one canonical company state, human owner root + veto, and watchdog-only scheduling. Runtime cutover success does not establish full architectural convergence.
