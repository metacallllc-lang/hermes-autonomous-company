# November 17–20: marketplace gigs, an order desk, and executives that look for new income

The November 16 checkpoint gave each executive seat a governed action tool under an owner veto. These four days
put that authority to work on revenue: the company opened marketplace offers it can deliver itself, built the
path from an order to a delivery, and gave the executives a measured way to invent and test new income. Most of
the time went into faults that stopped the loop from acting; they are listed below with what was observed after
each repair. **No customer, order, payment or revenue is claimed.**

## What was built

### Marketplace gigs the company can deliver itself

Four gigs were written and published on the company's Fiverr seller account, two per brand:

| Brand | Gig | Packages | Delivered by |
| --- | --- | --- | --- |
| MetaCall | Bank reconciliation and QuickBooks journal entries | $195 / $450 / $950 | deterministic reconciliation workflow |
| MetaCall | Clean, deduplicate and standardize Excel or CSV data | $45 / $95 / $195 | deterministic data-cleanup workflow |
| MetaBot | Business workflow audit and AI automation plan | $150 / $350 / $750 | CTO-written plan, COO review |
| MetaBot | Competitor and market research with a cited report | $75 / $175 / $395 | CMO-written report from public sources, COO review |

Three are live. The reconciliation gig sits in the Finance category, where the marketplace requires the seller's
own license declaration; that is a personal attestation, so it waits for the owner and was not made by the system.

### An order desk

Every CEO wake reads the seller's open orders and, for each one: acknowledges it, asks one specific question when an
input is missing or unusable, answers buyer messages in writing, does the work, runs a COO review, and queues the
delivery as a veto notice. Reports for the two MetaBot gigs are written by the owning seat's model; every factual
claim in a research report must cite a public page that was actually read, and the review refuses a report that
cites anything else, misses a promised section, asks for credentials or contains an email address. A live test
on sample briefs produced a cited three-competitor report and a one-workflow automation plan; the review caught
one email address and one truncated draft and forced a rewrite in both cases.

### A growth engine: brainstorm, experiment, act

- Each executive's twice-daily brief now carries a duty to brainstorm when it owns no experiment, its running
  experiments, a daily action quota, and (for the CRO) a batch of prospects to research.
- An experiment has an owner, a target metric, a deadline and tagged actions; every wake measures it from the
  ledgers and, at its deadline, scales it (target raised) or kills it with the numbers.
- An executive may launch a new offer only if it maps to a delivery capability the company has and clears the
  charter margin rule at worst-case effort; a launch is itself a veto notice.
- Outbound email may quote only the price of an active offer.
- Executive action authority now also covers opportunity, sponsorship, prospect and inbound-response work, and a
  due executive turn runs before further drafting work is handed out.

## Faults found and repaired

1. **The every-wake orders read looked at the buyer-side page**, so a seller order would never have been seen.
2. **Executive web search was throttled on every query** (HTTP 202). Search now uses the agent runtime's own
   search backend; a public page that redirects falls back to its extractor. Private destinations stay refused.
3. **A marketplace lane reported a held capability after the gigs were live**, refusing every idle wake. A fresh,
   authenticated read of the active gigs now closes it.
4. **A sponsorship task had been fenced since October 25 under one fixed identity** while still counted as open
   work. It now has one identity per 12-hour slot, so a failure fences only that slot.
5. **A run budget above the job-budget ceiling made every action turn unlaunchable for a day** (a regression
   introduced during this work and reverted).
6. **A recorded never-launched failure could not be re-proven**, so its executive lane stayed held all day.
7. **A hung marketplace browser tab could hold a CEO wake for about 25 minutes.** The desk now fails fast and
   caps itself at five minutes; an unread order list is reported as unknown, not empty.
8. **The selector repeatedly offered work the dispatcher refuses** (about 30 consecutive wakes on one task). The
   selector now applies the dispatcher's own admission rule.
9. **Turns that acted were failed for not writing a report**, discarding real actions. An acted turn now passes.
10. **Social drafts written by the CMO were never ingested after November 14** because of a file-name mismatch.
    Fixed; a draft that asks readers to message the page is refused, because those inboxes are not monitored.
11. **Two executives answered the same inbound email with conflicting facts.** One reply per inbound message is
    now enforced across all seats, including replies still inside the veto window.
12. **Growth actions failed on argument shape**, and a qualified prospect never reached buyer discovery. The
    action tool now documents every argument, tolerant parsing is in place, and qualification enriches the
    canonical pipeline record.
13. **The activity report listed emails outside its window and matched replies by address.** It now windows
    sends and matches replies by thread.

## What was observed

- The first offer launched by an executive: a written QuickBooks cleanup plan at $395 (38.7% margin at worst-case
  effort), executed after its veto window.
- The first growth experiment started by an executive seat.
- Executive-written replies went to a contact-data vendor (asking for written trial terms) and to a cloud startup
  program; the program answered with its application file. No award is claimed.
- The MetaBot Facebook page publishes daily within its cap; recent posts were confirmed through the platform's API.
  After the ingestion repair, five drafts for both brands across Facebook, Instagram and LinkedIn were queued;
  their publication was not yet observed at the time of writing.

## Verification

New suites: order desk 36/36 and growth engine 28/28. Existing suites touched by this work pass (capability gate,
seat action queue, email capability, CRO, operating model, selector, COO delivery, failure lifecycle). Failures in
a delegation lifecycle test, two continuation suites and an executive-failure-mode suite reproduce unchanged on
the code from before these changes and are not introduced here.

## Not established

- **No customer, marketplace order, payment or revenue.**
- None of the 246 ready contacts has yet been researched; buyer discovery still reports no qualified buyer.
- The marketplace delivery upload and order-message steps have not run on a real order.
- About one marketplace read in seven fails and is retried on the next wake.
- The CEO's no-effect streak remains above its threshold: activity is not a business result.
