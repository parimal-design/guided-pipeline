---
name: guided-pipeline
description: Use this skill whenever you are building, running, or documenting a multi-step process, pipeline, agent workflow, or task breakdown that a HUMAN needs to follow — not just an AI executing silently. Guarantees that after every single step, the human is told what just happened, what it means in plain language, and exactly what to do next. Trigger this any time a task has more than one step, any time you're designing a system with phases/stages/checkpoints, any time the user asks "what do I do next," "how do I use this," or "I don't know where to start," and any time you notice you've built something technically correct but confusing to navigate. Do NOT use for single-step tasks with no follow-on action.
---

# Guided Pipeline

A skill for turning any multi-step process into one a human can actually follow —
without opening every file to figure out what happened or what's next.

## The problem this solves

AI systems are excellent at breaking work into tasks, building validation into each
one, and executing end to end. What they routinely skip is telling the human running
the thing where they are. The result: a technically sound pipeline that only the AI
that built it can navigate. This skill exists to close that gap.

## The core rule

**After every step completes — always, no exceptions — produce a Status Report**
before starting the next step or waiting for input. Use the template in
`assets/status-report-template.md`. Never leave a completed step silent.

A step is not "done" until its Status Report has been shown to the human.

## The four things a Status Report must answer

1. **What just happened** — in plain language, no jargon dump.
2. **What it means** — the practical implication, not just the technical result.
3. **What's next** — the single next action, named specifically.
4. **How we'll know it worked** — the validation/check for this step (see below).

If you can't fill in all four, the step isn't actually finished — go back and
finish it before reporting.

## Modes: how much the human wants to approve

The human running the pipeline chooses how much control they want, and can
change their mind **at any point** — mid-pipeline, not just at the start. Three
modes:

1. **Manual** (default). Every step, no matter how small, waits for an
   explicit go-ahead before the next one starts. Nothing runs unattended.
2. **Balanced.** Only consequential or hard-to-reverse steps wait for
   approval. Cheap, easily-undone steps run automatically — still producing a
   Status Report each time, just without pausing for it.
3. **Autopilot.** Runs the whole pipeline start to finish without stopping for
   approval on anything, then hands over one consolidated report at the end
   covering every step, every validation result, and anything that failed.
   Per-step Status Reports still get written along the way (for the trail),
   they just aren't shown one at a time — they're bundled into the final report.

**Default is Manual.** Switch modes any time the human says so — "switch to
autopilot," "just approve the big stuff," "back to manual" — and the new mode
takes effect starting with the next step. Always confirm the switch back in
plain language ("Switching to autopilot — I'll run everything and report back
at the end") so it's never ambiguous which mode is active.

If a step is genuinely destructive or hard to reverse in a real-world sense
(deleting data, spending money, publishing something publicly), flag that
explicitly in the Status Report regardless of mode — even in autopilot, the
final report should make failures and high-stakes actions impossible to miss,
not bury them in a wall of "everything went fine."

### What counts as "consequential"

A step is consequential/hard-to-reverse if undoing it costs real time, money,
or trust — deleting or overwriting something, sending something externally,
spending money, or any step whose output the next several steps build on
heavily. Everything else — drafting, generating a first pass, running a
read-only check — is cheap.

## Why these four (the three lenses behind the skill)

The Status Report's four fields aren't arbitrary — each one is where a
specific lens on the pipeline shows up in what the human actually sees.
Three lenses, each documented in full in its own reference file:

- **`references/usability.md`** — makes state legible: what happened, what it
  means, and how much oversight the human wants (the Modes system). Behind
  the "What just happened," "What it means," and "Gate" fields.
- **`references/engineering.md`** — makes correctness checkable: a definition
  of done per step, a real validation gate, and a graceful failure path.
  Behind the "Validation" field.
- **`references/product.md`** — makes progress visible: success metrics and
  what's been learned across runs. Behind metric mentions in "What it means"
  and the Autopilot summary report.

Read whichever reference file is relevant to what you're currently doing —
designing the report format, or debugging why a validation gate keeps
failing, or deciding what to measure. They're peers; none is a prerequisite
for the others, but together they're what the four fields are built from.

## Structuring the pipeline itself

When you design or build the pipeline (not just report on it), build in:

- **A definition of done per step.** Write it before the step runs, not after.
  Vague steps produce vague status reports.
- **A validation gate per step.** Something concrete that either passes or doesn't
  — a test, a check, a re-read of the output against the definition of done.
- **Graceful degradation on failure.** When a step's validation fails, the Status
  Report says so plainly, explains the likely cause, and proposes a fix or a
  rollback — it never just stops silently or buries the failure in a stack trace.
- **A confirmation gate that respects the active mode.** Manual waits every
  time; Balanced waits only for consequential steps; Autopilot never waits but
  still reports everything at the end. See "Modes" above.
- **A running success metric**, if the pipeline has one (time saved, tasks
  completed, error rate). Surface it in status reports so progress is visible,
  not just activity.

## Quick checklist

Before calling any step "complete":

- [ ] Definition of done was written before the step ran
- [ ] Validation gate ran and its result is known (pass/fail, not assumed)
- [ ] Status Report filled out (all four fields)
- [ ] If failed: cause + proposed fix included, not just the error
- [ ] Gate respected for the active mode (Manual: waited; Balanced: waited only
      if consequential; Autopilot: logged for the final report)

## Reference files

- `references/usability.md` — the usability lens: legibility, translation, control
- `references/engineering.md` — the engineering lens: validation, failure handling
- `references/product.md` — the product lens: success metrics, feedback loops
- `assets/status-report-template.md` — the literal template to fill in after each step
