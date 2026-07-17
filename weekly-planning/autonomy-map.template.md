# Autonomy Map — Weekly Planning (template)

> Defines what the assistant may do alone vs. what needs your confirmation.
> On conflict, this map wins over the behavior-spec and any preference.
> Hard rules (✓) apply at EVERY autonomy level.

## Default level
**L1 / Review-All.** Every weekly plan stays a draft for your review before any event is
created, edited, or deleted.

## Scenarios

| Trigger | L1 — Review All | L2/L3 — Soft/Smart Auto | L4 — Full Auto | Hard rule |
|---|---|---|---|---|
| Generate weekly plan (markdown) | Auto-draft for review | Auto-draft | Auto-draft | |
| Suggest new blocks in the plan | Allowed as suggestion | Allowed | Allowed | |
| Read calendar to plan | Allowed | Allowed | Allowed | |
| Read project/context notes | Allowed | Allowed | Allowed | |
| Scan inbox for actions/reading | Allowed | Allowed | Allowed | |
| Create events | Needs confirmation | Auto only if explicitly enabled | Auto only if explicitly enabled | ✓ |
| Edit/move events | Needs confirmation | Auto only if explicitly enabled | Auto only if explicitly enabled | ✓ |
| Fix event colors | Auto if color system consulted | Auto | Auto | |
| Delete events | Literal confirmation required | Same | Same | ✓ |
| Non-primary calendars | Forbidden | Forbidden | Forbidden | ✓ |
| Missing weekly energy | Ask / mark Decision | Same | Same | ✓ |
| Missing critical family/health/interview info | Mark Decision | Same | Same | ✓ |
| Medical action or advice | Don't advise; transcribe/organize and refer to the professional | Same | Same | ✓ |
| Sensitive financial action | Don't execute; mark Decision | Same | Same | ✓ |
| Automatic scheduled run | Only prepare the markdown draft; never create/edit/color/delete events | Same | Same | ✓ |

## Rule
The system starts at L1. It only moves to L2/L3 on specific tasks once the evals prove
reliability. Hard rules apply at all levels: no autonomy level skips them.
