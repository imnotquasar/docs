# CheckIfInventoryBlocked

The `CheckIfInventoryBlocked` export allows you to check if the player's inventory is currently blocked (for example, when they are in a menu or in a restricted situation where they can't interact with their inventory).\
This is useful for ensuring certain actions only happen when the inventory is accessible.

***

## How to Use

To check if the inventory is blocked, use the following code:

```lua
local isBlocked = exports['qs-inventory']:CheckIfInventoryBlocked()
if isBlocked then
    print("Inventory is blocked.")
else
    print("Inventory is not blocked.")
end
```

Here’s an example of a command that checks if the player's inventory is blocked:

```lua
RegisterCommand('checkinventory', function()
    local isBlocked = exports['qs-inventory']:CheckIfInventoryBlocked()

    if isBlocked then
        print("Result: Inventory is currently blocked.")
    else
        print("Result: Inventory is not blocked and can be used.")
    end
end)
```

This example checks if the inventory is blocked when using the `/checkinventory` command.\
If the inventory is blocked, it will print a corresponding message; otherwise, it will confirm that the inventory is usable.
