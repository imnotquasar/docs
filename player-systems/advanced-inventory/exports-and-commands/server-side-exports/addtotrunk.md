# AddToTrunk

The `AddToTrunk` export allows you to add a specific item to a vehicle’s trunk.

***

## How to Use

To add an item to a trunk, use the following code:

```lua
exports['qs-inventory']:AddToTrunk('plate', 1, 1, 'sandwich', 1)
```

This adds the item 'sandwich' to **slot 1** of the trunk identified by the vehicle's plate, with a quantity of `1`.
