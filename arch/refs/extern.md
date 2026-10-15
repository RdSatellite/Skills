# !arch extern

> alias: `!ext`

## Description

The user has decided to apply an architectural extension. Carry it out by following the SOP skill that already covers this extension point, stored in the `agent/ext/` directory.

That SOP skill—not your own design—is the source of truth for how the extension is implemented. Follow its procedure, keep to the architectural boundaries it defines, and implement the extension as it describes.

## Hint

- The extension to be performed and the SOP skill covering it should be able to be inferred from the instruction or the current conversation. Otherwise, **stop and ask**.
- If no SOP skill exists for the extension point, it has not been designed yet. **Stop and report**, and point the user to `!arch sop` to create it first.
