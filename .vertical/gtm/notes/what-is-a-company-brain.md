# What is a company brain?

Status: Working note — definition draft + open questions
Authors: Micha + Felix
Date: 2026-07-04
Related: [the-big-cake.md](the-big-cake.md), [the-agentic-future.md](the-agentic-future.md)
Evidence this week: gbrain interviews (Lukas/defense 2026-07-02, Matthias/construction-software 2026-07-03), founders-chat threads, Srecko's Missing Backend memo (library/)

## Definition (Micha)

A company brain is one shared memory your AI agents read from and act on.

- **Captures all company context in one place:** Linear issues, CRM data, Slack
  discussions, and every meeting transcript (standups, sales calls, and the
  rest) land in one place instead of being spread across separate tools. Most
  of it is already being recorded; the brain just brings it together.
- **Makes your company queryable for agents:** any agent (or you) can just ask
  what's relevant instead of hunting across tools. For example, pulling all
  the related context from sales calls before building a feature, or
  understanding the state of a project in your company based on current Slack
  conversations.
- **Synthesizes knowledge from raw material:** it processes captured context
  in the background to make it useful: it extracts the key facts, links the
  entities, and resolves conflicts when sources disagree.
- **Adapts to your company:** the brain isn't a fixed template, it tracks the
  things that matter in your business. A SaaS tracks deals and accounts, a law
  firm tracks cases. The brain takes the shape of your business.
- **Captures how work is done in skills:** agents watch / listen to what is
  happening and turn procedural knowledge into skills. Other agents can
  discover and install them. This way they can start acting.
- **Every agent connects to the same brain:** your coding agent, your sales
  agent, your assistant all read from and write to one memory, so they share
  one picture instead of each keeping their own.

## The tacit-alpha point (Micha, 2026-07-04)

What makes a company unique today is the tacit knowledge embedded in the
organization — between people, departments, suppliers, partners. Transactive
memory systems ("who knows what"). That's their alpha. If your AI can't see
or navigate it, it will stay a co-pilot.

Implication chain: everyone has the same models → AI on explicit knowledge is
a symmetric boost (no advantage) → the only asymmetric AI is AI that runs on
YOUR tacit knowledge → making the tacit layer navigable is the actual
difference between AI-assisted and AI-native. Connects to: the compounding
claim (models can only compound what they can see), the three-month-employee
test (what that employee learns IS the transactive memory), and skillify
(capture by observation, not authorship — the reason this works now when
1990s knowledge management failed).

### The legibility promise (Micha, 2026-07-04)

In AI-native companies you make tacit knowledge explicitly available by
capturing it in a machine-readable layer. This is not trivial — it means
rethinking how organizations work, what data needs to be recorded and how.

The promise, once you manage it: not just your agents — every human in the
organization can see the entire organization.
- CEOs see the most pressing issues directly, unshackled from layers of
  middle management.
- Engineers access customer signals from sales calls while building features.
- A new hire, on day one, can ask why any decision was made and get the real
  answer — with sources. The knowledge that today takes three months of
  coffee chats to absorb, available from hour one.

### The three axes of legibility (framing, 2026-07-04 — might be its own essay)

Company opacity has three dimensions, and the machine-readable layer opens
all three:
- **Vertical (layers):** the CEO sees the pressing issues directly, past
  management layers. Hierarchy exists to route information; it also filters it.
- **Horizontal (silos):** the engineer reaches the customer signal in sales
  calls while building the feature. Departments hoard by accident.
- **Temporal (history):** the new hire gets the *why* behind any decision,
  with sources. Time hides intent; people leave, context leaves with them.

Note: the temporal axis reuses the three-month-employee test as the positive
promise instead of the skeptical test — same idea, two essays of mileage.

### Open questions (Micha, 2026-07-04)

