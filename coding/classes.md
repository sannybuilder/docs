# Classes

## Basic Concepts 

**A class** is a group of opcodes applied to in-game entities: player, peds, objects, etc.

Each class has a set of commands \(class members\). They can be split into the following groups:

* conditional opcodes
* regular opcodes \(methods\)
*  properties

### Conditional Commands 

Conditional commands are marked with the word `Check` in the resizable window that is displayed when you press `Ctrl+Space`. Many of these have the only parameter: the class owner \(a variable\).

Example:

```text
if
    Player.Defined($PLAYER_CHAR)
jf @anywhere
```

`Player` - class name   
`Defined` - class member   
`$PLAYER_CHAR` - class owner

### Regular Commands \(methods\)

Regular \(procedural\) commands are used to complete a single in-game action: move an object, destroy it and so on. A special kind of these commands is the constructor that creates an object \(an ped, a vehicle\) and stores its handle to a variable.

In Sanny Builder the constructor can be used either as a method or a property:

```text
Player.Create($PLAYER_CHAR, #NULL, 2488.5601, -1666.84, 13.38) - procedure
$PLAYER_CHAR = Player.Create(#NULL, 2488.5601, -1666.84, 13.38) - constructor
```

These create the same effect.

### Properties

Property allows you to read/write values to the class fields.

For example, the `Money` property of the class `Player` allows to operate with the following opcodes:

```text
0109: player $PLAYER_CHAR money += 1000000
010A:   player $PLAYER_CHAR money > 461@
010B: 4@ = player $PLAYER_CHAR money
```

With the property you can use the following commands without any opcodes:

```text
Player($PLAYER_CHAR).Money += 1000000
Player($PLAYER_CHAR).Money > 461@
4@ = Player($PLAYER_CHAR).Money
```

{% hint style="info" %}
In the current version there is a limit on using space characters in the string literals used as a parameter in a property. The compiler ignores these characters. For example, the command

```text
0@ = File.Open("file name","wb")
```

will be compiled as

```text
0@ = File.Open("filename","wb")
```
{% endhint %}

## Class Members 

There is a possibility of initializing the variables as class members to use them instead of class names:

```text
var
    $PLAYER_CHAR: Player
end
```

It declares the variable `$PLAYER_CHAR` as member of the class `Player`. So, the variable can be used instead of the class name:

```text
if
    $PLAYER_CHAR.Defined
jf @anywhere
```

{% hint style="info" %}
Such variables are compiled as the first parameter and therefore do not duplicate them.

```text
Player.SetClothes($PLAYER_CHAR, "PLAYER_FACE", "HEAD", Head)

$PLAYER_CHAR.SetClothes("PLAYER_FACE", "HEAD", Head))
```
{% endhint %}

These variables can be redeclared with another type.

## `Model` Class 

The model identifiers are always the members of the `Model` class. You can reference this class using their names:

```text
#AK47.Load
  
:loop
wait 0
if
  #AK47.Available
jf @loop
```

It is the same as:

```text
Model.Load(#AK47)

:loop
wait 0
if
    Model.Available(#AK47)
jf @loop
```

## Extended Parameters \(class constants\)

Some classes use parameters with special names. This possibility makes the source code more readable:

```text
Player.SetClothes($PLAYER_CHAR, "VEST", "VEST", Torso)
```

Last parameter \(`Torso`\) is the class constant that will be replaced with the number `0` at compilation.

These parameters are defined in the file `classes.db`.

For convenience, a list of extended parameters are displayed when you press `Ctrl+Space`. Simply put the cursor where an extended parameter should be, press `Ctrl+Space` and the parameters list will appear. You can then select a name from it and insert this into your code.

