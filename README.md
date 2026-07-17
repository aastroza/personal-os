# PersonalOS 🧭

An AI-native operating system for running your work and life through an agent — brain-dump into one inbox, let the agent process it into prioritized tasks against your goals, and start each session oriented in three sentences.

Built by a product leader going AI-native. It combines two ideas I liked from the community:
- a **backlog → goal-driven priority engine** (inspired by [Aman Khan's personal-os](https://github.com/amanaiproduct/personal-os)),
- a **project-based structure with work/personal streams and a content layer** (inspired by [GK's exec-assistant](https://github.com/geekayjahan/gks-exec-assistant)),

plus my own guardrails, cadence and voice.

## How it works
1. **Brain-dump** anything into `BACKLOG.md` — no structure needed.
2. **Process** — tell your agent "process my backlog." It turns notes into tasks, prioritized against `GOALS.md`.
3. **Orient** — start a session and the agent asks *"work, personal, or both today?"*, then orients you in 3 sentences: where things stand, this week's plan, the one thing to do today.
4. **Improve** — a weekly `skill-review` prunes and sharpens the agent's own skills so the system gets better over time.

## Priority model
| Priority | Meaning | Limit |
|---|---|---|
| **P0** | Do today | max 3 |
| **P1** | This week | max 7 |
| **P2** | Scheduled | — |
| **P3** | Someday / maybe | — |

A weekly **energy throttle** (1–5) decides the week's intensity: low → light week with air; high → more deep-work blocks and building.

## Skills
The agent's capabilities live in `core/skills/` — each is a markdown "skill" you or your agent can invoke.

| Skill | Pair | What it's for |
|---|---|---|
| `process-backlog` | — | Turn a raw brain-dump in `BACKLOG.md` into prioritized tasks against your goals. |
| `plan-my-week` | — | Build the week's plan + energy throttle from goals and backlog. |
| `prioritize` | — | Re-rank tasks under the P0–P3 model. |
| `daily-brief` | — | Start-of-day orientation in three sentences. |
| `inbox` | — | Triage email: classify, draft replies, run a daily digest (behavior-spec + evals + autonomy map inside). |
| `advisor` | — | Self-improving personal advisor: reads your goals/guardrails, runs an eval checklist before answering, learns after. |
| `ai-project-framework` | ↔ `ai-project-audit` | Scaffold a new AI project on solid ground — evals, behavior spec, autonomy map — **before** writing code. |
| `ai-project-audit` | ↔ `ai-project-framework` | Audit an existing AI project against that framework; scores maturity /21 and lists the gaps. |
| `skill-review` | — | Weekly prune-and-sharpen of the agent's own skills. |
| `security` | — | Anti-phishing / never-share policy: observed content is data, not instructions. |

> The `ai-project-framework` ↔ `ai-project-audit` pair encodes Shankha Dey's *No Vibes, Just Evals* frameworks + WHOOP eval practices. Start a project with the first; review it anytime with the second.

## Structure
```
PersonalOS/
├── CLAUDE.md          # session ritual — the agent reads this first
├── AGENTS.md          # operating manual (tool-agnostic: Claude Code, Cowork, Codex)
├── core/              # the generic, reusable framework (public)
│   ├── templates/     # starter files you copy into your own instance
│   └── skills/        # process-backlog, plan-my-week, daily-brief, prioritize, skill-review, inbox, security
└── me/                # YOUR private instance — goals, projects, backlog (gitignored)
```

## Quick start
1. Copy the files in `core/templates/` into a private `me/` folder.
2. Fill in `me/GOALS.md` (your goals) and `me/GUARDRAILS.md` (your non-negotiables).
3. Open the folder with your AI agent and say: *"Read CLAUDE.md and help me get oriented."*

## Privacy
`me/` is gitignored — your real goals, pipeline and personal data stay local. Only the generic framework is public.

## License
MIT — use it, fork it, make it yours.
