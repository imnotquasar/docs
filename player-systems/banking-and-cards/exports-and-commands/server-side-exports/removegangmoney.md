# RemoveGangMoney

The `RemoveGangMoney` export subtracts a specified amount of money from a gang's bank account, optionally including a reason. This is useful for gang-related systems where funds are spent on weapons, vehicles, bribes, or laundering processes.

***

## How to Use

To withdraw money from a gang account, provide the account name, amount, and an optional reason:

```lua
-- Example usage:
local accountName = "mafia_funds"
local amount = 2500
local reason = "Weapon shipment"

exports['qs-banking']:RemoveGangMoney(accountName, amount, reason)
```

This export is ideal for managing gang expenses in criminal economy systems, ensuring transparent and trackable financial flows for roleplay or balancing purposes.
