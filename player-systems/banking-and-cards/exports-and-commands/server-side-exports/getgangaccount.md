# GetGangAccount

The `GetGangAccount` export retrieves detailed information about a specific gang bank account using its name. This includes current balance and other related data. It’s useful for managing and displaying gang finances in scripts involving criminal activities or gang systems.

***

## How to Use

To get data from a gang account, pass the account name:

```lua
-- Example usage:
local accountName = "ballas_account"
local gangAccountData = exports['qs-banking']:GetGangAccount(accountName)

if gangAccountData then
    print("Gang balance: " .. gangAccountData.balance)
else
    print("Gang account not found")
end
```

This export is ideal for gang management systems, heist scripts, or any feature requiring real-time access to shared criminal funds.
