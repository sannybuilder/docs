# Arrays

An **array** represents an indexed collection of elements of the same type (called the base type).

## Array Declaration

```pascal
<type> <array name>[<size>]
```

The type can be one of the following: `Int`, `Float`, `String`, `LongString` or any available [class name](../instructions/classes.md):

```pascal
int intArray[10]
float floatArray[10]
string stringArray[10]
longstring longStringArray[10]
Car cars[5]
```

## Accessing array elements after declaration <a href="#accessing-array-elements" id="accessing-array-elements"></a>

After declaring an array, you can access its elements using square brackets notation. Arrays use zero-based indexes, where the first element of the array is available at the index `0`, the second one at the index `1`, etc:

```pascal
float values[10]
values[0] = 100.0

string stringArray[10]
stringArray[0] = 'str1'
stringArray[1] = 'str2'
stringArray[2] = 'str3'

longstring longStringArray[10]
longStringArray[0] = "str1"
longStringArray[1] = "str2"
longStringArray[2] = "str3"
```

You can also index array elements using variables, like so:

```pascal
int index = 2
int list[5]
list[index] = 10 // set the third element of the array to 10
```

{% hint style="warning" %}
Indexing arrays using variables is only supported in San Andreas, LCS and VCS
{% endhint %}

An element of an array can be used just like any other [variable](variables.md). If the array has a class type, each element can be used to call methods of that class:

```pascal
Player main
Player others[2]

main.addScore(10) // ADD_SCORE main 10
others[0].AddScore(10) // ADD_SCORE others[0] 10
```

## Spreading Arrays

Arrays support spread syntax with the `...` operator as a quick way to represent all array elements.

For example, if you have an array of 3 elements like so:

```cpp
float pos[3]
```

You can spread it to store the result of a command that returns three float numbers, e.g. `get_char_coordinates`:

```pascal
...pos = get_char_coordinates $scplayer 
// same as pos[0], pos[1], pos[2] = get_char_coordinates $scplayer
```

You can also spread an array to pass all elements to a command that requires that amount of arguments, e.g. `set_char_coordinates`:

```pascal
set_char_coordinates $scplayer ...pos
// same as set_char_coordinates $scplayer pos[0] pos[1] pos[2]
```

You can also use [spread syntax when calling functions](../functions.md#array-arguments).

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
