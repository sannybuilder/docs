# Data Types

Certain code elements must start or end with specific characters. They help the compiler to recognize their meaning. The following list is final and contains all types of data known to the compiler.

## Literals

### Numbers

Sanny Builder supports 32-bit integers and floating-point numbers. Integers are whole numbers represented as a string of digits from `0` to `9`. Negative numbers are denoted by a minus sign (`-`) in front of them. Examples of valid integer numbers include `0`, `1`, `123`, `-10`, and `-900000`.

Sanny also supports hexadecimal and binary notation for integer numbers. Hexadecimal numbers are represented as a string of digits from `0` through `9` and letters from `A` through `F`, prefixed with `0x` or `-0x`. For instance, `0xA`, `0xFFFF`, `-0x90`. Binary numbers are represented as a string of digits `0` and `1`, prefixed with `0b` or `-0b`. For example, `0b0`, `0b10110`, `-0b10000`.

{% hint style="success" %}
For your convenience Sanny's IDE has [shortcuts](../editor/hotkeys.md) `Ctrl`+`H` and `Ctrl`+`B` to convert numbers between decimal and hexadecimal/binary notations.
{% endhint %}

The maximum integer number is `2147483647` (`0x7FFFFFFF`), and the minimum is `-2147483648` (`-0x80000000`).

Floating-point numbers consist of the whole and fractional parts separated by a period (`.`). Examples include `-100.0`, `-1.0`, and `-22.434`.

{% hint style="info" %}
Unlike other titles, [GTA III uses 16-bit integer numbers](https://gtamods.com/wiki/Talk:Mission\_Scripting\_\(Overview\)#Fixed-point\_remark) to store decimal values. It means a precision of those values has a step value of 0.0625 units. I.e. you can use a number 0.0625, while 0.0630 will be rounded to 0.0625.
{% endhint %}

### String literals

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

## Variables

A [global variable](variables.md#global-variables) starts with `$` followed by a valid identifier (any combination of letters, digits and `_`).

```
0004: $MyVar = 100
```

A [local variable](variables.md#local-variables) name may only be a number followed by `@`.  The number is the local variable index in the list of local variables [allocated](../scm-documentation/gta-limits.md) to this script or a mission.

```
0006: 100@ = 10
```

An `ADMA` (**A**dvanced **D**irect **M**emory **A**ccess) variable is a reference to an address within in the `main.scm` file. They serve as global variables, i.e. you can read from and write to the address in the `main.scm`.&#x20;

```
$myVar = &0 // read first 4 bytes of the main.scm (&0) and write the value to $myVar
&57 += &120(&231,4i) // can be used as an array element
```

`ADMA` variables don't affect the size of the global variables space in the `main.scm` header.

## Labels

Labels are used to reference the code location from unconditional (opcodes `0002`, `0050`) or conditional jumps (opcode `004D`). They start with `:`followed by a valid identifier (a label name).

```
:MyLabel
```

To reference the label from an opcode use `@`  and then write the label name.

```
0002: jump @MyLabel
```

If a label name is written as a standalone statement followed by `()`  it represents a call to the subroutine with the `gosub` command:

```
// the following statements are equivalent
MyLabel()
gosub @MyLabel
```

## String Variables

A global variable containing a short string literal starts with `s$`.

```
05A9: s$MyString = 'GLOBAL'
```

A local variable containing a short string literal starts with`@s`.&#x20;

```
05AA: 1@s = 'LOCAL'
```

A global variable containing a long string literal starts with `v$`.&#x20;

```
06D1: v$MyString = "LONG_GLOBAL"
```

A local variable containing a long string literal starts with`@v`.&#x20;

```
06D2: 1@v = "LONG_LOCAL"
```

## Model Names

Models defined in `.ide` files can be referenced by`#` followed by the model name.&#x20;

```
0247: request_model #CELLPHONE
```
