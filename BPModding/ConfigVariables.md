# Config Variables
Config variables allow mod users to configure certain variables of your mod outside of the game without any modding knowledge.

> [!NOTE]  
> Config variables are under-rated in modding, hopefully it gets more popular over time.

## Enabling a config variable
Enabling it is straightforward but can be easily missed as it's under the Advanced section of the variable settings.

![](/Media/ConfigVariables/1.png)


## Using and configuring the variable
All config variables can be set or overwritten by adding the mod's path as a header/section followed by the actual variables and their values.

> [!TIP]
> Config variables will be overwritten at runtime with the one set in the config file, so make sure you implement additional logic to ensure the value doesn't go outside of the expected range.

Hover over the Config Variable checkbox for more info:
![](/Media/ConfigVariables/2.png)

1. Navigate to the game's `engine.ini` file which is located in:
`%localappdata%/<GameName>/saved/Config`
2. Open the file named `engine.ini` with a text editor and scroll to the bottom of it.
3. Add the specific pattern as is shown when hovering over the config variable checkbox.

![](/Media/ConfigVariables/3.png)


> [!IMPORTANT]  
> It's important to mention it for the mod users, so they know about it.

<hr>

## User cases for config variables
One of the most useful cases for it, which I constantly use is configurable hotkeys.<br>
Allowing mod users to freely change and customize the keys to suit their keyboard layouts.

Other useful uses for config variables, but not limited to:
- Enabling certain features.
- Different decimal values like maxHealth.
- Widget related like togglable data to be displayed.
- Functionality limitation.
