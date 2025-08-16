# GetMemberChips

The `GetMemberChips` export allows you to retrieve the number of casino chips a player has. This is useful for managing casino economy systems, such as chip stores, rewards, or betting restrictions based on balance.

***

## How to Use

To get a player's chip balance, use the following code:

```lua
local chips = exports['qs-diamondcasino']:GetMemberChips(source)
print("The player with ID " .. source .. " has " .. chips .. " chips.")
```

This export requires the player's ID as an argument and returns the number of chips they have. It is ideal for integration with other casino systems, such as buying or withdrawing chips.
