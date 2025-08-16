# GiveChipsToMember

The `GiveChipsToMember` export allows you to add a specified amount of casino chips to a player's account. This is useful for administrative actions, rewards, or promotional events within your casino system.

***

## How to Use

To give chips to a player, use the following code:

```lua
local chipAmount = 100 -- Replace with the amount of chips to add

exports['qs-diamondcasino']:GiveChipsToMember(source, chipAmount)
print("Added " .. chipAmount .. " chips to player with ID " .. source)
```

Internally, the export logs the action (e.g., using a `Debug` function to output details like the identifier and the amount) to help with monitoring and troubleshooting.
