# Edit Modes

Sanny Builder supports many games and platforms and so there is a predefined configuration for each supported game called an **edit mode**. 

Edit modes supply Sanny Builder with the following information:

* a target game
* paths to files with the game data
* paths to files with supporting information \([labels](customlabels.ini.md), [variables](./#variables), [constants](./#constants), etc\)

By default Sanny Builder reads the modes configuration from the file `<SB>\data\modes.xml`. This path can be customized via the `-x` CLI [option](../cli.md#x).

The file `modes.xml` is open for modification and extension, and users can create their own modes by changing it.

## File Format

`modes.xml` is a file in the XML format and can be changed in any text editor. It defines the available modes.

The root node is `<modes>` and it has no attributes. The file can only have one root node. 

Each edit mode is a child node of `<modes>` beginning with the opening tag `<mode>` and ending with the closing tag `</mode>`. The `<mode>` element has both mandatory and optional attributes as outlined below. The content of the `<mode>` is a set of specific tags \(properties\) defining paths to directories or files.

### Mode Attributes

#### id

`id` is a required and unique identifier of the mode. Sanny Builder uses the `id` to save some settings for this mode, e.g. a game directory.

A valid value for the `id` attribute is a unique series of characters not used for any other mode's id. 

#### extends

A mode can extend another mode \(the parent\) to reduce the number of duplicated properties. It is helpful for different versions of a game where most of the configuration is the same except for a few properties. The parent can also extend another mode. 

When a property is missing Sanny Builder recursively traverses all parent modes trying to find the property.

A valid value for the `extends` attribute is the `id` of another mode defined in the same file.

#### title

`title` defines the mode's displayed name. Due to the interface constraints avoid long names and keep it within the limit of 24 characters.

#### game

The `game` attribute defines a target game for the mode. There are 6 known values:

* `gta3`
* `vc`
* `sa`
* `lcs`
* `vcs`
* `sa_mobile`

Each game has an unique script format and the scripts compiled for one game are not compatible with scripts for another game.

Sanny Builder displays a game icon in front of the edit mode name so you know the target game. 

Before disassembling or compiling a script, make sure that the correct edit mode is active. Even if the script is compiled without errors, the game would crash trying to read a script in different format. 

{% hint style="info" %}
A compiled script file may store an information which game it is made for. When you open such a script, Sanny Builder prompts you to change the mode to the correct one. Ignoring this prompt may cause a crash of the disassembler, because the script format is unexpected for it.
{% endhint %}

#### type

One mode for each target game must be a default one. It means Sanny Builder uses this mode when run with the `--game` CLI [option](../cli.md#game).

The valid value for the `type` is `default.` Omit this attribute for non-default modes.

### Mode Parameters

#### arrays 

path to [`CustomArrays.ini`](../coding/arrays.md)

#### classes 

path to[`classes.db`](../coding/classes.md)

#### constants

path to[`constants.txt`](../coding/constants.md)

#### data 

path to the mode directory

#### ide 

path to either an `.ide` or `.dat` file:  
`.ide` files contain game [model names](../coding/data-types.md#model-names) and characteristics  
`.dat` files contain paths to other `.ide` files

`ide` element may have an optional `base` attribute to specify a folder that is used to resolve relative paths in the `.dat` file.

```text
<ide base="@game:\">default.dat</ide>
```

Without `base` all relative paths are resolved starting from the location of the `.dat` file.

A mode may have multiple `<ide>` elements.

#### keywords 

path to a list of [keywords](../coding/keywords.md)

#### labels 

path to [`CustomLabels.ini`](customlabels.ini.md)

#### missions 

path to[`missions.txt`](../features.md#custom-mission-titles)

#### opcodes 

path to a list of [opcodes](opcodes-list-scm.ini.md)

#### templates 

path to an [exclusive templates](code-templates.md) file

#### text 

path to a `.gxt` file

`<text>` has one required attribute: `format`. The supported values are:

`gta3`: `.gxt` has one table, plain keys, ANSI encoding  
`vc`: `.gxt` has multiple tables, plain keys, ANSI encoding  
`sa`: `.gxt` has multiple tables, hashed keys, ANSI encoding  
`sa_mobile`: `.gxt` has multiple tables, hashed keys, UTF-16 encoding

#### variables

path to [`CustomVariables.ini`](../coding/variables.md)

#### examples

path to [`opcodes.txt`](../opcode-search-tool.md)

### Built-in Variables

Sanny provides a few variables that can be used in parameters and attributes \(if applicable\).

`@game:` - path to the [game directory](../options/general.md#game-directory) configured in the options  
`@sb:` - path to the Sanny Builder directory \(where `sanny.exe` is located\)

Both paths do not include the trailing slash.

## Available Modes

Sanny Builder offers many different modes and their number may vary from version to version:

| Title | Naming schema  | Parameters order | Game |
| :--- | :--- | :--- | :--- |
| GTA III | community | custom | all versions of GTA III |
| GTA VC | community | custom | all versions of Vice City |
| GTA SA v1.0 | community | custom | SA v1.0  |
| GTA SA v2.0 | community | custom | SA v2.0 |
| GTA SA \(v1.0 - SCR\) | Rockstar | original | SA v1.0 |
| GTA LCS | Rockstar | original | all versions of Liberty City Stories |
| GTA VCS \(PSP\) | Rockstar | original | VCS for PSP |
| GTA VCS \(PS2\) | Rockstar | original | VCS for PS2 |
| SA Mobile | community | custom | SA Android and iOS versions |

The naming schema defines the way of describing the opcodes. The c_ommunity_ schema has the names randomly guessed over the years, such as `actor` or `thread`. The _Rockstar_ schema has the original taxonomy used by the game developers \(e.g. `char` or `script`\) that is consistent with the game's inner structures.  

The parameters order defines the way of arranging the opcode parameters. In the _custom_ order the parameter with the higher index may go earlier in the script. This is applicable to community opcode descriptions. The _original_ order have all parameters arranged from the smallest index to the largest index. This goes with the Rockstar schema to make scripts look like they are meant to be by the developers.

## Selecting a mode

To change the mode, click at the right bottom corner of the Sanny Builder's main window. A list of the available modes will appear. As you click the mode name Sanny Builder makes all necessary adjustments and you may continue working immediately.

![](../.gitbook/assets/edit_modes.png)

To select the mode using CLI run Sanny Builder with the `--mode` [option](../cli.md#mode). To select a default mode for the game use the `--game` [option](../cli.md#game).

Running Sanny Builder with the `-x` [option](../cli.md#x) allows loading the modes configuration from a file different from the default `modes.xml`. If Sanny Builder is already running, it reloads the configuration and updates the list of modes.

