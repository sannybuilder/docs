# Data Types

## Numbers

Sanny Builder supports 32-bit integers and floating-point numbers.&#x20;

### Integers

Integers are whole numbers using digits 0-9, with an optional minus sign for negatives (e.g., `0`, `123`, `-10`).

Also supported:

* **Hexadecimal**: Digits 0-9 and letters A-F, prefixed with `0x` or `-0x` (e.g., `0xA`, `-0x90`).
* **Binary**: Digits 0 and 1, prefixed with `0b` or `-0b` (e.g., `0b10110`, `-0b10000`).

{% hint style="success" %}
For your convenience Sanny's IDE has [shortcuts](../../editor/hotkeys.md) `Ctrl`+`H` and `Ctrl`+`B` to convert numbers between decimal and hexadecimal/binary notations.
{% endhint %}

The maximum integer number is `2147483647` (`0x7FFFFFFF`), and the minimum is `-2147483648` (`-0x80000000`).

### Floats

Floating-point numbers consist of the whole and fractional parts separated by a period (`.`). Examples include `-100.0`, `-1.0`, and `-22.434`.

{% hint style="info" %}
GTA III, unlike other titles, uses [16-bit integer numbers](https://gtamods.com/wiki/Talk:Mission_Scripting_\(Overview\)#Fixed-point_remark) to store decimal values. It means a precision of those values has a step value of 0.0625 units. I.e. you can use a number 0.0625, while 0.0630 will be rounded to 0.0625.
{% endhint %}

## String Literals

A text enclosed between single quotes `' '` is a [null-terminated string](https://en.wikipedia.org/wiki/String_\(computer_science\)#Null-terminated). It is limited to `15` characters.

```pascal
03A4: script_name 'MAIN'
```

Empty strings are allowed: `''`.

A text enclosed between `" "` is a [length-prefixed string](https://en.wikipedia.org/wiki/String_\(computer_science\)#Length-prefixed). Its maximum length cannot exceed `255` characters.

```pascal
0662: write_debug_message "Hello, world!"
```

If the literal contains `"` you must write `\` before it.

<pre class="language-pascal"><code class="lang-pascal"><strong>0662: write_debug_message "Hello, \"world\"! \n 'Here we go!'"
</strong></code></pre>

Empty strings are allowed: `""`.

## Model Names

Model IDs defined in `.ide` files can be referenced by`#` followed by a valid model name.&#x20;

```pascal
0247: request_model #CELLPHONE
```
