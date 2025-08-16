# itemAdded

The `qb-inventory:server:itemAdded` and `qb-inventory:client:itemAdded` events are triggered whenever an item is added to a player's inventory. You can use these events to implement custom logic when specific items are added.

{% hint style="info" %}
The event has the prefix "qb-" for automatic integration to qbcore.
{% endhint %}

***

### Event Structure (Server-Side)

```lua
AddEventHandler('qb-inventory:server:itemAdded', function(source, item, amount, totalAmount)
    -- Your logic here
end)
```

### Event Structure (Client-Side)

```lua
AddEventHandler('qb-inventory:client:itemAdded', function(source, item, amount, totalAmount)
    -- Your logic here
end)
```

***

### Parameters

* **source**: The player's source ID (integer).
* **item**: The item name being added (string).
* **amount**: The quantity of the item being added (integer).
* **totalAmount**: The total quantity of the item in the inventory after the addition (integer).

***

## Basic Example: Detect Specific Item Addition

### **Server-Side**

```lua
AddEventHandler('qb-inventory:server:itemAdded', function(source, item, amount, totalAmount)
    if item == "water_bottle" then
        print("Player added a water bottle to their inventory!")
        print("Amount added: " .. amount .. ", Total: " .. totalAmount)
    end
end)
```

### **Client-Side**

```lua
AddEventHandler('qb-inventory:client:itemAdded', function(source, item, amount, totalAmount)
    if item == "water_bottle" then
        print("Client detected a water bottle added!")
        print("Amount added: " .. amount .. ", Total: " .. totalAmount)
    end
end)
```

***

## Implementation Steps

1. Place the **server-side** code in a server-side Lua file and the **client-side** code in a client-side.
2. Match the `item` parameter with the item names defined in your inventory system.
3. Add any custom functionality, such as notifications, logging, or effects, as needed.

These events are simple yet powerful tools for extending your inventory system with custom logic when items are added.
