# Article queue

## 00. Running gbrain ourselves: field notes (added 2026-07-05, experience-based)

**Reader takeaway:** what adopting a company brain actually costs today —
someone else's mental models, DIY integrations, credential overhead, running
your own ops — from someone who did it, not a review. Ends on the build-vs-buy
question every startup faces: focus on making your beer taste better; the
infrastructure can help with that or distract from it.

**Status:** raw material in notes/running-gbrain-field-notes.md (dictated,
several [?] spots need Micha's correction). Pairs with "Why is everyone
talking about gbrain?" — pull essay and friction essay.

## 0. The three axes of legibility (added 2026-07-04, from company-brain session)

**Reader takeaway:** a lens for seeing their own org's opacity. Companies are
opaque in three directions — up/down (hierarchy filters what leaders see),
sideways (silos hide signals between departments), and backward (time hides
why decisions were made; people leave, context leaves with them). A
machine-readable context layer opens all three at once: the CEO sees pressing
issues past the layers, the engineer reaches sales-call signals while
building, the day-one hire gets the three-months-of-coffee-chats knowledge
with sources. One promise, three directions.

**Status:** framing stored in notes/what-is-a-company-brain.md. Sequence:
after the tacit-alpha essay (this is its optimistic twin — alpha explains
why the layer matters competitively; legibility shows what it feels like
to have one).

**Seed:** notes/what-is-a-company-brain.md (three axes section).

First short articles. One idea each, very short, novel insight over coverage.
Each entry leads with the reader takeaway — what the reader knows or does
differently after reading. If an entry has no honest takeaway, it doesn't get
written. Draft with /write; long-form candidates can carry
`Style: derek-sivers`.

Reader: technical founders and builders using coding agents; AI-native
operators; the angels watching them.

## 1. That thing you keep half-building has a name

**Reader takeaway:** if you've hacked together a check-in bot, a notes wiki
for your agents, or a "RAG that grew" — you're not procrastinating on a side
project. You've hit a real missing layer that everyone hits, and it has a
name: a company brain. Stop treating yours as a weekend hack and start
treating it as infrastructure — because the version you rebuild every month
is the one your agents will depend on next year.

**Evidence:** three independent homebrews surfaced this week alone — a
defense CEO who tried three times and asked a consultancy to spec it, a team
where every person runs their own LLM wiki, a founders-chat RAG that "evolved
into a complete knowledge graph system."

**Seed:** notes/what-is-a-company-brain.md (field evidence), Lukas + Matthias
interviews, founders chat 03.07.

## 2. What is a company brain (and is your setup one?)

**Reader takeaway:** a mental model to judge their own stack. A company brain
is one shared memory all your agents read from and act on. Test your
Obsidian/Notion/GitHub setup against it: Does every agent read the same
memory, or does each keep its own? Does it update itself in the background,
or only when you file things? Does it model *your* domain (deals, cases,
tenders) or generic notes? Most setups fail all three — now the reader knows
what to fix, buy, or build.

**Evidence:** Micha's six-bullet definition; why gbrain/gstack made the
category visible; Karpathy's LLM wiki as the mechanics.

**Seed:** notes/what-is-a-company-brain.md, Karpathy LLM wiki gist
(sources.md), big-cake panel 3.

## 3. The agent can write the tender. It can't find the tender.

**Reader takeaway:** when an agent disappoints, check what you did *before*
prompting it — most of the time you were hand-assembling context. Count the
copy-pastes that precede every "AI task" in your company: that assembly work,
not the writing, is the thing to automate next. The model stopped being your
bottleneck; your context supply chain is.

**Evidence:** a defense founder whose tenders an LLM could easily write —
every fact exists in the company — but nobody can use it because the context
must be copied in by hand, every time.

**Seed:** Lukas interview 2026-07-02.

## 4. You can't buy the AI-native stack yet. You can start recording.

**Reader takeaway:** three things to set up this week, even though the
tooling isn't ready: (1) record everything — meetings, decisions, agent
sessions — into artifacts a machine can read; (2) keep one id connecting
issue → branch → spec → commits, so future agents can trace *why*, not just
what; (3) prefer tools whose data you can walk away with. The payoff:
when the AI-native tooling arrives, your company has its own history as
training data. Companies that start recording then will start from zero.

**Evidence:** "if it was not recorded, it did not happen to the intelligence
layer"; Micha's own trace-linking setup; the spec-keeping debate.

**Seed:** notes/the-agentic-future.md, YC self-improving-company transcript,
founders chat 19.06.

## 5. The three-month-employee test

**Reader takeaway:** a one-question test to apply to any "AI memory" or
"knowledge" tool before buying or building it: can it tell you about the
partner company no document describes — assembled from invoices, a
misnamed Slack channel, and email threads? A three-month employee can.
If the tool only retrieves what you explicitly filed, it's search with
better marketing. Use the test in every demo; it collapses the category's
vagueness in one move.

**Evidence:** Lukas's "Firma X" bar (credit the conversation); Felix's "how
is this different from Obsidian/Notion setups" — this is the answer.

**Seed:** Lukas interview; notes/what-is-a-company-brain.md.

## 6. Delete more insights

**Reader takeaway:** if you're building a capture pipeline — meeting bots,
insight extractors, auto-wikis — build the relevance gate before you scale
ingestion. A system generating a million insights of which 2% matter doesn't
save work, it creates triage work, and that's why your team quietly stopped
reading its output at week three. Measure "acted on," never "captured."

**Evidence:** Matthias (his team lives this: check-in bots + insight wikis
that produce too much); Srecko's "suggest, don't make people author."

**Seed:** Matthias interview 2026-07-03; Srecko memo (library/).

## Parked (needs more field evidence first)

- **Agents propose, humans merge** — takeaway would be a design rule for
  anyone building agent-writes-to-shared-state products: git-grade rigor
  underneath, suggestion-shaped surface on top. Wait until we've built our
  own approval surface so the article has receipts.
- **Code is truth vs. intent is truth** — takeaway would be: your codebase
  answers what, never why; decide deliberately where "why" lives before your
  agents need it. Needs our own trace-linking setup as proof.
