# Creating a Widget
This guide will go through creating and interacting with the widget.

For more detailed information about widgets, visit: <br>
[UMG UI Designer Quick Start Guide](https://dev.epicgames.com/documentation/en-us/unreal-engine/umg-ui-designer-quick-start-guide-in-unreal-engine) on UnrealEngine documentation.

## Create the widget
1. Create the widget by right-clicking in the Content Browser -> User Interface -> Widget Blueprint, and select the User Widget under Common.

![](/Media/CreatingWidget/1.png)

2. You can rename it or use the default name for the Widget Blueprint you created.<br>
Name it with the prefix `WBP_` (WidgetBlueprint) 
followed by a suitable name for that widget, for this example: `WBP_MyWidget`

![](/Media/CreatingWidget/3.png)

3. Double-click on the created widget, and at the top-left side, search for `Canvas` and drag it onto the hierarchy root object.

![](/Media/CreatingWidget/4.png)

4. Do the same with, `Text` but drop it on top of the canvas panel.

![](/Media/CreatingWidget/5.png)

5. Set it as a variable, name it, and adjust its location as you wish. 

![](/Media/CreatingWidget/6.png)


> [!NOTE]  
> For more infomation about the widget layout/panels, visit: [Widget Blueprints](https://dev.epicgames.com/documentation/en-us/unreal-engine/widget-blueprints-in-umg-for-unreal-engine) on UE documentation.

## Widget Event Graph

1. Navigate to the Event Graph of the widget, and create a new custom event, by right-clicking and searching for `custom`.

![](/Media/CreatingWidget/7.png)

2. Name it `SetPositionText`.
3. Add a new Input variable, of type  Vector.

![](/Media/CreatingWidget/8.png)

4. Create the following logic as shown in the image below.

![](/Media/CreatingWidget/9.png)

## Initializing the widget
1. Navigate to the ModActor of your mod, and add a node called `Create Widget`.
2. Plug it into BeginPlay, so it creates the widget when the mod actor spawns.
3. Provide the widget class in the Class field.
4. Create and plug the `Add to Viewport` as shown in the image below.

![](/Media/CreatingWidget/10.png)

In order to use and access the newly created widget, we need to store it in a variable.

5. Drag the Return value of the widget, and promote it to a variable.

![](/Media/CreatingWidget/11.png)

## Using the widget
For this simple example, we will get the player pawn location on the event tick, and use the widget's method to set the position text.

![](/Media/CreatingWidget/12.png)

> [!TIP]
> Avoid directly accessing the text component outside of the widget like in mod actor BP, try using methods to ensure low coupling between objects.

# Results
We've created a simple custom widget where we can directly access it and call methods.

![](/Media/CreatingWidget/13.png)

<br>
<hr>

### Bonus
It's common practice to ensure the displayed data is easily understandable and readable.

For example:
- Formatting/appending the text with a description of the following data.
- For vector types, divide the vector by `100` units for easy readability.

![](/Media/CreatingWidget/14.png)

![](/Media/CreatingWidget/15.png)

