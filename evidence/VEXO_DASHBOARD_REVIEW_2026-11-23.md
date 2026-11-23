# November 22–23: the VEXO Command Center checked against its sources

The owner reported that the dashboard showed a company with "no movement". The Command Center (renamed from the
Hermes Command Center to **VEXO**) was reviewed panel by panel against the canonical stores it is supposed to
project. Several panels were wrong or misleading. In the same two days the company itself had real gaps that
made it idle for hours, and those were fixed too. **No customer, payment or revenue is claimed.**

## What the dashboard showed, and what the sources said

| Panel | Showed | Canonical source said | Fix |
| --- | --- | --- | --- |
| Company activity chart | The newest 200 mixed log rows back to October 10; the last week looked almost empty | 26–73 executive turns a day, plus actions, emails, social posts and prospect research | New per-day series from the assignment store and the send, social and prospect ledgers (`CompanyPulse.py`, every wake) |
| Headline | "CEO loop is stagnating" | Executives were working; only the CEO's selector found nothing new *between* executive slots | Headline now says "Company is working" when an executive turn ran in the last 3 hours, with the turn count, the quiet-wake count and the next slot |
| Inference balance | A 25-day-old reading from a provider the executives no longer use, against a fixed reserve | The live provider's own credit endpoint | Read every wake from the provider's credit and key endpoints; shows remaining credit, daily rate and runway |
| Mission tile | 7 of 9 criteria met on a superseded mission statement | The owner's current north star: verified monthly revenue, with five dated milestones | North-star tile and an Economy-page milestone list, from the company plan and externally observed revenue rows only |
| C-suite constellation | COO "Unknown" | The assignment store recorded the COO's turn as reconciled | When the observer's stricter re-check cannot reparse a turn the CEO already reconciled or terminally failed, the durable status is shown and flagged |
| C-Suite cards | CFO's latest activity "43 days ago"; CMO "no recorded activity" | Both had turns that day | Each card shows the role's latest turn and its work item from the assignment store |
| Economy lanes | "0 lanes · last evaluated unknown" after any wake that dispatched work | Every wake records all ten lanes | Lanes come from the newest wake that recorded them |
| Health signal "C-suite activity stale" | Raised from the retired October coordination thread | Executive turns live in the assignment store | Signal removed; the C-Suite header shows turns in the last 24 hours and the latest turn instead |
| Spend and send tiles | Unlabelled totals | All-time totals across all models/accounts and since the first send | Labels now say "all-time"; the email tile adds the 21-day count |

Unchanged and correct as labelled: last verified cash (with "current unknown"), owner attention, veto notices,
scheduler and charter state.

**Tests.** Command Center suites: live operations 28, projection 33, render 25, state projection 17, panels,
complete-cycle 6/6, scheduled task 15, supervision 18 and 21, trigger timing 5, launch safety 25, attribution 14,
model-cost reading 23 — all passing. Three browser suites fail as before this change: they look for elements of
the classic page (`ops-connection`, `aios-back-to-top`) that the current dashboard never had.

## What changed in the company

- **Social publishing restored.** The only route to the governed publisher was a CMO task with a fixed identity
  that had failed once in October; the admission rule then refused it forever, so nothing was published after
  November 21 and every wake ended in stagnation. The governed publisher (charter-gated, daily cap, idempotency,
  brand routing, read-back) now runs every wake, at most one post per 150 minutes. The first run published and
  verified a post on three channels.
- **No idle gaps.** Executives had a turn every 12 hours, then every 6; between slots nothing was admissible.
  Revenue and marketing seats now act every 3 hours; finance and operations twice a day.
- **Larger turns.** Executive action turns get 40 model calls, 24 tool uses and 20 minutes (was 20/12/10);
  all other work keeps the old limits.
- **Actions split across calls.** The executive model often sent an action's fields in pieces (recipient in one
  call, body in the next), so every call was refused. Fields the same seat gave for the same action and target in
  the same turn are now carried into its next call; a different target starts fresh. Verified live: a prospect
  record that failed six times was accepted.
- **Outreach without a recipient.** An outreach email with no recipient goes to the prospect the same seat
  qualified in the same turn — its own recorded value, still behind every mail gate and the veto window.
- **Applications answered from facts.** Executive briefs cut inbound email at 500 characters, so a 32-question
  startup-program form was never seen in full and the seats asked for it to be re-sent six times. Unanswered
  mail is now shown in full, every brief carries one canonical company-facts block, and each open application has
  a single owning seat that answers once.
- **Credit runway owned by the CFO.** The live inference credit position is in the CFO's brief every wake.
- **Correction to November 20.** The reconciliation gig did not wait on an owner declaration: it was never saved.
  The seller account already has live bookkeeping gigs in that category.

## Open

- No customer, payment or revenue. The first-customer milestone is due December 15.
- About 60% of executive turns pass result verification; the rest are recorded as failed.
- The bank read is refused by the bank API's IP allowlist, so current cash stays unknown.
