# CustomLabels.ini

You can give labels custom names that do not depend on the disassembler [configuration](../editor/options/formats.md#label-name-format). Those names are defined in the file `CustomLabels.ini` (one for each [edit mode](./#labels)).

## File Syntax

`<label offset>=<custom name>`

If the disassembler finds a label at the specified offset, this label gets the custom name.

To find out offset values enable the `CODE_OFFSETS` debug [option](../editor/console.md#code_offsets). After disassembling, a number in front of the script instruction is the offset value.
