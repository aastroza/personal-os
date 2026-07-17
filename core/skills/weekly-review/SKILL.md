---
name: weekly-review
description: A frank weekly evaluation that scores how your week actually went and pre-fills next week's planning template. Reads the real calendar (what happened), the approved plan (what was committed), your goals, and your learnings, then returns a verdict + a filled-in seed for next week. Use on "/weekly-review", "how was my week", "weekly retro", "weekly dashboard", or as the Step 0 input to a weekly planner. Read-only: never writes the calendar.
---

# Skill: weekly-review

**Goal:** give an honest read on the week that's ending — real vs. committed, vs. objectives, vs. learnings, vs. last week — and hand back a **pre-filled seed** so filling next week's plan is fast. This is the retro/dashboard that can feed a weekly planner's Step 0.

**Read-only.** Never creates, edits, colors or deletes calendar events. It only reads and writes markdown.

> Personalize by pointing the file references below at your own docs. A private, customized copy of this skill (with your real context) is what you install and consume; keep this generic template shareable.

## Inputs (read, don't dump)
1. **Real calendar** — the calendar of the week ending: what actually got scheduled and (where visible) what moved or dropped. This is "what happened".
2. **What was committed** — `WEEKLY_PLAN.md` (the approved plan + energy throttle). Source of truth is the markdown, not any seed note — once you approve, the plan lives in `WEEKLY_PLAN.md`.
3. **Objectives** — your goals doc (`GOALS.md`): did the week move the north star or just stay busy?
4. **Learnings** — `LEARNINGS.md`: which past pattern repeated or broke this week?
5. **Last week** — the prior entry: compare energy, one-outcome and load.

## Output — two parts

### Part A — The verdict (dashboard)
Short and frank. No empty optimism. Four cuts:
- **Real vs. committed** — of the P0/P1 committed, what got done, what slipped, and *why* (energy, interruptions, over-scoping).
- **Vs. objectives** — did the week advance the goals, or was it maintenance?
- **Vs. learnings** — which pattern from `LEARNINGS.md` showed up again (or was finally broken).
- **Vs. last week** — energy, load and one-outcome vs. last week (better / same / worse, one line each).
Lead with the single most important signal. Flag 🚩 what's at risk if it continues.

### Part B — Seed for next week (speeds up planning)
Pre-fill the inputs you'd otherwise type from scratch, marked as editable suggestions:
- **Suggested energy throttle (1–5)** — based on how the last 1–2 weeks actually went.
- **Carryover P0/P1** — what didn't get done and should roll forward (note if it should be dropped instead).
- **One-outcome candidates** — 1–2 "must-win" items tied to purpose/mastery, not just urgency.
- **Watch-outs** — any guardrail or eval that failed this week and must be protected next week.

Write Part B in the shape of `WEEKLY_PLAN.md` so the planner (or you) can drop it straight in.

## Rules
- **Don't invent.** If the calendar or plan doesn't show something, say "no data", don't guess.
- **Honest, not flattering.** Name what didn't work and why. No forced productivity.
- **Read-only.** Never touch the calendar. Markdown only.
- **Feeds the planner.** A weekly planner's Step 0 can read this skill's latest output instead of re-deriving the retro.

## How it runs
- **On demand:** `/weekly-review`.
- **Scheduled (optional):** as an automatic task before your weekly planning run.
