# Loops

A **loop** is a statement which allows code to be repeatedly executed. Sanny Builder supports three kinds of controls loops: [for](loops.md#for-end), [while](loops.md#while-end), [repeat](loops.md#repeat-until).

## FOR..END

The `FOR` loop has a strictly certain number of iterations \(repetitions\).

Syntax:  
`FOR <loop variable> = <initial value> TO/DOWNTO <final value> [step = 1]  
  <the loop body>  
END`

`<loop variable>` - a variable used as a counter for iterations  
`<initial value>` - a starting value of the loop variable \(any value including a [model identifier](data-types.md#model-names)\)  
`TO/DOWNTO` ****- increment or decrement the loop variable between iterations  
`<final value>` - a final value of the loop variable when finished \(any value including a model identifier\)`<step>` - an optional value the loop variable will be incremented or decremented with between iterations. By default its value equals to `1`.

```text
var
    $value: int = 0
    $final: int = 100
end

FOR $MyCounter = 1 to $final step 2
    $value += $mycounter
end
```

If the starting/final values or a step value contained in [variables](variables.md), these variables get the same type the loop variable has. If the loop variable is not declared with any type before using in the loop it gets the `Integer` type. In order to use the floating-point values as the `FOR` loop ranges, declare the loop variable with the `Float` type.

```text
var
    $MyCounter: float
end

FOR $MyCounter = 1.0 to $final step 2.0
end
```

Variables `$MyCounter` and `$final` both have the `Float` type after the loop.

## WHILE..END

Syntax:  
`WHILE <loop condition>  
  <the loop body>  
END`

```text
while not #AK47.Available
    wait 0
end
```

The `WHILE` loop is working until the loop condition returns `True`. The condition is evaluated before the loop iterations. Hence, if the condition is `False`, the statement sequence is never executed.

```text
$var = 10

while $var > 11
    inc($var)
end
```

As the condition `$var > 11` is `False`, the command `inc($var)` never gets executed.

The constants `True` and `False` can be used as the loop condition.

```text
while true
    <the loop body>
end
```

This loop's body executes infinitely until the loop stopped with the `Break` command.

```text
while false
    <the loop body>
end
```

This loop is ignored by the compiler as the condition is never met.

Currently the compiler accepts only one condition to be checked in the loop condition, but you can check more conditions within the loop body and use the commands `Break` and `Continue`.

## REPEAT..UNTIL

Syntax:

`REPEAT  
  <the loop body>  
UNTIL <loop condition>`

The `repeat..until` loop executes until the loop condition returns `False`. The condition is evaluated after iteration therefore the loop is guaranteed to be executed at least once.

{% hint style="info" %}
The constants `True` and `False` are valid for the use as the loop condition.`repeat..until true` - the loop has the only iteration.  
`repeat..until false` - the loop executes infinitely until it's stopped with the `Break` command.
{% endhint %}

Currently the compiler accepts only one condition to be checked in the loop condition, but you can check more conditions within the loop body and use the commands `Break` and `Continue`.

## Continue and Break

If you want to skip the current iteration and proceed to the next one, use the `Continue` command. The `Break` command causes the loop to stop immediately and proceed to the command after the loop body.

They can substitute an opcode parameter \(e.g., `jf continue`\) or serve as a standalone statement.

```text
if
    $currentactor.dead
jf Break // exit the loop

if
    not $currentactor.dead
then
   Continue // go to the next iteration
end
```

