# CreatePlayerAccount

The `CreatePlayerAccount` export creates a new bank account for a player with a specified name, initial balance, and list of authorized users. This is useful for initializing custom accounts such as business or shared accounts within your banking system.

***

## How to Use

To create a new bank account for a player, pass their source ID, the desired account name, starting balance, and a table of authorized users:

```lua
-- Replace the values accordingly
local playerId = 1 -- Player's source ID
local accountName = "business_main"
local accountBalance = 10000
local accountUsers = {1, 2, 3} -- Source IDs of other authorized users

exports['qs-banking']:CreatePlayerAccount(playerId, accountName, accountBalance, accountUsers)
```

This export is ideal for creating custom bank accounts such as business wallets, gang funds, or faction accounts that multiple users can access.
