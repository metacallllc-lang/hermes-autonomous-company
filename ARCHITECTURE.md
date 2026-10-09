# Architecture

## Core idea

The system separates **reasoning compute** from the **company operating system**.

A language model can be replaced. Company authority, durable state, evidence, workflows, recovery and governance must persist.

```text
Human owner
(root authority + veto)
        │
        ▼
AI CEO
(strategy, prioritization, delegation)
        │
        ├──────────────┬──────────────┬──────────────┬──────────────┬──────────────
        ▼              ▼              ▼              ▼              ▼
       CFO            COO            CRO            CMO            CTO
        │              │              │              │              │
        └──────────────────── digital workforce ────────────────────┘
                               │
                               ▼
                     tools / channels / systems
                               │
                               ▼
                 verification + evidence + persistence
                               │
                               └──────────────↺
```

## One canonical CEO loop

The company is designed around one authoritative CEO operating loop.

Supporting schedulers may:

- poll;
- monitor;
- collect events;
- trigger deterministic checks;
- update canonical state.

They should not independently become competing CEOs.

## Operating loop

The intended production loop is:

```text
WAKE
→ LOAD STATE
→ VERIFY AUTHORITY / HEALTH / COST
→ OBSERVE
→ RESEARCH
→ IDENTIFY OPPORTUNITIES / RISKS
→ STRATEGIZE
→ CREATE OR UPDATE WORK
→ SELECT EXECUTIVES
→ DELEGATE
→ EXECUTE
→ VERIFY
→ PERSIST
→ LEARN
→ REALLOCATE / RETRY / REPLACE / SCALE / STOP
→ CONTINUE
```

## C-suite

The executive layer gives the CEO specialized perspectives:

- **CFO** — economics, finance, unit economics, capital allocation
- **COO** — operating continuity, delivery, process, capacity
- **CRO** — pipeline, sales, partnerships, revenue execution
- **CMO** — market, brand, content, demand generation
- **CTO** — runtime, tools, integrations, reliability, technical production

The CEO remains the ordinary operating decision-maker within enacted authority.

## Workers

Executives delegate bounded work to workers, tools or child agents.

A worker result is not automatically company truth. Results are expected to be checked against:

- authority;
- evidence;
- canonical state;
- acceptance criteria;
- resulting external state where applicable.

## Canonical state

The architecture treats durable company records as more authoritative than conversational narrative.

Typical categories include:

- company state;
- authority classification;
- decisions;
- evidence;
- missions;
- delegated work;
- pipeline;
- revenue and accounting;
- capability/runtime state;
- health;
- corrections and superseding addenda.

## Memory

Historical experiments included Open Second Brain + Obsidian as a persistent-memory layer.

The useful doctrine survives:

- distinguish fact from inference;
- preserve provenance;
- resolve conflicts by freshness and evidence;
- avoid storing secrets;
- avoid turning memory into a raw transcript dump.

But no external memory provider is allowed to silently outrank canonical company state.

## Model independence

The design goal is:

> **The model reasons. The operating system runs the company.**

Models can therefore be selected based on:

- task suitability;
- cost;
- reliability;
- context needs;
- latency;
- provider availability.

A model route can fail without redefining company authority.
