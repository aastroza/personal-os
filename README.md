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
4. **Remember (optional)** — enable `memory` to preserve decisions, results, experiments, corrections, and useful collaboration context.
5. **Improve** — a weekly `skill-review` prunes and sharpens the agent's own skills so the system gets better over time.

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
| `memory` | — | Capture, recall, correct, and review the minimum durable context that improves future decisions. |
| `new-project` | — | Create a project packet and connect it to an optional code repository without duplicating technical state. |
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
│   ├── templates/     # starter files, including the optional memory layer
│   └── skills/        # backlog, planning, brief, memory, reviews, inbox, security
└── me/                # YOUR private instance — goals, projects, backlog (gitignored)
```

## Quick start
1. Create a private `me/` folder.
2. Copy the root templates you need (`BACKLOG`, `GOALS`, `GUARDRAILS`, `POV_VOICE`, `PROJECT_HQ`, `STATUS`, `WEEKLY_PLAN`) from `core/templates/` into `me/`, removing `.template` from their filenames. For each project, copy `core/templates/project.template.md` to `me/projects/<stream>/PROJECT.md`. Skip the memory templates; they use the destinations below.
3. Fill in `me/GOALS.md` (your goals) and `me/GUARDRAILS.md` (your non-negotiables).
4. Open the folder with your AI agent and say: *"Read CLAUDE.md and help me get oriented."*
5. Enable memory later only if you want it.

Invoke `new-project` when starting a stream. It creates the private project packet and, when repository setup is in scope, can add a repository-local `AGENTS.md` from `core/templates/PROJECT_AGENTS.template.md`. It does not initialize Git, publish changes, or create pull requests unless you explicitly ask.

## Memory

Memory is a small durable-context layer inspired by [jxnl/personal-monorepo-template](https://github.com/jxnl/personal-monorepo-template). It is deliberately not a second task manager or a transcript archive:

- project state stays in each project's overview;
- tasks stay in `BACKLOG.md`, project `TASKS.md`, or `WEEKLY_PLAN.md`;
- people, experiments, decisions, and results live under `me/memory/`;
- existing canonical files are updated before new notes are created;
- incidental context requires approval before it is written;
- secrets, raw private conversations, and sensitive personal dossiers are excluded.

Memory is enabled only when `me/memory/README.md` exists. Without that file, agents skip memory reads, proposals, and writes.

Invoke `memory` to remember something, recall why a decision was made, correct stale context, close out meaningful work, or review what should be consolidated or removed. Behavior examples live in `core/skills/memory/EVALS.md`.

For developer projects, the code repository remains authoritative for source, issues, pull requests, CI, and releases. Memory keeps the operating context around that work—entry points, rationale, experiment conclusions, outcomes, and links to delivery evidence—without copying diffs or logs.

To enable memory:

1. Create `me/memory/` with `people/`, `experiments/`, `decisions/`, and `results/` inside it.
2. Copy `core/templates/MEMORY.template.md` to `me/memory/README.md`. This file is the enablement gate.
3. Create entries from the other templates only when you need them, using these destinations:

| Public template | Private destination |
|---|---|
| `MEMORY.template.md` | `me/memory/README.md` |
| `person.memory.template.md` | `me/memory/people/<slug>.md` |
| `experiment.memory.template.md` | `me/memory/experiments/YYYY-MM-DD-<slug>.md` |
| `decision.memory.template.md` | `me/memory/decisions/YYYY-MM-DD-<slug>.md` |
| `result.memory.template.md` | `me/memory/results/YYYY-MM-DD-<slug>.md` |

## Privacy
`me/` is gitignored — your real goals, pipeline, memory, and personal data stay local. Only the generic framework and empty templates are public. A private repository is still not a secret manager: keep credentials and authentication material out of memory.

## Cross-platform text

`.gitattributes` normalizes Markdown and CSV files to LF. `.editorconfig` asks compatible editors to use UTF-8, LF, and a final newline. Together they avoid text-format churn between Windows and macOS.

## License
MIT — use it, fork it, make it yours.
