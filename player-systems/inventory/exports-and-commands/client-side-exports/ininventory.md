# inInventory

The **inInventory** export allows you to check whether the inventory is currently open or closed. It returns a boolean value, making it useful for managing interactions or preventing actions while the inventory is open.

***

## How to Use

To check the inventory status, use the following code:

```lua
local isInventoryOpen = exports['qs-inventory']:inInventory()

if isInventoryOpen then
    print("The inventory is currently open.")
else
    print("The inventory is closed.")
end
```

This will return `true` if the inventory is open and `false` if it is closed. You can use this information to control other systems or restrict specific actions while the inventory is in use.
