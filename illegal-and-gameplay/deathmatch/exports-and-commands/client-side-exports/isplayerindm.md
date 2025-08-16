# IsPlayerInDM

The `IsPlayerInDM` export allows you to check if a player is currently participating in a Deathmatch session. This is useful for managing or restricting specific actions while the player is engaged in a Deathmatch.

***

## How to Use

To check whether the player is in a Deathmatch session, use the following code:

```lua
if exports['qs-deathmatch']:IsPlayerInDM() then
    print("Player is in a Deathmatch match")
end
```

This will return a boolean value (`true` or `false`) indicating whether the player is actively in a Deathmatch. You can use this information to implement custom logic, such as disabling specific features, triggering events, or providing Deathmatch-specific functionality during the session.
