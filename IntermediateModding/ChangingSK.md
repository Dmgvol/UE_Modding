# Changing SkeletalMesh(SK)
The process is similar to StaticMesh swap but with a few additions of weight-paint and a few additional replications in UE.

We will need Blender, and a Blender PSK-plugin to be able to import the `.psk` files which are exported from FModel/UModel.<br>
Blender is free and available on [Blender website](https://www.blender.org/) or on [Steam page (Blender)](https://store.steampowered.com/app/365670/Blender/).

The plugin link: [io_scene_psk_psa](https://github.com/DarklightGames/io_scene_psk_psa).<br>
_(download the correct version, and follow the instructions in that repo readme)_

Note: I'm still using the [older version](https://github.com/Befzz/blender3d_import_psk_psa) for Blender v3, so it might look different a bit.

## Blender
For this example, I will be changing the SkeletalMesh(SK) of one of the enemies in Ghostrunner 2.<br>
Start by locating your model in FModel, then export the model into a `.psk` file.

![](/Media/SKSwap/fmodel1.png)

Using the installed Blender `.psk` plugin, load the file into Blender **without scaling it down**.

![](/Media/SKSwap/1.png)

The SK mesh will be loaded inside an Armature object, shown in the top-right corner.

### Preparing the new model
I've picked this simple model of a [medieval knight](https://sketchfab.com/3d-models/medieval-knight-sculpture-game-ready-6cdd055b4afa41eb9360dbbfe75c7f10) to be used in the SK swap.

#### Scale and Rotation
Load the new model into the Blender project along with the original SK.<br>
Scale and rotate the new mesh so the mesh is as close as possible to the original one, scale and rotation-wise.

![](/Media/SKSwap/2.png)

#### Aligning
Align the new mesh as close as possible to the original mesh.<br>
This ensures the animations will be played properly without weird bone morphing.

If your mesh is rigged like the model I'm using, then simply switch to Pose mode and move the bones to align as closely as possible.

Note:
If your mesh is not rigged, either quickly rig it with automatic weights(look it up on Youtube), use Mixamo to auto-rig or manually move the vertices in Edit mode.

![](/Media/SKSwap/3.png)

#### Applying armature changes
If your model is rigged, and you've aligned the model to the original model, then make sure you apply those changes to the Armature.

![](/Media/SKSwap/4.png)

This will set the current pose as the default pose.


#### Unparenting
We no longer need the armature of the new mesh.<br>
Select the mesh, right-click, Parent -> Clear and Keep Transformation.

![](/Media/SKSwap/5.png)

Once the mesh is separated from its armature, remove the armature (of the new mesh).

![](/Media/SKSwap/6.png)

#### Removing Vertex Groups
Before we parent our mesh to the original Armature, we want to get rid of all the existing bones, also known as Vertex Groups.<br>
This will prevent overlapping and irrelevant bones from being listed in our original Armature.

![](/Media/SKSwap/7.png)

#### UV Map names
This is optional for a complete mesh swap where the new mesh completely takes over the old mesh,<br>
but it's crucial for merging a new mesh into an existing mesh!

With the mesh I'm using, there are 3 UV Maps - we only need one to match the original mesh UV Map name.

![](/Media/SKSwap/8.png)

Navigate to the original mesh, and copy the name of the UV Map, usually it's `UV_SINGLE`.<br>
Go back to the new mesh UV Maps, remove all besides the first one, and name it exactly how the original UV map is named.<br>
In this example, it's `UV_SINGLE`.

![](/Media/SKSwap/9.png)


### Weight-Paint
We've reached the challenging part, weight-paint.<br>
If you don't have any experience with weight-painting in Blender, I would highly suggest watching a few YouTube tutorial videos on it as it's quite a big subject that I won't be covering in this guide.

#### Parenting back
Select your mesh, then select the armature of the original mesh, right-click -> Parent -> With Empty Groups.<br>
The mesh will be parented into the original armature object, inheriting all the vertex groups(bones) of the original one.

![](/Media/SKSwap/10.png)

**Important!**
Always rename the armature of the mesh, to `Armature`! Do not skip this!!!<br>
Without it, the skeleton structure will be altered when imported into UnrealEngine, creating an incorrect/unmatching skeleton structure with the original one, which will break all animations.

![](/Media/SKSwap/11.png)

#### Painting time!
This part is the most time-consuming part, as you have to weight-paint **every** single bone of the mesh to be as close as possible to how it looks on the original mesh.<br>

Switch to Weight-Paint mode, and start weight-painting every single bone, by going one by one in the Vertex Group list.<br>

Tip: I always open another Blender window with the original model in weight-paint mode with the same selected bone.<br>
This helps in getting the proportions and strengths of the target weight-paint result.

![](/Media/SKSwap/12.png)

Once you're done weight-paint, you can check your results by going to Pose mode and moving the individual bones to see if they morph/move as expected.

### Dummy Materials
Dummy materials are done in order to prevent the game from changing the mesh materials at runtime, and to ensure our custom model stays with its original materials throughout the game session.

_Note: You can skip this part ONLY if you're 100% sure the materials are not changed in runtime._

Using FModel, we can see there are 3 materials the original mesh is using.<br>
So create 3 new materials and place them at the top of the list, so they're the first ones followed by your custom model materials.

![](/Media/SKSwap/13.png)

Every material needs to have at least one face assigned to it, otherwise they will be ignored in UnrealEngine.<br>
To do so, the easiest trick is to zoom into the inside of the mesh and extrude a random line multiple times.<br>
Then select the first extructed face, click on dummy material and then Assign (repeat for the number of dummy materials you have). 

![](/Media/SKSwap/14.png)

### Important notes
Here are some important notes to consider while working with SK in Blender:
- Never adjust or move the original skeleton.
- Always have the armature object named `Armature`.
- Align the new mesh as closely as possible to the original mesh, to ensure seamless animations.
- Material names don't matter, it's their order in the list that matters.
- Test your weight-paint results in Pose mode before exporting to save time.

### Exporting!
Well done reaching the exporting part, you've made it through the hardest section of the mod!<br>
Before you export, double-check the materials are correct, the UV maps are correct, the weight-paint is functional, and the root object is named `Armature`.

![](/Media/SKSwap/15.png)

When Exporting, make sure to scale it down to `0.01`.<br>
Here are my settings for exporting:

![](/Media/SKSwap/16.png)



## UnrealEngine
Open your UE project, and create the same folder structure to match the original folder where the SK is located.<br>
Then drag and drop the exported `.fbx` file and click "Import All".

![](/Media/SKSwap/ue1.png)

Name the SkeletalMesh(the character model) to match with how it's named in the game files (important!).

### Assigning ShadowPhysics (if any)
Some games have ShadowPhyiscs in their characters so if your SK doesn't have it - skip this step.<br>

ShadowPhysics in modding is the same as the original PhysicsAssets, so simply duplicate it and name it exactly how it's named in the game files.<br>
_(You can double-check it using FModel, opening the SK asset and scrolling down a bit)_

Once the PA is duplicated and named to match the SP, double-click on the SkeletalMesh(SK), scroll down and drag the SP into its slot.

![](/Media/SKSwap/ue2.png)

### Replicating Skeleton and PhysicsAsset
When you import your mesh into UE, it auto-generates the Skeleton and PhysicsAsset which have to match with the game files.<br>

Using FModel, we can see the name and location of the used Skeleton.<br>
Rename the skeleton to match it, and move it to the same folder as shown in FModel (create the folder structure). 

In my case, the skeleton is named `SK_Enemy_Shinobi` and is located in `/Visual/Character/Shinobi`, so I've created the same folders, named the skeleton, and moved it to that folder.

![](/Media/SKSwap/ue3.png)

**Don't forget:** Do the same with the PhysicsAsset and ShadowPhyiscs(if any).

### Materials
This part will be different in every game and the used SK, so it's a bit difficult to cover all of them.<br>
Creating materials - I won't be covering this, as there are plenty of tutorials on YouTube.

In terms of modding there are 2 options: plain materials, and replicated Material Instances _(in case "plain" doesn't work)_.

Plain means you create an empty Material, drag and drop the used textures and connect it to the Material node, as shown below with a single texture for the BaseColor.<br>
For better quality materials, you would want to have ORM(Occlusion, Roughness, Metallic) and Normal textures as well.

![](/Media/SKSwap/ue4.png)

**Note:**
If plain materials don't work, try to set the same settings as the original/base material.

![](/Media/SKSwap/ue6.png)

If that doesn't work, then you will have to use a replicated Material Instance.


### Pack and test
Once everything is done, double-check you named the asset correctly, placed the skeleton and PA in the correct location, done with the materials and textures.
You can name the materials and textures with common naming conventions for easier readability and maintenance (optional but recommended).

![](/Media/SKSwap/ue5.png)

Pack it and test it!<br>

Only pack the new SK, and the used materials and textures.<br>
DON'T pack the skeleton, physicsAsset or the ShadowAsset.

UE4 -> using UnrealPak (or chunks, if you want). <br>
UE5 -> chunk assigning _(unless the game has no IOStore)_.

For more information about how to package your mod, view [Cooking Content guide](/IntermediateModding/CookingContent.md).<br>
(don't forget to name your mod with `_P` in its name)

# Results 
![](/Media/SKSwap/result.png)