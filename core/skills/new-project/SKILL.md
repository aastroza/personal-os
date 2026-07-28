---
name: new-project
description: Create or connect a PersonalOS project with a private project packet and optional repository-local agent instructions. Use when the user asks to start a project or stream, connect an existing code repository, scaffold a repository-backed project, or create project-level AGENTS.md guidance.
---

# New Project

Create the smallest durable project packet that future agents can discover. Keep project management in PersonalOS and technical truth in the repository.

## 1. Establish the scope

1. Read the root `AGENTS.md`, `core/templates/project.template.md`, and the user's goals and guardrails when available.
2. Choose a lowercase hyphenated slug and classify the project as `work`, `personal`, or `both`.
3. Identify whether the project has no repository, an existing repository, or a planned repository.
4. Use known facts and the user's request. Mark missing information as `→ fill when ready`; do not turn setup into a long interview.

If `me/projects/<slug>/` already exists, update the existing packet instead of creating a parallel one. Never overwrite files without inspecting them first.

## 2. Create the PersonalOS packet

Create `me/projects/<slug>/PROJECT.md` from `core/templates/project.template.md` and fill only supported fields.

Create `me/projects/<slug>/TASKS.md` when it does not exist, with empty `P0` through `P3` sections that follow the PersonalOS limits. Do not invent tasks.

The project overview owns durable state, focus, milestones, and source links. `TASKS.md` owns actionable project work.

For an AI project, this skill creates the project structure. Use `ai-project-framework` separately only when the user also wants eval, behavior-spec, and autonomy artifacts.

## 3. Connect a repository

For repository-backed work:

1. Record the repository, default branch, and links or named entry points for canonical setup, run, validation, CI, and deploy instructions in `PROJECT.md`. Keep executable commands in the repository README, manifests, or local `AGENTS.md`.
2. Inspect the repository README, existing agent instructions, build manifests, and CI configuration before documenting entry points or commands.
3. Keep code, issues, pull requests, CI logs, releases, and technical documentation in the repository. Link them from PersonalOS; do not copy them.
4. When repository-local setup is part of the request and `<repository-root>/AGENTS.md` does not exist, inspect other root instruction files before creating it from `core/templates/PROJECT_AGENTS.template.md`. If another instruction file exists, preserve it and ask whether to create a compatible pointer or reconcile shared guidance; do not create a parallel instruction set silently.
5. Include only sources and commands verified from repository evidence. Omit unknown rows or sections from `AGENTS.md` and report missing setup information to the user.
6. If an `AGENTS.md` already exists, preserve it. Propose focused additions only when the user asks.

## 4. Respect action boundaries

- Do not initialize Git, create a remote, branch, commit, push, open or merge a pull request, deploy, or release unless the user explicitly requests that action.
- Do not copy secrets or private PersonalOS content into a code repository.
- Do not create memory unless memory is enabled and the normal memory approval rules allow it.
- Use available Git or GitHub workflows when publishing is explicitly requested; do not recreate them inside this skill.

## 5. Report

Return the created or updated paths, the connected repository, any fields left for the user, and any external actions that were deliberately not taken.
