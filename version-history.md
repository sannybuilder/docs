# Version History

## v. 3.9.1 - 18.09.2023

* array name in expressions without opcode could be a constant [#250](https://github.com/sannybuilder/dev/issues/250)&#x20;
* preserve global variable index when disassembling with extra info [#251](https://github.com/sannybuilder/dev/issues/251)&#x20;
* default choice for option [Case converting](editor/options/formats.md#case-converting) should be "As is" [#256](https://github.com/sannybuilder/dev/issues/256)
* fix an issue with compiling opcode 0B17 [#254](https://github.com/sannybuilder/dev/issues/254)&#x20;
* fix an issue when Sanny doesn't present the option to use the included script text. [#258](https://github.com/sannybuilder/dev/issues/258)&#x20;
* fixed some issues with string variables [#259](https://github.com/sannybuilder/dev/issues/259), [#265](https://github.com/sannybuilder/dev/issues/265)

## v. 3.9.0 - 09.09.2023

* command names defined in [Sanny Builder Library](https://library.sannybuilder.com) JSON files are now valid [keywords](language/instructions/keywords.md)
* [HEX..END](language/instructions/hex..end.md#byte-repetition) improvements (repeat the same byte N times, include binary files)
* simplified [const](language/data-types/constants.md#syntax) and [variable](language/data-types/variables.md#declaring-a-variable-type) declarations (`const x = 1, y = 2`, `float x, y, z`)
* new [operators](language/instructions/expressions.md#bitwise) (`bitwise`, `=@`, `=#`)
* `{$INCLUDE_ONCE}` [directive](language/directives.md#usdinclude\_once)
* adding new [edit modes](edit-modes/) can be done by copying them into the `data` folder, the `modes.xml` is gone
* bug fixes and other changes

👏 Thanks to all people who helped and contributed to this release, and many thanks to my supporters on [Patreon](https://patreon.com/seemann).

{% hint style="warning" %}
Previous versions allowed the compilation of some broken code. Now, it will produce an error. You can find examples of such code [here](https://github.com/sannybuilder/dev/issues/231#issuecomment-1627984136).
{% endhint %}

[Complete list of changes](https://github.com/sannybuilder/dev/issues/231)

## v. 3.8.5 - 22.02.2023

* fix bug [#216](https://github.com/sannybuilder/dev/issues/216)

## v. 3.8.4 - 17.02.2023

* keep previously opened documents when launching SB with an input file (Open with) [#151](https://github.com/sannybuilder/dev/issues/151)
* add "--decompile" parameter to [CLI](editor/cli.md#decompile)
* fix bugs [#212](https://github.com/sannybuilder/dev/issues/212), [#213](https://github.com/sannybuilder/dev/issues/213), [#180](https://github.com/sannybuilder/dev/issues/180)
* fix some compilation issues with classes using string literals

## v. 3.8.3 - 08.01.2023

* fix bugs [#210](https://github.com/sannybuilder/dev/issues/210), [#204](https://github.com/sannybuilder/dev/issues/204), [#168](https://github.com/sannybuilder/dev/issues/168)
* fix [a bug](https://github.com/sannybuilder/GetObjectID/issues/1) in model search
* update CLEO+ plugin to [1.1.3](https://github.com/JuniorDjjr/CLEOPlus/releases/tag/v1.1.3)

## v. 3.8.2 - 08.09.2022

* fix bugs [#200](https://github.com/sannybuilder/dev/issues/200), [#187](https://github.com/sannybuilder/dev/issues/187)

## v. 3.8.1 - 01.09.2022

* added support for more commands terminating an if statement with multiple conditions [#133](https://github.com/sannybuilder/dev/issues/133)

```
    if and
        0AB0: is_key_pressed 9
	0AB0: is_key_pressed 10
    0AA0: gosub_if_false @label // was not working before, now compiles
```

* new and updated [translations](https://github.com/sannybuilder/translations) (Spanish, Ukrainian, Romanian, Armenian)
* [new color themes](https://github.com/sannybuilder/themes) contributed by the users
* [massive update](https://github.com/MatiDragon-YT/help-system) for local help files (CHM)
* new [edit mode](edit-modes/) for GTA SA PS2 with PS2 CLEO commands
* updated local [CLEO](https://cleo.li/) and plugin files:&#x20;
  * CLEO for San Andreas 4.4.1
  * CLEO for GTA III and Vice City 2.0.0.6
  * plugin [CLEO+ 1.1.2](https://github.com/JuniorDjjr/CLEOPlus/releases/tag/v1.1.2)
* fixed bugs [#172](https://github.com/sannybuilder/dev/issues/172), [#189](https://github.com/sannybuilder/dev/issues/189)

👏 Thanks to everyone who contributed to this version: [NicusorN5](https://github.com/NicusorN5), [Junior\_Djjr](https://github.com/JuniorDjjr), [wmysterio](https://github.com/wmysterio), [MatiDragon](https://github.com/MatiDragon-YT), [DanielSant0s](https://github.com/DanielSant0s), [JaggerJam69](https://github.com/JaggerJam69), [Vital](https://github.com/VitalRus95), [Sdas50](https://github.com/Sdas50), [nick7](https://github.com/nick7)

[Complete list of changes](https://github.com/sannybuilder/dev/issues/182)

## v. 3.8.0 - 04.08.2021

* [integration with Sanny Builder Library](editor/features.md#integration-with-sanny-builder-library): a new portal documenting all known opcodes
* 16 [new color themes](https://github.com/sannybuilder/themes)
* disassembler now outputs the content of a `hex..end` block as a string if it's a sequence of ASCII characters ending with 00 [#33](https://github.com/sannybuilder/dev/issues/33)
* [new debug option](editor/console.md#skip\_extra\_info) to let disassembler ignore custom information attached to the compiled script
* [new CLI parameter](editor/cli.md#option) to launch the editor with custom options
* [custom user templates](edit-modes/code-templates.md#adding-a-new-template) are now stored in a separate file and kept between updates
* [hotkeys](editor/hotkeys.md) using Numpad buttons have been changed (Zoom text: Ctrl + +/- and Navigate to label and back: Alt + Right/Left)
* updated [CLEO+](https://github.com/JuniorDjjr/CLEOPlus) plugin to v1.0.8
* updated translations to Hungarian, Spanish, Ukrainian and Chinese languages
* [fixed 16 bugs](https://github.com/sannybuilder/dev/issues/130#issue-805022048)

👏 Kudos to contributors to this release: [forms55](https://github.com/forms55), [MatiDragon](https://github.com/MatiDragon-YT), [Vital](https://github.com/VitalRus95), [wmysterio](https://github.com/wmysterio), [XMDS](https://github.com/XMDS)

[Complete list of changes](https://github.com/sannybuilder/dev/issues/130)

## v. 3.7.0 - 30.01.2021

* declared [constants](language/data-types/constants.md) are getting highlighted ([#28](https://github.com/sannybuilder/dev/issues/28))
* the autocomplete list displays declared constants ([#40](https://github.com/sannybuilder/dev/issues/40))
* each editor tab maintains its own [edit mode](edit-modes/) selection ([#87](https://github.com/sannybuilder/dev/issues/87))
* new VC Mobile mode with CLEO Android opcodes ([sannybuilder/data#11](https://github.com/sannybuilder/data/pull/11))
* added spaceeinstein's [Opcode Restoration project](https://github.com/cleolibrary/opcodes-restoration-project) opcodes in VC PC mode
* error messages now have a link to localized documentation if possible ([#101](https://github.com/sannybuilder/dev/issues/101))
* [user tools](editor/features.md#external-tools-menu) configuration supports **@sb:** and **@game:** variables ([#72](https://github.com/sannybuilder/dev/issues/72))
* [CLEO+](https://github.com/JuniorDjjr/CLEOPlus) plugin updated to v1.0.7
* fixed bugs: [#103](https://github.com/sannybuilder/dev/issues/103) [#114](https://github.com/sannybuilder/dev/issues/114) [#120](https://github.com/sannybuilder/dev/issues/120)

{% hint style="info" %}
Read more on constants highlighting there: [Language service](editor/language-service.md).
{% endhint %}

[Complete list of changes](https://github.com/sannybuilder/dev/issues/90)

:clap: Kudos to [XMDS](https://github.com/XMDS) for contributions to this release.

## v. 3.6.2 - 29.11.2020

* fixed a bug with labels missing in disassembled CLEO scripts [#99](https://github.com/sannybuilder/dev/issues/99)

## v. 3.6.1 - 27.11.2020

* updated translation to Ukrainian language
* updated CLEO+ plugin to v1.0.4
* updated opcode definitions and keywords for CLEO opcodes [#95](https://github.com/sannybuilder/dev/issues/95)
* fixed several regression bugs in compiler [#96](https://github.com/sannybuilder/dev/issues/96), [#98](https://github.com/sannybuilder/dev/issues/98)
* minor fixes and improvements (see the [complete list](https://github.com/sannybuilder/dev/issues/91))

:clap: Kudos to [wmysterio](https://github.com/wmysterio/) and [XMDS](https://github.com/XMDS) for their contributions.

## v. 3.6.0 - 11.11.2020

* support for [enumerated types](language/instructions/classes.md#class-constants) in classes
* new [types](edit-modes/opcodes-list-scm.ini.md#parameter-types) of opcode parameters: [`m%`](https://github.com/sannybuilder/dev/issues/10) and [`k%`](https://github.com/sannybuilder/dev/issues/21)
* initial support for language [extensions](edit-modes/extensions.md)
* better integration with CLEO library:
  * updated third-party tools in the `tools` directory:
    * CLEO v4.4
    * SCRLog v2020.2
    * added [CLEO+ plugin](https://github.com/sannybuilder/dev/issues/71) for GTA SA with 250+ new opcodes
  * [recognize Cleo for Android](https://github.com/sannybuilder/dev/issues/64) scripts (`*.csa`, `*.csi`) as compiled scripts
  * compiler uses CLEO opcodes `0A9E`, `0A9F`, `0A90`, `0A91` [in certain expressions when no opcode is supplied](https://github.com/sannybuilder/dev/issues/58#issuecomment-723376464)
  * unified description and keywords for CLEO opcodes across different edit modes
* added [keywords](language/instructions/keywords.md) for all opcodes in GTA SA SCR mode
* word _thread_ has been replaced with _script_ in opcode definitions and keywords ([see why](https://gtamods.com/wiki/Talk:Script#Thread-%3EScript\).))
* IDE updates:
  * the game directory is no longer required to compile a script ([#48](https://github.com/sannybuilder/dev/issues/48))
  * the "Compile and Copy" destination could be configured ([#9](https://github.com/sannybuilder/dev/issues/9))
  * updated Spanish and Italian translations
  * added option to associate Sanny Builder with `*.csa` and `*.csi` files (CLEO Android scripts).

[Complete list of changes](https://github.com/sannybuilder/dev/issues/61)

:clap: Kudos to [MatiDragon](https://github.com/MatiDragon-YT) and [Wesser](https://gtaforums.com/profile/172776-wesser/) for updated translations.

## v. 3.5.1 - 21.08.2020

* fixed a bug with LCS and VCS compilation ([#56](https://github.com/sannybuilder/dev/issues/56))
* arrays in LCS and VCS now get custom names from `CustomVariables.ini` and `CustomArrays.ini` ([#53](https://github.com/sannybuilder/dev/issues/53))

:clap: Kudos to [darkdraggy](https://gtaforums.com/profile/1097463-darkdraggy/) for reporting the first bug and helping to test the fix.

## v. 3.5.0 - 18.08.2020

* updated [command line interface](editor/cli.md)
  * Unix-style syntax with hyphens ([#42](https://github.com/sannybuilder/dev/issues/42))
  * new options [`-x`](editor/cli.md#x), [`--game`](editor/cli.md#game), [`--mode`](editor/cli.md#mode)
* improved [edit modes](edit-modes/)
  * `games.xml` renamed to `modes.xml`, inner [structure](edit-modes/#file-format) updated
  * modes can now [inherit](edit-modes/#extends) properties of other modes (useful for different versions of one game)
  * a new mode for SA v2.0 (using [`CustomLabels_v2.ini`](edit-modes/customlabels.ini.md))
  * separate modes for VCS PSP and VCS PS2 ([#41](https://github.com/sannybuilder/dev/issues/41))
  * support for [custom IDE/DAT](edit-modes/#ide) files
  * "hot" reloading of modes configuration ([#15](https://github.com/sannybuilder/dev/issues/15))
  * increased available space for the mode name section ([#8](https://github.com/sannybuilder/dev/issues/8))
* updated opcode definitions for LCS/VCS\*
* removed SAMB to SB converter ([#27](https://github.com/sannybuilder/dev/issues/27))
* fixed [file association](editor/options/general.md#file-association) ([#43](https://github.com/sannybuilder/dev/issues/43#issuecomment-670219723))
* fixed a bug with LCS and VCS compilation ([#49](https://github.com/sannybuilder/dev/issues/49), [#0053](http://bugs.sannybuilder.com/view.php?id=53), [#0064](http://bugs.sannybuilder.com/view.php?id=64))
* fixed an issue with [Opcode Search Tool](editor/opcode-search-tool.md) window not available after minimize ([#35](https://github.com/sannybuilder/dev/issues/35))

{% hint style="warning" %}
New opcode definitions for GTA LCS and GTA VCS are incompatible with the previous definitions. You must disassemble the `main.scm` prior to making any scripts for those games.
{% endhint %}

:clap: Kudos to [marcelo\_20xx](https://gtaforums.com/profile/95582-marcelo\_20xx/) and [fastman92](https://gtaforums.com/profile/423631-fastman92/) for their awesome contribution to this release.

## v. 3.4.1 - 06.08.2020

* fixed incorrect number of parameters in opcode `04E3` in `VCSSCM.INI`
* fixed the issue with the disassembler ignoring `Write opcodes` [option](editor/options/general.md#write-opcodes) and producing a callable label when a regular label is expected

## v. 3.4.0 - 04.08.2020

* added compiler support for the `SCM` format of GTA: Vice City Stories ([#2](https://github.com/sannybuilder/dev/issues/2))
* added syntax for [declaring](language/data-types/variables.md#shorter-form-of-declaration) local variables with custom names ([#32](https://github.com/sannybuilder/dev/issues/32))
* added a simpler form of calling subroutines using [labels](language/data-types/#labels): a label name followed by a pair of parentheses `()` substitutes a `gosub` command
* added more customization points for [edit modes](edit-modes/):
  * path to a GXT file used by the disassembler ([#7](https://github.com/sannybuilder/dev/issues/7))
  * path to `opcodes.txt` ([#5](https://github.com/sannybuilder/dev/issues/5))
  * exclusive [code templates](edit-modes/code-templates.md)
* added a new tutorial on higher level constructions in the Sanny Builder language, see `help\examples` directory
* IDE updates:
  * `Run San Andreas` menu action now checks for `gta-sa.exe` (Steam)
  * a new menu item to quickly bootstrap a CLEO script file (see the bottom note in [Code Templates](edit-modes/code-templates.md))
  * links to the new documentation portal in the main menu and error messages
* minor updates:
  * updated opcode descriptions (player money += in SA, award\_achievement in SA Mobile, `0479` in VCS)
  * renamed variables `script_controlled_player` and `flag_player_on_mission` to `PLAYER_ACTOR` and `ONMISSION` respectively in GTA III's `CustomVariables.ini` ([#3](https://github.com/sannybuilder/data/issues/3))
  * reverted files in the `help\GXT Strings` directory to the older version ([#25](https://github.com/sannybuilder/dev/issues/25))
  * renamed `macroes.txt` to `templates.txt`
* [translation updates](https://github.com/sannybuilder/translations/milestone/1)

:clap: Kudos to [OrionSR](https://gtaforums.com/profile/213525-orionsr/), [ZAZ](https://gtaforums.com/profile/67506-zaz/), [XMDS](https://gtaforums.com/profile/1034872-xmds), and [Wesser](https://gtaforums.com/profile/172776-wesser/) for their awesome contribution to this release.

## v. 3.3.3 - 20.10.2019

* fixed a [bug](http://bugs.sannybuilder.com/view.php?id=52) causing incorrect external scripts compilation

## v. 3.3.2 - 19.10.2019

* fixed bugs [#0036](http://bugs.sannybuilder.com/view.php?id=36), [#0050](http://bugs.sannybuilder.com/view.php?id=50)
* fixed the opcode `059C` in the Vice City mode

## v. 3.3.1 - 14.09.2019

* fixed the bug [#0048](http://bugs.sannybuilder.com/view.php?id=48)
* included `constants.txt` missing in the `GTA SA` mode

## v. 3.3.0 - 08.09.2019

* added compiler support for the Liberty City Stories `SCM` format
* added aliases for the [timer variables](language/data-types/variables.md#timer-variables): `TIMERA` and `TIMERB`
* changed the [Ranges check](editor/options/general.md#ranges-check) option to apply to the global variables

## v. 3.2.4 - 04.08.2019

* fixed bugs [#0031](http://bugs.sannybuilder.com/view.php?id=31), [#0032](http://bugs.sannybuilder.com/view.php?id=32), [#0033](http://bugs.sannybuilder.com/view.php?id=33), [#0040](http://bugs.sannybuilder.com/view.php?id=40), [#0044](http://bugs.sannybuilder.com/view.php?id=44)
* fixed a regression defect when a CHM help file can not be open
* updated opcode definitions for GTA 3 and Vice City
* added IDE support for CLEO 2.0 for III and VC

## v. 3.2.3 - 07.07.2019

* improved support for the version of GTA San Andreas for Wi﻿nStore, Xbox 360, and P﻿S3
* fixed an issue with opcodes `09A4` and `0A18` not being properly decompiled in the SA\_Mobile mode

## v. 3.2.2 - 05.07.2014

* added translation into Korean language (thanks to MINE)
* improved [HEX..END](language/instructions/hex..end.md) construct processing
* fixed the bug [#0000028](http://bugs.sannybuilder.com/view.php?id=28)

## v. 3.2.1 - 04.05.2014

* added translation into Indonesian language (thanks to IMasterFX)
* CLEO for GTA III and CLEO for Vice City updated (thanks to Silent)
* fixed bugs [#0000026](http://bugs.sannybuilder.com/view.php?id=26), [#0000027](http://bugs.sannybuilder.com/view.php?id=27)

## v. 3.2.0 - 22.03.2014

* adding custom edit modes by editing the `games.xml` file is now possible
* new edit mode - `GTA SA SCR`
* variables can be quickly declared using a type name prefix
* CLEO updated to the version 4.3.16
* added the [InstaSearch](editor/features.md#instasearch) feature (formerly 'jump to label' function)
* mission names can be changed by editing appropriate `missions.txt` files
* improved [association](editor/options/general.md#file-association) of the script file extensions with Sanny Builder
* Sanny Builder only checks if the game directory path is not empty, no checks for specific files (such as an `.exe`)
* minor improvements in the SB updating feature
* changed the Sanny Builder icon and the menu icons
* fixed the bug [#0000024](http://bugs.sannybuilder.com/view.php?id=24)

## v. 3.1.4 - 22.02.2014

* CLEO updated to the version 4.3.14
* fixed minor interface glitches for hi-res displays
* updated German, Polish, Chinese, Ukrainian translations

## v. 3.1.3 - 22.12.2013

* added support for iOS and Android versions of GTA San Andreas
* a [code scan](editor/options/editor.md#code-scan-distance) value is now used when making a list of constants
* updated Chinese and German translations

## v. 3.1.2 - 06.10.2013

* added Czech translation
* added options to associate file extensions `.cs` and `.cm` with Sanny Builder
* fixed bugs [#0000011](http://bugs.sannybuilder.com/view.php?id=11), [#0000020](http://bugs.sannybuilder.com/view.php?id=20)

## v. 3.1.1 - 22.09.2013

* added a new directive [$OPCODE](language/directives.md#usdopcode) to register a new opcode in the script
* corrected behavior of the directive [$INCLUDE](language/directives.md#usdinclude) while scanning directories for the file
* fixed bugs [#0000005](http://bugs.sannybuilder.com/view.php?id=5), [#0000019](http://bugs.sannybuilder.com/view.php?id=19)

## v. 3.1.0 - 14.09.2013

* `VCSCM.ini` is updated to include opcodes for the GTA VC mobile version and unsupported opcodes
* when the option [Add extra info to SCM](editor/options/general.md#add-extra-info-to-scm) is enabled, Sanny Builder remembers the game a script is compiled for, to use the proper edit mode when decompiling
* when the option `Add extra info to SCM` is enabled, Sanny Builder adds a source code into a script file (only when the directive [$EXTERNAL](language/directives.md#usdexternal) or [$CLEO](language/directives.md#usdcleo) is present)
* added a new directive [$NOSOURCE](language/directives.md#usdnosource) to prohibit including a source code into a compiled script
* some hotkeys are now customizable in the options
* added a feature to check automatically if an update exists at the program startup
* [directives ](language/directives.md)`$VERSION` and `$VERSION_RESTORE` are deprecated
* updated Spanish and Chinese translations
* Coords manager is now able to change the player's angle in GTA VC
* The Sanny Builder installation now includes the [SCRLog CLEO plugin](http://www.gtagarage.com/mods/show.php?id=23846) by LINK/2012 (can be found in the `tools` folder)
* fixed bugs [#0000010](http://bugs.sannybuilder.com/view.php?id=10), [#0000014](http://bugs.sannybuilder.com/view.php?id=14), [#0000015](http://bugs.sannybuilder.com/view.php?id=15), [#0000016](http://bugs.sannybuilder.com/view.php?id=16)

## v. 3.09 - 28.07.2013

* Sanny Builder is licensed under the Sanny Builder Freeware/Donationware License Agreement
* added a feature to report found bugs via [the official bug tracker](http://bugs.sannybuilder.com)
* added a feature to check if an update is available
* Coords manager is upgraded to work with all known versions of GTA3, VC and SA (thanks to Silent)
* added an updated Chinese translation
* fixed bugs [#0000002](http://bugs.sannybuilder.com/view.php?id=2), [#0000003](http://bugs.sannybuilder.com/view.php?id=3), [#0000004](http://bugs.sannybuilder.com/view.php?id=4), [#0000006](http://bugs.sannybuilder.com/view.php?id=6), [#0000009](http://bugs.sannybuilder.com/view.php?id=9)
* minor design changes

## v. 3.08 - 05.07.2013

* added [Silent's ASI Loader](http://www.gtagarage.com/mods/show.php?id=21709) v1.1 as a default ASI loader for CLEO 3 and CLEO 4
* added Chinese translation
* added classes `File` and `Audiostream` for backward compatibility with CLEO 4 by Alien

{% hint style="info" %}
`File.Open`, `Audiostream.Load`, `Audiostream.Load3D` were methods in CLEO 4. Now they are properties. It means, if you get an error when compiling old sources with these commands, change their syntax to:\
`var = File.Open(file_name, mode)`\
`var = Audiostream.Load(file_name)`\
`var = Audiostream.Load3D(file_name)`
{% endhint %}

* the compiler now accepts a string literal as a parameter in a class property

{% hint style="info" %}
There is a [limit](language/instructions/classes.md#properties) on using space characters in such parameter.
{% endhint %}

* the compiler now throws an error for a malformed string literal like `text1"text2"` or `text1'text2'` (without a leading quotation mark)
* the compiler is able to compile comment markers (curly braces) within a string (`"{text1}text2"`)
* the semicolon (`;`) can not be used to comment out a line of the code
* changed the syntax of the [\debug](./#command-line-usage) parameter
* added flag icons for the available languages in the options
* fixed some issues with disassembling of the VCS SCM format

## v. 3.06 - 17.06.2013

* added new [operators ](language/instructions/built-in-commands.md)`++` and `--`
* added support for block [comments](editor/features.md#commenting-code) `/* */`
* `SASCM.INI` got an update from the [GTAG Database](https://gtagmodding.com/opcode-database/)
* replaced properties `Actor.Armour` and `Actor.Car` with their correct versions `Actor.AddArmour` and `Actor.MissionCar`
* added a new property `Actor.CurrentCar` for the opcode `03C0` in the SA and VC classes.
* added new hotkeys `Ctrl+Num+` and `Ctrl+Num-` to quickly change the text size
* Sanny Builder now remembers a number of closed files for the option [Load all closed files](editor/options/editor.md#editor-configuration)
* fixed a bug when the compiler failed to compile a source with multiple [HEX..END](language/instructions/hex..end.md) constructs
* fixed a bug of version 3.05 when the program hung on startup trying to open a file

## v. 3.05 - 05.06.2013

* added new translations for the following languages: Finnish, Polish, Hungarian, Turkish, Ukrainian
* the CLEO library updated to version 4.1.1.30f (CLEO 4 by Alien)
* added a possibility to install CLEO for GTA III and Vice City (made by Alien)
* opcode files (\*\*SCM.ini, opcodes.txt) replaced with the ones from the CLEO 4 library installation
* new [command line parameter](./#command-line-usage) `\nosplash`

## v. 3.04 - 17.08.2008

* the editor is able to to convert hexadecimal numbers to decimal ones and vice versa (`Ctrl+H`), and convert the model names to their IDs (`Ctrl+Alt+H`)
* removed a warning message about `script.img` being used by the game when compiling a CLEO script
* the post-compilation report shows the size of a CLEO script (as `Largest script`)
* fixed a bug when compiling an array with constant numeric indexes
* the installer no longer requires the system administrator rights

## v. 3.03 - 17.11.2007

* the previous version of CLEO had a bug
* minor changes (the toolbar position wasn't saved)

## v. 3.02 - 16.11.2007

* new version of the CLEO library
* main toolbar is movable
* the Compile+Copy feature (`F7`) does not create a copy of the output file if the source has `$E` or `$CLEO` directives
*   during a compilation run after pressing `F6`, the output file for a source file with the `$CLEO` directive

    is created in the same directory; after `F7` the output file is created in the CLEO directory (similarly to `SCM` files)
* new translations: Italian, Portuguese

## v. 3.01- 06.08.2007

* bug-fixes update

## v. 3.00 - 04.08.2007

* the CLEO 3 library is integrated into Sanny Builder
* disassembler supports the `SCM` format of Vice City Stories
* [constants ](language/data-types/constants.md)support
* new [directives](language/directives.md) `$INCLUDE`,`$EXTERNAL`,`$CLEO`
* [writing of the additional info](editor/options/general.md#add-extra-info-to-scm) to the end of a script file
* [custom arrays](editor/options/formats.md#custom-names) support
* a [possibility](editor/console.md#skip\_scm\_header) to decompile SCM files having no header
* an ability to create an external script named `AAA`
* a new [command line parameter](./#command-line-usage) `\compile`
* a possibility to use a floating-point value as the counter value in a [FOR..END](language/control-flow/loops.md#for-end) loop
* dropped support for the commands `WriteMem` and `ReadMem`
* a possibility to use regular expressions when searching
* a possibility to save a source file in the `RTF` or `HTML` formats
* an ability to skip the splashes at SA startup
* a new key combo `Ctrl+Enter`
* updated `SASCM.INI`

## v. 2.99e - 01.01.2007

* fixed a bug when parts of the code within the [HEX..END](language/instructions/hex..end.md) construct disappeared in [debug mode](editor/console.md#debug-options)
* a HEX..END construct now accepts the [aDMA](language/instructions/hex..end.md#using-adma-numbers) type and string literals
* a [FOR ](language/control-flow/loops.md#for-end)loop accepts model identifiers as the counter values

## v. 2.99d - 03.12.2006

* Memory Hacker became a [separate tool](https://sannybuilder.com/downloads).
* fixed a decompiler bug

## v. 2.99c - 30.11.2006

* added the Memory Hacker plug-in
* disassembler supports the `SCM` format of Liberty City Stories
* support for constant numbers as indexes of global [arrays](language/data-types/arrays.md)
* a global variable gets disassembled with the type [aDMA](language/data-types/#variables) (`&`) if its address is not divisible by 4
* the compiler uses default values during compilation of a`main.scm` with the missing header segments (`DEFINE XXX`)
* a possibility to Drag\&Drop a file into the editor to open it
* new preprocessor [directives](language/directives.md): `{$VERSION}`, `{$VERSION_RESTORE}`

{% hint style="info" %}
If you get a compiler error message like `Unknown directive xxxx` when compiling the sources from v2.99, replace the line `{$VERSION xxxx}` to any place after the header, for instance before the comment `//-------------MAIN---------------`
{% endhint %}

## v. 2.99 - 27.09.2006

* added new commands `WriteMem` and `ReadMem`
* support for [hexadecimal](language/data-types/#hexadecimal-numbers) numbers
* `HEX..END` statement accepts labels and global variables
* full support for the [ADMA](language/data-types/#variables) datatype
* an opportunity to give [custom names](editor/options/formats.md#custom-names) to labels
* an opportunity to choose a [different case](editor/options/formats.md#case-converting) for custom names and strings
* added [console](editor/console.md) to switch debug options
* decompiler supports `GXT` files of GTA III & GTA VC
* added escape sequences in [long string literals](language/data-types/#string-literals)
* information about [INI](edit-modes/opcodes-list-scm.ini.md) file (version, author, date)
* classes support the original order of the parameters (like in `SASCM.INI` by PLPynton). The script should have a line {`$VERSION x.0.xxxx`} to support such order, see comments in the `INI` about this
* added option to confirm an exit from the program
* a dropdown menu to switch [edit modes](edit-modes/)
* converting of the selected piece of code
* an opportunity to pass the current file name to an [external tool](editor/features.md#external-tools-plug-ins-menu)
* corrected some mistakes in the configuration files
* removed auto-casting of an integer number to the float one when a variable is declared as `Float`. Now the compiler chooses an opcode depending on the number type only (in math expressions without opcodes)
* reading/writing of the player's z\_angle in [Coord Manager](editor/features.md#player-coordinates-management); quick insertion of the z\_angle value in the script by pressing `Ctrl+Shift+E` (for SA)

{% hint style="info" %}
The following opcodes were changed in `SASCM.INI`: `0181`, `00c3`, `00c4` in order to support the commands `WriteMem` and `ReadMem`. The original scripts did not use these opcodes and the unmodified games do not implement them so it should not break existing scripts.
{% endhint %}

{% hint style="info" %}
The class member `Car.SetSpeedInstantly` was named incorrectly (with a wrong opcode) in the `classes.db` for SA. If you get an error message about this method during compilation, rename it to`Actor.DrivingPlane`. We apologize.
{% endhint %}

## v. 2.98 - 04.08.2006

* Sanny Builder became multilingual
* added menu for [external applications](editor/features.md#external-tools-plug-ins-menu)
* a special version of [Opcode Search Tool](editor/opcode-search-tool.md) has been built into SB. The details can be found in the file `OST Readme.txt`
* validating math expressions during disassembling when [Write opcodes](editor/options/general.md#write-opcodes) is disabled (to ensure that opcodes are used properly)
* an [opportunity to choose](editor/options/general.md#manual-img-opening) a `script.img` file manually if the folder with the `main.scm` file does not have one
* an opportunity to add a new [code template](editor/features.md#code-templates) directly from the editor; added template descriptions
* the list of models can be sorted alphabetically/by value (`Alt+S` when the list is active)
* minor corrections and changes

## v. 2.97 - 11.06.2006

* new data type: `&` for direct byte address ([ADMA](language/data-types/)).
* minor updates

## v. 2.96 - 01.04.2006

* improved the [jump to label](editor/features.md#instasearch) option
* added an opportunity to show the list of templates
* added an [option](editor/options/general.md#replace-mission-numbers) to replace mission numbers with their names
* fixed some bugs

## v. 2.9f - 18.02.2006

* the `DEFINE OBJECT` list is now optional (the compiler can make it out of model names used in the script)
* support for block comments `{}`
* keypress [recording](editor/features.md#keypress-recording-macro)
* minor changes

## v. 2.9 - 15.12.2005

* added [additional commands](language/instructions/built-in-commands.md)
* new operator `IN`
* added [IF..THEN..ELSE..END](language/control-flow/conditions.md#high-level-constructs)
* added support for `WHILE` and `REPEAT` [loops](language/control-flow/loops.md)
* added support for nested loops
* added a new function [Alloc](language/instructions/built-in-commands.md#alloc), allowing to assign a specific memory address to a global variable
* new comment style: `//`
* the editor now remembers the position of markers and the cursor in closed files

## v. 2.6 - 05.11.2005

* full support of `SCM` formats of Vice City and GTA 3
* an opportunity to [declare](language/instructions/classes.md#declaring-a-class-instance) variables and arrays as class instances
* added a feature to display the list of variables and labels
* added [loops](language/control-flow/loops.md) (`FOR..END`)
* minor changes:
  * missions can be referenced by their name (`start_mission MYMISSION` where `MYMISSION` is the label defined in line`DEFINE MISSION XX at @MYMISSION`)
  * `Ctrl+Space` displays the list of imported models (`DEFINE OBJECT`)
  * new [operator](language/control-flow/conditions.md#relational-operators) `<>`
  * if the disassembler can't find a `script.img` file, it uses the one from the game folder
  * added `handle` type for [arrays](language/data-types/arrays.md)
  * an [opportunity](editor/options/general.md#show-warning) to switch off a warning that the `script.img` file is being used by the game

## v. 2.5 - 10.10.2005

* added [properties](language/instructions/classes.md#properties) support
* added [code templates](editor/features.md#code-templates) support
* added construction [VAR...END](language/data-types/variables.md#var-end-construct) for variables declaration
* all math commands can be used without opcodes (`0004..008B`)
* new [operators](language/control-flow/conditions.md#relational-operators) `<` and `<=`
* added a capability that the compiler itself set necessary value for the [IF command](language/control-flow/conditions.md#low-level-if-statements)
* added [extended parameters](language/instructions/classes.md#extended-parameters-class-constants) support
* added models list showing
* minor changes and fixes

## v. 2.0 - 18.09.2005

* added [classes](language/instructions/classes.md) support
* added [keywords](language/instructions/keywords.md) support
* some math commands can be written without opcodes (e.g.`0004`, `0005`, `0006`, `0007`, `0038`, `0039`, `0042`, `0043`)
* for the opcode `00D6` the default parameter is `0` (`if` = `if 0`)
* added the [option](editor/options/formats.md#label-name-format) to customize labels output
* added [keywords](language/instructions/keywords.md) `True` and `False` which correspond to `1` and `0`
* added construction [HEX...END](language/instructions/hex..end.md) for writing hexadecimal values directly in a binary output

## v. 1.1 - 07.09.2005

* added [coords manager](editor/features.md#player-coordinates-management)
* some bugs fixed

## v. 1.0 - 04.09.2005

* new format of [labels](language/data-types/#labels)
* added [converter](editor/features.md#sa-mission-builder-source-code-converter) from the BW's SA Mission Builder syntax
* disassembler adds the model names and the text from `american.gxt` in a source file
* added new options
* fixed some bugs

## v. 0.8 - 20.08.2005

* added an ability to [associate](editor/options/general.md#file-association) `SCM` files with Sanny Builder
* disassembler adds an additional index to the file name if a file with the same name already exists (e.g, if `main.scm.txt` already exists, a new file will be `main.scm[0].txt`)
* more informative error messages
* added a check for duplicated labels
* fixed some bugs

## v. 0.7 - 10.08.2005

* added new options for text editing
* added an ability to work with multiple files simultaneously
* added a function to auto-complete an opcode with the `F1` button (beta)

## v. 0.6 - 04.08.2005

* disassembling support for GTA SA `SCM` format
* compilation of text sources into `main.scm` and `script.img`
* basic features for text editing