1. If you capture what makes your company unique in data — what is left?
   Could an AI run the business? (First-pass answer "humans give taste and
   direction" flagged by Micha as too grand. Sharper candidate: alpha is a
   flow, not a stock. The brain captures yesterday's tacit knowledge; humans
   at the edge — customer calls, novel situations — generate tomorrow's. A
   company that stops generating new tacit knowledge has a perfectly
   documented commodity.)
   Quotable candidates (Naval-style compression, 2026-07-04, none picked yet):
   - "You can copy what a company knows. You can't copy how fast it learns."
   - "Alpha isn't what you know. It's how fast you learn."
   - "Stored knowledge is a commodity. Learning is a moat."
   - "Your alpha isn't in the database. It's in the delta." (gimmick risk)
   (Earlier stock/flow phrasings rejected as not good enough — the metaphor
   was the scaffolding, not the idea.)

   Riff continuation (Micha, 2026-07-04): "Companies are learning machines.
   Data is not your alpha. ..." Completions:
   - "Companies are learning machines. Data is not your alpha — your
     learning rate is."
   - "Data is the exhaust. The loop is the alpha."
   - "Data is what the machine already learned. Alpha is what it learns next."
   Note: "companies are learning machines" closes the arc from the June
   anchor post ("Software has a built-in feedback loop. Companies do not.") —
   same thesis flipped from diagnosis to design. Candidate spine for the
   whole essay series. Also the anti-"data moat" angle: data is the ash,
   not the fire.

2. AI labs are on a path to capture all of this (centralization of memory in
   the model layer). How do companies keep control of their alpha / what
   makes them unique? (Connects to: model-provider independence assumption in
   the-agentic-future.md, Lukas's can't-send-defense-data constraint,
   Srecko's vendor-lock-in must-have. Candidate framing: the model is rented,
   the brain is owned. Possible essay: "Who owns your company's brain?")

## Felix — the most pressing questions

- Why does everyone talk about gbrain? Why does Garry talk about it?
- How is it different from all the other Obsidian, Notion, GitHub setups?

## Big Cake parts (Felix)

- **Data ingestion** — we connect as many sources for you as possible (seeing
  if people trust us with data is a good skin-in-the-game test)
- **An agent-friendly data layer** that reflects the domain reality of your
  business (must be accurate and efficient to query)
- **Synthesis, cleanup, graph building**
- **Domain modelling**
- **Easy to set up / use interface into agents?** How??
- **Dashboard to see what happened in the brain (for trust):** I want to see
  inside, especially updates; I probably want to approve critical changes or
  conflicts
- **Skillify:** agent suggests things to turn into a skill based on sessions &
  context → if this works people will go wild
- **Tracing all agent sessions** to see skills & context emerge — auto-improve
  via skills
- **Tool & skills analytics layer:** help them understand what skills are
  used / stale and how to make them more efficient

## This week's field evidence (for the definition to answer to)

- **Lukas (defense):** "would buy in a second"; tried building it himself
  three times, asked Netlight to spec it ("Autonomous Internal Agents MVP").
  His quality bar: the system must create "Firma X" as an entity from
  invoices, Slack channels, and emails when no document about Firma X exists —
  order out of chaos, replacing what a three-month employee knows. His use
  case: tenders — the LLM could write them, but all context must be
  copy-pasted by hand. His worry: permissions/composability (CEO emails must
  be in the mix but must not leak).
- **Matthias (construction software):** everyone on the team hand-builds their
  own tooling (daily check-in bot over email/Slack/calendar with an LLM wiki;
  a product-insights wiki over Slack + Granola). His warning: "a million
  generated insights doesn't mean two percent are useful" — relevance, not
  capture, is the bottleneck. His product already runs the loop we describe:
  per-customer markdown rules, reasoning pass when users edit outputs, rule
  weights, background eval regressions.
- **Founders chat:** Sebastian asking who can build knowledge graphs from
  unstructured data; Klemens's homebrew whole-company knowledge graph exposed
  as an MCP server ("started as RAG, evolved"); the June spec debate (Nimar:
  "code is truth" vs Rod: living versioned docs, agent-maintained; Micha: one
  id connecting issue → branch → spec → commits so agents can trace intent).
- **Srecko's memo:** the engine's mental model is git (branch, review, merge,
  audit) but the surface must feel like Notion; suggest, don't make people
  author; the artifact, not the field, is the unit of control.
