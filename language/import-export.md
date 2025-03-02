# Import/Export

{% hint style="warning" %}
This page describes a new experimental feature added in [CLEO 5](https://cleo.li). In order to use it, CLEO 5 must be installed.

For technical details and specification refer to [Modules RFC](https://github.com/sannybuilder/dev/issues/264).
{% endhint %}

CLEO 5 allows to share reusable code across multiple scripts and projects in a form of **modules**.&#x20;

Modules are pre-compiled files that export [functions](functions.md). Scripts can import them by name and call as regular SCM functions. Modules act as libraries that can be developed independently from scripts consuming them.

### Export

To create a module with an exported function, create a new CLEO script with one or multiple functions. To make the function visible outside of the module, add an `export` keyword before function definition:

<pre class="language-pascal"><code class="lang-pascal"><strong>{$CLEO .mod}
</strong>
export function sum(a: int, b: int): int
  int result = a + b
  return result
end
</code></pre>

This is an example module with one exported function. Save it as `my.txt` and compile to get a `my.mod` file.

* A module can export multiple functions
* Some functions can remain private (not exported)
* Modules should not have any code outside of functions.

### Import

To use a module in a script, add an `import` statement in your code:

```pascal
{$CLEO .cs}
wait 2000

import sum from "my.mod" // see an example module above

int res = sum(10, 20) // call imported function with 2 arguments and store the result
print_help_formatted "10 + 20 = %d" res

terminate_this_custom_script
```

Compile this script and run in game to see the result.&#x20;

#### Syntax

```pascal
import <function name> from "<module path>"
```

* function name should match the exported function name. Name is case insensitive.
* module path should point to the module file relative to the current script.

To import multiple functions from the same module, separate them with commas:

```pascal
import <name 1>, <name 2>, <name 3> from "<module path>"
```

Imported functions are _opaque_, which means the compiler currently does not validate if it is called with the correct number of arguments. It is user responsibility to provide a correct number of arguments and also make sure there are enough variables to store the result, if the imported function returns any.

{% hint style="info" %}
Loading functions code from a module occurs in runtime. A module file has to be distributed along with script that uses it. Modules can be updated independently from scripts; scripts recompilation is not required as long as the exported function retains its name.
{% endhint %}
