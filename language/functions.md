# Functions

First native support for functions in GTA was added in Liberty City Stories. The games prior to that only had limited subroutines invoked with the `gosub` command. Those subroutines allowed to avoid code duplication; however, they were operating on the same scope as the code invoking them. Any variables used in a subroutine would alter the state of the script.

CLEO Library brought support for functions (dubbed _scm func_) in early versions, and it became important part of the modern scripting techniques. Each SCM function owns `16` or `32` local variables ([depending](../scm-documentation/gta-limits.md) on the game), none of them would clash with the local variables of the script calling the functions. CLEO5 improved SCM functions a lot by completely isolating script and function state, adding support for string arguments, and more.

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
A function must end with the `end` keyword.

Functions are available anywhere in the current scope. Functions defined inside other functions only available in that function.

#### Example

```typescript
function sum(a: int, b: int): int
  int result = a + b
  return result
end
```

### Signature

A function's signature defines what types of input arguments the function receives and what type of value it returns. Function arguments may be of a primitive type `int`, `float, string`, or a class, e.g. `Car` or `Pickup`. Since v4.2 they can also be an array.

{% hint style="warning" %}
String arguments are only supported in CLEO 5. They are always passed as pointers.
{% endhint %}

A function may have zero parameters. If it has parameters, they are listed between `()`.  Each parameter has a name and a type, separated by a colon. Parameter declaration syntax is similar to that of [`var..end`](data-types/variables.md#declaring-a-variable-type). Each parameter can be used as a function's local variable in the function body.

<pre class="language-pascal"><code class="lang-pascal">function loadModel(modelId: int)
<strong>    request_model modelId
</strong>    while not is_model_available modelId
        wait 0
    end
end
</code></pre>

`modelId` is an input parameter of the `int` type. It can be used as a local variable.

If the function returns something, its type has to be defined after the list of parameters (or the function name, if there are no parameters). E.g.:

```pascal
function foo: float
function bar(i: int): int
```

### Array Arguments

Since v4.2. function arguments can be arrays. To define an array argument, use the following syntax:

```
function move(pos: float[3])
```

Here `pos` is an array with 3 elements of type `float`. To call this function, you need to pass three float values:

```
move(100.0, -200.0, 25.0)
```

If you have an array, you can pass it to the function using the [spread operator](instructions/expressions.md#spreading-arrays) `...`:

```
float pos = float[3]
...pos = get_char_coordinates $scplayer
move(...pos)
```



The last function argument can be declared as a variadic argument, using the following syntax:

```pascal
function myFunction(...args: int[5]) {
  // Function implementation
}
```

Here, the last argument `...args: int[5]` represents an array of integers with a maximum length of `5`. Zero or more integers can be passed to this function, and they will be accessible within the function as the elements of the `args` array.

```pascal
myFunction()
myFunction(1,2,3)
myFunction(1,2,3,4,5,6) // Error: Exceeds maximum argument length
```

To find out the actual number of arguments the function was called with, you can use [GET\_CLEO\_ARG\_COUNT](https://library.sannybuilder.com/#/sa/script/extensions/CLEO/2000) from CLEO5:

```
function loadModels(...models: int[16]) // allow up to 16 values
    int count = get_cleo_arg_count // get actual number of arguments, this is CLEO5 opcode
    count--
    int i

    for i = 0 to count
        request_model models[i]
    end
    load_all_models_now
end

```

### Calling a Function

Functions can be called using its name followed by open and closed braces:

```pascal
function foo
end

foo()
```

`()` are required for the function call, even if function receives no arguments. Without `()` function name is compiled as it's offset or address (if this is a static [foreign function](functions.md#foreign-functions)):

```pascal
function foo
end

jump foo // jumps into the function body
```

### Function Body

A function's body include all instructions executed when the main code calls the function. The function may have zero instructions. Function parameters can be referenced in the body as local variables. The function may create extra local variables and even new functions, available only within this function:

```pascal
int x

function mod
  int x = 5  // this `x` only exists within function `mod`
end

x = 10
mod()
// x is still equal to 10
```

### Return From Function

Function ends at the `end` keyword. You may exit early using the `return` keyword.&#x20;

{% hint style="warning" %}
Exit from a function using `return` keyword is only supported in CLEO 5 (San Andreas). For other CLEO versions use `cleo_return` command.
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

#### Returning logical values

For a function to be used as a [condition](control-flow/conditions.md) in `IF..THEN`, it must have a special return type: `logical`.&#x20;

```pascal
function check(): logical

if check()
then
end
```

`logical` function returns a result of logical expression, or `true` or `false`.

<pre class="language-pascal"><code class="lang-pascal"><strong>return true
</strong>return false
return 0@ == 1
return Char.DoesExist(0@)
</code></pre>

A value returned from a logical function sets the script's [condition result](control-flow/conditions.md) and be combined with other checks in one IF statement.

```pascal
function isDefined(val: int): logical
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

#### Returning Values

The function may return one or multiple values, using the `return` keyword.&#x20;

To define a function that returns something, add a colon and a type at the end of the function signature:

```pascal
function maxItems: int
```

To return a value use `return` followed a value:

```pascal
return 5
```

To read the returned value, a caller must provide a variable:

```javascript
int value = maxItems() // value is 5
```

{% hint style="info" %}
Returning any value, even 0, from a function is considered a success if the function is used as a condition.

```pascal
function zero: int
  return 0
end

if
  zero()
then
  // success
else
  // will never be here
end
```
{% endhint %}

If a function may fail and not have a valid result, its return type should be marked as `optional` and a blank return can be used:

```pascal
function createCar: optional int
  return
end

if
  Car c = createCar()
then
  // got a car handle in c
else
  // got nothing
end
```

`optional` keyword must precede the list of return types.

#### &#x20;Optional Return Type

Some functions may not be able to return correct values (_a fallible function_). For example, a function reading a file may fail if the file does not exist. In this case the return type can be marked with the `optional` keyword:

```pascal
function getValues: optional int, int, int
  if <...>
  then
     return 1 2 3
  else
     return
  end
end
```

Function `getValues` may return `3` integer values or nothing. On calling end, to check whether a fallible function succeeded it can be wrapped into IF..THEN condition like so:

```pascal
int a, b, c
if
  a, b, c = getValues()
then
  // we got 3 values in a, b, c
else
  // we got nothing, a, b, c have not been changed
end
```

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

```pascal
function<cc[,address]>(args): return type
```

A `cc` or calling convention defines who's in charge of cleaning up the stack when function returns.

CLEO and Sanny Builder supports 3 major conventions:

* _cdecl_ - caller cleans up the stack
* _stdcall_ - callee cleans up the stack
* _thiscall_ - callee cleans up the stack. Since `thiscall` is a class method function, it additionally receives a pointer to the class instance in `ecx` register.

You can read more about different types of calling conventions on [Wikipedia](https://en.wikipedia.org/wiki/X86_calling_conventions).&#x20;

Optional address parameter defines where this function is located in the game memory (static functions). If this address can only be known in runtime, this parameter can be omitted.

A return type can be `int`, `float,` or `string`.

#### Example

```pascal
function CStats__GetStatType<cdecl,0x558E30>(statId: int): int

int type = CStats__GetStatType(42)

// 0AA7: call_function_return {address} 0x558E30 {numParams} 1 {pop} 1 {funcParams} 42 {var_funcRet} 0@ 
```

This code invokes a function at address `0x558E30` with argument `42` and stores the returned value in the variable `type`.&#x20;

Passing multiple arguments can be done as usual:

```pascal
function Foo<stdcall,0x400000>(int, float): int

int value = Foo(10, 20.0)

// 0AA7: call_function_return {address} 0x400000 {numParams} 2 {pop} 0 {funcParams} 20.0 {var_funcRet} 10 0@ 
```

Calling a `thiscall` function requires the first argument to always be a pointer to the class instance.

```pascal
function Destroy<thiscall,0x400000>(struct: int)

int instance = 0xDEADD0D0
Destroy(instance)

// 0006: 0@ = 0xDEADD0D0
// 0AA6: call_method {address} 0x400000 {struct} 0@ {numParams} 0 {pop} 0
```

When function's address is not known at compile time, you still can define a foreign function and use a function pointer to call it by reference. To declare a function pointer, [declare a new variable](data-types/variables.md#declaring-a-variable-type) with the function name as the type:

```pascal
function Destroy<thiscall>(struct: int)
Destroy method // define a pointer to function Destroy
...
method = 0x400000 // function is located at 0x400000
method(0xDEADD0D0) // call function using the pointer

// 0006: 0@ = 0x400000
// 0AA6: call_method {address} 0@ {struct} 0xDEADD0D0 {numParams} 0 {pop} 0
```

{% hint style="info" %}
Static function's name represents its address when used without `()`

```pascal
function Foo<stdcall,0x400000>(int, float): int

int addr = foo // addr = 0x400000
```
{% endhint %}
