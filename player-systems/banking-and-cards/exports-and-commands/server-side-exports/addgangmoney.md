# AddGangMoney

The `AddGangMoney` export adds funds directly to a gang's shared bank account. You specify the account name, the amount to deposit, and an optional reason for the transaction. This is useful for scripts that reward gangs for activities like robberies, drug deals, or territory control.

***

## How to Use

To deposit money into a gang account, pass the account name, amount, and an optional reason:

```lua
-- Example usage:
local accountName = "vagos_account"
local amount = 5000
local reason = "Territory payout"

exports['qs-banking']:AddGangMoney(accountName, amount, reason)
```

This export is ideal for criminal roleplay mechanics that automate income for gangs or factions, maintaining a clean transaction history.
