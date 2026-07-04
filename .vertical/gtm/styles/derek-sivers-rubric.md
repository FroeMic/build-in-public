# Eval rubric: Derek Sivers style

Scores how closely a text matches the style in `derek-sivers.md`. It evals
**Derek-ness only** — not whether the idea is good, and not whether it sounds
like Micha (that's TASTE.md's job).

How to run: give a judge (fresh Claude session, or ask in-session) this file,
the style pack, and the text. The judge must quote evidence from the text for
every score — no unquoted claims.

## Step 1 — Mechanical counts (do these first, they're objective)

| Check | Target | Red line |
|---|---|---|
| Average sentence length | 8–15 words | any sentence > 25 words |
| Sentences per paragraph | 1–3 | any paragraph > 4 sentences |
| Total length | 200–400 words | > 500 words |
| Hedges ("I think", "maybe", "probably", "somewhat", "arguably", "in many cases") | 0 | ≥ 3 |
| Weak sentence openers ("There is/are", "It is", "I think", "Whether or not") | 0–1 | ≥ 3 |
| Adjectives + adverbs per 100 words | < 5 | > 10 |
| Ideas in the piece | exactly 1 | 2+ |

Report each count with the worst offender quoted.

## Step 2 — Dimensions (0–10 each, with evidence)

**1. Compression** — 10: deleting any sentence breaks the piece. Test: put
each sentence on its own line (his method); every one must earn its line.
5: a few sentences restate or decorate. 0: paragraphs of setup and recap.

**2. Structure** — 10: opens mid-scene or with a direct question; one turn;
principle arrives *after* the concrete material earned it; title is the idea.
5: right parts, wrong order (principle first, then justification).
0: essay-shaped windup, context-setting, "in this post".

**3. Sentence mechanics** — 10: short declaratives, hard length variation,
first words punch, last words linger, strong subjects and verbs.
5: correct but monotone — all sentences the same length.
0: long comma-chained sentences, passive voice, nominalizations.

**4. Concreteness** — 10: a real scene, a real number, a named moment; at
most one vivid parable. 5: examples exist but generic ("a founder might...").
0: abstract-noun claims stacked on abstract-noun claims.

**5. Directness** — 10: plain assertions, second person where natural, zero
hedges or permission-asking. 5: assertive but third-person distant.
0: qualified, hedged, "it could be argued".

**6. Ending** — 10: last line is a command, aphorism, or dare that lingers
("Don't be a donkey."); stops one line before a lesser writer would.
5: ends fine but keeps a soft summary sentence. 0: recaps the point.

## Step 3 — Discrimination test

Answer honestly: *"If this appeared on sive.rs between two real essays, what
would a regular reader notice as off — first, specifically?"* One paragraph.
If the answer is "nothing", say what gave you pause anyway.

## Step 4 — Verdict

```
Scores: compression X · structure X · mechanics X · concreteness X · directness X · ending X
Overall: X/10 (not an average — weight compression and ending highest)
Sounds like Sivers: yes / almost / no
```

Then the **three highest-leverage edits**, each shown as before → after,
rewritten in-style. Not a list of problems — actual rewritten lines.

## Notes for the judge

- Don't reward polish. Derek's writing is plain, not smooth. A slick,
  "well-written" text should score LOW on directness and compression.
- Don't punish simplicity as "thin". Short and plain is the target.
- Length bias check: if you scored a longer text higher, re-check — this
  rubric anti-correlates with length.
- If the text hedges because it's Micha's X voice, don't average it away —
  score it honestly and note the register conflict. TASTE.md and this pack
  are different targets on purpose.
