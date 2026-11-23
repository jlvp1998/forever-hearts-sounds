# Forever Hearts sounds

The sounds for the Forever Hearts MUD. OpenMud downloads them when you type `spupdate` while connected to Forever Hearts. After that it only downloads what changed.

## For players

1. Connect to Forever Hearts with OpenMud.
2. Type `spupdate` once. The sounds go into `Documents\OpenMud\forever hearts`.
3. That's it. The game plays footsteps, doors, fights, pickups, shops, crafting and the story's moments through your soundpack.

Commands, typed in OpenMud while connected to Forever Hearts:

- `sphelp`: list these commands.
- `spvol` followed by 0 to 100: master volume.
- `ambvol` followed by 0 to 100: background volume.
- `spmute`: all sounds off or on.
- `spcheck`: see if there's an update.
- `spupdate`: get the newest sounds.

## What's in here

`sounds/` holds every sound file. These are the sounds from the original Forever Hearts audio game, with the same folder layout, so a sound's name is just its path. For example, `footstep/wood/` means "a random file from that folder" and `level_up.ogg` means that file.

## How the game asks for sounds

When OpenMud sees the MUD's welcome line, it sends `soundpack on`. From then on the MUD sends that client hidden lines, never shown to players. Each line ends with a volume from 0 to 100:

```
#$#fh hello
#$#fh play footstep/wood/ 50          one sound. A name ending in / plays a random file from that folder.
#$#fh amb background/forest.ogg 35    the looping room background. "none" stops it.
#$#fh loop battle music/attack.ogg 40 an extra loop with an id, like boss battle music
#$#fh stoploop battle
#$#fh ingame                          a character entered the world (the menu music stops)
#$#fh menu                            back at the character list (the menu music plays)
```

## Adding or changing sounds

Add, replace or remove files under `sounds/` and push. Everyone gets the change the next time they type `spupdate`. OpenMud also checks quietly when you connect, and tells you when an update is ready.

To use a new sound, the MUD has to send its name. Sound names are set in the MUD's `Mud/Engine/Sounds.cs` and the other engine files. Room backgrounds and footstep surfaces for the new areas are set in `Mud/data/world.json`, with `"ambience"` and `"floor"`.
