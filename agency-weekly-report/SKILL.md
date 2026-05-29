---
name: agency-weekly-report
description: Generate a polished, client-ready weekly status report for a marketing, content, or creator agency client. Use whenever the user asks to "build the weekly report", "write the Friday update", "summarize the week for [client name]", or pastes raw work logs / Linear / Notion exports and asks for a client-facing summary. Do NOT use this skill for internal team retros or for individual employee performance reviews — it is specifically scoped to outbound client communication.
license: MIT
---

# agency-weekly-report

You are generating a weekly status report that an agency owner or account manager will send to a paying client. The recipient is busy, slightly skeptical, and reads on mobile. Your output replaces a 60–90 minute manual writing task.

## When this skill applies

The user has just asked you to build a weekly client update, OR has pasted any combination of:

- Raw notes from the week (slack messages, daily standups, voice memos transcribed)
- Linear / Jira / Asana ticket exports
- Notion task database exports
- GA / Plausible / GSC metrics dumps
- Slack #client-name channel scrollback

Do NOT use this skill for internal team retros, performance reviews, or one-off project recaps.

## Hard rules

1. **Always ask for the missing inputs before writing.** Required: `client_name`, `week_range` (e.g. "May 19–25, 2026"), and `raw_inputs` (paste-in or file path). Optional but strongly preferred: `client_goals` for the quarter, `prior_week_report` for continuity.

2. **Never invent metrics.** If a number is not in the inputs, omit it. Do not estimate, round, or "reasonable-default" any KPI. A missing metric is better than a wrong one — clients lose trust fast over numerical errors.

3. **Lead with outcomes, not activity.** "Shipped X" beats "Worked on X for 6 hours." Translate task lists into business impact wherever possible.

4. **Surface blockers honestly.** A clean report with no blockers reads as performative. If the inputs show stuck work, name it and propose the unblock ask in the "We need from you" section.

5. **Match the tone of the prior report** if one is provided. If not, default to: confident, plain-English, no buzzwords, no emoji, no exclamation marks.

## Output structure

Use this exact markdown skeleton:

```markdown
# [Client name] — Weekly update
**Week of [date range]**

## Highlights
- [3–5 bullet outcomes, one line each, lead verb]

## What we shipped
- [Specific deliverables, with links where relevant]

## In progress
- [What's in flight + expected ship date]

## Blockers / risks
- [Honest list; "None this week" only if truly true]

## Metrics
| Metric | This week | Last week | Δ |
|---|---|---|---|
| [only metrics present in inputs] |

## We need from you
- [Asks: approvals, content, access, decisions]

## Next week
- [Top 3 priorities — concrete, not "continue work on X"]
```

Render the table in the Metrics section only if at least 2 metrics are provided with comparison values. Otherwise use a plain bullet list.

## Tone calibration

- "We shipped the homepage hero redesign" ✓
- "We have been working on iterating the homepage experience" ✗
- "Conversion dropped 12% — investigating the form field change" ✓
- "Conversion saw some headwinds this period" ✗

## Length target

400–700 words total. If the user's inputs produce more, ask which workstream to compress. Clients abandon reports over 800 words on mobile.

## Self-check before delivering

Before returning the final report, verify:

- [ ] No invented numbers
- [ ] At least one concrete next-week priority
- [ ] Blockers section is honest (not blank if there were any)
- [ ] No emoji, no buzzwords, no exclamation marks
- [ ] Length 400–700 words

If any check fails, fix and re-verify before returning to the user.

## See also

- `reference/example-input.md` — sample raw week inputs
- `reference/example-output.md` — sample finished report
- `reference/report-template.md` — bare markdown template
