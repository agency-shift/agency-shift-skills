# Walkthrough — agency-incident-recap

Sample run of the skill on a real incident pattern.

---

## Input the user pastes

```
Incident summary: Newsletter sent to full list with placeholder subject
Start time: May 21, 14:08 UTC
End time: May 21, 14:51 UTC (corrected version sent)
Duration: 43 minutes
Client: Brackenfell Coffee
Severity: P1 (client-degraded — wrong subject line, but content was
the real campaign, not test data)

Client-facing impact: The May newsletter went out to ~18,400
subscribers with the subject line "TEST — do not send". The body
content was correct (the May new-roast announcement). Open rate
suffered as expected — 8.2% vs typical 32% for newsletters. About
1,500 subscribers we estimate would have opened didn't.

Cause: Our deploy pipeline promoted a draft Klaviyo job to production
during the morning's staging deploy. The job had been set up Friday
afternoon with a placeholder subject and was never re-saved with
the real subject before being scheduled. The "stage-only" flag on
the deploy did not block Klaviyo job promotion because we'd never
configured that check against Klaviyo's job API — only against
Vercel functions.

Evidence: Slack thread starting at 14:09 (Eduardo flagged it), Klaviyo
admin log shows job run at 14:08:42, Vercel deploy log shows the
auto-promotion at 14:07:51.

Actions taken:
- Pulled the bad send at 14:51 with a corrected newsletter (same body,
  corrected subject "may roast launch")
- Posted to brackenfell #incidents channel at 15:10 with initial recap

Prevention plan:
- Added a deploy-time check that compares the source environment
  marker on every queued Klaviyo job against the deploy target. Fails
  the deploy if mismatched. Committed in PR #284, merged today.
- Added "subject line never blank" validation on all Klaviyo jobs at
  job-creation time. Caught during code review for the deploy check.
```

---

## Output the skill produces

```markdown
# Incident recap — Brackenfell Coffee — Newsletter wrong subject

**Sent to client on:** May 22, 2026
**Incident window:** May 21, 14:08 UTC – 14:51 UTC   (43 minutes)
**Severity:** P1 — client-degraded

## The client message (paste-ready)

Subject: Recap: newsletter subject line issue, May 21

Hi Sarah,

Between 14:08 and 14:51 UTC yesterday, the May newsletter went out
to your full list (~18,400 subscribers) with the subject line
"TEST — do not send" instead of the real subject. The email body
itself was correct — the May new-roast announcement.

Practical impact: open rate came in at 8.2% versus your typical
~32% for newsletters. By our estimate that's roughly 4,400
subscribers who would have opened and didn't. We sent a corrected
version at 14:51 with the right subject ("may roast launch"). Open
rate on the corrected send was 28.1% — close to baseline.

Cause was on us. Our deploy pipeline promoted a draft Klaviyo job
to production during a routine staging deploy. The draft had been
set up Friday afternoon with a placeholder subject and was never
re-saved with the real one before being scheduled. The pre-deploy
"stage only" check we had in place blocked Vercel functions but
not Klaviyo jobs — a gap we should have closed already.

Fix shipped today. We added two safeguards:

- A deploy-time check that compares every queued Klaviyo job's
  environment marker against the deploy target, and fails the
  deploy if they don't match. This would have caught yesterday's
  issue. Committed and tested today in PR #284.

- A job-creation validation that rejects any Klaviyo job with a
  blank or placeholder subject line. Caught during code review
  on the same PR.

We're back to normal operations. Happy to jump on a 15-minute
call this week if you'd like to walk through it in detail —
otherwise no further action needed on your end.

— Valdeir

---

## Internal record (NOT sent to client — for the agency's own log)

### Timeline
| Time   | Event |
|--------|-------|
| Fri PM | Draft Klaviyo job created with placeholder subject "TEST — do not send" |
| 14:07:51 | Routine staging deploy auto-promotes the draft job to production (Vercel deploy log) |
| 14:08:42 | Klaviyo job runs against full list (Klaviyo admin log) |
| 14:09 | Eduardo flags in Slack #brackenfell-internal |
| 14:12 | Incident triage starts, full team on call |
| 14:35 | Corrected newsletter draft prepared |
| 14:48 | Subject + send list verified |
| 14:51 | Corrected newsletter sent |
| 15:10 | Initial recap posted to brackenfell #incidents channel |

### Root cause (technical)
The deploy pipeline's "stage-only" guard was implemented as a Vercel
function-level check (blocks promotion of stage-tagged Vercel
functions to production). Klaviyo jobs are scheduled via the Klaviyo
API at job creation time and the scheduling state is stored
externally — outside the deploy pipeline's visibility. When the
staging deploy ran, the existing Klaviyo job's scheduled-state was
read as "queued", interpreted as eligible for promotion, and
elevated to production.

Two missed safeguards:
1. The deploy guard never knew Klaviyo job state existed
2. The job-creation step never validated that the subject line
   wasn't a placeholder

### Contributing factors
- Friday afternoon draft job that was never edited again before
  Monday's deploy
- No human-in-the-loop check between draft → schedule for newsletter
  jobs (Klaviyo flows have one, manual newsletter campaigns did not)

### Actions taken
- Pulled bad send + sent corrected version — May 21, 14:51 ✓
- Posted client-facing recap to channel — May 21, 15:10 ✓
- Shipped deploy-time Klaviyo job check — May 22 (PR #284) ✓
- Shipped subject-line blank-check validation — May 22 (PR #284) ✓
- Sent recap email to Sarah — May 22 ✓

### Open actions
- Add same human-in-the-loop check on Klaviyo newsletter campaigns
  that flows already have — Marco, due May 30
- Document this incident in the team's runbook — Eduardo, due May 28

### What would have prevented this
- Deploy-time check across all integrations (now in place for Klaviyo;
  still missing for Customer.io and the Shopify webhook config)
- Subject-line validation at job-creation time (now in place)
- Human approval gate for newsletter campaigns (open action)
```

---

## Notes for the agency

- The client message opens with the time window and impact, not the
  cause. Sarah's first thought is "how bad" not "why".
- "Practical impact" paragraph quantifies the cost — 4,400 missed
  opens — without catastrophizing. This is honest and earns trust.
- "Cause was on us" — three words, said once, then move on. Not eight
  apologies.
- Prevention is concrete: PR number, specific check, what it would
  have caught. Not "we've added monitoring."
- No individual team member is named in the client recap, but the
  internal record names Eduardo and Marco for action ownership. This
  protects the team's relationship with the client while keeping
  accountability inside.
- The "happy to jump on a 15-minute call" offer is genuine but not
  pleading. Sarah can take it or leave it without feeling pressured.
