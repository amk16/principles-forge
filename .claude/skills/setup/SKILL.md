---
name: setup
description: One-time wizard that turns this empty scaffold into a working principles vault for YOUR field. Asks what domain you want principles for, co-defines the persona, the dimensions, the measurement schema, and the exemplar sources, then fills CLAUDE.md and seeds every file. Run this once, before /generate.
---

# /setup — configure this vault for your field

This scaffold ships empty and domain-neutral. This wizard co-defines, with the owner, the few things that are field-specific, then writes them into `CLAUDE.md` and the seed files. **Ask one question at a time, wait for the answer, then move on.** Lead with a recommendation when you offer choices.

## Step 0 — Check state

Read `CLAUDE.md`. If the `<< >>` placeholders are already filled (the vault is configured), say so and ask whether the owner wants to reconfigure (overwrites `CLAUDE.md` persona/dimensions/schema; leaves existing `principles/`, `trends/`, `raw/` untouched) or exit. Otherwise continue.

## Step 1 — Domain

Ask: **"What field do you want to build principles for?"** Examples to prompt them: cold-email copywriting, pitch-deck design, technical writing, product onboarding, standup comedy sets, recipe development, negotiation, UI design. Get one clear noun phrase. This becomes `<<DOMAIN>>` everywhere.

## Step 2 — Persona

Propose a persona title in the shape *"an evidence-bound `<<DOMAIN>>` director"* and a one-line voice (direct, specific, cites the exemplar). Offer 2–3 title options, recommend one, let the owner rename. Capture their name/handle as `<<OWNER>>` (ask if unknown). This fills the top of `CLAUDE.md`.

## Step 3 — Dimensions

Explain: principles are organized by **dimension** — the 4–8 orthogonal axes along which quality in this field varies. For web design these were typography, color, layout, components, story-flow, motion, copy. Propose a starter set of 4–8 dimensions for *their* field, recommend it, and refine together. Keep them orthogonal and each nameable in one word or short phrase.

For each agreed dimension, create `principles/<dimension-slug>.md` by copying `principles/_TEMPLATE.md` and filling only the frontmatter + H1 + an empty Provenance callout (`> [!info] Provenance` \ `> Received canon `[prior-knowledge]` — no evidence yet.`). Leave the principles list empty; `/generate` and the owner fill it over time. This becomes `<<DIMENSIONS>>`.

## Step 4 — Measurement schema (the crux)

This is what makes the vault evidence-bound rather than vibes. In web design, every exemplar was probed for *exact* attributes: typeface name, measured px size, line-height, hex colors, runtime libraries. For **their** field, co-define the analogous checklist: **the concrete, quotable, countable things to pull from every exemplar** so a claim reads "exemplar X did exactly this" not "this feels strong."

Guide them with the test: *could two people extract the same value from the same exemplar and agree?* If yes, it belongs in the schema. Examples by field:
- Cold email → subject line verbatim + word count; opening-line hook type; # of sentences before the ask; the exact CTA phrasing; personalization tokens used.
- Pitch deck → slide count; words-per-slide; the one-sentence ask verbatim; where the metric slide sits; chart type per data slide.
- Recipe writing → ingredient count; step count; sensory cue phrasing; technique named per step; yield/time stated up front or not.
- Web / landing-page design → typeface names + measured px sizes + line-heights; ground and accent colors (computed hex/rgb); nav link count; runtime libs (GSAP/Lenis/Three).

**Tag each attribute by how `/generate` gets it from a URL exemplar:**
- `(content)` — readable from fetched page text or pasted content (wording, counts, structure). `WebFetch` handles it.
- `(rendered)` — needs a **real browser** (computed fonts, colors, sizes, layout, motion, runtime globals). `/generate` probes these via the `chrome-devtools` MCP, exactly like a design sweep.

If any attribute is `(rendered)`, tell the owner the vault needs the **chrome-devtools MCP** installed in Claude Code for URL exemplars in this domain (pasted screenshots still work without it). Purely `(content)` domains need no MCP — just `WebFetch`.

Write the agreed, tagged checklist into the `## Measurement schema` section of `CLAUDE.md` as `<<MEASUREMENT_SCHEMA>>`. This same checklist becomes the extraction template `/generate` runs against each exemplar.

## Step 5 — Sources

Ask where the owner encounters strong exemplars in this field (newsletters, swipe files, specific accounts, books, galleries, publications, a folder of saved examples). Seed `sources.md`'s **Active** table with these. Note which are **browsable** — a gallery or site `/generate` can survey with `WebSearch`/`WebFetch` to pull fresh exemplars on request (like award galleries in a design sweep) — versus offline wells the owner draws from by hand. It's fine to start with 2–3; exemplars can also be pasted or linked ad hoc without being a registered source.

## Step 6 — Wire it up

- Fill every `<< >>` slot in `CLAUDE.md` (persona, owner, domain, dimensions list, measurement schema).
- Update `index.md`: replace the placeholder domain language, list the dimension wikilinks in the Map and the "do real work" order, set State → `Sessions run: 0`.
- Append a `log.md` entry: vault configured for `<<DOMAIN>>`, N dimensions, schema defined.
- **Offer** (don't force) `git init && git add -A && git commit -m "Configure vault for <<DOMAIN>>"`. If the owner declines or git is unavailable, continue — the vault works as a plain folder.

## Step 7 — Hand off

Tell the owner setup is done and what to do next: *"Collect 4–6 strong exemplars in <<DOMAIN>>, then run `/generate` and paste them in. After two sessions, patterns that recur will become principle promotion candidates."* Keep it short.
