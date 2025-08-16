# AddMoney

The `AddMoney` export adds a specified amount of money to a bank account, optionally including a reason for the transaction. This is useful for rewarding jobs, missions, or scripted events that require deposits into job, gang, or personal accounts.

***

## How to Use

To deposit funds into an account, pass the account name, the amount to add, and an optional reason:

```lua
-- Example usage:
local accountName = "mechanic_funds"
local amount = 2000
local reason = "Job payout"

exports['qs-banking']:AddMoney(accountName, amount, reason)
```

This export is ideal for scripted systems that automate income, such as completed tasks, job rewards, or scheduled payments.
