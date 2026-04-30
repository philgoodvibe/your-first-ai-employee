# Mission 2 — The Launch Kit

> **For [EMPLOYEE NAME]:** Mission 1 must be complete and locked before starting this. Reference `01-strategy/` and `context-folder/` throughout.

## The mission

Build the complete go-to-market kit for the niche [OWNER NAME] picked in Mission 1. Everything in [OWNER NAME]'s voice. Ready to ship.

## Why this matters

A locked positioning brief is worthless without the assets to take it to market. Your job is to produce real, ready-to-use launch artifacts so [OWNER NAME] can stop strategizing and start selling.

## Definition of done

A folder named `02-launch-kit/` in our working directory containing:

1. **`landing-page/index.html`** — a single-file HTML landing page that:
   - Opens in a browser without dependencies
   - Mobile-responsive
   - Headline + sub-headline that match the positioning brief
   - 3-section structure (problem, solution, proof, CTA)
   - One primary CTA above the fold
   - Email capture form (form action can be a placeholder; we'll wire it up later)
   - Brand voice from `context-folder/10-brand-voice/`

2. **`lead-magnet-1.md`** — a 5–7 page lead magnet (markdown, PDF-ready) on a topic the ICP urgently wants. Title compelling. Useful even without buying anything from us. Calls back to our positioning at the end.

3. **`lead-magnet-2.md`** — a second lead magnet at a different awareness level. If lead-magnet-1 was for problem-aware, make this one for solution-aware. Or vice versa.

4. **`email-sequence/`** — folder with:
   - `email-1-welcome.md` — sent immediately after opt-in
   - `email-2-credibility.md` — sent day 1
   - `email-3-pain-amplification.md` — sent day 2
   - `email-4-solution-tease.md` — sent day 4
   - `email-5-soft-pitch.md` — sent day 6
   - `email-6-objection-handling.md` — sent day 8
   - `email-7-direct-pitch.md` — sent day 10

   Each email: subject line, preview text, body, single CTA.

5. **`social-plan-8-weeks.md`** — an 8-week (~2 month) social media plan with:
   - Week-by-week themes (8 themes)
   - 3 posts per week (24 posts total)
   - For each post: platform recommendation, format (text / image / carousel / video), full copy, hashtag suggestions
   - One pillar post per week (longer-form thought piece)
   - One CTA post per week (driving to lead magnet or landing page)

## How to work

- Spawn the **Designer** sub-agent for the landing page. Spawn the **Copywriter** sub-agent for emails, lead magnets, and social copy. Spawn the **Editor** sub-agent for a final pass before declaring done.
- Reference `context-folder/40-past-content/` for voice. If a draft sounds like AI, send it back to the Copywriter for a rewrite.
- For the landing page, use a clean, modern, mobile-first design. Keep CSS inline so the file is fully self-contained.

## When in doubt

Ask. Especially for: brand colors, font preferences, primary CTA destination, and email-sequence timing.

---

*Brief authored: [DATE]. Mission status: not started → in progress → review → locked.*
