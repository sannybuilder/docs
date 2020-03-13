# Variables

A **variable \(var\)** is a named storage location that contains a value and can be read/rewrite many times. There are two types of variables.

## Global variables

A global variable starts with `$` followed by an identifier \(name\).  The global variable name is any combination of letters, digits and `_`:

`$variable1 $100 $____`

Their values are available from any place of the code.

### **Saved Variables**

A saved variable is a special global variable available only in `LCS` and `VCS` modes. Its name is prefixed with `$_`, e.g. `$_var`. The value of this variable persists across saved games. Global variables denoted by `$` only \(e.g. `$var`\) are not saved and they get blank values when the LCS or VCS game loads.

## Local variables

A local variable name may only be a number followed by `@`.

```text
0@ 
999@ 
56@
```

Their values are available only within the current script or the mission.

{% hint style="warning" %}
The number of local variables per script is strictly [limited](../scm-documentation/gta-limits.md).
{% endhint %}

### **Timer Variables**

Each script or a mission have 2 special local variables called `TIMERA` and `TIMERB`. The value of a timer variable is increased automatically when the game clock advances, so they are commonly used to measure time elapsed since the timer reset:

```text
0006: TIMERA = 0 // reset the timer

:WAIT_2S
0001: wait 0 ms
00D6: if
0019:   TIMERA > 2000 // if the timer value is > 2000, i.e. 2 seconds has passed
004D: jump_if_false @WAIT_2S
0662: printstring "2 seconds has passed" // display the message
```

{% hint style="info" %}
`TIMERA` and `TIMERB` names are only available starting with Sanny Builder v3.3.0. Older scripts reference these timers via the local variables `16@`, `17@` \(GTA3, VC\) or `32@`, `33@` \(SA\).
{% endhint %}

## VAR..END construct

Variables are commonly used in the expressions. If the right operand is a number constant, the opcode can be omitted:

```text
$var = 0
$myarray($index, 10i) >= 150
```

If both operands in the expression are variables, the compiler can not determine the correct opcode, because the types of the variables are unknown.

For example, there are two opcodes to increment a variable value: `0058` for integer values and `0059` for floating-point values.

```text
0058: $Var1 += $Var2 // (int)
0059: $Var1 += $Var2 // (float)
```

Assuming there is no opcode, which one to use?

```text
$Var1 += $Var2 // ??
```

To communicate the compiler a variable type use the `VAR..END` construct.

`VAR..END` construct allows to declare variables and their types for the advanced use.

Syntax:  
`var  
<variable>: <type>  
end`

For example, if both variables are declared, the compiler is able to process the expression without opcodes:

```text
var
    $Var1 : Integer
    $Var2 : Integer
end
$Var1 += $Var2 // opcode 0058
```

The following types of variables are supported:

* `Integer`, `Int` - integer values
* `Float` - floating-points values
* `String`, `ShortString` - a variable containing a string literal with the fixed length \(only for the arrays, use `s$`, `@s` for variables\)
* `LongString` - a variable containing a string literal with the variable length \(only for the arrays, use `v$`, `@v` for variables\)
* `<Class name>` - any available [class name](classes.md)

The types of the local variables can be declared too.

{% hint style="info" %}
Once the type of the variable is declared it is used for all the code following the declaration.  
You can re-declare variables to set the new type:

```text
thread 'Food'
var
    10@ : Float
    $Var : Float
end
$var = 1
10@ = $Var
end_thread

thread 'Loop'
var
    10@ : Int
    $Var : Int
end
$var = 1
10@ = $Var
end_thread
```

In the `'Food'` script `10@` is the floating-point variable. In the `'Loop'` script `10@` is the integer variable.

You can re-declare variables as many times as you need.
{% endhint %}

## Shorter Form of Declaration

Since v3.2.0 it's possible to declare a variable of a built-in type \(`Int`, `Float`, `String`, `LongString`\) using only the type name.

Syntax:  
`<type> <variable name>`

```text
int 0@ // 0@ declared as an integer variable.
```

## Variable Initialization

You can specify an initial value for the variable when declaring it. Write `=` and then the value:

```text
var
    $fVar: float = 1.0
end
```

or

```text
float $fVar = 1.0
```

The variable `$fVar` is now declared as `Float` and the compiler adds the opcode `0005` in the script:

```text
0005: $fVar = 1.0
```

Initialization is allowed for variables, but not for arrays.

