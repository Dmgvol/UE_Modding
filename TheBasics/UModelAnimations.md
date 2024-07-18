# Previewing Animations
UModel is great at finding all associated animations of a skeleton mesh and playing them.

Once you load your Skeletal Mesh(SK), SkeletalMesh->FindAnimations.

![](/Media/umodel_anim1.png)

After a short search, it will print the number of found animations for this SK.

![](/Media/umodel_anim2.png)


### Basic Navigation
- LMB - Orbit around SK.
- RMB - Zoom in/out.
- `[` - Previous Animation.
- `]` - Next Animation.
- `Space` - Play current animation.

## Exporting Animations (.psa)
Using the FlatView search, type in the name of the animation, then right-click and Export.
![](/Media/umodel_anim3.png) <br>

The exported `.psa` file is a Skeletal Mesh(SK) animation that can be loaded into Blender using a plugin or/and used for modding.