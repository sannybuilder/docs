# Labels

Labels reference a location in the code. They can be used in certain control flow commands to perform unconditional (`jump`, `gosub`) or conditional jumps (`goto_if_false`).&#x20;

To create a new label in the code use `:` followed by a valid identifier (a label name).

```
:MyLabel
```

To reference this label in a command, use `@` followed by the label name.

```
jump @MyLabel
```

If a label name is written as a standalone statement followed by `()`, it represents a `gosub` command (a subroutine call):

```
// the following statements are equivalent
MyLabel()
gosub @MyLabel
```
