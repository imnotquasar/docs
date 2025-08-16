# itemRemoved

The `qb-inventory:server:itemRemoved` and `qb-inventory:client:itemRemoved` events are triggered whenever an item is removed from a player's inventory. You can use these events to implement custom logic when specific items are removed.

{% hint style="info" %}
The event has the prefix "qb-" for automatic integration to qbcore.
{% endhint %}

***

### Event Structure (Server-Side)

```lua
AddEventHandler('qb-inventory:server:itemRemoved', function(source, item, amount, totalAmount)
    -- Your logic here
end)
```

### Event Structure (Client-Side)

```lua
AddEventHandler('qb-inventory:client:itemRemoved', function(source, item, amount, totalAmount)
    -- Your logic here
end)
```

***

## Parameters

* **source**: The player's source ID (integer).
* **item**: The item name being removed (string).
* **amount**: The quantity of the item being removed (integer).
* **totalAmount**: The total quantity of the item remaining in the inventory after the removal (integer).

***

## Basic Example: Detect Specific Item Removal

### **Server-Side**

```lua
AddEventHandler('qb-inventory:server:itemRemoved', function(source, item, amount, totalAmount)
    if item == "water_bottle" then
        print("Player removed a water bottle from their inventory!")
        print("Amount removed: " .. amount .. ", Remaining: " .. totalAmount)
    end
end)
```

### **Client-Side**

```lua
AddEventHandler('qb-inventory:client:itemRemoved', function(source, item, amount, totalAmount)
    if item == "water_bottle" then
        print("Client detected a water bottle removed!")
        print("Amount removed: " .. amount .. ", Remaining: " .. totalAmount)
    end
end)
```

***

## Implementation Steps

1. Place the **server-side** code in a server-side Lua file and the **client-side** code in a client-side.
2. Match the `item` parameter with the item names defined in your inventory system.
3. Add any custom functionality, such as notifications, logging, or effects, as needed.

These events provide an effective way to track and respond to item removals in your inventory system.
