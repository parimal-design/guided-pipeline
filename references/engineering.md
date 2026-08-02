# The Engineering Lens

Why this lens: breaking work into steps is easy; the harder and more valuable
part is defining what "correct" looks like for each one, checking against it,
and handling it well when a step doesn't meet that bar. This lens is the
reasoning behind the Status Report's "Validation" field.

## Validation gates, not just task breakdown

A step isn't done because it ran without throwing an error — it's done when
its output has been checked against a definition of "correct" that was
written *before* the step ran. Write the definition of done first; vague
definitions produce vague validation, which produces vague status reports.

Maps to: the "Validation" field (✅/❌), and the "definition of done per step"
guidance in SKILL.md.

## Error recovery and graceful degradation

Something will eventually fail. The difference between a good pipeline and a
fragile one is what happens next: does it explain what broke and offer a path
forward, or does it just stop — or worse, continue silently in a broken
state? Build the failure path with as much care as the happy path: likely
cause, proposed fix or rollback, and never a bare stack trace standing in for
an explanation.

Maps to: the "❌ Failed" branch of the Validation field.

## Applying this lens to a new pipeline

- Define "done" for a step before the step runs, not after.
- Design the validation check alongside the step, not bolted on afterward.
- Plan the failure path as deliberately as the success path.
