---
name: agency-incident-recap
description: Turn the messy timeline of a project incident (something broke, missed launch, data issue, deployment that took down a client site, integration that silently failed) into a client-facing recap with what happened, impact, fix, and prevention. Use whenever the user pastes a Slack thread, error log, postmortem doodle, or describes "we had an issue with X" and asks for "the recap", "the apology email", "what do I tell the client". Do NOT use this skill for routine "thing didn't work, we fixed it in five minutes" updates — only for incidents the client noticed or should be told about proactively.
license: MIT
---

# agency-incident-recap

You are producing the document that determines whether the agency keeps the client after a real incident. The recap is two things at once: a calm, factual record of what happened (so the client can stop worrying about it) and an honest commitment to prevention (so they don't churn). Your output replaces the "let me write this carefully tomorrow" message that gets postponed and becomes the moment the relationship cools.

## When this skill applies

The user describes or pastes evidence of an incident:

- Slack thread of the team responding to something breaking
- Error logs / monitoring screenshots / Vercel/AWS notifications
- A client message saying "what happened with X" or "the site was down"
- A postmortem doodle / notes file the team wrote internally
- A description: "we missed the launch", "the email blast went to the wrong list", "the API integration silently failed for 3 days"

And the user has asked for: "the recap", "what do I tell the client", "incident report", "the apology email", "the postmortem", or pasted with intent to send something to the client.

Do NOT use this skill for:
- Routine bug fixes the client didn't notice (don't manufacture incidents)
- Internal-only postmortems (different format — those need root-cause analysis depth this skill skips)
- General "weekly report" status (use `agency-weekly-report`)

## Hard rules

1. **Establish the timeline before writing anything.** Required: `incident_summary` (one sentence — what broke), `start_time` and `end_time` (when did it start, when did it stop), `client_facing_impact` (what did the client / their users actually experience), `cause` (what was the root or contributing cause). Strongly preferred: `evidence` (Slack thread, logs).

2. **Lead with impact, not cause.** The client cares about what they experienced first, the technical reason second. Open with: "Between [time] and [time], [client]'s [thing] was [unavailable / degraded / wrong]." Then go to cause.

3. **No "we are looking into it" closures.** Every recap ends with a fix that has shipped OR a fix that has a named owner and date. Open-ended language like "we are still investigating" belongs in an *interim update*, not a recap.

4. **Honest about agency fault, even when uncomfortable.** If the agency caused the incident (bad deploy, missed monitoring, human error), name it cleanly in **Cause**. Hiding behind "a complex set of factors" is the fastest path to losing the account.

5. **Never name an individual on the team.** "Our deploy pipeline had a misconfigured environment variable" is acceptable. "Marco deployed the bad config" is not. The agency owns the work as a unit; individual blame leaks out of the recap and damages morale.

6. **Prevention must be concrete.** "We've added monitoring" is vague. "We've added a Vercel deploy guard that fails the build if the production environment variable is missing — committed yesterday in commit abc1234" is specific. The client can tell the difference.

## Output structure

Use this exact markdown skeleton:

```markdown
# Incident recap — [Client name] — [Short incident name]

**Sent to client on:** [today's date]
**Incident window:** [start time] – [end time]   ([duration in minutes/hours])
**Severity:** [P0 client-fully-down / P1 client-degraded / P2 partial issue / P3 quiet issue]

## The client message (paste-ready)

Subject: [Specific. e.g. "Recap: Newsletter blast issue, May 21" — NOT "Following up" or "An update for you"]

[Salutation — first name],

[Sentence 1: what happened in client terms, with the time window.]

[Sentence 2–3: what their users / business experienced. Honest. Specific.]

[Paragraph 2: cause — in plain English. 2–4 sentences. No jargon shield.]

[Paragraph 3: fix — what's done, what's pending with owner + date.]

[Paragraph 4: prevention — concrete change to make this not happen again.]

[Closing — one sentence acknowledging the impact, one concrete next step (a call if needed, an offer like credit, or a clear "we're back to normal operations").]

[Signoff], [first name]

---

## Internal record (NOT sent to client — for the agency's own log)

### Timeline
| Time | Event |
|---|---|
| [hh:mm] | [event in 1 line] |

### Root cause (technical)
[Plain English explanation of what actually broke. This goes deeper than the client-facing version.]

### Contributing factors
- [Process / monitoring / human factors that made it worse]

### Actions taken
- [Action — date completed]

### Open actions
- [Action — owner — due date]

### What would have prevented this
- [Concrete safeguard]
- [Concrete safeguard]
```

## Tone calibration in the client message

- "Between 14:08 and 14:51 UTC on May 21, the May newsletter was sent to your full list of 18,400 subscribers with the wrong subject line ('TEST — do not send'). 43-minute window before we caught it and sent the corrected version." ✓

- "Yesterday afternoon we experienced a small issue with the newsletter system that affected a few users." ✗ (vague on time, vague on impact, "small" / "few" are softening hedges)

- "Cause: our staging-vs-production environment switch wasn't gated, and a draft job was promoted to production by a deploy that should have been staging-only. The job ran against the live list before our pre-send check fired." ✓

- "Cause: there was a complex interaction between several systems." ✗ (jargon shield)

- "Prevention: we've added a deploy-time check that fails the build if `STAGE_ONLY=true` is missing on staging deploys. Live in commit a1b2c3d, tested with a dry-run on May 22." ✓

- "Prevention: we've added more monitoring." ✗ (zero specificity)

## Length target

Client message: 180–350 words. Anything shorter looks dismissive of a real incident; anything longer signals the agency is over-explaining (which reads as defensive).
Internal record: as long as needed.

## Self-check before delivering

Before returning to the user, verify:

- [ ] First sentence of the client message names the time window and the impact
- [ ] Cause is in plain English, no jargon shield, owns agency fault if applicable
- [ ] Fix is either complete or has owner + date — never "investigating"
- [ ] Prevention names a specific safeguard, not "more monitoring"
- [ ] No individual team member named
- [ ] No emoji, no "thrilled", no "we appreciate your patience"
- [ ] Internal record has a full timeline (separate from the client message)

If any check fails, fix and re-verify before returning to the user.

## See also

- `reference/example-walkthrough.md` — sample incident inputs + finished client recap + internal record
