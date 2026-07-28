# MEMORY

> Durable context, not a transcript archive or second task manager.

The presence of this file at `me/memory/README.md` enables memory.

## What belongs here

- `people/` — collaboration context, preferences, durable responsibilities, and links to canonical tasks.
- `experiments/` — bounded trials and what they taught you.
- `decisions/` — choices whose rationale will matter later.
- `results/` — completed outcomes, verification, and learning.

Project state stays with each project under `me/projects/<stream>/`. Tasks stay in `BACKLOG.md`, project `TASKS.md`, or `WEEKLY_PLAN.md`.

## Operating rules

1. Capture only information likely to improve a future decision.
2. Update an existing canonical file before creating another.
3. Link related memories instead of copying them.
4. Separate facts from inference and mark uncertainty.
5. Use `last_verified` only when a time-sensitive fact was actually confirmed.
6. Ask before storing durable context unless the user explicitly said to remember it.
7. Never store secrets, credentials, raw private conversations, or sensitive personal dossiers.

## Review

Periodically ask:

- What is stale or contradictory?
- Which experiments lack a conclusion?
- Which decisions have been superseded?
- Which results lack verification?
- What should be consolidated or removed?

Propose changes before merging or deleting memory.
