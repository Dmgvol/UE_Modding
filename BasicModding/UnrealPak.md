# Creating Pak Files
To ensure your mod is loaded by the game, it needs to be in a `.pak` file, and if our game has IOStore enabled then 3 files; `.pak`, `.utoc`, and `.ucas`.

To get UnrealPak scripts, download it from [UnrealPak](https://github.com/Dmgvol/UE_Modding/raw/main/Tools/UnrealPak.zip)

## UnrealPak Folder
Create a folder that will contain the scripts, raw mod folder and output pak files, similar to this:

![](/Media/UnrealPak/unrealpak1.png)

_(Extract the provided UnrealPak zip file)_

## Mod Folder
For every mod, a mod folder with the exact folder structure is required.

```
Modname_P\GameName\Content\...
```

__Structure__<br>
- Replace the modname with your actual mod name.
- Ensure the folder ends with `_P`(important).
- Replace GameName with the binary name of your game.

Depending on the mod and which files it overrides, it will have the same folder hierarchy followed by the original game folder hierarchy, which is visible in FModel and UModel.

__Examples__<br>
A mod folder for a mod that replaces textures in Ghostrunner;<br>
```
\NewTex_P\Ghostrunner\Content\Visual\Characters\Hero_Swords\Mat\Tex
```

A mod folder for a mod that replaces a weapon model in Trepang2;<br> 
```
\newPistol_P\CPPFPS\Content\Weapon\Pistol
```

## Folder Contents
Once the folder structure is created, copy the necessary files, that **needs to be overwritten or added**.<br>
If you compiled the project content within UE editor - copy the files you want to be included in the mod.

In order to modify/overwrite the game's files with your custom files, you have to have the same folder structure and the same file names for the files, matching the original file paths/files.

__For example__<br>
In an example of a texture mod, the following folder stucture is used:<br>
```
\modname_P\Ghostrunner\Content\Visual\Characters\Hero_Swords\Mat\Tex\
```

The content of the following folder is:

![](/Media/UnrealPak/unrealpak2.png)

<hr>

## Using the Script
Simple, just drag the mod folder onto the `UnrealPak-With-compression.bat` to begin packaging the mod folder. <br>
Shortly after, a pak file with the same name will be created.

![](/Media/UnrealPak/unrealpak3.png)


## Adding mods to the Game
1. Navigate to the Paks folder of the game.

Usually it's following this pattern:

```
...\GameName\GameName\Content\Paks
```

For example, Ghostrunner game:<br>
```
...\Ghostrunner\Ghostrunner\Content\Paks
```


2. Copy the generated pak file into the game's Paks folder.
3. Rename the pak file to suit your mod purpose.
4. Make sure the name ends with `_P` **(IMPORTANT)**.<br>
For example: `myMod_P.pak`

