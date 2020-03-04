# Массивы

An **array** represents an indexed collection of elements of the same type \(called the base type\). You can work with any element directly via its index. An index numeration begins with a zero. These arrays are supported in San Andreas, LCS and VCS.

## Общий синтаксис

San Andreas:  
`<array name>(<index var name>,<size><type>)`

Liberty City Stories, Vice City Stories:  
`<array name>(<index var name>,<size>)`

`<array name>`: local or global variable  
`<index var name>`: any variable containing an index value  
`<size>`: any value greater than 0  
`<type>`: chars `i` `f` `s` `v` denote one of the array types:

| Letter | Item Type | Item Size \(bytes\) |
| :--- | :--- | :--- |
| i | integer | 4 |
| f | float | 4 |
| s | string | 8 |
| v | string | 16 |

In LCS, VCS, array elements are only 4 bytes in length. Therefore, there is no need in type declaration.

An array could contain the elements of the same type only:

```text
$index = 0
$array($index,10i) = 1
```

## Объявление массивов

1\) declare an array using the [VAR..END](variables.md#var-end-construct) construct

`var  
   <array name>: array <size> of <type>  
end`

```text
var
    $FloatArray: array 10 of Float
end
```

Now you can work with this array without specifying its type and size:

```text
$FloatArray[$RndIndex] += 100.0
```

2\) use a number as an index

For instance, you have the array `$strings`, containing 10 elements of type `s`. You can use a constant number to work with the specified element:

```text
s$strings[0] = 'str1'
s$strings[1] = 'str2'
	...
s$strings[9] = 'str10'
```

These variables can also be used as the class name:

```text
$players[0].Build 
```

By default in the `GTA SA` [edit mode](../edit-modes.md), array elements are decompiled with the numbers as indexes. You can turn this feature off through the [console](../console.md) using the command `toggle constant_indexes off`. The same feature is available in LCS and VCS but is disabled by default. You can enable this through the Console.

