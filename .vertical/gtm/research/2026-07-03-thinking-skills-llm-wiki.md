# Research: Clear-Thinking Skills + Karpathy's Knowledge System

Researched 2026-07-03 (Opus web-research agent). Two questions for the build-in-public
writing agent: (1) does a "clear-thinking / aha-extraction" skill already exist,
(2) what exactly is Karpathy's local LLM wiki. Companion to
`2026-07-03-writing-agent-landscape.md`.

---

## QUESTION 1 — Existing "clear-thinking / aha-extraction" skills

### Garry Tan's gstack `/office-hours` (the strongest match)

Closest published thing to an aha-extraction interview skill: a Socratic diagnostic that writes a design doc — no code. Source: [office-hours/SKILL.md](https://github.com/garrytan/gstack/blob/main/office-hours/SKILL.md).

Two modes: **Startup Mode** (hard diagnostic pushback) and **Builder Mode** (generative "find the coolest version" brainstorming).

The **six forcing questions** (Startup Mode), asked sequentially with smart-skip routing:
1. **Demand Reality** — strongest evidence someone actually wants this (behavior, not interest)
2. **Status Quo** — what users do right now, even badly; what the workaround costs
3. **Desperate Specificity** — name the actual human; title; what gets them promoted/fired
4. **Narrowest Wedge** — smallest version someone would pay for this week
5. **Observation & Surprise** — watched someone use it without helping? what surprised you?
6. **Future-Fit** — in 3 years, more essential or less?

**Socratic mechanics (the transferable part):** *Push twice* ("first answer is polished; the real answer emerges after the second or third push"); *Force specificity* (replace categories with names/consequences); *Take positions* (state what's wrong + what evidence would change your mind); *Challenge the strongest version* (steelman, not strawman). Flow: Context → Mode Select → Diagnostic Questions → Premise Challenge → Alternatives (min 2) → Design Doc.

**Other gstack thinking skills** ([docs/skills.md](https://github.com/garrytan/gstack/blob/main/docs/skills.md)):
- **`/spec`** — vague intent → executable spec in five phases.
- **`/plan-ceo-review`** — founder-mode reframing: "What is this product actually for?", hunts "the 10-star product hiding inside this request"; opportunities surfaced *one at a time* for cherry-picking; "premise challenge" = falsifiable claims for the user to validate.
- **`/plan-design-review`** — rates each dimension 0–10 and explains "what a 10 looks like," then edits toward it. Directly reusable as a writing eval rubric pattern.

All persist decisions to `~/.gstack/projects/` for cross-session continuity.

### Jesse Vincent (obra) Superpowers — `brainstorming` skill

Repo: [obra/superpowers](https://github.com/obra/superpowers), skill: [skills/brainstorming](https://github.com/obra/superpowers/tree/main/skills/brainstorming). Mechanics:
- **One question at a time**, multiple-choice preferred, only one clarifying question per message (explicit anti-overwhelm rule).
- Nine-step flow: explore context → clarifying questions → propose 2–3 approaches with trade-offs + recommendation → present design in sections, approval per section → write design doc → **self-review spec for placeholders/contradictions/ambiguity** → user review → transition.
- "Incremental validation": approval before moving on. Output is a spec, never code.

The section-by-section approval + self-review-for-contradictions loop is worth copying.

### Matt Pocock's `teach` skill — Socratic, but teaching-oriented

[mattpocock/skills](https://github.com/mattpocock/skills), teach at [productivity/teach/SKILL.md](https://github.com/mattpocock/skills/blob/main/skills/productivity/teach/SKILL.md). Socratic but aimed at *teaching you*, not extracting *your* insight. Mechanics: establishes the "mission" by interrogating *why* you want to learn; assesses "zone of proximal development" from a `learning-records/` dir; alternates Knowledge and Skills-practice phases with the tightest-possible feedback loop. Pocock's broader relevant idea is "**grilling**" — getting the agent to interview you Socratically, one decision at a time, proposing a recommended answer for each.

### Every / Spiral "collaborative interview" — thin on primary detail

Spiral runs a collaborative interview before generating ([third-party review](https://www.funblocks.net/aitools/reviews/spiral-12)), but **no primary-source breakdown of the actual questions exists**. Known to exist, mechanics undisclosed.

### Naval Ravikant — no skill, only a philosophy others prompt-ify

Naval publishes no skills. Relevant idea: aphorisms/tweets as *compression* — "pointers, addresses, or mnemonics" for learnings ([Sloww](https://www.sloww.co/naval-ravikant/), [Founders podcast](https://podscripts.co/podcasts/founders/191-naval-ravikant-a-guide-to-wealth-and-happiness)). Third-party prompt packs exist but are career prompts, not idea-compression skills. **No published "turn-my-rambling-into-an-aphorism" skill found — a gap worth filling.** Transferable principle: aphorism = lossy compression optimized for recall, so an aha compressor should optimize for memorability/pointer-value, not completeness.

### Landscape summary

Recurring copyable pattern across all of the above: **sequential single questions, push-past-the-first-answer, force specificity/names, propose a default answer per question, emit a durable doc as the deliverable.** No widely-adopted standalone "insight miner / aha extractor" SKILL.md exists — the niche is unfilled.

---

## QUESTION 2 — Karpathy's knowledge system & LLM wiki

### The append-and-review note (mid-2025, primary source)

[karpathy.bearblog.dev/the-append-and-review-note](https://karpathy.bearblog.dev/the-append-and-review-note/) ([HN thread](https://news.ycombinator.com/item?id=44658745)):
- **One** single text note in Apple Notes ("more notes + folders = too much cognitive bloat").
- **Append**: any idea/todo appended on top, plain text; only structure is functional tags (`watch:`, `listen:`, `read:`).
- **Review**: periodically skim downward; "rescue" still-relevant items back to the top by copy-paste, merging related entries.
- **Gravity effect**: unimportant items "naturally continue to sink. They are never lost, they just don't deserve the top of mind." Deletion rare. Single note = trivial Ctrl-F.
- No LLM involvement — purely manual. (Spawned Obsidian clones, e.g. the [Jot plugin](https://forum.obsidian.md/t/introducing-jot-a-card-style-note-taking-plugin-for-obsidian-inspired-by-andrej-karpathy-s-append-and-review-note/112912).)

### The LLM Wiki (April 2026 — the blueprint)

Primary source: [Karpathy's llm-wiki gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f). Persistent, compounding markdown knowledge base an agent maintains — explicitly beyond RAG: "the LLM **incrementally builds and maintains a persistent wiki** … The knowledge is compiled once and then *kept current*, not re-derived on every query."

**Three-layer architecture:**
- **`raw/`** — curated source docs. Immutable: "the LLM reads from them but never modifies them."
- **`wiki/`** — LLM-generated markdown: summaries, entity pages, concept pages, comparisons, overview, synthesis. "The LLM owns this layer entirely."
- **Schema** — a `CLAUDE.md`/`AGENTS.md` describing structure, conventions, workflows.

**Three operations:**
- **Ingest** — read source, discuss key takeaways with you, write summary page, update index, update relevant entity/concept pages across the wiki, append to log.
- **Query** — search relevant pages, read, synthesize with citations.
- **Lint** — periodic health check: "contradictions between pages, stale claims that newer sources have superseded, orphan pages with no inbound links."

**Supporting files:** `index.md` (categorized catalog with one-line summaries, updated every ingest) and `log.md` (append-only chronological record with consistent grep-able prefixes). Why markdown: models are trained on huge amounts of it. Karpathy reports ~100 articles / ~400k words staying navigable via index + summaries, beating RAG for his research use ([corroboration](https://levelup.gitconnected.com/beyond-rag-how-andrej-karpathys-llm-wiki-pattern-builds-knowledge-that-actually-compounds-31a08528665e)).

Convergence: the LLM Wiki's append-only `log.md` + curated `index.md` is the append-and-review note **automated by an agent** — capture stays append-only; the agent does the "rescue to top" via index/entity-page updates.

### Others running agent-maintained local markdown wikis

1. **Stefan Imhoff — "Agentic Note-Taking: Obsidian + Claude Code"** ([post](https://www.stefanimhoff.de/writing/agentic-note-taking-obsidian-claude-code/)): Fleeting Notes in Zettelkasten `YYYYMMDDHHmm.md`; three-tier maturation Fleeting → Literature → Permanent; reorganized **6,000 notes** with Claude into hybrid Zettelkasten + PARA; `qmd` command for fast vault search; Claude auto-generates backlinks; `CLAUDE.md` captures vault structure. Planned: agent pattern-mining across all notes.
2. **AgriciDaniel/claude-obsidian** ([repo](https://github.com/AgriciDaniel/claude-obsidian)) — "Self-organizing AI second brain … Based on Karpathy's LLM Wiki pattern." 15 Claude Code skills, LYT/PARA/Zettelkasten modes, plain markdown.
3. **ballred/obsidian-claude-pkm** ([repo](https://github.com/ballred/obsidian-claude-pkm)) — atomic one-idea-per-note Zettelkasten, agent-maintained; **lucasrosati/claude-code-memory-setup** ([repo](https://github.com/lucasrosati/claude-code-memory-setup)) — Obsidian + graph layer as persistent Claude Code memory.

Voice-notes → inbox → periodic agent distillation: the *shape* exists everywhere, but no polished end-to-end primary write-up. Partial gap.

---

## Synthesis — what to copy

**(a) Aha-extraction interview skill.** Borrow `/office-hours`' spine, retargeted from "does this product have demand" to "what's the real insight here":
- Sequential single questions, propose a default answer each time (Superpowers + Pocock's grilling). Never dump a question list.
- **Push twice** — the aha is usually in the second/third answer.
- **Force specificity / de-abstract** — replace categories with a specific moment, person, number, before/after. Single most transferable mechanic.
- **Premise challenge + steelman** — restate the strongest version back: "is *that* what you mean?"
- **Compress last (Naval)** — end with a lossy compression pass: one aphorism/pointer sentence, optimized for memorability not completeness.
- **Emit a durable artifact** — an "insight card," not chat.

**(b) Local capture-everything wiki feeding writing evals.** Adopt Karpathy's LLM Wiki structure: `raw/` (immutable — voice notes, transcripts, drafts, fragments), agent-owned `wiki/` (phrase bank, recurring-theme pages, exemplar pages, aha cards), schema doc. Wire in:
- Append-only `log.md` as the capture inbox; agent promotes entries into evergreen pages during **ingest** (read → discuss takeaways → write → update index → log).
- `index.md` as the curated top-of-mind catalog.
- **Lint as the eval hook**: contradictions, stale claims, orphan pages — extended for writing (voice drift, overused phrases, unsupported claims). Voice/style evals (EQ-Bench metrics, edit-diff mining) run against the same `wiki/` exemplar pages, so knowledge base and evals share one source of truth.
