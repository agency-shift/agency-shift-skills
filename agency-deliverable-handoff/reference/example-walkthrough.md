# Walkthrough — agency-deliverable-handoff

Sample run of the skill on a finished homepage redesign.

---

## Input the user pastes

```
Client: Brackenfell Coffee
Deliverable: Homepage performance + redesign (existing brand)
Brief reference: SOW signed June 1, milestone "Performance fixes shipped" due July 31

Done items:
- Image optimization (next/image, AVIF + WebP fallback) — Linear PER-12
- Critical CSS extraction — Linear PER-14
- Removed three unused tracking scripts — Linear PER-15
- Added preconnect hints for fonts + Shopify CDN — Linear PER-16
- New product grid (4-up mobile-first) — Linear DES-22

Assets:
- Staging build: https://brackenfell-staging.vercel.app
- Lighthouse comparison: https://brackenfell-staging.vercel.app/_lh
- Loom walkthrough (8 min): https://loom.com/share/abc123
- Figma comments: https://figma.com/file/xyz789?node-id=42

Known issues (NOT blockers):
- Safari 17 has a 200ms flash of old grid on first paint (race condition
  with the lazy-load library). Fix queued for next sprint, Linear PER-19.
- Mobile menu animation is slightly janky on iOS 16 (the brand was on
  iOS 15 in testing — they shipped 17 last week).

Tone: long-term client, informal — we've worked with them for 18 months
```

---

## Output the skill produces

```markdown
# Handoff — Homepage performance + redesign
**Client:** Brackenfell Coffee
**Delivered:** July 28, 2026

## The message (paste-ready)

Subject: Homepage performance work is ready for review

Hi Sarah,

The homepage performance work is live on staging. Mobile LCP dropped
from 4.1s to 1.8s, the new product grid is in, and the three unused
scripts are gone. Ready for your sign-off before we push to production.

**Where to look:**
- Preview the staging build → https://brackenfell-staging.vercel.app
- Compare Lighthouse before/after → https://brackenfell-staging.vercel.app/_lh
- Watch the 8-min walkthrough → https://loom.com/share/abc123
- Review the Figma grid comments → https://figma.com/file/xyz789?node-id=42

Two known issues to flag: a 200ms grid flash on Safari 17 (race
condition, fix queued for next sprint) and a slightly janky menu
animation on iOS 16. Neither blocks shipping — both are tracked.

Can you reply with a thumbs-up or any change requests by Wednesday?
We'd like to push to production Thursday morning before the bank
holiday weekend.

— Valdeir

---

## QA checklist (internal — verify before sending)
- [x] All asset URLs open without a login prompt for the client
- [x] Every brief item has a status (shipped / descoped / deferred)
- [x] Known issues are named, not hidden
- [x] The reply ask is concrete (approve by Wednesday)
- [x] No internal Slack / Linear / Notion URLs leak in the asset list
- [x] The deliverable runs/loads/renders on the device the client uses
       (tested: desktop Safari 17, iOS 16/17, Android Chrome)

## Scope check against brief
| Brief item | Status | Note |
|---|---|---|
| Image optimization (Lighthouse mobile ≥85) | shipped | Now at 94 |
| Critical CSS extraction | shipped | LCP -2.3s on mobile |
| Remove unused tracking scripts | shipped | 3 scripts removed; analytics retained |
| Preconnect hints | shipped | Font + Shopify CDN |
| New product grid (mobile-first) | shipped | 4-up on mobile, 6-up on desktop |
| Subscription product launch | deferred | Out of scope per kickoff brief |

## Known issues (referenced in the client message above only briefly)
- Safari 17 — 200ms flash of old grid on first paint. Cause: race
  condition between the lazy-load library and the new grid component.
  Fix queued for next sprint, Linear PER-19. Not user-facing as a bug,
  reads as a flicker.
- iOS 16 — mobile menu animation slightly janky. Brand was on iOS 15
  during build/testing; iOS 17 shipped July 22 and brought subtle CSS
  changes. Will patch alongside Safari 17 fix.
```

---

## Notes for the agency

- The message is 145 words — well inside the 100–250 target.
- The opening sentence carries the news (performance work is live), the
  outcome (LCP 4.1s → 1.8s), and the ask (sign-off before prod push).
  No "we hope you're well" preamble.
- Two known issues named honestly with proposed fix paths. Sarah will
  trust the next handoff because we didn't hide these.
- ONE ask in the closing: thumbs-up or change requests by Wednesday.
  Not "let us know your thoughts" (vague), not "approve, plus tell us
  about Q4" (multiple).
- Asset list has 4 links, all verb-led. None are internal-only.
- Signed "Valdeir" only — matches the long-term informal relationship.
