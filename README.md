

# UE4/5 Modding Guides 
A collection of UE4 (and 5) Modding Guides.</br>
The perfect place for anyone new, to learn UE modding and start creating mods <u><strong>today</strong></u>.</br>

</br></br>

## Before we begin...
These two tools every modder needs to have:<br>
- [Unreal Engine](https://www.unrealengine.com/en-US/)
- [FModel](https://fmodel.app/)

## Where to start?
If you're completely new, I would suggest picking on a simple mod idea/goal that will teach you the basics, for example; texture swap or just a value change within one of the files.
</br>
Just so you get the idea and the principles of UE4/5 modding and how it works.
<br><br>
<i>(If you're new and want to jump head-first into custom maps... then don't, that doesn't work like that).</i>

## The Basics
We will start with how we can browse and export game files.

- [Finding AES key (.pak encryption)](./TheBasics/AesKey.md)
- [Exporting - FModel](./TheBasics/ExportingFModel.md)
- [Exporting - UModel](./TheBasics/ExportingUModel.md)
- [Previewing Animations - UModel](./TheBasics/UModelAnimations.md)
- [Browsing UAssets - FModel](./TheBasics/UsingFModel.md)

## Basic Modding
Let's start changing values!</br>
This is essential to <b>ANY</b> value changing.</br>
- [Editing UAsset values - UAssetGUI](./BasicModding/UAssetGUI.md) (UE4)
- [Editing UAsset values - Hex](./BasicModding/HexEditing.md) _(Manual _hex, _in case_ UAssetGUI fails_)_
- [Editing UMaps - stove](./BasicModding/EditingUmaps.md) (UE4)
- [Disabling/Removing textures of objects](./BasicModding/DisablingObjects.md) (UE4)
- [Creating Pak Files - UnrealPak](./BasicModding/UnrealPak.md) (UE4)
- [Mod example - modifying Blueprint default values](./BasicModding/example1.md) (UE4)

## Intermediate Modding
Replacing Assets like textures, materials, static meshes, and SkeletalMeshes (such as characters). </br>

- [Creating a UE4/5 project](./IntermediateModding/CreatingProject.md)
- [Cooking/compiling in UE4 and UE5 with chunks](./IntermediateModding/CookingContent.md)
- [Replacing textures](./IntermediateModding/ChangingTextures.md)
- [Changing StaticMesh](./IntermediateModding/ChangingSM.md)
- [Changing SkeletalMesh](./IntermediateModding/ChangingSK.md)
- [Merging SkeletalMesh](./IntermediateModding/MergingSK.md)

## Advanced Modding
- [Replicating a Material for MaterialInstances](./AdvancedModding/ReplicatingMI.md)
- [Introduction to Blueprint/Logic Mods](./AdvancedModding/BpModsIntro.md)
- [Introduction to Blueprint Dummying/Replication](./AdvancedModding/BpReplication.md)

### Blueprint Modding
I won't be going into detail as that is where UnrealEngine4 experience comes in and this will cover the bare basics.</br>
<b>Note:</b> If you're new to UE4 - just tinker with it, everything is on YouTube.

- [Working with a mod loader - UML/UE4SS/DML/NML]() (Coming Soon)
- [ModActor structure and lifecycle]() (Coming Soon)
- [Creating a Widget]() (Coming Soon)
- [Hotkeys for BP mods]() (Coming Soon)
- [Config Variables - mod configurations]() (Coming Soon)
- [Custom Mod GameSaves]() (Coming Soon)
- [Mod Example - Custom logger (UserWidget)]() (Coming Soon)

## Expert
At this stage, you already know how to swap/modify any UAsset and do blueprints as your second language, YET looking for more advanced stuff to try.
- ["Injecting" custom Widgets into game menus using Blueprints]() (Coming Soon)
- [UHT for C++ Headers using UE4SS]() (Coming Soon)
- [Replicating C++ headers]() (Coming Soon)
- [Mod Example - Headers in practice, (game: Sprawl)]() (Coming Soon)

## Masterclass
I won't be covering any more complex witch-craft so if you've learned all of the above, then you can continue learning and evolving on your own.<br>


## Game Memory
Useful for creating speedrunning livesplit, custom randomizers and even trainers.
- [Finding CE pointers]()  (Coming Soon)
- [Finding offsets using UE4SS]() (Coming Soon)


##  Blender (3D Modelling)
- [Importing models (.glTF2 and .psk files)]() (Coming Soon)
- [Importing animations (.psa files)]() (Coming Soon)

## Substance Painter (Texturing)
- [Importing textures to Substance]() (Coming Soon)
- [Exporting to UE4 - Albedo, Normal and ORM]() (Coming Soon)


---

# Useful Links/Tools

### Browse and Edit UAssets
- [FModel](https://fmodel.app/)
- [UModel](https://www.gildor.org/en/projects/umodel)
- [UAssetGUI](https://github.com/atenfyr/UAssetGUI)
- [stove](https://github.com/bananaturtlesandwich/stove)

### UE
- [Epic Launcher](https://www.epicgames.com/store/en-US/)
- [Universal Unreal Engine 4 Unlocker (UUU)](https://framedsc.github.io/GeneralGuides/universal_ue4_consoleunlocker.htm)
- [UnrealPak](https://github.com/Dmgvol/UE4_Modding/raw/master/Tools/UnrealPak.zip)
- [UE4SS - UE4/5 Scripting System](https://github.com/UE4SS-RE/RE-UE4SS)

### 3D Modeling
- [Blender](https://www.blender.org/) or [Steam's version](https://store.steampowered.com/app/365670/Blender/)
- [Blender 4 Psk plugin](https://github.com/DarklightGames/io_scene_psk_psa) - written by **DarklightGames**
- [Blender 3 Psk plugin](https://github.com/Befzz/blender3d_import_psk_psa) - written by **Befzz**

### Reverse Engineering
- [Cheat Manager](https://www.cheatengine.org/) - Written by **Dark Byte**
- [x64dbg](https://x64dbg.com/) - Written by **mrexodia**
- [BinaryNinja](https://binary.ninja/)
- [Hex Editor Neo](https://freehexeditorneo.com/)

### The rest
- [All available/known UE modding tools](https://github.com/Buckminsterfullerene02/UE-Modding-Tools) written by **Buckminsterfullerene**.

### Discords
[UE Modding](https://discord.gg/unreal-engine-modding-876613187204685934)

---

# Credits
- [FatihG_](https://www.youtube.com/c/fatihG/) for teaching me how to mod.
- [atenfyr](https://github.com/atenfyr/)(adolescent in Discord) for [UAssetGUI](https://github.com/atenfyr/UAssetGUI) and [UAssetAPI](https://github.com/atenfyr/UAssetAPI).
- [RussellJerome](https://github.com/RussellJerome) for creating the [ModLoader](https://github.com/RussellJerome/UnrealModLoader).


### Special Thanks:
- LongerWarrior, JanisSG, Jan and Animayyo for their amazing support throughout the whole journey of GR modding.
- Mythical
- Narknon
- Cranch
- Buckminsterfullerene02
- Atenfyer/Adolescent
- Spuds
- Truman 
- Lisht/Kein
- KunoDemetries

---

