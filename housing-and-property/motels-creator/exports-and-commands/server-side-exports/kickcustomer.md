# kickCustomer

The `kickCustomer` export allows you to remove a player from their assigned motel room by specifying their unique identifier. This can be used for administrative purposes or to manage motel room availability.

***

## **How to Use**

To kick a player from their motel room, use the following code:

```lua
local playerIdentifier = "steam:110000123456789" -- Replace with the player's identifier
exports['qs-motels-creator']:kickCustomer(playerIdentifier)
print("Player with identifier " .. playerIdentifier .. " has been removed from their motel room.")
```

This example will remove the specified player from their assigned motel, update the server-side data, and notify them in-game. Use this export to manage motel rooms effectively in your scripts.
