# GetMetaData

The **GetMetaData** export allows you to retrieve specific metadata associated with a player, enabling you to access custom information stored in their profile.

***

## How to Use

To get metadata for a player, use the following code:

```lua
local playerIdentifier = "Player_CitizenID" -- Replace with the player's identifier

local metaData = exports['qs-inventory']:GetMetaData(playerIdentifier)
if metaData then
    print("Player Metadata: " .. json.encode(metaData))
else
    print("No metadata found for the player.")
end
```

This retrieves and prints the metadata associated with the specified player, providing flexibility for custom logic and features.
