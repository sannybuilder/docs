# Constants

**A constant** is an identifier with a predefined value. Contrary to a variable the value of the constant can’t be changed in run-time. At compilation the constant name is replaced with the value associated with it. Constant values can be numeric \(numerals\) and string \(string literals\), and contain an expression.

To define new constant use the construct `CONST..END`. It syntax looks like this:

`CONST  
<constant name> = <constant value>  
END`

The _constant name_ is any allowed identifier \(letters, numbers and “\_”\). There are reserved names that can’t be used, as Continue, True, And and so on. The _constant value_ may be a number \(a model identifier, a label\); a string; an expression \(for example class or variable\); another constant.

Example:

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

At compilation the constant _MoneyRequired_ will be replaced with the number `30` and _PlayerMoney_ with `$PLAYER_CHAR.Money`

The compiler also uses 2 internal constants `True` and `False` which values are equal to `1` and `0` respectively.

You can use the constant anywhere except the case:

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

Also there are the limits with using of a complex expression as a constant.

The list of the constants could be called at any place of the code by pressing `Ctrl + [space]`.

