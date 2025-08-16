# ClearOtherInventory

The `ClearOtherInventory` export allows you to **wipe the contents** of a specific external inventory, such as a stash, trunk, or custom storage.

***

## How to Use

To clear an external inventory, use the following code:

```lua
RegisterCommand('clearother', function(source, args, raw)
    exports['qs-inventory']:ClearOtherInventory('stash', 'inventory_debug_stash0')
end)
```

This command clears the stash identified by the name `'inventory_debug_stash0'`. The first parameter `'stash'` indicates the inventory type (it could be `'trunk'`, `'glovebox'`, etc.). Once executed, all items inside that stash will be permanently removed.

> 🛑 **Warning:** This action cannot be undone. Use it with caution in live environments.
