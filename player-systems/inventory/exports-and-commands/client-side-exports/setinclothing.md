# setInClothing

The **setInClothing** export allows you to enable or disable the clothing registration loop. This loop continuously checks and updates clothing items in the inventory. It is particularly useful when interacting with clothing systems to ensure seamless functionality.

***

## How to Use

To control the clothing loop, use the following code:

```lua
-- Enable the clothing loop
exports['qs-inventory']:setInClothing(true)

-- Disable the clothing loop
exports['qs-inventory']:setInClothing(false)
```

This ensures that clothing items are correctly tracked when the loop is enabled and prevents conflicts by pausing the loop when disabled, such as during the use of a clothing menu.
