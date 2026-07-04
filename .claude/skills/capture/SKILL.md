---
name: capture
description: Record the published version of a post and learn from Micha's edits. Use after he posts something, when he pastes a final version, or says "I posted it" / "capture this".
---

# Capture taste from a published post

Micha's edits between draft and published version are the highest-signal taste
data this repo has. This skill records the final and turns the diff into
updated taste rules.

## 1. Get the final version

- If he pasted the published text, use that.
- Otherwise check `git diff` on `.vertical/gtm/posts/` — an edited Draft
  section usually IS the published version.
- If neither, ask him to paste what he actually posted.

## 2. Record it

In the post file:
- Add a `## Final` section with the published text (keep `## Draft` as the
  original draft — if the draft was edited in place, recover the original from
  git history).
- Set `Status: Posted`.
- Update the row in `social-calendar.md` (Status: Posted, add link if he has one).

## 3. Mine the diff

Compare draft and final. For each meaningful change, name what he did and why
(one line each): word swaps, deletions, added lines, reshaping. Deletions are
the most informative — what he cuts is the cut list.

Then update `.vertical/gtm/TASTE.md`:
- **Change confirms an existing rule** → strengthen it or add the example to
  its evidence, only if it sharpens the rule.
- **Change shows something new** → add a rule, evidenced by this pair.
- **Change contradicts a rule** → don't silently overwrite. Show him both and
  ask whether taste changed; update accordingly.
- Add a one-liner to the Pair log. Promote the pair into Calibration pairs
  (and rotate the weakest one out to the log) only if it teaches something the
  current three don't.
- Keep TASTE.md under ~150 lines — merge and sharpen, never just append.

## 4. Report

Tell him in 2-3 sentences what his edits taught the system this time. If his
edits are getting smaller over time, say so — that's the loop working.
