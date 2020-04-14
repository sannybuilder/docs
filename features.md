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

Фрагменты кода - это заранее подготовленный код, которой вставляется в редактор, после ввода имени фрагмента \(например, `load`\) и нажатия `F2`. Редактор вставит следующий код:

```text
#.Load

while not #.Available

  wait 0

end
```

Все фрагменты содержатся в файле `macroes.txt`. Этот файл имеет следующий синтаксис:

`Имя фрагмента` пишется отдельной строкой. После имени должен стоять знак `=`. После `=` можно добавить краткое описание фрагмента. Поддерживаются только однострочные описания. После строки с именем записывается содержимое фрагмента, каждая строка начинается знаком `=`. Место, куда должен быть помещен курсор после вставки, обозначается символом `|`.

Также можно добавить новый фрагмент в файл `macroes.txt` прямо из редактора. Для этого нужно выделить нужный кусок текста и выбрать меню `Сервис->Добавить макрос`. В появившемся диалоговом окне вы должны ввести имя фрагмента \(также можно добавить описание\) и нажать кнопку `OK`. Новый фрагмент будет сразу же готов к использованию.

Вызвать список фрагментов можно комбинацией `Ctrl+J`.

## Запись и воспроизведение нажатий кнопок

Можно записывать последовательность нажатия клавиш \(макрос\) и воспроизводить ее позднее. Например, есть следующий код:

```text
$Actor = Actor.Create(CivMale, #MALE01, 100.0, 100.0, 10.0)
$ActorWithGun = Actor.Create(CivMale, #MALE01, 110.0, 100.0, 20.0)
$Gang01 = Actor.Create(CivMale, #MALE01, 120.0, 100.0, 30.0)
$Gang02 = Actor.Create(CivMale, #MALE01, 130.0, 100.0, 40.0)
$Killer = Actor.Create(CivMale, #MALE01, 140.0, 100.0, 50.0)
$ActorWithoutGun = Actor.Create(CivMale, #MALE01, 150.0, 100.0, 60.0) 
```

Допустим, нужно обменять переменные в каждой паре строк \(поставить вместо `$Actor` `$ActorWithGun`, а вместо `$ActorWithGun` - `$Actor` и т.д.\).

Поставьте курсор на первую строку и нажмите `Ctrl+M`. С этого момента редактор запоминает все нажатия клавиш, так что будьте осторожны.

1. Зажмите `Ctrl` и нажмите один раз `стрелку вправо`. `Ctrl` нужен так как строки разной длины. 
2. Теперь нажмите `Shift+Home` и `Ctrl+Ins`. 
3. Нажмите `стрелку вниз`. Курсор должен оказаться на второй строке, при этом глобальная переменная будет в буфере обмена. 
4. Нажмите `Ctrl+стрелка вправо` и `Shift+Ins`.
5. Нажмите `Ctrl+стрелка влево`, `Shift+Home`, `Ctrl+Ins` и кнопку `Delete`
6. Нажмите `стрелку вверх`
7. Нажмите `Ctrl+Shift+стрелка вправо` и `Shift+Ins`
8. Нажмите кнопку `Home`.

Теперь первые две строки выглядят так:

```text
$ActorWithGun = Actor.Create(CivMale, 100.0, 100.0, 10.0)
$Actor = Actor.Create(CivMale, 110.0, 100.0, 20.0)
```

и курсор стоит в начале первой строки. Теперь нажмите `Ctrl+M`. Макрос записан. Теперь можно воспроизводить записанную последовательность комбинацией `Ctrl+P`. Установите курсор на третью строку, нажмите `Ctrl+P`, и переменные `$Gang01` и `$Gang02` поменяются местами.

Во время записи макроса можно поставить/снять запись на паузу нажатием `Ctrl+P`.

## Замена номеров миссий на их названия

Sanny Builder допускает использовать имя миссии в команде `start_mission`. Именем миссии явлется ее метка, которая определена в блоке `DEFINE MISSION`.

Например, у вас есть 

```text
DEFINE MISSION 10 AT @MYMISSION
```

Вы можете использовать вместо `start_mission 10` команду `start_mission MYMISSION`.

Также существует [опция](editor/options/general.md#zamenyat-nomera-missii) `Заменять номера миссий`. Когда она включена, дизассемблер автоматически заменяет все номера миссий в коде на их имена. Эта опция дает возможность безболезненно удалять миссии, не заботясь о переименовывании номеров в коде.

Для дополнительного удобства после команды `start_mission` можно вызвать список имен миссий нажатием `Ctrl+пробел`.

См. также [Быстрый переход к миссии](features.md#momentalnyi-poisk).

## Использование оригинальных имен миссий

Начиная с версии 3.2.0 Sanny Builder поддерживает оригинальные названия миссий для каждого [режима редактирования](edit-modes.md). Названия содержатся в файле `missions.txt`. Этот файл используется при дизассемблировании, чтобы добавить название миссии как комментарий рядом командой определения \(`DEFINE MISSION`\) или вызова миссии \(`start_mission`\). 

При дизассемблировании `main.scm` с измененными миссиями, отредактируйте соответствующий файл `missions.txt`, чтобы названий миссий соответствовали скрипту.

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

