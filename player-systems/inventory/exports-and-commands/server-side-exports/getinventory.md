# GetInventory

The **GetInventory** export allows you to retrieve the inventory of a specific player. This is useful for checking items, quantities, or metadata associated with the items in their inventory.

***

## How to Use

To get a player's inventory, use the following code:

```lua
local inventory = exports['qs-inventory']:GetInventory(playerSource)

if inventory then
    for slot, item in pairs(inventory) do
        print("Slot: " .. slot)
        print("Item Name: " .. item.name)
        print("Quantity: " .. item.amount)
        print("Metadata: " .. json.encode(item.info))
    end
else
    print("No inventory found for this player.")
end
```

This returns a table where each key represents a slot number, and each value contains the item's data (`name`, `amount`, `info`, etc.). You can use this structure to validate items, read specific metadata, or apply your own custom logic.
