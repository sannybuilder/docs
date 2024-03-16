# Functions

First native support for functions in GTA was added in Liberty City Stories. The games prior to that only had limited subroutines invoked with the `gosub` command. Those subroutines allowed to avoid code duplication; however, they were operating on the same scope as the code invoking them. Any variables used in a subroutine would alter the state of the script.

CLEO Library brought support for functions (dubbed _scm func_) in early versions, and it became important part of the modern scripting techniques. An SCM Function has its own variable stack. You are given additional `16` or `32` variables ([depending](../scm-documentation/gta-limits.md) on the game), none of them would clash with the local variables of the script calling the functions. CLEO5 improved SCM Functions a lot by completely isolating script and function state, adding support for string arguments, and more.

Sanny Builder 4 adds new syntactic element to the language to easily create and use SCM functions in the code.

{% hint style="info" %}
Visit [this GitHub ticket](https://github.com/sannybuilder/dev/issues/263) for more technical information and examples on function syntax.&#x20;
{% endhint %}

### Syntax

To make a new function, use the `function` keyword.

```pascal
function <signature>
<body>
end
```

`signature` defines function's input parameters and their type, and also an optional return type.\
`body` is the code that runs when you call the function.\
A function must end with the `end` keyword.&#x20;

#### Example

```typescript
function sum(a: int, b: int): int
  int result = a + b
  return true result
end
```

### Signature

A function's signature defines what types of input arguments the function receives and what type of value it returns. Function arguments may be of a primitive type `int`, `float, string`, or a class, e.g. `Car` or `Pickup`.

{% hint style="info" %}
String arguments are always passed as pointers.
{% endhint %}

A function may have zero parameters. If it has parameters, they are listed between `()`.  Each parameter has a name and a type, separated by a colon. Parameter declaration syntax is similar to that of [`var..end`](data-types/variables.md#declaring-a-variable-type). Each parameter can be used as a function's local variable in the function body.

If the function returns something, its type has to be defined after the list of parameters (or the function name, if there are no parameters). E.g.:

```pascal
function foo: float
function bar(i: int): int
```

### Body

A function's body include all instructions executed when the main code calls the function. The function may have zero instructions. Function parameters can be referenced in the body as local variables. The function may create extra local variables and even new functions, available only within this function:

```pascal
int x

function mod
int x = 5
end

x = 10
mod()
// x is still equal to 10
```

### Return From Function

Function ends at the `end` keyword. You may exit early using the `return` keyword.&#x20;

{% hint style="success" %}
`return` keyword can be used in both gosub subroutines and functions.
{% endhint %}

```pascal
function SetWantedLevel(level: int)
  set_max_wanted_level level
end // no explicit return, function ends here

function SetWantedLevel(level: int)
  if or
    level < 0
    level > 6
  then
     return // early return, code below won't be executed
  end
  set_max_wanted_level level
end // function ends here
```

When leaving the function, you can optionally set the condition flag in the current script like so:&#x20;

```pascal
return true
return false
```

`true` and `false` set the script's [condition result](control-flow/conditions.md). It can be used with `IF..THEN` to check on the function result and act accordingly:&#x20;

```pascal
function isDefined(val: int)
  if val <> 0
  then return true
  else return false
  end
end

if isDefined(5)
then
  // result is true
else
  // result is false
end
```

{% hint style="info" %}
The example above can also be written in a more concise way:

```pascal
function isDefined(val: int)
  return val <> 0
end
```
{% endhint %}

### Returning Values

The function may return one or multiple values, using the `return` keyword.&#x20;

To define a function that returns something, add a colon and a type at the end of the function signature:

```pascal
function maxItems: int
```

To return a value use `return` followed by `true` or `false` and a value:

```pascal
return true 5
return false 5
```

To read the returned value, a caller must provide a variable:

```javascript
int value = maxItems() // value is 5
```

It can also be used with `IF..END`:

```pascal
int value
if 
  value = maxItems()
then
 // function returned true and a value
else
 // function returned false and a value
end
```

### Declaring functions

Functions must be known to the compiler before they are used in the code.

Functions whose body precedes any call don't need a declaration:

```pascal
function foo
end

foo // compiles
```

If, however, the function implementation is located later in the code, it will produce a compilation error, as the function name cannot be resolved.

```pascal
foo // error, foo is not defined

function foo
end
```

To solve it, declare a function upfront using a `define` keyword:

```pascal
define function <name>(<input types>):<output types>
```

#### Example

```pascal
define function foo
define function setPos(float, float, z: float)
define function bar(int, float): int
```

#### Rules

* forward declaration starts with the word `DEFINE`. The same word is used to declare elements of SCM header.
* `<name>` must be a valid identifier.
* input arguments may omit names and only list types `(float, float, float)`.
* forward declaration must have the same number of input and output parameters as the actual implementation. Types of parameters must match too.
* each function may have only one forward declaration.

### Foreign Functions

CLEO provides an interface for calling game's native functions. There are 4 opcodes that support different calling conventions:

```
0AA5: call_function {address} [int] {numParams} [int] {pop} [int] {funcParams} [arguments]
0AA6: call_method {address} [int] {struct} [int] {numParams} [int] {pop} [int] {funcParams} [arguments]
0AA7: call_function_return {address} [int] {numParams} [int] {pop} [int] {funcParams} [arguments] {var_funcRet} [var any]
0AA8: call_method_return {address} [int] {struct} [int] {numParams} [int] {pop} [int] {funcParams} [arguments] {var_funcRet} [var any]
```

As you may guess, using them directly is not very convenient. These opcodes have their own quirks, like having to provide input arguments in reverse order.

Sanny Builder 4 offers an interface for defining foreign functions in code and using them as regular functions. It can be done by adding calling convention type to a forward declaration.

```
define function<cc[,address]>(args): return type
```

A `cc` or calling convention defines who's in charge of cleaning up the stack when function returns.

CLEO and Sanny Builder supports 3 major conventions:

* _cdecl_ - caller cleans up the stack
* _stdcall_ - callee cleans up the stack
* _thiscall_ - callee cleans up the stack. Since `thiscall` is a class method function, it additionally receives a pointer to the class instance in `ecx` register.

You can read more about different types of calling conventions on [Wikipedia](https://en.wikipedia.org/wiki/X86\_calling\_conventions).&#x20;

Optional address parameter defines where this function is located in the game memory (static functions). If this address can only be known in runtime, this parameter can be omitted.

#### Example

```pascal
define function CStats__GetStatType<cdecl,0x558E30>(statId: int): int

int type = CStats__GetStatType(42)

// 0AA7: call_function_return {address} 0x558E30 {numParams} 1 {pop} 1 {funcParams} 42 {var_funcRet} 0@ 
```

This code invokes a function at address `0x558E30` with argument `42` and stores the returned value in the variable `type`.&#x20;

Passing multiple arguments can be done as usual:

```pascal
define function Foo<stdcall,0x400000>(int, float): int

int value = Foo(10, 20.0)

// 0AA7: call_function_return {address} 0x400000 {numParams} 2 {pop} 0 {funcParams} 20.0 {var_funcRet} 10 0@ 

```

Calling a `thiscall` function requires the first argument to always be a pointer to the class instance.

```pascal
define function Destroy<thiscall,0x400000>(struct: int)

int instance = 0xDEADD0D0
Destroy(instance)

// 0006: 0@ = 0xDEADD0D0
// 0AA6: call_method {address} 0x400000 {struct} 0@ {numParams} 0 {pop} 0

```

When function's address is not known at compile time, you still can define a foreign function and use a function pointer to call it by reference. To declare a function pointer, [declare a new variable](data-types/variables.md#declaring-a-variable-type) with the function name as the type:

```pascal
define function Destroy<thiscall>(struct: int)
Destroy method // define a pointer to function Destroy
...
method = 0x400000 // function is located at 0x400000
method(0xDEADD0D0) // call function using the pointer

// 0006: 0@ = 0x400000
// 0AA6: call_method {address} 0@ {struct} 0xDEADD0D0 {numParams} 0 {pop} 0
```

