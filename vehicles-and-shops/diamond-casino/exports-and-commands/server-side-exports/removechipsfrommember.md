# RemoveChipsFromMember

The `RemoveChipsFromMember` export allows you to remove a specified amount of casino chips from a player. This is useful for enforcing betting losses, withdrawals, or other casino-related transactions.

***

## How to Use

To remove chips from a player, use the following code:

```lua
local chipAmount = 50 -- Replace with the amount of chips to remove

exports['qs-diamondcasino']:RemoveChipsFromMember(source, chipAmount)
print("Removed " .. chipAmount .. " chips from player with ID " .. source)
```

This export requires the player's ID and the number of chips to deduct. It automatically processes the transaction and logs the action, making it an efficient way to manage casino chips.
