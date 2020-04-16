# Hotkeys

Sanny Builder supports standard keyboard shortcuts for the file and text operations `(Ctrl+N`, `Ctrl+Z`, etc\). There are extra hotkeys to make scripting easier. Some of them are also [customizable](editor/options/hotkeys.md).

<table>
  <thead>
    <tr>
      <th style="text-align:left">Key/Combo</th>
      <th style="text-align:left">Operation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Main Menu</b>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><code>F5</code>
      </td>
      <td style="text-align:left">open file as a script and disassemble</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>F6</code>
      </td>
      <td style="text-align:left">compile the editor content to a script file</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>F7</code>
      </td>
      <td style="text-align:left">compile the editor content to a script file and copy the file to the scripts
        directory for the current game</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>F8</code>
      </td>
      <td style="text-align:left">run the game for the current <a href="edit-modes/">edit mode</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>F10</code>
      </td>
      <td style="text-align:left">open the <a href="editor/options/">options</a> window</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>F12</code>
      </td>
      <td style="text-align:left">open documentation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Text</b>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><code>TAB</code>, <code>Shift+TAB</code>
      </td>
      <td style="text-align:left">move the selected text to the left / right (tab)</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>Ctrl+Alt+A</code>
        </p>
        <p><code>Ctrl+Alt+D</code>
        </p>
      </td>
      <td style="text-align:left">move the selected text to the left / right (by one symbol)</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>Ctrl+Alt+B</code>
        </p>
        <p><code>Ctrl+Alt+N</code>
        </p>
        <p><code>Ctrl+Alt+M</code>
        </p>
      </td>
      <td style="text-align:left">toggle different modes of the text selection: Normal, Columnar (same as
        selection with pressed <code>Alt</code>), Lines</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>Ctrl+Shift+U</code>
        </p>
        <p><code>Ctrl+Shift+L</code>
        </p>
      </td>
      <td style="text-align:left">make word uppercase / lowercase</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Num+</code>
      </td>
      <td style="text-align:left">increase the text size (zoom in)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Num-</code>
      </td>
      <td style="text-align:left">decrease the text size (zoom out)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+T</code>
      </td>
      <td style="text-align:left">delete word</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Y</code>
      </td>
      <td style="text-align:left">delete line</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Shift+Y</code>
      </td>
      <td style="text-align:left">clear line</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Q</code>
      </td>
      <td style="text-align:left"><a href="features.md#commenting-code">comment / uncomment</a> line</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Navigation</b>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Shift+B</code>
      </td>
      <td style="text-align:left">jump between brackets: <code>{}</code>, <code>()</code>, <code>&lt;&gt;</code>, <code>[]</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>Ctrl+Shift+Num8</code>
        </p>
        <p><code>Ctrl+Shift+Num2</code>
        </p>
      </td>
      <td style="text-align:left">scroll the page one line up / down</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>Ctrl+ScrollUp</code> 
        </p>
        <p><code>Ctrl+ScrollDown</code>
        </p>
      </td>
      <td style="text-align:left">page up / down</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Shift+0..9</code>
      </td>
      <td style="text-align:left">toggle a <a href="features.md#bookmarks-quick-jump">bookmark</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+0..9</code>
      </td>
      <td style="text-align:left">jump at the <a href="features.md#bookmarks-quick-jump">bookmark</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+G</code>
      </td>
      <td style="text-align:left">go to line</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>Ctrl+Num4</code>
        </p>
        <p><code>Ctrl+Num6</code>
        </p>
      </td>
      <td style="text-align:left"><a href="features.md#instasearch">search </a>the word under the cursor
        below/above in the code</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Num2</code>
      </td>
      <td style="text-align:left"><a href="features.md#instasearch">jump </a>to the label under the cursor</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Num8</code>
      </td>
      <td style="text-align:left">return the cursor back to the previous position (before <a href="features.md#instasearch">InstaSearch</a>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Enter</code>
      </td>
      <td style="text-align:left">open the file which name is under the cursor (see also <a href="coding/directives.md#usdinclude">relative path priorities</a>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Code</b>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Space</code>
      </td>
      <td style="text-align:left">show the list of classes / class members / models / labels / variables
        / missions</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Shift+Space</code>
      </td>
      <td style="text-align:left">show the list of parameters for the current class command</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Shift+C</code>
      </td>
      <td style="text-align:left">insert the <a href="features.md#player-coordinates-management">player&apos;s coordinates</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Shift+E</code>
      </td>
      <td style="text-align:left">insert the <a href="features.md#player-coordinates-management">player&apos;s z_angle</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>F1</code>
      </td>
      <td style="text-align:left">search opcode with the word under the cursor (with ignoring of <code>_</code> and <code>.</code>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+F1</code>
      </td>
      <td style="text-align:left">search opcode with the word under the cursor (without ignoring of <code>_</code> and <code>.</code>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>F2</code>
      </td>
      <td style="text-align:left">use <a href="features.md#code-snippets">code snippet</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+J</code>
      </td>
      <td style="text-align:left">show list of <a href="features.md#code-templates">code templates</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+M</code>
      </td>
      <td style="text-align:left">start/stop recording of a <a href="features.md#keypress-recording-macro">macro </a>(keystroke
        pressings sequence)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+P</code>
      </td>
      <td style="text-align:left">replay <a href="features.md#keypress-recording-macro">macro</a>/pause while
        processing</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+H</code>
      </td>
      <td style="text-align:left">convert a number under the cursor from decimal to hexadecimal and vice
        versa</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+Alt+H</code>
      </td>
      <td style="text-align:left">convert a model name under the cursor to its numeric ID and vice versa</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Misc</b>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Ctrl+~</code>
      </td>
      <td style="text-align:left">open <a href="console.md">console</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>Alt+S</code>
      </td>
      <td style="text-align:left">(when the list of models is active) re-sort the list</td>
    </tr>
  </tbody>
</table>