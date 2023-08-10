# 0090: Duplicate constant

The compiler finds a duplicate constant declaration. It happens when there is a `const..end` struct with the constant name that matches:

* another constant declared anywhere in the same file or any included files
* a local variable declared using `int` or `float` keywords.

For example, this code would produce an error:

```
const x = 1

int x
```

**Possible solutions:** give the constant another name.
