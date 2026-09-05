---
name: coop
description: Coordinate cooperative coding sessions the user drives through explicit modes - do (complete clearly marked TODOs), try (stage a proposed change without editing code), check (report issues in applied changes), and diag (diagnose problems and propose a fix). Use only when the user invokes a coop mode by name or marker (for example /do, /try, !check, /diag); do not apply to ordinary coding requests.
---

# Coop

The user drives coding work through explicit cooperative modes rather than free-form requests.

This file is the router for the coop skill. Each mode has an authoritative companion file under `refs/`. WHen a mode is triggered:

1. Identify the triggered mode.
2. Read its corresponding `refs/<mode>.md` file first.
3. Follow that files `Description` and `Hint` sections literally.
4. Apply the shared rules below unless the companion file explicitly defines a stricter rule.

Do not substitute the behavior described here for the authoritative companion file.

## Modes

| Trigger | Instruction file | What to do |
| --- | --- | --- |
| `!do` / `/do` | `refs/do.md` | Some positions are marked as TODOs. Gather the necessary context and implement those TODO items. A clearly marked TODO must exist in recently modified content (for example, a #TODO comment); otherwise stop and request a specification. |
| `!try` / `/try` | `refs/try.md` | A clear implementation instruction needs an attempt. Do not modify source code directly. Instead, write the proposed change into `.agent/ref.*`, clearing stale content first, so the user can review and apply it. The target instruction must be identifiable from the current conversation context. |
| `!check` / `/check` | `refs/check.md` | Review changes that have already been applied, most likely changes discussed recently. Report findings in chat only. Make no modifications. |
| `!diag` / `/diag` | `refs/diag.md` | Diagnose the problem at the location or component identified by the user and propose a solution. Report in chat only. Make no modifications. |

## Shared rules

### Flash Response

Coop modesassume that the human has already supplied the relevant context and instruction.

Therefore:

- Act directly on the supplied context.
- Avoid broad repository exploration when the required context is already available.
- Do not perform unnecessary discovery merely to increase confidence.
- If genuinely necessary context is missing, ask briefly for exactly what is missing.

Offer fast and context-driven ops, not careless.
