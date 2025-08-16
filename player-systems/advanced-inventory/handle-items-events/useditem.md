# usedItem

The `inventory:usedItem` event is triggered whenever a player uses an item from their inventory. You can use this event to implement custom logic for specific items.

***

## Event Structure <a href="#event-structure" id="event-structure"></a>

```lua
AddEventHandler('inventory:usedItem', function(itemName, ...)
    -- Your logic here
end)
```

***

### **Parameters** <a href="#parameters" id="parameters"></a>

1. **`itemName`**: The name of the used item (string).
2. **`...`**: Additional parameters if the item sends extra data.

***

## Basic Example: Detect Specific Item Use <a href="#basic-example-detect-specific-item-use" id="basic-example-detect-specific-item-use"></a>

```lua
AddEventHandler('inventory:usedItem', function(itemName)
    if itemName == "water_bottle" then
        print("Player used a water bottle!")
    end
end)
```

***

## **Implementation Steps** <a href="#implementation-steps" id="implementation-steps"></a>

1. Place the code in a server-side.
2. Match the item name (`itemName`) to your inventory items.
3. Add any custom functionality as needed.

This event is a simple and effective way to extend your inventory system with custom item logic.
