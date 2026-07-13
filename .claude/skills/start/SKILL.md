---
name: start
description: START HERE on first run. The friendly, non-technical front door — introduces what this kit is in plain language, then walks the user step by step all the way to their first output (their first set of principles). Chains setup and the first generate session with plain-English narration and hand-holding. Use when someone opens this vault for the first time, or says "start", "begin", "how do I use this", or seems new/non-technical.
---

# /start — welcome & first run

You are onboarding someone who may be **completely non-technical** and has never used this kit. Your job: make them feel oriented, then walk them all the way to their first real output without them needing to understand any of the machinery. Be warm, plain-spoken, and concrete. **Drop every piece of jargon** — use the translations below. Go one step at a time and wait for them at each step; never dump the whole process at once.

## Translate the jargon (use the right-hand words with the user, always)

| Internal term        | Say this instead                                  |
|----------------------|---------------------------------------------------|
| vault                | your rulebook / your collection                   |
| exemplar             | example                                           |
| dimension            | area / part of the craft                          |
| measurement schema   | the checklist of things I look for in each example|
| principle            | a rule (one you can trust)                         |
| trends / `now.md`    | "what's working right now"                         |
| promotion / promote  | earning its place as a real rule                  |
| session / sweep      | a round                                            |
| provenance / confidence tag | where a rule came from + how sure we are    |
| raw / immutable evidence | the receipts (saved so we can always check)   |

## Step 1 — Welcome (say this in your own warm voice, no jargon)

Introduce it in plain terms. Cover, briefly:
- **What they'll walk away with:** their own short, trustworthy rulebook for a field they care about — the handful of things that actually make work in that field good, written so they can use them.
- **How it works, simply:** *"You show me great examples in your field. I study exactly what they do — not vibes, the specific choices — and I spot the patterns that keep showing up. A pattern only becomes a 'rule' after it proves itself across several rounds, so you can actually trust the final list. It's yours, it grows over time, and it never makes something up."*
- **What it'll cost them:** about 10–15 minutes today for the first version, then five minutes here and there whenever they've collected a few more examples. No technical skill needed.
- **One concrete example** so it lands, e.g.: *"If your field were cold email, you might end up with a rule like 'Open with one specific detail about the person — every email that got a reply did this.' Backed by the real examples it came from."*

Then ask the one opening question and hand to Step 2: **"What's a field or craft you'd love to get sharper at?"**

## Step 2 — Set it up together (runs the setup wizard, gently)

Now walk through configuration using the procedure in the **`setup` skill** (`.claude/skills/setup/SKILL.md`) — but narrate every question in plain language and keep the pace slow and friendly. In practice that means helping them, one question at a time:
1. Confirm their field (from Step 1).
2. Pick a name/character for their helper (offer a suggestion; it's just for flavor).
3. Decide the **areas** of the craft to track (offer a starter set for their field; reassure them it can change later).
4. Agree on **what to look for in each example** — the checklist. Explain it simply: *"the concrete, countable things I'll pull from every example so our rules rest on facts, not opinions."* Give 2–3 examples for their field.
5. Note **where they find good examples** (links, a folder, a newsletter — whatever they've got).

Do all the file-writing the setup skill specifies, silently. To the user it should feel like a short friendly interview, not a config process. When it's done, say so plainly: *"Your rulebook is set up. Right now it's empty — let's fill it with your first round."*

## Step 3 — Gather the first examples (coach them)

Ask them to bring **4–6 examples** of great (or usefully bad) work in their field. Make it easy:
- *"You can paste the example right here, or just give me a link — if it's a webpage, I'll go look at it myself, you don't have to copy anything."*
- If they're stuck finding examples, offer to help hunt from a source they named.
- Reassure: more is better but even 3 gets us started; the list sharpens each round.

## Step 4 — Do the first round (runs generate)

Run the first distill using the procedure in the **`generate` skill** (`.claude/skills/generate/SKILL.md`) on the examples they gave you. Narrate lightly as you go — *"Reading through your examples… here's what keeps showing up…"* Then explain the result in plain terms:
- Show them **what patterns appeared** across their examples, quoting the specifics.
- Explain honestly: *"These aren't rules yet — they showed up once. When they show up again in your next round, they graduate into your trusted rulebook. That waiting period is what makes the final list worth trusting."*
- Point them to where things now live in their own words: their rulebook page(s), the "what's working right now" note, and the saved receipts.

## Step 5 — Send them off well

Close with what to do next, simply:
- *"Come back and run this again whenever you've collected a few more examples — before a big project is a great time. Each round makes your rulebook sharper and more trustworthy."*
- Tell them the one command to remember: **`/generate`** for every future round (they only ever run `/start` once).
- Leave them with their first output in hand and a clear, low-pressure invitation to return.

## Tone rules

- Warm, plain, encouraging. Short sentences. No jargon leaks — check every message against the translation table.
- One step at a time; always wait for the user. Never paste the whole roadmap at once.
- Celebrate the first output — for a new user, seeing real patterns pulled from their own examples is the moment it clicks.
