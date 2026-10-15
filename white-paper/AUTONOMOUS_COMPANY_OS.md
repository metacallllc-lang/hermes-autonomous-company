# Autonomous Company OS

## Draft public white paper

### Abstract

Large language models can reason, write, analyze and operate tools, but an autonomous company requires more than model intelligence.

It requires a persistent operating layer that separates reasoning from authority, preserves company state, coordinates specialized executives and workers, verifies external effects, survives failures and allows humans to retain constitutional control without becoming routine dispatchers.

This paper describes the emerging architecture and operating principles behind the MetaBot Autonomous Company OS.

## 1. The model is not the company

A model can be replaced.

The company must persist.

Therefore the operating system owns:

- mission;
- authority;
- state;
- evidence;
- workflows;
- decisions;
- recovery;
- cost controls;
- tool integration;
- business records.

The model supplies reasoning compute inside that structure.

## 2. Human authority without human middleware

Many “human-in-the-loop” systems accidentally make the human the workflow engine.

The preferred boundary is different:

**Human:** root authority, veto, reserved decisions, irreducible acts.  
**AI company:** ordinary strategy and execution inside enacted authority.

This reduces unnecessary human intervention without removing human sovereignty.

## 3. Constitutional boundary

The system can improve execution but cannot autonomously expand its own permission.

This gives a simple invariant:

> **Optimization may change how work is done. It may not silently change who is allowed to authorize it.**

## 4. Executive specialization

One general-purpose agent can become a bottleneck.

The architecture instead uses an executive layer:

- CEO;
- CFO;
- COO;
- CRO;
- CMO;
- CTO.

The CEO integrates tradeoffs while executives contribute specialized reasoning and own departmental continuity.

## 5. Delegation

Work is delegated to bounded child agents, workers and tools.

A child can be isolated from unrelated context and return a result.

But a returned result is not automatically accepted as truth.

It must be reconciled with:

- requested task;
- evidence;
- authority;
- acceptance criteria;
- resulting external state.

## 6. Evidence before narrative

A company cannot be governed by confident prose.

The architecture therefore distinguishes evidence levels.

Examples:

```text
intent ≠ execution
configuration ≠ runtime usability
provider accepted ≠ delivered
internal ledger ≠ company-wide reality
historical proof ≠ current connectivity
```

## 7. Failures as operating data

Autonomous systems will fail.

Useful autonomy therefore requires:

- detection;
- classification;
- repair;
- persistence;
- circuit breaking;
- correction of false claims;
- continuity after repair.

A production system should become more truthful after an incident.

## 8. Memory and canonical state

Conversational memory is useful but cannot become the hidden constitution.

Canonical records must allow the company to answer:

- What is true now?
- What was decided?
- Who had authority?
- What evidence supports it?
- What is historical?
- What remains unknown?

Historical memory experiments using an inspectable Obsidian-based second brain reinforced these principles even where the specific integration may later change.

## 9. Economics

A technically autonomous company that cannot create value is incomplete.

The operating system should measure:

- pipeline;
- conversion;
- cash collection;
- delivery;
- margin;
- retention;
- enterprise value;
- model / infrastructure cost;
- owner intervention cost.

Technical repairs should increasingly become interrupts to an economic default workload.

## 10. Model routing

A company should not depend on one model provider.

Models can be routed based on:

- suitability;
- cost;
- reliability;
- context requirements;
- latency;
- availability.

The system must preserve authority and evidence even when the reasoning model changes.

## 11. Public evidence

This project intentionally publishes facts while keeping source code and sensitive evidence private.

The goal is to make claims inspectable without exposing:

- credentials;
- customer privacy;
- banking data;
- exploitable internal detail;
- proprietary implementation.

## 12. Research direction

The broader question is not whether humans or AI should “win.”

It is:

**What operating architecture lets humans retain sovereignty while AI dramatically expands the amount of useful work that can be performed?**

The Autonomous Company OS is one attempt to answer that question in production rather than simulation.

## 13. Architectural continuation — October 13, 2026

