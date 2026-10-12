# Continuous Company Loop

**Updated:** 2026-10-12  
**Status:** architectural target / implementation in progress; full 24/7 event-driven production proof is not yet claimed.

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
→ reconcile affected work
→ independently verify
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

## Economic opportunity queue

Fresh economic work should have a first-class durable queue separate from failed-work replacement semantics.

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

The existing scheduled CEO wake remains valuable, but its role changes.

It should become a **watchdog / dead-man recovery mechanism**, not the normal cadence of the company.

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

When no eligible work or meaningful event exists, the company may sleep cheaply.

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
