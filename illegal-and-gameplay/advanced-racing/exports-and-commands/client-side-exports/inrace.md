# InRace

The `InRace` export allows you to check if a player is currently participating in a race. This is useful for managing or restricting specific actions while the player is actively racing.

***

## How to Use

To check whether the player is in a race, use the following code:

```lua
local inRace = exports['qs-advancedracing']:InRace()
print("Is the player currently in a race? " .. tostring(inRace))
```

This will return a boolean value (`true` or `false`) indicating whether the player is actively participating in a race. You can then use this information to implement custom logic, such as blocking certain interactions, modifying gameplay mechanics, or displaying race-specific UI elements.
