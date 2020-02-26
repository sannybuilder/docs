# Constants

A **constant** is an identifier with a predefined value. Contrary to a [variable ](variables.md)the value of the constant can not be changed in run-time. During compilation the constant name is replaced with the value associated with it. The constant values can be numeric \(numerals\) and string \(string literals\), and contain an expression.

## Syntax

To define a new constant use the `CONST..END` construct:

`CONST  
    <constant name> = <constant value>  
END`

The `constant name` is any allowed identifier \(any combination of letters, numbers and `_`\). There are reserved names that can not be used, such as `Continue`, `True`, `And` and few others.   
The `constant value` might be a number \(also a model identifier or a label\); a string; an expression \(for example a class or a variable\); another constant.

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

At compilation the constant `MoneyRequired` will be replaced with the number `30` and `PlayerMoney` with `$PLAYER_CHAR.Money`

The compiler also uses 2 internal constants `True` and `False` which values are equal to `1` and `0` respectively.

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

Also there are some limitations when using a complex expression as the constant value.

