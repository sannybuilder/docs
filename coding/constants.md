# Constants

A **constant** is an identifier with an associated predefined value. The identifier must be unique in the current compilation context (the main source file and all [includes](directives.md#usdinclude)).

In compile-time the constant gets replaced with the value associated with it, e.g., a number or a string literal. Contrary to a variable the value of the constant cannot be changed in run-time.&#x20;

Constants are declared either statically or dynamically. Each [edit mode](../edit-modes/) can load static constant definitions from a file using the `<constants>` parameter in the `modes.xml`. Dynamic declarations get created in the script code with the syntax outlined below.

## Syntax

To declare a new constant in the code, use the `const` keyword.

```pascal
const <constant name> = <constant value>    
```

A constant name is any allowed identifier (a combination of letters, numbers and `_`). There are names reserved by the compiler that cannot be used, such as `Continue`, `Break`, `And` etc. (see `compiler.ini)`.\
\
A constant value might be a number (also a [model identifier](data-types.md#model-names) or a [label](data-types.md#labels)); a [string literal](data-types.md#string-literals); a [variable](variables.md) (also a [class property](classes.md#properties)); another constant.

For example:

```pascal
const x = 5
```

You can declare multiple constants separating each declaration with a comma like this:

```pascal
const a = 1, b = 2, c = 3
```

If you prefer to have each declaration on its own line, conclude them in a `CONST..END` construct:

```pascal
const
    a = 1
    b = 2
    c = 3
end
```

More complex example:

```pascal
var
   $PLAYER_CHAR: Player
end

const
    MoneyRequired = 30
    PlayerMoney = $PLAYER_CHAR.Money
end

if
    PlayerMoney > MoneyRequired
then
    PlayerMoney += -1
end
```

During compilation the constant `MoneyRequired` gets replaced with the number `30` and `PlayerMoney` with `$PLAYER_CHAR.Money`

When the [Language service](../editor/language-service.md) is enabled, a list of constants gets displayed after pressing `Ctrl+Space`.

