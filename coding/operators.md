# Operators

Sanny Builder supports many common operations to be written without an explicit opcode. The compiler, in this context, analyzes both the left and right sides of the expression as well as the operator between them to determine the appropriate opcode to use.

Due to the nature of the language, there are different opcodes for different types of data involved in operations. For instance, adding integer values requires a distinct opcode compared to adding two floating-point values. In some scenarios, it requires the upfront [declaration](variables.md#declaring-a-variable-type) of variable types, so the compiler can select the appropriate opcode.

The majority of supported operations in Sanny Builder involve just two operands: one on the left-hand side (**LHS**) and another on the right-hand side (**RHS**).

### Assignment

* `LHS = RHS` - an assignment operation. `RHS` is a numeric constant, variable, or string literal. In this context, `LHS` always refers to a variable.
* `LHS += RHS` - an addition operation. `LHS` and `RHS` must be of the same type, either integer or float. The value of `LHS` gets incremented by the value of `RHS`.
* `LHS -= RHS` - a subtraction operation
* `LHS *= RHS` - a multiplication operation
* `LHS /= RHS` - a division operation

The following operations require the `CLEO` extension (`{$USE CLEO}` or `{$CLEO}`).

* `LHS = value1 + value2` - add two integer values together and write the result in `LHS`
* `LHS = value1 - value2` - subtract one integer value from another and write the result in `LHS`
* `LHS = value1 * value2` - multiply two integer values and write the result in `LHS`
* `LHS = value1 / value2` - divide one integer value by another and write the result in `LHS`

### Comparison

* `LHS == RHS` - an "equal to" operation. Both sides must have the same value for the comparison to return true
* `LHS > RHS` - a "greater than" operation
* `LHS >= RHS` - a "greater than or equal to" operation
* `LHS < RHS` - a "less than" operation
* `LHS <= RHS` - a "less than or equal to" operation
* `LHS <> RHS` - a "not equal" operation. Both sides must have different values for the comparison to return true

{% hint style="info" %}
The language does not have a dedicated Boolean type. The result of each comparison only affects the current [IF statement](conditions.md).
{% endhint %}

### Bitwise

The game lacks native support for bitwise operations, making them accessible exclusively through the use of a [CLEO plugin](https://library.sannybuilder.com/#/sa/bitwise). The `bitwise` [extension](../edit-modes/extensions.md) must be enabled to use the following operations (`{$USE bitwise}`).

| Operation                         | Opcode | Expression    |
| --------------------------------- | ------ | ------------- |
| AND                               | 0B10   | 0@ = 1@ & 2@  |
| OR                                | 0B11   | 0@ = 1@ \| 2@ |
| XOR                               | 0B12   | 0@ = 1@ ^ 2@  |
| NOT                               | 0B13   | 0@ = \~1@     |
| MOD                               | 0B14   | 0@ = 1@ % 2@  |
| Shift Right                       | 0B15   | 0@ = 1@ >> 2@ |
| Shift Left                        | 0B16   | 0@ = 1@ << 2@ |
| AND (compound assignment)         | 0B17   | 0@ &= 1@      |
| OR (compound assignment)          | 0B18   | 0@ \|= 1@     |
| XOR (compound assignment)         | 0B19   | 0@ ^= 1@      |
| NOT (mutable)                     | 0B1A   | \~0@          |
| MOD (compound assignment)         | 0B1B   | 0@ %= 1@      |
| Shift Right (compound assignment) | 0B1C   | 0@ >>= 1@     |
| Shift Left (compound assignment)  | 0B1D   | 0@ <<= 1@     |

### Timed addition and subtraction

The game natively supports timed addition and subtraction, providing FPS-independent calculations in relevant contexts. Read an [article](https://gtamods.com/wiki/SCM\_language#Operators) on GTAMods.com for more information.

| Operation                                  | Opcode | Expression      |
| ------------------------------------------ | ------ | --------------- |
| ADD\_TIMED\_VAL\_TO\_FLOAT\_VAR            | 0078   | $var +=@ 5.0    |
| ADD\_TIMED\_VAL\_TO\_FLOAT\_LVAR           | 0079   | 0@ +=@ 5.0      |
| ADD\_TIMED\_FLOAT\_VAR\_TO\_FLOAT\_VAR     | 007A   | $var1 +=@ $var2 |
| ADD\_TIMED\_FLOAT\_LVAR\_TO\_FLOAT\_LVAR   | 007B   | 0@ +=@ 1@       |
| ADD\_TIMED\_FLOAT\_VAR\_TO\_FLOAT\_LVAR    | 007C   | 0@ +=@ $var     |
| ADD\_TIMED\_FLOAT\_LVAR\_TO\_FLOAT\_VAR    | 007D   | $var +=@ 1@     |
| SUB\_TIMED\_VAL\_FROM\_FLOAT\_VAR          | 007E   | $var -=@ 5.0    |
| SUB\_TIMED\_VAL\_FROM\_FLOAT\_LVAR         | 007F   | 0@ -=@ 5.0      |
| SUB\_TIMED\_FLOAT\_VAR\_FROM\_FLOAT\_VAR   | 0080   | $var1 -=@ $var2 |
| SUB\_TIMED\_FLOAT\_LVAR\_FROM\_FLOAT\_LVAR | 0081   | 0@ -=@ 1@       |
| SUB\_TIMED\_FLOAT\_VAR\_FROM\_FLOAT\_LVAR  | 0082   | 0@ -=@ $var     |
| SUB\_TIMED\_FLOAT\_LVAR\_FROM\_FLOAT\_VAR  | 0083   | $var -=@ 1@     |

### Cast assignment

Casting operations convert a value from one type to another. The game supports a conversion between `Integer` and `Float` types.

{% hint style="info" %}
The use of the operator =# requires that types of both variables are [known](variables.md#declaring-a-variable-type).
{% endhint %}

| Operation                        | Opcode | Expression |
| -------------------------------- | ------ | ---------- |
| CSET\_VAR\_INT\_TO\_VAR\_FLOAT   | 008C   | $i =# $f   |
| CSET\_VAR\_FLOAT\_TO\_VAR\_INT   | 008D   | $f =# $i   |
| CSET\_LVAR\_INT\_TO\_VAR\_FLOAT  | 008E   | 0@ =# $f   |
| CSET\_LVAR\_FLOAT\_TO\_VAR\_INT  | 008F   | 1@ =# $i   |
| CSET\_VAR\_INT\_TO\_LVAR\_FLOAT  | 0090   | $i =# 1@   |
| CSET\_VAR\_FLOAT\_TO\_LVAR\_INT  | 0091   | $f =# 0@   |
| CSET\_LVAR\_INT\_TO\_LVAR\_FLOAT | 0092   | 0@ =# 1@   |
| CSET\_LVAR\_FLOAT\_TO\_LVAR\_INT | 0093   | 1@ =# 0@   |
