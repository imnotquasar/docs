# Clothing items events

Quasar Inventory now brings a clothing system that was requested by multiple customers in our community, which is based on turning any clothing store into a clothing store with metadata, the metadata will share information between players and each garment will have its own data, allowing us to use different clothes as items.

***

## **Exports for clothing use**

To use the clothing integration feature, you may need to make a small modification to your clothing system. Many paid clothing systems already include this modification by default, but if not, you can ask the creator of your clothing system for assistance.

Our asset has a loop that continuously checks the player's clothes, ensuring they are always represented as items within the inventory NUI. When opening a clothing store menu, this loop needs to be temporarily stopped using a specific export from our system. Once the menu is closed, the loop can be resumed.

***

## Example: Stopping the clothing loop when opening the store

When you open the clothing store menu, you need to call the export to stop the loop:

```lua
-- Event to open the clothing store
RegisterNetEvent('openClothingStore', function()
    exports['qs-inventory']:setInClothing(true) -- Stops the clothing loop
    TriggerEvent('your-clothing-system:openMenu') -- Replace with your clothing system's open event
end)
```

***

## Example: Resuming the clothing loop when closing the store

When the clothing store menu is closed, you must call the export to resume the loop:

```lua
-- Event to close the clothing store
RegisterNetEvent('closeClothingStore', function()
    TriggerEvent('your-clothing-system:closeMenu') -- Replace with your clothing system's close event
    exports['qs-inventory']:setInClothing(false) -- Resumes the clothing loop
end)
```

***

## How it works

{% stepper %}
{% step %}
### **When the clothing store menu is opened**

The export `exports['qs-inventory']:setInClothing(true)` temporarily pauses the clothing loop to allow players to interact with the clothing store without issues.
{% endstep %}

{% step %}
### **When the clothing store menu is closed**

The export `exports['qs-inventory']:setInClothing(false)` resumes the loop, ensuring the player's current clothing is properly reflected in the inventory system.
{% endstep %}
{% endstepper %}

This approach ensures a seamless experience for players while maintaining compatibility between the clothing system and **qs-inventory**.
