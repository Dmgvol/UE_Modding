# ModActor life cycle
Understanding the lifecycle of a ModActor (Actor Blueprint) in Unreal Engine is crucial for effective modding.

This guide will go through the basics of a blueprint.


## BeginPlay
The `BeginPlay` method in a blueprint is typically called at the beginning of the actor's lifecycle. <br>
This event is fired once when the actor is spawned into the game world or when the game starts if the actor is already placed in the level.

### Key acitvies for `BeginPlay`
- Initialization: Set up initial properties, load game saves, create widgets, identify references, etc.
- Component Setup: Initialize and configure components like meshes, physics, and collision settings.
- Event Binding: Bind events to custom logic, such as handing player inputs or interactions.
- Spawn Related Actors: If your bp needs to spawn other actors then the `BeginPlay` node is an appropriate place to handle such spawns.

> [!TIP]
> Use BeginPlay for setting initial values and loading assets. 


## Tick
The `Tick` method is called every frame, providing a way to update the actor's logic and handle real-time operations.<br>
This method is critical for tasks that require continuous updates, such as monitoring player input.

### Key activities for `Tick`
- Monitor Player Input: Continuously check and respond to player inputs, like movement commands or interaction requests.
- State Checking: Check for certain conditions like health thresholds, proximity to other actors, or specific game states.
- Timed Events: Manage events or actions that need to occur after specific intervals, such as cooldowns or scheduled actions.

> [!TIP]
> Optimize Tick to maintain performance.
