# Compiler

### Show warning

This option is only used during compilation of the San Andreas scripts. If the game is running, the file `script.img` containing external scripts can not be overwritten as the game uses this file and the compiler complains about it. You may disable the warning by unchecking this box.

### Strict IF Validation

The compiler counts and validates number of used conditions in an IF statement. The limit is `8`.

### Ranges check

The number of local and global [variables](../../language/data-types/variables.md) is limited. When this option is checked, the compiler checks if a variable fits the available range.
