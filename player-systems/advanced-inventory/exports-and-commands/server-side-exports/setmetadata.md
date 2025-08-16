# SetMetaData

The **SetMetaData** export allows you to assign specific metadata to a player, enabling custom information storage tied to their profile.

***

## How to Use

To set metadata for a player, use the following code:

```lua
local playerIdentifier = "Player_CitizenID" -- Replace with the player's CitizenID or identifier
local metaInfo = "player_rank"
local metaValue = "Elite"

exports['qs-inventory']:SetMetaData(playerIdentifier, { [metaInfo] = metaValue })
print("Metadata '" .. metaInfo .. "' set to: " .. metaValue)
```

This assigns the specified metadata (`metaInfo`) with the given value (`metaValue`) to the player, allowing for flexible customizations.
