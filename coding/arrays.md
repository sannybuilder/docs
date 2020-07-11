# Arrays

An **array** represents an indexed collection of elements of the same type \(called the base type\). You can work with any element directly via its index. An index numeration begins with a zero. Arrays are supported in San Andreas, LCS and VCS.

## General Syntax

San Andreas:  
`<array name>(<index var name>,<size><type>)`

```text
$index = 0
$array($index,10i) = 1
```

`<array name>`: local or global [variable](variables.md)  
`<index var name>`: any variable containing an index of the element to read or write  
`<size>`: any value greater than 0  
`<type>`: one of characters `i` `f` `s` `v`:

| Letter | Item Type | Item Size \(bytes\) |
| :--- | :--- | :--- |
| i | integer | 4 |
| f | float | 4 |
| s | string | 8 |
| v | string | 16 |

Liberty City Stories, Vice City Stories:  
`<array name>(<index var name>,<size>)`

{% hint style="info" %}
In LCS, VCS, array elements are only 4 bytes in length. Therefore, there is no need in type declaration.
{% endhint %}

```text
$index = 0
$array($index,10) = 1
```

## Array Declaration

Arrays can be declared using the [`VAR..END`](variables.md#var-end-construct) construct:  
`var  
   <array name>: array <size> of <type>  
end`

```text
var
    $FloatArray: array 10 of Float
end
```

### Accessing array elements after declaration

After declaring an array you can work access its elements using square brackets:

```text
var
    $FloatArray: array 10 of Float
end
$index = 1
$FloatArray[$index] += 100.0
```

### Using constant indexes

You can use positive integer numbers and zero to access a particular array element:

```text
var
    $FloatArray: array 10 of Float
end
$FloatArray[1] += 100.0
```

Elements of an array containing [string literals](data-types.md#string-literals) can be accessed with [string variables](data-types.md#string-variables):

```text
// initializing first three elements of the $strings array
s$strings[0] = 'str1'
s$strings[1] = 'str2'
s$strings[2] = 'str3'
```

An array can be declared as a collection of [class instances](classes.md#class-instances):

```text
var
  $players: array 2 of Player
end
$players[0].Build
```

{% hint style="info" %}
By default in the `GTA SA` [edit mode](../edit-modes/), the disassembler prints array elements with the numbers as indexes. The same feature is available in LCS and VCS but is disabled by default. You can turn this feature on and off using the [debug option](../console.md#constant_indexes) `CONSTANT_INDEXES`. 
{% endhint %}

