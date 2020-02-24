# Data Types

`$` - a global variable

```text
0004: $MyVar = 100
```

`@` \(before an identifier\) - a label. The text directly after is used to reference the label in jumps

```text
0002: jump @MyLabel
```

`@` \(after a number\) - a local variable. The number is a [local variable](variables.md#local-variables) id.

```text
0006: 100@ = 10
```

`'...'` - a short string \(15 chars max\).

```text
03A4: name_thread 'MAIN'
```

Empty string is also allowed: `' '`

`"..."` - a long string \(maximum length is determined by the opcode it uses\)

Single quotes do not need anything special, but to use double quotes you must specify slash char  before a quote.

Empty string is also allowed: `" "`

```text
0662: write_debug_message "Hello, \"world\"! \n 'Here we go!'"
```

`s$` - a global string variable

```text
05A9: s$MyString = 'GLOBAL'
```

`@s` - a local string variable

```text
05AA: 1@s = 'LOCAL'
```

`v$` - a global long string variable

```text
06D1: v$MyString = "LONG_GLOBAL"
```

`@v` - a local long string variable

```text
06D2: 1@v = "LONG_LOCAL"
```

`#` - a model identifier from '.ide' files

```text
0247: request_model #CELLPHONE
```

`&` - ADMA \(Advanced Direct Memory Access\). Reads/writes the values within the SCM even not in the variables block. Does not affect the second segment size.

ADMA can be used same as a global variable.

```text
&57 += &120(&231,4i)
```

`0x` - a hexadecimal number   
`-0x` - a negative hexadecimal number

```text
0004: $var = -0xBB08
```

A number has to be within the `-80000000..7FFFFFFF` range.

