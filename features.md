# Возможности

Sanny Builder как среда программирования предоставляет пользователю следующие возможности.

## Подсветка синтаксиса

Sanny Builder подсвечивает код разными цветами, чтобы облегчить его чтение. Настройки подсветки могут быть изменены в [опциях программы](editor/options/syntax-highlighting.md).

## Быстрый переход по тексту

Текущую строку можно запомнить, если поставить закладку нажатием `Ctrl+Shift+0..9`, а затем вернуться к ней нажатием `Ctrl+0..9`.   
Удалить все закладки можно через меню `Правка -> Удалить закладки`.

Также можно перейти к строке по ее номеру через опцию `Перейти...`. Она вызывается комбинацией `Ctrl+G`. Введите порядковый номер нужной строки, и редактор быстро переместит Вас к ней.

## Моментальный поиск

Моментальный поиск позволяет находить слово или метку прямо в редакторе без вызова диалога поиска.

Чтобы найти в тексте другое вхождение слова под курсором, нажмите `Ctrl+Num6`, чтобы искать его ниже по тексту или `Ctrl+Num4`, чтобы искать выше. Курсор немедленно переместится к строке, где есть такое слово. Продолжайте нажимать `Ctrl+Num4/Num6`, чтобы найти другие строки с нужным словом.

Чтобы перейти к строке, обозначенной меткой \(например, `:MyLabel`\), поместите курсор на ссылку на эту метку \(`@MyLabel`\) и нажмите `Ctrl+Num2`. Редактор немедленно переместит курсор к строке с искомой меткой.

Если позиция курсора не изменилась, это означает, что моментальный поиск не смог найти нужное слово в тексте.

Перед изменением позиции курсора моментальный поиск запоминает текущую позицию, и если вы решили вернуться на предыдущее место, нажмите `Ctrl+Num8`.

## Показ различной информации о текущем опкоде

