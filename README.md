# Hermes Autonomous Company

**MetaBot: one Hermes-native AI CEO, a governed executive team, and an evidence trail for what the company actually did.**

The human owner retains **root + veto**. The CEO selects authorized work; executives execute; independent verification determines what can be recorded as an outcome.

**Start here:** [60-second evidence walkthrough](DEMO.md) · [Current proof and limits](CURRENT_STATE.md) · [Claim-by-claim evidence](PUBLIC_EVIDENCE_INDEX.md)

![MetaBot operating model: owner authority, one Hermes CEO, executives, verification and canonical state. Architecture illustration, not a live runtime capture.](assets/company-loop.svg)

### What you can inspect today

| Observed in the October 15 production evidence | Proof boundary |
|---|---|
| Current production is **Hermes v0.22.2**, base commit `d923a5eb487a17c0a68801bba9ef0f56c81040a8`, with preserved local runtime repairs | Git HEAD and live runtime identity agree. v0.22.1 remains the historical migration/rollback milestone. See the [current scoped record](evidence/HERMES_V0_22_2_SELF_FUNDING_2026-10-15.md). |
| Rollback checkpoint independently verified before cutover | **8/8** database integrity checks passed; git bundle + HEAD matched; **23,622** manifest entries had zero missing files or hash mismatches. |
| Governance loaded in production and synthetic cron admission/recovery passed | One owner; governance hook evidence advanced during the synthetic session; in-flight restart produced `claimed → running → unknown` with one execution row and no replay. |
| Pre-existing automatic paid fallbacks were removed | All six approved paid primaries remain configured; housekeeping/per-job free selection is explicit and automatic fallback chains remain empty. Paid admission requires funding proof; this is not a total-cost measurement. |
| Earlier event-driven company evidence remains preserved | October 12–14 evidence still documents CEO wake/delegation, terminal handling, concurrency and bounded outreach verification; it is historical context, not the latest milestone. |

**Current status: v0.22.2 admission PASS WITH QUALIFICATION / PROVEN-SCOPED; self-funding enforcement activated with ordinary paid admission CLOSED pending a recovery-cost bound; full company convergence remains PARTIAL.** `max_iterations` is a hard bound; `run_budget_seconds` is not a hard wall-clock kill. Replacement-lineage and D20 repairs are proven within the reported repair scope. The [current record](evidence/HERMES_V0_22_2_SELF_FUNDING_2026-10-15.md) separates the runtime repair report, new funding acceptance, provider renewal cancellation and remaining unknowns. Self-funding status is **UNKNOWN**, not a claim that the company pays for itself. The [October 15 migration record](evidence/HERMES_V0_22_1_PRODUCTION_MIGRATION_2026-10-15.md) establishes the exact-pin cutover, governance activity, durable cron admission and scoped restart recovery. The 18 executives still use Hermes' temporary standalone compatibility arrangement, Command Center does not yet surface `execution_id` / `owner_epoch` / `generation` / receipt state, canonical receipt settlement was not observed in the cutover window, and no economic outcome is claimed. Full 24/7 autonomous operation therefore remains unproven. Public revenue and cash measurements remain **UNKNOWN** unless authoritatively measured.

