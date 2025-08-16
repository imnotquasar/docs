# GetAccount

The `GetAccount` export retrieves detailed information about a specific bank account using its name. This includes current balance and other metadata. It’s useful for scripts that need to display or validate account data before performing operations.

***

## How to Use

To fetch data from an account, simply pass the account name:

```lua
-- Example usage:
local accountName = "gang_vagos"
local accountData = exports['qs-banking']:GetAccount(accountName)

if accountData then
    print("Current balance: " .. accountData.balance)
else
    print("Account not found")
end
```

This export is ideal for scripted systems that automate income, such as completed tasks, job rewards, or scheduled payments.
