# Switch

**Switch statement** compares a variable with one or many given values and executes a block of code associated with this value when a match is found. Starting from v4.0, Sanny Builder supports it for all games.

### Syntax

```pascal
switch <var>
   case <n1>, <n2>, ... <n3>
     // do something if <var> is equal to n1, n2, or n3
   case <n4>
     // do something if <var> is equal to n4
   default
     // do something if none of the values above matched the variable
end
```

`<var>` a global or local [variable](../data-types/variables.md). Can be an integer, float, or string variable.\
`<n>` - a comma-separated list of values the variable is compared with. Sanny uses `==` [operator](../instructions/expressions.md) to compare values. `n` can be an integer number, float, string, also a [constant](../data-types/constants.md).

{% hint style="info" %}
Each case can be associated with up to `8` values.
{% endhint %}

Default case is optional and can be omitted. When provided, default must be the last in the list of cases.

Switch statement does not support any extra instructions outside of `case` or `default` blocks. It also does not support a "fall through" behavior usually found in C-like languages. When the case block ends, the control flow is transferred out of the switch statement.

#### Example

```pascal
switch 0@
   case 1, 2, 3
     0ace: "Value is 1, 2, or 3"
   case 5
     0ace: "Value is 5"
   default
     0ace: "Value is not 1, 2, 3, or 5"
end
```

