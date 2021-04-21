# Enums.txt

An **enumerated type** or **enum** is a finite set of constants \(called _enum fields_\) under a common prefix \(_enum name_\).

Enumerated types have a few advantages over ordinary constants. They don't pollute the global namespace and are the first-class citizens in the type system. Parameters with an enumerated type are limited on allowed values range which in turn helps to avoid errors caused by an invalid id usage.

**Enums.txt** is a text file that defines a list of the enumerated types available in the [edit mode](./).

## File Format

Each enumerated type is defined with the following syntax:

`enum <enum name>  
<enum fields>  
end`

`enum name` -  any combination of letters, digits and `_`   
`enum fields` - one or many lines with the format:  
    `<enum field name> [= <enum field value>]`   
    where  
    `enum field name` - any combination of letters, digits and `_`   
    `enum field value` - a number or a [string literal](../coding/data-types.md#string-literals) enclosed in double quotes. if not present, the compiler assigns a [new value](enums.txt.md#enum-values) automatically.

```text
enum Town
  LS = 0
  SF = 1
  LV = 2
end
```

Enum fields can be separated with line breaks \(see the example above\) or with a comma:

```text
enum Town
  LS = 0, SF = 1, LV = 2
end
```

It is possible to define many enumerated types in one file. Each enum must have an unique name.

{% hint style="warning" %}
No comments or any extra syntax are allowed in the enums file.
{% endhint %}

### Enum fields

Each enum field gets a value either implicitly or explicitly. Explicit values are getting assigned when a combination of the equal sign and the value follows the field name. Sanny Builder allows integer numbers and string literals to be used as enum values:

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
   Player1 = "X"
   Player2 = "O"
end
```

`TicTacToe.Player1` is equal to `X` and `TicTacToe.Player2` is equal to `O`.

Implicit values are getting assigned automatically starting from `0` for the first field, `1` for the second field, `2` for the third and so on:

```text
enum Town
  LS
  SF
  LV
end
```

`Town.LS` is equal to `0`, `Town.SF` is equal to `1` and `Town.LV` is equal to `2`.

For a mix of implicit and explicit values the following rules take place:

* a field following an explicit value gets assigned to that value incremented by `1`

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

*  a field following an explicit string value gets its value after the field name:

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

