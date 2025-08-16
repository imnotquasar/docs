# GetItemList

The **GetItemList** export allows you to retrieve the complete list of items defined in your **shared/items.lua** file. This is useful for accessing and managing all item data programmatically within your scripts.

***

## How to Use

To get the full list of items, use the following code:

```lua
local itemList = exports['qs-inventory']:GetItemList()

for itemName, itemData in pairs(itemList) do
    print("Item Name: " .. itemName)
    print("Label: " .. itemData.label)
    print("Weight: " .. itemData.weight)
end
```

This will return a table containing all the items and their properties, such as name, label, weight, type, and more. You can use this to interact with or display item details dynamically in your scripts.
