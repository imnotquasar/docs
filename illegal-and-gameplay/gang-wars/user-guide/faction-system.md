# Faction system

Here you can select the zones available for conquest, remember that you must add the name of the job or gang and then add the color of the zone.

***

## Basic configuration of Blips and Factions <a href="#basic-configuration-of-blips-and-factions" id="basic-configuration-of-blips-and-factions"></a>

Each zone will consist of three zones of collectable drugs, if you are the leader of a zone, you will farm twice as much, you will have to configure everything in CircleZones, but please, keep in mind that you cannot add more, so there are only 3 zones.

To do this we will go to config.lua in Config.DropBlipColors, and add the jobs along with a color that we choose in the [https://docs.fivem.net/docs/game-references/blips/](https://docs.fivem.net/docs/game-references/blips/).

```lua
Config.DropBlipColors = { -- Colors: https://docs.fivem.net/docs/game-references/blips/
    ['realestate'] = 39,
    ['ambulance'] = 38,
    ['lostmc'] = 39,
    ['ballas'] = 38,
    -- ['example'] = color,
}
```
