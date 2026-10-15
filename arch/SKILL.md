---
name: arch
description: Carry out architecture-level changes through the scoped `!arch` namespace - `!arch move` (alias `!mv`, relocate a file or block the user has decided to move, together with every related change), `!arch sop` (alias `!sop`, turn extension points the user explicitly provides into standardized, reusable SOP skills under `agent/ext/`), and `!arch extern` (alias `!ext`, apply an architectural extension by following the SOP skill that already covers it). Use only when the user writes one of these exact forms; ignore bare mode words and ordinary requests to move files, restructure, or refactor.
---

# Arch

The user drives architecture-level work through a single scoped namespace - `!arch move`, `!arch sop`, or `!arch extern` - instead of free-form requests. These commands act on structure rather than on local implementation detail: they relocate code between places, turn declared extension points into repeatable procedures, and carry out those procedures.

This file is the router for the arch skill. Each mode has an authoritative companion file under `refs/`, relative to this `SKILL.md`. When a mode is triggered:

1. Identify the triggered mode.
2. Read its corresponding `refs/<mode>.md` file first.
3. Follow that file's `Description` and `Hint` sections literally.
4. Apply the shared rules below unless the companion file explicitly defines a stricter rule.

Do not substitute the behavior described here for the authoritative companion file.


## Modes

| Trigger | Alias | Instruction file | What to do |
| --- | --- | --- | --- |
| `!arch move` | `!mv` | `refs/move.md` | The user has decided to move the specified file or block to a certain location. Identify all the related changes that may arise from the move and make them at the same time. The object to be moved and its destination must be inferable from the instruction; otherwise stop and ask. |
| `!arch sop` | `!sop` | `refs/sop.md` | Convert the architectural extension points the user explicitly provided into standardized, reusable SOP skills stored in `agent/ext/`. Treat the existing abstract architecture as the basis for extension boundaries, responsibilities, and integration procedures. |
| `!arch extern` | `!ext` | `refs/extern.md` | The user has decided to apply an architectural extension. Follow the SOP skill that already covers this extension point, keeping to the boundaries it defines, instead of designing an implementation yourself. The extension and its SOP skill must be identifiable from the instruction or the current conversation; otherwise stop and ask. If no SOP skill exists for it, stop and report and point the user to `!arch sop`. |

## Shared rules

### The decision is the source of truth

All three modes operate on a decision the user has already made, not on one you infer.

- What the operation acts on must be identifiable without guessing: the object and its destination (`move`), the extension points (`sop`), or the extension and the SOP skill covering it (`extern`).
- Guessing is forbidden. If required information is missing, stop and ask for exactly what is missing.
- Operationalize what was decided. Do not redesign, extend, or improve the architecture along the way.
- In `extern`, that decision is already recorded in the SOP skill. Follow it rather than designing the extension yourself.

### Related changes only

- The project may be in an unstable or uncompileable state. Do not attempt to make it compile.
- Make only the associated changes caused by the operation itself - for example references to a moved location, the integration procedure a generated skill plugs into, or the procedure an SOP skill prescribes.
- Never touch unrelated code, and do not treat this as an opportunity for a broader refactor.
