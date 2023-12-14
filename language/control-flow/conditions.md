# Conditions

A **conditional** **statement** allows to evaluate one or more conditional instructions and based on the result of the evaluation either execute or skip a block of code. [Conditional statements](https://en.wikipedia.org/wiki/Conditional\_\(computer\_programming\)) can be found in nearly all programming languages. It is an important part of the control flow.&#x20;

### Single Condition

A conditional statement starts with an **IF** keyword and ends with an **END** keyword.

#### Syntax

```pascal
if
  <condition>
then
  <consequent>
else
 <alternative>
end
```

`<condition>` - a conditional instruction. This instruction turns the condition result into either `true` or `false.`\
`<consequent>` - a branch of the code that executes if the condition result is `true`.\
`<alternative>` - an optional branch of the code that executes if the condition result is `false`. If `else` is omitted the flow skips the `consequent` branch and continues after a closing `end` keyword.

#### Example

```pascal
if
  is_player_playing 0
then
  0ace: "player is ready"
else
  0ace: "player is not ready"
end
```

Depending on the result of the `is_player_playing` instruction, one or another message will be displayed.

### Multiple Conditions (AND)

`if and` allows to combine up to `8` conditional instructions and execute a block of code if **all of them are `true`**.

#### &#x20;Syntax

```pascal
if and
  <condition 1>
  <condition 2>
  ...
  <condition 8>
then
  <consequent>
else
  <alternative>
end
```

`<consequent>` - a branch of the code that executes if all conditions are `true`.\
`<alternative>` - an optional branch of the code that executes if any condition is `false`. If `else` is omitted the flow skips the `consequent` branch and continues after a closing `end` keyword.

{% hint style="warning" %}
[Short-circuit evaluation](https://en.wikipedia.org/wiki/Short-circuit\_evaluation) is not supported. All conditions are evaluated regardless of the result of the preceding checks.
{% endhint %}

#### Example

Checking if a number is within the given range:

```pascal
int x
if and
  x >= 0
  x <= 10
then
  0ace: "x is between 0 an 10"
end
```

### Multiple Conditions (OR)

`if or` allows to combine up to `8` conditional instructions and execute a block of code if **at least one of them** **is `true`**.

#### &#x20;Syntax

```pascal
if or
  <condition 1>
  <condition 2>
  ...
  <condition 8>
then
  <consequent>
else
  <alternative>
end
```

`<consequent>` - a branch of the code that executes if any condition is `true`.\
`<alternative>` - an optional branch of the code that executes if all conditions are `false`. If `else` is omitted the flow skips the `consequent` branch and continues after a closing `end` keyword.

{% hint style="warning" %}
[Short-circuit evaluation](https://en.wikipedia.org/wiki/Short-circuit\_evaluation) is not supported. All conditions are evaluated regardless of the result of the preceding checks.
{% endhint %}

#### Example

Checking if the vehicle model matches one of the given choices:

```pascal
if or
  model == #PCG600
  model == #FREEWAY
then
  0ace: "model is either PCG600 or Freeway"
else
  0ace: "model is neither PCG600 nor Freeway"
end
```
