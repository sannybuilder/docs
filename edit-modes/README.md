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

путь к [`CustomLabels.ini`](customlabels.ini.md)

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

Sanny предоставляет несколько переменных, которые могут использоваться в параметрах и атрибутах \(там, где это применимо\).

`@game:` - путь к [папке с игрой](../options/general.md#direktoriya-igry), которая выбрана в настройках  
`@sb:` - путь к папке Sanny Builder \(где находится `sanny.exe`\)

Оба пути не включают в себя завершающий слеш \(`/`\).

## Список режимов

Sanny Builder предлагает много различных режимов, их количество может меняться от версии к версии:

| Название | Имена опкодов | Порядок параметров | Игра |
| :--- | :--- | :--- | :--- |
| GTA III | сообщество | измененный | все версии GTA III |
| GTA VC | сообщество | измененный | все версии Vice City |
| GTA SA v1.0 | сообщество | измененный | SA версия 1.0  |
| GTA SA v2.0 | сообщество | измененный | SA версия 2.0 |
| GTA SA \(v1.0 - SCR\) | Rockstar | первоначальный | SA версия 1.0 |
| GTA LCS | Rockstar | первоначальный | все версии Liberty City Stories |
| GTA VCS \(PSP\) | Rockstar | первоначальный | VCS для PSP |
| GTA VCS \(PS2\) | Rockstar | первоначальный | VCS для PS2 |
| SA Mobile | сообщество | измененный | SA версия для Android и iOS |

Колонка `Имена опкодов` определяет способ именования опкодов. Первые имена неизвестным опкодам были даны в результате анализа игрового кода, проводимого сообществом скриптеров в течение многих лет. Так появились такие термины как `актёр` или `поток`. Альтернативой является оригинальная терминология, использованная разработчиками игры \(соответственно `персонаж` или `скрипт`\). Эта терминология вместе со списком оригинальных названий всех опкодов оказались доступны в коде игры GTA SA: Mobile.   

`Порядок параметров` определяет как расположены параметры опкода относительно друг друга. В первоначальном порядке все параметры находятся в той последовательности, как было задумано разработчиками игры, от параметра с наименьшим индексом к параметру с наибольшим индексом. Измененный порядок подразумевает, что в некоторых опкодах параметры переставлены местами для повышения читаемости кода или по иным причинам.

Сочетание оригинальной терминологии и сохранение порядка следования параметров обеспечивает максимальное сходство скриптов с тем языком, который использовали разработчики игры.

## Переключение режимов

Чтобы переключить режим редактирования, кликните в правом нижнем углу программы. Появится список доступных режимов. Выберите нужный и кликните по нему. Sanny Builder загрузит все требуемые файлы и вы сразу можете продолжить работу.

![](../.gitbook/assets/edit_modes.png)

Выбрать режим через командную строку можно с [опцией](../cli.md#mode) `--mode`. Чтобы выбрать режим по умолчанию для какой-либо игры, используйте [опцию](../cli.md#game) `--game`.

Запуск Sanny Builder с [опцией](../cli.md#x) `-x` позволяет загрузить конфигурацию режимов из файла, отличного от `modes.xml`. Если при этом Sanny Builder уже запущен, он перезагрузит конфигурацию и обновит список доступных режимов.

