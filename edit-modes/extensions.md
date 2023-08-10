# Расширения

**Расширение** - это набор новых инструкций (опкодов), добавленных в игру. [Библиотека CLEO](https://cleo.li) и плагины к ней являются наиболее известным источником таких наборов.

Чтобы Sanny Builder знал о намерении использовать в скрипте нестандартные опкоды, скрипт должен иметь [директиву](../coding/directives.md#usduse) `{$USE}`. Эта директива подключает дополнительный набор инструкций (см. ниже [список доступных расширений](extensions.md#extensions-list)):

```
{$USE CLEO}
{$USE ini}
{$USE CLEO+}
```

Каждый опкод, доступный в [INI файлах](opcodes-list-scm.ini.md) Sanny Builder, принадлежит к какому-либо расширению. Это сделано через файл `extensions.txt`.&#x20;

{% hint style="info" %}
См. [#74](https://github.com/sannybuilder/dev/issues/74) чтобы узнать о дальнейших планах по развитию расширений.
{% endhint %}

### Расширения по умолчанию

Стандартные игровые опкоды включены в расширение с именем `default`, которое доступно по умолчанию в каждом скрипте.  Использование директивы `{$USE default}` допускается, но является избыточным.

Использование [директивы](../coding/directives.md#usdcleo) `{$CLEO}` также подразумевает   `{$USE CLEO}`, что делает стандартные CLEO опкоды доступными компилятору.

### Список расширений <a href="#extensions-list" id="extensions-list"></a>

Sanny Builder включает в себя общие и популярные расширения для различных режимов редактирования:

| Имя расширения                                                            | Источник                                                                             | Режимы, в которых доступно                                           |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| <p><strong>CLEO</strong></p><p><code>{$USE CLEO}</code></p>               | <p>CLEO для GTA III <br>CLEO для Vice City</p><p>CLEO 4.4</p>                        | <p>GTA III</p><p>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p> |
| <p><strong>ini</strong></p><p><code>{$USE ini}</code></p>                 | <p>плагин IniFiles.cleo<br>(поставляется с CLEO)</p>                                 | <p>GTA III<br>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>    |
| <p><strong>file</strong></p><p><code>{$USE file}</code></p>               | <p>плагин FileSystemOperations<br>(поставляется с CLEO)</p>                          | <p>GTA III<br>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>    |
| <p><strong>bitwise</strong></p><p><code>{$USE bitwise}</code></p>         | <p>плагин IntOperations<br>(поставляется с CLEO4)</p>                                | <p>GTA III<br>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>    |
| <p><strong>clipboard</strong></p><p><code>{$USE clipboard}</code></p>     | плагин ClipboardControl                                                              | <p>GTA III<br>Vice City</p><p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>    |
| <p><strong>memory</strong></p><p><code>{$USE memory}</code></p>           | плагин MemoryModule                                                                  | <p>GTA III<br>Vice City</p>                                          |
| <p><strong>CLEO+</strong></p><p><code>{$USE CLEO+}</code></p>             | плагин CLEO+                                                                         | GTA SA v1.0, v2.0, (v1.0 - SCR)                                      |
| <p><strong>newOpcodes</strong></p><p><code>{$USE newOpcodes}</code></p>   | плагин newOpcodes                                                                    | GTA SA v1.0, v2.0                                                    |
| <p><strong>vcmobile</strong></p><p><code>{$USE vcmobile}</code></p>       | Vice City на мобильных устройствах                                                   | Vice City                                                            |
| <p><strong>Restoration</strong></p><p><code>{$USE Restoration}</code></p> | [Opcode Restoration Project](https://gtamods.com/wiki/Opcodes\_Restoration\_Project) | Vice City                                                            |

Допускается использование опкодов из источников, не перечисленных выше, при этом компилятор не будет требовать использование директивы `{$USE}`.
