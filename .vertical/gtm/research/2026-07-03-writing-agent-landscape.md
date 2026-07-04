# Research: Build-in-Public Writing Agents, Voice Pipelines, and Evals for Subjective Writing Quality

Researched 2026-07-03 (Opus web-research agent). Context: designing a build-in-public
writing agent for this repo that accumulates taste in Claude Code skills and improves
them via an eval loop.

---

## 1. People & projects building personal writing agents

### The strongest primary reference: Every's Spiral (Dan Shipper)
Spiral is the most mature "write-in-my-voice" system with published mechanics, and it maps almost 1:1 onto what we want to build. Worth reading their own posts closely:

- **Voice capture via stylometry.** Spiral computes a "writing fingerprint" (sentence-length distributions, punctuation frequency, word-choice ratios, syntactic structure) from your published corpus, then picks relevant samples per draft. They report generating 5,500+ style guides from 168,000+ writing samples ([Spiral 4.0](https://every.to/on-every/spiral-4-0-goes-agent-native)).
- **Taste is partly baked-in principles, partly model-level.** Spiral carries an explicit "library of principles" (active voice, most-interesting-idea-in-the-hook) layered on top of the base model's "gut sense for writing" ([Spiral v3: An AI Writing Partner With Taste](https://every.to/on-every/introducing-spiral-v3-an-ai-writing-partner-with-taste)).
- **Three-stage pipeline**: pre-writing idea vetting → draft generation (stylometry + domain expertise) → polishing with custom editing rules. Front-end starts with a **collaborative interview** to surface "what you're really trying to say," then generates **three simultaneous drafts** you mix and match ([v3](https://every.to/on-every/introducing-spiral-v3-an-ai-writing-partner-with-taste)).
- **The discrimination eval, in production.** Spiral runs an **LLM-as-judge discrimination test**: an evaluator tries to distinguish generated text from the writer's real samples in blind testing. They report ~**87%** blend rate ("blends with authentic samples ~9 times out of 10") ([Spiral 4.0](https://every.to/on-every/spiral-4-0-goes-agent-native)).
- **Agent-native.** Spiral 4.0 exposes a remote MCP server (`https://api.writewithspiral.com/mcp/`), CLI, and API. Background on Dan Shipper's thinking: [He Built an AI Ghostwriter With Taste](https://every.to/podcast/spiral-s-creator-on-why-better-writing-means-better-thinking).

**Key gap**: their published material does **not** describe learning from user edit-diffs as a training signal. The loop is human-selects-among-drafts, not diff-capture. That gap is where our approach is genuinely differentiated.

### Matt Pocock — skills craft, not writing voice (transfers by analogy)
Pocock's `mattpocock/skills` is his real `.claude` directory published, ~20K+ stars, framed as "workflow enforcement, no freestyle" ([repo](https://github.com/mattpocock/skills), [CLAUDE.md](https://github.com/mattpocock/skills/blob/main/CLAUDE.md)). Engineering-focused, **not** writing-in-voice. What transfers: his meta-skill **`writing-great-skills`** (vocabulary/principles for authoring predictable skills), plus `teach` (build a skill over multiple sessions) and `handoff` (compact context). Reference for *how to structure skill files*, not for voice.

### Garry Tan — same story: gstack is code, not content
`gstack` is Garry Tan's Claude Code setup — CEO/Designer/Eng-Manager/QA personas as slash commands ([repo](https://github.com/garrytan/gstack), [TechCrunch](https://techcrunch.com/2026/03/17/why-garry-tans-claude-code-setup-has-gotten-so-much-love-and-hate/)). ~66K stars. **Nothing about writing in his own voice** — liftable pieces are the *persona-as-skill* pattern and the `/office-hours` "six forcing questions" discovery step (a good model for idea-capture/angle-selection). No public Garry Tan writing-agent setup exists.

### Nat Eliason — the "edit, don't generate" school
Clearest voice arguing AI belongs in *editing*, not first-draft generation: voice-to-text + Claude to lightly clean transcripts and outline, but keeps the writing himself ([What AI Can't Write](https://blog.nateliason.com/p/ai-writing); [tweet on the AI writing app he wants](https://x.com/nateliason/status/1890421585737044128)). Early Spiral fan ([tweet](https://twitter.com/nateliason/status/1803128723912139088)). Design implication: the agent should be a *drafting-and-critique partner feeding a human edit*, and the edit is the signal.

### David Perell — voice preservation via extensive priming
Documented by Every ([How David Perell Uses ChatGPT to Write for Millions](https://every.to/chain-of-thought/how-david-perell-uses-chatgpt-to-write-for-millions)) — heavy context-priming, model as thinking partner rather than ghostwriter.

### swyx — thread came up empty
No primary source found specifically on voice-preserving AI writing workflows.

### Others worth knowing
- **`jalaalrd/anti-ai-slop-writing`** — a cross-agent SKILL.md that eliminates detectable AI patterns (six detection categories, core rules <500 lines, detailed vocab loaded on demand) ([repo](https://github.com/jalaalrd/anti-ai-slop-writing)). A ready-made component for the critique stage.
- Community write-ups of Claude Code / CLAUDE.md as a *writing* OS (secondary sources): "About Me file read before every task" + "brand-voice skill" pattern ([aimaker](https://aimaker.substack.com/p/how-i-turned-claude-code-into-personal-ai-agent-operating-system-for-writing-research-complete-guide), [ranthebuilder](https://ranthebuilder.cloud/blog/how-i-use-claude-cowork-to-write-with-ai-in-my-voice/)).

---

## 2. Pipeline patterns for write-in-my-voice systems

Canonical pipeline (Spiral + academic edit literature):

1. **Idea capture + angle selection** — a discovery interview ("what are you really trying to say"), not a cold prompt.
2. **Multiple candidate drafts** — generate N (Spiral does 3) to explore the possibility space.
3. **Voice conditioning** — stylometric fingerprint + few-shot samples from own corpus, plus explicit written principles.
4. **Self-critique against style rules** — banned-lexicon/anti-slop pass and rubric before showing drafts.
5. **Human edit** — the human picks and rewrites.
6. **Capture the edit as signal** — the diff between AI draft and published final is the training data.

### The edit-diff learning signal — strongest academic backing
**"Can AI writing be salvaged?"** (arXiv 2409.14509, [HTML](https://arxiv.org/html/2409.14509v2)):
- Expert edits break down as **replacements 74% / deletions 18% / insertions 8%**; 70% of non-deletion edits preserve meaning, 30% are substantive.
- LLM idiosyncrasies are consistent across GPT-4o, Claude-3.5-Sonnet, Llama-3.1: templates like "a mix of X and Y," "the weight of X," overused words ("unspoken" in ~15% of outputs).
- **Seven-category edit taxonomy**: awkward word choice/phrasing (28%), poor sentence structure (20%), redundant exposition (18%), clichés (17%), plus purple prose, lack of specificity, tense inconsistency. Ready-made schema for tagging verdicts mined from diffs.
- **Edits demonstrably improve alignment**: Writer-edited > LLM-edited > LLM-generated in preference ordering; automated few-shot span detection reached 0.46 precision vs 0.57 human agreement — a system *can* learn to flag the spans you'd edit.

### Prompt/skill-improvement loop options
- **GEPA (Reflective Prompt Evolution)** — best fit for a taste-accumulating skill loop. Replaces scalar rewards with **natural-language reflection on execution traces**, maintains a Pareto frontier of candidates; beat MIPROv2 by 13% / GRPO by 20% with 35× fewer rollouts (ICLR 2026 oral). Ships as `dspy.GEPA` and standalone ([arXiv 2507.19457](https://arxiv.org/abs/2507.19457), [repo](https://github.com/gepa-ai/gepa), [DSPy docs](https://dspy.ai/api/optimizers/GEPA/overview/)). Natural-language feedback fits a subjective reward far better than a number.
- **Promptim / promptimizer** (LangChain, eval-driven prompt optimizer) ([blog](https://www.langchain.com/blog/promptim), [repo](https://github.com/hinthornw/promptimizer)).
- **Anthropic's skill tooling**: `skill-creator` and Skill Creator 2.0's **eval + Improve mode** — define input/expected-output test cases; on failure, Improve mode reads failure logs and proposes targeted skill edits ([Agent Skills engineering post](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills), [Skill Creator 2.0](https://www.thetoolnerd.com/p/anthropic-skill-creator-20-update), [skills repo](https://github.com/anthropics/skills), [best-practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)). Mechanical constraint: a rendered SKILL.md enters the conversation *once*, not re-read per turn — voice rules must be standing instructions ([Claude Code skills docs](https://code.claude.com/docs/en/skills)). Skills should be third-person with concrete Input:/Output: few-shot pairs.

---

## 3. Evals for subjective writing quality

### LLM-as-judge pitfalls (and mitigations)
Documented biases: **verbosity bias** (longer = higher score), **self-preference bias** (models favor their own outputs), **position bias** ([eugeneyan](https://eugeneyan.com/writing/llm-evaluators/); [Justice or Prejudice?](https://llm-judge-bias.github.io/); [The Judge Who Never Admits, arXiv 2602.07996](https://arxiv.org/pdf/2602.07996)). Standard mitigations:
- **Pairwise comparison with position swapping** (run twice, swap order) instead of absolute 1–10 scores.
- **Hide model identity**; **randomize order**; **state explicitly how verbosity should be treated** ([evidentlyai](https://www.evidentlyai.com/llm-guide/llm-as-a-judge); [qaskills 2026 guide](https://qaskills.sh/blog/llm-as-judge-evaluation-guide-2026)).
- Anchor rubrics in **real labeled examples**; calibrate against a human-labeled set.

### The discrimination test (strongest eval)
Spiral's blind **"can the judge distinguish your draft from your real published samples"** test — track a blend rate over time. Sidesteps verbosity/polish bias because it tests *indistinguishability from you*, not "goodness."

### Slop / novelty / originality measures
- **EQ-Bench Creative Writing v3** ([leaderboard](https://eqbench.com/creative_writing.html), [repo](https://github.com/EQ-bench/creative-writing-bench)): a **Slop column** (frequency-match against a master list of over-represented LLM words/phrases), a **Repetition column** (top word/bigram/trigram frequencies), and a **Novelty** component. As of June 2026 they judge with Claude Sonnet 4.6 for ELO. The slop list and repetition metric are directly liftable.
- **Lechmazur's writing benchmark** — forced incorporation of mandatory elements; a model for "did the draft actually say the specific thing" ([repo](https://github.com/lechmazur/writing)).
- **Banned-phrase / slop lists**: 50+ words (delve, tapestry, testament, vibrant, pivotal), 35+ phrases, 16 openers (Certainly/Moreover/Additionally), structural tells (`**Term:**` bold-colon prefix, "It's not X. It's Y.", rule-of-three), em-dash overuse ([anti-ai-slop repo](https://github.com/jalaalrd/anti-ai-slop-writing); [oliviacal blacklist](https://www.oliviacal.com/post/ai-writing-tells); [ruben.substack "Ban."](https://ruben.substack.com/p/delve)). Recommended production shape: **two-layer validator** (prompt + code-side regex) — prompts alone catch ~80% ([ozigi](https://blog.ozigi.app/blog/stopping-ai-slop-in-production-banned-lexicon-validator)).
- **Novelty via embedding distance** from the existing corpus to flag pastiche/regression-to-average.

---

## 4. Failure modes people actually report

- **Regression to the author's average / voice drift.** A Berkeley study ran 300 first-person narratives through three frontier models under "preserve the voice" prompts; **every model, every condition drifted the same way — fewer function words** ([bookmoth summary](https://bookmoth.app/blog/ai-writing-tool-that-preserves-voice/)). Voice loss is systematic, not prompt-fixable — hence stylometric conditioning + a discrimination eval.
- **Pastiche / slop from shared training data.** The idiosyncrasy paper found *identical* idiosyncratic phrases across GPT/Claude/Llama — the "average LLM voice" is a strong attractor.
- **Reward-hacking the judge.** Verbosity and self-preference bias mean a naïve judge rewards polish/length; a skill loop optimizing against it will Goodhart toward slop.
- **Engagement Goodharting on platforms.** LinkedIn penalizes engagement-bait; generic AI content shows a **~35% conversion decline after 3 months** vs stable human content ([zoomsphere](https://www.zoomsphere.com/blog/linkedin-algorithm-2026-why-generic-ai-content-kills-your-organic-reach); [rankscience](https://www.rankscience.com/blog/the-ai-content-trust-gap-solution)). Don't optimize the loop on raw engagement.
- **AI-tells that (sometimes) hurt — weaker than folklore.** A 1,000+ URL study found most AI tells statistically insignificant (<±0.1 correlation with engagement). Real negatives: **"Conclusion" headers (~−0.118)**, "Not only… but also," intro filler. **Em dashes correlated slightly *positively*** ([Search Engine Land](https://searchengineland.com/ai-writing-tics-engagement-study-470051)). Ban structural/filler tells; skip the em-dash panic.

---

## What this implies for the pipeline

1. **Copy Spiral's proven spine, add the piece they're missing.** Discovery interview → multi-draft (3) → stylometric voice conditioning → anti-slop self-critique → human edit. The differentiator is **step 6: capture the AI-draft→published-final diff** and mine it, using the seven-category taxonomy from arXiv 2409.14509 as the logging schema.
2. **Make the discrimination test the north-star eval**, not a quality score. Track blend rate (judge can't tell agent draft from real posts) over time.
3. **Layer slop control**: EQ-Bench slop/repetition metrics + a code-side banned-lexicon validator, calibrated against real engagement data (ban "Conclusion"/filler/"not only… but also"; don't reflexively ban em dashes).
4. **Drive the skill-improvement loop with GEPA-style natural-language reflection, not scalar rewards.** Subjective quality signals are better expressed as prose critique of traces; also harder to Goodhart.
5. **Guard against drift explicitly**: embedding-distance-from-corpus novelty check catching both pastiche (too close to generic LLM voice) and off-voice drift (too far from the author). Re-anchor rubrics to freshly labeled human examples on a schedule.
6. **Never optimize on engagement directly** — lagging, adversarial signal; optimize on voice fidelity + the author's own edit-acceptance rate.

Empty threads (not padded): no swyx primary source on voice-preserving workflows; neither Garry Tan nor Matt Pocock has a public *writing*-in-voice setup — their value is skill-authoring and persona patterns only.