Sections 1–12 preserve the October 9 draft. This dated continuation incorporates the contracts now explicit in [GOVERNANCE.md](../GOVERNANCE.md), [ARCHITECTURE.md](../ARCHITECTURE.md) and [CONTINUOUS_COMPANY_LOOP.md](../CONTINUOUS_COMPANY_LOOP.md). These are required architectural boundaries; documentation alone does not prove runtime enforcement.

### Propose → Commit → Audit

Agents, the CEO, C-suite and Bot Chat may propose decisions, work and state changes. Conversation output is proposal, not canonical company truth. A decision within enacted authority may authorize execution without establishing that execution succeeded.

Only the existing authorized canonical-state writer may commit durable truth. It must validate write authority, intended mutation, source identity/session and timestamp, evidence references, delegation context and admission criteria; record provenance and the admission result; and refuse missing, stale, contradictory or insufficient support.

Independent verifiers establish outcome and convergence against evidence and acceptance criteria. Commit alone is not outcome acceptance. Pending, rejected and ambiguous outcomes retain their status; an authorized writer records corrections or rollback with evidence. Only admitted, evidence-backed state informs the next loop. Unknown remains **UNKNOWN**.

### Evidence-gated IDLE

`IDLE` is a proposed state transition, not an executive assertion. The authorized writer must refuse it without fresh exhaustion/eligibility evidence covering:

- unprocessed events;
- eligible economic opportunities;
- due follow-ups;
- pipeline review/requalification;
- due bounded discovery;
- economically useful capability repair.

The record must include checks, supporting evidence, reasons for ineligibility and the next event/deadline/watchdog wake condition. An empty inbox, zero selected work or an open pipeline count proves neither exhaustion nor eligibility. Missing or ambiguous evidence cannot authorize sleep. Independent verification must accept or reject the committed idle outcome. Discovery remains bounded and useful; the contract does not require constant inference or manufactured work.

### Mutable surfaces and sealed authority

| Class | Architectural rule |
| --- | --- |
| `MUTABLE` | Operational state, opportunity ranking and non-protected prompts/configuration may change within enacted authority; canonical writes still require provenance, evidence and authorized admission. |
| `MUTABLE_WITH_ADMISSION` | Routing, harness/workflow/selector logic, state writers and verifiers require a recorded cause, bounded scope, baseline/version, tests, independent verification and accept/reject/rollback admission before production acceptance. |
| `SEALED` | Constitutional authority, owner root/veto, root grants/authentication/recovery, delegation ceilings, protected resources/destinations and audit requirements are protected from ordinary agent or optimization-loop mutation; the existing reserved authority process governs changes. |

A mutable surface cannot weaken a sealed boundary or expand the actor's authority.

### Verification must also be verified

Recurring verifier regression, and regression before admitting verifier changes, must exercise `KNOWN_GOOD`, `KNOWN_BAD` and `AMBIGUOUS/UNKNOWN` fixtures. The expected decisions are acceptance, rejection and unresolved status respectively. Coverage must include evidence sufficiency, authority, committed-state convergence and idle eligibility. Expected versus observed results and independent review of failures must be preserved. A verifier cannot establish its own adequacy by self-report; passing fixtures alone are not live production proof.

### Verifiable, destination-aware delegation

The required evidence chain is:

```text
root principal
→ agent identity
→ delegation
→ attenuated scope
→ normalized action/tool + arguments
→ authorized resource/destination
→ execution
→ verified outcome
```

Every consequential delegation must trace to its parent grant and policy decision. Child scope may narrow the parent grant, never exceed it. Neither the CEO nor a protocol or gateway creates constitutional authority by delegating or transporting a request.

For network-capable tools and agents, authorization must evaluate identity, resource, normalized parameters and destination together with action class. Permission to use a tool does not authorize arbitrary discovery URLs, internal/loopback targets, metadata or credential endpoints, or unregistered remote peers. Protected destination boundaries remain sealed.

### Event-driven continuation inside the existing company loop

Meaningful events should wake the existing CEO, which loads canonical state, verifies/reconciles affected work, ranks eligible opportunities and dispatches bounded executive lanes. Terminal results feed the next event. Failed work remains failed; replacement requires distinct identity/provenance and fresh admission, while fresh opportunities remain separate from replacement semantics.

