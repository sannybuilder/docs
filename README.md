# Introduction

**Sanny Builder** is a fast and powerful tool designed for the GTA 3D game series \(GTA3, VC, SA, LCS; partially VCS\).

It includes a disassembler, permitting the end-user to transform the game scripts into text. The compiler feature offers a convenient editor with a large number of useful functions such as [syntax highlighting](editor/options/syntax-highlighting.md), error checking, advanced search tools, [player coordinates reading](features.md#player-coordinates-management), fast movement through code and much more.

Sanny offers an advanced code syntax which is similar to existing programming languages. This syntax includes changeable [classes](coding/classes.md), [keywords ](coding/keywords.md)and high-level statements. We recommend you continue reading and fully explore the documentation to learn more about SB and its capabilities. We provide a wealth of information that will help you get started in mission coding.

## **Installation and Updates**

Run the installer and follow its instructions. During installation you could optionally select the game directory you plan to work with, associate files with the `.SCM` extension with Sanny Builder and install the [CLEO library](https://cleo.li).  You can always update these settings in the program options.

To uninstall the program, run the file `unins000.exe` located in its root folder.

Latest versions and updates are always available at [sannybuilder.com](https://sannybuilder.com/)

## Command line usage

`\sa` - run as SA editor \(default\)  
`\vc` - run as VC editor  
`\gta3` - run as GTA3 editor  
`\lcs` - run as LCS editor  
`\vcs` - run as VCS editor  
`\sa_mobile` - run as SA Mobile editor.

{% hint style="info" %}
You can also change the current [edit mode](edit-modes/) in run-time.
{% endhint %}

`\debug` - enables the [debug options](console.md#running-with-the-debug-parameter)  
  
`\compile input_file_path [output_file_path]` - compiles the file and exits

```text
sanny.exe \compile C:\myscm.txt C:\myscm.scm
```

{% hint style="info" %}
The `output_file_path` __parameter is optional. If there is no path specified for an output file, the compiler uses the [format rules](editor/options/formats.md#file-name-format). Note that the source file must have no errors. If there are errors found during compilation, they will be logged in the file `compile.log`. When compilation ends, the program shuts down.
{% endhint %}

`\nosplash` - runs Sanny Builder without the splash screen

## Contacts

[sannybuilder.com](https://sannybuilder.com/)  
[Sanny Builder @ Github](https://github.com/sannybuilder/dev/issues)  
[Sanny Builder @ Twitter](https://twitter.com/SannyBuilderDev)  
[Sanny Builder @ Facebook](https://facebook.com/SannyBuilder)  
[Sanny Builder @ GTAForums.com](http://gtaforums.com/index.php?showtopic=211077)

For any questions e-mail me at [mail@sannybuilder.com](mailto:mail@sannybuilder.com) or raise a ticket on [Github](https://github.com/sannybuilder/dev/issues).

Use responsibly at your own risk. In Backup We Trust.

© 2005-2020 Seemann

