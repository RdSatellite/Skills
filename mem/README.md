# Memory Skill Bundle

A set of skills for managing project memory across sessions.

They are:

- `!mem init`: Initialize the memory structure.
- `!mem save`: Confirm changes and record progress.

## Memory Structure

To manage project memory effectively, the bundle uses at least two types of files::

1. `MEMORY.md`, the main memory. The main memory file provides a concise overview of the project: what it is for, what we want to accomplish, and the overall development process.MEMORY.md is read at the beginning of every new session, so it should remain concise and contain only information that is broadly useful for understanding the project.
2. `Progress Files`, the detailed history. Progress files contain detailed records of changes, decisions, and completed work. They are archived under `.agent/progress/`. Their locations are listed in `MEMORY.md`, allowing us to review detailed history when needed without loading everything into the main memory at once.
