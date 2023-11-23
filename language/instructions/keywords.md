# Keywords

Keyword syntax is the way to encode script instructions using special words. In general, any command name as defined in [Sanny Builder Library](https://library.sannybuilder.com) is a valid keyword.&#x20;

When using keywords, they must be the first word on the line, followed by arguments (if any).&#x20;

Here is an example of a WAIT command using its name as the keyword:

```
wait 0
```

Extra words are allowed (similarly to [opcode syntax](opcodes.md)):

```
CREATE_PLAYER 0 at 811.875 -939.9375 35.75 store_to $player 
```

Edit modes can define extra aliases to command names in the file [keywords.txt](../../edit-modes/#keywords):&#x20;

```
jump @label // 'jump' is an alias to the GOTO command
```

A keywords list can be displayed after pressing `Ctrl+Space`.
