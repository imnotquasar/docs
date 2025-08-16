# CreateUsableItem

The **CreateUsableItem** export allows you to create items using QS logic, making it ideal for adding metadata or custom functionality to items.

***

## How to Use

To create a usable item, use the following code:

```lua
local itemName = "water_bottle"

exports['qs-inventory']:CreateUsableItem(itemName, function(source, item)
    print("Player used item: " .. item.name)
    -- Add your custom logic here
    if item.metadata and item.metadata.quality then
        print("Item quality: " .. item.metadata.quality)
    end
end)
```

This creates a usable item and attaches the specified logic to it, allowing for dynamic behavior based on item properties or metadata.
