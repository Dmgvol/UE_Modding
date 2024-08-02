# Hotkeys in Blueprint
For modders, hotkeys in Blueprints provide a way to execute additional logic when specific keys are pressed.<br> 
This feature allows for the creation of custom in-game actions, shortcuts, and debug commands, enhancing the player's experience and testing efficiency.

## Event Graph
The easiest way to monitor if a specific key is pressed is by using the following logic shown:

![](/Media/HotKeys/1.png)


What if we have more keys to monitor? use `Sequence` flow node.

![](/Media/HotKeys/2.png)

> [!TIP]
> Useful for single use or togglable operations, like toggling a flashlight on and off.

## Macro
The more keys you monitor, the messier it gets and to prevent "spaghetti code", it is recommended to use a custom Macro.

1. Left side panel, under the Macros section, press the `+` to create a new Macro and name it `KeyPressed`.

![](/Media/HotKeys/3.png)

2. Create the shown inputs and outputs in the Macro.

![](/Media/HotKeys/4.png)

3. Create the same logic as we had in the event graph, and connect the nodes as shown in the image.

![](/Media/HotKeys/5.png)

4. Now we can use the macro in our event graph.<br>
It's much cleaner and easier to read and maintain.

![](/Media/HotKeys/6.png)

<hr>

### Key press and release
If you need to monitor whenever a key is being pressed and released, create the following macro:

![](/Media/HotKeys/7.png)

> [!TIP]
> Useful for toggling actions while holding the key, like using an in-game tool while a key is being pressed.

### Key down time
If you need to monitor the time a certain key is being held down, create the following macro:

![](/Media/HotKeys/8.png)

> [!TIP]
> Useful for events where the player needs to hold a key for X amount of seconds, like opening a door or quick-action sequences in cinematics.