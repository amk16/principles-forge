---
name: generate
description: The recurring distill session — the engine of the vault. Loads prior state, takes 4–6 exemplars (pasted content OR URLs, which it fetches/probes itself), pulls the measurement-schema specifics from each, writes one immutable dated evidence file, updates trends/now.md on the confidence ladder, and proposes principle promotions. Runs in Claude Code (uses WebSearch/WebFetch and, for rendered detail, the chrome-devtools MCP). Run before a big project or whenever you've gathered a fresh batch of exemplars.
---

# /generate — distill a fresh batch of exemplars

You are the vault's persona (see `CLAUDE.md`). This skill refreshes the vault's understanding from **exemplars the owner brings you**. Everything you write must be specific, cited to a named exemplar, and confidence-tagged. Runs in **Claude Code**: when an exemplar is a URL, you fetch and probe it yourself rather than asking the owner to paste it.

## Step 0 — Load prior state

Read, in order: `CLAUDE.md` · `sources.md` · `trends/now.md` · the **two most recent** files in `raw/sweeps/` (if any).

**If `CLAUDE.md` still has unfilled `<< >>` placeholders**, the vault is unconfigured — stop and run `/setup` first, then return here.

## Step 1 — Gather exemplars

Ask the owner for **4–6 exemplars** of strong (or instructively weak) work in the domain. Each can be:
- **Pasted content** — text, or a screenshot you can read.
- **A URL / website** — you fetch and probe it yourself (Step 2b); the owner just hands you the link.
- **"Find some for me"** — if the owner points you at a named source in `sources.md` (a gallery, a publication, a feed) and asks you to pull fresh exemplars, use `WebSearch`/`WebFetch` to survey it and pick a diverse set, the way a design sweep surveys galleries.

For each, capture a short name/slug and where it came from (for `sources.md`). Fewer than 4 is fine for a thin session — note it in caveats.

## Step 2 — Extract per exemplar

Run the **measurement schema** from `CLAUDE.md` against each exemplar. Pull the exact, quotable, countable values it names — quote wording verbatim, count what it counts, name concrete choices. Never eyeball or guess; if an attribute genuinely isn't determinable, mark it `n/a` rather than inventing it.

### Step 2a — pasted content
Read the schema attributes straight off the pasted text/screenshot.

### Step 2b — URL / website exemplars
Get the page yourself, then extract:
- **`(content)` attributes** (wording, structure, counts, copy) → `WebFetch` the URL and read them from the returned content.
- **`(rendered)` attributes** (computed fonts, colors, sizes, layout, motion, runtime libraries) → probe in a **real browser via the `chrome-devtools` MCP**, mirroring a design sweep:
  1. Open a page; set viewport **1440×900** (`resize_page`) for run-over-run comparability.
  2. Navigate to the URL (read-only — never log in or submit forms); take a hero screenshot.
  3. Run a computed-style probe via `evaluate_script` for exactly the `(rendered)` attributes the schema names (e.g. `getComputedStyle` on the relevant selectors; `document.fonts`; `window.gsap`/`THREE`/canvas census). Quote measured values, never guessed ones. **Probe robustly:** match text values (prices, counts, phrases) against container-level `innerText`, never leaf nodes only — modern frameworks split "$24 / per month" across child spans, and a leaf-only query reports the value missing. Likewise, checking the served HTML for a value can miss it when it lives in a hydration JSON payload (Next.js props) rather than markup — the rendered DOM is the source of truth for `(rendered)` attributes.
  4. Scroll and re-screenshot if the schema cares about anything below the fold.
- If the domain's schema has **no `(rendered)` attributes**, `WebFetch` alone is enough — no browser needed. If a `(rendered)` attribute is required but the `chrome-devtools` MCP isn't available, mark it `n/a (needs chrome-devtools MCP)` and note it in caveats rather than guessing.

## Step 3 — Write the evidence file (immutable)

Create `raw/sweeps/YYYY-MM-DD — <slug>.md` with frontmatter (`type: sweep`), structured as: exemplars table (name / source / date) → per-exemplar dossier (the schema attributes, filled) → a **cross-exemplar tallies table** (which attributes recurred, and in how many of N) → session notes + caveats. **Never edit an older evidence file** — a new session is always a new dated file.

## Step 4 — Update `trends/now.md`

Diff this session's tallies against the current reading, entry by entry:
- **Confirmed again** → bump confidence (`[medium — 1 session]` → `[high — N sessions]`), append the new session wikilink.
- **Absent this session** → keep but downgrade; absent 2 consecutive sessions → `~~strike~~ [SUPERSEDED <date>]`.
- **New pattern (≥2 named exemplars this session)** → add as `[medium — 1 session]`.
- Refresh the Provenance callout and the Watchlist (promotion candidates for next session).

## Step 5 — Propose promotions & retirements

Patterns holding across **2+ sessions** → list as promotion candidates for the relevant `principles/` page, **with proposed wording** in the vault's principle style (bold imperative rule + explanation + inline confidence/provenance tag). Principles contradicted by 2+ sessions → retirement/revision candidates. **Propose only — do not edit `principles/` without the owner's approval in-session.** On approval, apply with provenance wikilinks and supersede notation.

## Step 6 — Housekeeping

Update `sources.md` (add any new sources these exemplars came from) · update the State block in `index.md` (session count, pending candidates) · append a `log.md` entry · if the vault is a git repo, `git add -A && git commit` with a short session summary (skip silently if not a repo).

## Step 7 — Report

In chat, lead with what changed: new trends, confirmations, deaths, promotion proposals awaiting the owner's call, and any thin spots. Short, cited to exemplars, no file dumps.

## Rules

- **Never modify `raw/`** — new evidence is a new dated file.
- Extract only what's actually present in the exemplar; quote specifics, never guess. For `(rendered)` attributes use **computed values from a real browser**, never eyeballed fonts or colors.
- **Read-only browsing**: fetch and probe pages, but never log in, submit forms, or accept anything beyond cookie banners.
- Every claim cites the exemplar + session date; wikilinks, not paths, in note prose.
- One session = one dated evidence file + one `log.md` entry, always, even if findings are thin.
- Trends are perishable and principles are durable — never let a single-session pattern be written as a principle.
