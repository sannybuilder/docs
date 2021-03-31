# Data Types

Certain code elements must start or end with specific characters. They help the compiler to recognize their meaning. The following list is final and contains all types of data known to the compiler.  

## Variables

A [global variable](variables.md#global-variables) starts with `$` followed by a valid identifier \(any combination of letters, digits and `_`\).

```text
0004: $MyVar = 100
```

A [local variable](variables.md#local-variables) name may only be a number followed by `@`.  The number is the local variable index in the list of local variables [allocated](../scm-documentation/gta-limits.md) to this script or a mission.

```text
0006: 100@ = 10
```

An `ADMA` \(**A**dvanced **D**irect **M**emory **A**ccess\) variable is a reference to an address within in the `main.scm` file. They serve as global variables, i.e. you can read from and write to the address in the `main.scm`. 

```text
$myVar = &0 // read first 4 bytes of the main.scm (&0) and write the value to $myVar
&57 += &120(&231,4i) // can be used as an array element
```

`ADMA` variables don't affect the size of the global variables space in the `main.scm` header.

## Labels

Labels are used to reference the code location from unconditional \(opcodes `0002`, `0050`\) or conditional jumps \(opcode `004D`\). They start with `:`followed by a valid identifier \(a label name\).

```text
:MyLabel
```

To reference the label from an opcode use `@`  and then write the label name.

```text
0002: jump @MyLabel
```

If a label name is written as a standalone statement followed by `()`  it represents a call to the subroutine with the `gosub` command:

```text
// the following statements are equivalent
MyLabel()
gosub @MyLabel
```

## String literals

A text enclosed between single quotes `' '` is a short string literal \(`15` characters max\).

```text
03A4: script_name 'MAIN'
```

Blank strings are also allowed: `' '`.

A text enclosed between `" "` is a long string literal \(maximum length is determined by the opcode it uses\)

If the literal contains `"` you must write `\` before it.

```text
0662: write_debug_message "Hello, \"world\"! \n 'Here we go!'"
```

Blank strings are also allowed: `" "`.

## String Variables

A global variable containing a short string literal starts with `s$`.

```text
05A9: s$MyString = 'GLOBAL'
```

A local variable containing a short string literal starts with`@s`. 

```text
05AA: 1@s = 'LOCAL'
```

A global variable containing a long string literal starts with `v$`. 

```text
06D1: v$MyString = "LONG_GLOBAL"
```

A local variable containing a long string literal starts with`@v`. 

```text
06D2: 1@v = "LONG_LOCAL"
```

## Model Names

Models defined in `.ide` files can be referenced by`#` followed by the model name. 

```text
0247: request_model #CELLPHONE
```

## Hexadecimal Numbers

`0x` - a hexadecimal number   
`-0x` - a negative hexadecimal number

```text
0004: $var = -0xBB08
```

A hexadecimal number has to be within the `-80000000..7FFFFFFF` range.

