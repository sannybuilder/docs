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

Сокращенная версия: `-c`

## --debug

`--debug` - переключает [отладочные опции](console.md#otladochnye-opcii)

```text
sanny.exe --debug 11000
```

## --game

`--game <game>` - выбирает [режим редактирования по умолчанию](edit-modes/#type) для выбранной игры. Допустимые значения `game`:

* `gta3`
* `vc`
* `sa`
* `lcs`
* `vcs`
* `sa_mobile`

Сокращенная версия: `-g`

```text
sanny.exe --game sa
```

## --mode

`--mode <id>` - выбирает режим редактирования с заданным [`id`](edit-modes/#id). Режимы и их `id` определяются в файле `modes.xml`.

Сокращенная версия: `-m`

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

