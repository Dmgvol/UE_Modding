# FModel
FModel is one of the best tools to browse, view and export all of the file types within the `.pak` file.
<br>
If your game has AES: [Adding AES](#adding-aes-key-optional).<br>
If your game has usmapping: [Adding mappings](#adding-usmapping-optional) _(mostly UE5+)_.

# Creating Game Preset
Launch the tool, Directory -> Selector.

FModel has presets for different games, so it will remember the PAK file and its settings.

To add a new one, simply expand the "Add Undetected Game".

![](/Media/fmodel_1.png)

Next, give it a name and specify the path to the Paks folder of the game. For example:<br>
![](/Media/fmodel_2.png)<br>
And click the `+` button on the right to create a game preset.

Now you can pick the newly created profile and choose the correct UE4 version.
Once ready, click OK to begin.

And the next time you launch FModel, you just pick the game and click OK.
![](/Media/fmodel_3.png)

## Adding AES key (optional)
If your game has AES encryption, navigate to Directory -> AES and input the AES to be able to read the PAK file.

![](/Media/fmodel_4.png)

## Adding USMapping (optional)
If your game has mapping (mostly UE5+), navigate to Settings, enable the "Local Mapping File", and provide the .usmap file for the game.

![](/Media/fmodel_usmapping.png)

_Where can you get that `.usmap`? usually provided by modders_

# Browsing Game Files
That's the part where you have to start to explore and look around to find what you're looking for.

### Navigation Basics
![](/Media/fmodel_5.png) <br>

- Archives Tab: All available `.pak` files within the Paks folder.
- Folders Tab: The hierarchical structure of the `.pak`.
- Packages Tab: Files of the current selected folder.


### Exporting 
Exporting is simple, just right-click on the file(s) you want, and pick the right export type.
![](/Media/fmodel_6.png)<br>

<br>
Different asset types can be exported differently.<br>

-   `.uasset` such as blueprints, DataTables, Structs - export directly or Json (read-only).
- Textures - as `.png`.
- Models such as StaticMesh or SkeletalMesh (characters) - `.psk`
- Animations - `.psa`


It doesn't have to be as exact, it really depends on the case and mod.
<br>
For example: exporting a skeletal mesh as `.uasset` to edit the used textures by changing the paths.

