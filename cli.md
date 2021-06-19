# Command Line Interface

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
sanny.exe --debug 110000
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

## --option

{% hint style="info" %}
Available since v3.8.0
{% endhint %}

`-o <option name> <value>` - sets the value of the specified [option](options/). To set multiple options, list each of them individually:

`-o <option1 name> <option1 value> -o <option2 name> <option2 value> ... -o <optionN name> <optionN value>` 

Option name can be one of the following:

{% hint style="warning" %}
This list is not final and subject to change at any moment.
{% endhint %}

| Name | Allowed Values | Options Tab |
| :--- | :--- | :--- |
| [Editor::ShowPanel](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::ShowOpcodeInfo](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::ShowLineNumbers](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::ShowGutterBorder](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::OpenLastFile](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::OpenAllClosedFiles](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::ConfirmExit](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::LanguageService](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::SemanticConstHighlighting](options/editor.md#editor-configuration) | 0, 1 | Editor |
| [Editor::IdentifiersListAuto](options/editor.md#code-scan-distance) | 0, 1 | Editor |
| [Editor::ScanDistance](options/editor.md#code-scan-distance) | 0..65535 | Editor |
| [Editor::Lang](options/general.md#interface-language) | known locale id | General |
| [Editor::QuickGameLoading](options/general.md#quick-game-loading) | 0, 1 | General |
| [Editor::ShowProgress](options/general.md#show-progress) | 0, 1 | General |
| [Editor::ShowReport](options/general.md#show-report) | 0, 1 | General |
| [Decompiler::OverwriteOutputFile](options/general.md#always-overwrite-output-file) | 0, 1 | General |
| [Decompiler::ManualIMGOpening](options/general.md#manual-img-opening) | 0, 1 | General |
| [Decompiler::HexadimalOffsets](options/formats.md#label-name-format) | 0, 1 | Formats |
| [Decompiler::LabelsFormat](options/formats.md#label-name-format) | 1, 2, 3 | Formats |
| [Decompiler::AlwaysWriteOpcodes](options/general.md#write-opcodes) | 0, 1 | General |
| [Decompiler::ReplaceMissionNumbers](options/general.md#replace-mission-numbers) | 0, 1 | General |
| [Decompiler::InsertOriginalMissionNames](options/general.md#insert-original-mission-names) | 0, 1 | General |
| [Compiler::ShowIMGWarning](options/general.md#show-warning) | 0, 1 | General |
| [Compiler::CheckConditions](options/general.md#check-conditions) | 0, 1 | General |
| [Compiler::CheckLocalVariables](options/general.md#ranges-check) | 0, 1 | General |
| [Compiler::AddExtraInfo](options/general.md#add-extra-info-to-scm) | 0, 1 | General |
| [CustomNames::UseCustomLabels](options/formats.md#custom-names) | 0, 1 | Formats |
| [CustomNames::UseCustomVariables](options/formats.md#custom-names) | 0, 1 | Formats |
| [CustomNames::UseCustomArrays](options/formats.md#custom-names) | 0, 1 | Formats |
| [CustomNames::Format](options/formats.md#case-converting) | 0, 1, 2 | Formats |

{% hint style="info" %}
Options set via CLI are not persistent and only applied to the current session. On the next launch Sanny Builder will use values stored in the `settings.ini`.
{% endhint %}

Shortcut: `-o`

```text
sanny.exe -o Compiler::CheckConditions 0 -o Editor::LanguageService 1
```

