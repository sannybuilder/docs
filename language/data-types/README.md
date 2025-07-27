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

Floating-point numbers include whole and fractional parts separated by a dot (e.g., `-100.0`, `-1.0`, `-22.434`).

{% hint style="info" %}
GTA III, unlike other titles, decimals are stored as [16-bit integers](https://gtamods.com/wiki/Talk:Mission_Scripting_\(Overview\)#Fixed-point_remark) with a step size of **0.0625**, meaning values like `0.063` are rounded to `0.0625`.
{% endhint %}

## String Literals

Text in **single quotes** (`'...'`) is a [null-terminated string](https://en.wikipedia.org/wiki/String_\(computer_science\)#Null-terminated), limited to `7` (III, VC) or `15` (SA) characters.

```pascal
script_name 'MAIN'
```

Empty strings like `''` are allowed.



Text in **double quotes** (`"..."`) is a [length-prefixed string](https://en.wikipedia.org/wiki/String_\(computer_science\)#Length-prefixed), with a maximum of `255` characters.

```cpp
write_debug "Hello, world!"
```

Empty strings like `""` are also allowed.

\
Use `\` to escape quotes or special characters:

```cpp
write_debug "Hello, \"world\"! \n 'Here we go!'"
```

## Model Names

Model IDs defined in `.ide` files can be referenced by `#` followed by a valid model name.&#x20;

```php
request_model #CELLPHONE
```

