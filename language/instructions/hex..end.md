# HEX..END

Sanny Builder supports writing raw content into an output file. Within this construct, all values are directly written in an output file without undergoing any checks.

{% hint style="warning" %}
Use this feature only if you know what you're doing. Any mistakes will corrupt the script file making it unreadable by the game or a script editor.
{% endhint %}

## Syntax

```pascal
hex
<hexadecimal input>
end
```

```pascal
hex
  04 00 02 08 00 04 01
end
```

This sequence of bytes is the compiled version of the opcode `0004: $2 = 1`, so the game will correctly read it and set the value of the variable `$2` to `1`.

Each byte consists of two digits. The compiler ignores any spaces, effectively treating a pair of two digits separated by a space as one value. Additionally, when there's an unpaired digit, it is automatically prefixed with a leading `0`.

For example, a sequence of three letters `A B C` will be compiled as the number `0xAB0C`.

The `HEX..END` construct also accepts [string literals](../data-types/#string-literals), [labels](../data-types/#labels), [global variables](../data-types/variables.md#global-variables), [model names](../data-types/#model-names). They are compiled without a preceding data type byte.

```pascal
:get_offset
hex
    04 00 02 $PLAYER_CHAR 01 @get_offset
end
```

This is the exact copy of the opcode `0004: $PLAYER_CHAR = @get_offset`

A string literal enclosed in double quotes is compiled as a sequence of characters.

```pascal
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

```pascal
hex
    "\0\b\t\n\r\xDD"
end
```

It produces the following sequence of bytes: `00 08 09 0A 0D DD`.

## Entering large numbers

For convenience, large numbers can be prefixed with an `&` symbol. The number following the `&` symbol can be positive or negative, and it can be represented in either decimal or hexadecimal format.

```pascal
hex
    &1000 &-0xA33500
end
```

This example produces the following sequence of bytes: `E8 03 00 CB 5C FF`.

## Byte Repetition

In cases where it is necessary to repeat a specific byte multiple times, such as when creating a zero-filled buffer, indicate the count by appending `(n)` after the byte, where `n` is a positive integer number:

```pascal
hex
 00(10)
end
```

This syntax is equivalent to:

```pascal
hex
  00 00 00 00 00 00 00 00 00 00
end
```

Byte repetitions can be used multiple times within the same block, and they can also be set with a constant value.

```pascal
const n = 25

hex
00(n) 01(3) 02(4)
end
```

## Including binary files

`hex..end` allows usage of the `$INCLUDE` directive to embed the contents of a binary file directly into the script's body. The syntax is as follows:

```pascal
hex 
 {$INCLUDE <path>}
end
```

Path resolution follows the rules set for the [{$INCLUDE}](../directives.md#usdinclude) directive.
