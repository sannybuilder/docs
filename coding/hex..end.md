# HEX..END

Sanny Builder supports writing a raw content in an output file. All values within this construct are written in an output file without any checks.

{% hint style="info" %}
Use this feature only if you know what you're doing. Any mistakes will corrupt the script file making it unreadable by the game or a script editor.
{% endhint %}

## Syntax

`hex  
<any hexadecimal numbers>  
end`

```text
hex
    04 00 02 0800 04 01
end
```

This sequence of bytes is the compiled version of the opcode `0004: $2 = 1`, so the game will correctly read it and set the value of the variable `$2` to `1`.

You must specify each byte you're going to write with two digits. All spaces are ignored. The compiler treats any two digits with a space between them as a single byte value. A single digit \(`0..F`\) is prefixed with `0`. So, for example, a sequence of three letters`A B C` will be compiled as the number `0xAB0C`.

The `HEX..END` construct also accepts string literals, labels, global variables identifiers, model names. They are compiled without a preceding data type.

```text
:get_offset
hex
    04 00 02 $PLAYER_CHAR 01 @get_offset
end
```

This is the exact copy of the opcode `0004: $PLAYER_CHAR = @get_offset`

String literals are compiled as a sequence of characters enclosed in double quotes.

```text
hex
    "This is a string"
end
```

## Escape Sequences

The following escape sequences are supported within a string:

| Name | Escape Sequence | Byte Form |
| :--- | :--- | :--- |
| Null  | \0 | 00 |
| Backspace | \b | 08 |
| Tab | \t | 09 |
| Line Feed | \n | 0A |
| Carriage Return | \r | 0D |
| Numeric escape sequence | \x`nn` | `nn` |
| Escape char | \`char` | `char` |

```text
hex
    "\0\b\t\n\r\xDD"
end
```

It produces the following sequence of bytes: `00 08 09 0A 0D DD`.

Currently multiple spaces in a string literal are converted into a single one. Thus a line `"This    is  a     string"` is converted into `"This is a string"`. Use the backward slash character `\` to add multiple spaces in a string literal: `"This \ \ \ is \ a \ \ \ \ string"`.

## Using aDMA Numbers

Also you can use the [aDMA ](data-types.md)data type to write a numeric constant in an output file. The number after the `&` sign can be both positive or negative, decimal or hexadecimal.

```text
hex
    &1000 &-0xA33500 
end
```

This example produces the following sequence of bytes: `E8 03 00 CB 5C FF`.

