# Running gbrain ourselves: field notes

Status: Working note — raw material for an experience-based article
Author: Micha (dictated 2026-07-05, structured by agent; corrections applied same day)
Related: [what-is-a-company-brain.md](what-is-a-company-brain.md), essays/QUEUE.md

The honest adoption report: what it actually took to get gbrain running for
ourselves, what hurt, what worked. Complements the thesis essays with dirt
under the fingernails. Also quietly the strongest argument for the hosted
version, without ever pitching it.

## The pain

- **You adopt someone else's mental models.** Getting productive means
  learning how the system thinks it should be used. A lot of that learning
  was chatting with the codebase itself to figure out how it's supposed to
  work.
- **Ingestion is on you.** The repo has recipes for how to ingest certain
  types of data, but you are still left to implement the ingestion yourself.
  And it's not always clear whether to use a tool directly or set up an
  integration for it.
- **Operations means running a full OpenClaw/Hermes node.** You want limits,
  guardrails, all of that — and to take real advantage of gbrain you have to
  run a full node. Most people in a company don't, and never will.
- **It integrates only so-so with Claude and Codex.** Which is what most
  people actually use.
- **Single use case vs. multi use case.** For one use case it's fine. How to
  best work with it across multiple use cases is an open question.
- **No UI.** You live in files and sessions; there's no window into what the
  brain knows or what changed.

## The good

- It really seems to work. Working with our agents got noticeably better.
- Building features on top of it worked great.

## The insight (the article's ending)

As a startup you should be focused on making your beer taste better.
(The old brewery parable: breweries once ran their own power plants, until
electricity became something you buy. You brew the beer; you buy the power.)

gbrain can help make your beer taste better. Setting it up and operating it
yourself can also distract you from exactly that.

## Article notes

- Register: experience-based, honest, specific — the pains listed as lived
  moments, not feature critique. No pitch; the hosted conclusion stays
  implicit (the reader does that math alone).
- The beer line is the closer. It also scopes the essay: this is not a
  review of gbrain, it's about the build-vs-buy line for company
  infrastructure when you're supposed to be finding product-market fit.
- Fits the series as the ground-truth companion to "Why is everyone talking
  about gbrain?" — that one explains the pull, this one reports the friction.
