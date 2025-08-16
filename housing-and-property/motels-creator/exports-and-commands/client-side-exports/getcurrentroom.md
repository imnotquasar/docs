# getCurrentRoom

The `getCurrentRoom` export allows you to retrieve the identifier of the room the player is currently in. This is useful for tracking player location within the motel system or implementing room-specific logic.

***

## How to Use

To get the current room of a player, use the following code:

```lua
local currentRoom = exports['qs-motels-creator']:getCurrentRoom()
if currentRoom then
    print("The player is currently in room: " .. currentRoom)
else
    print("The player is not in any room.")
end
```

This example retrieves the room identifier and checks if the player is inside a room. Use this export to integrate room data into your scripts seamlessly.
