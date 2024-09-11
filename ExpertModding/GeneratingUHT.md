# UHT Headers using UE4SS
UHT (Unreal Header Tool) processes C++ headers, generating necessary code for Unreal Engine's reflection system. When modding, dumping UHT headers provides the essential class and structure definitions needed to create blueprint mods.

> [!NOTE]  
> Not all logic is stored in blueprint, majority of the logic is in C++ which we can dump the header files for.
> We won't be able to see the actual code but it gives us classes, variables, enums, object types, methods, delegates and etc.

We will be using the [UE4SS](https://github.com/UE4SS-RE/RE-UE4SS) tool for this.
Additional guide: [UHT header dump guide by UE4SS](https://docs.ue4ss.com/dev/feature-overview/dumpers.html#unreal-header-tool-uht-dumper).

## Using UE4SS
> [!IMPORTANT]
> Make sure you read UE4SS repo, as different games will require different configuration/settings/builds to function. 

1. Download UE4SS and extract its content into the binary exe folder.<br>
For example: `...\Sprawl\Sprawl\Binaries\Win64`.
2. Open the `UE4SS-settings.ini` file.
3. Set the game's UE version under EngineVersionOverride section.

![](/Media/UHT/1.png)

4. Make sure you have `ConsoleEnabled`, `GuiConsoleEnabled`, and `GuiConsoleVisible` set to `1`.

![](/Media/UHT/2.png)

5. Save changes, launch the game and if everything was done correctly - an additional panel should pop up.
6. Click the Dumpers tab, and then on "Generate UHT Compatible Headers".

![](/Media/UHT/3.png)

7. Shortly after, a new folder called `UHTHeaderDump` will be created in the same folder as you placed the UE4SS files.


## Exploring the Dumped Header Files
1. Navigate to `UHTHeaderDump` folder, and into `\UHTHeaderDump\<GameBinaryName>\Public`.
2. This folder will contain all the reflected header files of the game, which we can use in modding.

![](/Media/UHT/4.png)

> [!TIP]  
> Explore the main or/and the largest header files, as they can give additional insight of methods and variables which are not visible in blueprints while using FModel.