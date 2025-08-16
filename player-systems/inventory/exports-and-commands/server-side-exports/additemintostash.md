# AddItemIntoStash

The **AddItemIntoStash** export allows you to add items directly into a specified stash, including specifying slots.

***

## How to Use

To add an item to a stash, use the following code:

```lua
local stashID = "stash_house" -- Identifier for the stash
local itemName = "bread" -- Name of the item to add
local itemAmount = 10 -- Quantity of the item
local itemSlot = nil -- Specify a slot or use nil for automatic placement
local stashSlots = 50 -- Total slots available in the stash
local stashMaxWeight = 1000 -- Maximum weight capacity of the stash

exports['qs-inventory']:AddItemIntoStash(stashID, itemName, itemAmount, itemSlot, nil, stashSlots, stashMaxWeight)
print("Added " .. itemAmount .. " " .. itemName .. " to stash: " .. stashID)
```

This export enables you to manage stashes efficiently by dynamically adding items while respecting the stash's slot and weight limitations.
