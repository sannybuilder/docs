# Disassembler

### Replace mission numbers

When this option is checked, the disassembler [replaces mission numbers](../features.md#replacing-mission-numbers-with-their-names) in `start_mission` with their names. The mission name is the label name defined in the file header. This name also could be used to quickly navigate to the mission code.

### Insert original mission names

When this option is checked, the disassembler adds the [mission title](../features.md#custom-mission-titles) as a comment for the opcode `start_mission` and for the line `DEFINE MISSION` in the file header.

### Disassemble with IF AND / IF OR&#x20;

Disassembler replaces the [number of conditions](../../language/control-flow/conditions.md#syntax) in the `IF` opcode with `AND` or `OR`

### Always overwrite output file

This option determines how the disassembler treats the output file when a file with the same name exists already. By default the disassembler keeps the existing file and creates a new one with the extra number in the name (e.g. `main[0].txt`).&#x20;

When this option is checked the disassembler replaces the existing file with a new file.

### Manual IMG opening

When the disassembling process starts, the program searches the file `script.img` containing some game scripts. If this file is not present in the same folder with the `.SCM` file or in the `San Andreas\data\scripts` folder, the error message is displayed. If this option is enabled, a file select dialog appears and you can provide another `script.img` file manually.

### Write opcodes

If this option is unchecked, the disassembler uses available [classes](../../language/instructions/classes.md) and [keywords](../../language/instructions/keywords.md) instead of opcodes. In addition, simple math expressions have no opcodes.&#x20;

If the option is checked, all opcodes are present in the output file.

### Add extra info to SCM

If this option is checked the compiler adds extra information at the end of the resulting file. This info is used later when this file gets disassembled to restore the source closer to the original. The following data is stored:&#x20;

* [HEX..END](../../language/instructions/hex..end.md) constructs offsets
* [global variables](../../language/data-types/variables.md#global-variables) names
* full source code (use [$NOSOURCE](../../language/directives.md#usdnosource) to disable)
* current [edit mode](../../edit-modes/)

{% hint style="info" %}
The file compiled with the extra information can not be open in Sanny Builder prior to v3.00 (unless the `ignore_unknown` [option](../console.md#ignore_unknown) is enabled).

Starting from v3.8.0 the disassembler can [ignore extra information](../console.md#skip_extra_info).
{% endhint %}
