# Migration to new SBL modes in SB4

When converting code from old legacy modes based on INI with custom parameter order, keep in mind the following conventions used in new SBL modes (GTA III SBL, GTA VC SBL, GTA SA SBL):

* all params follow their original order, where output variables go after input arguments (`create_player 0 0 0 0 store_to $player1`)
  * SB4 provides special syntax, where outputs in an assignment expression can be listed on the left-hand side, e.g. `$player1 = create_player 0 0 0 0`)
* command name can be used instead of opcode (`shake_cam 100`)
* `Actor` is called `Char`
* `Marker` is called `Blip`
* `Model` class no longer exists, its methods can be found in static `Streaming` class
* `$PLAYER_CHAR` replaced with `$player1`
* `$PLAYER_ACTOR` replaced with `$scplayer`
* `angle` is called `heading`
* `thread` is called `script`
