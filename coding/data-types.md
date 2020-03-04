# Типы данных

Код разделен на отдельные элементы, каждый из которых обозначается по-своему и выполняет конкретную функцию в скрипте.

## Переменные

Если перед именем переменной \(комбинация букв, цифр, и `_`\) стоит знак `$` - это [глобальная переменная](variables.md#globalnye-peremennye).

```text
0004: $MyVar = 100
```

A [local variable](variables.md#local-variables) name may only be a number followed by `@`.  The number is the [local variable](variables.md#local-variables) index in the list of local variables unique to this script or a mission.

```text
0006: 100@ = 10
```

An `ADMA` \(**A**dvanced **D**irect **M**emory **A**ccess\) variable is a reference to the offset in the `main.scm` file. They serve as global variables, i.e. you can read from and write to an address in the `main.scm`. 

```text
$myVar = &0 // read first 4 bytes of the main.scm and write them to $myVar
&57 += &120(&231,4i) // can be used as an array element
```

`ADMA` variables don't affect the size of the global variables space in the `main.scm` header.

## Метки

Labels are used to reference the code location from unconditional or conditional jumps. They start with `:`followed by a valid identifier \(a label name\).

```text
:MyLabel
```

To reference the label from an opcode use `@`  and then write the label name.

```text
0002: jump @MyLabel
```

## Строковые литералы

A text enclosed between single quotes `' '` is a short string literal \(`15` characters max\).

```text
03A4: name_thread 'MAIN'
```

Blank strings are also allowed: `' '`.

A text enclosed between `" "` is a long string literal \(maximum length is determined by the opcode it uses\)

If the literal contains `"` you must write `\` before it.

```text
0662: write_debug_message "Hello, \"world\"! \n 'Here we go!'"
```

Blank strings are also allowed: `" "`.

## Строковые переменные

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

## Имена моделей

Models from `.ide` files can be referenced by`#` followed by the valid model name. 

```text
0247: request_model #CELLPHONE
```

## Числа в 16-ричном формате

`0x` - a hexadecimal number   
`-0x` - a negative hexadecimal number

```text
0004: $var = -0xBB08
```

A hexadecimal number has to be within the `-80000000..7FFFFFFF` range.

