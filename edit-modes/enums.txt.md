# Enums.txt

An **enumerated type** or **enum** is a set of constants \(called _enum members_\) under a common prefix \(_enum name_\). 

Enumerated types have a few advantages over ordinary constants, such as keeping the global namespace dense and being first-class citizens in the type system \(command parameters having an enumerated type are limited on allowed values range and as a result it eliminates the whole class of errors when an invalid id is used\).

**Enums.txt** is a text file that defines a list of the enumerated types available in the [edit mode](./).

## File Format

Each enumerated type is defined with the following syntax:

`enum <enum name>  
<enum members>  
end`

`enum name` -  any combination of letters, digits and `_`   
`enum members` - one or many lines with the format:  
    `<enum member name> [= <enum member value>]`   
    where  
    `enum member name` - any combination of letters, digits and `_`   
    `enum member value` - optional. if not present, the compiler assigns a [new value](enums.txt.md#enum-values) automatically.

```text
enum Town
  LS = 0
  SF = 1
  LV = 2
end
```

Enum members can be separated with line breaks \(see the example above\) or with a comma:

```text
enum Town
  LS = 0, SF = 1, LV = 2
end
```

It is possible to define many enumerated types in one file. Each enum must have an unique name.

{% hint style="warning" %}
No comments or any extra syntax are allowed in the enums file.
{% endhint %}

### Enum values

Each enum member gets a value either implicitly or explicitly. Explicit values are getting assigned when a combination of the equal sign and the value follow the member name. Sanny Builder allows integer numbers and string literals to be used as enum values:

```text
enum Town
  LS = 0
  SF = 1
  LV = 2
end
```

`Town.LS` is equal to `0`, `Town.SF` is equal to `1` and `Town.LV` is equal to `2`.

```text
enum TicTacToe
   Player1 = 'X'
   Player2 = 'O'
end
```

`TicTacToe.Player1` is equal to `'X'` and `TicTacToe.Player2` is equal to `'O'`.

Implicit values are getting assigned automatically starting from `0` for the first member, `1` for the second member, `2` for the third and so on:

```text
enum Town
  LS
  SF
  LV
end
```

`Town.LS` is equal to `0`, `Town.SF` is equal to `1` and `Town.LV` is equal to `2`.

For a mix of implicit and explicit values the following rules take place:

* a member following an explicit value gets assigned to that value incremented by `1`

```text
enum E
  A = 10
  B
  C = 100
  D
  E
end
```

`E.A` = `10`, `E.B` = `11`, `E.C` = `100`, `E.D` = `101`, `E.E` = `102`

*  a member following an explicit string value gets its value after the member name:

```text
enum Month
  Jan = "January"
  Feb = "February"
  March
end
```

`Month.Jan` = `"January"`,   
`Month.Feb` = `"February"`,   
`Month.March` = `"March"`

{% hint style="warning" %}
An enum can't have a mix of both integer and string values.  The first explicit value takes control of what type of values this enum gets:

```text
enum Int
  X, Y // X = 0, Y = 1,
end

enum String
  X, Y = "Y" // X = "X", Y = "Y"
end

```
{% endhint %}

