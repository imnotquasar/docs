# CreateJobAccount

The `CreateJobAccount` export initializes a bank account tied to a specific job or organization. It sets up the account with a given name and starting balance. This is useful for scripts that need to create shared financial accounts for jobs like police, EMS, or mechanic shops.

***

## How to Use

To create a job-linked account, provide the name of the account and the initial balance:

```lua
-- Replace with your job account name and starting balance
local accountName = "police_funds"
local accountBalance = 50000

exports['qs-banking']:CreateJobAccount(accountName, accountBalance)
```

This export is ideal for roleplay servers where factions or jobs need centralized funds, such as police departments, government groups, or business entities.
