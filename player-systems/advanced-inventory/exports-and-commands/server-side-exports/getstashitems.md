# GetStashItems

The **GetStashItems** export allows you to check all items currently stored in a specified stash.

***

## How to Use

To retrieve items from a stash, use the following code:

```lua
local stashID = "stash_house" -- Identifier for the stash

local stashItems = exports['qs-inventory']:GetStashItems(stashID)

if stashItems then
    for slot, itemData in pairs(stashItems) do
        print("Slot: " .. slot)
        print("Item: " .. itemData.name)
        print("Amount: " .. itemData.amount)
    end
else
    print("No items found in stash: " .. stashID)
end
```

This retrieves all items in the specified stash, including their slot, name, and quantity, for further processing or display.
