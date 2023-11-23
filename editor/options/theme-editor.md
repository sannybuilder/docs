# Theme Editor

Theme Editor is a new built-in tool that replaces syntax highlighting options. It can be launched from the [Editor](editor.md#color-theme) tab.

![](../../.gitbook/assets/theme-editor-en.PNG)

Theme configuration includes colors and style for interface and code elements.

Each element has 3 properties: `Foreground`, `Background`, and `Style`. Some properties can be unavailable for certain elements.\
Available `style` elements are: **B** – bold, **I** – italic, **U** – underlined.

### **Interface Elements**

* **Editor** – text color and background of the main editing area
* **Active Line** – a line where the cursor is
* **Gutter** – area to the left of the editor
* **Bottom Panel** – status bar at the bottom of the editor
* **Bottom Panel Border** – color of section borders in the bottom panel

### Code elements

* [Comments](../../language/comments.md) – a text after `//` or between `{}` or `/* */`
* [Labels](../../language/data-types/) – identifiers starting with `@`
* [Variables](../../language/data-types/variables.md) – identifiers starting with `$` (global variables), or ending with `@` (local variables)\
  Also the [aDMA](../../language/data-types/) type (starts with `&`) and [arrays](../../language/data-types/arrays.md) are highlighted as variables.
* [Keywords](../../language/instructions/keywords.md) – the special words stored in the file `keywords.ini` (one for all [edit modes](../../edit-modes/)) and a file`keywords.txt` (one per edit mode)
* Numbers – integer and floating-point numbers
* Strings – a text between double quotes `" "` or single quotes `' '`
* Models – identifiers starting with `#`
* [Classes](../../language/instructions/classes.md) – the part of a class command before the `.` character
* [Commands](../../language/instructions/classes.md) – the part of a class command after the `.` character, or a [subroutine](../../language/data-types/#labels)
* [Directives ](../../language/directives.md)– a command starting with `{$`
* [Constants](../../language/data-types/constants.md) – identifiers, declared within the `CONST..END` construct. See also [Semantic highlighting](editor.md#editor-configuration).

{% hint style="info" %}
The highlighting configuration is also used when the code source is saved into the `RTF` or `HTML` formats.
{% endhint %}
