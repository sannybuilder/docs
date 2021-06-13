# Интерфейс командной строки

## --compile

`--compile <путь к исходному файлу> [путь к конечному файлу]` - скомпилировать `исходный файл` и закрыть программу

```text
sanny.exe --compile C:\myscm.txt C:\myscm.scm
```

{% hint style="info" %}
Если `путь к конечному файлу` пропущен, компилятор использует [настройки форматирования](options/formats.md#imena-failov). 
{% endhint %}

{% hint style="info" %}
Ошибки, возникшие во время компиляции, записываются в файл `compile.log`.
{% endhint %}

Краткая форма: `-c`

## --debug

`--debug` - переключает [отладочные опции](console.md#otladochnye-opcii)

```text
sanny.exe --debug 110000
```

## --game

`--game <game>` - выбирает [режим редактирования по умолчанию](edit-modes/#type) для выбранной игры. Допустимые значения `game`:

* `gta3`
* `vc`
* `sa`
* `lcs`
* `vcs`
* `sa_mobile`

Краткая форма: `-g`

```text
sanny.exe --game sa
```

## --mode

`--mode <id>` - выбирает режим редактирования с заданным [`id`](edit-modes/#id). Режимы и их `id` определяются в файле `modes.xml`.

Краткая форма: `-m`

```text
sanny.exe --mode vcs_psp
```

## --no-splash

`--no-splash` - запускает Sanny Builder без загрузочного экрана

```text
sanny.exe --no-splash
```

## -x

`-x <file path>` - устанавливает путь к файлу с [режимами редактирования](edit-modes/)

```text
sanny.exe -x ..\my-modes.xml
```

## --option

{% hint style="info" %}
Доступно, начиная с v3.8.0
{% endhint %}

`--option <имя опции> <значение>` - устанавливает значение определенной [опции](options/). Чтобы установить несколько опций сразу, перечислите их друг за другом:

`--option <имя 1й опции> <значение 1й опции> --option <имя 2й опции> <значение 2й опции> ... --option <имя N опции> <значение N опции>` 

Имя опции может принимать одно из следующих значений:

{% hint style="warning" %}
Данный список не окончательный и может меняться.
{% endhint %}

| Имя | Допустимые значения | Вкладка в настройках |
| :--- | :--- | :--- |
| [Editor::ShowPanel](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Editor::ShowOpcodeInfo](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Editor::ShowLineNumbers](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Editor::ShowGutterBorder](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Editor::OpenLastFile](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Editor::OpenAllClosedFiles](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Editor::ConfirmExit](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Editor::LanguageService](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Smart](options/editor.md#nastroiki) | 0, 1 | Редактор |
| [Decompiler::OverwriteOutputFile](options/general.md#perezapis-vykhodnogo-faila) | 0, 1 | Общие |
| [Engine::ShowProgress](options/general.md#pokazyvat-progress) | 0, 1 | Общие |
| [Engine::ShowReport](options/general.md#pokazyvat-otchet) | 0, 1 | Общие |
| [Compiler::ShowIMGWarning](options/general.md#pokazyvat-preduprezhdenie) | 0, 1 | Общие |
| [Decompiler::ManualIMGOpening](options/general.md#ruchnoi-vybor-img-faila) | 0, 1 | Общие |
| [QuickGameLoading](options/general.md#bystraya-zagruzka-igry) | 0, 1 | Общие |
| [Compiler::CheckConditions](options/general.md#proverka-uslovii) | 0, 1 | Общие |
| [Compiler::CheckLocalVariables](options/general.md#proverka-peremennykh) | 0, 1 | Общие |
| [Decompiler::AlwaysWriteOpcodes](options/general.md#ispolzovat-opkody) | 0, 1 | Общие |
| [Decompiler::ReplaceMissionNumbers](options/general.md#zamenyat-nomera-missii) | 0, 1 | Общие |
| [Decompiler::InsertOriginalMissionNames](options/general.md#vstavlyat-originalnye-imena-missii) | 0, 1 | Общие |
| [Compiler::AddExtraInfo](options/general.md#dobavlyat-dopolnitelnuyu-informaciyu-v-scm) | 0, 1 | Общие |
| [CustomNames::UseCustomLabels](options/formats.md#sobstvennye-imena) | 0, 1 | Форматирование |
| [CustomNames::UseCustomVariables](options/formats.md#sobstvennye-imena) | 0, 1 | Форматирование |
| [CustomNames::UseCustomArrays](options/formats.md#sobstvennye-imena) | 0, 1 | Форматирование |
| [CustomNames::CustomNamesFormat](options/formats.md#registr-bukv) | 0, 1, 2 | Форматирование |
| [Editor::IdentifiersListAuto](options/editor.md#glubina-prosmotra-koda) | 0, 1 | Редактор |
| [Editor::LookingDepth](options/editor.md#glubina-prosmotra-koda) | 0..65535 | Редактор |
| [Formats::HexadimalOffsets](options/formats.md#imena-metok) | 0, 1 | Форматирование |
| [Formats::LabelsFormat](options/formats.md#imena-metok) | 1, 2, 3 | Форматирование |
| [Lang](options/general.md#yazyk-interfeisa) | номер локали | Общие |

{% hint style="info" %}
Опции, измененные через командную строку, не являются постоянными и применяются только в текущей сессии. После перезапуска Sanny Builder будет использовать значения из файла settings.ini.
{% endhint %}

Краткая форма: `-o`

```text
sanny.exe -o Compiler::CheckConditions 0 -o Editor::LanguageService 1
```

