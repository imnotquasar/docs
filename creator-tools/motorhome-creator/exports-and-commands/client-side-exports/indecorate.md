# inDecorate

The `inDecorate` export allows you to check whether a player is currently in decoration mode. This is particularly useful for managing or restricting specific actions, such as placing objects or enabling specific UI elements, while the player is decorating.

***

## **How to Use**

To check if a player is in decoration mode, use the following code:

```lua
local isInDecorateMode = exports['qs-motorhome']:inDecorate()
if isInDecorateMode then
    print("The player is currently in decoration mode.")
else
    print("The player is not in decoration mode.")
end

```

The export returns a boolean value (`true` or `false`) indicating whether the player is actively in decoration mode. Use this export to implement custom logic, such as preventing movement, disabling certain menus, or modifying gameplay mechanics during decoration mode.
