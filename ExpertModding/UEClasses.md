# Creating Classes based on UHT Headers
Once we have UHT headers, we can use them to construct relevant classes in our UE project and then use those classes, variables, methods and data objects in our blueprint mods.

> [!NOTE]
> This guide won't cover all cases, only a basic example of a single class, variable and method.

For this example, I will be making a mod for [Trepang2](https://store.steampowered.com/app/1164940/Trepang2/) where player regenerates 25% health on enemy execution.<br>
Similar to Doom, where the player regenerates health on enemy execution.


## Research
First thing we need to do is identify the used class and the methods and/or variables that we will use for our mod.

![](/Media/Headers/1.png)

Looking at the player BP, the health is being called from the parent class, `BaseCharacter`.

![](/Media/Headers/2.png)

Assuming we already have the UHT headers, look for the class header, in this case it's `BaseCharacter.h`.

> [!IMPORTANT]
> If you don't have UHT headers, go to [Dumping UHT](/ExpertModding/GeneratingUHT.md) guide.

Scrolling down, we can find the health methods, for max health getter and health setter method.

![](/Media/Headers/3.png)

## Unreal Engine - Creating the Class
> [!NOTE]
> If you can't see or add C++ classes, you will have to recreate the project with C++ setting enabled.

1. Launch the UE project and create a new C++ class by File -> New C++ Class.
2. For the Parent class, set it to `Character` class.
- - You can see the base class in the header class declaration line.
- - If it's not in the list, go down the class hierarchy until you reach a native UE class. 

> [!TIP]
> Depending on the scale of the project, you can either recreate the whole/full hierechy structure or directly the base class.
> Meaing that if you have ClassA -> ClassB -> Character, with "directly" it means ClassA -> Character (skipping any in-between).
> And full meaning all of it, all three, one by one. 

3. Click next, and name it **EXACTLY** as the header file.
4. Set it to `Public` and click Create Class.

![](/Media/Headers/4.png)

## Visual Studio
1. Once a class is created, Visual Studio will be launched, with 2 new objects; `.cpp` and `.h` with the given class name (`BaseCharacter.cpp` and `BaseCharacter.h`).
2. In the `BaseCharacter.cpp` file, remove everything besides the `#include "BasePlayer.h"`.
3. In the `BaseCharacter.h`, remove any methods and variables that were auto added on creation (we don't care about them).

![](/Media/Headers/5.png)

4. Add the same class tags as in the dumped header file.

![](/Media/Headers/6.png)

> [!TIP]
> Pay attention to the declaration fields/tags of each item.

5. Now add the methods and variables you're interested.

![](/Media/Headers/7.png)


#### About Methods/Functions
Each method in the header needs to return its type of a default value. <br>
A few examples:
- For boolean, add `{return false;};` 
- for floats or integers, add `{return 0;};`
- for voids, add `{};`

> [!NOTE]
> If it's a custom type then you will need to recreate it, and only then use it.

### Compile
To compile the project, right-click on the project name in the Solution Explorer and then "Build Solution".

![](/Media/Headers/8.png)

If everything was done correctly, the build will be successful.

![](/Media/Headers/9.png)

> [!NOTE]  
> It's quite common for the build to fail which can be caused by countless of reasons, and I'm afraid I can't cover them in this guide.

## Back to UnrealEngine
Go back to UnrealEngine editor, into the mod Blueprint.<br>
You should now be able to access those variables and methods within their corresponding classes.

In this case, it was the player character which I can cast to and access all of its C++ stuff.

![](/Media/Headers/10.png)


Now we can properly use methods and variables from C++ classes in our bp mods.<br>
And for this example, the player health is set on an enemy execution by a configurable percentage.

![](/Media/Headers/11.png)



## Results
The final mod can be found here:<br>
[Trepang2 - Health Regen on Enemy Execution](https://www.nexusmods.com/trepang2/mods/92)