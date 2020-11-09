# Extensions

An **extension** is a set of new instructions added to the vanilla game. The CLEO library and its plugins is the most known way of adding those. 

To make Sanny Builder aware of the custom instructions and explicitly signal their intentional usage, a script must have `{$USE}` directives. `{$USE}` directive enables a particular set of instructions \(see below the [list of extensions](extensions.md#extensions-list)\).

```text
{$USE cleo}
{$USE IniFiles}
{$USE cleo+}
```

Each opcode included in Sanny Builder's [INI files](opcodes-list-scm.ini.md) has been categorized to belong to some extension. Currently it is done via the file `extensions.txt`. 

{% hint style="info" %}
See [\#74](https://github.com/sannybuilder/dev/issues/74) for more information on how this feature is expected to function in the future.
{% endhint %}

### Implicit Extensions

Vanilla opcodes have been included in the `default` extension that is implicitly available in any script. `{$USE default}` is possible but redundant. 

Using `{$CLEO}` directive also implies `{$USE cleo}` so standard CLEO opcodes are available to the compiler already.

### Extensions List

Sanny Builder ships some common and recognized extensions for different edit modes:

| Edit Mode | Extension Name | Description |
| :--- | :--- | :--- |
| GTA III | cleo | CLEO 2.0 for GTA III  |
| GTA III | cleo 1.1 | CLEO 1.1 for GTA III \(not recommended, prefer CLEO 2.0\) |
| Vice City | cleo | CLEO 2.0 for Vice City |
| Vice City | cleo 1.1 | CLEO 1.1 for Vice City \(not recommeded, prefer CLEO 2.0\) |
| GTA SA v1.0, v2.0, \(v1.0 - SCR\) | cleo | CLEO 4.4 |
| GTA SA v1.0, v2.0, \(v1.0 - SCR\) | IniFiles | IniFiles.cleo plugin \(ships with CLEO4\) |
| GTA SA v1.0, v2.0, \(v1.0 - SCR\) | FileSystemOperations | FileSystemOperations.cleo plugin \(ships with CLEO4\) |
| GTA SA v1.0, v2.0, \(v1.0 - SCR\) | ClipboardControl | ClipboardControl.cleo plugin |
| GTA SA v1.0, v2.0, \(v1.0 - SCR\) | cleo+ | CLEO+ plugin |
| GTA SA v1.0, v2.0 | newOpcodes | newOpcodes plugin |



