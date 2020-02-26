# Version History

## v. 3.3.3 - 20.10.2019

* fixed [bug](http://bugs.sannybuilder.com/view.php?id=52) causing incorrect external scripts compilation

## v. 3.3.2 - 19.10.2019

* fixed bugs [\#0036](http://bugs.sannybuilder.com/view.php?id=36), [\#0050](http://bugs.sannybuilder.com/view.php?id=50)
* fixed opcode `059C` in Vice City mode

## v. 3.3.1 - 14.09.2019

* fixed bug [\#0048](http://bugs.sannybuilder.com/view.php?id=48)
* included `constants.txt` missing in GTA SA mode

## v. 3.3.0 - 08.09.2019

* added compiler support for Liberty City Stories SCM format
* added aliases for the [timer variables](coding/variables.md#timer-variables): `TIMERA` and `TIMERB`
* changed the `Ranges check` option to apply to the global variables

## v. 3.2.4 - 04.08.2019

* fixed bugs [\#0031](http://bugs.sannybuilder.com/view.php?id=31), [\#0032](http://bugs.sannybuilder.com/view.php?id=32), [\#0033](http://bugs.sannybuilder.com/view.php?id=33), [\#0040](http://bugs.sannybuilder.com/view.php?id=40), [\#0044](http://bugs.sannybuilder.com/view.php?id=44)
* fixed regression defect when a CHM help file can not open
* updated opcode definitions for GTA 3 and Vice City
* added IDE support for CLEO 2.0 for III and VC

## v. 3.2.3 - 07.07.2019

* improved support of the version of GTA San Andreas for Wi﻿nStore, Xbox 360, and P﻿S3
* fixed an issue with opcodes `09A4` and `0A18` not being properly decompiled in SA\_Mobile mode

## v. 3.2.2 - 05.07.2014

* added translation into Korean language \(thanks to MINE\)
* improved [HEX..END](coding/hex..end.md) construct processing
* fixed bug [\#0000028](http://bugs.sannybuilder.com/view.php?id=28)

## v. 3.2.1 - 04.05.2014

* added translation into Indonesian language \(thanks to IMasterFX\)
* CLEO for GTA III and CLEO for Vice City updated \(thanks to Silent\)
* fixed bugs [\#0000026](http://bugs.sannybuilder.com/view.php?id=26), [\#0000027](http://bugs.sannybuilder.com/view.php?id=27)

## v. 3.2.0 - 22.03.2014

* adding custom edit modes by editing the `games.xml` file is now possible
* new edit mode - `GTA SA SCR`
* variables can be quickly declared using a type name prefix
* CLEO updated to the version 4.3.16
* added the InstaSearch feature \(formerly 'jump to label' function\)
* mission names can be changed by editing appropriate `missions.txt` files
* improved association of the script file extensions with Sanny Builder
* Sanny Builder only checks if the game directory path is not empty, no checks for specific files \(such as an `.exe`\)
* minor improvements in the SB updating feature
* changed the Sanny Builder icon and the menu icons
* fixed bug [\#0000024](http://bugs.sannybuilder.com/view.php?id=24)

## v. 3.1.4 - 22.02.2014

* CLEO updated to the version 4.3.14
* fixed minor interface glitches for hi-res displays
* updated German, Polish, Chinese, Ukrainian translations

## v. 3.1.3 - 22.12.2013

* added support for iOS and Android versions of GTA San Andreas
* a looking depth value is now used when making a list of constants
* updated Chinese and German translations

## v. 3.1.2 - 06.10.2013

* added Czech translation
* added options to associate file extensions `.cs` and `.cm` with Sanny Builder
* fixed bugs [\#0000011](http://bugs.sannybuilder.com/view.php?id=11), [\#0000020](http://bugs.sannybuilder.com/view.php?id=20)

## v. 3.1.1 - 22.09.2013

* added a new directive `$OPCODE` to register a new opcode in the script
* corrected behavior of the directive `$INCLUDE` while scanning directories for the file
* fixed bugs [\#0000005](http://bugs.sannybuilder.com/view.php?id=5), [\#0000019](http://bugs.sannybuilder.com/view.php?id=19)

## v. 3.1.0 - 14.09.2013

* `VCSCM.ini` is updated to include opcodes for the GTA VC mobile version and unsupported opcodes
* when the option `Add extra info to SCM` is enabled, Sanny Builder remembers the game a script is compiled for, to use the proper edit mode when decompiling
* when the option `Add extra info to SCM` is enabled, Sanny Builder adds a source code into a script file \(only when the directive `$EXTERNAL` or `$CLEO` is present\)
* added a new directive `$NOSOURCE` to prohibit including a source code into a compiled script
* some hotkeys are now customizable in the options
* added a feature to check automatically if an update exists at the program startup
* [directives ](coding/directives.md)`$VERSION` and `$VERSION_RESTORE` are deprecated
* updated Spanish and Chinese translations
* The Coords manager is now able to change the player's angle in GTA VC
* The Sanny Builder installation now includes the [SCRLog CLEO plugin](http://www.gtagarage.com/mods/show.php?id=23846) by LINK/2012 \(can be found in the `tools` folder\)
* fixed bugs [\#0000010](http://bugs.sannybuilder.com/view.php?id=10), [\#0000014](http://bugs.sannybuilder.com/view.php?id=14), [\#0000015](http://bugs.sannybuilder.com/view.php?id=15), [\#0000016](http://bugs.sannybuilder.com/view.php?id=16)

## v. 3.09 - 28.07.2013

* Sanny Builder is licensed under the Sanny Builder Freeware/Donationware License Agreement
* added a feature to report found bugs via [the official bug tracker](http://bugs.sannybuilder.com/)
* added a feature to check if an update is available
* The Coords manager is upgraded to work with all known versions of GTA3, VC and SA \(thanks to Silent\)
* added an updated Chinese translation
* fixed bugs [\#0000002](http://bugs.sannybuilder.com/view.php?id=2), [\#0000003](http://bugs.sannybuilder.com/view.php?id=3), [\#0000004](http://bugs.sannybuilder.com/view.php?id=4), [\#0000006](http://bugs.sannybuilder.com/view.php?id=6), [\#0000009](http://bugs.sannybuilder.com/view.php?id=9)
* minor design changes

## v. 3.08 - 05.07.2013

* added [Silent's ASI Loader](http://www.gtagarage.com/mods/show.php?id=21709) v1.1 as a default ASI loader for CLEO 3 and CLEO 4
* added Chinese translation
* added classes `File` and `Audiostream` for backward compatibility with CLEO 4 by Alien\*
* the compiler now accepts a literal string as a parameter in [a class property](coding/classes.md)\*\*
* the compiler is no more allowed to compile a string like `text1"text2"` or `text1'text2'` \(without a leading quotation mark\)
* the compiler is allowed to compile the comment characters within a string \(`"{text1}text2"`\)
* the semicolon \(`;`\) can not be used to comment out a line of the code
* changed syntax of the [\debug](./#command-line-usage) parameter
* added flag icons for the available languages in the options
* fixed some issues in VCS decompiling

{% hint style="info" %}
\* `File.Open`, `Audiostream.Load`, `Audiostream.Load3D` were methods in CLEO 4. Now they are properties. It means, if you get an error when compiling old sources with these commands, change their syntax to:  
 `var = File.Open(file_name, mode)  
var = Audiostream.Load(file_name)  
var = Audiostream.Load3D(file_name)`
{% endhint %}

{% hint style="info" %}
\*\* There is a limit on using space characters in such parameter.
{% endhint %}

## v. 3.06 - 17.06.2013

* added new operators `++` and `--`
* added support for block comments `/*   */`
* SASCM.INI is updated with help of the [GTAG Database](https://gtagmodding.com/opcode-database/)
* properties `Actor.Armour` and `Actor.Car` are replaced with their correct versions `Actor.AddArmour` and `Actor.MissionCar`
* added new property `Actor.CurrentCar` for the opcode `03C0` in the SA and VC classes.
* added new hotkeys `Ctrl+Num+` and `Ctrl+Num-` to quickly change the text size
* Sanny Builder now remembers a number of closed files for the option Load all closed files
* fixed bug when the compiler failed to compile numerous [HEX..END](coding/hex..end.md) constructs
* fixed bug of version 3.05 when the program hung on startup trying to open a file passed as a parameter

## v. 3.05 - 05.06.2013

* added new translations for the following languages: Finnish, Polish, Hungarian, Turkish, Ukrainian
* the CLEO library updated to version 4.1.1.30f \(CLEO 4 by Alien\)
* added possibility to install CLEO for GTA III and Vice City \(made by Alien\)
* the opcode files \(\*\*SCM.ini, opcodes.txt\) replaced with the ones from the CLEO 4 library installation
* new [command line parameter](./#command-line-usage) `\nosplash`

## v. 3.04 - 17.08.2008

*  the editor got abilities to convert hexadecimal numbers to decimal ones and vice versa \(`Ctrl+H`\), and convert the model names to their IDs \(`Ctrl+Alt+H`\)
*  removed the complaining message about the script.img being used by the game when compiling a CLEO script
*  the compiling report displays size of a CLEO script \(as Largest script\)
*  fixed bug when compiling an array with constant numeric indexes
*  the installer no longer required the system administrator rights

## v. 3.03 - 17.11.2007

* the previous version of CLEO had a bug
* minor changes \(the toolbar position wasn't saved\)

## v. 3.02 - 16.11.2007

*  new version of the CLEO library
*  main toolbar is movable
*  `F7` while compiling SCM with no header \(with `$E`, `$CLEO` directives\) does not make a copy of the output file
*  while compiling a source file with directive `$CLEO` by pressing `F6`, the output file is created at the same directory; if by pressing `F7` a copy of the output is created at the CLEO directory \(like with common SCM files\)
*  new translations: Italian, Portuguese

## v. 3.01- 06.08.2007

* bug-fixes update

## v. 3.00 - 04.08.2007

* the CLEO 3 library is integrated into Sanny Builder
* VCS SCM format support \(decompiling only\)
* [constants ](coding/constants.md)support
* new directives `$INCLUDE`,`$EXTERNAL`,`$CLEO`
* writing of the additional info in the end of the `main.scm`
* custom arrays support
* possibility to decompile the files having no header
* ability to create an external script named `AAA`
* new command line parameter `\compile`
* possibility to use the floating-point values as a counter value in `FOR..END` loop
* the commands `WriteMem` and `ReadMem` are not supported anymore
* possibility to use the regular expressions when searching
* possibility to save a source file in the RTF or HTML formats
* ability to skip the splashes at SA startup
* new key combo `Ctrl+Enter`
* updated `SASCM.INI`

## v. 2.99e - 01.01.2007

* fixed bug when parts of the code within the `HEX..END` construction disappeared in the debug\_mode decompiling
* a [HEX..END](coding/hex..end.md) statement could accept the `aDMA` type and strings
* a `FOR` statement could accept the model identifiers as the counter values

## v. 2.99d - 03.12.2006

* Memory Hacker became a separate tool. Now downloadable at: [http://sannybuilder.com/downloads](http://sannybuilder.com/downloads)
*  fixed a decompiler bug

## v. 2.99c - 30.11.2006

* added the Memory Hacker plug-in
* possibility to decompile the `main.scm` of Liberty City Stories
* support for numbers as indexes of global [arrays](coding/arrays.md)
* global variables are decompiled with the type aDMA \(`&`\) if are not dividable by 4
* at compilation the default values for the segments are used when the file header is not present
* possibility to Drag&Drop a file into the editor to open it
* new preprocessor [directives](coding/directives.md): `{$VERSION}`, `{$VERSION_RESTORE}`

{% hint style="info" %}
If you get a compiler error message like `Unknown directive xxxx` when compiling the sources from v2.99, replace the line `{$VERSION xxxx}` to any place after the header, for instance before the comment `//-------------MAIN---------------`
{% endhint %}

## v. 2.99 - 27.09.2006

* added new commands `WriteMem` and `ReadMem`
* support for hexadecimal numbers
* `HEX..END` statement can accept labels and global variables
* full support for the `ADMA`datatype
* opportunity to give custom names to labels
* opportunity to choose a different case for custom names and strings \(`Options->Format`\)
* added the console in order to switch the special options of SB
* decompiler supports the GXT files of GTA III & GTA VC
* added special symbol constants in the long strings
* information about an INI file \(version, author, date\)
* classes support an original order of the parameters \(like in `SASCM.INI` from PLPynton\). In order to support such order there should be a line {`$VERSION x.0.xxxx`}, see comments in the INI about this
* added option to confirm exit program
* quick switching of the Edit Mode
* converting of the selected piece of code
* opportunity to pass the current file name to the external tool
* corrected some mistakes in the configuration files
* removed auto-casting of an integer number to a float one when the variable was declared as `Float`. Now the compiler chooses an opcode depending on the number type only \(in math expressions without opcodes\)
* reading/writing of the player's z\_angle in Coord Manager; quick insertion of this one in a script by pressing `Ctrl+Shift+E` \(for SA\)

{% hint style="info" %}
The following opcodes were changed in `SASCM.INI`: `0181`, `00c3`, `00c4` in order to support the commands `WriteMem` and `ReadMem`. In original files these opcodes are not used and the games do not support them so there should be no problem.
{% endhint %}

{% hint style="info" %}
The class member `Car.SetSpeedInstantly` was named incorrectly \(with wrong opcode\) in the file `classes.db` for SA. If you get the error message about this method at compilation, rename it in `Actor.DrivingPlane` manually. We apologize.
{% endhint %}

## v. 2.98 - 04.08.2006

* Sanny Builder became multilingual
* added menu for external applications
* the special version of Opcode Search Tool is built in SB Details in a file `OST Readme.txt`
* checking of the math expressions while decompiling when the option `Write opcodes` is disabled \(to sure that all the opcodes were used correctly\)
* an opportunity to choose an IMG-file manually if the last one is not found in a folder with the SCM file \(the option "`Manual IMG opening`"\)
* an opportunity to add new macros directly from the editor; added macros descriptions
* the list of models can be sorted alphabetically/by value \(`Alt+S` when the list is active\)
* minor corrections and changes

## v. 2.97 - 11.06.2006

* new data type: `&` that denotes direct byte address \([ADMA](coding/data-types.md)\).
* minor updates

## v. 2.96 - 01.04.2006

* improved the option jump to label
* added an opportunity to call macros list of macros
* added an option of replacement of mission numbers with their names
* fixed some bugs

## v. 2.9f - 18.02.2006

* model names is added to the `DEFINE OBJECT` list by the compiler \(this list may be not presented in the source file at all\)
* block comments support `{}`
* macrorecording
* minor changes

## v. 2.9 - 15.12.2005

* additional commands \(see by item 2.5\) are added
* operator `IN` is added
* construction `IF..THEN..ELSE..END` is added
* loops `WHILE`, `REPEAT` are added
* the opportunity of use of the enclosed loops is added.
* function `alloc()` is added, allowing to specify for a variable the specific address in memory
* new comment style: `//`
* positions of markers and the cursor are remembered for the closed files

## v. 2.6 - 05.11.2005

* full support of formats of Vice City and GTA3 is added
* the opportunity of initialization of variables and files as members of a class is added
* display of the list of variables and labels is added
* support of loops \(`FOR` operator\) is added
* minor changes:
  * missions can be started on their name \(`start_mission MYMISSION`\), where `MYMISSION` is a name of a starting label \(`DEFINE MISSION 100 at @MYMISSION`\)
  * the list of imported models \(defined objects\) on `Ctrl+Space` is accessible
  * new operator `<>`
  * if the disassembler can't find the `script.img`, it uses the one from the game folder
  * for arrays the type handle is added
  * an opportunity of switching-off of the warning of use IMG by game

## v. 2.5 - 10.10.2005

* added "properties" support
* added macroes support
* added construction [VAR...END](coding/variables.md#var-end-construct) for variables management
* all math commands can be used without opcodes `0004..008B`
* new operators `<` and `<=`
* added a capability that the compiler itself set necessary value for `IF` command
* added "extended" parameters support
* added models list showing
* minor changes and fixes

## v. 2.0 - 18.09.2005

* added classes support
* added keywords support
* added a capability to write some math commands without opcodes \(now such capability exists for opcodes `0004`, `0005`, `0006`, `0007`, `0038`, `0039`, `0042`, `0043`\)
* for opcode `00D6` the default parameter is `0` \(`if` = `if 0`\)
* added the option of a choice of various kinds of labels \(`Formats->Labels Format`\)
* added keywords `True` and `False` which designate `1` and `0` accordingly
* added construction [HEX...END](coding/hex..end.md) for writing hexadecimal values directly in SCM

## v. 1.1 - 07.09.2005

* added coords manager
* some bugs fixed

## v. 1.0 - 04.09.2005

* new format of labels
* added converter from BW's SA Mission Builder syntax
* at decompiling names of models and texts from `american.gxt` are added in source
* added new options
* some bugs fixed

## v. 0.8 - 20.08.2005

* added the capability to associate SCM files with the program
* after decompiling the output file get an addition index if a file with same name already exists. \(e.g, if `main.scm.txt` already exists, a new file will be `main.scm[0].txt`\)
* error messages became more informative
* added check of label redeclaring
* some bugs fixed

## **v. 0.7 - 10.08.2005**

* added new options for the text editing
* added a capability to work with several files simultaneously
* added a function to auto-complete a line with the F1 button \(beta\)

## **v. 0.6 - 04.08.2005**

* full decompiling of GTA SA SCM files
* compiling of the source files into a SA SCM file and an IMG file
* some options for the text editing

