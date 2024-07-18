# Replicating Material Instances
Mostly used in game that won't accept custom/plain materials or the modder wants to inherit a material behavior without breaking it and adjusting its parameters.

__Number of examples to use a MaterialInstance(MI)__
- When a game won't accept plain materials, like [HighOnLife](https://store.steampowered.com/app/1583230/High_On_Life/). <br>
For custom materials to work in such a game, you have to find an already existing MI with the same parameters as your target mesh.
- There's a hologram material that you want to use in your mod but want it to look the same but with your image/text. <br>
If there's a glitching effect or panning effect, you would like to keep it while having your texture in it.
- The character is using a special MaterialInstance with specific effects like a built-in outline, so you can set your own texture while keeping the original structure.

## Identify the Base Material
Using FModel:
- Find and open the MI you want to replicate, it should be of type `MaterialInstanceConstant`.
- Look at the Parent material, and click it to navigate to it.

![](/Media/ReplicatingMI/1.png)

Depends on the level of material inheritance, it's not a direct link to the parent so you have to keep going down the inheritance to find the base material.<br>
In this example, the MI inherits from another MI - go to that parent until you reach the base material.

![](/Media/ReplicatingMI/2.png)

This is the base material because its type is no longer `MaterialInstanceConstant` but a simple `Material` type.<br>

1. Open your UE project.
2. Create the same folder structure in your content browser as it's shown in FModel.
3. Create a new material and name it to match the base material, in my case it's `M_Master_Computer_Display`.

![](/Media/ReplicatingMI/3.png)

## Replicate Material Parameters
Once the base material is created, we can start replicating all the parameters we need.<br>
For this example, it's just a single texture parameter, but you can add more parameters that are part of the base material such as values, colors, and textures. <br>
When you add more parameters - Make sure you connect them to the Material node, it doesn't have to make sense.. just connected.

In the original MI, the parameter I'm interested in is `Base_TEX`.
- Open the newly created base material.
- Create the parameter, name it exactly as in FModel, and connect it to the Material Node.

![](/Media/ReplicatingMI/4.png)

## Instantiate the Material
1. Right-click on the newly created base Material.
2. Create Material Instance.

![](/Media/ReplicatingMI/5.png)

Move the new MaterialInstance(MI) into the folder of the target MI.<br>

![](/Media/ReplicatingMI/6.png)

## Using the MI
Now that we're done with the replication part, let's start using it.

1. Right-click on the MI and create a **another** MI from it.

![](/Media/ReplicatingMI/7.png)

2. Move the newly created MI to your mod folder.
3. Name it whatever you want.
4. Open the MI.
5. Check any parameters you would like to overwrite compared to the previous MI in the inheritance.
6. Set the overwrite values for the parameters such as textures, colors and values _(just a single tex in this example)_.

![](/Media/ReplicatingMI/8.png)

You can assign it to your static meshes and skeletal meshes.


<hr>

# Example of MI Replication with StaticParameters
There will be some Material Instances that will still fail to render the custom textures, even when doing the MI replication/dummying.<br>
For such cases, you need to instantiate another MI of the same type, without going down the MI inheritance line as shown above.

- It's commonly spotted when both custom plain materials and replicated base materials don't work.

For example, a character in a game called "Alone in the Dark" (UE4.27) won't accept custom materials.<br>
1. Using FModel, look at the default material instances used by the SK.
2. Find a MI that is close to your material needs within the used material instances, like BaseColor, ORM, and/or Normal map.
3. In this example, the MI I've picked is the MI used for the hat, called `MI_Fleece_GraceHat` which is the most basic and suitable for this need.
4. In UE editor, create a material with the same name inside the same folder as in FModel.
5. Create the needed parameters inside that plain material, but keep the name as the original, `MI_Fleece_GraceHat`. <br>
**Don't pack this material in your mod**

![](/Media/ReplicatingMI/example1.png)

6. Create a MI from that material, and apply your textures in the MI parameters.

If you're replacing a MI - name and place in the it in place of another MI.<br>
If you're replacing the skeletal mesh - name it whatever you want, just don't forget to pack it.

![](/Media/ReplicatingMI/example2.png)

