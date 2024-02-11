# SCM Debugger

Sanny Builder 4.0 offers a native debugger for SCM scripts. It means you can add breakpoints in your code and pause the game as it hits a breakpoint. You can then step through the code and inspect values of global and local variables.

{% embed url="https://www.youtube.com/watch?v=4-CiQZNQr18" %}

{% hint style="warning" %}
Debugging functionality is very basic at the moment. It only works with scripts located in`main.scm.` Only GTA San Andreas v1.0 is supported. CLEO scripts and other games are not supported.
{% endhint %}

### Configuring Debugger

Before using a debugger, configure a path to the game executable in the main [options](options/debugger.md). When Sanny knows the path, it can run a new instance of the game, or attach to the already running process.

You can also provide additional arguments that will be used when launching the game.

### Running the Debugger

Using the debug menu, you can start new game process and debug the scripts.&#x20;

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Alternatively, if the game is already running, you can simply attach to it. If attaching did not work, check the debugger.log in Sanny Builder root directory. It is possible that the game is already being debugged or it requires elevated permissions (i.e. you need to run Sanny Builder as admin).&#x20;

### Breakpoints

When you compile the script Sanny displays a green dot on each compiled line. Lines that did not produce any [instruction](../language/instructions/) (e.g. directives, comments, declarations, etc.) won't have a dot.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Green dots are clickable. When you click it, Sanny sets up a new breakpoint on this line and marks it red. Clicking a red dot removes the breakpoint.

### Stepping Through the Code

When the game encounters an instruction with a breakpoint it immediately pauses, and the debugger takes control. You can see the active line in red. From now on, you can click variable names and see their current values displayed at the bottom.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

To resume the game execution, click the `Continue` button  in the Debug menu or on the main toolbar ![](<../.gitbook/assets/image (7).png>). The game will continue as usual until it hits another breakpoint if any.

To step into the next instruction, click the `Step Into` button ![](<../.gitbook/assets/image (8).png>). The game will execute the current instruction and pause again.
