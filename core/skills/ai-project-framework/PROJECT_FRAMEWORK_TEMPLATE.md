# AI Project Framework — Pre-Build Canvas

> Fill this in **before you write a single line of code**. Based on Shankha Dey's *No Vibes, Just Evals* (three frameworks) + eval practices from Anjali Ahuja & Hilary Gridley (*How AI-Native PMs Collaborate with Engineers*).
>
> **How to use:** answer every field. Keep unknowns as `→ fill when ready` — never invent. When done, drop this file into the project and run `/ai-project-framework` (it will ingest it and generate `EVALS.md`, `BEHAVIOR_SPEC.md`, `AUTONOMY_MAP.md`). Re-run `/ai-project-audit` after every incident.

---

## 0. Project one-liner

- **What is this project / feature, in one sentence?**
  → …
- **Who is it for (the user)?**
  → …
- **What does "good" mean here — which outcome/KPI moves if it works?** *(WHOOP: define "good" once = moves the KPI, not per-feature vibes.)*
  → …
- **AI components in scope** *(one Behavior Spec per component below — e.g. classifier, drafter, summarizer):*
  → …

---

## 1. EVALS — What does "good" mean? *(Framework 01)*

> Score AI behavior before your users do. Format: **scenario → input → expected output → threshold**. No universal threshold — it depends on stakes, reversibility, and the human-parity bar. Minimum **5 scenarios**, include **2 edge cases**. Start with your own data (I → we → everyone).

| # | Scenario | Input (example) | Expected output | Threshold |
|---|----------|-----------------|-----------------|-----------|
| 1 | **Normal case** — typical input | … | … | >90% |
| 2 | **Edge case 1** — boundary input | … | … | >80% |
| 3 | **Edge case 2** — another boundary | … | … | >80% |
| 4 | **Failure mode** — input that must trigger refusal | … | Should NOT do X | 0% auto |
| 5 | **High stakes** — input with irreversible consequences | … | Conservative behavior | 100% review |
| 6 | **Your biggest fear** — the case you dread most | … | … | ~0% miss |

**Regression rule:** when accuracy "improves," ask *which bucket* improved. If any bucket regressed, stop and fix the regression before shipping.

---

## 2. SYNTHETIC PERSONAS — Who generates the eval inputs? *(add-on: WHOOP)*

> WHOOP runs evals against ~300 synthetic personas built from slices of real user data, including edge personas (day-zero user, 5+ year user, pregnant user). List **3–5** you'll test against — mix representative + edge. Post-launch, monitor the same eval metrics on live users.

| Persona | Slice / who they represent | Why they stress the system (edge?) |
|---------|----------------------------|-------------------------------------|
| 1 | … | representative |
| 2 | … | representative |
| 3 | … | edge |
| 4 | … | edge |

---

## 3. BEHAVIOR SPEC CANVAS — one per AI component *(Framework 02)*

> Plain language. Completed before a line of code. These rules live as a **system prefix / policy**, never inside the chat context. Copy this block for each component.

### Component: `<name>`
**What it does (1 sentence):** …

- **ALWAYS DO** — non-negotiable behaviors, every case, regardless of input:
  → …
- **NEVER DO** — hard stops; what it must refuse or avoid regardless of input:
  → …
- **UNACCEPTABLE OUTPUTS** *(add-on: Anjali — define what's unacceptable, not just what's perfect)* — outputs that must never appear (dangerous suggestion, factual error about user data, etc.):
  → …
- **TONE / VOICE** *(if it generates text)* — style, length, sign-off, forbidden phrases:
  → …
- **CONFIDENCE THRESHOLD** — below X% → review; above X% → proceed. How did you pick X?
  → …
- **EDGE CASES** — the 3 scenarios you're most worried about, written explicitly:
  → …
- **DETERMINISTIC vs LLM** — which rules are enforced in code (hard) vs left to the LLM (flexible)? *(Temperature 0–0.3 for consistent output.)*
  → …

---

## 4. AUTONOMY MAP — How much can it act alone? *(Framework 03)*

> The dial controls the blast radius. **Default = L1.** Move right only when your evals earn it. Hard rules (✓) apply at **every** level — no confidence score overrides them.
>
> L1 Review all · L2 Soft auto (high-conf + known auto, rest review) · L3 Smart (auto most; review low-conf/unknowns) · L4 Full auto (hard rules + audit log) · L5 Autonomous/self-improving (extreme caution).

- **Current level:** L… — because …
- **Target level & what would earn it:** …

| Scenario / Trigger | L1 | L2/L3 | L4 | Hard rule |
|--------------------|----|-------|----|-----------|
| Normal, known input | Draft → review | Auto if >X% | Auto | |
| Unknown source/sender | Review | Review | Review | ✓ |
| Irreversible action (calendar / financial / delete / send) | Review + sign-off | Review + sign-off | Review + sign-off | ✓ |
| Confidence < threshold | Review | Review | Review | ✓ |
| `<your scenario>` | … | … | … | |

### Hard floor rules (write these FIRST — the floor beneath all levels)
> **These must be enforced in code, outside the LLM/chat context.** The OpenClaw lesson: a hard rule kept inside the chat is treated as a fungible instruction — an agent ignored an in-chat rule, compacted the conversation, and deleted most of an inbox. Rules in the prompt are suggestions; rules in code are guarantees.

1. …
2. …
3. …

**How to level up:** run the EVALS on a real batch; if no bucket regressed and behavior held, only then move *one* low-risk scenario up a level. Never jump for convenience.

---

## 5. SHIP GATE — go / no-go *(add-on: WHOOP)*

- **Ship when:** ≥ **80–90%** on evals **AND** no high-stakes failure scenarios are appearing **AND** no stat-sig decline on the target KPI.
- **Do NOT ship if:** any hard-rule scenario fails even once, or a high-stakes/"biggest fear" case triggers.
- **Post-launch:** monitor the same eval metrics on live users; review results (e.g. twice a week); feed failures back into EVALS.

---

## THE RULES (checklist)

- [ ] EVALS: at least 5 scenarios, 2 edge cases, thresholds set, shared with the team **before** the sprint.
- [ ] BEHAVIOR SPEC: one canvas per component, plain language, ALWAYS/NEVER/UNACCEPTABLE filled, done before any code.
- [ ] AUTONOMY MAP: level set before architecture, hard rules written first and enforceable **in code**.
- [ ] SHIP GATE: threshold + unacceptable-cases defined; post-launch monitoring planned.
