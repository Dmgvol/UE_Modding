# Adding custom game buttons into existing menus
The purpose of this guide/mod is to add a custom button that looks and behaves like one of the game's buttons, to an existing menu.<br>

> [!NOTE]  
> This guide assumes you already know how to create blueprint mods.

In Ghostrunner 2, there's a menu button "Extras" with 2 sub-buttons.<br>
And our goal is to add the same-looking button into its stack but with our own text and logic.

![](/Media/GameMenus/1.png)

> [!NOTE]  
> Every game will be different but this is the generic approach to this type of mod.

## Finding the components
In this particular example, the main menu panel is called `BP_PanelStartMenu`, <br>
which we can look into and find the Credits sub-button, as shown in the image.

![](/Media/GameMenus/2.png)

In the image, we can see a few useful things:
- The type of the component, `BP_PanelStartMenuSubButton_C` which we will need to dummy it.
- The base properties like the TitleText.
- The parent object holding this item, which is `VerBoxExtrasButtons`.

> [!IMPORTANT]  
> In UE4 it won't matter if the component has IsVariable set to false, you can still access it directly.
> In UE5 it's different, only IsVariable components can be accessed, so you will have to find and navigate through the widget hierarchy.


## Dummying/replicating it
1. Create both widget blueprints in their original folders and name exactly how it's in-game files.

![](/Media/GameMenus/3.png)

> [!TIP]  
> In some rare cases, it's worth to fully replicate the entire button design for more control.

2. Open the menu button widget, and dummy the necessary fields/methods/delegates.

![](/Media/GameMenus/4.png)

3. For a button, we need to handle the text and a way to detect the click.

- The text is stored in a variable of type Text named `TitleText`.
- The click detection is done via an event dispatcher/delegate named `OnClickDelegate`.

![](/Media/GameMenus/4-1.png)

> [!TIP]  
> Different games will need different approaches to it. 
> The delegate/dispatcher will be different in every game, and if the button widget has any component of type Button (the default UE type), you can bind to it.


4. Navigate to the dummy widget for the menu panel.
5. Create the menu button widget in the canvas panel (doesn't matter where).
6. Name it with the correct name, exactly how it's named in FModel, and set it as a variable (right of the name).

![](/Media/GameMenus/5.png)


## Hooking into the menu
In the ModActor, we first want to check if it's the current map and destroy the mod if it isn't the correct level name.

> [!NOTE]  
> Relevant for main menu level or a menu which is persistent in a specific level.
> If it's a pause menu, you need a different logic to detect it.

![](/Media/GameMenus/6.png)

Now we need to detect if the menu is loaded which may be delayed and not persistent on level begin.<br>
That's why I've used a loop timer to constantly look for it.

![](/Media/GameMenus/7.png)

Once the panel was detected, the next thing is: 
- Create the button widget.
- Set default variables like the title text.
- Bind/handle the OnClick of the button.

And then attach the button to the original button's parent.

![](/Media/GameMenus/8.png)

## Results
The button is created at the bottom of the stack/list and works as intended.
![](/Media/GameMenus/9.png)

> [!TIP]  
> Different games might require additional logic to work properly in an existing menu/system.


<hr>

### Examples
Few examples where this technique was used:
- The [FOV slider](https://www.nexusmods.com/highonlife/mods/5) mod for HighOnLife, where the slider looks exactly as the rest of the settings.
- The [Full Codex](https://www.nexusmods.com/ghostrunner2/mods/22) mod for Ghostrunner 2, where the additional codex categories and panels look and behave exactly like the first codex category.
- The [Ghostrunner Trainer](https://github.com/Dmgvol/Ghostrunner-Mods/blob/main/LogicMods/Trainer/trainer.md) mod for Ghostrunner 1, where all settings for the mod were using the same buttons and layout as the original game settings.