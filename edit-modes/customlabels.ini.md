# CustomLabels.ini

You can give labels custom names that do not depend on the disassembler [configuration](../editor/options/formats.md#label-name-format). The names are specified in the file `CustomLabels.ini` \(one for each edit mode\).

File syntax:  
`<label offset>=<custom name>`

If the disassembler finds a label at the specified offset, this label gets the given custom name.

To find out the offset value change the labels format to [`Global Offset`](../editor/options/formats.md#global-offset) in the options. After disassembling, a number in the label name is the offset value.

