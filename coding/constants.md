# Constants

A **constant** is an identifier with a predefined value. Contrary to a variable the value of the constant can not be changed in run-time. In compile-time the constant gets replaced with the value associated with it. The value of the constant can be numeric \(numbers, [model names](data-types.md#model-names) or [labels](data-types.md#labels)\) and string \(string literals\), and contain an expression.

Constants are declared either statically or dynamically. Each [edit mode](../edit-modes/) can load static constant definitions from a file using the `<constants>` parameter in the `modes.xml`. Dynamic declarations are part of the script code and use the syntax outlined below.

## Syntax

To declare a new constant in the code use the `CONST..END` construct:

`CONST  
    <constant name> = <constant value>  
END`

A constant name is any allowed identifier \(a combination of letters, numbers and `_`\). There are names reserved by the compiler that can not be used, such as `Continue`, `Break`, `And`, etc \(see `compiler.ini)`.  
  
A constant value might be a number \(also a [model identifier](data-types.md#model-names) or a [label](data-types.md#labels)\); a [string literal](data-types.md#string-literals); a [variable](variables.md) \(also a [class property](classes.md#properties)\); another constant.

```text
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

A list of the currently defined constants is displayed after pressing `Ctrl+Space`.

## Limitations

You can use constants anywhere except the case:

```text
const
    VarName = $Var
    IndexName = 25
end
VarName[IndexName] = 0
```

To compile such expression, you must write the opcode, for example:

```text
0004: VarName[IndexName] = 0
```

Also there are some limitations with using an expression as the constant value.

