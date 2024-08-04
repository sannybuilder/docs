# История изменений

## v. 4.0.0 - 04.08.2024

* [functions support](https://docs.sannybuilder.com/language/functions) (`function..end`)
* [CLEO 5 modules](https://docs.sannybuilder.com/language/import-export) support
* [new SBL edit modes](edit-modes/#available-modes)
* [debugger](https://docs.sannybuilder.com/editor/scm-debugger) for main.scm scripts
* [`switch..end`](https://docs.sannybuilder.com/language/control-flow/switch)
* binary number format (`0b101010`)
* new tabs
* other improvements and fixes

See the [complete list of changes](https://github.com/sannybuilder/dev/issues/277). Visit [SannyBuilder Discord](https://sannybuilder.com/discord) for additional information and support.

{% hint style="info" %}
This release won't be possible without great feedback and testing from Sanny Builder community as well as support from my [Patreon](https://www.patreon.com/seemann).
{% endhint %}

## v. 3.9.1 - 18.09.2023

* имя массива в выражениях без опкодов  может быть константой [#250](https://github.com/sannybuilder/dev/issues/250)&#x20;
* декомпилятор использует Alloc для глобальных переменных, если они отличаются от CustomVariables.ini [#251](https://github.com/sannybuilder/dev/issues/251)&#x20;
* опция "[Регистр букв](editor/options/formats.md#registr-bukv)" по умолчанию установлена в "Как есть" [#256](https://github.com/sannybuilder/dev/issues/256)
* исправлена ошибка, возникающая при компиляции опкода 0B17 [#254](https://github.com/sannybuilder/dev/issues/254)&#x20;
* исправлена ошибка, из-за которой редактор не предлагал использовать исходный код скрипта [#258](https://github.com/sannybuilder/dev/issues/258)&#x20;
* исправлены некоторые проблемы, связанные с объявлением строковых переменных [#259](https://github.com/sannybuilder/dev/issues/259), [#265](https://github.com/sannybuilder/dev/issues/265)

## v. 3.9.0 - 09.09.2023

* названия команд, используемые в JSON файлах [Sanny Builder Library](https://library.sannybuilder.com), могут использоваться в качестве [ключевых слов](coding/keywords.md)
* улучшения [HEX..END](coding/hex..end.md#byte-repetition) (многократное повторение байтов, подключение бинарных файлов)
* упрощенное объявление [констант](coding/constants.md#obyavlenie-konstant) и [переменных](coding/variables.md#declaring-a-variable-type) (`const x = 1, y = 2`, `float x, y, z`)
* новые [операторы](coding/operators.md#pobitovye-operacii) (побитовые, `=@`, `=#`)
* [директива](coding/directives.md) `{$INCLUDE_ONCE}`
* новые [режимы редактирования](edit-modes/) могут быть добавлены простым копированием в папку `data`, файла `modes.xml` больше нет&#x20;
* исправления ошибок и другие улучшения

👏 Спасибо всем, кто помогал и участвовал в этом релизе, а так же большое спасибо тем, кто поддерживает меня на [Patreon](https://patreon.com/seemann).

{% hint style="info" %}
Некоторый ошибочный код, который компилировался в предыдущих версиях, теперь будет вызывать ошибку. См. примеры такого кода [тут](https://github.com/sannybuilder/dev/issues/231#issuecomment-1627984136).
{% endhint %}

[Полный список изменений](https://github.com/sannybuilder/dev/issues/231)

## v. 3.8.5 - 22.02.2023

* исправлен баг [#216](https://github.com/sannybuilder/dev/issues/216)

## v. 3.8.4 - 17.02.2023

* при запуске программы с файлом (опция Открыть с помощью...) ранее открытые файлы должны быть доступны [#151](https://github.com/sannybuilder/dev/issues/151)
* [новая опция](editor/cli.md#decompile) командной строки `--decompile`&#x20;
* исправлены баги [#212](https://github.com/sannybuilder/dev/issues/212), [#213](https://github.com/sannybuilder/dev/issues/213), [#180](https://github.com/sannybuilder/dev/issues/180)
* исправлены некоторые проблемы компиляции классов с аргументами в виде строковых литералов

## v. 3.8.3 - 08.01.2023

* исправлены баги [#210](https://github.com/sannybuilder/dev/issues/210), [#204](https://github.com/sannybuilder/dev/issues/204), [#168](https://github.com/sannybuilder/dev/issues/168)
* исправлен [баг](https://github.com/sannybuilder/GetObjectID/issues/1) в поиске моделей
* плагин CLEO+ обновлен до [1.1.3](https://github.com/JuniorDjjr/CLEOPlus/releases/tag/v1.1.3)

## v. 3.8.2 - 08.09.2022

* исправлены баги [#200](https://github.com/sannybuilder/dev/issues/200), [#187](https://github.com/sannybuilder/dev/issues/187)

## v. 3.8.1 - 01.09.2022

* добавлена поддержка большего количества команд, завершающих выражение с несколькими условиями [#133](https://github.com/sannybuilder/dev/issues/133)&#x20;

```
    if and
        0AB0: is_key_pressed 9
	0AB0: is_key_pressed 10
    0AA0: gosub_if_false @label // раньше не работало, теперь компилируется
```

* новые и обновленные [переводы](https://github.com/sannybuilder/translations) (испанский, украинский, румынский, армянский языки)
* [новые темы оформления](https://github.com/sannybuilder/themes), созданные и присланные пользователями
* [большое обновление](https://github.com/MatiDragon-YT/help-system) локальных справочных материалов
* новый [режим редактирования](edit-modes/) для GTA SA PS2 с поддержкой команд PS2 CLEO
* обновлены файлы [CLEO](https://cleo.li/) и плагины:&#x20;
  * CLEO для San Andreas 4.4.1&#x20;
  * CLEO для GTA III и Vice City 2.0.0.6&#x20;
  * плагин [CLEO+ 1.1.2](https://github.com/JuniorDjjr/CLEOPlus/releases/tag/v1.1.2)&#x20;
* исправлены баги [#172](https://github.com/sannybuilder/dev/issues/172), [#189](https://github.com/sannybuilder/dev/issues/189)&#x20;

👏 Спасибо тем, кто участвовал в создании этой версии: [NicusorN5](https://github.com/NicusorN5), [Junior\_Djjr](https://github.com/JuniorDjjr), [wmysterio](https://github.com/wmysterio), [MatiDragon](https://github.com/MatiDragon-YT), [DanielSant0s](https://github.com/DanielSant0s), [JaggerJam69](https://github.com/JaggerJam69), [Vital](https://github.com/VitalRus95), [Sdas50](https://github.com/Sdas50), [nick7](https://github.com/nick7)

[Полный список изменений](https://github.com/sannybuilder/dev/issues/182)

## v. 3.8.0 - 04.08.2021

* [интеграция с Sanny Builder Library](editor/features.md#integration-with-sanny-builder-library): новым порталом с документацией по всем известным опкодам
* добавлено 16 [новых тем оформления](https://github.com/sannybuilder/themes)
* дизассемблер теперь выводит содержимое блока `hex..end` как строку, если оно является последовательностью ASCII символов, завершающейся нулевым байтом [#33](https://github.com/sannybuilder/dev/issues/33)
* [новая отладочная опция](editor/console.md#skip\_extra\_info), которая позволяет дизассемблеру игнорировать блок с доп. информацией в конце скрипта
* [новый параметр командной строки](editor/cli.md#option) для запуска Sanny Builder с определенными настройками
* [пользовательские шаблоны кода](edit-modes/code-templates.md#adding-a-new-template) теперь сохраняются в отдельный файл, чтобы обновления их не перезаписывали
* сочетания [горячих клавиш](editor/hotkeys.md), которые использовали цифровую клавиатуру (Numpad), были изменены (Размер текста: Ctrl + +/- and Переход к метке и обратно: Alt + Right/Left)
* плагин [CLEO+](https://github.com/JuniorDjjr/CLEOPlus) обновлен до версии 1.0.8
* обновлены переводы на венгерский, испанский, украинский и китайский языки
* [исправлено 16 багов](https://github.com/sannybuilder/dev/issues/130#issue-805022048)

👏 Спасибо тем, кто помогал с этим релизом: [forms55](https://github.com/forms55), [MatiDragon](https://github.com/MatiDragon-YT), [Vital](https://github.com/VitalRus95), [wmysterio](https://github.com/wmysterio), [XMDS](https://github.com/XMDS)

[Полный список изменений](https://github.com/sannybuilder/dev/issues/130)

## v. 3.7.0 - 30.01.2021

* объявленные [константы](coding/constants.md) теперь подсвечиваются ([#28](https://github.com/sannybuilder/dev/issues/28))
* список автодополнения показывает объявленные константы ([#40](https://github.com/sannybuilder/dev/issues/40))
* для каждой вкладки в редакторе можно выбирать свой [режим редактирования](edit-modes/) ([#87](https://github.com/sannybuilder/dev/issues/87))
* новый режим VC Mobile с опкодами CLEO Android ([sannybuilder/data#11](https://github.com/sannybuilder/data/pull/11))
* в режим VC PC добавлены опкоды из [Opcode Restoration project](https://github.com/cleolibrary/opcodes-restoration-project) (автор spaceeinstein)
* сообщения об ошибке теперь содержат ссылку на переведенную документацию, если таковая имеется ([#101](https://github.com/sannybuilder/dev/issues/101))
* конфигурация [внешних приложений](editor/features.md#menyu-vneshnikh-prilozhenii) поддерживает переменные **@sb:** и **@game:** ([#72](https://github.com/sannybuilder/dev/issues/72))
* плагин [CLEO+](https://github.com/JuniorDjjr/CLEOPlus) обновлен до версии 1.0.7
* исправлены баги: [#103](https://github.com/sannybuilder/dev/issues/103) [#114](https://github.com/sannybuilder/dev/issues/114) [#120](https://github.com/sannybuilder/dev/issues/120)

{% hint style="info" %}
Узнать больше о подсветке констант можно в статье [Языковая служба](editor/language-service.md).
{% endhint %}

[Полный список изменений](https://github.com/sannybuilder/dev/issues/90)

👏 Спасибо [XMDS](https://github.com/XMDS) за вклад в этот релиз.

## v. 3.6.2 - 29.11.2020

* исправлен баг с метками, отсутствующими в дизассемблированных CLEO скриптах [#99](https://github.com/sannybuilder/dev/issues/99)

## v. 3.6.1 - 27.11.2020

* обновлен перевод на украинский язык
* обновлен плагин CLEO+ до версии 1.0.4
* обновлены описания и ключевые слова для CLEO опкодов [#95](https://github.com/sannybuilder/dev/issues/95)
* исправлены баги в компиляторе [#96](https://github.com/sannybuilder/dev/issues/96), [#98](https://github.com/sannybuilder/dev/issues/98)
* небольшие изменения и исправления (см. [полный список](https://github.com/sannybuilder/dev/issues/91))

👏 Спасибо [wmysterio](https://github.com/wmysterio/) и [XMDS](https://github.com/XMDS) за их вклад в это обновление.

## v. 3.6.0 - 11.11.2020

* поддержка [перечисляемых типов](coding/classes.md#class-constants) в классах
* новые [типы](edit-modes/opcodes-list-scm.ini.md#parameter-types) параметров опкодов: [`m%`](https://github.com/sannybuilder/dev/issues/10) and [`k%`](https://github.com/sannybuilder/dev/issues/21)
* начальная поддержка [расширений](edit-modes/extensions.md)
* улучшена интеграция с библиотекой CLEO:
  * обновлены пакеты в папке `tools`:
    * CLEO v4.4
    * SCRLog v2020.2
    * добавлен [плагин CLEO+](https://github.com/sannybuilder/dev/issues/71) для GTA SA с 250+ новыми опкодами
  * скомпилированные скрипты для CLEO Android (`*.csa`, `*.csi`) теперь [распознаются](https://github.com/sannybuilder/dev/issues/64)
  * компилятор использует CLEO опкоды `0A9E`, `0A9F`, `0A90`, `0A91` [в определенных выражениях без опкода](https://github.com/sannybuilder/dev/issues/58#issuecomment-723376464)
  * унифицированы описания и кейворды для CLEO опкодов среди различных режимов редактирования
* добавлены [кейворды](coding/keywords.md) для всех опкодов в режиме GTA SA SCR
* слово _thread_ было заменено на _script_ в описаниях опкодов и кейвордах ([см. почему](https://gtamods.com/wiki/Talk:Script#Thread-%3EScript%29.))
* обновления IDE:
  * директория игры теперь не является обязательной для запуска компиляции ([#48](https://github.com/sannybuilder/dev/issues/48))
  * папка для "Компилировать и сделать копию" теперь конфигурируется ([#9](https://github.com/sannybuilder/dev/issues/9))
  * обновлены переводы на испанский и итальянский языки
  * добавлена возможность ассоциировать Sanny Builder с расширениями `*.csa` и `*.csi` (скрипты для CLEO Android).

[Полный список изменений и исправлений](https://github.com/sannybuilder/dev/issues/61)

👏 Спасибо [MatiDragon](https://github.com/MatiDragon-YT) и [Wesser](https://gtaforums.com/profile/172776-wesser/) за обновленные переводы.

## v. 3.5.1 - 21.08.2020

* исправлен баг с компиляцией скриптов LCS и VCS ([#56](https://github.com/sannybuilder/dev/issues/56))
* массивы в LCS and VCS теперь получают собственные имена из файлов `CustomVariables.ini` и `CustomArrays.ini` ([#53](https://github.com/sannybuilder/dev/issues/53))

👏 Спасибо [darkdraggy](https://gtaforums.com/profile/1097463-darkdraggy/) за обнаружение первого бага и помощь в тестировании.

## v. 3.5.0 - 18.08.2020

* изменения в [интерфейсе командной строки](editor/cli.md)
  * Unix-подобный синтаксис с дефисами ([#42](https://github.com/sannybuilder/dev/issues/42))
  * новые опции [`-x`](editor/cli.md#x), [`--game`](editor/cli.md#game), [`--mode`](editor/cli.md#mode)
* улучшения [режимов редактирования](edit-modes/)
  * `games.xml` переименован в `modes.xml`, обновлена [внутренняя структура](edit-modes/#format-faila)
  * режимы могут [наследовать](edit-modes/#extends) свойства других режимов (полезно для поддержки различных версий одной игры)
  * новый режим для SA v2.0 (использует [`CustomLabels_v2.ini`](edit-modes/customlabels.ini.md))
  * раздельные режимы для VCS PSP и VCS PS2 ([#41](https://github.com/sannybuilder/dev/issues/41))
  * поддержка [собственных IDE/DAT файлов](edit-modes/#ide)
  * "горячая" перезагрузка режимов редактирования ([#15](https://github.com/sannybuilder/dev/issues/15))
  * увеличено пространство для имени режима в углу экрана ([#8](https://github.com/sannybuilder/dev/issues/8))
* обновлены описания опкодов LCS/VCS\*
* убран конвертер синтаксиса SAMB в SB ([#27](https://github.com/sannybuilder/dev/issues/27))
* исправлена [привязка файловых расширений](editor/options/general.md#privyazka-failovykh-rasshirenii) к Sanny Builder ([#43](https://github.com/sannybuilder/dev/issues/43#issuecomment-670219723))
* исправлен баг с компиляцией скриптов LCS и VCS ([#49](https://github.com/sannybuilder/dev/issues/49), [#0053](http://bugs.sannybuilder.com/view.php?id=53), [#0064](http://bugs.sannybuilder.com/view.php?id=64))
* исправлена проблема, при которой окно [Opcode Search Tool](editor/opcode-search-tool.md) было недоступно после сворачивания ([#35](https://github.com/sannybuilder/dev/issues/35))

{% hint style="warning" %}
Новые описания опкодов для GTA LCS и GTA VCS несовместимы с предыдущими версиями. Вы должны заново дизассемблировать `main.scm` этих игр прежде чем делать какие-то изменения.
{% endhint %}

👏 Спасибо [marcelo\_20xx](https://gtaforums.com/profile/95582-marcelo\_20xx/) и [fastman92](https://gtaforums.com/profile/423631-fastman92/) за их вклад в этот релиз.

## v. 3.4.1 - 06.08.2020

* исправлено неверное количество параметров у опкода `04E3` в `VCSSCM.INI`
* исправлена проблема в дизассемблере, которая приводила к игнорированию опции "Писать опкоды" и генерации невалидного кода

## v. 3.4.0 - 04.08.2020

* добавлена поддержка компиляции `SCM` в GTA: Vice City Stories ([#2](https://github.com/sannybuilder/dev/issues/2))
* добавлена возможность [объявлять](coding/variables.md#korotkaya-forma-obyavleniya-peremennykh) локальные переменные с собственными именами ([#32](https://github.com/sannybuilder/dev/issues/32))
* добавлен упрощенный синтаксис для вызова подпрограмм, используя [имя метки](coding/data-types.md#metki): если после имени метки стоит `()` это представляет команду`gosub`
* больше конфигураций для [режимов редактирования](edit-modes/):
  * путь к `GXT` файлу, который использует дизассемблер ([#7](https://github.com/sannybuilder/dev/issues/7))
  * путь к `opcodes.txt` ([#5](https://github.com/sannybuilder/dev/issues/5))
  * эксклюзивные [шаблоны кода](edit-modes/code-templates.md)
* добавлен новый туториал о высокоуровневых конструкциях в языке Sanny Builder (на английском), лежит в папке `help\examples`
* обновления IDE:
  * `Запуск San Andreas` из меню теперь проверяет наличие файла `gta-sa.exe` (Steam)
  * новый пункт меню для быстрого создания CLEO скрипта (см. примечание внизу статьи [Шаблоны кода](edit-modes/code-templates.md))
  * ссылки на новый портал с документацией в меню и сообщениях об ошибках
* небольшие изменения:
  * обновлены определения некоторых опкодов (player money += в SA, award\_achievement в SA Mobile, `0479` в VCS)
  * в файле `CustomVariables.ini` для GTA III переменные `script_controlled_player` и `flag_player_on_mission` переименованы в `PLAYER_ACTOR` и `ONMISSION` соответственно ([#3](https://github.com/sannybuilder/data/issues/3))
  * возвращена старая версия файлов в папке `help\GXT Strings` ([#25](https://github.com/sannybuilder/dev/issues/25))
  * файл `macroes.txt` переименован `templates.txt`
* [обновления переводов](https://github.com/sannybuilder/translations/milestone/1)

👏 Спасибо [OrionSR](https://gtaforums.com/profile/213525-orionsr/), [ZAZ](https://gtaforums.com/profile/67506-zaz/), [XMDS](https://gtaforums.com/profile/1034872-xmds), и [Wesser](https://gtaforums.com/profile/172776-wesser/) за их вклад в этот релиз.

## v. 3.3.3 - 20.10.2019

* исправлен [баг](http://bugs.sannybuilder.com/view.php?id=52), вызывавший неправильную компиляцию внешних скриптов

## v. 3.3.2 - 19.10.2019

* исправлены баги [#0036](http://bugs.sannybuilder.com/view.php?id=36), [#0050](http://bugs.sannybuilder.com/view.php?id=50)
* исправлен опкод `059C` в режиме `Vice City`

## v. 3.3.1 - 14.09.2019

* исправлен баг [#0048](http://bugs.sannybuilder.com/view.php?id=48)
* добавлен файл `constants.txt,` который отсутствовал для режима `GTA SA`

## v. 3.3.0 - 08.09.2019

* добавлена поддержка для компиляции `SCM` Liberty City Stories
* добавлены алиасы для [переменных-таймеров](coding/variables.md#peremennye-taimery): TIMERA and TIMERB
* опция [Проверка переменных](editor/options/general.md#proverka-peremennykh) теперь применяется и к глобальным переменным

## v. 3.2.4 - 04.08.2019

* исправлены баги [#0031](http://bugs.sannybuilder.com/view.php?id=31), [#0032](http://bugs.sannybuilder.com/view.php?id=32), [#0033](http://bugs.sannybuilder.com/view.php?id=33), [#0040](http://bugs.sannybuilder.com/view.php?id=40), [#0044](http://bugs.sannybuilder.com/view.php?id=44)
* исправлен дефект предыдущей версии, когда CHM справка не открывалась
* обновлены описания опкодов для GTA 3 и Vice City
* в IDE добавлена поддержка CLEO 2.0 для III и VC

## v. 3.2.3 - 07.07.2019

* улучшена поддержка версии GTA San Andreas для Wi﻿nStore, Xbox 360 и P﻿S3
* исправлена ошибка с неправильной декомпиляцией опкодов `09A4` и `0A18` в режиме `SA_Mobile`

## v. 3.2.2 - 05.07.2014

* добавлен перевод на корейский язык (спасибо MINE)
* улучшена работа конструкции [HEX..END](coding/hex..end.md)
* исправлен баг [#0000028](http://bugs.sannybuilder.com/view.php?id=28)

## v. 3.2.1 - 04.05.2014

* добавлен перевод на индонезийский язык (спасибо IMasterFX)
* обновлены CLEO для GTA III и CLEO для Vice City (спасибо Silent)
* исправлены баги [#0000026](http://bugs.sannybuilder.com/view.php?id=26), [#0000027](http://bugs.sannybuilder.com/view.php?id=27)

## v. 3.2.0 - 22.03.2014

* добавление собственных [режимов редактирования](edit-modes/) возможно путем изменения файла `games.xml`
* новый режим редактирования `GTA SA SCR`
* переменные [могут быть объявлены](coding/variables.md#korotkaya-forma-obyavleniya-peremennykh) при помощи указания типа перед именем переменной
* CLEO обновлена до версии 4.3.16
* добавлен [моментальный поиск](editor/features.md#momentalnyi-poisk) в тексте (ранее эта возможность называлась "переход к метке")
* [оригинальные названия миссий](editor/features.md#ispolzovanie-originalnykh-imen-missii) могут быть изменены через файл missions.txt
* улучшена [ассоциация](editor/options/general.md#associaciya-failovykh-rasshirenii) расширений скриптовых файлов с Sanny Builder
* при указании директории игры Sanny Builder проверяет только существование этой директории и не проверяет наличие дополнительных файлов в ней
* небольшие улучшения в функции проверки обновлений
* изменена иконка Sanny Builder и иконки в меню
* исправлен баг [#0000024](http://bugs.sannybuilder.com/view.php?id=24)

## v. 3.1.4 - 22.02.2014

* CLEO обновлена до версии 4.3.14
* исправлены некоторые ошибки в интерфейсе на высоких разрешениях экрана
* обновлены переводы на немецкий, польский, китайский, украинский языки

## v. 3.1.3 - 22.12.2013

* добавлена [поддержка](edit-modes/) iOS и Android версий GTA: San Andreas
* значение [глубины просмотра](editor/options/editor.md#glubina-prosmotra-koda) теперь используется при построении списка констант
* обновлены переводы на китайский и немецкий языки

## v. 3.1.2 - 06.10.2013

* добавлен перевод на чешкий язык
* добавлены [опции](editor/options/general.md#associaciya-failovykh-rasshirenii) ассоциации файлов `.cs` и `.cm` с Sanny Builder.
* исправлены баги [#0000011](http://bugs.sannybuilder.com/view.php?id=11), [#0000020](http://bugs.sannybuilder.com/view.php?id=20)

## v. 3.1.1 - 22.09.2013

* добавлена новая директива [$OPCODE](coding/directives.md#usdopcode) для регистрации нового опкода через скрипт
* скорректировано поведение директивы [$INCLUDE](coding/directives.md#usdinclude) при поиске файла
* исправлены баги [#0000005](http://bugs.sannybuilder.com/view.php?id=5), [#0000019](http://bugs.sannybuilder.com/view.php?id=19)

## v. 3.1.0 - 14.09.2013

* в `VCSCM.ini` добавлены опкоды из мобильной версии GTA VC и отмечены неподдерживаемые опкоды
* при включенной опции [Добавлять доп. информацию в SCM](editor/options/general.md#dobavlyat-dopolnitelnuyu-informaciyu-v-scm), Sanny Builder запоминает игру, для которой был скомпилирован скрипт, чтобы включить нужный [режим редактирования](edit-modes/) при декомпиляции
* при включенной опции `Добавлять доп. информацию в SCM`, Sanny Builder добавляет исходный код в тело скрипта (только при наличии директивы [$EXTERNAL](coding/directives.md#usdexternal) или [$CLEO](coding/directives.md#usdcleo))
* добавлена новая директива [$NOSOURCE](coding/directives.md#usdnosource), чтобы запретить добавление исходного кода в тело скрипта
* некоторые горячие клавиши могут быть изменены [в опциях](editor/options/hotkeys.md)
* добавлена возможность автоматически проверять наличие обновления при запуске программы
* директивы [$VERSION](coding/directives.md#usdversion) и [$VERSION\_RESTORE](coding/directives.md#usdversion\_restore) устарели (компилируются, но не имеют эффекта)
* обновлены перевод на испанский и китайский языки
* [Менеджер координат](editor/features.md#izmenenie-koordinat-i-ugla-razvorota-igroka) может изменять угол поворота игрока в GTA VC
* в комплектацию Sanny Builder добавлен [CLEO плагин SCRLog](http://www.gtagarage.com/mods/show.php?id=23846) от LINK/2012 (можно найти в папке tools)
* исправлены баги [#0000010](http://bugs.sannybuilder.com/view.php?id=10), [#0000014](http://bugs.sannybuilder.com/view.php?id=14), [#0000015](http://bugs.sannybuilder.com/view.php?id=15), [#0000016](http://bugs.sannybuilder.com/view.php?id=16)

## v. 3.09 - 28.07.2013

* в Sanny Builder добавлено лицензионное соглашение вида Freeware/Donationware
* добавлена возможность сообщать о найденных багах в [официальный баг-трекер](http://bugs.sannybuilder.com/)
* добавлена возможность проверять наличие обновления для Sanny Builder
* [Менеджер координат](editor/features.md#izmenenie-koordinat-i-ugla-razvorota-igroka) теперь поддерживает все известные версии GTA3, VC и SA (спасибо Silent)
* добавлена обновленная версия перевода на китайский язык
* исправлены баги [#0000002](http://bugs.sannybuilder.com/view.php?id=2), [#0000003](http://bugs.sannybuilder.com/view.php?id=3), [#0000004](http://bugs.sannybuilder.com/view.php?id=4), [#0000006](http://bugs.sannybuilder.com/view.php?id=6), [#0000009](http://bugs.sannybuilder.com/view.php?id=9)
* небольшие изменения дизайна

## v. 3.08 - 05.07.2013

* добавлен [Silent's ASI Loader](http://www.gtagarage.com/mods/show.php?id=21709) v1.1 для CLEO 3 и CLEO 4
* добавлен перевод на китайский язык
* добавлены классы `File` и `Audiostream` для обратной совместимости с CLEO 4 от Alien

{% hint style="info" %}
`File.Open`, `Audiostream.Load`, `Audiostream.Load3D` были [методами](coding/classes.md#metody) в CLEO 4. Теперь они [свойства](coding/classes.md#svoistva). Это означает, что если вы получаете ошибку при компиляции старых скриптов, где использовались эти команды, измените их синтаксис следующим образом:

```
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
* добавлена поддержка [блочных комментариев](editor/features.md#kommentirovanie-koda) /\* \*/
* `SASCM.INI` обновлен при помощи [базы GTAG](https://gtagmodding.com/opcode-database/)
* [свойства](coding/classes.md#svoistva) `Actor.Armour` и `Actor.Car` заменены на корректные версии `Actor.AddArmour`, `Actor.MissionCar`
* добавлено новое свойство `Actor.CurrentCar` для опкода `03C0` в скриптовых классах для игр SA и VC
* добавлены [новые комбинации клавиш](editor/hotkeys.md) `Ctrl+Num+` и `Ctrl+Num-` для быстрого изменения размера шрифта в редакторе
* Sanny Builder запоминает число закрытых файлов для опции [Открывать все закрытые файлы](editor/options/editor.md#nastroiki)
* исправлена ошибка при компиляции скрипта с большим числом вставок [HEX..END](coding/hex..end.md)
* исправлена ошибка версии 3.05, когда программа зависала при запуске, пытаясь открыть файл, переданный в качестве параметра

## v. 3.05 - 05.06.2013

* добавлены новые языки перевода (финский, польский, венгерский, украинский, турецкий)
* библиотека CLEO обновлена до версии 4.1.1.30f (CLEO 4 от Alien)
* добавлена возможность установить CLEO для GTA III и для Vice City (автор - Alien)
* [файлы опкодов](edit-modes/opcodes-list-scm.ini.md) (\*\*SCM.ini, opcodes.txt) замененены на файлы из комплекта CLEO 4.
* добавлен новый параметр запуска программы [\nosplash](./#parametry-komandnoi-stroki)

## v. 3.04 - 04.08.2008

* в редактор кода добавлены возможности конвертации чисел из 16-чной системы счисления в 10-чную и наоборот (`Ctrl+H`), а также конвертировать имя модели в ID и обратно (`Ctrl+Alt+H`)
* убрано сообщение о невозможности изменить `script.img` при компиляции CLEO-скриптов
* отчет о компиляции показывает размер CLEO-скрипта (пункт `Largest Script`)
* исправлена ошибка при компиляции массива с числовыми индексами
* инсталлятор не требует прав администратора

## v. 3.03 - 17.11.2007

* предыдущая версия CLEO была с ошибкой
* мелкие исправления (положение панели инструментов теперь сохраняется)

## v. 3.02 - 16.11.2007

* новая версия CLEO
* панель инструментов можно передвигать
* `F7` при компиляции `SCM` без заголовка (c директивами [$E](coding/directives.md#usdexternal), [$CLEO](coding/directives.md#usdcleo)) не делает копию
* при компиляции файла с директивой `$CLEO` нажатием `F6` файл создается в той же папке, нажатием `F7` дополнительно создается копия в папке CLEO (по аналогии с компиляцией `main.scm`)
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
* [возможность декомпилировать](editor/console.md#skip\_scm\_header) файлы `main.scm` без заголовка
* можно использовать внешний скрипт с именем AAA
* новый [параметр командной строки](./#parametry-komandnoi-stroki) `\compile`
* в цикле [FOR](coding/loops.md#for-end) можно использовать дробные значения счетчика
* команды `WriteMem` и `ReadMem` больше не поддерживаются
* поддержка поиска по тексту с использованием регулярных выражений
* возможность сохранять исходник в формат RTF или HTML
* возможность [пропускать заставки](editor/options/general.md#bystraya-zagruzka-igry) при запуске San Andreas
* новая комбинация клавиш: [Ctrl+Enter](editor/hotkeys.md)
* обновленный [SASCM.INI](edit-modes/opcodes-list-scm.ini.md)

## v. 2.99e - 01.01.2007

* справлена ошибка с пропаданием части кода при декомпиляции в режиме отладки внутри конструкции [HEX..END](coding/hex..end.md)
* конструкция HEX..END может принимать [тип aDMA](coding/hex..end.md#ispolzovanie-tipa-adma) для записи чисел и [строки](coding/data-types.md#strokovye-literaly)
* к цикле [FOR](coding/loops.md#for-end) можно использовать имена моделей в качестве значений счетчика

## v. 2.99d - 03.12.2006

* убран Memory Hacker (он стал [отдельной программой](http://sannybuilder.com/downloads))
* исправлена одна ошибка в декомпиляторе

## v. 2.99c - 30.11.2006

* добавлен плагин Memory Hacker
* возможность декомпиляции main.scm Liberty City Stories
* поддержка [числовых констант в качестве индекса](editor/console.md#constant\_indexes) глобального массива
* при декомпиляции переменные заменяются на тип [ADMA](coding/data-types.md#peremennye), если не делятся на `4`
* при компиляции при отсутствии заголовка выставляются значения по умолчанию
* возможность открывать файлы в редакторе методом Drag\&Drop
* новые препроцессорные директивы: [{$VERSION}](coding/directives.md#usdversion), [{$VERSION\_RESTORE}](coding/directives.md#usdversion\_restore)

{% hint style="info" %}
Если при компиляции вы получаете сообщение об ошибке в заголовке (`Неизвестная команда DEFINE OBJECTS`) переместите строку `{$VERSION xxxx}` в любое место после заголовка, например перед комментарием `//-------------MAIN---------------`
{% endhint %}

## v. 2.99 - 27.09.2006

* добавлены две новые команды WriteMem и ReadMem
* поддержка чисел в шестнадцатиричном формате
* конструкция [HEX..END](coding/hex..end.md) может принимать значения меток и глобальных переменных
* поддержка типа данных & для [массивов](coding/arrays.md), а также в выражениях без опкодов: `&57 += &120(&231,4i)`
* возможность давать [собственные имена меткам](editor/options/formats.md#sobstvennye-imena)
* возможность [выбирать регистр букв](editor/options/formats.md#registr-bukv) для собственных имен меток и переменных, а также стринговых переменных
* добавлена [консоль](editor/console.md) для специальных опций SB
* поддержка `GXT` файлов GTA III, GTA VC
* [поддержка символьных констант](coding/data-types.md#strokovye-literaly) в длинных строках
* информация об авторе и версии [INI](edit-modes/opcodes-list-scm.ini.md) файла
* поддержка классами `INI` с оригинальным порядком следования параметров (как SASCM.INI от PLPynton)
* [опция](editor/options/editor.md#nastroiki) подтверждения выхода
* возможность быстро переключать режим редактирования
* конвертация отдельного, выделенного участка кода
* возможность передавать во [внешнее приложение](editor/features.md#menyu-vneshnikh-prilozhenii) в качестве параметра имя текущего открытого файла
* исправлены некоторые ошибки в конфигурационных файлах
* убрана автоматическая конвертация числа в тип `Float`, если переменная была объявлена как `Float`, а в нее записывалось целое число. Теперь опкод выбирается только в зависимости от типа числа
* чтение/изменение Z\_angle игрока в [Coord Manager](editor/features.md#izmenenie-koordinat-i-ugla-razvorota-igroka); возможность вставки значения угла в скрипт нажатием `Ctrl+Shift+E` (для SA)

## v. 2.98 - 04.08.2006

* Sanny Builder полностью [русифицирован](editor/options/general.md#yazyk-interfeisa)
* добавлено [меню внешних приложений](editor/features.md#menyu-vneshnikh-prilozhenii)
* в SB встроена специальная версия [Opcode Search Tool](editor/opcode-search-tool.md)
* проверка математических выражений при декомпиляции с выключенной опцией [Писать опкоды](editor/options/general.md#ispolzovat-opkody)
* возможность выбирать `IMG` файл самостоятельно, если таковой не найден в папке с `main.scm`(опция [Ручной выбор IMG-файла](editor/options/general.md#ruchnoi-vybor-img-faila))
* возможность добавлять новые [фрагменты кода](editor/features.md#pereispolzovanie-fragmentov-koda) прямо из редактора; добавлены описания макросов
* список моделей можно сортировать по алфавиту/по значению (`Alt+S`, когда активен список)
* минорные исправления и изменения

## v. 2.97 - 11.06.2006

* новый [тип данных](coding/data-types.md#peremennye): `&`
* минорные изменения

## v. 2.96 - 01.04.2006

* расширена [опция прохода по меткам](editor/features.md#momentalnyi-poisk)
* добавлена возможность вызвать список [фрагментов кода](editor/features.md#pereispolzovanie-fragmentov-koda)
* добавлена [опция замены](editor/options/general.md#zamenyat-nomera-missii) номеров миссий на их имена
* исправлены некоторые ошибки

## v. 2.9f - 18.02.2006

* новые модели автоматически добавляются в список `DEFINE OBJECTS` (этот список можно вообще не использовать)
* добавлены блочные комментарии: `{}`
* добавлена запись [макросов](editor/features.md#zapis-i-vosproizvedenie-nazhatii-knopok)
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
* добавлена поддержка циклов ( оператор [FOR](coding/loops.md#for-end) )
* миссии можно запускать по их имени (`start_mission MYMISSION`), где `MYMISSION` - это имя стартовой метки (`DEFINE MISSION 100 at @MYMISSION` )
* доступен список импортируемых моделей (`DEFINE OBJECTS`) по `Ctrl+пробел`
* новый [оператор](coding/conditions.md#operatory-sravneniya) `<>`
* если при декомпиляции не найден `script.img`, используется оригинальный файл
* для [массивов](coding/arrays.md) добавлен тип `handle`
* возможность отключения предупреждения об использовании `IMG` игрой

## v. 2.5 - 10.10.2005

* добавлена поддержка [свойств](coding/classes.md#svoistva) классов
* добавлена поддержка [фрагментов кода](editor/features.md#pereispolzovanie-fragmentov-koda)
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
* для опкода `00D6` по умолчанию устанавливается параметр `0`, если иное не установлено (`if` = `if 0`)
* добавлена [опция выбора](editor/options/formats.md#imena-metok) различных видов меток
* добавлены [константы](coding/constants.md) `True` и `False`, которые обозначают `1` и `0` соответственно
* добавлена конструкция [HEX..END](coding/hex..end.md) для записи шестнадцатиричных значений прямо в `SCM`

## v. 1.1 - 07.09.2005

* добавлен [Coord Manager](editor/features.md#izmenenie-koordinat-i-ugla-razvorota-igroka)
* исправлены некоторые ошибки

## v. 1.0 - 04.09.2005

* новый формат [меток](coding/data-types.md#metki)
* добавлен конвертор из синтаксиса BW's SA Mission Builder
* при декомпиляции в исходник добавляются названия моделей и содержимое `american.gxt`
* добавлены новые опции
* пофиксены некоторые ошибки

## v. 0.8 - 20.08.2005

* добавлена возможность ассоциировать `SCM` файлы с программой
* теперь при декомпиляции имя выходного файла изменяется, если такой файл уже существует (например, если уже существует `main.scm.txt`, то имя нового файла будет `main.scm[0].txt`)
* сообщения об ошибках стали более информативными
* добавлена проверка на дублирование [меток](coding/data-types.md#metki)
* пофиксены некоторые ошибки

## v. 0.7 - 10.08.2005

* увеличено число опций для работы с текстом
* добавлена возможность работать с несколькими файлами одновременно
* добавлена функция поиска опкодов через `F1` (beta)

## v. 0.6 - 04.08.2005

* полная декомпиляция `SCM` файлов San Andreas
* компиляция скриптов в `SCM` файл (SA) и `IMG`файл
* доступны минимальные опции работы с текстом
