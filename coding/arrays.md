# Arrays

An **array** represents an indexed collection of elements of the same type (called the base type). You can work with any element directly via its index. An index numeration begins with a zero. Arrays are supported in San Andreas, LCS and VCS.

## General Syntax

San Andreas:

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

Liberty City Stories, Vice City Stories:

In LCS, VCS, array elements are only 4 bytes in length. Therefore, there is no need in type declaration.

```pascal
<array name>(<index var name>,<size>)
```

```pascal
$index = 0
$array($index,10) = 1
```

## Array Declaration

Arrays can be declared using the `var` keyword (similar to [variables](variables.md)):

```pascal
var <array name>: array <size> of <type>
```

```pascal
var $FloatArray: array 10 of Float
```

### Accessing array elements after declaration <a href="#accessing-array-elements" id="accessing-array-elements"></a>

After declaring an array, you can access its elements using square brackets:

```pascal
var $FloatArray: array 10 of Float

$index = 0

// increasing value of the first element by 100
$FloatArray[$index] += 100.0

// same
$FloatArray[0] += 100.0
```

Elements of an array containing [string literals](data-types.md#string-literals) can be accessed using [string variables](data-types.md#string-variables):

```pascal
// initializing first three elements of the $strings array
s$strings[0] = 'str1'
s$strings[1] = 'str2'
s$strings[2] = 'str3'
```

An array can be declared as a collection of [class instances](classes.md#class-instances), its methods are available for each element:

```pascal
var $players: array 2 of Player

$players[0].Build
```

{% hint style="info" %}
By default, the disassembler prints array elements with the numbers as indexes in the `GTA SA` [edit mode](../edit-modes/). The same feature is available in LCS and VCS but is disabled by default. You can turn this feature on and off using the [debug option](../editor/console.md#constant\_indexes) `CONSTANT_INDEXES`.&#x20;
{% endhint %}
