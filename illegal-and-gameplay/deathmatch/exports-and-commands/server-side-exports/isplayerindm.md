# IsPlayerInDM

The `IsPlayerInDM` export allows you to check if a specific player (identified by their source) is currently participating in a Deathmatch. This is useful for managing gameplay logic or triggering specific events for players in active matches.

***

## **How to Use**

To check if a player is in a Deathmatch, use the following code:

```lua
if exports['qs-deathmatch']:IsPlayerInDM(source) then
	print('Player: ' .. source .. ' is in a Deathmatch match')
end
```

This allows for custom logic to be applied based on the player's status, such as restricting access to certain features or logging their participation.
