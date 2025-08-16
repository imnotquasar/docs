# RemoveItemIntoStash

The **RemoveItemIntoStash** export allows you to remove items from a specified stash dynamically.

***

## How to Use

To remove an item from a stash, use the following code:

```lua
local stashID = "stash_house" -- Identifier for the stash
local itemName = "bread" -- Name of the item to remove
local itemAmount = 5 -- Quantity of the item to remove
local itemSlot = nil -- Specify a slot or use nil for automatic targeting
local stashSlots = 50 -- Total slots available in the stash
local stashMaxWeight = 1000 -- Maximum weight capacity of the stash

exports['qs-inventory']:RemoveItemIntoStash(stashID, itemName, itemAmount, itemSlot, stashSlots, stashMaxWeight)
print("Removed " .. itemAmount .. " " .. itemName .. " from stash: " .. stashID)
```

This export ensures efficient management of stash contents by removing specified items while respecting slot and weight parameters.
