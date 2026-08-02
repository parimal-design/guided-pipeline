# The Usability Lens

Why this lens: a pipeline can be technically flawless and still be unusable if
the human running it can't tell what's happening. This lens is about making
state legible — it's the reasoning behind the Status Report's "what just
happened," "what it means," and the Modes system.

Built on three of Jakob Nielsen's usability heuristics.

## 1. Visibility of system status

The user should always know what state the system is in, without going
looking for it. After every step, say what happened and what's next — never
require someone to open files, read logs, or re-run something just to find
out where they are.

Maps to: the "What just happened" and "How we'll know it worked" fields.

## 2. Match between system and the real world

Speak the user's language, not the system's. A pipeline built by an AI tends
to report in terms of files touched or internal step numbers. A human wants
to know what that means for them — "your draft is ready to review," not
"step 4a completed, output written to /tmp/stage4.json." Translate before
reporting; briefly explain a term rather than assuming familiarity.

Maps to: the "What it means" field, and the tone of the report generally.

## 3. User control and freedom

People should be able to stop, undo, or redirect before anything happens.
"Control" isn't one fixed level of hand-holding — different people, and the
same person on different pipelines, want different amounts of oversight.
This is why the skill offers three modes (Manual / Balanced / Autopilot) the
human can switch between at any time, rather than a single hardcoded gate.

Maps to: the Modes system and the "Gate" field in the Status Report.

## Applying this lens to a new pipeline

- Write status in the user's terms before you write it in the system's terms.
- Never let a completed step go unreported, regardless of which mode is active.
- Default to the most conservative mode (Manual); let the human loosen it.
