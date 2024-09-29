# Cooking Content
Once you're done with everything you need to do inside the editor, it's time to compile the assets.

__For UE4__
 - Navigate to [Cooking UE4](#cooking-ue4-unrealpak-route) for UnrealPak route.
 - Navigate to [Chunks in UE4](#cooking-ue4-generating-chunks-route).

__For UE5__
- Navigate to [Cooking UE5](#cooking-ue5) <br>


# Cooking UE4 (UnrealPak Route)
Once you're ready, click File -> Cook Content for Windows.

![](/Media/Compiling/ue4_1.png)

After a while, the cooking will be completed and you will be able to find the cooked content inside the Saved folder of your project.

```
ProjectName\Saved\Cooked\WindowsNoEditor\ProjectName\Content\...
```

From here, you will have to use UnrealPak which you can learn more about packaging your mod here: [Creating Pak - UnrealPak](/BasicModding/UnrealPak.md).
<br>
Based on which assets you've created, you will need to copy-paste them into the mod folder (covered in unrealPak guide). 

# Cooking UE4 (Generating-Chunks Route)
Another method of cooking UE content is by packaging specific assets into predefined chunks.<br>
it's faster as there is no need for UnrealPak but It's limited as it packs only what's in the editor. <br>
Meaning it's not suitable if you want to combine modified assets or precooked assets into that mod.

Follow the packaging process in the UE5 section as it's the same procedure.<br>
And once you're done with assigning to chunk:
File -> Package Project -> Windows

> [!IMPORTANT]  
> UE4's process is identical with UE5 in terms of cooking using chunks.

<hr>

# Cooking UE5
For UE5, modders have to assign their assets to specific chunk ids, and there are 2 methods to do so, which will be covered below.

The two methods are [Manual Chunks](#manual-chunk-ids) and [BulkChunk](#bulk-assign-using-datatabledt). <br>

Once the chunks are assigned, simply [Package it](#packaging-ue5).

### Manual Chunk IDs
Right-click on the asset(s) you would like to cook -> Asset Actions -> Assign to Chunk.

![](/Media/Compiling/UE5_1.png)

A small pop-up will show up, where you can input a value between 0 to 300.

Pick any ID that you wish (besides 0), and make sure it's not already used by the game.<br>
_(Look at the Paks folder)_


You can double-check the assigned chunk ID of assets, by selecting all of the assets, and then clicking on Audit Assets.

### Bulk Assign using DataTable(DT)
This method will assign all (or explicit) files within the **same** folder, which has its advantages and disadvantages.

Right-click to create a new asset -> Miscellaneous -> Data Asset.

![](/Media/Compiling/UE5_2.png)

Pick the `PrimaryAssetLabel` from the list.

![](/Media/Compiling/UE5_3.png)


Once created, open the DataAsset, and:
- Set the Priority to 1.
- Pick any Chunk Id from 0 to 10,000.
- set "Apply Recursively" if you have multiple folders.
- Set `Cook Rule` to `Always Cook`.
- Check `Label assets in My Directory` field.
- (Optional) You can hand-pick specific assets/blueprints that you wish to pack.

Note: Using DataAsset will pack everything inside the folder.<br>
So if you want to pack specific ones, make sure to specify them in Explicit section.

![](/Media/Compiling/UE5_4.png)

## Packaging UE5
At the middle top section of the editor, click Platforms -> Windows -> Package Project. <br>
Then select a folder to build the project. <br>
_I usually make a `Build` folder inside the project folder._

![](/Media/Compiling/UE5_5.png)

Once the cooking part is complete, you will find the chunk-assigned results in: <br>
```
\ProjectName\Build\Windows\ProjectName\Content\Paks
```

1. Copy the 3 files from the build folder into the game's Paks folder.
2. Rename it to whatever you want but ensure it ends with `_P` in its name.<br>
For example: `myMod_P`, for all 3 files.
