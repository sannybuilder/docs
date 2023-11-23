# Data Types

## Numbers

### Integers

Sanny Builder supports 32-bit integers and floating-point numbers. Integers are whole numbers represented as a string of digits from `0` to `9`. Negative numbers are denoted by a minus sign (`-`) in front of them. Examples of valid integer numbers include `0`, `1`, `123`, `-10`, and `-900000`.

Sanny also supports hexadecimal and binary notation for integer numbers. Hexadecimal numbers are represented as a string of digits from `0` through `9` and letters from `A` through `F`, prefixed with `0x` or `-0x`. For instance, `0xA`, `0xFFFF`, `-0x90`. Binary numbers are represented as a string of digits `0` and `1`, prefixed with `0b` or `-0b`. For example, `0b0`, `0b10110`, `-0b10000`.

{% hint style="success" %}
For your convenience Sanny's IDE has [shortcuts](../../editor/hotkeys.md) `Ctrl`+`H` and `Ctrl`+`B` to convert numbers between decimal and hexadecimal/binary notations.
{% endhint %}

The maximum integer number is `2147483647` (`0x7FFFFFFF`), and the minimum is `-2147483648` (`-0x80000000`).

### Floats

Floating-point numbers consist of the whole and fractional parts separated by a period (`.`). Examples include `-100.0`, `-1.0`, and `-22.434`.

{% hint style="info" %}
GTA III, unlike other titles, uses [16-bit integer numbers](https://gtamods.com/wiki/Talk:Mission\_Scripting\_\(Overview\)#Fixed-point\_remark) to store decimal values. It means a precision of those values has a step value of 0.0625 units. I.e. you can use a number 0.0625, while 0.0630 will be rounded to 0.0625.
{% endhint %}

## String Literals

A text enclosed between single quotes `' '` is a short string literal (`15` characters max).

```
03A4: script_name 'MAIN'
```

Empty strings are allowed: `''`.

A text enclosed between `" "` is a long string literal (maximum length is determined by the opcode it uses)

```
0662: write_debug_message "Hello, world!"
```

If the literal contains `"` you must write `\` before it.

<pre><code><strong>0662: write_debug_message "Hello, \"world\"! \n 'Here we go!'"
</strong></code></pre>

Empty strings are allowed: `""`.

## Model Names

Model IDs defined in `.ide` files can be referenced by`#` followed by a valid model name.&#x20;

```
0247: request_model #CELLPHONE
```
