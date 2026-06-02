# Walkthrough — agency-brief-from-call

Sample run of the skill on a typical inbound discovery-call transcript.

---

## Input the user pastes

```
Client name: Brackenfell Coffee
Agency name: Hudson & Co.

Transcript (Otter export, edited for length):

[00:01] Sarah (Brackenfell, CEO): Thanks for jumping on. So we've got the
Black Friday push coming up — November 28 — and we've got nothing
ready. The site's the bottleneck. It loads slow, the cart abandons,
and we can't even change the homepage without our old dev.

[00:03] Mike (Brackenfell, COO): The Klaviyo flows are a mess too.
We're not segmenting at all. Returning customers get the same emails
as cold leads.

[00:06] You (Hudson & Co.): What does "ready" look like for Nov 28?

[00:07] Sarah: The site needs to actually convert. We're at like 0.8%
on mobile, which is the bulk of our traffic. We did $180k on Black
Friday last year and we want to push for $300k. Realistic?

[00:09] You: It's tight but possible if we lock scope. What's not on
the list?

[00:11] Sarah: Anything redesign-y. No new brand work. We just want
the existing brand to load fast and convert. Mike?

[00:12] Mike: We'd also love to get subscriptions live but I know
that's a bigger lift. Let's park that.

[00:15] Sarah: Budget — we've got 25k allocated for this push.

[00:16] You: Who signs off on the work? Just the two of you?

[00:17] Sarah: Me. Mike consults but I sign.

[00:18] You: Last thing — your old dev. Is he around to hand over
access, or is that going to be a fight?

[00:19] Sarah: Honestly, no idea. Last we heard from him was March.
We can pay him a transition fee if needed but I'd rather rebuild
than negotiate.

[00:21] You: OK. Let me put together a brief and a fixed-fee SOW
for the November push. You'll have both by Friday.
```

---

## Output the skill produces

```markdown
# Brackenfell Coffee — Project brief
**Source:** May 22, 2026 call with Sarah (CEO) and Mike (COO)
**Prepared by:** Hudson & Co.

## What we heard
Brackenfell needs to hit $300K in Black Friday revenue on November 28 —
up from $180K last year. The current site is the bottleneck: slow load,
high mobile cart abandonment, and no one on the team can edit it
without the previous developer (last contacted in March, status
uncertain). Klaviyo email flows are unsegmented and treating returning
customers as cold leads. The window is six months and the budget for
the push is $25K.

## Scope
### In
- Performance audit + fixes on the existing storefront, mobile-first
- Cart abandonment recovery (technical + Klaviyo flow)
- Klaviyo segmentation rebuild: returning customer vs cold lead vs
  cart-abandoner
- Black Friday landing page or homepage variant for the campaign
- Pre-launch QA on a staging environment

### Out (for this engagement)
- Brand or visual redesign — Sarah was explicit: "no new brand work"
- Subscription product launch — Mike flagged as bigger lift, parked
- Negotiation or rebuild of relationship with previous developer

## Success criteria
- Mobile conversion rate above 1.5% during the Black Friday window
  (current: ~0.8%, target proposed by Sarah)
- Black Friday revenue: $300K target (vs $180K last year)
- Site loads under 2.5s LCP on mobile (no measurement provided yet —
  will benchmark in audit)

## Timeline
- **Start:** Within two weeks of SOW sign-off (target: week of June 3)
- **Key milestones:**
  - June 13 — Performance audit complete + fix plan
  - July 31 — Performance fixes shipped
  - September 15 — Klaviyo flows rebuilt + live
  - October 31 — Black Friday landing page complete + QA
  - November 25 — Final pre-launch QA on staging
- **End:** December 2, 2026 (post-BF retrospective + handoff)

## Decision-makers & approvers
- **Primary sign-off:** Sarah (CEO) — explicit: "Me. Mike consults but I sign."
- **Other stakeholders:** Mike (COO) — operational input, particularly
  on Klaviyo flow logic

## Budget signal
Sarah named $25K allocated for the Black Friday push. Scope above is
designed to fit within that budget. A fixed-fee SOW with milestone
billing will follow this brief.

## Open questions
1. Previous developer access — Sarah noted "we can pay a transition fee"
   but prefers rebuild. Need to confirm: can we get repository + hosting
   credentials within two weeks, or do we plan a rebuild from scratch?
2. Current Klaviyo plan tier + ESP limits — needed before we design the
   segmentation rebuild
3. Inventory & fulfillment readiness for the $300K target — is the
   warehouse/3PL ready for ~1.6x last year's volume?
4. Who on Brackenfell side reviews/approves Klaviyo email copy?

## Risks
- **Single-developer dependency on the previous dev** is the biggest
  blocker. If we cannot get access, the timeline compresses sharply
  because we'd be partly rebuilding rather than fixing.
- **No conversion baseline measurement** beyond Sarah's "0.8% on mobile"
  number. We need to install/verify analytics in week one or success
  criteria become impossible to evaluate.
- **Budget headroom is thin** for a six-month engagement with a hard
  date. Any scope creep will materially impact either the November 28
  launch quality or the cost.

## Next step proposed
Hudson & Co. will send a fixed-fee SOW reflecting the scope above by
Friday May 26. Once signed, kickoff the following Monday (June 1) with
the performance audit as the first deliverable.
```

---

## Notes for the agency

- Notice the brief never invented metrics. The "$300K target" is Sarah's
  number, not the agency's projection. The "0.8% mobile conversion" is
  her stated number, not a measurement we made.
- Three risks were surfaced even though Sarah/Mike didn't frame them as
  risks. This is the skill earning its keep.
- The previous-developer issue is BOTH in **Risks** and **Open
  questions** — risks are general, open questions are answerable.
- Budget paragraph is honest about being constrained without
  catastrophizing.
