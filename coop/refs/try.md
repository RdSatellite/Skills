# !coop try

> alias: `!try`

## Description

A clear implementation instruction has been received.

Attempt to solve the requirement, but do not modify the source code directly.

Instead, create a temporary `.agent/ref.md` (e,) file containing the proposed changes. There changes will be reviewed and applied seperately.

## Important

Direct modification of source code is strictly prohibited in this mode.

The `.agent/ref.md` file is the only place where the proposed implementation may be written.

## Hint

- Clear the file if any previous code exists in `.agent/ref.md` to keep the file clean.
- Usually, this command follows immediately after a certain explicit instruction and is only applicable to that particular instruction.
- If it is not possible to determine a specific instruction, **stop and ask for clarification**.
