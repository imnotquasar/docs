# Search

The **Search** export allows you to search for specific items in the player's inventory on the client side. This is useful for checking if a player has a particular item or the quantity of that item in their inventory.

***

## How to Use

To search for an item, use the following code:

```lua
local result = exports['qs-inventory']:Search('item_name')
if result then
    print("Item found! Quantity:", result)
else
    print("Item not found.")
end
```

Here’s an example of a command that checks if the player has a specific item, like "money":

```lua
RegisterCommand('checkclientitem', function()
    local result = exports['qs-inventory']:Search('money')

    if result then
        print('Result: Player has', result, 'money.')
    else
        print('Result: Player does not have money.')
    end
end)
```

This example checks for the **"money"** item in the player’s inventory and prints the result. If the item is found, it will return the quantity; otherwise, it will return `nil`.
