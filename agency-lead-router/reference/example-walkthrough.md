# Walkthrough — agency-lead-router

Sample run of the skill on an inbound contact-form submission.

---

## Input the user pastes

```
ICP definition (Hudson & Co.):
- Industry: DTC e-commerce, fashion / coffee / wellness verticals
- Company size: 5–30 staff, $1M–$10M revenue
- Budget band: $5K–$25K per engagement, willing to pay monthly retainer
- Pain trigger: post-launch growth stall, BFCM-deadline-driven, or
  previous-developer-left scenarios

Channel: Contact form submission via agencyshift.dev/contact

Received: just now

From: Jamie Lin <jamie@brackenfellcoffee.co>
Company: Brackenfell Coffee
Role: COO (per LinkedIn lookup)

Message:
Hey — I run ops at Brackenfell Coffee. We're a 14-person specialty
coffee subscription brand, ~$3M ARR, mostly UK. Black Friday is six
months out and we're not ready. Our old dev disappeared and we can't
even update the homepage. Klaviyo flows are a mess. We did $180K
last year on BF and want to push for $300K but we know the site is
the bottleneck.

Saw your weekly-report skill on GitHub — cool stuff. Are you taking
on new clients for the BF push? Budget would be in the $25K range
for the engagement.

Cheers,
Jamie
```

---

## Output the skill produces

```markdown
# Lead intake — Jamie Lin · Brackenfell Coffee
**Channel:** contact form (agencyshift.dev/contact)
**Received:** just now

## What they're asking
Are we available to take them on for a Black Friday performance + email
overhaul, budget ~$25K, six months out.

## ICP score: 7/8
| Dimension | Score | Note |
|---|---|---|
| Industry match | 2 | DTC e-commerce, coffee subscription — exact vertical |
| Company size | 2 | 14 staff, ~$3M ARR — squarely inside 5–30 / $1M–$10M band |
| Budget signal | 2 | $25K named upfront — top of our range, no negotiation hedge |
| Pain trigger | 1 | BFCM-deadline ✓, previous-dev-left ✓. Not a 2 only because timeline (six months) is generous — not panic-mode |

## Recommended route
- **Owner:** Partner / principal — this is a high-fit, high-budget lead
- **Action:** Book a discovery call within the next 48h
- **Reply by:** End of today (don't sit on a 7/8 lead)

## Reply draft

Subject: Re: BF push — yes, let's talk

Hi Jamie,

Short answer: yes, we have capacity for one more BFCM engagement
starting in the next two weeks. Brackenfell sounds like a good fit
based on what you've described — DTC coffee, 14 staff, lost
developer, six-month window.

Before we book a call, three quick questions so we don't waste each
other's time:

1. Can you get repository and hosting access for the existing site,
or are we partly rebuilding from scratch?
2. What's your current mobile conversion rate? Sales analytics is
where we'd start the audit.
3. Is the $25K a hard ceiling, or a starting figure if we land on a
scope that needs slightly more?

If those land OK on your end, I have Thursday at 3 PM UK or Friday
at 10 AM UK open this week — 30 minutes, no deck, just a conversation.

— Valdeir

## Open questions
1. Can the previous developer's hosting access be recovered, or is
this a partial-rebuild scenario?
2. Current mobile conversion rate (anchor for the "$300K vs $180K"
target's feasibility)
3. Is the $25K firm or flex?
4. What's their current Klaviyo plan tier — affects flow architecture
choices

## If this becomes an opportunity
- **Next agency step:** 30-min discovery call this week → fixed-fee
SOW within 48h of call → kickoff the Monday after sign-off
- **Likely deal shape:** Fixed-fee project ($20K–$25K) with optional
retainer for post-BF maintenance (Dec–Feb)
```

---

## Notes for the agency

- ICP score of 7/8 is high — partner-level, fast reply.
- Notice the reply asks three qualifying questions BEFORE booking a
  call. This protects calendar time and surfaces deal-killers early.
- The reply uses Valdeir's first name only because the relationship is
  new-but-direct — Jamie signed informally with "Cheers, Jamie".
- "$25K is a starting figure if we land on a scope that needs slightly
  more" question 3 — this is the test for whether the budget is
  anchored or anchored-with-flex. Materially changes how the SOW is
  structured.
- The skill never assumes Jamie's BF target ($300K) is achievable. The
  partner can decide that on the call.
