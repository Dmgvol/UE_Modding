# Changing StaticMeshes
The process is similar to texture swap but with a few additions of materials and textures.

We will need Blender, and a Blender PSK-plugin to be able to import the `.psk` files which are exported from FModel/UModel.<br>
Blender is free and available on [Blender website](https://www.blender.org/) or on [Steam page (Blender)](https://store.steampowered.com/app/365670/Blender/).

The plugin link: [io_scene_psk_psa](https://github.com/DarklightGames/io_scene_psk_psa).<br>
_(download the correct version, and follow the instructions in that repo readme)_

Note: I'm still using the [older version](https://github.com/Befzz/blender3d_import_psk_psa) for Blender v3, so it might look different a bit.


### Finding the model in FModel
For this example, I will be replacing this fuel-tank model with a [Sci-fi crate](https://sketchfab.com/3d-models/sci-fi-crate-now-free-8a8f77af0de14630b94d2cda49823a74) model which I found on Sketchfab.<br>

Once you found the model, Right-click -> Save Model.<br>
Which will save the model as `.psk` file.

![](/Media/changingSM/changingSM1.png)

### Blender time!
Using the plugin, import the `.psk` file <u>without</u> scaling down.<br>
(in the newer plugin and Blender 4, keep the scale to 1.0)<br>
(in old plugin, untick ScaleDown)

![](/Media/changingSM/changingSM2.png)

Import your custom model, and scale it to fit the original proportions.

![](/Media/changingSM/changingSM3.png)

Move the new mesh to the center, rename it to match the original name, and remove the old/original mesh.<br>
Then export as `.fbx` file, and scale it down to `0.01` (in export settings).

![](/Media/changingSM/changingSM4.png)


### Unreal Engine
Launch UE and create the same folder structure as in-game.<br>
Then drag and drop the `.fbx` file, and let it import the associated textures.

![](/Media/changingSM/changingSM5.png)

This step consists of importing any missing textures, creating the materials, and organizing the files a bit.

- Import any textures you need (as it doesn't always load all of them). 
- Rename the static mesh to **match the original file as in FModel**!
- Create and assign the materials (look up on youtube on how to work with materials).
- Renaming textures/materials and organizing (you don't have to, but it will be easier to maintain and work with).
- - I recommend following the best-practice naming conventions.
- - Where Textures start with `T_`, materials with `M_` and static meshes with `SM_`.
- - And moving all of our custom textures/materials into their own folder, for this example; `crate` folder.

![](/Media/changingSM/changingSM6.png)


### Packaging and in-game results
Once the materials are created, assigned, and named - Pack the mod.<br>

For more information about how to package your mod, view [Cooking Content guide](/IntermediateModding/CookingContent.md).<br>
(don't forget to name your mod with `_P` in its name)

![](/Media/changingSM/changingSM7.png)

