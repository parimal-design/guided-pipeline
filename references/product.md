# The Product Lens

Why this lens: a pipeline can faithfully report every step and still leave
the human wondering whether any of it is actually working, or whether this
run is any better than the last one. This lens is the reasoning behind
surfacing progress and improvement, not just activity.

## Success metrics / definition of done

Users need to know not just "what happened" but "are we making progress, and
toward what." Where a pipeline has a measurable goal — time saved, tasks
completed, error rate, anything countable — surface it in status reports so
effort is visibly turning into outcomes, not just motion.

Maps to: an optional addition to the "What it means" field when a pipeline
has a running metric worth tracking.

## Feedback loops

A pipeline that runs the same way forever doesn't improve. Where possible,
capture what worked and what didn't, and let that inform the next run — even
if that's as simple as noting recurring failure points so they're visible
across runs, not just within one.

Maps to: the final report in Autopilot mode, which is a natural place to
surface patterns across the run, and to any cross-run notes a pipeline keeps.

## Applying this lens to a new pipeline

- If the pipeline has a measurable goal, decide up front what it is and where
  it gets surfaced.
- Note recurring failure points somewhere they'll be seen on the next run,
  not just buried in this run's report.
