# GetItemTotalAmount

The **GetItemTotalAmount** export allows you to check the total quantity of a specific item in a player's inventory.

***

## How to Use

To get the total amount of an item, use the following code:

```lua
local playerSource = 1 -- Replace with the player's source ID
local itemName = "water_bottle"

local totalAmount = exports['qs-inventory']:GetItemTotalAmount(playerSource, itemName)
print("Total amount of " .. itemName .. ": " .. totalAmount)
```

This will return the total number of the specified item in the player's inventory.
