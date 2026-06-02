# Agency Shift skills

Open-source Claude Code skills for marketing, content, and creator agencies.

The work most agencies still do by hand — briefing, weekly reporting, deliverable handoff, lead routing, content QA — is the work Claude Code is now best at. This repo is the operating system: skills you install once, your team runs forever, you own.

Maintained by [Agency Shift](https://agencyshift.dev) — an AI-native ops studio working with EU and UK agencies.

---

## Why skills, not agents or apps

A **Claude Code skill** is a single markdown file that tells Claude *when* to use a specific workflow and *how* to do it well. No infra, no API key dance, no third-party SaaS. The skill lives in your repo, your team can read and edit it, and it runs anywhere Claude Code runs (terminal, IDE, web).

That's the whole pitch. Skills are how you turn "Claude can probably help with this" into "the system always handles this correctly, the same way, every time."

---

## Skills in this repo

| Skill | Status | What it does |
|---|---|---|
| [`agency-weekly-report`](./agency-weekly-report) | ✅ Stable | Generate a polished, client-ready weekly status report from messy week notes. Replaces a 60–90 min manual task. |
| [`agency-brief-from-call`](./agency-brief-from-call) | ✅ Stable | Turn a raw sales / discovery / kickoff call transcript into a structured project brief with scope, deliverables, deadlines, decision-makers, open questions, and risks. |
| [`agency-lead-router`](./agency-lead-router) | ✅ Stable | Classify an inbound lead against your ICP (0–8 score), recommend the right owner and next action, and draft the first-touch reply. |
| [`agency-deliverable-handoff`](./agency-deliverable-handoff) | ✅ Stable | Package a finished deliverable for client handoff — produces the handoff message, the QA checklist that proves it's done, the verb-led asset list, and a single concrete ask. |
| [`agency-content-qa`](./agency-content-qa) | ✅ Stable | Run a near-final deliverable through a brand-voice + technical-correctness + client-fit review. Returns issues categorized as Blockers / Fixes / Nits with proposed rewrites. |
| [`agency-client-email`](./agency-client-email) | ✅ Stable | Compose the email for delicate recurring situations — scope change, missed deadline, payment reminder, project pause, kickoff confirmation, fee increase, end-of-engagement wrap, difficult feedback. |
| [`agency-incident-recap`](./agency-incident-recap) | ✅ Stable | Turn the messy timeline of a project incident into a calm, factual client-facing recap with what happened, impact, fix, and a concrete prevention safeguard. Includes an internal record. |

New skills ship every couple of weeks. [Watch this repo](https://github.com/agency-shift/agency-shift-skills/subscription) to get notified, or [open an issue](https://github.com/agency-shift/agency-shift-skills/issues) with a recurring agency task you'd want a skill for.

---

## Quick start

You need [Claude Code](https://claude.com/claude-code) installed (free during preview, no API key required for personal use).

```bash
# 1. Clone the repo into your project's .claude/skills directory
cd your-project
mkdir -p .claude/skills
git clone https://github.com/agency-shift/agency-shift-skills .claude/skills/agency-shift

# 2. Open Claude Code in the project
claude

# 3. List the available skills
/skills

# 4. Try any of them — e.g. the weekly report
> Build the weekly report for Brackenfell Coffee, week of May 19–25, using these notes: <paste your week>

# Or the brief-from-call skill on a call transcript
> Turn this Otter transcript into a project brief for Brackenfell: <paste transcript>

# Or the lead router on an inbound email
> Route this inbound, ICP attached. <paste email> <paste ICP>
```

That's it. Claude Code will recognize the skill, ask for any missing inputs, and deliver the output.

### Alternative: install just one skill

```bash
mkdir -p .claude/skills/agency-brief-from-call/reference
curl -sL https://raw.githubusercontent.com/agency-shift/agency-shift-skills/main/agency-brief-from-call/SKILL.md \
  -o .claude/skills/agency-brief-from-call/SKILL.md
```

---

## How we design these skills

Three rules we follow when adding to this repo:

1. **Outcome-shaped, not feature-shaped.** Every skill replaces a specific recurring task an agency operator already does badly or slowly. We don't ship "agentic AI for productivity" — we ship "the Friday client update."
2. **Hard rules over soft prompts.** Each skill includes a self-check the model runs before returning output. No invented metrics. No buzzwords. No "I'll do my best." Skills that can't be trusted with a paying client's eyes don't ship.
3. **Drawn from real agency work, not hypotheticals.** The patterns these skills encode — weekly reporting, brief extraction, lead routing, deliverable handoff, content QA, client emails, incident recaps — come from real freelance and in-house operator work. As the catalog matures, skills that have been battle-tested across multiple live accounts will be marked accordingly. If you find a case where one breaks, [open an issue](https://github.com/agency-shift/agency-shift-skills/issues) — the fix usually ships within a week.

---

## Contributing

We accept PRs that follow the [SKILL.md format](./agency-weekly-report/SKILL.md) and include `reference/` examples (input + output). Open an issue first if your skill doesn't fit one of the planned ones above — we keep the catalog tight on purpose.

---

## When you want more than skills

If you've installed a few skills and you're thinking *"someone should set up the whole stack for me"* — that's what Agency Shift does. Done-with-you installs on the best stack, owned by your team, four to six weeks.

**[agencyshift.dev](https://agencyshift.dev)** · [Book intro call](https://cal.com/valdeir-lima-yfs2lk/15min)

---

## License

MIT. Use them, fork them, rebrand them, ship them to your clients. We just ask that you don't strip the attribution from `SKILL.md` files when redistributing.
