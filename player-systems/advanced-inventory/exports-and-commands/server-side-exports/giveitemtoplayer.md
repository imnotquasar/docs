# GiveItemToPlayer

The **GiveItemToPlayer** export allows you to deliver items to a player, including items with metadata. It can be configured in **server/custom** for more customization.

***

## How to Use

To give an item to a player, use the following code:

```lua
local playerSource = 1 -- Replace with the player's source ID
local itemName = "water_bottle"
local itemCount = 5

exports['qs-inventory']:GiveItemToPlayer(playerSource, itemName, itemCount)
print("Gave " .. itemCount .. " " .. itemName .. " to player.")
```

This delivers the specified item and quantity to the targeted player's inventory. You can expand the functionality by adding metadata configurations in **server/custom**.
