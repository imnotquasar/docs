# AddItem

The **AddItem** export allows you to add items to a player's inventory programmatically. It is particularly useful for adding items with metadata but can also be used for simple item additions without metadata.

***

## How to Use

### **Adding Items with Metadata**

If you need to include metadata, use the following example:

```lua
local playerSource = 1 -- Replace with the player's source ID
local itemName = "water_bottle"
local itemCount = 5
local itemSlot = nil -- Use nil to assign the first available slot
local itemMetadata = { expiry = "2025-01-01", quality = 100 }

exports['qs-inventory']:AddItem(playerSource, itemName, itemCount, itemSlot, itemMetadata)
```

### **Adding Items Without Metadata**

If no metadata is required, you can use this simpler version:

```lua
local playerSource = 1 -- Replace with the player's source ID
local itemName = "water_bottle"
local itemCount = 5

exports['qs-inventory']:AddItem(playerSource, itemName, itemCount)
```

### Explanation

* **`source`**: The player's source ID.
* **`item`**: The name of the item to add.
* **`count`**: The quantity of the item to deliver.
* **`slot`**: (Optional) Specify a slot to place the item; use `nil` for the next available slot.
* **`metadata`**: (Optional) Add custom data like quality, expiry, or other attributes.

This export is flexible and suitable for creating items dynamically or adding custom properties to items when required.
