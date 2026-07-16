---
name: find-unknowns
description: Surface and close the gaps between what the user envisions and what actually gets built — with emphasis on the parts a design phase misses: catching unknowns mid-build, and verifying after the fact that the user actually understood what changed. Use during and after a piece of work to log the judgment calls and edge cases you hit, explain what really changed to catch mismatches while they're cheap, and quiz the user to check their understanding. For the up-front design conversation prefer superpowers:brainstorming; for a pure relentless one-question interview prefer /grilling — this skill is the lightweight unknowns lens that wraps around both and covers the during/after stages they don't.
---

The quality of what we build together is bottlenecked by how well we've clarified the unknowns — the gaps between the map (what the user pictures) and the territory (what actually gets built). This skill's job is to find and close those gaps cheaply, with a deliberate focus on the stages a design phase leaves uncovered: while you're building, and after you're done.

## The mental model: four kinds of unknowns

Keep this frame in the back of your mind. It tells you what you're fishing for.

- **Known knowns** — already stated in the request. Nothing to do.
- **Known unknowns** — gaps the user knows exist but hasn't resolved. Ask about these directly.
- **Unknown knowns** — details so obvious to the user they'd never write them down, but that you'd get wrong without them. Draw these out by proposing a concrete approach and letting them react ("I'll store it as UTC" → "no, always local time").
- **Unknown unknowns** — factors neither of you has considered, or a quality bar the user can't yet articulate. Surface these by prototyping and pointing at references so the user recognizes what they want when they see it.

Every instrument below is just a cheap way to move something out of the bottom-right quadrant before it turns into expensive rework.

## Before building — hand off, don't duplicate

The up-front design conversation is already well covered, so don't reinvent it here:

- For turning an idea into a full design and spec, **invoke `superpowers:brainstorming`** (if available). It runs the clarifying-questions → propose-approaches → written-spec flow with proper gates.
- For a pure relentless, one-question-at-a-time stress test of an existing plan, **use `/grilling`**.

The one lightweight pre-build move that belongs *here*, for when you're **not** doing a full brainstorm (a small change, a quick fix): a **blind-spot pass** — a fast sweep for what the request doesn't mention but probably needs (error cases, empty/huge inputs, auth, migrating existing data, who else touches this). Present the list, flag which you'll assume defaults for and which genuinely need a decision. If the answer is "this deserves a real design," hand off to `superpowers:brainstorming` instead of interviewing piecemeal.

## During building — the part nothing else captures

- **Implementation notes** — As you build, log the deviations, edge cases, and judgment calls you hit ("the API returns null here, so I defaulted to 0"; "the spec didn't say what happens on a duplicate — I made it idempotent"). These are exactly the unknown knowns and unknown unknowns surfacing in real time. Capture them instead of letting them vanish into the diff, and surface the *consequential* ones to the user while the decision is still cheap to revisit — don't wait until the end to mention that you silently picked a behavior they might disagree with.

## After building — did the intent actually land

- **Explainer / pitch** — Summarize what actually changed and why, in the user's terms (not a changelog of files). The real payoff isn't documentation — it's that restating the change in plain language exposes any mismatch between what they wanted and what got built, while it's still cheap to adjust.
- **Quiz** — When it matters that the *user* understands the change (not just that the code works), ask them a couple of pointed questions about it. A one-directional explanation lets both of you assume understanding that isn't there; a question or two flushes out the gap. This is the unknowns lens pointed back at the human, and it's the piece that code-review and verification skills don't cover — they check the code, not the person.

## How to run it

1. Name the stage and the instrument you're reaching for, and why. Don't run all of them — pick what fits.
2. Prefer resolving unknowns by exploring the codebase, prototyping, or pointing at references over interrogating the user — cheaper for them, and it catches things questions miss.
3. When you do ask, ask sparingly and attach a recommended default, so the user spends attention only where their judgment changes the outcome.
4. Stop when the remaining unknowns are cheap to fix later. The goal isn't total certainty — it's moving the *expensive* surprises up front, and confirming the intent survived the trip into code.
