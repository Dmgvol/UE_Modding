# Example - Custom Logger
As an example, we will create a custom widget to print different messages for both debugging and notification purposes.

> [!IMPORTANT]  
> This guide assumes you've gone through the previous bp modding guides and you know how to create blueprints, widgets, methods, variables.

We will need to create 3 assets;
- ModActor: The main logic for our mods.
- WBP_Logger: The widget holding the notifications.
- WBP_Notification: The actual notification containing the message.

## Create Widget Layout
This widget will hold a vertical list of notifications.

- Create a new widget, named `WBP_Logger`.
- Add a canvas panel.
- Add a scroll box anchored.
- Anchor it to the left side, stretched vertically.
- Tick "size to content".
- Set "Is Variable" and name it accordingly.

> [!NOTE]  
> Feel free to design it as you wish, I've created a simple vertical box so the notification stack underneath eachother when added.

![](/Media/BpLogger/1.png)

> [!NOTE]  
> We will come back to it to implement the logic once we have the notification widget.

## Create Notification widget
This widget is the actual visual notification that will be added to the list.

- Create another widget, named `WBP_Notification`.
- Add a Canvas Panel.
- Add a Text component.
- - Name it and set it as `Is Variable`.
- - Check `Size to Content`.
- - Add Margin `10, 0, 10, 10`.

![](/Media/BpLogger/2.png)

### Timed notification
Navigate to the event graph of the widget and create the following logic.

![](/Media/BpLogger/3.png)

This will create a timer that will call the DestroyNofitication method after X seconds.

> [!TIP]
> Create a float variable for the notification time, and set its display value.


## Creating notifications
Navigate back to the `WBP_Logger`, the widget that holds the notifications in a scroll box, and create the following logic.

![](/Media/BpLogger/4.png)

- Create a custom method, named `PushNotification` with a String input.
- Add a `Create Widget` node and provide the notification widget class in the Class field.
- Get the text component from the widget and set its text.
- Add the newly created widget as a child into the scroll box component.

## Create ModActor
Create the main actor BP for your mod, named `ModActor`.<br>
Then, create the widget, add it to the viewport and save the reference into a variable.

![](/Media/BpLogger/5.png)


## Using the logger
For this example, a different notification will be pushed based on the pressed keys, but you can use it for debugging or display other useful notifications to the player.

![](/Media/BpLogger/6.png)

> [!TIP]
> You can push notifications, as long as you have the reference to the widget instance.

<hr>

# Results
The notifications stack in the list, and each one disappears after 3 seconds. <br>

![](/Media/BpLogger/loggerResult.gif)
