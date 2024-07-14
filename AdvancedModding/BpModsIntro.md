# Blueprint Modding
Blueprint modding in Unreal Engine allows modders to create and customize game features through a visual scripting system, eliminating the need for traditional coding. This powerful tool enables the modification of gameplay mechanics, AI behaviors, and user interfaces, making it accessible for modders to enhance and personalize game experiences quickly and efficiently.

## Getting Started
If you're part of a game's Discord, check if there's a modding scene for that game, and ensure there's an already existing BP modloader of some type.

**This guide assumes you're using UE4SS, UML, or DML.** <br>
(if nothing sounds similar, you might need to research and ask around the modding scene of your game)

1. Double-check the version of UE the game is using by right-clicking on the exe -> properties -> details tab.
2. Download the correct UE version and create a new project.<br> 
For more details read the [Creating a UE4/5 project](./IntermediateModding/CreatingProject.md) guide.

## Setting up
1. In the Content Browser, create a new folder called `Mods`
2. In the Mods folder, create another new folder and call it whatever you like, like `MyMod`

## Creating the Blueprint
Right-click and select the Blueprint Class.

![](/Media/BpIntro/1.png)

Choose the Actor class.

![](/Media/BpIntro/2.png)

Once the BP is created, rename it to `ModActor`.

![](/Media/BpIntro/3.png)

Double-click the BP and switch to the Event Graph tab, where you will be greeted with a few default nodes.<br>
- EventBeginPlay: executes the code once when the BP is spawned/created.
- EventActorBeginPlay: we will skip this one.
- EventTick: executes the code every time the game is updated, every single frame, if not more..

We will come back to it, so close the window for now.

![](/Media/BpIntro/4.png)

For this example, we will create a widget, a UI to display that the mod is loaded in-game.

## Creating the widget

1. In the Content Browser, right-click->User Interface-> Widget Blueprint.
2. Name it whatever you want, I named it `WBP_MyWidget`.
3. Open it.

![](/Media/BpIntro/5.png)

Search for `Canvas` in the Palette and drag it onto the root object of the widget.<br>
Canvas allows us to place other objects wherever we want on the screen.

![](/Media/BpIntro/6.png)

Seach for `Text` and drag the Text object on the Canvas.

![](/Media/BpIntro/7.png)

1. Select the text.
2. Set your text within the Text field, I set it to `Loaded!` as a test.
3. Save it, close.

![](/Media/BpIntro/9.png)

## Coding the Blueprint

1. Open the BP we created earlier.
2. Pull the EventBeginPlay pin and search for `Create Widget`, and click it.

![](/Media/BpIntro/10.png)

A new node will be created and connected.<br>
Click on the Class dropdown in the node and select your widget by name.

![](/Media/BpIntro/11.png)

1. Drag the Return Value pin from the widget creation node.
2. Look for `Add to viewport` and click it.

![](/Media/BpIntro/12.png)

You should have the same thing as in the image below.<br>
The code basically means: <br>
On begin, create the specified widget, and add it to the screen/viewport.

![](/Media/BpIntro/13.png)

## Final Mod-Folder Structure
And the mod folder should look like this:

![](/Media/BpIntro/14.png)



## Pack it and Test it
The packaging process will vary based on the UE version. <br>
UE4 -> using UnrealPak. <br>
UE5 -> chunk assigning _(unless the game has no IOStore)_.

For more info, check [Cooking with UE](/IntermediateModding/CookingContent.md).

### Loading the mod
Depending on the modloader, the loading process may vary, so double-check with the used modloader instructions or with the modding community for the game you're modding.


![](/Media/BpIntro/15.png)

