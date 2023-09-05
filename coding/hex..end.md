# HEX..END

Sanny Builder supports writing raw content into an output file. Within this construct, all values are directly written in an output file without undergoing any checks.

{% hint style="warning" %}
Use this feature only if you know what you're doing. Any mistakes will corrupt the script file making it unreadable by the game or a script editor.
{% endhint %}

## Syntax

```
hex
<hexadecimal input>
end
```

```
hex
  04 00 02 08 00 04 01
end
```

This sequence of bytes is the compiled version of the opcode `0004: $2 = 1`, so the game will correctly read it and set the value of the variable `$2` to `1`.

Each byte consists of two digits. The compiler ignores any spaces, effectively treating a pair of two digits separated by a space as one value. Additionally, when there's an unpaired digit, it is automatically prefixed with a leading `0`.

For example, a sequence of three letters `A B C` will be compiled as the number `0xAB0C`.

The `HEX..END` construct also accepts [string literals](data-types.md#string-literals), [labels](data-types.md#labels), [global variables](variables.md#global-variables), [model names](data-types.md#model-names). They are compiled without a preceding data type byte.

```
:get_offset
hex
    04 00 02 $PLAYER_CHAR 01 @get_offset
end
```

This is the exact copy of the opcode `0004: $PLAYER_CHAR = @get_offset`

A string literal enclosed in double quotes is compiled as a sequence of characters.

```
hex
    "This is a string"
end
```

## Escape Sequences

The following escape sequences are supported within a string literal:

| Name                    | Escape Sequence | Byte Form |
| ----------------------- | --------------- | --------- |
| Null                    | \0              | 00        |
| Backspace               | \b              | 08        |
| Tab                     | \t              | 09        |
| Line Feed               | \n              | 0A        |
| Carriage Return         | \r              | 0D        |
| Numeric escape sequence | \x`nn`          | `nn`      |
| Escape char             | \\`char`        | `char`    |

```
hex
    "\0\b\t\n\r\xDD"
end
```

It produces the following sequence of bytes: `00 08 09 0A 0D DD`.

Currently multiple spaces in a string literal are converted into a single one. Thus a line `"This    is  a     string"` is converted into `"This is a string"`. Use the backward slash character `\` to add multiple spaces in a string literal: `"This \ \ \ is \ a \ \ \ \ string"`.

## Entering large numbers

For convenience, large numbers can be prefixed with an `&` symbol. The number following the `&` symbol can be positive or negative, and it can be represented in either decimal or hexadecimal format.

```
hex
    &1000 &-0xA33500
end
```

This example produces the following sequence of bytes: `E8 03 00 CB 5C FF`.

## Byte Repetition

In cases where it is necessary to repeat a specific byte multiple times, such as when creating a zero-filled buffer, indicate the count by appending `(n)` after the byte, where `n` is a positive integer number:

```
hex
 00(10)
end
```

This syntax is equivalent to:

```
hex
  00 00 00 00 00 00 00 00 00 00
end
```

Byte repetitions can be used multiple times within the same block, and they can also be set with a constant value.

```
const n = 25

hex
00(n) 01(3) 02(4)
end
```

## Including binary files

`hex..end` allows usage of the `$INCLUDE` directive to embed the contents of a binary file directly into the script's body. The syntax is as follows:

```
hex 
 {$INCLUDE <path>}
end
```

Path resolution follows the rules set for the [{$INCLUDE}](directives.md#usdinclude) directive.
