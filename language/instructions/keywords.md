# Keywords

Keyword syntax is the way to encode script instructions using special words. In general, any command name as defined in [Sanny Builder Library](https://library.sannybuilder.com) is a valid keyword.&#x20;

When using keywords, they must be the first word on the line, followed by arguments (if any).&#x20;

Here is an example of a WAIT command using its name as the keyword:

```pascal
wait 0
```

Extra words are allowed (similarly to [opcode syntax](opcodes.md)):

```pascal
CREATE_PLAYER 0 at 811.875 -939.9375 35.75 store_to $player 
```

A keywords list can be displayed after pressing `Ctrl+Space`.



### Extra keywords

{% hint style="warning" %}
Editing `keywords.txt` is deprecated and legacy keywords are left only for backward compatibility with old scripts. Adding new keywords is discouraged.
{% endhint %}

Edit modes can define extra aliases to command names in the file [keywords.txt](../../edit-modes/#keywords):

```javascript
0002=jump
0002=goto
```

```javascript
jump @label // 'jump' is an alias to the GOTO command
```
