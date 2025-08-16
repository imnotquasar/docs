# CreateGangAccount

The `CreateGangAccount` export creates a shared bank account for a gang or criminal group. You define the account's name and its initial balance. This is useful for systems where gangs manage shared money for operations like drug trafficking, weapon purchases, or laundering.

***

## How to Use

To create a gang account, pass the account name and starting balance:

```lua
-- Replace with the gang account name and starting balance
local accountName = "ballas_account"
local accountBalance = 30000

exports['qs-banking']:CreateGangAccount(accountName, accountBalance)
```

This export is ideal for criminal roleplay systems that include gangs, mafias, or cartels needing centralized and trackable funds.
