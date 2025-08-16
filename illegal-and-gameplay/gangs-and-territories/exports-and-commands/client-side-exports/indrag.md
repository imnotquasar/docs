# inDrag

The `inDrag` export allows you to check whether the player is currently dragging an injured player. This is particularly useful for restricting or modifying gameplay mechanics, such as disabling certain menus or actions while dragging.

***

## How to Use

To check if the player is dragging an injured player, use the following code:

```lua
local isDragging = exports['qs-gangs']:inDrag()
if isDragging then
    print("The player is dragging an injured person.")
else
    print("The player is not dragging anyone.")
end
```

This export returns a boolean (`true` or `false`) indicating whether the player is actively dragging another character. Use this information to create custom logic that adapts based on the player's interaction state.
