# UModel
UModel is commonly used to browse, view and export; meshes, skeletal meshes, textures, audio files, and config files.</br>
For more complex and in-depth assets such as blueprints, and materials, use [FModel](./ExportingFModel.md).
<br>
UModel will be able to export all files but not browse them properly as FModel does.

## Setting Up
Download the tool, and launch it.<br>
![](/Media/umodel_1.png)<br>


- Specify the full path of the Paks folder of the game.
- Click the "Override game detection" and specify the exact UE version the game is using.
- If you want sounds, tick the Sound checkbox.
- Click OK.
- If the `.pak` is encrypted, UModel will ask for the AES key.
    

## Browsing Assets
You will be greeted with this window, where the left side contains the hierarchical structure of the pak file, and the right side contains the current selected folder and its content.
![](/Media/umodel_2.png)<br>

This part is where you have to explore a bit to find what you want/need.

Meshes and textures will be previewed when double-clicked.<br>
Clicking `O` _(as in Omega)_ in the preview will close the current preview.

## Exporting
Once you find the correct mesh, texture, blueprint, etc, you have two export options;
- Saving as is, meaning textures will be exported as `.uasset`.
- - Do that if you're exporting non-media assets like Blueprints.
- - How? Right-click -> Save Content.
- Regular Export, meaning textures will be exported as `.png` files, and SkeletalMeshes(SK) as `.psk` files.
- - Do that if you're exporting media assets like meshes and textures.
- - How? Export Button at the bottom.

<br>


### Exporting Skeletal Mesh(SK)
![](/Media/umodel_3.png)<br>
- Select the file(s) you want and click Export at the bottom.
- Specify the export path.
- Make sure you have `.psk`for Skeletal Mesh, and `.png` for textures.
- Once ready, click OK.


<br><br>
## Extras
Setting up the UModel can be repetitive, and you can automate this process by creating a simple `.bat` script to automate it.

For this example, I want to auto-open the GR2 pak file, so I will create a `GR2.bat` file within the UModel folder.

_(open it with a text editor)_

Syntax:
```
umodel.exe -game=<version> -path="<paks-folder>" -AES=<AES-key>
```

- Replace the `<version>` with the UE4 version, for example `-game=4.27`.
- Replace the `<paks-folder>` with the full path to the game's Paks folder.
- Optional: If your game contains AES, make sure to add the `-AES=` tag at the end, followed by the actual AES key (`-AES=0x9ED...`).

Make sure you save the file.<br>
And whenever you want to browse that specific game, you double-click the `.bat` script instead of manually doing it.

Thank me later.