The existing **two-hour scheduled wake is watchdog/dead-man recovery only**, not normal cadence or a reason to delay eligible work. Per-role lanes and consequential resource locks bound concurrency. One CEO and one canonical company state remain authoritative; no new scheduler, state plane or architecture layer is introduced. The owner remains **root + veto**, not routine dispatcher.

> **The loop may optimize execution. It may not optimize or expand its own authority.**

### Doctrine and demonstrated enforcement

The public classification through October 13 is **PARTIAL / PROVEN-SCOPED**. Preserved October 12 evidence supports event-driven failure continuation between watchdog wakes and **213.47 seconds** of CFO/CMO native execution overlap for that observed pair. Separate bounded follow-up repair acceptance and sends do not combine into a universal successful continuation claim.

Full successful executive completion → immediate event wake → independent verification → reconciliation/retirement → next economic work remains **NOT PROVEN**, as does full 24/7 continuity. Complete enforcement of the state-commit, idle and verifier-regression contracts is not established by those observations.

Provider acceptance plus Sent-folder verification does not imply recipient delivery, reading, replies, customers, revenue or cash. Financial measurements remain **UNKNOWN** unless independently established. [CURRENT_STATE.md](../CURRENT_STATE.md), [TRACTION.md](../TRACTION.md), [PUBLIC_EVIDENCE_INDEX.md](../PUBLIC_EVIDENCE_INDEX.md), [DEMO.md](../DEMO.md) and [README.md](../README.md) define the public evidence boundary; the [dated case-study continuation](../case-study/FROM_AGENT_TO_AUTONOMOUS_COMPANY.md#phase-7--event-driven-continuation-and-evidence-gated-idle) records the reported debugging separately.

## 14. Runtime admission and consequential authority — October 15, 2026

**Runtime cutover: PASS / PROVEN-SCOPED. Architectural convergence: outstanding.** Section 13 remains the October 13 snapshot. This continuation separates the observations in the [October 15 migration record](../evidence/HERMES_V0_22_1_PRODUCTION_MIGRATION_2026-10-15.md), covering the window ending 10:05 America/Guatemala, from target controls in [ARCHITECTURE.md](../ARCHITECTURE.md), [GOVERNANCE.md](../GOVERNANCE.md) and [ROADMAP.md](../ROADMAP.md). Publishing this paper does not rerun production verification.

The intervening [October 14 record](../evidence/RECONCILIATION_CONTINUATION_PROOF_2026-10-14.md) established reconciliation/retirement and autonomous continuation into internal economic work for a scoped CRO lineage. Its first recovery wake was expedited by a test notification; later ordinary continuation was separately evidenced. That result advances the earlier snapshot without establishing universal wake latency, full unattended continuity or external economic conversion.

### Exact-pin migration as an admission result

Production moved from `b23600860f82bd66d345c0a1baefd0f264605955` to **Hermes v0.22.1**, detached at `297552a9d646119871391d202509822cd86330df`, with agreement between git HEAD and runtime `code_sha`. Supported dependency synchronization completed; root and all 18 executive profiles migrated from schema 50 to 51. During this window the stable channel selected v0.22.2, outside the tested target, so normal update was not run. Exact target verification, rather than channel naming, defined the admitted version.

The rollback checkpoint was independently verified before cutover: **8/8 SQLite integrity checks**, matching git bundle/HEAD, **23,622 manifest entries**, zero missing files and zero hash mismatches. A broken initial backup attempt was rejected and re-made. Rollback remained available and unused; checkpoint integrity does not establish that a production rollback was exercised.

| Evidence surface | Observed result | Limit |
| --- | --- | --- |
| Isolated stage | **Gate A PASS; Gate B PASS; governance negative matrix PASS**. Deny-before-effect and hook error/timeout fail-closed behavior measured with a redirected staged home and loopback mock provider. | Host isolation, not a VM boundary; partial epoch/generation/lineage coverage; delegated subagents not exercised. |
| Production probe | **12/12 checks passed**, including one gateway owner, governance-plugin hook evidence in a synthetic session, durable cron admission, state integrity and reachable Command Center. | Production business-tool DENY cases were not re-exercised; probe success does not imply all architecture criteria passed. |
| Production owner-loss recovery | Idle owner count one → zero → one; in-flight synthetic attempt retained one row through `claimed → running → unknown`, without replay or duplicate row, and one owner after recovery. Supervisor honored operator pause and recovered. | No canonical receipt settlement observed; no universal exactly-once effect guarantee or closure of the separate older October 14 restart-child boundary. |
| Model-route correction | Pre-existing automatic fallbacks to two paid models cleared after backups in root plus six profiles; free routes and explicit `escalate` alias retained. | Deliberate paid escalation remains available; total model cost and universal budget enforcement were not measured. |

This recovery result preserves uncertainty as company state. An interrupted attempt becoming `unknown` does not establish success or failure of an outside effect and does not authorize replay.

### Separate runtime cutover from convergence acceptance

The 18 executives remained **standalone by config (temporary compatibility shim)**; no served-profile migration occurred. The existing CEO adapter already used native cron admission. Compatibility checks and absence of idle-exit gateway debris do not establish served-profile convergence.

Command Center already reads canonical execution/session stores, but its payload lacks `execution_id`, `owner_epoch`, `generation` and receipt fields. Execution identity and receipt visibility remain partial; stale/current execution discrimination remains unverified. Receipt settlement is **UNKNOWN**. The old install stamp remains disclosed metadata drift; git/runtime agreement supplies the pinned identity. Wrapper `rc=0` and `idle_refused` do not establish useful work or correct idle eligibility.

### Single-use effect permits — architecture direction

For consequential actions, the target extends scoped delegation into consumable authority:

```text
root principal → durable organizational identity → delegation → attenuated scope
→ exact normalized action / resource / destination → single-use effect permit
→ ephemeral execution identity → atomic claim / consume → dispatch
→ target receipt → independent verification → canonical state
```

The permit must not widen its parent grant. Atomic consumption before dispatch is intended to prevent concurrent reuse, mutation after approval and a second effect after an uncertain response. Target receipt and independent verification bind the consumed authority to the observed result. **UNKNOWN must not silently mint a fresh permit.** This extends ordinary idempotency rather than replacing it.

Email sends, payments, purchases, campaign actions and other consequential API calls are candidate surfaces. These are **ADOPT / TEST directions**, not claims that all production tools implement single-use permits or that receipt settlement has been demonstrated. The synthetic no-replay recovery observation is narrower than this target control.

### Durable organizational identity and ephemeral execution identity

The organizational role, such as CEO, may persist across restarts. Each process/session/attempt must receive fresh, bounded execution authority derived from current delegation and, for consequential actions, the current effect permit. A restarted executive does not inherit open-ended authorization from its role name or an earlier session.

Missions, grants, evidence and canonical company state must survive independently of disposable conversations. Identity separation remains architecture direction; partial epoch/generation/lineage test coverage and missing Command Center fields do not establish complete production enforcement.

### Explicit compatibility-admission gate for future Hermes upgrades

The [upgrade doctrine](../ROADMAP.md#october-15-external-learning-follow-through) requires a separate admit-or-hold decision for each future target:

```text
new release → isolated compatibility audit → exact target verification
→ gateway/profile tests → plugin + model-route regression → CEO-cycle test
→ governance ALLOW / DENY regression → persistence + restart / owner-loss proof
→ admit or hold
```

Resume/recovery behavior, command-ledger compatibility and relevant plugin boundaries require explicit verification. The October 15 exact-pin cutover and independently verified rollback checkpoint are the reference procedure. An upstream release or update-channel selection cannot substitute for compatibility evidence; this doctrine is not a claim that future versions have already passed.

One CEO, one canonical company state, owner **root + veto** and watchdog-only scheduling remain governing constraints. **Full 24/7 autonomy, receipt settlement and complete architectural convergence remain unproven.** No mail, social, payment or customer/prospect action was taken to prove cutover; no delivery, reply, customer, conversion, sponsor award, revenue or cash outcome follows from these runtime observations. Unmeasured outcomes remain **UNKNOWN**, not zero.
