# Disabling/Removing Objects
It's an easy trick I've learned which I think can come in handy for some modders. <br>
If you want to remove objects such as textures or even blueprints, you can literally erase uasset content, and pack an empty file back into pak file.

It works on models, VFX, textures, sounds, and even blueprints.

## Locating Game Files
For this example, I will be removing one of the enemies in Ghostrunner, the spiders.

First, I will locate the character blueprint using FModel.
<br>
Which in this case is `/Content/ArtificialIntelligence/Characters/BP_EnemySpider`.

![](/Media/RemovingObjects/spider1.png)

## Create Mod Folder
Create a mod folder with the same folder structure as it is found in FModel.

Every mod folder follows the pattern:<br>
`ModName_P/<Game>/Content/...`<br>
And for this example that will be:
`NoSpiders_P/Ghostrunner/Content/...` followed the full path.

Which is:<br>
`/NoSpiders_P/Ghostrunner/Content/ArtificialIntelligence/Characters`


![](/Media/RemovingObjects/spider3.png)

## Empty UAssets
1. Create 2 text files, and rename them to match the object/asset we want to remove.
2. Change the extension from `.txt` to `.uasset` and `.uexp`.

![](/Media/RemovingObjects/spider4.png)

## Pack and Test
Package the mod folder using UnrealPak (Guide: [How to Pak](/BasicModding/UnrealPak.md)).


This mod is available to download here: [No More Spiders for GR1](https://www.nexusmods.com/ghostrunner/mods/28)