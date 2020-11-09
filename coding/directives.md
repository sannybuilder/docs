# Directives

Preprocessing **directives** are the special words that make the compiler function in different ways. They starts with `$` and enclosed between the curly brackets `{}`.

## $VERSION

{% hint style="warning" %}
This directive is deprecated since v3.1.0
{% endhint %}

Sets what version of [opcodes](../edit-modes/opcodes-list-scm.ini.md) to use during compilation.

Syntax:  
`{$VERSION x.y.zzzz}`

* `X`- [edit mode](../edit-modes/) ID
* `y` - parameters order
  * `0` - original: 0, 1, 2, etc
  * `1` - custom order, some parameters reordered
* `zzzz` - opcodes version

By default the compiler uses the version `current_edit_mode.1.0000`.

## $VERSION\_RESTORE

{% hint style="warning" %}
This directive is deprecated since v3.1.0
{% endhint %}

Restores the version to the value prior to using `$VERSION`.

Syntax:  
`{$VERSION_RESTORE}`

## $INCLUDE

Allows to insert the content of an external text file in the current file. If the compiler finds this directive it opens the file at the location provided as the parameter and proceeds from the code written in the included file. When it reaches the end of the included file it returns back to the previous file.

Syntax:  
`{$INCLUDE path\to\file}`

```text
{$INCLUDE loadwav.txt}
{$INCLUDE C:\dev\getarrayindex.txt}
```

If the file path is relative, the compiler scans directories in the following order to find the file:

1. directory of the file with the directive
2. `data` folder for the current edit mode
3. Sanny Builder root directory
4. the game directory

If none of these directories contains a requested file the compiler throws an exception. 

You may use this directive unlimited number of times. The included files may contain this directive too.

{% hint style="info" %}
A shorter form of this directive is `$I`.
{% endhint %}

## $EXTERNAL

Makes the compiler to treat the file as an external script. Meaning, the resulting output file will be header-less and with relative [label](data-types.md#labels) offsets, as an `.scm` file from the `script.img`. Using this directive requires that the file contains only one script or a single mission.

An alternative way to get such file is the debug [option](../console.md#skip_scm_header) `SKIP_SCM_HEADER`. This option could be enabled in the console or from the dropdown list on the main toolbar.

Syntax:  
`{$EXTERNAL}`

{% hint style="info" %}
A shorter form of this directive is `$E`.
{% endhint %}

## $CLEO

An analogue of the `$E` one, but the compiler automatically copies an output file to the `game\CLEO` directory. The file also gets an extension provided as the directive parameter.

Syntax:  
`{$CLEO <extension>}`

`extension` is an optional parameter specifying the file extension of the output file. It starts with the period character `.`. If no extension is present, the compiler uses the default value `.cs`

```text
{$CLEO .cm} // the file gets the extension .cm
{$CLEO} // the file gets the default extension .cs
```

So this directive is the perfect solution to make a CLEO script.

## $NOSOURCE

Prohibits the compiler from including a source code of the script. 

Without this directive when either the directive `$EXTERNAL` or `$CLEO` is present and the [option](../options/general.md#add-extra-info-to-scm) `Add extra info to SCM` is enabled, Sanny Builder adds the source code into an output file.

Syntax:  
`{$NOSOURCE}`

## $OPCODE

Registers a custom opcode via the script. 

All the opcodes definitions are contained in a [special file](../edit-modes/opcodes-list-scm.ini.md), one for each supported game. But sometimes it's necessary to add a custom opcode to use in the current script. `$OPCODE` makes it possible without touching the INI file.

Syntax:  
`{$OPCODE <opcode definition>}`  
 or  
`{$OPCODE <path\to\file>}`  
 or  
`{$OPCODE}`

`opcode definition` - it accepts an definition in the same [format](../edit-modes/opcodes-list-scm.ini.md#opcode-definition) as the INI file.

```text
{$OPCODE 0CCC=1,my_new_opcode %1d%}
```

`path\to\file` - this directive also accepts a file name as its parameter. This file must contain only opcodes definitions to be loaded. If a relative path is provided, the compiler scans directories using the same rules as for [$INCLUDE](directives.md#usdinclude).

```text
{$OPCODE additional_opcodes.ini}
```

When used without any parameter, this directive reloads the original opcodes definitions file and reverts all changes made.

```text
{$OPCODE}
```

{% hint style="info" %}
A shorter form of this directive is `$O`.
{% endhint %}

## $USE

Enables custom instructions set to the compiler. See [Extensions](../edit-modes/extensions.md) for more information.

```text
{$USE cleo+}
```



