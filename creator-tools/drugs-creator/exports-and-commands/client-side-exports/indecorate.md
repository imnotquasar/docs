# inDecorate

The `inDecorate` export allows you to check if a player is currently in decoration mode. This is useful for managing or restricting specific actions while decoration mode is active.

***

## How to Use

To check whether the player is in decoration mode, use the following code:

```lua
local inDecorate = exports['qs-drugs-creator']:inDecorate()
print("Is the player in decoration mode? " .. tostring(inDecorate))
```

This will return a boolean value (`true` or `false`) indicating whether the player is in decoration mode. You can then use this information to implement custom logic, such as blocking certain actions or triggering events during decoration.
