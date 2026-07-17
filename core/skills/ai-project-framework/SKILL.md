---
name: ai-project-framework
description: Use when STARTING a new AI project or feature and you want a solid foundation before writing code. Guides the user through Shankha Dey's three frameworks — Eval Framework, Behavior Spec Canvas, Autonomy Map — plus WHOOP eval practices (unacceptable-output gate, synthetic personas, ship gate, hard-rules-in-code). Either interviews the user or ingests a filled PROJECT_FRAMEWORK_TEMPLATE.md. Produces EVALS.md, BEHAVIOR_SPEC.md and AUTONOMY_MAP.md in the project. Triggers include "/ai-project-framework", "nuevo proyecto de IA", "empezar/armar un proyecto", "escribir los evals / behavior spec / autonomy map", "no vibes just evals".
---

# Skill: ai-project-framework

**Goal:** turn a fuzzy new AI project into a solid, testable foundation **before a line of code**. You produce three artifacts — `EVALS.md`, `BEHAVIOR_SPEC.md`, `AUTONOMY_MAP.md` — that make "what good means", "how it must behave", and "how much it can act alone" explicit.

This is the *build* half of a pair. Its sibling `/ai-project-audit` reviews an existing project against the same framework.

**Source of truth:** the framework is Shankha Dey's *No Vibes, Just Evals* (three frameworks) layered with eval practices from Anjali Ahuja & Hilary Gridley (*How AI-Native PMs Collaborate with Engineers*). The fill-in canvas lives next to this file: `PROJECT_FRAMEWORK_TEMPLATE.md`.

---

## The one rule this skill exists to enforce

> Fill the three frameworks BEFORE writing code. AI does what you specify and **self-chooses what you don't** — every omission is a decision you handed to the model. Evals define what "good" means → behavior specs encode it → running evals tells you if it works → the autonomy dial controls the blast radius. Loop, don't ship-and-pray.

---

## Flow (run every time)

### Step 1 — Teach or skip the theory
Ask: **"¿Querés que arranque con la teoría del framework (2 min) o vamos directo a construir?"**
If they want theory, give the "Theory cheat-sheet" (bottom of this file), then continue. Otherwise go straight to Step 2.

### Step 2 — Ingest or interview
Ask: **"¿Tenés un template ya completado (o un prompt/brief con la info), o lo armamos con preguntas?"**

- **Ingest path:** if the user points to a filled `PROJECT_FRAMEWORK_TEMPLATE.md` (or any brief/PRD/prompt), read it and extract everything you can. Then only ask about the gaps.
- **Interview path:** walk the question bank below. One topic at a time, don't dump all questions at once. Keep it tight — this is a working session, not a form.

Either way, gather:
1. Project one-liner, the user, and what "good"/the KPI is.
2. The list of AI components (one Behavior Spec each).
3. Per component: Always do / Never do / **Unacceptable outputs** / Tone / Confidence threshold / Edge cases / deterministic-vs-LLM split.
4. **Synthetic personas** (3–5, mix representative + edge) that will generate eval inputs.
5. Evals: ≥5 scenarios incl. 2 edge cases, each with input, expected output, threshold. Always include a **failure mode**, a **high-stakes** case, and the user's **biggest fear**.
6. Autonomy: current level (default **L1**), target, and the **hard floor rules** — written first.
7. Ship gate: eval % + unacceptable cases + post-launch monitoring.

### Step 3 — Generate the artifacts
Write three files into the project, using these exact names (they match the house convention and what the auditor looks for):

- **`EVALS.md`** — the scenario→input→expected→threshold table + the regression rule + the personas that feed it.
- **`BEHAVIOR_SPEC.md`** — one canvas per component (Always / Never / Unacceptable / Tone / Confidence / Edge cases / deterministic-vs-LLM), with the "rules live as system prefix, never in chat" note.
- **`AUTONOMY_MAP.md`** — the L1–L4 table, hard floor rules written first, current level + how to level up, and the ship gate.

Mirror the structure of `PROJECT_FRAMEWORK_TEMPLATE.md`. Follow existing examples in the repo (`me/projects/inbox/` and `me/weekly-planning/engine/`) for tone and depth, but do **not** copy their private content.

