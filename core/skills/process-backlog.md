# Skill: process-backlog

**Trigger:** "process my backlog" / start of week / cuando entra un item nuevo a mitad de semana.

**Goal:** turn raw notes in `me/BACKLOG.md` into prioritized, actionable tasks — priorizadas
contra **dos horizontes a la vez**: las metas estables (`me/GOALS.md`) y el **contrato vivo de esta
semana** (`me/WEEKLY_PLAN.md`), aplicando lo aprendido (`me/WEEKLY_LEARNINGS.md`).

> Por qué: GOALS es el "siempre" (trimestral). Priorizar solo contra GOALS produce tareas
> correctas para el trimestre pero ciegas a la semana. El backlog tiene que aterrizar en la
> realidad de ESTA semana — su outcome, su energía, su experimento — y no re-aprender de cero
> lo que ya sabés de vos mismo.

## Contexto que se lee ANTES de priorizar (cable de entrada)
1. `me/BACKLOG.md` — los items crudos a procesar.
2. `me/GOALS.md` — el north star estable (jerarquía de prioridades + weighting de la fase).
3. `me/WEEKLY_PLAN.md` — el contrato vivo. Leer específicamente:
   - **The one outcome of the week** — nada del backlog puede desplazarlo.
   - **Energy throttle (1–5)** — throttle bajo ⇒ sé conservador metiendo cosas nuevas; alto ⇒ hay aire.
   - **Experimento de la semana** — no generes tareas que lo contradigan (ej. si el experimento es
     timeboxing, no bajes 5 tareas Claude-heavy sueltas).
   - **Cuánto P0/P1 ya está ocupado** — los caps (P0≤3, P1≤7) vienen **medio llenos** del planner.
     Contá los slots libres reales antes de prometer nada.
   - **Innegociables + Radar** — no pisar lo protegido; lo que es de otra semana va al Radar, no a esta.
4. `me/WEEKLY_LEARNINGS.md` (solo el tope) — el último **"Ajuste que aplico"** y el **"Patrón
   recurrente"**. Es la lente: aplicá el ajuste de la semana en vez de re-descubrirlo el viernes.

## Steps
1. Leer los 4 insumos de arriba (backlog + goals + weekly plan + learnings).
2. Para cada item: clarificar a una acción concreta (verbo + outcome). Tirar duplicados y ruido.
3. Asignar **stream** (`ai-native-build`, `job-search`, `investing`, o item de vida → Weekly Planning)
   y **prioridad** (P0–P3), evaluando contra GOALS **y** contra el contrato de la semana + learnings.
   Después de identificar el stream, leer su overview y solo las decisiones/resultados relevantes de
   `me/memory/` cuando puedan cambiar la clasificación. No cargar todo el árbol de memoria.
4. **Reconciliar contra el plan vivo, no dumpear en paralelo (cable de salida):**
   - Si el item se gana un slot de ESTA semana → entra al P0/P1 de `me/WEEKLY_PLAN.md`. Como los caps
     ya vienen medio llenos, si no hay slot libre, **algo se baja** — decilo explícito y por qué
     (contra el one outcome + throttle + learnings).
   - Si no se gana la semana → va al `me/projects/<stream>/TASKS.md` del stream como "next", y al
     **Radar** del WEEKLY_PLAN si no hay que dejarlo caer. No lo metas a la fuerza en la semana.
5. Enforce caps sobre el total de la semana: **P0 ≤ 3, P1 ≤ 7** (el conteo incluye lo que ya puso el
   planner). Si el backlog empuja por encima, el más débil cae a P2/P3 con motivo.
6. **Dejar rastro (cable de retorno):** todo movimiento que toque el plan vivo a mitad de semana
   (item que entró, algo que se bajó, reprioridad) se anota en **una línea** en la sección
   **"Real vs. planeado"** de `me/WEEKLY_PLAN.md`. Esa es la materia prima que el planner destila el
   viernes a `WEEKLY_LEARNINGS.md`; si no queda rastro, el aprendizaje se pierde (falla observada
   semana 13–17 Jul: la sección quedó vacía).
7. Limpiar de BACKLOG los items procesados.
8. Resumir: qué entró a la semana (y qué se bajó, por qué), qué fue a TASKS.md/Radar, y la una cosa
   para empezar ahora.

**Rules:**
- No inventar tareas; si un item es ambiguo, preguntá una cosa o marcá `→ fill when ready`.
- El **one outcome** de la semana es intocable por el backlog.
- Respetá el **throttle**: energía baja no se compensa metiendo más backlog.
- Los caps se cuentan sobre el **total de la semana**, incluyendo lo que ya puso el planner — no
  arranques de cero.
- Una tarea procesada nunca se convierte en memoria por el solo hecho de ser importante. Si el
  procesamiento revela una decisión, corrección o contexto durable, aplicar `core/skills/memory/SKILL.md`
  y pedir aprobación salvo que el usuario haya dicho explícitamente que lo recuerdes.
