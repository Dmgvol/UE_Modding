# Working with a ModLoader
A custom blueprint mod loader allows modder to load custom blueprint logic into the level.

> [!NOTE]  
> Each mod loader has its own set of rules and requirements, so make sure you read the readme of the used mod loader.

## List of common BP modloaders
The most popular modloaders are:
- [UE4SS](https://github.com/UE4SS-RE/RE-UE4SS) (UE4/UE5)
- [UML](https://github.com/RussellJerome/UnrealModLoader) by [Russell Jerome](https://github.com/RussellJerome) (UE4 only)
- - Dmgvol's fork: [UML v2.2.1a](https://github.com/Dmgvol/UnrealModLoader) (UE4 only)

Game specific modloaders:
- DML (DmgModLoader)
- - For [Ghostrunner 2](https://www.nexusmods.com/ghostrunner2/mods/5)
- - For [Rooftops&Alleys](https://www.nexusmods.com/rooftopsandalleystheparkourgame/mods/16)

- NML (Narknon ModLoader)
- - For [AtomicHeart](https://www.nexusmods.com/atomicheart/mods/11)
- - For [Hogwarts Legacy](https://www.nexusmods.com/hogwartslegacy/mods/56)

_(It's such a few of them, there are more mod loaders)_


## UML/UE4SS/DML
These three mod-loaders use the same pattern, where the mod blueprint is named ModActor within its corresponding folder in the Mods folder.

The mod loader spawns a single instance of that blueprint into every persistent level.

UML and UE4SS are done via DLL injections, while DML is a pak-version that doesn't require any third-party software to function.

### UE Setup
![](/Media/BpIntro/3.png)

- BP mods go into `/Mods` followed by the mod name, for example: `/Mods/MyMod/`.
- The mod blueprint has to be named `ModActor`.

For UML and UE4SS, 2 additional custom methods have to be persistent within the graph editor; `PreBeginPlay` and `PostBeginPlay`.<br>
But the default `BeginPlay` also works, which is fired once when the actor is spawned.

![](/Media/ModLoaders/UmlLayout.png)

> [!NOTE]
> For a detailed explanation, watch this video: [UML ModActor tutorial](https://www.youtube.com/watch?v=fB3yT85XhVA)


> [!IMPORTANT]  
> The packed/compiled pak file name must match with the mod folder within the editor.


## NML
Narknon's Modloader uses a different approach for loading mods, where it loads custom levels by name.<br>
Each custom mod level has "level bp" where the main logic is executed for the corresponding mod.

## UE Setup
The setup for NML or any other mod loader with map names as "entry", level assets must be created within a specific folder like `CustomContent`.

![](/Media/ModLoaders/NmlLayout.png)

The level name is the name of your mod, which will be entered into the mod loader in-game.

> [!IMPORTANT]  
> The name of the mod is the name of the level asset.


