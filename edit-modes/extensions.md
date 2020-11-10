# Extensions

An **extension** is a set of new instructions added to the vanilla game. The CLEO library and its plugins is the most known way of adding those. 

To make Sanny Builder aware of the custom instructions and explicitly signal their intentional usage, a script must have `{$USE}` [directive](../coding/directives.md#usduse). The `{$USE}` directive enables a particular set of instructions \(see below the [list of extensions](extensions.md#extensions-list)\).

```text
{$USE CLEO}
{$USE ini}
{$USE CLEO+}
```

Each opcode included in Sanny Builder's [INI files](opcodes-list-scm.ini.md) has been categorized to belong to some extension. Currently it is done via the file `extensions.txt`. 

{% hint style="info" %}
See [\#74](https://github.com/sannybuilder/dev/issues/74) for more information on how this feature is expected to function in the future.
{% endhint %}

### Implicit Extensions

Vanilla opcodes have been included in the `default` extension that is implicitly available in any script. `{$USE default}` is possible but redundant. 

Using `{$CLEO}` directive also implies `{$USE CLEO}` so standard CLEO opcodes are available to the compiler already.

### Extensions List

Sanny Builder ships some common and recognized extensions for different edit modes:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Extension Name</th>
      <th style="text-align:left">Provided by</th>
      <th style="text-align:left">Edit Modes where available</th>
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
        <p>CLEO 2.0 for GTA III
          <br />CLEO 2.0 for Vice City</p>
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
        <p><b>CLEO 1.1</b>
        </p>
        <p><code>{$USE CLEO 1.1}</code>
        </p>
      </td>
      <td style="text-align:left">CLEO 1.1 for GTA III
        <br />CLEO 1.1 for Vice City
        <br />(not recommended, prefer CLEO 2.0)</td>
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
      <td style="text-align:left">IniFiles.cleo plugin
        <br />(ships with CLEO)</td>
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
      <td style="text-align:left">FileSystemOperations plugin
        <br />(ships with CLEO)</td>
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
      <td style="text-align:left">IntOperations plugin
        <br />(ships with CLEO4)</td>
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
      <td style="text-align:left">ClipboardControl plugin</td>
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
      <td style="text-align:left">MemoryModule plugin</td>
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
      <td style="text-align:left">CLEO+ plugin</td>
      <td style="text-align:left">GTA SA v1.0, v2.0, (v1.0 - SCR)</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>newOpcodes</b>
        </p>
        <p><code>{$USE newOpcodes}</code>
        </p>
      </td>
      <td style="text-align:left">newOpcodes plugin</td>
      <td style="text-align:left">GTA SA v1.0, v2.0</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>vc mobile</b>
        </p>
        <p><code>{$USE vc mobile}</code>
        </p>
      </td>
      <td style="text-align:left">Vice City on mobile devices</td>
      <td style="text-align:left">Vice City</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>ios</b>
        </p>
        <p><code>{$USE ios}</code>
        </p>
      </td>
      <td style="text-align:left">GTA SA on iOS</td>
      <td style="text-align:left">SA Mobile</td>
    </tr>
  </tbody>
</table>

Using opcodes from the third-party libraries not listed there is possible and the compiler will not be warning you.

