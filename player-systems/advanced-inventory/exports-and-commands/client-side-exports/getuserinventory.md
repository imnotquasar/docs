# getUserInventory

The **getUserInventory** export allows you to retrieve the list of items currently in a player's inventory in `.amount` format. This can be useful for checking item quantities or implementing custom inventory logic directly from the client side.

***

## How to Use

To get the player's inventory, use the following code:

```lua
local inventory = exports['qs-inventory']:getUserInventory()

for itemName, itemData in pairs(inventory) do
    print("Item Name: " .. itemName)
    print("Amount: " .. itemData.amount)
end
```

This will return a table of items with their quantities, making it easy to access and manipulate the player's inventory programmatically. Use this to search for specific items, display inventory details, or validate item counts.
