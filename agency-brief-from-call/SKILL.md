---
name: agency-brief-from-call
description: Turn a raw sales, discovery, or kickoff call transcript into a structured project brief with scope, deliverables, deadlines, decision-makers, and open questions. Use whenever the user pastes a call transcript (Otter, Fireflies, Fathom, Zoom auto-transcript, voice memo transcription) and asks for "the brief", "the scope doc", "the SOW input", or "turn this call into a brief". Do NOT use this skill for internal team meeting notes or for one-off conversation summaries — it is specifically scoped to client-facing project briefs that will be sent back to the client for sign-off.
license: MIT
---

# agency-brief-from-call

You are turning a raw call transcript into a project brief that the agency will send back to the prospect or client for written agreement. The reader is a busy decision-maker. Your output replaces a 60–120 minute manual extraction task and prevents the most common agency failure: misaligned scope.

## When this skill applies

The user has pasted any of:

- Otter.ai / Fireflies.ai / Fathom / Zoom / Granola transcript export
- A pasted Notion or Doc page with raw call notes
- A voice memo or video transcription
- A long Slack/Loom thread that documents a call

And the user has asked for "the brief", "scope doc", "SOW prep", "project plan", or "turn this into a brief".

Do NOT use this skill for:
- Internal team retros or standups
- Sales call summaries that are NOT going back to the client
- Strategy memos for the agency's own planning

## Hard rules

1. **Ask for the missing inputs before writing.** Required: `client_name`, `transcript` (paste-in or file path), `agency_name` (defaults to "the agency" if missing). Strongly preferred: `prior_emails` for context, `stated_budget` if it came up.

2. **Never invent scope items.** If a deliverable is not explicitly named or strongly implied in the transcript, omit it. If the client said "we might also need X", file it under "Out of scope / future" — not in the core deliverable list.

3. **Surface every open question.** Anything the client said "we'll figure that out later" or "I'll check with my team on" gets a numbered question in the **Open questions** section. Open questions are the deal — they are NOT a sign the brief is incomplete.

4. **Name the decision-maker explicitly.** If multiple people were on the call, identify who has sign-off authority. If unclear, ask in **Open questions**.

5. **Flag scope risk in plain English.** If the transcript reveals a likely scope blow-up (vague success criteria, "we'll iterate as we go", no clear definition of done), call it out in **Risks** — even if the client didn't.

6. **Quote the client where it sharpens the brief.** A short direct quote ("we need this live before Black Friday") beats your paraphrase. Use quotes sparingly — 2–4 max — and always with the speaker named.

## Output structure

Use this exact markdown skeleton:

```markdown
# [Client name] — Project brief
**Source:** [date] call with [names of attendees on client side]
**Prepared by:** [Agency name]

## What we heard
A 3–5 sentence summary of the business problem the client articulated. Lead with the outcome they want, not the activity. End with their stated timeline if one was given.

## Scope
### In
- [Specific deliverables, each one line, lead verb]

### Out (for this engagement)
- [Things explicitly named that are NOT in scope, OR strong "maybe later" signals]

## Success criteria
- [How we'll know this engagement worked. Use the client's words if they gave criteria.]

## Timeline
- **Start:** [date or "TBC pending sign-off"]
- **Key milestones:** [list with target dates if given]
- **End:** [date or "TBC"]

## Decision-makers & approvers
- **Primary sign-off:** [name, role] — [why this person]
- **Other stakeholders:** [name, role, role in the project]

## Budget signal
[One paragraph. If a number was named, quote it. If a range was given, name the range. If avoided, write "Not discussed on the call." Do not invent.]

## Open questions
1. [Question, one line each]

## Risks
- [Anything in the transcript that could blow up scope, timeline, or trust]

## Next step proposed
[One concrete next step the agency proposes — e.g. "We send a fixed-fee SOW by [date] reflecting the scope above. Once you sign, we kick off the following Monday."]
```

## Tone calibration

- "Client needs a refreshed homepage live before Black Friday peak (mentioned: Nov 15 deadline)." ✓
- "Client is looking to potentially explore options around their digital presence." ✗
- "Open question: who owns the brand voice guidelines if no one has them written down today?" ✓
- "We may need to discuss some additional considerations around brand assets." ✗

## Length target

400–900 words total. If the transcript is so dense that the brief would run longer, ask which workstream to compress. Briefs over 1,000 words signal lack of clarity, not thoroughness.

## Self-check before delivering

Before returning the final brief, verify:

- [ ] No invented deliverables — every item in **Scope: In** has a transcript reference you could point to
- [ ] At least one **Open question** (it's almost impossible for a discovery call to have zero)
- [ ] Decision-maker named or explicitly flagged as unknown
- [ ] At least one **Risk** if the engagement is non-trivial
- [ ] A concrete **Next step proposed** — not "we'll be in touch"
- [ ] No emoji, no buzzwords, no "we are excited to..."

If any check fails, fix and re-verify before returning to the user.

## See also

- `reference/example-walkthrough.md` — sample raw transcript + finished brief
