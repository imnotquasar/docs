# CanCarryItem

The **CanCarryItem** export checks if a player can carry a specified item based on their inventory capacity.

***

## How to Use

To verify if a player can carry an item, use the following code:

```lua
local playerSource = 1 -- Replace with the player's source ID
local itemName = "water_bottle"
local itemCount = 5

local canCarry = exports['qs-inventory']:CanCarryItem(playerSource, itemName, itemCount)
if canCarry then
    print("Player can carry the item.")
else
    print("Player cannot carry the item.")
end
```

This will return `true` if the player has enough space for the specified item and `false` if not.
