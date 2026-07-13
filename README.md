# Principles Forge

**A method for growing your own set of principles — for any field — using Claude, from real examples instead of vibes.**

Most "principles" you find online are one person's taste, stated with confidence. This kit builds principles the other way: you feed Claude real *exemplars* of strong work, it extracts the concrete specifics, and a rule only earns "principle" status after the same pattern shows up across **multiple separate sessions**. Nothing gets promoted on a single lucky example, and nothing that isn't measured gets stated as fact.

It runs in **Claude Code**. You bring the examples — paste them in, or just hand over **URLs** and Claude fetches and probes them itself (page content via web fetch; for visual fields like web design, computed fonts/colors/layout via the `chrome-devtools` MCP, exactly like an award-site design sweep). You supply the taste in *what* counts as a good example; Claude does the measuring.

---

## How it works: three layers

```
raw/sweeps/     immutable evidence   →  every session's exact specifics, dated, never edited
   ↓ (a pattern across ≥2 exemplars)
trends/now.md   perishable reading   →  "what strong work is doing right now" — rewritten each session
   ↓ (holds across 2+ sessions, you approve it)
principles/     durable rules        →  the earned principles you actually consult
```

Every claim carries a **confidence tag** (`[high]` / `[medium]` / `[low]`) and points either to the exemplar it came from or to `[prior-knowledge]` (received wisdom, honestly labeled). Outdated claims are **superseded, never deleted**, so the vault keeps its own history.

That two-stage ladder — evidence → trend → principle — is the whole trick. It's why the principles you end up with are ones you've *watched* hold up, not ones you hoped were true.

---

## Use it in 3 steps

1. **Open the scaffold in Claude Code.** Drop this folder into a project (or clone it) and open it. For visual fields (web design and the like) also install the `chrome-devtools` MCP so Claude can probe live pages; text fields need nothing extra.
2. **Run `/start`.** This is the only thing a first-timer needs. It explains what the kit is in plain language, then walks you the whole way — a few friendly setup questions, gathering your first examples, and producing your first draft of rules — no jargon, about 10–15 minutes.
3. **Run `/generate` for every round after that.** Whenever you've collected a few more examples (pasted, or just links it fetches and probes for you), it studies them, updates what's working, and graduates patterns into trusted rules once they've held up across rounds.

> Under the hood, `/start` runs `/setup` (one-time configuration) then your first `/generate`. Power users can call those two directly and skip the guided intro.

Do real work in your field? Read your `principles/` pages first, then skim `trends/now.md` for the current flavor.

**Cadence:** `/generate` is the whole maintenance ritual. Run it before a big project, or roughly monthly when you've collected a fresh batch. It tolerates long gaps by design — there's no daily upkeep and nothing rots if you skip a month.

---

## What one principle looks like (worked example: cold-email copywriting)

After a couple of `/generate` sessions, a `principles/openers.md` page might hold:

```markdown
## Principles

1. **Name a specific, observable detail about them in the first line.** Generic
   flattery ("love what you're building") reads as a mail-merge; a concrete
   observation earns the next sentence. `[high — 2 sessions, confirmed 2026-08:
   4/5 replied-to examples opened with a named detail]`
2. **Get to the ask within 3 sentences.** Every measured high-reply example
   stated its one ask by sentence 3; the low-reply pile averaged 6.
   `[medium — 1 session]` ← [[2026-08-14 — reply-rate batch]]
```

Notice: each rule is an **imperative you can act on**, backed by a **count from named examples**, tagged with **how sure we are**. That's the output shape for any field — swap "openers" for "slide anatomy," "plating," "step clarity," whatever your dimensions are.

---

## Layout

```
CLAUDE.md                  the operating manual + persona + the 9 hard rules
.claude/skills/setup/      the one-time configuration wizard  (/setup)
.claude/skills/generate/   the recurring distill session      (/generate)
principles/_TEMPLATE.md     the anatomy of a principle page
trends/now.md               perishable current reading (starts empty)
raw/sweeps/                 immutable dated evidence lands here
sources.md · index.md · log.md   registry · hub · append-only ledger
```

Git is **optional** — commit if you like a history, or just keep it as a plain folder.

---

*Adapted from a live web-design principles vault. The field-specific parts (galleries, browser probing, typographic dimensions) were stripped out; what remains is the portable method: measured exemplars, a confidence ladder, and human-approved promotion.*
