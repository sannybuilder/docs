# Директивы

Preprocessing **directives** are the special words that make the compiler function in different ways. They starts with `$` and enclosed between the curly brackets `{}`.

## $VERSION

{% hint style="warning" %}
This directive is deprecated since v3.1.0
{% endhint %}

This directive sets what version of opcodes should be used during compilation.

Syntax:  
`$VERSION x.y.zzzz`

* `X`- edit mode ID
* `y` - parameters order
  * `0` - original, numeric
  * `1` - custom order
* `zzzz` - opcodes version

By default the compiler uses the version `current_edit_mode.1.0000`.

## $VERSION\_RESTORE

{% hint style="warning" %}
This directive is deprecated since v3.1.0
{% endhint %}

This directive restores the version to the value prior to using `$VERSION`.

## $INCLUDE

This directive allows to insert the content of an external text file in the current file. If the compiler finds this directive it opens the file by the path passing as the directive's parameter and continues the compiling process from the code written in the included file. When it reaches the end of the file it returns back to the previous file.

Syntax:  
`{$INCLUDE file path}`

```text
{$INCLUDE loadwav.txt}
{$INCLUDE C:\dev\getarrayindex.txt}
```

If the file path is relative, the compiler searches the file in the following order:

1. directory of the file with the directive\*
2. Sanny Builder\data\&lt;game&gt;
3. Sanny Builder root directory
4. the game directory

If none of these directories contains a needed file the compiler throws an exception. You can use this directive unlimited number of times. The included files can contain this directive as well.

{% hint style="info" %}
\*All paths used in the `$INCLUDE` directive are relative to the directory of the currently processed file.
{% endhint %}

{% hint style="info" %}
A shorter form of this directive is `$I`.
{% endhint %}

## $EXTERNAL

This directive makes the compiler to process the file like an external script. Meaning, the resulting file will be header-less and with relative label offsets, so it will be the same as an `.scm` file from the `script.img`. Using this directive requires that the file contains only one script \(or a single mission\).

The alternative way to get such file is the debug option `SKIP_SCM_HEADER`. This option could be enabled in the console or from the list on the main toolbar.

Syntax:  
`{$EXTERNAL}`

{% hint style="info" %}
A shorter form of this directive is `$E`.
{% endhint %}

## $CLEO

This directive is an analogue of the `$E` one, but the output file is copied into the `game\CLEO` directory automatically. It also gets the file extension specified as a directive parameter.

Syntax:  
`{$CLEO <extension>}`

`Extension` is an optional parameter. If no extension is present, the compiler uses the default value `.cs`

```text
{$CLEO} // the file gets the default extension .cs
```

So this directive is the perfect solution to make a CLEO script.

## $NOSOURCE

This directive prohibits the compiler from including a source code of the script. By default, when the option Add extra info to SCM is enabled, Sanny Builder adds a source code into a script file \(only when either the directive `$EXTERNAL` or `$CLEO` is present\). This directive changes the default behavior of the compiler, not allowing to include the source code into an output file.

Syntax:  
`{$NOSOURCE}`

## $OPCODE

This directive allows to register a custom opcode directly via the script. Commonly, all the opcodes definitions are contained in a special file, one for each supported game. But sometimes it's necessary to add a custom opcode for the current script. The directive `$OPCODE` makes it possible without editing an opcodes INI file.

Syntax:  
`{$OPCODE <opcode definition>}`  
 or  
`{$OPCODE <file name>}`  
 or  
`{$OPCODE}`

It accepts an opcode definition in the same syntax as the INI file.

```text
{$OPCODE 0CCC=1,my_new_opcode %1d%}
```

This directive also accepts a file name as its parameter. This file must contain only opcodes definitions to be loaded. If no global path is specified for the file, the compiler searches it using the same rules as for [$INCLUDE](directives.md#usdinclude).

```text
{$OPCODE additional_opcodes.ini}
```

When used without any parameter, this directive reloads the original opcodes definitions file, so all the changes made by previous using of this directive are gone.

```text
{$OPCODE}
```

{% hint style="info" %}
A shorter form of this directive is `$O`.
{% endhint %}





