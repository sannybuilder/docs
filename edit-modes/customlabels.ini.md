# CustomLabels.ini

You can give labels custom names that do not depend on the disassembler [configuration](broken-reference). Those names are defined in the file `CustomLabels.ini` (one for each [edit mode](./#labels)).

## File Syntax

`<label offset>=<custom name>`

If the disassembler finds a label at the specified offset, this label gets the custom name.

To find offset values, enable the [`CODE_OFFSETS`](../editor/debug-options.md#code_offsets) debug option. After disassembly, the number displayed before each script instruction represents its offset value.
