---
name: mem
description: Manage cross-session project memory through the scoped `!mem` namespace - `!mem init` (create the initial memory structure) and `!mem save` (confirm a milestone and record progress in the memory files). Use only when the user invokes the exact `!mem init` or `!mem save` command; ignore bare memory words and ordinary requests.
---

# Mem

This skill manages cross-session project memory through two scoped commands.

Each `!mem` sub command has an authoritative instruction file under `refs/`. When a command is triggered, read the corresponding file first and follow its `Description` and `Hint` sections literally.

## Commands

| Trigger | Instruction file | What to do |
| --- | --- | --- |
| `!mem init` | `refs/init.md` | The project has just been established. Create the memory structure (`.agent/` with `MEMORY.md`), then ask the user about the project's purpose if it is not already known. |
| `!mem save` | `refs/save.md` | The project has reached a milestone. Confirm the changes, then update the memory files to record the progress. If no `.agent/` memory structure exists, the project has not been initialized: stop and report. |

## Shared rules

- Only the exact commands `!mem init` and `!mem save` trigger this skill. Bare words such as `memory` or `save` do not.
- Read the existing memory files before editing so updates extend the recorded context instead of replacing it.
- Keep `MEMORY.md` concise and overview-level because it is read at the start of every session. Detailed changes, decisions, and history belong in the progress files.
- If a required precondition is missing—for example, no memory structure exists when handling !mem save—stop and report the problem. Do not guess or silently create missing structures.
