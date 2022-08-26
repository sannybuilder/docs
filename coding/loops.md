# Loops

A **loop** is a statement which allows code to be repeatedly executed. Sanny Builder supports three kinds of controls loops: [for](loops.md#for-end), [while](loops.md#while-end), [repeat](loops.md#repeat-until).

## FOR..END

The `FOR` loop has a strictly certain number of iterations (repetitions).

Syntax:\
`FOR <loop variable> = <initial value> TO/DOWNTO <final value> [step = 1]`\
&#x20; `<the loop body>`\
`END`

`<loop variable>` - a [variable](variables.md) used as a counter for iterations\
`<initial value>` - a value of the loop variable before the first iteration (any value including a [model identifier](data-types.md#model-names))\
`TO` or `DOWNTO` **** - increment or decrement the loop variable between iterations\
`<final value>` - a value of the loop variable after the last iteration (any value including a model identifier)\
`<step>` - an optional value the loop variable will be incremented or decremented with between iterations. By default it is equal to `1`.

```
var
    $value: int = 0
    $final: int = 100
end

FOR $MyCounter = 1 to $final step 2
    $value += $mycounter
end
```

If the `loop variable` is not [declared](variables.md#var-end-construct) with any type before the loop it gets the `Integer` type. If  `initial value`, `final value` or `step` are variables, they get the same type the `loop variable` has To use floating-point numbers for the initial and final values, declare the loop variable with the `Float` type.

```
var
    $MyCounter: float
end

FOR $MyCounter = 1.0 to $final step 2.0
end
```

Variables `$MyCounter` and `$final` both have the `Float` type after the loop.

## WHILE..END

Syntax:\
`WHILE <loop condition>`\
&#x20; `<the loop body>`\
`END`

`loop condition` - a single conditional opcode\
`loop body` - commands to execute on each iteration; can be omitted

```
while not #AK47.Available
    wait 0
end
```

The `WHILE` loop works while the loop condition is true. The condition is evaluated before a loop iteration. Hence, if the condition is false, the loop body never gets executed.

```
$var = 10

while $var > 11
    inc($var)
end

// as the loop condition is false, inc($var) never gets executed
```

[Constants](constants.md) `True` and `False` can be used as a loop condition.

```
while true
    <loop body>
end
```

This loop body executes infinitely until the loop is stopped with the `Break` command.

```
while false
    <loop body>
end
```

This loop is ignored by the compiler as the condition is never met.

{% hint style="info" %}
Currently the compiler accepts only one opcode in the loop condition, but you can check more conditions before the loop body and use the commands `Break` and `Continue`.

```
while true
    if and
       $var >= 0
       $var <= 100
    then
       Break
    end
    // loop executes while $var is in the range [0...100]
      
    <loop body>
end
```
{% endhint %}

## REPEAT..UNTIL

Syntax:\
`REPEAT`\
&#x20; `<the loop body>`\
`UNTIL <loop condition>`

`loop body` - commands to execute on each iteration; can be omitted\
`loop condition` - a single conditional opcode

The `REPEAT..UNTIL` loop executes until the loop condition returns false. The condition is evaluated after iteration therefore the loop is guaranteed to be executed at least once.

[Constants](constants.md) `True` and `False` can be used as the loop condition.

```
repeat
  // the loop has the only iteration
until true 
```

```
repeat
  // the loop executes infinitely until it's stopped with the Break command
until false
```

{% hint style="info" %}
Currently the compiler accepts only one opcode in the loop condition, but you can check more conditions after the loop body and use the commands `Break` and `Continue`.

```
repeat  
   <loop body>
   if and
     $var >= 0
     $var <= 100
   then
     Break
   end
  // loop executes while $var is in the range [0...100]      
until false
```
{% endhint %}

## Continue and Break

If you want to skip the current iteration and proceed to the next one, use the `Continue` command.&#x20;

The `Break` command causes the loop to stop immediately and proceed to the command after the loop body.

They can substitute an opcode parameter (e.g., `jf Continue`) or serve as a standalone statement.

```
while true
  if
    not $currentactor.dead
  jf Break // exit the loop

  if
    $currentactor.dead
  then
    Continue // go to the next iteration
  end
end
```
