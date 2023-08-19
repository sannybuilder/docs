# Variables

A **variable (var)** is a named storage location that contains a value and can be read/rewrite many times. Variables can be either _global_ or _local_.

## Global variables

A global variable starts with `$` followed by any combination of letters, digits and `_`:

`$variable1`\
`$100`\
`$____`

Their values are available from any place of the code.

### **Saved Variables**

A saved variable is a special global variable available only in `LCS` and `VCS` modes. Its name is prefixed with `$_`, e.g., `$_var`. The value of this variable persists across saved games. Global variables denoted by `$` only (e.g., `$var`) are not saved and they get blank values when the LCS or VCS game loads.

### DMA Variables

When global variables are compiled, each one of them gets a new index in the global variable space. This index will be used by the game to locate the variable value. This index is unique across all scripts (hence global).

A global variable with the name that only consists of digits is called a `DMA`-variable (**D**irect **M**emory **A**ddress). See also [Alloc](built-in-commands.md#alloc).

## Local variables

A local variable name may only be a number followed by `@`.

```pascal
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

```pascal
0006: TIMERA = 0 // reset the timer

:WAIT_2S
0001: wait 0 ms
00D6: if
0019:   TIMERA > 2000 // if the timer value is > 2000, i.e. 2 seconds has passed
004D: jump_if_false @WAIT_2S
0662: printstring "2 seconds has passed" // display the message
```

{% hint style="info" %}
`TIMERA` and `TIMERB` names are only available starting with Sanny Builder v3.3.0. In older scripts the timers are known as `16@`, `17@` (GTA3, VC) or `32@`, `33@` (SA).
{% endhint %}

## Declaring a variable type

Variables are commonly used in the expressions. If the right operand is a number constant, the opcode can be omitted:

```pascal
$var = 0
$myarray($index, 10i) >= 150
```

If both operands in the expression are variables, the compiler cannot determine the correct opcode, because the types of the variables are unknown.

For example, there are two opcodes to increment a variable value: `0058` for integer values and `0059` for floating-point values.

```pascal
0058: $Var1 += $Var2 // (int)
0059: $Var1 += $Var2 // (float)
```

Assuming there is no opcode, which one to use?

```pascal
$Var1 += $Var2 // ??
```

To tell the compiler the type of the variable, use the `var` keyword.

```pascal
var <variable>: <type>
```

A `variable` is a valid global or local variable name as described above.

A `type` could be one of these:

* `Integer`, `Int` - integer values
* `Float` - floating-points values
* `String`, `ShortString` - a variable containing a string literal with the fixed length (only for the arrays, use `s$`, `@s` for variables)
* `LongString` - a variable containing a string literal with the variable length (only for the arrays, use `v$`, `@v` for variables)
* `<Class name>` - any available [class name](classes.md)

Example:

```pascal
var $size: integer
```

You can define types for multiple variables by separating each declaration with a comma like this:

```pascal
var $x: float, $y: float, $z: float
```

If you prefer to have each declaration on its own line, conclude them in a `VAR..END` construct:

```pascal
var
   $x: float
   $y: float
   $z: float
end
```

When variable types are known, the compiler is able to process the expression without opcode:

```pascal
var
    $Var1 : Integer
    $Var2 : Integer
end
$Var1 += $Var2 // opcode 0058
```



{% hint style="info" %}
Once the type of the variable is declared it is used for all the code following the declaration.\
You can re-declare variables to set the new type:

```
script_name 'Food'
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

Since v3.2.0 it's possible to declare a variable of a built-in type (`Int`, `Float`, `String`, `LongString`) using only the type name.

Syntax:\
`<type> <variable name>`

```pascal
int 0@ // 0@ declared as an integer variable.
```

Starting from v3.4.0 it is possible to declare variables with custom names:

```pascal
int a
float distance
string name

a = 1
distance = 15.5
name = 'CJ'
```

An initial value can follow the variable name to reduce the number of the lines of code:

```pascal
int a = 1
float distance = 15.5
string name = 'CJ'
```

The compiler binds a new local variable to each name. In the example above one may expect a resulting code to look like:

```pascal
0006: 0@ = 1 
0007: 1@ = 15.5 
05AA: 2@ = 'CJ'
```

{% hint style="info" %}
Due to [design limitations](https://github.com/sannybuilder/dev/issues/32) this feature is only available in CLEO scripts.
{% endhint %}

## Variable Initialization

You can specify an initial value for the variable when declaring it. Write `=` and then the value:

```pascal
var $fVar: float = 1.0
```

or

```pascal
float $fVar = 1.0
```

The variable `$fVar` is now declared as `Float` and the compiler adds the opcode `0005` in the script:

```pascal
0005: $fVar = 1.0
```

Initialization is allowed for variables, but not for arrays.
