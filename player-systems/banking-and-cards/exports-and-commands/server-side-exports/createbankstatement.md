# CreateBankStatement

The `CreateBankStatement` export logs a transaction into a player's bank account history. It includes the transaction amount, reason, type (deposit, withdrawal, etc.), and account type (personal, job, gang). This is useful for keeping an accurate record of player or faction financial activity.

***

## How to Use

To add a new statement entry, provide the player's source ID, account name, amount, transaction reason, statement type, and account type:

```lua
-- Example usage:
local playerId = 1 -- Source ID of the player
local account = "personal_main"
local amount = 1500
local reason = "Vehicle purchase"
local statementType = "withdraw" -- "deposit" or "withdraw"
local accountType = "personal" -- "personal", "job", or "gang"

exports['qs-banking']:CreateBankStatement(playerId, account, amount, reason, statementType, accountType)
```

This export is ideal for systems that need detailed transaction logs for audits, UIs, or admin monitoring tools.
