---
name: coop
description: Coordinate cooperative coding sessions through the scoped `!coop` namespace - `!coop do` (complete clearly marked TODOs), `!coop try` (stage a proposed change without editing code), `!coop check` (review applied changes), and `!coop diag` (diagnose a problem and propose a fix). Use only when the user writes one of these exact `!coop <mode>` forms; ignore bare mode words such as do or check, and never apply coop behavior to ordinary coding requests.
---

# Coop

The user drives coding work through a single scoped namespace - `!coop do`, `!coop try`, `!coop check`, or `!coop diag` - instead of free-form requests.

This file is the router for the coop skill. Each mode has an authoritative companion file under `refs/`, relative to this `SKILL.md`. When a mode is triggered:

1. Identify the triggered mode.
2. Read its corresponding `refs/<mode>.md` file first.
3. Follow that file's `Description` and `Hint` sections literally.
4. Apply the shared rules below unless the companion file explicitly defines a stricter rule.

Do not substitute the behavior described here for the authoritative companion file.


## Modes

| Trigger | Instruction file | What to do |
| --- | --- | --- |
| `!coop do` | `refs/do.md` | Some positions are marked as TODOs. Gather the necessary context and implement those TODO items. A clearly marked TODO must exist in recently modified content (for example, a #TODO comment); otherwise stop and request a specification. |
| `!coop try` | `refs/try.md` | A clear implementation instruction needs an attempt. Do not modify source code directly. Instead, write the proposed change into `.agent/ref.*`, clearing stale content first, so the user can review and apply it. The target instruction must be identifiable from the current conversation context. |
| `!coop check` | `refs/check.md` | Review changes that have already been applied, most likely changes discussed recently. Report findings in chat only. Make no modifications. |
| `!coop diag` | `refs/diag.md` | Diagnose the problem at the location or component identified by the user and propose a solution. Report in chat only. Make no modifications. |

## Shared rules

### Flash Response

Coop modes assume that the human has already supplied the relevant context and instruction.

Therefore:

- Act directly on the supplied context.
- Avoid broad repository exploration when the required context is already available.
- Do not perform unnecessary discovery merely to increase confidence.
- If genuinely necessary context is missing, ask briefly for exactly what is missing.

Offer fast and context-driven ops, not careless.
