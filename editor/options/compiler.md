# Compiler

<div align="left"><figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure></div>

## File Name Format

<div align="left"><figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure></div>

These fields specify the path and name for compiled files using placeholder variables:

* `$dir` – input file directory path
* `$name` – input file name (without extension)
* `$ext` – input file extension

**Example:** Input file: `C:\MyDir\main.txt`

* `$dir` = `C:\MyDir`
* `$name` = `main`
* `$ext` = `.txt`

Using format `$dir\$name.scm` creates output file: `C:\MyDir\main.scm`

## String Case

![](<../../.gitbook/assets/image (23).png>)

Compiler will transform [string literals](../../language/data-types/#string-literals) to selected case.

## Options

### Strict IF Validation

The compiler counts and validates number of used conditions in an IF statement. The upper limit is `8`.

### Ranges check

The number of local and global [variables](../../language/data-types/variables.md) is [limited](../../scm-documentation/gta-limits.md). When this option is checked, the compiler checks if a variable fits the available range.

### Add extra info to SCM

If this option is checked the compiler adds extra information at the end of the resulting file. This info is used later when this file gets disassembled to restore the source closer to the original. The following data is stored:&#x20;

* [HEX..END](../../language/instructions/hex..end.md) constructs offsets
* [global variables](../../language/data-types/variables.md#global-variables) names
* full source code (use [$NOSOURCE](../../language/directives.md#usdnosource) to disable)
* current [edit mode](../../edit-modes/)

{% hint style="info" %}
Starting from v3.8.0 the disassembler can [ignore extra information](../console.md#skip_extra_info).
{% endhint %}

### Show warning

This option is only used during compilation of the San Andreas scripts. If the game is running, the file `script.img` containing external scripts can't be overwritten as the game uses this file and the compiler complains about it. You may disable the warning by unchecking this box.
