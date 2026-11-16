# November 14–16 — executives that act, under an owner veto

The November 13 audit found a company that reasoned but did not act. These three days changed what an
executive seat can do, and repaired the faults that stopped the loop from reaching it. This record states
what was built, what was observed afterwards, and what remains unproven.

## The model: executives decide and act; the owner holds a veto

The owner's directive is veto power only. Each executive seat (CRO, CMO, CFO, COO, CTO) now has a
governed action tool scoped to its own capabilities:

| Seat | Actions it can take |
| --- | --- |
| CRO | read the marketplace seller inbox, reply to buyers on-platform, governed outreach, email |
| CMO | generate authorized content, publish to company social channels, email |
| CFO | read the bank of record (read-only), issue an invoice for a real order, email |
| COO | delivery readiness, execute and review a delivery |
| CTO | bounded repair and deploy |

- **Internal actions** (reads, content generation, readiness checks) run immediately and return their result.
- **External actions** (email, marketplace replies, publishing, invoices, deliveries) are validated by the
  seat's existing handler, recorded as a **veto notice** with the full message and the executive's reason,
  and executed automatically by the next CEO wake after a 60-minute window — unless the owner vetoes.
- Every action still passes the same gate as before: the sealed charter tier, daily caps, idempotency,
  suppression list and owner pause. Nothing here widens authority; it connects the authority the charter
  already granted to the executives who own the outcomes.

Email is composed by the executive and sent through the existing provider rail from one of the four
company identities, with the B1 25/day cap, a CAN-SPAM footer on outreach, and a prior-contact rule: a
second message to the same person is an explicit follow-up decision, not a retry. The company works in
writing only; a new message that offers a call or meeting is refused, because no one can attend it.

Marketplace work uses the existing authenticated seller session. The seller surface is read on every wake;
the CRO may compose an on-platform reply, quoting only prices on the approved offer sheet.

Executive turns now run twice a day with a fresh brief that lists unanswered inbound messages, active
marketplace threads, the seat's action queue and any open owner directive.

## Faults found and repaired along the way

1. **A phantom scheduler row held an executive lane for 60 cycles.** A job fired twice 35 ms apart; the
   scheduler correctly refused the duplicate, but the runtime read that bookkeeping row as the job's
   verdict, marked completed work FAILED, and then asserted on every wake while trying to dispose of it.
   Settled-without-start rows are now excluded; the lane reconciled on the next wake.
2. **In-turn tools ran in the wrong Python environment.** Executive turns run inside the agent gateway's
   own environment, which lacks the browser library, so every marketplace action from inside a turn failed.
   Seat actions now always execute in the company's own interpreter.
3. **Turns that acted were failed for writing no report.** The verifier required a report file even when
   the executive's output was an action. A recorded action now satisfies it; a turn that does nothing still fails.
4. **A spent daily cap stalled the CEO.** After the day's four permitted posts, the weekly plan minted a
   new publish task every wake and the CEO spent 16 consecutive wakes on a guaranteed refusal. A spent cap
   now means "due tomorrow".
5. **Thirteen owner directives had sat unconsumed since October.** Each received a written disposition.

## What was observed on November 16

- Two executive-written emails were sent — one replying to an inbound prospect, one answering a cloud
  provider's startup-program team — and both were independently found in the mailboxes' Sent folders.
  The second waited out its veto window before sending.
- Four authorized posts were published (the B2 daily cap), and the CMO generated four more for the queue.
- The CFO read the bank of record through its read-only capability.
- An owner-facing activity report is now written on every wake from ledgers only, and the owner's briefing
  reads it first.

## Verification

New tests: action queue (7), email capability (5), cap deferral (3) — all pass. Existing suites pass for
the CRO (22), CMO (21) and CFO (28) capabilities, the capability gate (21/21), the operating model (15/15),
the selector (8/8) and the owner-request ledger (31/31). Two failures in the delegation suites and one in the
authority classifier reproduce unchanged on the pre-change code and are not introduced here.

## Not established

- **No customer, payment, contract or revenue.** Neither email has a reply yet.
- The CRO has not yet completed a turn on the corrected tool path.
- On November 15 the model provider returned errors on every CEO turn for most of the day; turns resumed
  later that day. The upstream cause was not isolated.
- Marketplace listing publication remains held behind an unresolved capability limit.
