# RemoveFromTrunk

The `RemoveFromTrunk` export allows you to remove a specific item from a vehicle’s trunk.

***

## How to Use

To remove an item from a trunk, use the following code:

```lua
exports['qs-inventory']:RemoveFromTrunk(source, 'plate', 1, 'sandwich', 1)
```

This removes the item `'sandwich'` from **slot 1** of the trunk identified by the vehicle's plate, triggered by the given player `source`.
