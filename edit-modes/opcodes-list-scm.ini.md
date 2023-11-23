# Opcodes List (SCM.INI)

{% hint style="success" %}
Opcodes documentation can be found in [Sanny Builder Library](https://library.sannybuilder.com/).
{% endhint %}

`SCM.INI` is the file containing information about opcodes used during disassembling and compiling script files. Sanny Builder ships a list of opcodes for each [edit mode](./#opcodes).

{% hint style="info" %}
Starting v4.0, this file is optional and can be substituted with the new definition files available for download in [Sanny Builder Library](https://library.sannybuilder.com/). New SBL edit modes use only JSON files.
{% endhint %}

| Game                 | File Name  | Location        |
| -------------------- | ---------- | --------------- |
| GTA III              | SCM.INI    | data\gta3       |
| Vice City            | VCSCM.INI  | data\vc         |
| San Andreas          | SASCM.INI  | data\sa         |
| Liberty City Stories | LCSSCM.INI | data\lcs        |
| Vice City Stories    | VCSSCM.INI | data\vcs        |
| VC Mobile            | VCSCM.INI  | data\vc\_mobile |
| SA Mobile            | SASCM.INI  | data\sa\_mobile |

## File Format

Lines starting with `;` are ignored.

### Metadata

Special INI parameters provide metadata information about the opcodes list.

`VERSION` – defines the version of this file. See the [$VERSION](../language/directives.md#usdversion) directive\
`PUBLISHER` – who authored this version \
`DATE` – the update date. \
\
The disassembler prints the metadata in the first line of the output file.

### Opcode Definition

Each line has the following syntax:

`xxxx=N, yyyy` \
`XXXX` – the opcode number\
`N` – the number of parameters\
`yyyy` – the opcode description.

The opcode number and the number of parameters are final and can't be changed. The description is open to modifications.

If the INI file contains multiple definitions for the same opcode, the latter controls.

By convention a description for a conditional opcode starts with two spaces.

### Opcode Parameters

A parameter is a dynamic part of the opcode. They start and end with `%`&#x20;

```
0001=1,wait %1d% ms
```

This line is the definition of the opcode `0001`. When the disassembler finds `0001` in a script it prints the words`wait` and `ms` with the parameter value in-between to the output file.

A parameter consists of two parts: a `number` and a `type`.

#### Parameters Order

The number in parameter `%1d%` is its index. The idea is that some opcodes have their parameters rearranged to make source code more readable.

```
0053=5,%5d% = create_player %1o% at %2d% %3d% %4d%
```

The disassembler writes the 5th opcode parameter before any others.&#x20;

```
0053: $PLAYER_CHAR = сreate_player #NULL at 2488.562 -1666.865 12.8757 
```

If the parameters will follow their original order, the opcode `0053` would look like:

```
0053: сreate_player #NULL at 2488.562 -1666.865 12.8757 $PLAYER_CHAR
```

{% hint style="warning" %}
Changing parameters order in the INI file should be avoided by any means as it makes the source code incompatible with the default opcode definitions or earlier scripts.
{% endhint %}

{% hint style="info" %}
Parameters order may vary from mode to mode. See the comparison table in [Edit modes](./#available-modes) to find out which mode uses which type.
{% endhint %}

#### Parameter Types

A letter following the index number indicates the parameter type.

`d` - any value\
`p` - a [label](../language/data-types/#labels) reference\
`o` - any [model](../language/data-types/#model-names) id (including objects)\
`m` - an `.ide` model id (no objects)\
`g` - a key from the [`.gxt`](./#text) file\
`x` - an external script ID\
`k` - a fixed-size null-terminated string literal (128 bytes)

{% hint style="info" %}
You can freely change parameters types, if needed.
{% endhint %}
