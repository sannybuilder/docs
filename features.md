# Features

Sanny Builder provides the end-user the following features:

## Syntax Highlighting

Sanny Builder highlights different elements of the code for easier reading. The color scheme can be customized via the [options](options/syntax-highlighting.md).

## Bookmarks / Quick jump

You can bookmark a line by pressing `Ctrl+Shift+0..9` and then get back to it by pressing `Ctrl+0..9`. To delete all bookmarks, use the menu option `Edit->Clear All Bookmarks`. 

Alternatively you can go to a particular line using the `Go To Line` feature. Press `Ctrl+G`, enter the line number and the editor will move the cursor to it.

## InstaSearch

The InstaSearch feature allows to find a word or a label directly in the editor without using the `Find` dialog box.

To find an occurrence of the word under the cursor, press `Ctrl+Num6` to start searching it below in a code, or `Ctrl+Num4` to search above. The cursor will immediately move to the line where such word is found. Keep pressing `Ctrl+Num4/Num6` to find other occurrences of this word.

To jump to the line with a label \(e.g, `:MyLabel`\), put the cursor on the label reference \(`@MyLabel`\) and press `Ctrl+Num2`. The editor will move the cursor to the line with this label.

If InstaSearch did not find the word in the code, the cursor position remains unchanged.

Before changing the cursor position InstaSearch remembers it, so if you want to return back press `Ctrl+Num8`.

## Displaying Information about Opcode

When the [option](options/editor.md#editor-configuration) `Show opcode info` is enabled the bottom bar displays:

* a number of parameters for the current opcode;
* a model ID when the cursor is on the [model name](coding/data-types.md#model-names) and `IDE` files for the current [edit mode](edit-modes/#ide) have been loaded;
* a constant value when the cursor is on the constant name and the [language service](language-service.md) is enabled.

## Opcode Search

Use the built-in [Opcode Search tool](opcode-search-tool.md) to find an opcode you need.

## Player Coordinates Management

Press `Ctrl+Alt+1` when GTA San Andreas is running and the Coords Manager window will appear. You can read the player's coordinates from the game memory and modify them there. 

In the top edit line you can enter the XYZ coordinates, delimited by the space character or the comma character `,`. Additionally, you can insert the player's coordinates in the script source by pressing `Ctrl+Shift+C`. To insert the player's z-angle, press `Ctrl+Shift+E`.

## Keypress Recording \(Macro\)

You can record a key pressing sequence \(macro\) and playback it later. Consider the following code:

```text
$Actor = Actor.Create(CivMale, #MALE01, 100.0, 100.0, 10.0)
$ActorWithGun = Actor.Create(CivMale, #MALE01, 110.0, 100.0, 20.0)
$Gang01 = Actor.Create(CivMale, #MALE01, 120.0, 100.0, 30.0)
$Gang02 = Actor.Create(CivMale, #MALE01, 130.0, 100.0, 40.0)
$Killer = Actor.Create(CivMale, #MALE01, 140.0, 100.0, 50.0)
$ActorWithoutGun = Actor.Create(CivMale, #MALE01, 150.0, 100.0, 60.0) 
```

Say, you need to exchange the actor's handles in each pair \(i.e have `$ActorWithGun` instead of `$Actor`, and vice versa\).

Place the cursor in the first line before `$Actor` and press `Ctrl+M`. The editor immediately begins recording all keys - so be careful!

1. Press and hold `Ctrl` and press the `Right Arrow` button once 
2. Press `Shift+Home` and `Ctrl+Ins`.
3. Press the `Down Arrow` button. The cursor must be on the second line with the global variable in the clipboard
4. Press `Ctrl+Right Arrow` and `Shift+Ins`.
5. Press `Ctrl+Left Arrow`, `Shift+Home`, `Ctrl+Ins` and `Delete`
6. Press the `Up Arrow` button
7. Press `Ctrl+Shift+Right Arrow` and `Shift+Ins`
8. Press the `Home` button.

Now the first two lines should look like these:

```text
$ActorWithGun = Actor.Create(CivMale, 100.0, 100.0, 10.0)
$Actor = Actor.Create(CivMale, 110.0, 100.0, 20.0)
```

with the cursor being in the beginning of the first line. Now press `Ctrl+M` to stop recording.

You can playback the recorded sequence by pressing `Ctrl+P`. Place the cursor in the beginning of the third line, press `Ctrl+P` and the actor handles will be swapped.

During recording, you can pause/unpause it by pressing `Ctrl+P`.

## Replacing Mission Numbers with their Names

Sanny Builder allows using a mission name in the opcode `start_mission`. The mission name is the label defined with a `DEFINE MISSION` command. Say, you have:

```text
DEFINE MISSION 10 AT @MYMISSION
```

Instead of `start_mission 10` you can write`start_mission MYMISSION`.

There is also the [Replace Mission Numbers](options/general.md#replace-mission-numbers) option. When it's enabled, the decompiler automatically replaces all mission numbers with their names.

To call the mission names list, press `Ctrl+Space`. The cursor has to be directly after the `start_mission` command.

Additionally, you can use [InstaSearch](features.md#instasearch) to navigate to the mission code when the cursor is under the mission name.

## Custom Mission Titles

Since v3.2.0 Sanny supports custom mission titles for each available [edit mode](edit-modes/#missions). They are stored in the `missions.txt` file. This file is used by the disassembler to add the title as a comment on line with mission define \(`DEFINE MISSION`\) or start \(`mission_start`\) command. 

If a `SCM` file contains custom-made missions you may edit the `missions.txt` to have the correct titles after disassembling.

## Multilingual Interface

Sanny Builder has fully multilingual interface translated into 15 languages. You can switch the languages in the [options](options/general.md#interface-language) \(`F10`\). Refer to [sannybuilder/translations](https://github.com/sannybuilder/translations) for more information on how to create or update a translation.

## External Tools Menu

You can configure up to `9` apps to run when you need them. Each app has its own hotkey for your convenience. You may also pass the parameters to your app if needed. To pass the name of the currently opened file use the special word `$SB_FileName`.

Since v3.7.0 it's also possible to pass the variables `@sb:` and `@game:` that represent Sanny Builder directory and current game directory respectively into the command-line parameters of the external app:

```text
Parameters:
--cwd=@sb: --game-dir=@game:
```

## Commenting Code

Comments start with the double slash `//`, as seen in other programming languages. Everything after `//` to the end of the line is ignored by the compiler.

To comment out multiple lines or a part of the line, use block comments `{}`:

```text
0001: wait  {comments here} 0 ms
```

Since version 3.06 Sanny Builder also supports the C++-like comments `/* */`.

```text
0001: wait  /* comments here */ 0 ms
```

To comment out or uncomment multiple lines select them and press `Ctrl+Q` \(this hotkey is configurable in the [options](options/hotkeys.md)\).

## Checking for updates

Sanny Builder is able to check if a new version is available. To use this feature go to menu `Help->Check for update...`. The editor will connect to a remote server and if a newer version is available it prompts the download and install. 

The editor can also check for an update during startup if you enable this option in the updater window.

