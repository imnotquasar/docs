# GetItemLabel

The **GetItemLabel** export returns the label of a specific item, allowing you to retrieve its display name.

***

## How to Use

To get the label of an item, use the following code:

```lua
local itemLabel = exports['qs-inventory']:GetItemLabel('tosti')
print("Item Label: " .. itemLabel)
```

This will return the label associated with the specified item.