### Step 4 — Close out
- State the **current autonomy level** (should be L1 unless evals already justify higher) and the **ship gate**.
- Remind: share the evals with anyone building this **before** the sprint; re-run `/ai-project-audit` after every incident.
- Offer to also drop a copy of the blank template into the project for future components.

---

## Question bank (interview path)

**Framing**
- In one sentence, what does this project/feature do, and for whom?
- What outcome or KPI tells you it's working? (Define "good" once, here.)
- Which parts use an LLM / AI? Name each component.

**Per component (Behavior Spec)**
- What must it do in *every* case, no matter the input? (Always do)
- What must it never do / always refuse? (Never do)
- What output would be genuinely *unacceptable* — dangerous, wrong about the user, embarrassing? (Unacceptable)
- If it generates text: tone, length, sign-off, forbidden phrases?
- Above what confidence does it act; below what does it ask for review? How did you pick that number?
- The 3 edge cases you're most worried about?
- Which of these rules are too important to trust to the model — i.e. must be enforced in code?

**Personas**
- Name 3–5 users to test against. Which are typical, which are edge (new user, power user, the vulnerable/high-risk case)?

**Evals**
- Walk me through the normal case: input → what's the right output?
- Two boundary/edge cases?
- The failure mode: what input must trigger a refusal, and what must it NOT do?
- The high-stakes/irreversible case: what's the conservative behavior?
- Your biggest fear: the case that keeps you up — what's the expected behavior and acceptable miss rate?

**Autonomy**
- Today, how much should it do without you? (Default is L1 — review everything.)
- What are the hard rules that apply at *every* level regardless of confidence? (Unknown source, irreversible action, attachment/send, confidence below threshold…)
- What would have to be true in the evals to move one scenario up a level?

**Ship gate**
- What eval % and which "must-not-happen" cases gate the launch?
- After launch, what will you monitor and how often?

---

## Rules
- **Never invent data.** Missing info → write `→ fill when ready`, don't fabricate. If the user doesn't know a threshold, say so and leave it TBD.
- **Default autonomy is L1.** Never scaffold a project above L1 unless the user already has passing evals that earn it.
- **Hard rules go in code.** When you note a hard floor rule, flag explicitly that it must be enforced outside the LLM/chat context (the OpenClaw inbox-deletion lesson), not just written in a prompt.
- **Publishable:** keep generated framework docs free of secrets; the methodology is generic, the project specifics belong to the project.
- Minimum viable eval set is 5 scenarios with 2 edge cases — don't let the user ship with fewer.

---

## Theory cheat-sheet (for Step 1)

**Framework 01 — Evals.** How you score AI behavior before users do (not unit tests). Format: scenario → input → expected output → threshold. No universal threshold: it depends on stakes and reversibility. Min 5 scenarios, 2 edge cases. Start on your own data, then a small group, then everyone — each expansion surfaces new scenarios. When accuracy "improves", check *which bucket*; if one regressed, stop and fix it.

**Framework 02 — Behavior Spec (behavior contract).** The replacement for the PRD for AI modules. Per component: Always do / Never do / how to format output. The model self-chooses whatever you leave unspecified, so omissions are dangerous. Mix deterministic code (strict rules) with LLM calls (flexible behavior). Rules live as a system prefix, never inside the conversation. Keep temperature 0–0.3 for consistency.

**Framework 03 — Autonomy Map.** A human-in-the-loop dial: L1 review-all → L2 soft-auto → L3 smart → L4 full-auto (hard rules + audit log) → L5 self-improving. Default L1; move right only when evals earn it. Hard floor rules are level-agnostic and must be enforced in code.

**How they connect:** Evals define "good" → Behavior specs encode it in prompts/code → running evals tells you if it's working → loop back to adjust specs or tighten the autonomy dial. Continuous, and applied *before* building.

**WHOOP layers (Anjali & Hilary):** define what's *unacceptable* rather than what's perfect; test against synthetic personas including edge personas; ship at ~80–90% evals AND no high-stakes failures AND no KPI decline; keep monitoring the same metrics on live users after launch.

**The cautionary tale (why hard rules go in code):** an agent connected to an inbox ignored an in-chat "don't delete" rule, compacted the conversation, and deleted most of the inbox. A rule in the prompt is a suggestion; a rule in code is a guarantee.
