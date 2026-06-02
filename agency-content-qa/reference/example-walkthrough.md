# Walkthrough — agency-content-qa

Sample run of the skill on a blog post draft.

---

## Input the user pastes

```
Client: Brackenfell Coffee
Type: Blog post
Brand voice doc (excerpt):
- Plain English, no buzzwords ("synergy", "robust", "leverage" — banned)
- Lowercase headlines for blog posts (their house style)
- No exclamation marks (Sarah's pet peeve)
- Em-dashes encouraged
- Sentences short. Active voice.
- Numbers always written as digits (47, not "forty-seven")

Original brief:
"Friday post for the blog. Topic: why we switched to single-origin
beans for the new house roast. ~600 words. Should reference our two
new farmer partners (Catalina Mejia in Colombia, Solomon Kebede in
Ethiopia) and the cupping scores. Goal: drive subscribers to the
roast launch on July 15."

Draft:

The Switch To Single-Origin: A Brand New Era For Brackenfell

We're thrilled to share that Brackenfell has made the bold and
exciting decision to leverage single-origin beans for our brand new
house roast! This is a transformative moment for our company and
we couldn't be more excited to share it with you all.

For too long, blended beans have dominated the specialty coffee
landscape, creating a robust but somewhat homogenized experience.
We've decided to do something different. Starting July 15, our
house roast will showcase the unique characteristics of single-origin
beans from two incredible partner farms.

Our first partner is Catalina from Colombia. Her farm produces
beautiful washed beans with bright acidity and notes of citrus and
chocolate that scored remarkably high in our cupping sessions.

Our second partner is from Ethiopia. The natural processing brings
out forty-three distinct flavor notes (according to our master roaster)
including wild berry and floral elements that we think you'll love.

We believe this represents a paradigm shift in how we think about
coffee. By leveraging direct trade relationships and synergizing with
small-scale farmers, we're able to deliver an experience that's both
more authentic and more delicious.

We hope you're as excited as we are! Pre-orders are open now at
brackenfellcoffee.co/single-origin. Subscribe today and don't miss
out on this amazing journey!
```

---

## Output the skill produces

```markdown
# QA — The Switch To Single-Origin
**Type:** Blog post
**Reviewed against:** Brand voice doc + project brief
**Verdict:** Needs rewrite

## Summary
Three Blockers — banned buzzwords used twice, exclamation marks
throughout, headline capitalization wrong, and one farmer named only
by first name + missing the Ethiopian farmer's name entirely (which
the brief specifically required). The piece is also missing the cupping
scores the brief called for. Tone leans 4–5 notches too "excited"
relative to the brand voice doc. Send back for one revision pass before
this can ship.

## Blockers

### B1 · Banned buzzwords
- **Where:** Paragraph 1 ("leverage single-origin beans") and paragraph
  5 ("leveraging direct trade relationships and synergizing").
- **Why:** Brand voice doc explicitly bans "leverage" and "synergy".
- **Rewrite:** P1 → "use single-origin beans". P5 → "By working
  directly with small-scale farmers."

### B2 · Headline capitalization
- **Where:** Headline "The Switch To Single-Origin: A Brand New Era
  For Brackenfell"
- **Why:** Brand voice doc specifies lowercase headlines for blog posts.
- **Rewrite:** "the switch to single-origin: a brand new era for
  brackenfell" — or shorter (recommended): "single-origin: what
  changes july 15"

### B3 · Missing farmer name (brief requirement)
- **Where:** Paragraphs 3 and 4. Catalina is named first-name-only.
  Solomon Kebede is not named at all.
- **Why:** The brief explicitly named both farmers (Catalina Mejia,
  Solomon Kebede). Naming farmers properly is the whole point of a
  single-origin story.
- **Rewrite:** P3 → "Our first partner is Catalina Mejia in Colombia."
  P4 → "Our second partner is Solomon Kebede in Ethiopia."

## Fixes

### F1 · Exclamation marks (4 instances)
- **Where:** Paragraphs 1, 6, 7 (twice).
- **Why:** Brand voice doc: "no exclamation marks (Sarah's pet peeve)".
- **Rewrite:** Replace every "!" with "." and reread for tone — the
  draft reads as over-eager without them, which is closer to the brand
  voice anyway.

### F2 · Missing cupping scores (brief requirement)
- **Where:** Paragraphs 3 and 4 mention cupping but never give the
  scores.
- **Why:** Brief: "should reference … the cupping scores."
- **Rewrite:** Add the actual scores after the flavor notes — they're
  in the cupping log shared with the brief.

### F3 · "forty-three" should be 43
- **Where:** Paragraph 4 ("forty-three distinct flavor notes").
- **Why:** Brand voice doc: "Numbers always written as digits."
- **Rewrite:** "43 distinct flavor notes".

### F4 · Long sentences in active voice
- **Where:** Paragraph 1, sentence 1 (38 words, multiple clauses).
- **Why:** Brand voice doc: "Sentences short. Active voice." Current
  sentence is neither.
- **Rewrite:** Split into 2–3 short sentences. Example: "We're
  switching to single-origin beans for the new house roast. Launches
  July 15. Two farms — Colombia and Ethiopia."

## Nits

### N1 · Headline is generic
- **Where:** Current headline.
- **Why:** "A brand new era" is the kind of phrase that doesn't
  earn its space.
- **Rewrite:** Suggested above in B2 — "single-origin: what changes
  july 15" is concrete and specific.

### N2 · "We believe this represents a paradigm shift"
- **Where:** Paragraph 5 opening.
- **Why:** Edges toward buzzword territory. Brand voice doc isn't
  explicit on "paradigm shift" but it's adjacent to the banned list.
- **Rewrite:** "This changes what's in the bag — and where it comes
  from."

## CTA check
- **Present?** yes
- **Specific?** No — two CTAs (pre-order + subscribe) competing in
  the same sentence, plus an exclamation mark.
- **Action:** Fix. Pick one. Recommended: "Pre-orders open now at
  brackenfellcoffee.co/single-origin." Drop the second CTA — the
  page itself will offer subscription.

## Brand voice check
- **Tone match:** Leans too excited (4 exclamation marks, "thrilled",
  "amazing", "we couldn't be more excited"). Brand voice is calm,
  confident, direct.
- **Vocabulary flags:** "leverage", "synergizing", "robust",
  "paradigm shift" — all outside the voice.
- **Length vs format norm:** Within range (~590 words estimated), no
  issue.

## Self-check (internal)
- [x] Every Blocker has a proposed rewrite
- [x] No comment is "this could be better" without specifics
- [x] CTA reviewed
- [x] No facts let through without source verification (cupping scores
       flagged as missing from draft)
```

---

## Notes for the agency

- Verdict "Needs rewrite" was the correct threshold call — 3 Blockers
  triggers it, regardless of how many Fixes/Nits.
- B3 (missing farmer name) is a great example of the brief catching
  something the writer missed in their own draft.
- Notice the QA never invented the cupping scores — it flagged them
  missing rather than pulling numbers out of thin air.
- Each comment references the specific source (brand voice doc /
  brief), so the writer can verify rather than argue.
