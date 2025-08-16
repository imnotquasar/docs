# canUsePhone

The **canUsePhone** export allows you to block or unblock the use of the phone. This is particularly useful for integrating with other assets, such as preventing phone use while a player is handcuffed or in a restricted state.

***

## How to Use

To enable or disable phone usage, pass a boolean value (`true` or `false`) to the export:

```lua
-- Block phone usage
exports['qs-smartphone']:canUsePhone(false)

-- Unblock phone usage
exports['qs-smartphone']:canUsePhone(true)
```

This gives you control over when players can access their phones, depending on the situation or external conditions.
