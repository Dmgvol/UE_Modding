# Using UAssetGUI
UAssetGUI is a user-interfaced tool for essentially hex editing but without seeing any hex.

## Example - Changing clip size for Trepang2
For this example, we will change the magazine size for the SMG weapon, which is located inside the weapon's blueprint called `BP_SMG`.

![](/Media/fmodel_trepang_smg1.png)
<br>
I'm using FModel as it's easier and faster to navigate.<br>
Once the file is found, export the asset, resulting in 2 files, `.uasset` and `.uexp`.

<br>

### Open using UAssetGUI.
Default variables are always located in the Export starting with 
`(Default__...)`

![](/Media/umodel_trepang_smg1.png)

As we can see, there are quite a handful of values we can change.<br>
But in this example, we will change the maximum clip size.

![](/Media/umodel_trepang_smg2.png)
Once the changes are made, simply save the file! <br>
The tool will automatically generate `.bak` file, but you don't need them, so feel free to remove them.

### 
The last step is to pack the modified `.uasset` and `.uexp` using UnrealPak, and you're done!




<br><br>

## Editing via JSON
UAssetGUI allows to export uasset files into editable `.json` files.<br>
File -> Save As, and pick the `.json` as the save-type.

![](/media/UMODEL_trepang_smg3.png)

JSON format gives full control over the structure of the asset.

![](/media/UMODEL_trepang_smg4.png)
<br>
Once the changes are made and saved:
Load the modified json file into UAssetGUI, and then save it as a regular `.uasset` file.

<br>




## Example 2 - Trepang2: adding items to list (advanced)
We know that we can edit, replace, and remove elements from an asset but how about adding new elements?<br>
In this example, we will add an element to an array that doesn't exist in the asset. <br>

![](/Media/fmodel_trepang_mission1.png)
In Trepang2, there's a game mode HordeMode which stores all of its available levels in a list/array, inside `BP_CombatSimMissionList_Trepang2`.

Export to Uasset, open using UAssetGUI and save to `.json`. <br>


**Note:** save json via UAssetGUI, **not** FModel.<br> FModel creates a read-only json...


To achieve adding a completely new element, you need 4 things: <br>
1. Add new NameMap (references).<br>
2. Add Imports (reference declaration).<br>
3. Adjust NameCount in Generation.<br>
4. Add item to the array.<br>



For this example, I want to add `Mission_Horde_Killstation` to the list, which is an unused level but still functioning.

### Adding new NameMap
The NameMap contains all the used references.

![](/Media/json_trepang_mission1.png)<br>
Each reference exists in 3 formats, which we need to add for our new level.<br>
Scroll down to the bottom and add these 3 lines:<br>
```json
    "/Game/UI/CombatSimulator/Missions/UNUSED/Mission_Horde_Killstation",
    "Default__Mission_Horde_Killstation_C",
    "Mission_Horde_Killstation_C"
```

![](/Media/json_trepang_mission2.png)<br>
_(don't forget to add `,` on the last item before adding, as I have after the "Package")_


### Add Imports
Scroll down a bit and find the `Imports` section.

![](/Media/json_trepang_mission3.png)

Scroll to the bottom of Imports, and add these 3 sections;
The Package declaration, Blueprint declaration, and Class Declaration.

![](/Media/json_trepang_mission4.png)

The object names refer to the 3 NameMap added earlier.<br>
The `OuterIndex` points to the initial Import out of the 3. <br>
The last Import is `-122` making our import in index `-123`, thus we specify that index for the Blueprint and Class declaration.
<br>

### Adjust NameCount in Generation
Scroll down until you find the `Generations` section, containing the number of `NameCount`.
<br>![](/Media/json_trepang_mission5.png)<br>
Append the count by the number of additional added imports.<br>
Which is `3` for this example, making the NameCount: `135`.


### Add item to the array
For this example, I want to append the array `CombatSimulatorMissions` which can be found by searching within the `.json` file. <br>

![](/Media/json_trepang_mission6.png)

Duplicate the first element, and adjust the value to point to the BlueprintGeneratedClass that was added earlier.

Why `-124`?<br>
The last index was `-122`, the first import (the path/package) was `-123` and the BlueprintGeneratedClass was one after, making it `-124`.

### Save changes!
Save the modified `.json` file, and open it using UAssetGUI.<br>
If done correctly, no errors will appear and you can double-check that everything is added correctly by viewing the NameMap, ImportData, and the actual array, ensuring it has the items and points to the correct element.

![](/Media/json_trepang_mission7.png)

Make sure you save, so UAssetGUI can generate the updated `.uasset` and `.uexp` files.

Once done, simply pack using UnrealPak.