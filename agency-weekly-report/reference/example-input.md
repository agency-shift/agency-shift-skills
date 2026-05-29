# Example raw input

This is the kind of mess an agency operator usually has at the end of the week. The skill turns it into a client-ready report.

## Context
- Client: Brackenfell Coffee Roasters (Dublin, e-commerce + 2 cafés)
- Week range: May 19–25, 2026
- Account manager: Saoirse
- Quarter goal: 25% lift in online subscription revenue; launch wholesale program

## Raw notes from the week

**Mon 19/05**
- Standup: kicked off A/B test on subscription page (variant: shorter form, removed company-name field)
- Meeting with Conor (their CMO) — he confirmed wholesale program launch pushed to June 10
- I exported last month's subscription metrics, saw something weird in the trial-to-paid conversion — dropped from 38% to 24%. Flagged it.

**Tue 20/05**
- Designed 3 new banner variants for the homepage "Roaster of the Month" feature
- Conor approved 2 of them, asked us to drop variant C (too dark)
- Found the trial-to-paid drop is related to the form field change from last week. Reverted.
- Trial-to-paid back up to 35% within 24h. Sent slack message to Conor.

**Wed 21/05**
- Shipped the 2 approved banners on staging
- Worked on the wholesale form copy with Niamh (their content lead)
- Slack with Conor: he wants the wholesale form to integrate with their MYOB invoicing system. New scope, need to estimate.

**Thu 22/05**
- Pushed banners to prod
- CTR on Roaster of the Month went from 1.2% to 2.8% on the new banners
- Started wholesale form integration spike — confirmed MYOB has a public API, ~4 hrs of work to integrate
- Niamh blocked on wholesale FAQ copy because she's out sick. Need someone to cover.

**Fri 23/05**
- Subscription page A/B test concluded — short-form variant won, +14% trial signups. Rolling out 100%.
- Sent Conor the wholesale MYOB integration estimate (€600, 4–6 hrs)
- Friday review: Niamh still out, FAQ copy stuck

## Metrics for the week
| Metric | This week | Last week |
| --- | --- | --- |
| Trial signups | 187 | 164 |
| Trial-to-paid conversion | 35% | 24% (recovered from regression) |
| Roaster of the Month CTR | 2.8% | 1.2% |
| Revenue (online) | €18,420 | €17,200 |
| Wholesale leads (new) | 6 | 4 |

## What we need from client
- Decision on €600 MYOB integration estimate
- Backup writer for Niamh's FAQ copy (she's out 1–2 more weeks)
- Confirm wholesale launch date (still June 10?)