При включенной [опции](editor/options/editor.md#nastroiki) `Показывать информацию об опкодах` Sanny Builder показывает количество параметров для опкода и, если курсор находится над [именем модели](coding/data-types.md#imena-modelei), ее ID \(только для моделей из IDE-файлов и только когда определена [директория игры](editor/options/general.md#direktoriya-igry)\).

## Конвертирование исходников SA Mission Builder

В текущей версии поддерживается формат SAMB 0.33. Для конвертации откройте файл в Sanny Builder и выберите пункт меню `Сервис->Конвертация->MB->SB`. 

Также можно конвертировать отдельный, выделенный участок кода.

{% hint style="info" %}
При конвертировании используется файл `MB.ini`, в котором содержатся текстовые имена переменных и значения их адресов. Если Вы добавляли свои переменные в файл `variables.ini` в SAMB 0.33, используйте его \(переименовав в`MB.ini`\).
{% endhint %}

## Поиск нужного опкода

Используйте программу [поиска опкодов](opcode-search-tool.md), чтобы найти нужный опкод.

## Изменение координат и угла разворота игрока

Нажмите `Ctrl+Alt+1`, когда запущена игра, и появится окно менеджера. Здесь вы можете установить новые координаты и угол разворота игрока и скопировать текущие. В верхнем поле ввода вы можете указать сразу 3 координаты, разделив их пробелом или `,`. Также вы можете быстро вставить координаты игрока в редакторе комбинацией `Ctrl+Shift+C`. Вставка угла разворота \(`z_angle`\) в редакторе производится нажатием `Ctrl+Shift+E`.

## Переиспользование фрагментов кода

A code snippet is the group of lines that are inserted in the editor when you type a snippet name \(e.g.  `load`\) and press `F2` . The editor will add the following piece of the code:

```text
#.Load

while not #.Available

  wait 0

end
```

All snippets are contained in the file `macroes.txt`. This file has the following syntax:  
A snippet name is written in a separate line. The equal sign `=` follows the name. After the equal sign you can also add a short hint. The snippet code starts at the next line, each line begins with the equals sign. The cursor position is marked with the `|` character

Additionally, it's possible to save the code snippet in the file `macroes.txt` directly from the editor. Select the code and click the `Service->Add macros` menu. Enter the name of a new snippet, the description \(optionally\) in the appeared dialog window and press the `OK` button. The snippet is ready to be used.

To call the snippet list, press `Ctrl+J`.

## Запись и воспроизведение нажатий кнопок

You can record a key pressing sequence \(macro\) and playback it later. Consider the following code:

```text
$Actor = Actor.Create(CivMale, #MALE01, 100.0, 100.0, 10.0)
$ActorWithGun = Actor.Create(CivMale, #MALE01, 110.0, 100.0, 20.0)
$Gang01 = Actor.Create(CivMale, #MALE01, 120.0, 100.0, 30.0)
$Gang02 = Actor.Create(CivMale, #MALE01, 130.0, 100.0, 40.0)
$Killer = Actor.Create(CivMale, #MALE01, 140.0, 100.0, 50.0)
$ActorWithoutGun = Actor.Create(CivMale, #MALE01, 150.0, 100.0, 60.0) 
```

Say, you need to exchange the actor's handles in each pair \(i.e have `$ActorWithGun` instead of `$Actor`, and vice versa\).

Place the cursor in the first line before `$Actor` and press `Ctrl+M`. The editor immediately begins recording all keys - so be careful!

1. Press and hold `Ctrl` and press the `Right Arrow` button once 
2. Press `Shift+Home` and `Ctrl+Ins`.
3. Press the `Down Arrow` button. The cursor must be on the second line with the global variable in the clipboard
4. Press `Ctrl+Right Arrow` and `Shift+Ins`.
5. Press `Ctrl+Left Arrow`, `Shift+Home`, `Ctrl+Ins` and `Delete`
6. Press the `Up Arrow` button
7. Press `Ctrl+Shift+Right Arrow` and `Shift+Ins`
8. Press the `Home` button.

Now the first two lines should look like these:

```text
$ActorWithGun = Actor.Create(CivMale, 100.0, 100.0, 10.0)
$Actor = Actor.Create(CivMale, 110.0, 100.0, 20.0)
```

with the cursor being in the beginning of the first line. Now press `Ctrl+M` to stop recording.

You can playback the recorded sequence by pressing `Ctrl+P`. Place the cursor in the beginning of the third line, press `Ctrl+P` and the actor handles will be swapped.

During recording, you can pause/unpause it by pressing `Ctrl+P`.

## Замена номеров миссий на их названия

Sanny Builder allows using a mission name in the opcode `start_mission`. The mission name is the label defined with a `DEFINE MISSION` command. Say, you have:

```text
DEFINE MISSION 10 AT @MYMISSION
```

Instead of `start_mission 10` you can write`start_mission MYMISSION`.

There is also the [Replace Mission Numbers](editor/options/general.md#replace-mission-numbers) option. When it's enabled, the decompiler automatically replaces all mission numbers with their names.

To call the mission names list, press `Ctrl+Space`. The cursor has to be directly after the `start_mission` command.

Additionally, you can use [InstaSearch](features.md#instasearch) to navigate to the mission code when the cursor is under the mission name.

## Использование оригинальных имен миссий

Since v3.2.0 Sanny supports custom mission titles for each available [edit mode](edit-modes.md). Mission titles are stored in the `missions.txt` file located in the `data\<game>` folder. This file is used by the decompiler to add the title for each mission entry. If the `main.scm` file contains custom-made missions you may edit the `missions.txt` to have the correct title order after decompiling.

## Многоязычный интерфейс

Sanny Builder has fully multilingual interface translated into 15 languages. You can switch the languages in the [options](editor/options/general.md#interface-language) \(`F10`\). Refer to [sannybuilder/translations](https://github.com/sannybuilder/translations) for more information on how to create or update a translation.

## Меню внешних приложений

You can add up to `9` tools which can be executed whenever you need them. Every tool has its own hotkey for your convenience. You may also pass the parameters to your tool. To pass the name of the currently opened file use the special word `$SB_FileName`.

## Комментирование кода

Comments start with the double slash `//`, as seen in other programming languages. Everything after `//` to the end of the line is ignored by the compiler.

To comment out multiple lines or a part of the line, use block comments `{}`:

```text
0001: wait  {comments here} 0 ms
```

Since version 3.06 Sanny Builder also supports the C++-like comments `/* */`.

```text
0001: wait  /* comments here */ 0 ms
```

To comment out or uncomment multiple lines select them and press `Ctrl+Q`.

## Собственные имена для меток

You can give labels custom names that do not depend on the decompiler configuration. The names are specified in the file `CustomLabels.ini` \(one for each game\).

File syntax:  
`<label offset>=<custom name>`

If the decompiler finds a label at the specified offset, this label gets the given custom name.

To find out the offset value set the labels format to [`Global Offset`](editor/options/formats.md#global-offset) in the options. After decompiling, a number in the label name is the offset value.

## Проверка обновлений

Sanny Builder is able to check if a new version is available. To use this feature go to menu `Help->Check for update...`. The editor will connect to a remote server and if a newer version is available it prompts the download and install. 

The editor can also check for an update during startup if you enable this option in the updater window.

