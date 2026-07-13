# Principles Forge

**Build your own rulebook for any craft — with Claude Code — from real examples instead of opinions.**

Show Claude great examples of work in a field you care about. It studies exactly what they do, finds the patterns that keep showing up, and turns the ones that prove themselves into a short list of rules you can actually trust. Nothing becomes a "rule" on a single lucky example, and nothing that isn't grounded in a real example gets stated as fact.

Works for anything — cold email, pitch decks, web design, recipes, negotiation, UI, technical writing. You pick the field.

---

## Get started (5 minutes to your first rules)

**1. Get the kit**

```bash
git clone https://github.com/amk16/principles-forge.git
```

Or download the ZIP (green **Code** button → *Download ZIP*) and unzip it.

**2. Open the folder in Claude Code**

```bash
cd principles-forge
claude
```

**3. Type `/start`**

That's the whole thing. `/start` explains what this is in plain language, then walks you the rest of the way:

- asks a few friendly questions to set up your field,
- helps you gather your first 4–6 examples (paste them, or just give links — Claude fetches them for you),
- studies them and writes up what it found.

About 10–15 minutes, no jargon, no technical steps.

**4. That's your first draft.** Your rules live in the `principles/` folder, in plain markdown you can read and edit.

**5. Come back anytime** with more examples and type `/generate`. Each round makes your rulebook sharper — and rules only "graduate" once they've held up across multiple rounds.

---

## The three commands

| Command | When | What it does |
|---|---|---|
| `/start` | **Once**, the first time | Introduces the kit and walks you to your first output. Start here. |
| `/generate` | **Every round after** | Takes new examples, updates what's working, promotes proven patterns into rules. |
| *(just read* `principles/`*)* | When you're doing real work | Your trusted rulebook, ready to consult. |

---

## Requirements

- **Claude Code** — that's it for most fields.
- **Optional:** the `chrome-devtools` MCP, only if your field is **visual** (web design, landing pages) and you want Claude to measure live pages — real fonts, colors, and layout. Text fields (copy, decks, writing) don't need it. `/start` tells you if yours does.

---

## How it works (the idea in 30 seconds)

Everything flows up through three layers, and a claim has to earn each step:

```
  You show examples
        │
        ▼
  raw/          the receipts — exact specifics pulled from each example, dated, never edited
        │  (a pattern shows up across 2+ examples)
        ▼
  trends/       "what's working right now" — the current reading, rewritten each round
        │  (the pattern holds up across 2+ rounds, and you approve it)
        ▼
  principles/   your trusted rulebook — the rules you actually use
```

Every rule is tagged with **how sure we are** (`high` / `medium` / `low`) and **where it came from** (which examples, or honestly labeled as received wisdom). Old rules get **crossed out with a note**, never silently deleted — so your rulebook keeps its own history.

That waiting period — a pattern has to prove itself twice before it's a rule — is the whole point. You end up with rules you've *watched* hold up, not ones someone hoped were true.

---

## What a finished rule looks like

Example from a cold-email rulebook, after a couple of rounds:

```markdown
1. **Open with one specific, observable detail about the person.** Generic
   flattery ("love what you're building") reads as a mass-mail; a concrete
   observation earns the next sentence. `[high — 2 rounds, 4/5 replied-to
   examples opened with a named detail]`
```

Notice the shape: a **plain instruction you can act on**, backed by a **count from real examples**, tagged with **how confident we are**. Same shape for any field — swap "openers" for "slide layout," "plating," "step clarity," whatever fits your craft.

---

## What's in the folder

```
CLAUDE.md                 the operating manual (persona + the rules of the method)
.claude/skills/
  start/                  /start    — the guided first run (start here)
  setup/                  /setup    — one-time field configuration
  generate/               /generate — the recurring round that grows your rules
principles/               your rulebook (starts empty; _TEMPLATE.md shows the shape)
trends/now.md             "what's working right now" (starts empty)
raw/sweeps/               the dated receipts land here
sources.md                where you find good examples
index.md · log.md         the hub · a running history
```

Git is **optional** — keep a history if you like, or just use it as a plain folder.

---

*Adapted from a live web-design principles vault. The web-specific parts were stripped out; what remains is the portable method — real examples, a confidence ladder, and rules that have to earn their place.*
