# setInventoryDisabled

The **setInventoryDisabled** export allows you to enable or disable the use of the inventory. This is particularly useful for systems like handcuffs or third-party NUI menus where you want to prevent players from accessing their inventory temporarily.

***

## How to Use

To control whether the inventory can be opened, use the following code:

```lua
-- Disable inventory
exports['qs-inventory']:setInventoryDisabled(true)

-- Enable inventory
exports['qs-inventory']:setInventoryDisabled(false)
```

This export accepts a boolean value:

* **`true`**: Disables the inventory, preventing it from opening.
* **`false`**: Enables the inventory, allowing it to open again.

This is ideal for scenarios where you need to restrict inventory access temporarily, ensuring smooth interaction with other systems or menus.
