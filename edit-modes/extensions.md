# Расширения

**Расширение** - это набор новых инструкций \(опкодов\), добавленных в игру. [Библиотека CLEO](https://cleo.li) и плагины к ней являются наиболее известным источником таких наборов.

Чтобы Sanny Builder знал о намерении использовать в скрипте нестандартные опкоды, скрипт должен иметь [директиву](../coding/directives.md#usduse) `{$USE}`. Эта директива подключает дополнительный набор инструкций \(см. ниже [список доступных расширений](extensions.md#extensions-list)\):

```text
{$USE CLEO}
{$USE ini}
{$USE CLEO+}
```

Каждый опкод, доступный в [INI файлах](opcodes-list-scm.ini.md) Sanny Builder, принадлежит к какому-либо расширению. Это сделано через файл `extensions.txt`. 

{% hint style="info" %}
См. [\#74](https://github.com/sannybuilder/dev/issues/74) чтобы узнать о дальнейших планах по развитию расширений.
{% endhint %}

### Расширения по умолчанию

Стандартные игровые опкоды включены в расширение с именем `default`, которое доступно по умолчанию в каждом скрипте.  Использование директивы `{$USE default}` допускается, но является избыточным.

Использование [директивы](../coding/directives.md#usdcleo) `{$CLEO}` также подразумевает   `{$USE CLEO}`, что делает стандартные CLEO опкоды доступными компилятору.

### Список расширений <a id="extensions-list"></a>

Sanny Builder включает в себя общие и популярные расширения для различных режимов редактирования:

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x418;&#x43C;&#x44F; &#x440;&#x430;&#x441;&#x448;&#x438;&#x440;&#x435;&#x43D;&#x438;&#x44F;</th>
      <th
      style="text-align:left">&#x418;&#x441;&#x442;&#x43E;&#x447;&#x43D;&#x438;&#x43A;</th>
        <th style="text-align:left">&#x420;&#x435;&#x436;&#x438;&#x43C;&#x44B;, &#x432; &#x43A;&#x43E;&#x442;&#x43E;&#x440;&#x44B;&#x445;
          &#x434;&#x43E;&#x441;&#x442;&#x443;&#x43F;&#x43D;&#x43E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><b>CLEO</b>
        </p>
        <p><code>{$USE CLEO}</code>
        </p>
      </td>
      <td style="text-align:left">
        <p>CLEO 2.0 &#x434;&#x43B;&#x44F; GTA III
          <br />CLEO 2.0 &#x434;&#x43B;&#x44F; Vice City</p>
        <p>CLEO 4.4</p>
      </td>
      <td style="text-align:left">
        <p>GTA III</p>
        <p>Vice City</p>
        <p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>CLEO1.1</b>
        </p>
        <p><code>{$USE CLEO1.1}</code>
        </p>
      </td>
      <td style="text-align:left">CLEO 1.1 &#x434;&#x43B;&#x44F; GTA III
        <br />CLEO 1.1 &#x434;&#x43B;&#x44F; Vice City
        <br />(&#x43D;&#x435; &#x440;&#x435;&#x43A;&#x43E;&#x43C;&#x435;&#x43D;&#x434;&#x443;&#x435;&#x442;&#x441;&#x44F;,
        &#x438;&#x441;&#x43F;&#x43E;&#x43B;&#x44C;&#x437;&#x443;&#x439;&#x442;&#x435;
        CLEO 2.0)</td>
      <td style="text-align:left">
        <p>GTA III</p>
        <p>Vice City</p>
        <p></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>ini</b>
        </p>
        <p><code>{$USE ini}</code>
        </p>
      </td>
      <td style="text-align:left">&#x43F;&#x43B;&#x430;&#x433;&#x438;&#x43D; IniFiles.cleo
        <br />(&#x43F;&#x43E;&#x441;&#x442;&#x430;&#x432;&#x43B;&#x44F;&#x435;&#x442;&#x441;&#x44F;
        &#x441; CLEO)</td>
      <td style="text-align:left">
        <p>GTA III
          <br />Vice City</p>
        <p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>file</b>
        </p>
        <p><code>{$USE file}</code>
        </p>
      </td>
      <td style="text-align:left">&#x43F;&#x43B;&#x430;&#x433;&#x438;&#x43D; FileSystemOperations
        <br />(&#x43F;&#x43E;&#x441;&#x442;&#x430;&#x432;&#x43B;&#x44F;&#x435;&#x442;&#x441;&#x44F;
        &#x441; CLEO)</td>
      <td style="text-align:left">
        <p>GTA III
          <br />Vice City</p>
        <p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>bitwise</b>
        </p>
        <p><code>{$USE bitwise}</code>
        </p>
      </td>
      <td style="text-align:left">&#x43F;&#x43B;&#x430;&#x433;&#x438;&#x43D; IntOperations
        <br />(&#x43F;&#x43E;&#x441;&#x442;&#x430;&#x432;&#x43B;&#x44F;&#x435;&#x442;&#x441;&#x44F;
        &#x441; CLEO4)</td>
      <td style="text-align:left">
        <p>GTA III
          <br />Vice City</p>
        <p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>clipboard</b>
        </p>
        <p><code>{$USE clipboard}</code>
        </p>
      </td>
      <td style="text-align:left">&#x43F;&#x43B;&#x430;&#x433;&#x438;&#x43D; ClipboardControl</td>
      <td style="text-align:left">
        <p>GTA III
          <br />Vice City</p>
        <p>GTA SA v1.0, v2.0, (v1.0 - SCR)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>memory</b>
        </p>
        <p><code>{$USE memory}</code>
        </p>
      </td>
      <td style="text-align:left">&#x43F;&#x43B;&#x430;&#x433;&#x438;&#x43D; MemoryModule</td>
      <td style="text-align:left">GTA III
        <br />Vice City</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>CLEO+</b>
        </p>
        <p><code>{$USE CLEO+}</code>
        </p>
      </td>
      <td style="text-align:left">&#x43F;&#x43B;&#x430;&#x433;&#x438;&#x43D; CLEO+</td>
      <td style="text-align:left">GTA SA v1.0, v2.0, (v1.0 - SCR)</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>newOpcodes</b>
        </p>
        <p><code>{$USE newOpcodes}</code>
        </p>
      </td>
      <td style="text-align:left">&#x43F;&#x43B;&#x430;&#x433;&#x438;&#x43D; newOpcodes</td>
      <td style="text-align:left">GTA SA v1.0, v2.0</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>vcmobile</b>
        </p>
        <p><code>{$USE vcmobile}</code>
        </p>
      </td>
      <td style="text-align:left">Vice City &#x43D;&#x430; &#x43C;&#x43E;&#x431;&#x438;&#x43B;&#x44C;&#x43D;&#x44B;&#x445;
        &#x443;&#x441;&#x442;&#x440;&#x43E;&#x439;&#x441;&#x442;&#x432;&#x430;&#x445;</td>
      <td
      style="text-align:left">Vice City</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>ios</b>
        </p>
        <p><code>{$USE ios}</code>
        </p>
      </td>
      <td style="text-align:left">GTA SA &#x43D;&#x430; iOS</td>
      <td style="text-align:left">SA Mobile</td>
    </tr>
  </tbody>
</table>

Допускается использование опкодов из источников, не перечисленных выше, при этом компилятор не будет требовать использование директивы `{$USE}`.

