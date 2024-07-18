# Changing Textures

For this example, I will change a sword texture for GR2 (UE4.27) but the same principles apply to any other game and engine version.

Once you located the texture you want to replace, export it as PNG and edit it to suit your needs.

![](/Media/ChangingTexture/changingTex1.png)

Launch UE and create the same folder structure as it's shown in FModel.

![](/Media/ChangingTexture/changingTex2.png)

Import the texture(s) into its folder and keep the **same exact** name as it's named in FModel.

![](/Media/ChangingTexture/changingTex3.png)


Notes:<br>
Try and match any texture settings you override with its original type. <br>
- If it's a `Normal` map texture, make sure you pick NormalMap in CompressionSettings.
- If it's an ORM (packed Occlusion|Roughness|Metalic into one), make sure you pick Masks in CompressionSettings. <br>
You can double-check everything in FModel.


Once done, simply pack it and test it in-game.<br>
For more information about how to package your mod, view [Cooking Content guide](/IntermediateModding/CookingContent.md).<br>

(don't forget to name your mod with `_P` in its name)

![](/Media/ChangingTexture/changingTex4.png)


