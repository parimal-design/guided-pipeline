# Guided Pipeline

**Makes AI outputs usable by humans, not just technically correct.**

## The problem

You ask an AI to build you a system. It does: breaks the work into tasks,
validates each one, executes end-to-end. Technically great. Then you open the
project the next day and have no idea what's done, what's next, or where to
even start. The only way to find out is to read every file the AI created.

That happened to me. This skill is the fix.

## What it does

Drop `guided-pipeline` into any AI coding tool or agent workspace that supports
Agent Skills (Claude Code, Claude.ai, Cursor, etc.). From then on, every
multi-step process it runs for you ends each step with a short **Status Report**:

- **What just happened**: in plain language
- **What it means**: for you, not for the system
- **What's next**: the specific next action
- **How we know it worked**: the validation result

You choose how much oversight you want, and can change it any time mid-pipeline:

- **Manual** (default): every step waits for your go-ahead.
- **Balanced**: only consequential/hard-to-reverse steps wait; easy ones just
  run and get reported.
- **Autopilot**: the whole thing runs unattended, then you get one report
  covering every step at the end.

Just say "switch to autopilot," "only ask me about the big stuff," or "back to
manual" at any point.

At the very end of a pipeline, it also runs a **Gut Check**: in plain
language, it checks the whole output against what you originally asked
for, not just the last step. This is global, not per-step. It runs once,
comparing the entire run against your original goal, so gradual drift gets
flagged instead of buried under a pile of individually fine-looking steps.

## Install

```bash
npx skills add parimal-design/guided-pipeline
```

That's the standard install path via the community `skills` CLI, which detects
your agent (Claude Code, Codex, GitHub Copilot, OpenCode, and others) and
installs accordingly.

If your tool doesn't support the CLI, install manually instead:

```bash
git clone https://github.com/parimal-design/guided-pipeline.git
cp -r guided-pipeline ~/.claude/skills/
```

(Path above is for Claude Code. For Claude.ai or another tool that supports
Agent Skills, upload the `guided-pipeline` folder wherever that tool lets you
add skills.)

## Example

```
Step 2 of 4: Outline drafted

What happened: Turned your notes into a 5-section outline.
What it means: You have a structure to react to before I write full paragraphs.
Validation: ✅ Every section traces back to something in your notes.
Next: Review the outline, then say the word and I'll write the full draft.
```

## Quick start

1. Start any multi-step task as you normally would.
2. After the first step finishes, you should see a Status Report, not silence.
3. By default (Manual mode), it waits for you to say the word before the next
   step starts. Switch to Balanced or Autopilot any time by just saying so.
4. That's it. No configuration needed.

## Why this isn't just "another Claude.md"

Most AI-behavior skill packs (rightly) focus on making the AI write better
code: clearer assumptions, less overengineering, tighter loops. This skill is
about something adjacent but different: making the *output of any pipeline
legible to the human running it*, grounded in usability, engineering, and
product thinking. Full reasoning behind each in `references/usability.md`,
`references/engineering.md`, and `references/product.md`.

## Files

- `SKILL.md`: the skill itself (Status Report format, Modes, Gut Check)
- `references/usability.md`: the usability lens (legibility, translation, control)
- `references/engineering.md`: the engineering lens (validation, failure handling)
- `references/product.md`: the product lens (success metrics, feedback loops)
- `assets/status-report-template.md`: the template every step's report follows, including the end-of-pipeline Gut Check block
- `evals/cases/guided-pipeline.json`: trigger and behavioral eval cases for the skill

## License

MIT. Use it, fork it, adapt it to your own pipelines.
