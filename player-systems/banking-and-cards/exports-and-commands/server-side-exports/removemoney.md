# RemoveMoney

The `RemoveMoney` export withdraws a specific amount of money from a bank account, optionally including a reason. This is useful for deducting funds due to purchases, fines, service costs, or scripted penalties.

***

## How to Use

To subtract money from an account, pass the account name, the amount to remove, and an optional reason:

```lua
-- Example usage:
local accountName = "business_main"
local amount = 1200
local reason = "Office furniture purchase"

exports['qs-banking']:RemoveMoney(accountName, amount, reason)
```

This export is ideal for shop systems, automated services, or penalties that require securely removing funds from personal, job, or shared accounts.
