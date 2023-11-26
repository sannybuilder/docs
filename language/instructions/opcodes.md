# Opcodes

{% hint style="warning" %}
This page describes the legacy script format, usually produced by the Sanny disassembler with the [option](../../editor/options/general.md#write-opcodes) "Write opcodes" enabled. It's recommended to use other available [syntactic forms](./) in new scripts.
{% endhint %}

Opcode syntax is the oldest and most basic way of encoding SCM instructions. Each instruction has an associated id (operation code, or **opcode**). This id can be written in a script as a 4-digit hexadecimal number, followed by a colon:

```
0000:
```

If the instruction does not require any arguments, that's all you need to compile it. Most of the time, though, instructions need some input values to customize their behavior:

```
0001: 1000
```

`0001:` is an opcode for the WAIT command. It has one input argument that defines how long the game should "wait" until it can proceed to the next instruction. In this case, the wait time is `1000` milliseconds, or one second.

Some instructions may return one or multiple values. Those values will be stored in the variables that you must provide:

<pre><code><strong>00BF: $hours $minutes
</strong></code></pre>

`00BF:` returns current in-game time (hours and minutes) and requires 2 variables. A choice of variables is on the scripter.

{% hint style="info" %}
Sanny's compiler only cares about numbers and strings when it comes to processing opcode arguments. Any other words serve as comments and are ignored (unless it's a [named variable](../data-types/variables.md#shorter-form-of-declaration) or [constant](../data-types/constants.md))

```
0001: wait 0 ms // 'wait' and 'ms' are ignored
```
{% endhint %}

Some instructions can be used as [conditions](../control-flow/conditions.md) to check on various things. You can combine up to 8 instructions in one check:

```pascal
if
  0018: $var 0 // test if $var is greater than 0
then
 ...
end
```

Any conditional opcode can be negated by adding `0x8000` to the id. For original opcodes it's as simple as changing the first `0` to `8`:

```pascal
if
  8018: $var 0 // test if $var is less than or equal to 0
then
 ...
end
```
