# SetItemMetadata

The **SetItemMetadata** export allows you to assign metadata to an existing item in a player's inventory.

***

## How to Use

To set metadata for an item, use the following code:

```lua
local playerSource = 1 -- Replace with the player's source ID
local itemSlot = 2 -- Replace with the item's slot
local itemMetadata = { quality = 100, expiry = "2025-01-01" }

exports['qs-inventory']:SetItemMetadata(playerSource, itemSlot, itemMetadata)
print("Metadata updated for item in slot: " .. itemSlot)
```

This assigns the specified metadata to the item in the given inventory slot.
