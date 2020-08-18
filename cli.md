# Интерфейс командной строки

## --compile

`--compile <input file path> [output file path]` - compiles the file and exits

```text
sanny.exe --compile C:\myscm.txt C:\myscm.scm
```

{% hint style="info" %}
The `output file path` __parameter is optional. If there is no output path parameter, the compiler uses the [format rules](options/formats.md#file-name-format) to compute the output file name. 
{% endhint %}

{% hint style="info" %}
The input file must have no errors. If there are errors found during compilation, they will be logged in the file `compile.log`. When compilation ends, the program shuts down.
{% endhint %}

Shortcut: `-c`

## --debug

`--debug` - toggles [debug options](console.md#running-with-debug)

```text
sanny.exe --debug 11000
```

## --game

`--game <game>` - selects the [default mode](edit-modes/#type) for the given game. Known `game` values are:

* `gta3`
* `vc`
* `sa`
* `lcs`
* `vcs`
* `sa_mobile`

Shortcut: `-g`

```text
sanny.exe --game sa
```

## --mode

`--mode <id>` - selects the mode by `id`. [Modes](edit-modes/) and their ids are defined in the `modes.xml` file.

Shortcut: `-m`

```text
sanny.exe --mode vcs_psp
```

## --no-splash

`--no-splash` - runs Sanny Builder without the splash screen

```text
sanny.exe --no-splash
```

## -x

`-x <file path>` - sets the path to the file with the [edit modes](edit-modes/) configuration

```text
sanny.exe -x ..\my-modes.xml
```

