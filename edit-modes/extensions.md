# Extensions

An **extension** is a set of new instructions added to the vanilla game. The [CLEO library](https://cleo.li) and its plugins is the most known way of adding those.

To make Sanny Builder aware of the custom instructions and explicitly signal their intentional usage, a script must have `{$USE}` [directive](../language/directives.md#usduse). The `{$USE}` directive enables one or multiple sets of instructions (see below the [list of extensions](extensions.md#extensions-list)).

```
{$USE CLEO, ini, CLEO+}
```

Each opcode included in Sanny Builder's [INI files](opcodes-list-scm.ini.md) has been categorized to belong to some extension. Currently it is done via the file `extensions.txt`.

{% hint style="info" %}
New edit modes shipped with Sanny Builder 4 use command definitions managed through Sanny Builder Library (SBL). They don't use [INI files](opcodes-list-scm.ini.md) and `extensions.txt`.  Information about each extension can be found in the JSON file located in the mode directory, or on the [Sanny Builder Library](https://library.sannybuilder.com/#/) website.&#x20;
{% endhint %}

## Implicit Extensions

Standard game opcodes have been included in the `default` extension that is implicitly available in any script. `{$USE default}` is possible but redundant.

Using `{$CLEO}` [directive](../language/directives.md#usdcleo) also implies `{$USE CLEO}` so standard CLEO opcodes are available to the compiler already.

## Extensions List

Sanny Builder ships some common and recognized extensions for different edit modes.&#x20;

{% hint style="info" %}
This list does not apply to the new SBL edit modes. Find a list of extensions for each game in [Sanny Builder Library](https://library.sannybuilder.com/#/).
{% endhint %}

| **Extension Name**                                                        | **Source**                                                                           | **Edit Modes Where Available**                                                                       |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| <p><strong>CLEO</strong></p><p><code>{$USE CLEO}</code></p>               | <p>CLEO for GTA III<br>CLEO for Vice City</p><p>CLEO 4.4</p><p>CLEO Android</p>      | <p>GTA III</p><p>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p><p>SA Mobile</p><p>VC Mobile</p> |
| <p><strong>ini</strong></p><p><code>{$USE ini}</code></p>                 | <p>IniFiles.cleo plugin<br>(ships with CLEO)</p>                                     | <p>GTA III<br>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>                                    |
| <p><strong>file</strong></p><p><code>{$USE file}</code></p>               | <p>FileSystemOperations plugin<br>(ships with CLEO)</p>                              | <p>GTA III<br>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>                                    |
| <p><strong>bitwise</strong></p><p><code>{$USE bitwise}</code></p>         | <p>IntOperations plugin<br>(ships with CLEO4)</p>                                    | <p>GTA III<br>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>                                    |
| <p><strong>clipboard</strong></p><p><code>{$USE clipboard}</code></p>     | ClipboardControl plugin                                                              | <p>GTA III<br>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>                                    |
| <p><strong>memory</strong></p><p><code>{$USE memory}</code></p>           | MemoryModule plugin                                                                  | <p>GTA III<br>Vice City</p>                                                                          |
| <p><strong>CLEO+</strong></p><p><code>{$USE CLEO+}</code></p>             | CLEO+ plugin                                                                         | GTA SA v1.0, v2.0, (v1.0 - SCR)                                                                      |
| <p><strong>newOpcodes</strong></p><p><code>{$USE newOpcodes}</code></p>   | newOpcodes plugin                                                                    | GTA SA v1.0, v2.0                                                                                    |
| <p><strong>Restoration</strong></p><p><code>{$USE Restoration}</code></p> | [Opcode Restoration Project](https://gtamods.com/wiki/Opcodes\_Restoration\_Project) | Vice City                                                                                            |

Using opcodes provided by the third-party libraries not listed above is still possible, the compiler will not require the `{$USE}` directive for them.
