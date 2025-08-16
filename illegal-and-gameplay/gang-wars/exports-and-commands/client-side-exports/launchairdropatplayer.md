# LaunchAirdropAtPlayer

The `LaunchAirdropAtPlayer` export allows you to spawn an airdrop directly at the player's location. This is useful for creating immersive gameplay events or rewarding players in specific scenarios.

***

## How to Use

To launch an airdrop at the player's location, use the following code:

```lua
if exports['qs-gangwars']:LaunchAirdropAtPlayer() then
    print("Airdrop has been launched at the player's location")
end
```

This will trigger an airdrop at the current position of the player. You can use this functionality to add custom events, such as loot rewards, in-game objectives, or any scenario that requires dynamic item drops near players.
