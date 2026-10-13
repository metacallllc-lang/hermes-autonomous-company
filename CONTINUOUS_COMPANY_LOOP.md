# Continuous Company Loop

**Updated:** 2026-10-13

**Status:** PARTIAL / PROVEN-SCOPED — real event-driven failure continuation and CFO/CMO concurrency have evidence; full 24/7 successful operation is not claimed. See [CURRENT_STATE.md](CURRENT_STATE.md) for the dated proof boundary.

## Thesis

An autonomous company should not spend most of its time waiting for a scheduled cron wake.

The target operating model is a **continuous event-driven company**:

- always available;
- economically opportunistic;
- able to wake immediately on meaningful events;
- able to run independent executive lanes concurrently;
- cheap while idle;
- governed by one authoritative CEO;
- constrained by explicit authority and resource locks.

The design goal is:

> **When useful authorized work exists, the company keeps moving. When nothing useful exists, it sleeps cheaply and wakes immediately on new information.**

## One CEO, many executive lanes

The company retains one authoritative CEO.

The C-suite may operate concurrently in separate bounded lanes:

```text
                         OWNER
                      root + veto
                           │
                           ▼
                          CEO
                  authoritative arbiter
                           │
       ┌───────────┬───────┼───────┬───────────┐
       ▼           ▼       ▼       ▼           ▼
      CFO         COO     CRO     CMO         CTO
       │           │       │       │           │
       └───────────┴───────┴───────┴───────────┘
                           │
                           ▼
                    durable events
                           │
                           └──────────────► CEO
```

Initially, each executive lane should allow at most one active assignment for that role.

Independent executive work should not require a single company-wide assignment lock.

## Event-driven continuation

Meaningful company events should wake the CEO immediately.

Examples include:

- executive completed;
- executive failed;
- work refused;
- customer reply;
- investor/acquirer reply;
- sponsor response;
- payment event;
- order;
- follow-up due;
- deadline approaching;
- opportunity discovered;
- material market change;
- provider failure;
- owner directive;
- recovery condition;
- stale work detected.

The intended loop is:

```text
EVENT
→ persist
→ wake CEO
→ load canonical state
→ independently verify
→ reconcile affected work
→ update company state
→ rank eligible opportunities
→ dispatch executive lanes
→ executives execute independently
→ terminal/result events
→ wake CEO again
↺
```

## Executive → CEO signals

Executives should be able to emit durable signals such as:

- `EXECUTIVE_COMPLETED`
- `EXECUTIVE_FAILED`
- `OPPORTUNITY_DISCOVERED`
- `BLOCKER_DISCOVERED`
- `EXTERNAL_RESPONSE`
- `PAYMENT_EVENT`
- `DEADLINE_DUE`
- `BETTER_PATH_PROPOSED`

A signal is not authority.

It is a durable input to the CEO decision loop.

Each signal should preserve:

- emitting role;
- assignment/job/session;
- event type;
- timestamp;
- evidence references;
- recommended action where applicable;
- authority requirements;
- resulting disposition.

## CEO → executive signals

After reconciliation and prioritization, the CEO may dispatch new work immediately.

Examples:

- CRO → qualify new sponsor / buyer / investor;
- CMO → improve offer positioning;
- CFO → analyze price / margin / cash;
- COO → prepare fulfillment / delivery;
- CTO → repair a revenue-blocking technical defect.

The CEO remains the allocator and decision-maker within enacted authority.

Multiple authorized choices are an operating decision for the CEO, not an owner escalation. Execute safe independent branches concurrently within lane and resource constraints.

## Economic opportunity queue

Fresh economic work uses the existing canonical durable opportunity queue separately from failed-work replacement semantics. Keep one CEO and one canonical company state; no new architecture layer is required.

A fresh opportunity record should be able to represent:

- source event / directive;
- proposed role;
- objective;
- supporting evidence;
- expected cash;
- probability;
- speed;
- margin;
- strategic value;
- effort / cost / risk;
- required authority;
- current state;
- provenance.

A bounded ranking heuristic may include:

```text
expected cash
× probability
× speed
× margin
× strategic value
÷ effort / cost / risk
```

Unknown inputs remain UNKNOWN.

The ranking system may prioritize execution.

It may not expand authority.

## Concurrency model

The initial target is one active assignment per executive role:

- CFO lane: 1
- COO lane: 1
- CRO lane: 1
- CMO lane: 1
- CTO lane: 1

This permits multiple independent lanes to work concurrently.

