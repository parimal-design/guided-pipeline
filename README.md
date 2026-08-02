# Guided Pipeline

**An Agent Skill that makes AI-built pipelines usable by the human running them.**

## The problem

You ask an AI to build you a system. It does — breaks the work into tasks,
validates each one, executes end to end. Technically great. Then you open the
project the next day and have no idea what's done, what's next, or where to
even start. The only way to find out is to read every file the AI created.

That happened to me. This skill is the fix.

## What it does

Drop `guided-pipeline` into any AI coding tool or agent workspace that supports
Agent Skills (Claude Code, Claude.ai, Cursor, etc.). From then on, every
multi-step process it runs for you ends each step with a short **Status Report**:

- **What just happened** — in plain language
- **What it means** — for you, not for the system
- **What's next** — the specific next action
- **How we know it worked** — the validation result

You choose how much oversight you want, and can change it any time mid-pipeline:

- **Manual** (default) — every step waits for your go-ahead.
- **Balanced** — only consequential/hard-to-reverse steps wait; easy ones just
  run and get reported.
- **Autopilot** — the whole thing runs unattended, then you get one report
  covering every step at the end.

Just say "switch to autopilot," "only ask me about the big stuff," or "back to
manual" at any point.

## Why this isn't just "another Claude.md"

Most AI-behavior skill packs (rightly) focus on making the AI write better
code — clearer assumptions, less overengineering, tighter loops. This skill is
about something adjacent but different: making the *output of any pipeline
legible to the human running it*, built on three of Nielsen's usability
heuristics (visibility of system status, match between system and the real
world, user control and freedom) plus engineering-grade validation gates and
product-grade success metrics. See `references/usability.md`,
`references/engineering.md`, and `references/product.md` for the full
reasoning behind each.

## Install

```bash
git clone https://github.com/<your-username>/guided-pipeline.git
cp -r guided-pipeline ~/.claude/skills/
```

(Path above is for Claude Code. For Claude.ai or another tool that supports
Agent Skills, upload the `guided-pipeline` folder wherever that tool lets you
add skills.)

## Example

```
Step 2 of 4 — Outline drafted

What happened: Turned your notes into a 5-section outline.
What it means: You have a structure to react to before I write full paragraphs.
Validation: ✅ Every section traces back to something in your notes.
Next: Review the outline — say the word and I'll write the full draft.
```

## Quick start

1. Start any multi-step task as you normally would.
2. After the first step finishes, you should see a Status Report — not silence.
3. By default (Manual mode), it waits for you to say the word before the next
   step starts. Switch to Balanced or Autopilot any time by just saying so.
4. That's it — no configuration needed.

## Files

- `SKILL.md` — the skill itself
- `references/usability.md` — the usability lens (legibility, translation, control)
- `references/engineering.md` — the engineering lens (validation, failure handling)
- `references/product.md` — the product lens (success metrics, feedback loops)
- `assets/status-report-template.md` — the template every step's report follows

## License

MIT — use it, fork it, adapt it to your own pipelines.
