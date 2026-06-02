---
name: agency-deliverable-handoff
description: Package a finished deliverable for client handoff — produces the handoff message, the QA checklist that proves it's done, the asset link manifest, and the next-action ask. Use whenever the user says "ship this", "hand this over", "send to client", "deliverable is ready", or pastes a list of done items + asset URLs and asks for the handoff message. Do NOT use this skill for weekly status updates (use agency-weekly-report instead) or for internal team handoffs between two agency staff.
license: MIT
---

# agency-deliverable-handoff

You are packaging a finished deliverable for the client. The recipient is the client's primary contact. They are not going to read a long message — they are going to scan, click two or three links, run a quick check, and either approve or reply with one change request. Your output replaces the 30–60 minute "let me write the handoff email" task that often gets postponed and creates the impression the work isn't actually done.

## When this skill applies

The user has indicated a deliverable is ready and provided some combination of:

- A list of done items (Linear / Jira / Asana ticket IDs marked complete)
- Asset URLs (Figma, Loom, hosted PDFs, staging links, repo branches)
- Notes on what was changed vs the original brief
- Open known issues that aren't blockers

And the user has said: "ship it", "send to client", "handoff", "deliverable ready", "wrap up", or pasted assets and asked for the message.

Do NOT use this skill for:
- Weekly status updates → use `agency-weekly-report`
- Internal handoffs between two agency team members (different format needed)
- Pre-handoff QA inside the agency (use `agency-content-qa` first, then come back here)

## Hard rules

1. **Require the deliverable scope before writing.** Required: `client_name`, `deliverable_name` (what was promised — e.g. "homepage redesign", "Q2 brand audit", "weekly content batch May 19–25"), and at least one `asset_link`. Strongly preferred: `original_brief` for scope-back-reference, `known_issues` if any.

2. **Compare against the brief.** If `original_brief` was provided, every item in the brief gets a status: shipped, descoped, deferred. No item silently disappears.

3. **Name known issues honestly.** If something is "done but a bit rough" or "shipped but we want to revisit X", it goes in **Known issues** with a proposed fix path. Hiding issues until the client finds them is the fastest way to lose a retainer.

4. **One ask, not three.** The handoff message ends with ONE clear ask of the client: approve, give feedback by date X, or trigger the next phase. Multiple asks dilute the response rate.

5. **Asset list with verb labels.** Don't dump raw URLs. Each link gets a verb-led label: "Preview the staging build", "Review the Figma comments", "Approve the merge to main". The verb makes the link self-explanatory.

6. **Match the relationship tone.** If `tone` is provided (e.g. "long-time client, informal", "new client, polished"), match it. Default: confident, plain-English, no exclamation marks, signed with first name only.

## Output structure

Use this exact markdown skeleton:

```markdown
# Handoff — [Deliverable name]
**Client:** [client name]
**Delivered:** [today's date]

## The message (paste-ready)

Subject: [Deliverable name] is ready for review

[Salutation],

[2–3 sentences. Open with what's shipped + one outcome sentence + one transition to the asset list.]

**Where to look:**
- [Verb-led label] → [URL]
- [Verb-led label] → [URL]
- [Verb-led label] → [URL]

[1–2 sentences. Reference any known issues briefly with a link to the issues section, OR confirm the work matches the brief. Make the ONE ask.]

[Signoff], [first name]

---

## QA checklist (internal — verify before sending)
- [ ] All asset URLs open without a login prompt for the client
- [ ] Every brief item has a status (shipped / descoped / deferred)
- [ ] Known issues are named, not hidden
- [ ] The reply ask is concrete (approve / change / schedule)
- [ ] No internal Slack / Linear / Notion URLs leak in the asset list
- [ ] The deliverable runs/loads/renders on the device the client uses (desktop AND mobile if relevant)

## Scope check against brief
| Brief item | Status | Note |
|---|---|---|
| [item] | shipped / descoped / deferred | [one-line context] |

## Known issues (will be in the client message above only if material)
- [issue, with proposed fix or "we'll handle in maintenance"]
```

## Tone calibration in the client message

- "The homepage redesign is live on staging. Faster on mobile, conversion-tracking wired up, ready for your review." ✓
- "We are thrilled to share that we have completed the homepage redesign deliverable!" ✗
- "Two small things to flag: form field validation has a known race condition on Safari — fix is queued for this week. Doesn't block your review." ✓
- "Everything is perfect, no issues at all." ✗ (almost never true; clients distrust this)

## Length target

Client message: 100–250 words. Beyond that, the client stops reading before the ask.
Internal QA + scope-check: as long as needed.

## Self-check before delivering

Before returning to the user, verify:

- [ ] The message is paste-ready (no `[placeholder]` tokens)
- [ ] Asset list has 2–5 links (1 is suspicious, 6+ is overwhelming)
- [ ] Each link has a verb-led label
- [ ] One concrete ask in the closing line
- [ ] Brief scope check is filled in if `original_brief` was provided
- [ ] No emoji, no "thrilled", no "we hope you love it"

If any check fails, fix and re-verify before returning to the user.

## See also

- `reference/example-walkthrough.md` — sample deliverable inputs + finished handoff message
