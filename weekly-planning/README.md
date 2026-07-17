# Weekly Planning Engine (template)

An opinionated, self-improving weekly planning system for an AI assistant that plans your
week *with* you — learning from the gap between what you planned and what actually happened,
so each week's plan gets sharper than the last.

This folder is the **engine / methodology** — generic and publishable. It contains no personal
data. To use it, copy these templates and fill the `{{PLACEHOLDERS}}` with your own reality
(schedule, non-negotiables, goals). Your filled-in copies and your dated plans are **your
private data** and should live outside any public repo.

## What's here

- `SKILL.template.md` — the weekly ritual the assistant runs (e.g. every Friday): learn from
  last week, read the calendar, draft next week's plan, self-evaluate, hand off to daily ops.
- `behavior-spec.template.md` — the operable rules the planner obeys (Always Do / Never Do /
  tone / confidence thresholds / edge cases). This is what you *correct* when a plan misfires.
- `autonomy-map.template.md` — what the assistant may do alone vs. what needs your confirmation
  (L1 Review-All → L4 Full-Auto). Hard rules apply at every level.
- `evals.template.csv` — the pass/fail test set the planner grades each draft against before
  showing you. The exam; the behavior-spec is the student. ("No vibes, just evals.")
- `calendar-colors.template.md` — a category color code so your calendar is legible at a glance.
- `templates/weekly-note.template.md` — the weekly input note (goal, energy, learnings, priorities).
  Fill it each week as a phone note; tomorrow it can be an app's front-end form. Same methodology.
- `methodology.md` — the philosophy the system is built on, with sources.

## The loop (why it compounds)

```
Weekly note (your raw intent: goal, energy, learnings, priorities)
        ↓
Weekly Planner (scheduled run): learns from last week's gap → drafts next week
        ↓  handoff
Daily operating layer: runs the week, records what REALLY happened vs. plan
        ↓  feeds back
Learnings log (persists week over week — this is the compounding asset)
        ↺  planner reads it next cycle → more precise every time
```

The split matters: the **engine** (this folder) is the product/method; your **data** stays
private. Same seam a real app would need — methodology you can share, user data you never do.
