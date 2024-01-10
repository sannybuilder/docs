# Labels

Labels mark a location in the code. They can be used by certain commands to perform unconditional (`jump`, `gosub`) or conditional (`goto_if_false`) transfer of control flow to the marked location.&#x20;

To create a new label in the code use `:` followed by a valid identifier (a label name).

```pascal
:MyLabel
```

To reference this label in a command, use `@` followed by the label name.

```pascal
jump @MyLabel
```

If a label name is written as a standalone statement followed by `()`, it represents a `gosub` command (a subroutine call):

```pascal
// the following statements are equivalent
MyLabel()
gosub @MyLabel
```
