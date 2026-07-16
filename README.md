# find-unknowns

A lightweight [Claude Code](https://claude.com/claude-code) slash command that helps you **surface and close the gaps between what you envision and what actually gets built** — the *unknowns* in a piece of work.

It's inspired by Anthropic's field guide, [*Finding Your Unknowns*](https://claude.com/blog/a-field-guide-to-claude-fable-finding-your-unknowns), which frames model output quality as being bottlenecked by how well you clarify your unknowns.

## The idea

Everything runs on one mental model — the four kinds of unknowns:

| Quadrant | What it is | How you close it |
|---|---|---|
| **Known knowns** | Already in the request | Nothing to do |
| **Known unknowns** | Gaps you know exist | Ask directly |
| **Unknown knowns** | Obvious to you, never written down | Propose a concrete approach, let yourself react |
| **Unknown unknowns** | Neither of you has considered it | Prototype, point at references |

Every instrument in the skill is just a cheap way to move something out of the bottom-right quadrant *before it gets expensive to fix*.

## ⚠️ This skill is designed to work WITH two other skills — not replace them

`find-unknowns` is deliberately **not** a do-everything skill. It's the *unknowns lens* that wraps around your workflow and covers the stages other tools ignore. It hands off the up-front work:

| Stage | Handled by | Notes |
|---|---|---|
| **Before** – full design → spec → plan | [`superpowers:brainstorming`](https://github.com/obra/superpowers) → `writing-plans` | find-unknowns *routes to it*, doesn't duplicate it |
| **Before** – relentless interview of a plan | [`/grilling`](commands/grilling.md) | Sharp, one-question-at-a-time stress test |
| **Before** – quick blind-spot pass | **find-unknowns** | Only for small fixes not worth the full design flow |
| **During** – build | **find-unknowns** | Implementation notes — *nothing else covers this* |
| **After** – did the intent land? | **find-unknowns** | Explainer + quiz — *nothing else covers this* |

**Dependencies / companions:**

- **[superpowers](https://github.com/obra/superpowers)** — the `brainstorming` and `writing-plans` skills own the up-front design and planning. `find-unknowns` invokes `superpowers:brainstorming` for real design work instead of reinventing it.
- **`/grilling`** — a companion command (included here in [`commands/grilling.md`](commands/grilling.md)) for a pure, relentless plan interview. `find-unknowns` points you to it rather than doing its own interrogation. **Not my work** — forked from [Matt Pocock's skills repo](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md). See [Credits](#credits).

Together the three reproduce the whole *Finding Your Unknowns* toolkit — distributed across tools that trigger at the right moment, rather than one essay you read once.

## Install

Copy the command file(s) into your Claude Code commands directory:

```bash
# user-level (available in every project)
cp commands/find-unknowns.md ~/.claude/commands/
cp commands/grilling.md      ~/.claude/commands/   # optional companion
```

For the before-build handoff to work, also install [superpowers](https://github.com/obra/superpowers).

## Usage

```
/find-unknowns
```

Invoke it **during** and **after** a piece of work — to log the judgment calls you hit while building, explain what really changed (to catch mismatches while they're cheap), and quiz yourself to confirm the intent actually landed. For the up-front design conversation, use `superpowers:brainstorming`; for a pure interview, use `/grilling`.

## Credits

- **`/grilling`** ([`commands/grilling.md`](commands/grilling.md)) is **forked from [Matt Pocock](https://github.com/mattpocock)'s skills repo** — original: [`skills/productivity/grilling/SKILL.md`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md), used under the **MIT License** (Copyright (c) 2026 Matt Pocock; see [`NOTICE`](NOTICE)). All credit for that skill goes to him; it's included here only as a companion so this repo works out of the box.
- The **unknowns mental model** and lifecycle framing come from Anthropic's field guide, [*Finding Your Unknowns*](https://claude.com/blog/a-field-guide-to-claude-fable-finding-your-unknowns).
- The **before-build handoff** relies on [superpowers](https://github.com/obra/superpowers) by [obra](https://github.com/obra).

## License

MIT
