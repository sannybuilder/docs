# История изменений

## v. 3.3.3 - 20.10.2019

* исправлен [баг](http://bugs.sannybuilder.com/view.php?id=52), вызывавший неправильную компиляцию внешних скриптов

## v. 3.3.2 - 19.10.2019

* исправлены баги [\#0036](http://bugs.sannybuilder.com/view.php?id=36), [\#0050](http://bugs.sannybuilder.com/view.php?id=50)
* исправлен опкод `059C` в режиме `Vice City`

## v. 3.3.1 - 14.09.2019

* исправлен баг [\#0048](http://bugs.sannybuilder.com/view.php?id=48)
* добавлен файл `constants.txt,` который отсутствовал для режима `GTA SA`

## v. 3.3.0 - 08.09.2019

* добавлена поддержка для компиляции `SCM` Liberty City Stories
* добавлены алиасы для [переменных-таймеров](coding/variables.md#peremennye-taimery): TIMERA and TIMERB
* опция [Проверка переменных](editor/options/general.md#proverka-peremennykh) теперь применяется и к глобальным переменным

## v. 3.2.4 - 04.08.2019

* исправлены баги [\#0031](http://bugs.sannybuilder.com/view.php?id=31), [\#0032](http://bugs.sannybuilder.com/view.php?id=32), [\#0033](http://bugs.sannybuilder.com/view.php?id=33), [\#0040](http://bugs.sannybuilder.com/view.php?id=40), [\#0044](http://bugs.sannybuilder.com/view.php?id=44)
* исправлен дефект предыдущей версии, когда CHM справка не открывалась
* обновлены описания опкодов для GTA 3 и Vice City
* в IDE добавлена поддержка CLEO 2.0 для III и VC

## v. 3.2.3 - 07.07.2019

* улучшена поддержка версии GTA San Andreas для Wi﻿nStore, Xbox 360 и P﻿S3
* исправлена ошибка с неправильной декомпиляцией опкодов `09A4` и `0A18` в режиме `SA_Mobile`

## v. 3.2.2 - 05.07.2014

* добавлен перевод на корейский язык \(спасибо MINE\)
* улучшена работа конструкции [HEX..END](coding/hex..end.md)
* исправлен баг [\#0000028](http://bugs.sannybuilder.com/view.php?id=28)

## v. 3.2.1 - 04.05.2014

* добавлен перевод на индонезийский язык \(спасибо IMasterFX\)
* обновлены CLEO для GTA III и CLEO для Vice City \(спасибо Silent\)
* исправлены баги [\#0000026](http://bugs.sannybuilder.com/view.php?id=26), [\#0000027](http://bugs.sannybuilder.com/view.php?id=27)

## v. 3.2.0 - 22.03.2014

* добавление собственных [режимов редактирования](edit-modes.md) возможно путем изменения файла `games.xml`
* новый режим редактирования `GTA SA SCR`
* переменные [могут быть объявлены](coding/variables.md#korotkaya-forma-obyavleniya-peremennykh) при помощи указания типа перед именем переменной
* CLEO обновлена до версии 4.3.16
* добавлен [моментальный поиск](features.md#momentalnyi-poisk) в тексте \(ранее эта возможность называлась "переход к метке"\)
* [оригинальные названия миссий](features.md#ispolzovanie-originalnykh-imen-missii) могут быть изменены через файл missions.txt
* улучшена [ассоциация](editor/options/general.md#associaciya-failovykh-rasshirenii) расширений скриптовых файлов с Sanny Builder
* при указании директории игры Sanny Builder проверяет только существование этой директории и не проверяет наличие дополнительных файлов в ней
* небольшие улучшения в функции проверки обновлений
* изменена иконка Sanny Builder и иконки в меню
* исправлен баг [\#0000024](http://bugs.sannybuilder.com/view.php?id=24)

## v. 3.1.4 - 22.02.2014

* CLEO обновлена до версии 4.3.14
* исправлены некоторые ошибки в интерфейсе на высоких разрешениях экрана
* обновлены переводы на немецкий, польский, китайский, украинский языки

## v. 3.1.3 - 22.12.2013

* добавлена [поддержка](edit-modes.md) iOS и Android версий GTA: San Andreas
* значение [глубины просмотра](editor/options/editor.md#glubina-prosmotra-koda) теперь используется при построении списка констант
* обновлены переводы на китайский и немецкий языки

## v. 3.1.2 - 06.10.2013

* добавлен перевод на чешкий язык
* добавлены [опции](editor/options/general.md#associaciya-failovykh-rasshirenii) ассоциации файлов `.cs` и `.cm` с Sanny Builder.
* исправлены баги [\#0000011](http://bugs.sannybuilder.com/view.php?id=11), [\#0000020](http://bugs.sannybuilder.com/view.php?id=20)

## v. 3.1.1 - 22.09.2013

* добавлена новая директива [$OPCODE](coding/directives.md#usdopcode) для регистрации нового опкода через скрипт
* скорректировано поведение директивы [$INCLUDE](coding/directives.md#usdinclude) при поиске файла
* исправлены баги [\#0000005](http://bugs.sannybuilder.com/view.php?id=5), [\#0000019](http://bugs.sannybuilder.com/view.php?id=19)

## v. 3.1.0 - 14.09.2013

* в `VCSCM.ini` добавлены опкоды из мобильной версии GTA VC и отмечены неподдерживаемые опкоды
* при включенной опции [Добавлять доп. информацию в SCM](editor/options/general.md#dobavlyat-dopolnitelnuyu-informaciyu-v-scm), Sanny Builder запоминает игру, для которой был скомпилирован скрипт, чтобы включить нужный [режим редактирования](edit-modes.md) при декомпиляции
* при включенной опции `Добавлять доп. информацию в SCM`, Sanny Builder добавляет исходный код в тело скрипта \(только при наличии директивы [$EXTERNAL](coding/directives.md#usdexternal) или [$CLEO](coding/directives.md#usdcleo)\)
* добавлена новая директива [$NOSOURCE](coding/directives.md#usdnosource), чтобы запретить добавление исходного кода в тело скрипта
* некоторые горячие клавиши могут быть изменены [в опциях](editor/options/hotkeys.md)
* добавлена возможность автоматически проверять наличие обновления при запуске программы
* директивы [$VERSION](coding/directives.md#usdversion) и [$VERSION\_RESTORE](coding/directives.md#usdversion_restore) устарели \(компилируются, но не имеют эффекта\)
* обновлены перевод на испанский и китайский языки
* [Менеджер координат](features.md#izmenenie-koordinat-i-ugla-razvorota-igroka) может изменять угол поворота игрока в GTA VC
* в комплектацию Sanny Builder добавлен [CLEO плагин SCRLog](http://www.gtagarage.com/mods/show.php?id=23846) от LINK/2012 \(можно найти в папке tools\)
* исправлены баги [\#0000010](http://bugs.sannybuilder.com/view.php?id=10), [\#0000014](http://bugs.sannybuilder.com/view.php?id=14), [\#0000015](http://bugs.sannybuilder.com/view.php?id=15), [\#0000016](http://bugs.sannybuilder.com/view.php?id=16)

## v. 3.09 - 28.07.2013

* в Sanny Builder добавлено лицензионное соглашение вида Freeware/Donationware
* добавлена возможность сообщать о найденных багах в [официальный баг-трекер](http://bugs.sannybuilder.com/)
* добавлена возможность проверять наличие обновления для Sanny Builder
* [Менеджер координат](features.md#izmenenie-koordinat-i-ugla-razvorota-igroka) теперь поддерживает все известные версии GTA3, VC и SA \(спасибо Silent\)
* добавлена обновленная версия перевода на китайский язык
* исправлены баги [\#0000002](http://bugs.sannybuilder.com/view.php?id=2), [\#0000003](http://bugs.sannybuilder.com/view.php?id=3), [\#0000004](http://bugs.sannybuilder.com/view.php?id=4), [\#0000006](http://bugs.sannybuilder.com/view.php?id=6), [\#0000009](http://bugs.sannybuilder.com/view.php?id=9)
* небольшие изменения дизайна

## v. 3.08 - 05.07.2013

* добавлен [Silent's ASI Loader](http://www.gtagarage.com/mods/show.php?id=21709) v1.1 для CLEO 3 и CLEO 4
* добавлен перевод на китайский язык
* добавлены классы `File` и `Audiostream` для обратной совместимости с CLEO 4 от Alien

{% hint style="info" %}
`File.Open`, `Audiostream.Load`, `Audiostream.Load3D` были [методами](coding/classes.md#metody) в CLEO 4. Теперь они [свойства](coding/classes.md#svoistva). Это означает, что если вы получаете ошибку при компиляции старых скриптов, где использовались эти команды, измените их синтаксис следующим образом:

```text
переменная = File.Open(имя_файла, режим_открытия)
переменная = Audiostream.Load(имя_файла)
переменная = Audiostream.Load3D(имя_файла)
```
{% endhint %}

* компилятор теперь может принимать строковую константу в качестве параметра в свойстве класса

{% hint style="info" %}
Существует [ограничение](coding/classes.md#svoistva) на использование пробелов в таком параметре.
{% endhint %}

* компилятор больше не компилирует строки без начальной кавычки, например `text1"text2"` или `text1'text2'`
* компилятор может компилировать символы комментария внутри строки `"{text1}text2"`
* точка с запятой `;` больше не может использоваться для закомментирования строки
* изменен синтаксис параметра [\debug](./#parametry-komandnoi-stroki)
* добавлены иконки флагов для доступных языков перевода в [опциях](editor/options/general.md#yazyk-interfeisa)
* исправлены некоторые ошибки в декомпиляции для VCS

## v. 3.06 - 17.06.2013

* добавлены [новые операторы ++ и --](coding/built-in-commands.md)
* добавлена поддержка [блочных комментариев](features.md#kommentirovanie-koda) /\*   \*/
* `SASCM.INI` обновлен при помощи [базы GTAG](https://gtagmodding.com/opcode-database/)
* [свойства](coding/classes.md#svoistva) `Actor.Armour` и `Actor.Car` заменены на корректные версии `Actor.AddArmour`, `Actor.MissionCar`
* добавлено новое свойство `Actor.CurrentCar` для опкода `03C0` в скриптовых классах для игр SA и VC
* добавлены [новые комбинации клавиш](hotkeys.md) `Ctrl+Num+` и `Ctrl+Num-` для быстрого изменения размера шрифта в редакторе
* Sanny Builder запоминает число закрытых файлов для опции [Открывать все закрытые файлы](editor/options/editor.md#nastroiki)
* исправлена ошибка при компиляции скрипта с большим числом вставок [HEX..END](coding/hex..end.md)
* исправлена ошибка версии 3.05, когда программа зависала при запуске, пытаясь открыть файл, переданный в качестве параметра

## v. 3.05 - 05.06.2013

* добавлены новые языки перевода \(финский, польский, венгерский, украинский, турецкий\)
* библиотека CLEO обновлена до версии 4.1.1.30f \(CLEO 4 от Alien\)
* добавлена возможность установить CLEO для GTA III и для Vice City \(автор - Alien\)
* [файлы опкодов](scm-documentation/opcodes-list-scm.ini.md) \(\*\*SCM.ini, opcodes.txt\) замененены на файлы из комплекта CLEO 4.
* добавлен новый параметр запуска программы [\nosplash](./#parametry-komandnoi-stroki)

## v. 3.04 - 04.08.2008

* в редактор кода добавлены возможности конвертации чисел из 16-чной системы счисления в 10-чную и наоборот \(`Ctrl+H`\), а также конвертировать имя модели в ID и обратно \(`Ctrl+Alt+H`\)
* убрано сообщение о невозможности изменить `script.img` при компиляции CLEO-скриптов
*  отчет о компиляции показывает размер CLEO-скрипта \(пункт `Largest Script`\)
* исправлена ошибка при компиляции массива с числовыми индексами
*  инсталлятор не требует прав администратора

## v. 3.03 - 17.11.2007

* предыдущая версия CLEO была с ошибкой
* мелкие исправления \(положение панели инструментов теперь сохраняется\)

## v. 3.02 - 16.11.2007

* новая версия CLEO
* панель инструментов можно передвигать
* `F7` при компиляции `SCM` без заголовка \(c директивами [$E](coding/directives.md#usdexternal), [$CLEO](coding/directives.md#usdcleo)\) не делает копию
*  при компиляции файла с директивой `$CLEO` нажатием `F6` файл создается в той же папке, нажатием `F7` дополнительно создается копия в папке CLEO \(по аналогии с компиляцией `main.scm`\)
* новый язык перевода - итальянский, португальский

## v. 3.01 - 06.08.2007

* обновление, исправляющее некоторые ошибки

## v. 3.00 - 04.08.2007

* интегрирована библиотека [CLEO 3](https://cleo.li/ru)
* возможность декомпиляции `main.scm` Vice City Stories
* поддержка [констант](coding/constants.md)
* новые директивы [$INCLUDE](coding/directives.md#usdinclude), [$EXTERNAL](coding/directives.md#usdexternal), [$CLEO](coding/directives.md#usdcleo)
* запись [дополнительной информации](editor/options/general.md#dobavlyat-dopolnitelnuyu-informaciyu-v-scm) в конец `main.scm`
* задание [собственных массивов](editor/options/formats.md#sobstvennye-imena) при декомпиляции
* [возможность декомпилировать](console.md#skip_scm_header) файлы `main.scm` без заголовка
*  можно использовать внешний скрипт с именем AAA
* новый [параметр командной строки](./#parametry-komandnoi-stroki) `\compile`
* в цикле [FOR](coding/loops.md#for-end) можно использовать дробные значения счетчика
*  команды `WriteMem` и `ReadMem` больше не поддерживаются
*  поддержка поиска по тексту с использованием регулярных выражений
*  возможность сохранять исходник в формат [RTF или HTML](editor/options/syntax-highlighting.md)
* возможность [пропускать заставки](editor/options/general.md#bystraya-zagruzka-igry) при запуске San Andreas
* новая комбинация клавиш: [Ctrl+Enter](hotkeys.md)
* обновленный [SASCM.INI](scm-documentation/opcodes-list-scm.ini.md)

## v. 2.99e - 01.01.2007

* справлена ошибка с пропаданием части кода при декомпиляции в режиме отладки внутри конструкции [HEX..END](coding/hex..end.md)
* конструкция HEX..END может принимать [тип aDMA](coding/hex..end.md#ispolzovanie-tipa-adma) для записи чисел и [строки](coding/data-types.md#strokovye-literaly)
* к цикле [FOR](coding/loops.md#for-end) можно использовать имена моделей в качестве значений счетчика

## v. 2.99d - 03.12.2006

* убран Memory Hacker \(он стал [отдельной программой](http://sannybuilder.com/downloads)\)
* исправлена одна ошибка в декомпиляторе

## v. 2.99c - 30.11.2006

* добавлен плагин Memory Hacker
* возможность декомпиляции main.scm Liberty City Stories
* поддержка [числовых констант в качестве индекса](console.md#constant_indexes) глобального массива
* при декомпиляции переменные заменяются на тип [ADMA](coding/data-types.md#peremennye), если не делятся на `4`
* при компиляции при отсутствии заголовка выставляются значения по умолчанию
* возможность открывать файлы в редакторе методом Drag&Drop
* новые препроцессорные директивы: [{$VERSION}](coding/directives.md#usdversion), [{$VERSION\_RESTORE}](coding/directives.md#usdversion_restore)

{% hint style="info" %}
Если при компиляции вы получаете сообщение об ошибке в заголовке \(`Неизвестная команда DEFINE OBJECTS`\) переместите строку `{$VERSION xxxx}` в любое место после заголовка, например перед комментарием `//-------------MAIN---------------`
{% endhint %}

## v. 2.99 - 27.09.2006

* добавлены две новые команды WriteMem и ReadMem
* поддержка чисел в шестнадцатиричном формате
* конструкция [HEX..END](coding/hex..end.md) может принимать значения меток и глобальных переменных
* поддержка типа данных & для [массивов](coding/arrays.md), а также в выражениях без опкодов: `&57 += &120(&231,4i)`
* возможность давать [собственные имена меткам](editor/options/formats.md#sobstvennye-imena)
* возможность [выбирать регистр букв](editor/options/formats.md#registr-bukv) для собственных имен меток и переменных, а также стринговых переменных
* добавлена [консоль](console.md) для специальных опций SB
* поддержка `GXT` файлов GTA III, GTA VC
* [поддержка символьных констант](coding/data-types.md#strokovye-literaly) в длинных строках
* информация об авторе и версии [INI](scm-documentation/opcodes-list-scm.ini.md) файла
* поддержка классами `INI` с оригинальным порядком следования параметров \(как SASCM.INI от PLPynton\)
* [опция](editor/options/editor.md#nastroiki) подтверждения выхода
* возможность быстро переключать режим редактирования
* конвертация отдельного, выделенного участка кода
* возможность передавать во [внешнее приложение](features.md#menyu-vneshnikh-prilozhenii) в качестве параметра имя текущего открытого файла
* исправлены некоторые ошибки в конфигурационных файлах
* убрана автоматическая конвертация числа в тип `Float`, если переменная была объявлена как `Float`, а в нее записывалось целое число. Теперь опкод выбирается только в зависимости от типа числа
* чтение/изменение Z\_angle игрока в [Coord Manager](features.md#izmenenie-koordinat-i-ugla-razvorota-igroka); возможность вставки значения угла в скрипт нажатием `Ctrl+Shift+E` \(для SA\)

## v. 2.98 - 04.08.2006

* Sanny Builder полностью [русифицирован](editor/options/general.md#yazyk-interfeisa)
* добавлено [меню внешних приложений](features.md#menyu-vneshnikh-prilozhenii)
* в SB встроена специальная версия [Opcode Search Tool](opcode-search-tool.md)
* проверка математических выражений при декомпиляции с выключенной опцией [Писать опкоды](editor/options/general.md#ispolzovat-opkody)
* возможность выбирать `IMG` файл самостоятельно, если таковой не найден в папке с `main.scm`\(опция [Ручной выбор IMG-файла](editor/options/general.md#ruchnoi-vybor-img-faila)\)
* возможность добавлять новые [фрагменты кода](features.md#pereispolzovanie-fragmentov-koda) прямо из редактора; добавлены описания макросов
* список моделей можно сортировать по алфавиту/по значению \(`Alt+S`, когда активен список\)
* минорные исправления и изменения

## v. 2.97 - 11.06.2006

* новый [тип данных](coding/data-types.md#peremennye): `&`
* минорные изменения

## v. 2.96 - 01.04.2006

* расширена [опция прохода по меткам](features.md#momentalnyi-poisk)
* добавлена возможность вызвать список [фрагментов кода](features.md#pereispolzovanie-fragmentov-koda)
* добавлена [опция замены](editor/options/general.md#zamenyat-nomera-missii) номеров миссий на их имена
* исправлены некоторые ошибки

## v. 2.9f - 18.02.2006

* новые модели автоматически добавляются в список `DEFINE OBJECTS` \(этот список можно вообще не использовать\)
* добавлены блочные комментарии: `{}`
* добавлена запись [макросов](features.md#zapis-i-vosproizvedenie-nazhatii-knopok)
* минорные исправления и добавления

## v. 2.9 - 15.12.2005

* добавлены [дополнительные команды](coding/built-in-commands.md)
* добавлен оператор `IN`
* добавлена конструкция [IF..THEN..ELSE..END](coding/conditions.md#vysokourovnevye-konstrukcii)
* добавлены [циклы](coding/loops.md) `WHILE`, `REPEAT`; добавлена возможность использования вложенных циклов
* добавлена команда [ALLOC](coding/built-in-commands.md#alloc)
* новый стиль комментариев: `//`
* позиции маркеров и курсора запоминаются для закрытых файлов

## v. 2.6 - 05.11.2005

* добавлена поддержка форматов Vice City и GTA3
* добавлена возможность [объявления](coding/classes.md#obyavlenie-ekzemplyarov-klassa) переменных и массивов как экземпляров класса
* добавлен показ списка переменных и меток
* добавлена поддержка циклов \( оператор [FOR](coding/loops.md#for-end) \)
* миссии можно запускать по их имени \(`start_mission MYMISSION`\), где `MYMISSION` - это имя стартовой метки \(`DEFINE MISSION 100 at @MYMISSION` \)
* доступен список импортируемых моделей \(`DEFINE OBJECTS`\) по `Ctrl+Space`
* новый [оператор](coding/conditions.md#operatory-sravneniya) `<>`
* если при декомпиляции не найден `script.img`, используется оригинальный файл
* для [массивов](coding/arrays.md) добавлен тип `handle`
* возможность отключения предупреждения об использовании `IMG` игрой

## v. 2.5 - 10.10.2005

* добавлена поддержка [свойств](coding/classes.md#svoistva) классов
* добавлена поддержка [фрагментов кода](features.md#pereispolzovanie-fragmentov-koda)
* добавлена конструкция [VAR..END](coding/variables.md#konstrukciya-var-end) для эффективного управления переменными
* описаны все возможные математические опкоды: `0004..008B`
* новые операторы `<` и `<=`
* добавлена возможность автоподбора необходимого значения для оператора `IF`
* добавлена поддержка [текстовых названий](coding/classes.md#konstanty-klassa) параметров
* добавлен показ списка моделей
* минорные добавления и исправления

## v. 2.0 - 18.09.2005

* добавлена поддержка [классов](coding/classes.md)
* добавлена поддержка [ключевых слов](coding/keywords.md)
* добавлена возможность писать некоторые математические команды без опкодов
* для опкода `00D6` по умолчанию устанавливается параметр `0`, если иное не установлено \(`if` = `if 0`\)
* добавлена [опция выбора](editor/options/formats.md#imena-metok) различных видов меток
* добавлены [константы](coding/constants.md) `True` и `False`, которые обозначают `1` и `0` соответственно
* добавлена конструкция [HEX..END](coding/hex..end.md) для записи шестнадцатиричных значений прямо в `SCM`

## v. 1.1 - 07.09.2005

* добавлен [Coord Manager](features.md#izmenenie-koordinat-i-ugla-razvorota-igroka)
* исправлены некоторые ошибки

## v. 1.0 - 04.09.2005

* новый формат [меток](coding/data-types.md#metki)
* добавлен конвертор из синтаксиса BW's SA Mission Builder
* при декомпиляции в исходник добавляются названия моделей и содержимое `american.gxt`
* добавлены новые опции
* пофиксены некоторые ошибки

## v. 0.8 - 20.08.2005

* добавлена возможность ассоциировать `SCM` файлы с программой
* теперь при декомпиляции имя выходного файла изменяется, если такой файл уже существует \(например, если уже существует `main.scm.txt`, то имя нового файла будет `main.scm[0].txt`\)
* сообщения об ошибках стали более информативными
* добавлена проверка на дублирование [меток](coding/data-types.md#metki)
* пофиксены некоторые ошибки

## v. 0.7 - 10.08.2005

* увеличено число опций для работы с текстом
* добавлена возможность работать с несколькими файлами одновременно
* добавлена функция поиска опкодов через `F1` \(beta\)

## v. 0.6 - 04.08.2005

* полная декомпиляция `SCM` файлов San Andreas
* компиляция скриптов в `SCM` файл \(SA\) и `IMG`файл
* доступны минимальные опции работы с текстом

