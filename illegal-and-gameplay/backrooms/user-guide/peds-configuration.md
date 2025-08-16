# Peds Configuration

Quasar Backrooms allows you to add different Peds entities to give a fresh touch during casual use of this asset, you can manipulate this system completely or add new ones.

***

## Basic Peds configuration <a href="#airdrop-basic-configuration" id="airdrop-basic-configuration"></a>

Here you have the peds section, this section contains the peds provided in the download file together with the script, here you have the respawn distance of the ped on the player, in addition to the damage per second. These values are modifiable but be careful if you don't know what you are doing.

```lua
Config.Ped = {
    models = { -- NPC models that spawn in backrooms
        `QS_173`,
        `QS_doctor`,
        `QS_stealer`,
        `QS_bacteria`,
        `QS_096`,
        `QS_ATC`,
    },
    spawn = vec4(1787.62, -284.21, 20.86, 339.31), -- Ignore
    respawnDistance = 8.5, -- Distance to respawn if you move away from it
    damageDistance = 3.5 -- Distance to take damage per second
}
```
