# Режимы редактирования

Sanny Builder поддерживает разные игры и платформы в серии Grand Theft Auto. Для этого в его состав входит конфигурация для каждой поддерживаемой игры, которая называется **режимом редактирования**.

Режим редактирования определяет следующую информацию:

* целевая игра
* пути к игровым файлам
* пути к файлам со вспомогательной информацией \(имена [меток](./#labels), [переменных](./#variables), [констант](./#constants)\)

По умолчанию Sanny Builder читает конфигурацию режимов из файла `<SB>\data\modes.xml`. Этот путь может быть изменен через [опцию](../cli.md#x) командной строки `-x`.

Допускается изменение существующих режимов и создание новых путем внесения изменений в файл `modes.xml`.

## Формат файла

`modes.xml` - документ в формате `XML`, который может редактироваться в любом текстовом редакторе. В этом файле содержатся все доступные режимы.

Корневым является элемент `<modes>`, который не имеет атрибутов. В файле может быть только один корневой элемент. 

Каждый из режимов описывается одним из внутренних элементов `<modes>`, начинающихся с открывающего тэга `<mode>` и заканчивающихся закрывающим тэгом `</mode>`. Элемент `<mode>` имеет как обязательные, так и необязательные атрибуты, описанные ниже. Содержимое `<mode>` представляет собой набор различных тэгов \(элементов\), определяющих пути к папкам и файлам.

### Атрибуты режима

#### id

`id` is a required and unique identifier of the mode. Sanny Builder uses the `id` to save some settings for this mode, e.g. a game directory.

A valid value for the `id` attribute is a unique series of characters not used for any other mode's id. 

#### extends

A mode can extend another mode \(the parent\) to reduce the number of duplicated properties. It is helpful for different versions of a game where most of the configuration is the same except for a few properties. The parent can also extend another mode. 

When a property is missing Sanny Builder recursively traverses all parent modes trying to find the property.

A valid value for the `extends` attribute is the `id` of another mode defined in the same file.

#### title

`title` defines the mode's displayed name. Due to the interface constraints avoid long names and keep it within the limit of 24 characters.

#### game

The `game` attribute defines a target game for the mode. There are 6 known values:

* `gta3`
* `vc`
* `sa`
* `lcs`
* `vcs`
* `sa_mobile`

Each game has an unique script format and the scripts compiled for one game are not compatible with scripts for another game.

Sanny Builder displays a game icon in front of the edit mode name so you know the target game. 

Before disassembling or compiling a script, make sure that the correct edit mode is active. Even if the script is compiled without errors, the game would crash trying to read a script in different format. 

{% hint style="info" %}
A compiled script file may store an information which game it is made for. When you open such a script, Sanny Builder prompts you to change the mode to the correct one. Ignoring this prompt may cause a crash of the disassembler, because the script format is unexpected for it.
{% endhint %}

#### type

One mode for each target game must be a default one. It means Sanny Builder uses this mode when run with the `--game` CLI [option]().

The valid value for the `type` is `default.` Omit this attribute for non-default modes.

### Параметры режима

#### arrays

путь к [`CustomArrays.ini`](../coding/arrays.md)

#### classes

путь к [`classes.db`](../coding/classes.md)

#### constants

путь к[`constants.txt`](../coding/constants.md)

#### data

путь к директории режима редактирования

#### ide

путь к `.ide` или `.dat` файлу:  
`.ide` файлы содержат [имена моделей](../coding/data-types.md#imena-modelei) и их характеристики  
`.dat` файлы содержат пути к другим `.ide` файлам

Элемент `ide` имеет необязательный атрибут `base`, который задает папку, относительно которой расчитываются пути, определенные внутри `.dat` файла:

```text
<ide base="@game:\">default.dat</ide>
```

Без `base` все пути расчитываются относительно папки с `.dat` файлом.

Режим редактирования может иметь несколько элементов `<ide>`.

#### keywords

путь к файлу со списком [ключевых слов](../coding/keywords.md)

#### labels

путь к [`CustomLabels.ini`]()

#### missions

путь к [`missions.txt`](../features.md#ispolzovanie-originalnykh-imen-missii)

#### opcodes

путь к файлу со [списком опкодов](opcodes-list-scm.ini.md)

#### templates

путь к файлу с [эксклюзивными шаблонами](code-templates.md)

#### text

путь к `.gxt` файлу

`<text>` имеет обязательный атрибут: `format`. Допустимыми значениями являются:

`gta3`: `.gxt` с одной таблицей, текстовыми ключами, кодировкой ANSI  
`vc`: `.gxt` с несколькими таблицами, текстовыми ключами, кодировкой ANSI  
`sa`: `.gxt` с несколькими таблицами, зашифрованными ключами, кодировкой ANSI  
`sa_mobile`: `.gxt` с несколькими таблицами, зашифрованными ключами, кодировкой UTF-16

#### variables

путь к [`CustomVariables.ini`](../coding/variables.md)

#### examples

путь к [`opcodes.txt`](../opcode-search-tool.md)

### Доступные переменные

Sanny provides a few variables that can be used in parameters and attributes \(if applicable\).

`@game:` - path to the [game directory](../options/general.md#game-directory) configured in the options  
`@sb:` - path to the Sanny Builder directory \(where `sanny.exe` is located\)

Both paths do not include the trailing slash.

## Список режимов

Sanny Builder offers many different modes and their number may vary from version to version:

| Title | Naming schema  | Parameters order | Game |
| :--- | :--- | :--- | :--- |
| GTA III | community | custom | all versions of GTA III |
| GTA VC | community | custom | all versions of Vice City |
| GTA SA v1.0 | community | custom | SA v1.0  |
| GTA SA v2.0 | community | custom | SA v2.0 |
| GTA SA \(v1.0 - SCR\) | Rockstar | original | SA v1.0 |
| GTA LCS | Rockstar | original | all versions of Liberty City Stories |
| GTA VCS \(PSP\) | Rockstar | original | VCS for PSP |
| GTA VCS \(PS2\) | Rockstar | original | VCS for PS2 |
| SA Mobile | community | custom | SA Android and iOS versions |

The naming schema defines the way of describing the opcodes. The c_ommunity_ schema has the names randomly guessed over the years, such as `actor` or `thread`. The _Rockstar_ schema has the original taxonomy used by the game developers \(e.g. `char` or `script`\) that is consistent with the game's inner structures.  

The parameters order defines the way of arranging the opcode parameters. In the _custom_ order the parameter with the higher index may go earlier in the script. This is applicable to community opcode descriptions. The _original_ order have all parameters arranged from the smallest index to the largest index. This goes with the Rockstar schema to make scripts look like they are meant to be by the developers.

## Переключение режимов

To change the mode, click at the right bottom corner of the Sanny Builder's main window. A list of the available modes will appear. As you click the mode name Sanny Builder makes all necessary adjustments and you may continue working immediately.

![](../.gitbook/assets/edit_modes.png)

To select the mode using CLI run Sanny Builder with the `--mode` [option](). To select a default mode for the game use the `--game` [option]().

Running Sanny Builder with the `-x` [option]() allows loading the modes configuration from a file different from the default `modes.xml`. If Sanny Builder is already running, it reloads the configuration and updates the list of modes.

