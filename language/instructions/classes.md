# Classes

A **class** is a group of commands applied to the in-game entities: player, peds, objects, etc. For example, the `Player` class groups the commands performed over the player character.

## General Syntax

Syntax:\
`<Class name>.<Class member>(parameters)`

`Class name` - the name of a group of commands defined in the `classes.db` file for this edit mode\
`Class member` - one of the commands included in the class\
`Parameters` - 0 or more comma-delimited [parameters](../data-types/)

```
Player.SetMinWantedLevel($PLAYER_CHAR, 2)
```

`Player` - class name\
`SetMinWantedLevel` - class member\
`$PLAYER_CHAR, 2` - two parameters for `SetMinWantedLevel`

There are three types of class members:

* conditions
* methods
* properties

### Conditions

The list that appears when you press `Ctrl+Space` marks conditional commands with the word `Check`. They are used in [conditional expressions](../control-flow/conditions.md):&#x20;

```
if
    Player.Defined($PLAYER_CHAR)
jf @anywhere
```

### Methods

Methods are regular commands used to complete a single in-game action, e.g. moving an object, destroying a vehicle, etc.:

```
Object.PutAt($crate, 10.0, -25.5, 12.2)
Car.Destroy($car)
```

They are marked with the work `proc` in the list of class members.

A special kind of methods is a constructor. A constructor creates a new instance of a class and stores its handle to a variable.

In Sanny Builder the constructor can be written in two equivalent ways:

```
Player.Create($PLAYER_CHAR, #NULL, 2488.5601, -1666.84, 13.38)

```

```
$PLAYER_CHAR = Player.Create(#NULL, 2488.5601, -1666.84, 13.38)
```

### Properties

Property allows you to access class attributes and/or modify them.

For example, the `.Money` property of the `Player` class allows to operate with the amount of money of the player:

```
Player($PLAYER_CHAR).Money += 1000000 // add more money
Player($PLAYER_CHAR).Money > 461@ // check the amount
4@ = Player($PLAYER_CHAR).Money // read the amount and store in variable
```

{% hint style="warning" %}
In the current version the compiler ignores whitespace characters in [string literals](../data-types/#string-literals) used in property parameters:

```
0@ = File.Open("file name","wb")
```

will be compiled as:

```
0@ = File.Open("filename","wb")
```
{% endhint %}

## Class Instances

Almost all class members take a variable as the first parameter. This variable holds a handle of the class instance which is a concrete in-game entity the command is applied to:

```
Player.Build($PLAYER_CHAR)
```

`$PLAYER_CHAR` - the class instance.&#x20;

For some in-game entities there is only one instance to exist. An example of that would be the camera that controls what the player can see. The members of classes for such entities do not require a variable with the class instance:

```
Camera.SetBehindPlayer()
```

### Declaring a class instance

Variables can be [declared](../data-types/variables.md#var-end-construct) using a class name as the type:

```
var
    $PLAYER_CHAR: Player
end
```

It instructs the compiler that `$PLAYER_CHAR` holds an instance of the class `Player`. This variable can serve as an alias to the class name:

```
if
    $PLAYER_CHAR.Defined
jf @anywhere
```

{% hint style="warning" %}
If a variable substitutes a class name, the compiler also makes it the first parameter, hence no need to use it again in the list of parameters:

```
$PLAYER_CHAR.SetClothes("PLAYER_FACE", "HEAD", Head)
```

is equivalent to:

```
Player.SetClothes($PLAYER_CHAR, "PLAYER_FACE", "HEAD", Head)
```
{% endhint %}

Variables declared as instances of a class can be redeclared with another type.

### The `Model` Class&#x20;

[Model names](../data-types/#model-names) are always instances of the `Model` class:

```
#AK47.Load
  
:loop
wait 0
if
  #AK47.Available
jf @loop
```

It is equivalent to:

```
Model.Load(#AK47)

:loop
wait 0
if
    Model.Available(#AK47)
jf @loop
```

## Class constants

Class parameters can be assigned to an [enumerated type](../../edit-modes/enums.txt.md). It makes the source code more readable:

```
Player.SetClothes($PLAYER_CHAR, "VEST", "VEST", BodyPart.Torso)
```

The last parameter (`BodyPart.Torso`) is a member of the `BodyPart` enum substituted with `0` during compilation.  The enums and values are defined in the `enums.txt` file.

#### Extended parameters (deprecated)

Sanny Builder prior to v3.6 defined special constants for class members in the file `classes.db` . These parameters were called extended. This solution only allowed for one extended parameter per class member.&#x20;

Since v3.6 class members use enum names as their types and may have any number of enumerated parameters.&#x20;

For backward compatibility Sanny Builder still supports old extended parameters during compilation.  `classes.db` keeps them under the `DEPRECATED_ENUMS` section.

