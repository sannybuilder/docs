# Built-in Commands

The following commands are built directly into the compiler and serve mostly as [syntactic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar).

## INC

Increments the first parameter by the second one. The first parameter is a [variable](variables.md).

```text
Inc($IntVariable, $Value)
=
$IntVariable += $Value
```

The second parameter is equal to `1` if isn't specified.

```text
Inc(1@)
=
1@ += 1
```

Since the version 3.06 it's possible to use the `++` operator that can be applied to variables and increments their value by one.

```text
$var++
=
$var += 1
```

## DEC

Decrements the first parameter by the second one. The first parameter is a variable.

```text
Dec($IntVariable, $Value)
=
$IntVariable -= $Value
```

The second parameter is equal to `1` if isn't specified.

```text
Dec(1@)
=
1@ -= 1
```

Since the version 3.06 it's possible to use the `--` operator that can be applied to variables and decrements their value by one.

```text
$var--
=
$var -= 1
```

## MUL

Multiplies the first parameter by the second one. The first parameter is a variable.

```text
Mul($IntVariable, $Value)
=
$IntVariable = $IntVariable * $Value
```

The second parameter is equal to `2` if isn't specified.

```text
Mul(1@)
=
1@ = 1@ * 2
```

## DIV

Divides the first parameter by the second one. The first parameter is a variable.

```text
Div($IntVariable, $Value)
=
$IntVariable = $IntVariable / $Value
```

The second parameter is equal to `2` if isn't specified.

```text
Div(1@)
=
1@ = 1@ / 2
```

## ALLOC 

This function sets the memory address for the [global variable](variables.md#global-variables). It has to be used only for the ones with custom names \(e.g. `$text`\). For variables with numeric names \(DMA-variables\), the memory address is calculated out of this number: the variable `$40` always occupy four bytes in the `main.scm` header starting at the offset 40\*4=160.

```text
Alloc($MyVar, 40) - the variable $MyVar will be compiled as $40
```

{% hint style="info" %}
See also `help\examples\alloc.txt`
{% endhint %}

## SQR

Multiplies the variable by itself.

```text
sqr($var) 
=
$var *= $var
```

{% hint style="info" %}
The variable type has to be [declared](variables.md#var-end-construct).
{% endhint %}

## RANDOM

This function generates a random number within the specified range.

```text
$rnd = random(1, $high)
```

This function can be used for both integer and floating-point variables. The opcode is selected based on the type of the result variable \(`$rnd` in this example\).

