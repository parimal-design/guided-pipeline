## Status Report: Step [N], [step name]

**What just happened:**
[Plain-language description. No file paths, function names, or jargon unless the
user is technical and it's genuinely the clearest way to say it.]

**What it means:**
[The practical implication. Why should the user care, what changed for them?]

**Validation:**
[✅ Passed: brief description of what was checked]
[❌ Failed: what broke, likely cause, proposed fix or rollback]

**What's next:**
[The single next action, named specifically. Not "continue," say what the next
step actually is.]

**Gate (current mode: [Manual / Balanced / Autopilot]):**
[Manual: waiting for your word before starting the next step]
[Balanced, step is cheap: proceeding automatically, flagging here for visibility]
[Balanced, step is consequential: waiting for your word before starting the next step]
[Autopilot: proceeding automatically; this report is part of the final summary]

---

## Gut Check: end-of-pipeline / final report only

Not part of the per-step Status Report above. Run once, at the very end of
the pipeline (or right before Autopilot's consolidated report), comparing
the entire trajectory against the original goal, not the most recent step.

**Gut Check (end of pipeline):**
[✅ On track: the pipeline still serves the original goal: <one-line goal restated>]
[⚠️ Drift detected: <what changed vs. the original goal, plainly stated. No proposed fix, just flagging for you to decide.>]

---

### Example (filled in)

## Status Report: Step 2, Draft outline generated

**What just happened:**
I turned your notes into a five-section outline for the blog post.

**What it means:**
You have a structure to react to before I write full paragraphs. Easier to
redirect now than after a full draft exists.

**Validation:**
✅ Passed: every section maps to something you actually said in your notes;
nothing invented.

**What's next:**
Review the outline. Say the word and I'll write the full draft.

**Gate (current mode: Manual):**
Waiting for your word before starting the full draft. Easier to redirect now
than after a full draft exists.

### Example: Gut Check with drift detected

**Gut Check (end of pipeline):**
⚠️ Drift detected: you originally asked for a 500-word blog post outline;
across the last three steps this grew into a 2,000-word draft with two extra
sections you didn't ask for. Not proposing a fix, just flagging it so you can
decide whether to trim it back or keep the expanded scope.
