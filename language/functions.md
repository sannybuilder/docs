# Functions

First native support for functions in GTA was added in Liberty City Stories. The games prior to that only had limited subroutines invoked with the `gosub` command. Those subroutines allowed to avoid code duplication; however, they were operating on the same scope as the code invoking them. Any variables used in a subroutine would alter the state of the script.

CLEO Library brought support for functions (dubbed _scm func_) in early versions, and it became important part of the modern scripting techniques. An SCM Function has its own variable stack. You are given additional 16 or 32 variables ([depending](../scm-documentation/gta-limits.md) on the game), none of them would clash with the local variables of the script calling the functions. CLEO5 improved SCM Functions a lot by completely isolating script and function state, adding support for string arguments, and more.

Sanny Builder 4 adds new syntactic element to the language to easily create and use SCM functions in the code.

### Syntax

To define a new function, use the `function` keyword.

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

A function's signature defines what types of input arguments the function receive and what type of value it returns.&#x20;

A function may have zero parameters. If it has parameters, they are listed between `()`.  Each parameter has a name and a type, separated by a `:`. Parameter declaration syntax is similar to that of [`var..end`](data-types/variables.md#declaring-a-variable-type). Each parameter can be used as a function's local variable in the function body.

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

{% hint style="warning" %}
The `return` keyword is similar to the `return` command used in the SCM code to leave the gosub subroutine, but it acts differently in the functions.
{% endhint %}

In functions the return keyword is always followed by `true` or `false`.&#x20;

```
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
The example above can also be written in a more consise way:

```pascal
function isDefined(val: int)
  return val <> 0
end
```
{% endhint %}

### Returning Values

The function may return one or multiple values, using the `return` keyword.&#x20;

To define a function that returns something, add a `:` and a type at the end of the function signature:

```
function maxItems: int
```

To return a value use `return` followed by `true` or `false` and a value:

```
return true 5
return false 5
```

To read the returned value, a caller must provide a variable:

```javascript
int value = maxItems() // value is 5
```

It can be also be used with `IF..END`:

```pascal
int value
if 
  value = maxItems()
then
 // function returned true and a value
else
 // function returned false
end
```
