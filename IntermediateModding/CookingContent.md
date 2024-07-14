# Cooking Content
Once you're done with everything you need to do inside the editor, it's time to compile the assets.

For UE4 - Navigate to [Cooking UE4](#cooking-ue4) <br>
For UE5 - Navigate to [cooking UE5](#cooking-ue5) <br>


# Cooking UE4
Once you're ready, click File -> Cook Content for Windows.

![](/Media/Compiling/ue4_1.png)

After a while, the cooking will be completed and you will be able to find the cooked content inside the Saved folder of your project.

```cs
ProjectName\Saved\Cooked\WindowsNoEditor\ProjectName\Content\...
```

From here, you will have to use [UnrealPak](/BasicModding/UnrealPak.md).
<br>
Based on which assets you've created, you will need to copy-paste them into the mod folder (covered in unrealPak guide). 

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