Real CFO/CMO execution overlapped for 213.47 seconds in the preserved October 12 evidence. This proves that pair within scope, not unrestricted concurrency across all roles or payment/publication effects.

Concurrency must not imply unrestricted parallel consequential actions.

## Resource-level locks

Consequential resources should retain stricter locks independent of executive-lane concurrency.

Examples include:

- outbound email/send resource;
- payment / treasury resource;
- public publishing resource;
- credential mutation;
- governance / authority changes;
- protected production deployment surfaces.

Research, internal analysis and bounded artifact creation should not serialize the entire company unless they share an actual protected resource.

## Watchdog schedule

The existing **two-hour scheduled CEO wake is watchdog / dead-man recovery only**. It is not the normal cadence or a reason to delay eligible work.

The watchdog should detect:

- missed events;
- stale company state;
- unreconciled terminal work;
- due follow-ups;
- provider failures;
- orphaned assignments;
- opportunity starvation;
- health drift.

If event-driven continuation is healthy, the company may progress multiple times between scheduled watchdog wakes.

## Continuous does not mean wasteful

24/7 operation does not mean constant inference.

The system should avoid tight polling and unnecessary model calls.

The target is:

> **Always available, not always consuming inference.**

An empty event inbox alone is insufficient for idle. The CEO must also evaluate eligible economic work, due follow-ups, pipeline review/requalification, due discovery and capability repairs that unblock higher-value economic action. If ordinary queues are exhausted, run bounded economic discovery when due and admit evidence-backed opportunities through the existing queue.

The company may sleep cheaply only when none of those actions is eligible or due and no unprocessed event requires attention. Open pipeline rows alone do not establish eligibility; unknown inputs remain UNKNOWN. Discovery must be bounded and economically useful, without tight polling or work manufactured merely to stay busy.

`IDLE` is a proposed state transition, not an executive assertion of truth. The existing authorized canonical-state writer must refuse it unless fresh eligibility/exhaustion evidence covers unprocessed events, eligible economic work, due follow-ups, pipeline review/requalification, due bounded discovery and economically useful capability repair. Record the checks, evidence, reasons for ineligibility and next event/deadline/watchdog wake condition. Missing or ambiguous evidence cannot establish exhaustion. Independent verification accepts or rejects the committed idle outcome under [the state-commit contract](GOVERNANCE.md#durable-state-propose--commit--audit). This is required doctrine; production enforcement remains to be demonstrated.

When something relevant changes, it should wake immediately.

## Economic search loops

Each executive may maintain bounded recurring economic discovery responsibilities.

### CRO

```text
pipeline
→ market demand
→ buyers / sponsors / investors / partners
→ follow-ups
→ channel performance
→ opportunity proposals
```

### CMO

```text
market signals
→ competitor positioning
→ search / marketplace demand
→ offer improvement
→ messaging experiments
→ opportunity proposals
```

### CFO

```text
cash
→ cost
→ pricing
→ margin
→ runway
→ resource allocation
→ economically superior paths
```

### COO

```text
capacity
→ fulfillment
→ bottlenecks
→ delivery readiness
→ operating efficiency
→ scale readiness
```

### CTO

```text
runtime health
→ capability gaps
→ reliability
→ model/tool efficiency
→ revenue-blocking repairs
→ technical opportunity proposals
```

These loops remain subordinate to governance and CEO prioritization.

## Owner role

The owner remains:

- root authority;
- veto;
- reserved decisions;
- irreducible human/platform actions where required.

The owner should not become routine message bus, dispatcher or reconciliation worker.

## Proof standard

The continuous-company architecture is not considered production-proven merely because event schemas or queues exist.

Real event-driven failure continuation is proven within scope: durable terminal events woke the existing CEO task between watchdog runs, failure disposition was preserved and next economic work was selected. Failed work was not promoted to success. Successful executive completion through immediate verified reconciliation/retirement and next work remains a separate acceptance requirement; later reconciled dashboard rows alone do not prove it.

Strong proof requires a real chain such as:

```text
executive completes
→ durable event emitted
→ CEO wakes before watchdog schedule
→ verifies/reconciles
→ next economic work selected
→ another executive lane starts
```

A stronger proof includes at least two independent executive lanes operating concurrently while consequential resource locks remain intact.

The strongest proof is economic:

```text
continuous company loop
→ external opportunity
→ authorized action
→ response / order / resource commitment / cash
→ canonical evidence
→ next autonomous decision
```

## Governance invariant

The loop may optimize execution.

It may not optimize or expand its own authority.
