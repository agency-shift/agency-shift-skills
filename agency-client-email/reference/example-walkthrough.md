# Walkthrough — agency-client-email

Two sample runs of the skill on common situations.

---

## Example 1 — Scope change

### Input the user pastes

```
Situation: scope change
Client name: Brackenfell Coffee
Client relationship age: long-term (18 months)

Key facts:
- Original SOW signed June 1 for Black Friday push, fixed fee $25K
- Sarah just emailed asking us to also build out a wholesale order
  portal "while we're in there"
- Wholesale portal is a 3–4 week project on its own, ~$8–10K of
  additional work, would meaningfully impact the BF November timeline
- We want to keep her happy but cannot absorb this for free

Prior thread: Sarah's email reads:
"Hey — quick one. While you're rebuilding the storefront could you
also wire up a basic wholesale portal? Just a B2B login + order form
for our 12 cafe accounts. Should be quick, right?"
```

### Output

```markdown
# Client email — Scope change — Brackenfell Coffee

**Recipient:** Sarah (CEO)
**Relationship age:** long-term

## The email (paste-ready)

Subject: Re: wholesale portal — happy to scope it separately

Hi Sarah,

Good idea — and not in the BF SOW, so let me give you a real answer.

The wholesale portal (B2B login, account-level pricing, order
flow for 12 accounts) is about 3–4 weeks of work and $8–10K
depending on whether you want stock-aware pricing or a flat
catalog. If we slide it into the current engagement, the BF
launch on November 28 slips by 2–3 weeks — which I don't think
is what you want.

Better: I send you a separate one-page SOW for the wholesale
piece on Monday. We start it in early August after the BF
performance fixes are shipped, and it's live by mid-September —
ahead of any holiday wholesale push your cafes might run.

Sound right? If yes I'll have the SOW with you Monday morning.

— Valdeir

---

## Why this works (rationale for partner review)
- **The news in line 1:** "not in the BF SOW, so let me give you a
  real answer" — tells Sarah immediately this is treated as a real
  new project, not absorbed silently.
- **The ask:** "If yes I'll have the SOW with you Monday morning" —
  one concrete next step.
- **What we did NOT say:**
  - No apology for not being able to absorb it free
  - No vague "we'll see what we can do"
  - No softening of the cost or timeline
  - No abandoning the BF deadline

## Variant: shorter (long-term relationship)

Hi Sarah,

Wholesale portal is its own thing — 3–4 weeks, $8–10K. Can't
slot it in without slipping BF.

If I send you a separate one-pager Monday, we start it August,
live by mid-September. OK?

— V
```

---

## Example 2 — Missed deadline

### Input the user pastes

```
Situation: missed deadline
Client name: Brackenfell Coffee
Client relationship age: long-term (18 months)

Key facts:
- We committed Friday July 26 for the Klaviyo flow rebuild handoff
- We're not going to make it — bug in the segmentation logic
  surfaced Wednesday, fix needs another 2-3 days of testing
- New realistic delivery: Tuesday July 30
- Bug is solvable; this isn't a "we're stuck" situation, just slipped

Prior thread: None — proactive notification
```

### Output

```markdown
# Client email — Missed deadline — Brackenfell Coffee

**Recipient:** Sarah (CEO)
**Relationship age:** long-term

## The email (paste-ready)

Subject: Klaviyo handoff slipping to Tuesday July 30

Hi Sarah,

Heads up before you notice — the Klaviyo flow rebuild won't
be ready Friday as committed. We're delivering Tuesday July 30
instead.

Why: a bug in the segmentation logic surfaced Wednesday during
final testing — customers in the cart-abandon flow were getting
matched to the cold-lead segment under one condition. Took a day
to track down, needs another two to fix and re-test against the
full list.

Nothing else in the engagement is affected. Performance fixes
are still on schedule for the August 9 milestone. BF November
timeline isn't impacted.

We caused the slip — apologies for not flagging earlier in the
week. If a quick call would be useful Monday before the new
delivery, I can find time. Otherwise expect the handoff
Tuesday morning.

— Valdeir

---

## Why this works (rationale for partner review)
- **The news in line 1:** new date is named in the first sentence,
  including the day of the week to make it scannable.
- **The ask:** No "ask" per se — this is a notification with an
  offered call option, not a request. Sometimes there is no ask.
- **What we did NOT say:**
  - No multi-paragraph apology
  - No blaming testing, the library, the client, or "an unexpected
    issue"
  - No promise the new date is locked-in without saying why we
    believe it (two days to fix and re-test is concrete)

## Variant: shorter (long-term relationship)

Hi Sarah,

Klaviyo handoff slipping to Tuesday July 30 — segmentation bug
took longer to track than expected. Performance + BF timeline
untouched. Sorry for the slip.

— V
```

---

## Notes for the agency

- Both emails open with the actual news in the first line. Long-term
  relationships earn this directness — new clients get one more
  sentence of context first.
- Notice neither email uses "unfortunately", "regrettably", or "we
  appreciate your patience". These soft openers are corrosive over
  time.
- The missed-deadline email owns the slip ("We caused the slip")
  in one sentence — no more, no less. Repeated apology is worse
  than no apology.
- The variant short versions exist because for long-term clients,
  text-message-pace beats formal-email-pace. Use them when
  Sarah signs her messages with "S" instead of her full signature.
