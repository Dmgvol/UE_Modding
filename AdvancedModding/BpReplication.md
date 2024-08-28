# BP Replication/Dummying/Mimicking
Blueprint (BP) Replication in Unreal Engine 4/5 involves creating blueprints and other assets that mimic the variables and structures of existing in-game blueprints. <br>
This method, also known as creating "dummy blueprints", allows modders to access and manipulate game variables without modifying the original assets.

> [!NOTE]  
> This "replicating" is not overlapping with multiplayer replication.
> It's also known as asset dummying or mimicking process.

## Finding the BP we want to replicate
For this example, we will replicate a `float` value within the player character BP.

Using FModel, I found this value.<br>
_(Note for UE5: `Double` is `float` in UE5)_

![](/Media/replication/replication1.png)

And the base class of this blueprint is `Character` which we can see if we search for `SuperStruct` of the BP.

![](/Media/replication/replication2.png)

## Unreal Engine
1. In UE, create the **SAME** folder structure as in the folder in FModel.
2. Create a new BP of type `Character`.

![](/Media/replication/replication3.png)

1. Name the blueprint **EXACTLY** as in the game files.
2. Double check the folders are identical.

![](/Media/replication/replication4.png)

1. Create a new variable.
2. Name it **EXACTLY** as shown in FModel, in this case it's `NormalJumpVelocity`.
3. Set the correct type (in this case, it's `float`). 

**Note:** Some variables won't be using native types, so you will need to do more replication to be able to set them.

![](/Media/replication/replication5.png)

## Using It
Open your mod bp, and access it directly.<br>
In this case, it's a variable within the character bp which we can get by getting the player character object and casting it to the correct BP type, as shown below.

![](/Media/replication/replication6.png)

This allows modders to directly access and change the value of assets within the game-files without modifying the original ones.

### About Replication
This is not limited to variables, so you can replicate methods, delegates, any other type of assets, BP components, and even C++ headers.

## Packaging
We don't package anything that was replicated! <br>
As this will result in overwriting the game-files which we don't want. 

Only package the BP mod files.