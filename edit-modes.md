# Edit Modes

An **edit mode** is a set of options determining behavior of Sanny Builder when working with scripts of a particular game. Fact is, there is no game in the GTA series with the script format same to the others. So, each game requires special settings while editing scripts. That's the reason why the edit modes are introduced in Sanny Builder.

An edit mode includes \(but not limited to\) the following options:

* Sanny Builder disassemble a script file in a specific way
* Sanny Builder can compile a script for the given game
* you may run the game or read/change the player coordinates

By default, there are 7 different modes:

* `GTA III`
* `GTA VC`
* `GTA SA` \(for community named opcodes\)
* `GTA LCS`
* `GTA VCS`
* `SA Mobile` \(for Android and iOS versions\)
* `GTA SA SCR` \(with original names for opcodes\)

You may add a new mode by manually editing the `games.xml` file  located in the `<SB>\data\ directory`.

To switch the edit mode, click at the right bottom corner of the Sanny Builder's main window. A list of the available modes will appear. Choose one and click it. Sanny Builder will reload all needed files and you may start working.

![](.gitbook/assets/edit_modes.png)

Before disassembling or compiling a script, make sure that the correct edit mode is active. Even if the script is compiled with no errors, the game will crash when trying to read a script in different format.

A compiled script file may have an information which game it is made for. So, if you decompile such a script in another edit mode being active, Sanny Builder will propose you to change the mode to the correct one. Declining this prompt may cause a crash of the disassembler, because the script format is unexpected for it.

