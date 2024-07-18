# Editing UMaps using Stove
The tool can be found here: [Stove](https://github.com/bananaturtlesandwich/stove) by [bananaturtlesandwich](https://github.com/bananaturtlesandwich).

Stove can be useful for moving, duplicating, or removing existing objects.
<br>Along with editing default values of objects, and even transplanting actors from a different umap.

_It won't always work, but that's an additional option to edit `.umaps` to some extent._

## Loading UMaps
Launch Stove, and before opening the `.umap`:
- Specify the Paks folder of the game.
- Specify the game's UE version.
- AES key (if any).

Load the `.umap` you want, and you should see some kind of representation of the map, either just cube-shaped objects or cached meshes(both are fine).

If you know the name of the asset/actor, you can search for it in the top-left corner.

Stove: <br>
![](/Media/stove/stove1.png)

Compared to In-game, we can get our bearings of where the camera is, and navigate to where we need. <br>
![](/Media/stove/stove2.png)

For this example, I will duplicate a few props to illustrate the basics of this tool.<br>
To duplicate the selected object, `Alt+Drag`.
<br>
The position can be manually adjusted if needed.

![](/Media/stove/stove3.png)

Additionally, Stove allows of editing of default values of selected objects, both blueprints and native UE components such as this desk lamp blueprint (spawn instance values, not global).

![](/Media/stove/stove4.png)

## Saving and packing
Once you're satisfied with the changes, click File->Save.<br>
And proceed with the normal procedure of packing using UnrealPak.

### Results
![](/Media/stove/stove5.png)