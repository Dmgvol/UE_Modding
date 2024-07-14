# FModel and UAssets
FModel has a major advantage of browsing uassets, it can go in-depth with any UE asset such as blueprints, DataTables, Materials, SkeletalMeshes and more.<br>

- Blueprints: get the used variables and their default values, function names, and even bytecode.
- Materials: get the used material global variables, material instance parent, and the used textures.
- Skeletal Meshes: get the used Skeleton, PhysicsAssets, ShadowAssets.


## Examples
### Blueprints (BP)
Game: Trepang2<br>
![](/Media/fmodel_bp1.png)<br>
In this BP, we can see the parent(SuperStruct) of this BP, and default variable values such as the cost of this weapon and the used image as the thumbnail.
<br>

![](/Media/fmodel_bp2.png)
This BP holds all the data for the SMG in Trepang2, so you can see all the default variables such as.. damage per bullet, AmmoPerClip, ReloadDuration and many more. <br>
Can be used in weapon buff mods!


### Materials
Example of a MaterialInstance(MI) used for the SMG in Trepang2.<br>
![](/Media/fmodel_mat1.png) <br>

This gives us the following info:
- It's a MaterialInstance(MI) and not a plain/simple material.
- It has 3 texture parameters we can use.
- - Albedo.
- - Normal.
- - MRA.


Very important for using and replicating Material Instances in your mods.
<br><br>


### Skeletal Meshes (SK)
Here's the SK for the SMG in Trepang2 <br>
We can see the used Skeleton, which is useful for replicating it in the model swap mods. <br>
![](/Media/fmodel_sk1.png) <br>
The used PhysicsAssets and a ShadowPhysicsAsset. <br>
![](/Media/fmodel_sk2.png) <br>
And the assigned materials for the SK.
![](/Media/fmodel_sk3.png)



### DataAssets
DataAssets are used to store structural data, and this specific one holds the used materials and mesh details for the default gloves in Ghostrunner.
![](/Media/fmodel_da1.png) <br>
Can be swapped/modified with custom or any other data and the game will handle it as the "new default".

### UMaps
UMaps hold all the data of a level/section in the world.<br>
It holds a reference of any object used and any relevant default information of each object (It doesn't hold the actual mesh, just a reference to it).
![](/Media/fmodel_umap1.png) <br>
This `.umap` holds the data for the first section of the level and this specific StaticMesh(SM) of the road sign is part of it.<br>
We can see the default location, rotation and the used SM path.


## Verdict
FModel is a powerful tool when it comes to browsing and going in-depth into any UAsset type, and will quickly become the most used tool in your modding journey.<br>
Feel free to explore!
