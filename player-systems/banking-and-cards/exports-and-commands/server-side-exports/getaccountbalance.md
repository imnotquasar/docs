# GetAccountBalance

The `GetAccountBalance` export returns the current balance of a specified bank account by its name. It’s a quick and efficient way to retrieve just the numeric balance without extra account metadata.

***

## How to Use

To get the balance of an account, pass the account name:

```lua
-- Example usage:
local accountName = "police_funds"
local balance = exports['qs-banking']:GetAccountBalance(accountName)

print("Current balance: $" .. balance)
```

This export is ideal for scripts that need to check an account's available funds before proceeding with purchases, payouts, or resource checks.
