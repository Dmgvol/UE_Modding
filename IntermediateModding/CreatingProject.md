# Creating an UE project
When it comes to creating completely new assets or overwriting assets with custom ones, modders have to go through compiling the assets for the game/engine to recognize the mod files.

## Downloading the correct UE version
Before you begin downloading UnrealEngine, ensure you know the UE engine version the game is using.<br>
To do so, go to the game's folder, and right-click on the game's exe -> properties -> Details tab.

![](/Media/creatingProject/creatingProject1.png)

For this particular example, the game is using `UE5.2` (your game may have a different number).

Navigate to Epic Launcher, Unreal Engine Tab -> Library. <br>
Then click on the `+` sign.

![](/Media/creatingProject/creatingProject2.png)

An option for picking the UE version will appear, click the dropdown and select the UE version.

![](/Media/creatingProject/creatingProject3.png) <br>



The process is straightforward but we will go over each step.
Depending on your UE engine:
- Navigate to [UE4 Project Creation](#creating-a-new-project-ue4).
- Navigate to [UE5 Project Creation](#creating-a-new-project-ue5).
- If your game has IOStore, follow [Configuring UE5 for Chunks](#configuring-ue5-for-chunks).

_(If there are `.ucas`/`.utoc` files in Paks folder - the game has IOStore)_

## Creating a New Project (UE4)
Launch UE4, click Games at the bottom and click Next.

![](/Media/creatingProject/ue4_1.png)

Select the Blank template, and click Next.
<br>
Optionally, you can pick 3rd person or 1st person template if you want to match the game you're modding with to have some similar functionality at the start.

![](/Media/creatingProject/ue4_2.png)


Specify the path you would like to create the project in.<br>
Name the project **EXACTLY** as the game's project name.

_(If you're unsure of the name, go to the game folder and look.)_

Then click Create Project.

![](/Media/creatingProject/ue4_3.png)

And your UE4 project is created!

![](/Media/creatingProject/ue4_4.png)
 
One important setting to change before starting to mod is disabling the `share material shader code` in the Project Settings.<br>
This will ensure your custom materials work in-game.

![](/Media/creatingProject/ue4_5.png)


<hr>
<br>

## Creating a New Project (UE5)
The process is similar to UE4 but quicker a bit with a different UI.<br>

- Start by launching UE5 and selecting Games on the left column.
- Select Blank template.
<br>_(You can a template to match your game type, for easier testing)_
- Keep the default project default settings.
- Name your project **EXACTLY** as the game's project name, like the "binary name".

Q: Binary name? <br>
A: That's usually how the exe is named, the largest executable named: `"Gamename"-Shipping.exe`.


![](/Media/creatingProject/ue5_1.png)

Once you hit Create, your project will be created.

![](/Media/creatingProject/ue5_2.png)

## Configuring UE5 for Chunks
Go to Edit -> Project Settings -> Packaging, and ensure you have the following settings the same as in the image below.

![](/Media/creatingProject/ue5_3.png)

Don't forget to **untick** `Share Material Shader Code` in Project Settings - this will ensure your custom materials work in-game.

To enable chunk assigning in the editor, go to:<br>
Edit -> Editor Preferences -> search for `chunk` and tick the `Allow ChunkID assignmnets`.

![](/Media/creatingProject/ue5_4.png)

