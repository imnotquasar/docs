# SetCanOpenPhone

The **SetCanOpenPhone** export allows you to enable or block the use of the phone dynamically. This is particularly useful for controlling phone usage during specific events or scenarios, such as when a player is cuffed or in a restricted area.

***

## How to Use

To control phone access, use the following code:

```lua
exports['qs-smartphone-pro']:SetCanOpenPhone(false) -- Blocks phone access
exports['qs-smartphone-pro']:SetCanOpenPhone(true)  -- Allows phone access
```

This export takes a boolean (`true` or `false`) as an argument to enable or disable the phone. Use it in your scripts to manage phone functionality as needed.
