# Variables

A variable \(var\) is a named storage location that contains a value and can be read/rewrite many times. There are two types of variables.

## Global variables

Global variables are denoted by the $ character put before the name identifier. A global variable name is any combination of letters, underscores, and digits:

`$variable1 $100 $____`

Their values are available from any place of a code.

### **Saved Variables**

A saved variable is a special global variable available only in LCS and VCS modes. It is denoted by a combination of the dollar and the underscore put before the name identifier: $\_var. The value of this variable persists across saved games. Values of global variables denoted by the dollar sign only \($var\) are not saved and they get blank values when the LCS or VCS game loads.

## Local variables

Local variables are denoted by the `@` characher put after the name identifier. A local variable name can only include digits:

`0@ 999@ 56@`

Their values are available only within the current thread or mission.

Threads, external scripts and CLEO scripts have a limited amount of local variables. Refer to the [limits documentation](../scm-documentation/gta-limits.md) to find out the exact ranges.

### **Timer Variables**

Each script or mission have 2 special local variables called TIMERA and TIMERB. The value of a timer variable is increased automatically when the game clock advances, so they are commonly used to measure elapsed time in the script.

```text
0006: TIMERA = 0

:WAIT_2S
0001: wait 0 ms
00D6: if
0019:   TIMERA > 2000
004D: jump_if_false @WAIT_2S
0662: printstring "2 seconds has passed"
```

Note that TIMERA and TIMERB names are only available starting with Sanny Builder v3.3.0. Older scripts have these timers as numeric variables 16@, 17@ \(GTA3, VC\) or 32@, 33@ \(SA\).

## VAR..END construct

Variables are commonly used in expressions. If the right operand is a number constant, the opcode is not needed:

```text
$var = 0
$myarray($index, 10i) >= 150
```

If both operands in the expression are variables, the compiler can not find a correct opcode, because types of the variables are unknown.

For example, there are two opcodes to increment a variable value: 0058 for the integer values and 0059 for the floating-point values.

```text
0058: $Var1 += $Var2 // (int)
0059: $Var1 += $Var2 // (float)
```

Assuming there is no opcode, which one to use?

```text
$Var1 += $Var2 // ??
```

To communicate the compiler a variable type use the VAR..END construct.

VAR..END construct allows to declare variables and their types for the advanced use.

Syntax:  
`var  
<var name>: <type>  
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

* Integer, Int - integer values
* Float - floating-points values
* String, ShortString - a variable containing a string literal with the fixed length \(only for arrays, use s$, @s for variables\)
* LongString - a variable containing a string literal with the variable length \(only for arrays, use v$, @v for variables\)
* &lt;Class name&gt; - any available [class name](classes.md)

Types of local variables can be declared too.

Take a note that once the type of the variable is declared it is used for all the code following the declaration. You can redeclare variables to set a new type:

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

In the thread named "Food" 10@ is the floating-point variable. In the one named "Loop" 10@ is the integer variable.

You can redeclare variables as many times as you need.

## Short Form of Declaration

Since v3.2.0 it's possible to declare a variable of a built-in type \(Int, Float, String, LongString\) shortly using the type name.

Syntax:  
`<type> <variable name>`

```text
int 0@ // 0@ declared as an integer variable.
```

## Variable Initialization

Also you can set an initial value for the variable when declaring it. Write symbol = and then the initial value:

```text
var
$fVar: float = 1.0
end
```

or

```text
float $fVar = 1.0
```

Variable $fVar declared as Float and also the compiler will add an opcode in the script:

```text
0005: $fVar = 1.0
```

Initialization is allowed for the variables only, not for arrays.

