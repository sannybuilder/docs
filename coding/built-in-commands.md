# Built-in Commands

The following commands are built directly into the compiler and serve mostly as [syntactic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar).

## INC

Increments the first parameter by the second one. The first parameter is a [variable](variables.md).

```
Inc($IntVariable, $Value)
=
$IntVariable += $Value
```

The second parameter is equal to `1` if isn't specified.

```
Inc(1@)
=
1@ += 1
```

Since the version 3.06 it's possible to use the `++` operator that can be applied to variables and increments their value by one.

```
$var++
=
$var += 1
```

## DEC

Decrements the first parameter by the second one. The first parameter is a variable.

```
Dec($IntVariable, $Value)
=
$IntVariable -= $Value
```

The second parameter is equal to `1` if isn't specified.

```
Dec(1@)
=
1@ -= 1
```

Since the version 3.06 it's possible to use the `--` operator that can be applied to variables and decrements their value by one.

```
$var--
=
$var -= 1
```

## MUL

Multiplies the first parameter by the second one. The first parameter is a variable.

```
Mul($IntVariable, $Value)
=
$IntVariable = $IntVariable * $Value
```

The second parameter is equal to `2` if isn't specified.

```
Mul(1@)
=
1@ = 1@ * 2
```

## DIV

Divides the first parameter by the second one. The first parameter is a variable.

```
Div($IntVariable, $Value)
=
$IntVariable = $IntVariable / $Value
```

The second parameter is equal to `2` if isn't specified.

```
Div(1@)
=
1@ = 1@ / 2
```

## ALLOC 

This function sets the offset of a [global variable](variables.md#global-variables) at the global variable space that exists in the beginning of the `main.scm` header.

It's only meaningful for custom variables (e.g. `$text`) not defined in the `CustomVariables.ini`. [`DMA`-variables](variables.md#global-variables) always get their offset based on the number in their names, e.g the variable `$40` always occupies four bytes at the offset `160` (40\*4).

The first parameter must be a global variable, the second parameter must be a positive integer number or zero.

```
Alloc($MyVar, 40) - the variable $MyVar will be compiled as $40
```

{% hint style="info" %}
See also `help\examples\alloc.txt`
{% endhint %}

## SQR

Multiplies the variable by itself.

```
sqr($var) 
=
$var *= $var
```

{% hint style="info" %}
The variable type has to be [declared](variables.md#var-end-construct).
{% endhint %}

## RANDOM

This function generates a random number within the specified range.

```
$rnd = random(1, $high)
```

This function can be used for both integer and floating-point variables. The opcode is selected based on the type of the result variable (`$rnd` in this example).
