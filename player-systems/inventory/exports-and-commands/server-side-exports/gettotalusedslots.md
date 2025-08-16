# GetTotalUsedSlots

The **GetTotalUsedSlots** export allows you to retrieve the total number of slots currently in use in a player's inventory.

***

## How to Use

To get the used slots in a player's inventory, use the following code:

```lua
local playerSource = 1 -- Replace with the player's source ID

local usedSlots = exports['qs-inventory']:GetTotalUsedSlots(playerSource)
print("Total used slots: " .. usedSlots)
```

This returns the total number of inventory slots that are occupied by items for the specified player.
