# RemoveItem

The **RemoveItem** export allows you to remove items from a player's inventory. It is particularly useful for managing items with metadata but can also be used to remove items without metadata.

***

## How to Use

### **Removing Items with Metadata**

If the item has metadata, use the following example:

```lua
local playerSource = 1 -- Replace with the player's source ID
local itemName = "water_bottle"
local itemCount = 2
local itemSlot = nil -- Use nil to match any slot
local itemMetadata = { expiry = "2025-01-01", quality = 100 }

exports['qs-inventory']:RemoveItem(playerSource, itemName, itemCount, itemSlot, itemMetadata)
```

### **Removing Items Without Metadata**

If metadata is not needed, you can use this simpler version:

```lua
local playerSource = 1 -- Replace with the player's source ID
local itemName = "water_bottle"
local itemCount = 2

exports['qs-inventory']:RemoveItem(playerSource, itemName, itemCount)
```

### Explanation

* **`source`**: The player's source ID.
* **`item`**: The name of the item to remove.
* **`count`**: The quantity of the item to remove.
* **`slot`**: (Optional) Specify a slot to target; use `nil` to remove from any slot.
* **`metadata`**: (Optional) Specify metadata to match the item you want to remove.

This export provides flexibility for managing player inventories, whether you're removing basic items or handling items with specific attributes.