The October 15 economic-resume mission was delivered to the native CEO; its current portfolio winner remains **UNKNOWN**. The Arcade.dev A23 draft remains internal and unsent, with unsupported claims and owner-approval wording returned for correction. See the [dated follow-through and nonclaims](evidence/HERMES_V0_22_2_SELF_FUNDING_2026-10-15.md#economic-resume-follow-through--october-15-2026).

Built on [Nous Research's Hermes Agent](https://github.com/NousResearch/hermes-agent). This public repository contains sanitized evidence and architecture; implementation remains private.

For technical review, start with [the walkthrough](DEMO.md). For pilots, research support or infrastructure sponsorship, see [SPONSORSHIP.md](SPONSORSHIP.md) and [INVESTORS.md](INVESTORS.md).

---

This repository documents an operating experiment in **human-governed autonomous companies**: one AI CEO coordinates an executive layer and digital workforce to pursue real business objectives while the human owner retains root authority, veto power and reserved decisions.

> **Core v1 status:** BUILT / PRODUCTION  
> **Public scope:** facts, architecture, product, evidence, failures, corrections, business model and roadmap  
> **Not published here:** source code, credentials, private customer/prospect data, banking details, security-sensitive implementation paths or raw private transcripts

## What is being built

MetaBot Solutions is developing an **Autonomous Company OS**: a governed operating architecture for AI executives and digital workers that can observe company state, reason, delegate, execute within authority, verify results, persist evidence, recover from faults and continue operating.

The system is intentionally model-independent. The language model supplies reasoning; the operating system supplies company state, authority, workflows, evidence, persistence and controls.

The operating pattern is:

```text
Human owner (root + veto)
        ↓
AI CEO
        ↓
C-suite executives
        ↓
Digital workers / tools / channels
        ↓
Verification + evidence + persisted company state
        ↺
```

## Why this repository exists

Most AI-agent demonstrations show a successful interaction. This project is documenting a harder question:

**Can an AI-led company operate continuously, economically and safely under explicit human authority — including failures, repairs, evidence and commercial execution?**

We publish the facts because credibility requires more than demos.

This repository therefore preserves:

- what has been demonstrated;
- what remains unproven;
- failures and corrections;
- commercial progress;
- governance boundaries;
- product and pricing direction;
- sponsorship and investment opportunities;
- the path from digital workers to a full Autonomous Company OS.

## Evidence language

We deliberately distinguish different levels of proof.

For example:

```text
PROVIDER ACCEPTED
≠ RECIPIENT DELIVERED
≠ RECIPIENT READ
≠ HUMAN REPLY
≠ SIGNED CUSTOMER
≠ CASH COLLECTED
```

A claim is not upgraded merely because the next state would be convenient.

## Current public status

**October 15: Hermes v0.22.1 production cutover PASS; architectural convergence remains open.** The [dated migration evidence](evidence/HERMES_V0_22_1_PRODUCTION_MIGRATION_2026-10-15.md) records the exact pin to `297552a9d646119871391d202509822cd86330df`, independently verified rollback checkpoint, production governance-hook activity, removal of pre-existing automatic paid fallbacks, and scoped idle/in-flight restart recovery. Executives still use the temporary standalone compatibility arrangement; served-profile convergence and Command Center execution identity remain outstanding. Receipt settlement is UNKNOWN. This milestone establishes no economic outcome or full 24/7 continuity.

The later [October 14 reconciliation and continuation proof](evidence/RECONCILIATION_CONTINUATION_PROOF_2026-10-14.md) closes the `health_fresh` reconciliation deadlock: event wakes used a 90-second health-collector timeout, while the successful scan needed 160.5 seconds. The repair uses the existing 300-second bound without weakening freshness or verifier requirements. The original result and a distinct successor were independently reconciled and retired; another CRO sponsorship-preparation run followed. Global health remains **DEGRADED**, the two-hour watchdog is unchanged, and `paid_model_budget_usd=0` with free-only routing remains the recorded constraint. No paid-model spend was observed in this scoped repair/continuation record; model cost remains unmeasured.

The [October 14 economic-coverage and recovery addendum](evidence/ECONOMIC_COVERAGE_AND_RECOVERY_2026-10-14.md) adds scoped social execution, CEO-selected sponsorship preparation and scheduled-path reboot continuity. Fresh post-Hermes-restart reconciliation progressed, but full restart recovery remains open. The overall classification remains **PARTIAL / PROVEN-SCOPED**.

The following preserves the 2026-10-13 public reconciliation of operating evidence:

- Core v1 remains **BUILT / PRODUCTION**.
- Human owner remains **root + veto**, not routine dispatcher or option selector; execution improvements cannot expand protected authority.
- One canonical Hermes-native CEO loop remains the company operating loop.
- A natural scheduled CEO wake has now demonstrated real CEO inference, work selection, governed executive delegation and isolated CTO-home execution on the ordinary production path.
- The earlier CTO attempt remains failed. Later evidence proves real event-driven failure continuation and CFO/CMO concurrency; full continuous operation remains **PARTIAL / PROVEN-SCOPED**, not fully proven.
- The follow-up routing repair passed independent acceptance; three bounded follow-up sends were **SEND ACCEPTED + SENT-FOLDER VERIFIED**, with matching pipeline updates and no duplicate sends. This does not prove delivery, reading, replies, customers, revenue or cash.
- The commercial mission is now explicitly **multi-engine**: marketplace/Fiverr fast cash, MetaCall services, MetaBot pilots/licensing, investors/acquirers, and sponsorship/resources.
- Recognized revenue and treasury state remain **UNKNOWN unless independently measured**; the public record does not convert missing measurement into $0.
- Real outbound commercial activity exists, but recipient delivery, signed-customer revenue and cash collection are not yet proven.
- Failures and corrections remain part of the public evidence trail rather than being rewritten as success.

See [CURRENT_STATE.md](CURRENT_STATE.md), [TRACTION.md](TRACTION.md) and [COMMERCIAL_OPERATING_STRATEGY.md](COMMERCIAL_OPERATING_STRATEGY.md).

## Continuous company direction

The intended end state is not a company that wakes every few hours.

It is a **continuous event-driven autonomous company** in which meaningful events wake the CEO immediately, independent C-suite lanes can work concurrently, and terminal executive results trigger verification/reconciliation/continuation. The two-hour schedule is watchdog/recovery only.

The system should be:

> **Always available, not always consuming inference.**

When authorized useful work exists, the company should keep moving. An empty event inbox alone does not justify idle: review eligible opportunities, due follow-ups, pipeline review, due discovery and economically useful capability repair. When those checks find nothing due or eligible, it may sleep cheaply until an event or watchdog wake occurs.

The existing loop has scoped production evidence; the priority is proactive economic execution and remaining acceptance, without new architecture layers. Scoped successful reconciliation/retirement and next economic work are now evidenced by the [October 14 reconciliation and continuation proof](evidence/RECONCILIATION_CONTINUATION_PROOF_2026-10-14.md); repeatable unattended operation and immediate wake latency across all successful completions remain acceptance requirements. Reconciled dashboard rows alone do not establish that chain.

See [CONTINUOUS_COMPANY_LOOP.md](CONTINUOUS_COMPANY_LOOP.md).

## Why this is an ambitious bet

The project is not trying to win by making a prettier chatbot.

The bet is that the next valuable layer above individual AI agents is a **governed autonomous economic operating system**: a system that can carry durable authority, company state, executive roles, tools, verification, recovery and commercial objectives across models and sessions.

The credible version of that idea must survive real failure.

That is why the public record deliberately preserves failed repairs, stale state, refused actions, unknown measurements and incorrect prior claims instead of polishing them away.

The target proof is stronger than agent orchestration:

```text
economic objective
→ authorized CEO decision
→ delegated executive work
→ real tool execution
→ independently verified outcome
→ durable company state
→ next autonomous decision
→ external economic result
```

If that loop becomes repeatable, the value is not the prompt or the model. The value is the operating system around them.

## Hermes Desktop / Agent OS surface

On October 12, 2026 the existing MetaBot Command Center was integrated into Hermes Desktop as a standalone local plugin surface named **METABOT COMPANY**.

The integration preserves the chosen architecture:

```text
Hermes runtime
= agent execution

AI-OS
= canonical company / governance / economic state

MetaBot Command Center
= read-only company projection

Hermes Desktop
= primary owner Agent OS shell
```

The company surface can correlate executive assignments with exact Hermes profiles, jobs, attempts and stored sessions, and can navigate between the company-level view and the owning Hermes session.

The integration does not create a second scheduler, second authority plane or second source of company truth.

A real ordinary CTO cycle was observed through dispatch, running activity and terminal failure with changing model/tool counters. The UI preserved the failure rather than promoting process completion to success.

That failed October 12 attempt remains historical evidence. Later event-driven failure continuation and CFO/CMO concurrency are proven within scope. October 14 adds scoped successful reconciliation/retirement and autonomous economic continuation; universal successful executive continuation and full 24/7 operation are not claimed.

## Product direction

The commercial product has evolved from individual AI agents into a hierarchy:

```text
MetaBot Autonomous Company OS
        ↓
Autonomous executive / C-suite layer
        ↓
Department workforces
        ↓
Specialized digital workers
        ↓
Integrations + governance + audit + human checkpoints
        ↓
Ongoing workforce operations
```

The historical product thesis remains:

> **Build Your Workforce — not Buy an AI Agent.**

See [PRODUCT.md](PRODUCT.md) and [product/PRICING.md](product/PRICING.md).

## Multi-engine commercial operating model

MetaBot / MetaCall is not relying on one commercial funnel.

The governed company operating system supports multiple parallel economic engines:

- **marketplace / fast-cash services** — including Fiverr-style service offers where current demand can be measured quickly;
- **MetaCall Solutions** — bookkeeping, QuickBooks, cleanup, reconciliation, reporting and CFO-support services;
- **MetaBot Solutions** — digital workforces, autonomous-company infrastructure, pilots, licensing, partnerships and strategic transactions;
- **investment / acquisition** — strategic investors, angels, venture capital, potential acquirers and licensing partners;
- **sponsorship / non-dilutive resources** — model credits, cloud/API credits, hardware, startup programs, grants and research partnerships.

The CEO is expected to allocate effort dynamically toward the highest expected economic value rather than treating every channel equally.

The strongest near-term proof is not another internal architecture milestone. It is externally verified economic progress: a paid order, cash received, a serious investor/acquirer meeting, diligence, a sponsor commitment, model credits, hardware/resources, or another measurable transaction advance.

See [COMMERCIAL_OPERATING_STRATEGY.md](COMMERCIAL_OPERATING_STRATEGY.md).

## Public evidence policy

The deeper build history remains private because it contains implementation detail and sensitive operational evidence. This public repository publishes sanitized, supportable facts derived from that record.

We do **not** publish:

- source code;
- API keys, tokens or secrets;
- private email addresses or prospect identities;
- banking identifiers;
- private correspondence;
- security-sensitive local paths;
- raw transcripts that may contain sensitive data.

See [SECURITY_AND_PRIVACY.md](SECURITY_AND_PRIVACY.md).

## For customers, sponsors, partners and investors

We are looking for aligned parties who want to help move autonomous-company technology from production proof toward commercial scale.

You can engage as a:

- **pilot customer** — deploy a digital workforce or governed autonomous workflow;
- **enterprise partner** — integrate the operating model into a real organization;
- **infrastructure/model sponsor** — provide inference, compute, API or hardware resources;
- **research/technical partner** — help test governance, safety, verification and human-AI collaboration;
- **strategic investor or acquirer** — support scale, licensing, distribution and enterprise value creation.

See [SPONSORSHIP.md](SPONSORSHIP.md), [INVESTORS.md](INVESTORS.md) and [ROADMAP.md](ROADMAP.md).

## Repository map

- [CURRENT_STATE.md](CURRENT_STATE.md) — latest public state
- [ARCHITECTURE.md](ARCHITECTURE.md) — operating architecture
- [GOVERNANCE.md](GOVERNANCE.md) — human authority and autonomous execution boundaries
- [PRODUCT.md](PRODUCT.md) — product hierarchy and customer value
- [BUSINESS_MODEL.md](BUSINESS_MODEL.md) — paths to revenue and enterprise value
- [COMMERCIAL_OPERATING_STRATEGY.md](COMMERCIAL_OPERATING_STRATEGY.md) — multi-engine revenue, capital and resource-acquisition operating model
- [CONTINUOUS_COMPANY_LOOP.md](CONTINUOUS_COMPANY_LOOP.md) — event-driven 24/7 CEO/C-suite operating model
- [TRACTION.md](TRACTION.md) — demonstrated commercial and operating progress
- [ROADMAP.md](ROADMAP.md) — next milestones
- [SPONSORSHIP.md](SPONSORSHIP.md) — sponsorship and infrastructure support
- [INVESTORS.md](INVESTORS.md) — investor / strategic-partner thesis
- [PUBLIC_EVIDENCE_INDEX.md](PUBLIC_EVIDENCE_INDEX.md) — claim/evidence map
- [INDUSTRY_LANDSCAPE_AND_COMPETITIVE_LEARNING.md](INDUSTRY_LANDSCAPE_AND_COMPETITIVE_LEARNING.md) — external benchmark, lessons and continuous-learning doctrine
- [case-study/FROM_AGENT_TO_AUTONOMOUS_COMPANY.md](case-study/FROM_AGENT_TO_AUTONOMOUS_COMPANY.md)
- [white-paper/AUTONOMOUS_COMPANY_OS.md](white-paper/AUTONOMOUS_COMPANY_OS.md)

## Important distinction

This is currently a **public evidence and architecture repository**, not a public source-code repository.

The software implementation remains private. No open-source software license is implied by publication of these documents.

---

**MetaBot Solutions — humans retain authority; AI expands execution capacity.**


## Continuous competitive learning

The project continuously studies serious autonomous-company systems, multi-agent research, agent control planes and production failure reports. Useful external lessons are tested against MetaBot's governance and evidence requirements before adoption. See [INDUSTRY_LANDSCAPE_AND_COMPETITIVE_LEARNING.md](INDUSTRY_LANDSCAPE_AND_COMPETITIVE_LEARNING.md).
