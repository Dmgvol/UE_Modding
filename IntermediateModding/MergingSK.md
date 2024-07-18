# Merging SK
Merging SkeletalMesh(SK) is where you merge a specific mesh into an already existing SK without changing its original structure or materials. <br>
For example, a hat on top of a character, while keeping everything in its original state.

_This process is similar to SK swap but a bit shorter._

We will need Blender, and a Blender PSK-plugin to be able to import the `.psk` files which are exported from FModel/UModel.<br>
Blender is free and available on [Blender website](https://www.blender.org/) or on [Steam page (Blender)](https://store.steampowered.com/app/365670/Blender/).

The plugin link: [io_scene_psk_psa](https://github.com/DarklightGames/io_scene_psk_psa).<br>
_(download the correct version, and follow the instructions in that repo readme)_

<br>
For this example, I will be attaching a duck model onto a spider-mech in a game called AtomicHeart (ue4.27).

## Blender
Using the PSK plugin, import the model without scaling.

Blender 4: File->Import->PSK (scale 1).<br>
Blender 3: Using the dropdown menu.<br>
![](/Media/MergingSK/blender1.png)

Rename the root object to `Armature` (Important!).

![](/Media/MergingSK/blender2.png)

Import the new mesh, and align it to suit your model, scale and rotation-wise.

### Preparing the mesh
Before you merge, ensure the UV Map names are **identical**, otherwise the materials will be messed up.

1. Select the original mesh, go to UV Maps, and copy the name of the first UV map, usually, it's `UV_SINGLE`.
2. Select the new mesh, and go to UV Maps (as shown in the image below).
3. Rename the UV Map to match the original mesh UV map name, which in this case is `UV_SINGLE`.

![](/Media/MergingSK/uvmap.png)


### Merging

1. Select the new mesh.
2. Select the original mesh.
3. Click Ctrl+J to merge

![](/Media/MergingSK/blender3.png)

### Attaching to bone (weight-paint)
1. Select the mesh.
2. Go to Weight-Paint mode.
3. Pick a Vertex Group(also known as a bone), that would be logical for the new mesh to be attached to.
4. While the bone is selected, completely paint the new mesh in red.

This will make the new mesh to follow the bone in animations like it's attached to it.

**Note:**
If it's a hat, the logical bone will be the `head` bone, if it's a backpack then the `spine_03` bone, etc...

For this example, the new mesh should be "attached" to the Pelvis, so I've selected the pelvis bone and completely painted the new mesh part in red.

![](/Media/MergingSK/blender4.png)

### Exporting
Before you export:
- Change to Pose mode, and move the bones to see if the new merged mesh follows the correct bones.
- Check the textures work.
- Materials are in order (first the original mesh, then followed by your custom ones).

Export into `.fbx` with `0.01` scale.

![](/Media/MergingSK/blender5.png)


## UnrealEngine
1. Create the same folder structure as in the game files, of where the SK is located.
2. Drag and drop the exported FBX file into the UE content browser, and click Import All.

![](/Media/MergingSK/ue1.png)

### Replicating Skeleton, PhysicsAsset, and Materials
The next step is naming and placing the Skeleton and PhysicsAsset in their original folders.

1. Using FModel, open the SK and look for the full paths of the Skeleton and PhysicsAsset.
2. In UnrealEngine, create those folders.
3. Name the Skeleton and the PhysicsAsset the same as shown in FModel.
4. Move the two into their corresponding folders (if needed).

Now the same goes with the default materials of the mesh.
1. Using FModel, double-check the auto-generated materials are named correctly by opening the SK asset and looking at the used materials.
2. Move them to their original folders (create those folders if missing).

![](/Media/MergingSK/ue2.png)

### Preparing the SK
The last step is making sure the newly merged mesh looks as expected.<br>
Import the textures you need for the mesh and adjust the materials.

![](/Media/MergingSK/ue2.png)

## Pack and test
Only pack the modified SK and the used materials and textures for the new mesh part (not the original/replicated ones).<br>
DON'T pack the skeleton, physicsAsset, shadowPhysics(if any), or any of the replicated materials.

UE4 -> using UnrealPak _(or by assigning chunks)_.
UE5 -> chunk assigning _(unless the game has no IOStore)_.

For more information about how to package your mod, view [Cooking Content guide](/IntermediateModding/CookingContent.md).<br>
(don't forget to name your mod with `_P` in its name)

# Results 
![](/Media/MergingSK/result.jpg)

The mod was showcased in this video at 10:50 mark.<br>
[Atomic Heart but ruined by mods 4](https://www.youtube.com/watch?v=udicbk3VMrk)