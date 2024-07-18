# Example 1 - Modifying default BP values
As an example, we will modify the max ammo per clip/magazine for an SMG weapon in a game called Trepang2.

_(UE5 modders - Not possible if the game has IOStore enabled)_

### Finding the Asset
The first thing I do is find the correct blueprint containing that piece of information, which in this case is the `BP_SMG`.

![](/Media/Example-1/example_trepang_modifying1.png)

### Modifying the Asset
Export the asset, open the asset using UAssetGUI, and navigate to the default values section of the blueprint.<br>
Default values are in `Export n (Default__<BP_Name>_C)` in every BP, for this it's `Export 7 (Default__BP_SMG_C)`.

![](/Media/Example-1/example_trepang_modifying2.png)

If we scroll down a bit, we can find the value we were looking for, the `AmmoPerClip`, which I will set to `99`.

### Create the Pak file
Save the changes and begin with constructing the mod folder.

![](/Media/Example-1/example_trepang_modifying3.png)

In this case, the folder structure is:<br>
```
MoreAmmoSMG_P\CPPFPS\Content\Weapon\SMG
```

Where the last folder in the path, contains the modified assets (`.uasset` and `.uexp`).

### Results
Package it using UnrealPak, move the created pak file into Paks folder, and test it in-game.

![](/Media/Example-1/example_trepang_modifying4.png)