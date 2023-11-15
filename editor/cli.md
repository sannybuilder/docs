# Интерфейс командной строки

## --compile

`--compile <путь к исходному файлу> [путь к конечному файлу]` - скомпилировать `исходный файл` и закрыть программу

```
sanny.exe --compile C:\myscm.txt C:\myscm.scm
```

{% hint style="info" %}
Если `путь к конечному файлу` пропущен, компилятор использует [настройки форматирования](options/formats.md#imena-failov).&#x20;
{% endhint %}

{% hint style="info" %}
Ошибки, возникшие во время компиляции, записываются в файл `compile.log`.
{% endhint %}

Краткая форма: `-c`

## --decompile

`--decompile <путь к исходному файлу> [путь к конечному файлу]` - декомпилировать `исходный файл` и закрыть программу

```
sanny.exe --decompile C:\myscm.scm C:\myscm.txt
```

{% hint style="info" %}
Если `путь к конечному файлу` пропущен, компилятор использует [настройки форматирования](options/formats.md#imena-failov).&#x20;
{% endhint %}

{% hint style="info" %}
Ошибки, возникшие во время декомпиляции, записываются в файл `compile.log`.
{% endhint %}

Краткая форма: `-d`

**--use-source** - опциональный аргумент, который указывает на необходимость использования исходного кода в теле скрипта (если он есть). По умолчанию декомпилятор игнорирует его.

```
sanny.exe --decompile C:\1.cs --use-source
```

## --debug

`--debug` - переключает [отладочные опции](console.md#otladochnye-opcii)

```
sanny.exe --debug 110000
```

## --game

`--game <game>` - выбирает [режим редактирования по умолчанию](../edit-modes/#type) для выбранной игры. Допустимые значения `game`:

* `gta3`
* `vc`
* `sa`
* `lcs`
* `vcs`
* `vc_mobile`
* `sa_mobile`

Краткая форма: `-g`

```
sanny.exe --game sa
```

## --mode

`--mode <id>` - выбирает режим редактирования с заданным [`id`](../edit-modes/#id). `id` режима можно узнать в соответствующем файле `mode.xml`.

Краткая форма: `-m`

```
sanny.exe --mode vcs_psp
```

## --no-splash

`--no-splash` - запускает Sanny Builder без загрузочного экрана

```
sanny.exe --no-splash
```

## -x

`-x` - перезагружает настройки [режимов редактирования](../edit-modes/) (полезно при тестировании изменений этих настроек)

```sh
sanny.exe -x
```

## --option

{% hint style="info" %}
Доступно, начиная с v3.8.0
{% endhint %}

`--option <имя опции> <значение>` - устанавливает значение определенной [опции](options/). Чтобы установить несколько опций сразу, перечислите их друг за другом:

`--option <имя 1й опции> <значение 1й опции> --option <имя 2й опции> <значение 2й опции> ... --option <имя N опции> <значение N опции>`&#x20;

Имя опции может принимать одно из следующих значений:

{% hint style="warning" %}
Данный список не окончательный и может меняться.
{% endhint %}

| Имя                                                                                             | Допустимые значения | Вкладка в настройках |
| ----------------------------------------------------------------------------------------------- | ------------------- | -------------------- |
| [Editor::ShowPanel](options/editor.md#nastroiki)                                                | 0, 1                | Редактор             |
| [Editor::ShowOpcodeInfo](options/editor.md#nastroiki)                                           | 0, 1                | Редактор             |
| [Editor::ShowLineNumbers](options/editor.md#nastroiki)                                          | 0, 1                | Редактор             |
| [Editor::ShowGutterBorder](options/editor.md#nastroiki)                                         | 0, 1                | Редактор             |
| [Editor::OpenLastFile](options/editor.md#nastroiki)                                             | 0, 1                | Редактор             |
| [Editor::OpenAllClosedFiles](options/editor.md#nastroiki)                                       | 0, 1                | Редактор             |
| [Editor::ConfirmExit](options/editor.md#nastroiki)                                              | 0, 1                | Редактор             |
| [Editor::LanguageService](options/editor.md#nastroiki)                                          | 0, 1                | Редактор             |
| [Editor::SemanticConstHighlighting](options/editor.md#nastroiki)                                | 0, 1                | Редактор             |
| [Editor::IdentifiersListAuto](options/editor.md#glubina-prosmotra-koda)                         | 0, 1                | Редактор             |
| [Editor::ScanDistance](options/editor.md#glubina-prosmotra-koda)                                | 0..65535            | Редактор             |
| [Editor::Lang](options/general.md#yazyk-interfeisa)                                             | номер локали        | Общие                |
| [Editor::QuickGameLoading](options/general.md#bystraya-zagruzka-igry)                           | 0, 1                | Общие                |
| [Editor::ShowProgress](options/general.md#pokazyvat-progress)                                   | 0, 1                | Общие                |
| [Editor::ShowReport](options/general.md#pokazyvat-otchet)                                       | 0, 1                | Общие                |
| [Decompiler::OverwriteOutputFile](options/general.md#perezapis-vykhodnogo-faila)                | 0, 1                | Общие                |
| [Decompiler::ManualIMGOpening](options/general.md#ruchnoi-vybor-img-faila)                      | 0, 1                | Общие                |
| [Decompiler::HexadimalOffsets](options/formats.md#imena-metok)                                  | 0, 1                | Общие                |
| [Decompiler::LabelsFormat](options/formats.md#imena-metok)                                      | 0, 1, 2             | Общие                |
| [Decompiler::AlwaysWriteOpcodes](options/general.md#ispolzovat-opkody)                          | 0, 1                | Общие                |
| [Decompiler::ReplaceMissionNumbers](options/general.md#zamenyat-nomera-missii)                  | 0, 1                | Общие                |
| [Decompiler::InsertOriginalMissionNames](options/general.md#vstavlyat-originalnye-imena-missii) | 0, 1                | Общие                |
| [Compiler::ShowIMGWarning](options/general.md#pokazyvat-preduprezhdenie)                        | 0, 1                | Общие                |
| [Compiler::CheckConditions](options/general.md#proverka-uslovii)                                | 0, 1                | Общие                |
| [Compiler::CheckLocalVariables](options/general.md#proverka-peremennykh)                        | 0, 1                | Общие                |
| [Compiler::AddExtraInfo](options/general.md#dobavlyat-dopolnitelnuyu-informaciyu-v-scm)         | 0, 1                | Общие                |
| [CustomNames::UseCustomLabels](options/formats.md#sobstvennye-imena)                            | 0, 1                | Форматирование       |
| [CustomNames::UseCustomVariables](options/formats.md#sobstvennye-imena)                         | 0, 1                | Форматирование       |
| [CustomNames::UseCustomArrays](options/formats.md#sobstvennye-imena)                            | 0, 1                | Форматирование       |
| [CustomNames::Format](options/formats.md#registr-bukv)                                          | 0, 1, 2             | Форматирование       |

{% hint style="info" %}
Опции, измененные через командную строку, не являются постоянными и применяются только в текущей сессии. После перезапуска Sanny Builder будет использовать значения из файла `settings.ini`.
{% endhint %}

Краткая форма: `-o`

```
sanny.exe -o Compiler::CheckConditions 0 -o Editor::LanguageService 1
```
