# Arrays

An **array** represents an indexed collection of elements of the same type (called the base type). You can work with any element directly via its index. An index numeration begins with a zero. Arrays are supported in San Andreas, LCS and VCS.

## Array Declaration

Arrays can be declared using the `var` keyword (similar to [variables](variables.md)):

```pascal
var <array name>: array <size> of <type>
```

```pascal
var floatArray: array 10 of Float
```

You can declare arrays of primitive types (such as numbers or strings) using a more concise syntax:

```pascal
<type> <array name>[<size>]
```

The type can be one of the following: `Int`, `Float`, `String`, or `LongString`:

```pascal
int intArray[10]
float floatArray[10]
string stringArray[10]
longstring longStringArray[10]
```

### Accessing array elements after declaration <a href="#accessing-array-elements" id="accessing-array-elements"></a>

After declaring an array, you can access its elements using square brackets:

```pascal
var floatArray: array 10 of Float

int index = 0

// increasing value of the first element by 100
floatArray[index] += 100.0

// same
floatArray[0] += 100.0
```

String arrays can store [string literals](./#string-literals):

```lua
stringArray[0] = 'str1'
stringArray[1] = 'str2'
stringArray[2] = 'str3'

longStringArray[0] = "str1"
longStringArray[1] = "str2"
longStringArray[2] = "str3"
```

An array can be declared as a collection of [class instances](../instructions/classes.md#class-instances), its methods are available for each element:

```pascal
var players: array 2 of Player

$players[0].Build
```

{% hint style="info" %}
By default, the disassembler prints array elements with the numbers as indexes in the `GTA SA` [edit mode](../../edit-modes/). The same feature is available in LCS and VCS but is disabled by default. You can turn this feature on and off using the [debug option](../../editor/console.md#constant_indexes) `CONSTANT_INDEXES`.&#x20;
{% endhint %}

## Spreading Arrays

Arrays support spread syntax using `...` operator. Read more about it [here](../instructions/expressions.md#spreading-arrays).

## Legacy syntax

The legacy syntax is produced when you disassemble a script that uses arrays. This syntax represents low-level array implementation and is not recommended for direct use in new scripts. Instead, declare an array and access elements using square bracket notation (see above).

### San Andreas

```pascal
<array name>(<index var name>,<size><type>)
```

```pascal
$index = 0
$array($index,10i) = 1
```

`<array name>`: a local or global [variable](variables.md)\
`<index var name>`: any variable containing an index of the element to read or write\
`<size>`: a value between 1 and 255 (inclusive)\
`<type>`: one of characters `i` `f` `s` `v`:

| Letter | Item Type | Item Size (bytes) |
| ------ | --------- | ----------------- |
| i      | integer   | 4                 |
| f      | float     | 4                 |
| s      | string    | 8                 |
| v      | string    | 16                |

### Liberty City Stories, Vice City Stories

In LCS, VCS, array elements are only 4 bytes in length. Therefore, there is no need in type declaration.

```pascal
<array name>(<index var name>,<size>)
```

```pascal
$index = 0
$array($index,10) = 1
```
