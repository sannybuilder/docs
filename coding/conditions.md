# Conditions

The `IF` operator evaluates one or more conditions and creates a new branch of code.

## Low-level IF statements

`00d6: if <N>  
  <condition 1>  
  <condition 2>  
...  
  <condition N+1>  
004D: jump_if_false <label>`

`N` means the total number of conditions within the IF statement and the way the evaluation of conditions happens. 

| N | Number of Conditions | Logical Operator |
| :--- | :--- | :--- |
| 0 | 1 | the IF statement is true if the condition is true |
| 1..7 | 2..8 | `AND` \(all conditions must be true for the IF statement to be true\) |
| 21..27 | 2..8 | `OR` \(at least one of the conditions must be true for the IF statement to be true\) |

{% hint style="info" %}
A single IF statement can contain up to 8 conditions. 
{% endhint %}

{% hint style="info" %}
Sanny Builder allows to omit  `0` after `IF. IF 0` and  `IF` are equivalent.
{% endhint %}

`<label>`- a name of the [label](data-types.md#labels) where script jumps if the IF statement is false.  
`<condition>` - any conditional opcode evaluating to `true` or `false` 

If you have the  `Conditions check` enabled in the [options](../options/general.md#check-conditions), you can replace the if number with the keywords `AND` or `OR`. The compiler calculates the correct value itself.

```text
if and 
    $var > 0
    $var2 == 10.0
jf @anywhere
```

The compiler writes the number `1` instead of `and`.

`IF AND` - conditions connected with the logical operator `AND` \(a replacement for `if 1..7`\)  
`IF OR` - conditions connected with the logical operator `OR` \(a replacement for `if 21..27`\)

## High-level Constructs

To make writing conditions easier there are high-level constructs that don't require any additional labels:

`IF <N>/AND/OR  
  <condition 1>  
  <condition 2>  
  ...  
  <condition N+1>  
THEN  
  <commands if the statement is true>  
END`

`IF <N>/AND/OR  
  <condition 1>  
  <condition 2>  
  ...  
  <condition N+1>  
THEN  
  <commands if the statement is true>  
ELSE  
  <commands if the statement is false>  
END`

A condition is created by the rules described for [low-level conditions](conditions.md#low-level-if-statements). After `THEN` you have to specify the command\(-s\) that are executed if the condition is met. After `ELSE` you have to specify the command\(-s\) that are executed if the condition is not met.

The `IF` statement is closed with the word `END`.

```text
if $var == 5
then
    Inc($var)
else
    Dec($var)
end
```

{% hint style="info" %}
The  [`Conditions check`](../options/general.md#check-conditions) option  has to be enabled.
{% endhint %}

{% hint style="info" %}
Nested IF statements are supported.
{% endhint %}

## Relational Operators

* a **`==`** b - a is equal to b 
* a **`>=`** b - a is greater than or equal to b 
* a **`>`** b - a is greater than b 
* a **`<`** b - a is less than b 
* a **`<=`** b - a is less than or equal to b 
* a **`<>`** b - a is not equal to b

`a` and `b` are operands. The compiler is able to figure out an opcode if one of the operands is a number or a [string literal](data-types.md#string-literals), or both [variable' type](variables.md#var-end-construct) is known.

