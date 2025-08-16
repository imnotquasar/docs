# Create Gangs and Zones

Quasar Gangs & Territories is a versatile system for managing gangs, territories, and zones. It allows you to create gangs and assign them personal territories that are fully configurable in the `config.lua` file. These territories include unique zones for storage, a garage, and a boss menu, giving each gang their own distinct areas and features.

***

## Key Notes on Gang and Territory Creation <a href="#how-do-i-make-the-race-competitive" id="how-do-i-make-the-race-competitive"></a>

{% stepper %}
{% step %}
### Neutral and None Gangs

Do not delete the `none` or `neutral` gang configurations. The `none` gang is used for players without gang affiliation, while the `neutral` gang represents free or unclaimed territories.
{% endstep %}

{% step %}
### Gang-Specific Territories

Each gang's territory will be visible only to its members and is fully customizable. This includes defining RGB colors for gang identification, blip colors for territories, and the coordinates for each gang's actions.
{% endstep %}
{% endstepper %}

***

## Example Gang Configuration

In the `Config.Gangs` table, you can define gangs as follows:

```lua
Config.Gangs = {
    ['none'] = {}, -- Default for unaffiliated players

    ['neutral'] = { 
        ['territoryColor'] = 55, -- Default color for neutral territory
    },

    ['ballas'] = { -- Gang ID
        ['label'] = 'Ballas', -- Gang name
        ['color'] = { 151, 8, 120 }, -- Gang RGB color
        ['territoryColor'] = 27, -- Territory blip color
        ['locations'] = {
            ['boss'] = vector3(114.32, -1961.11, 21.32), -- Boss menu
            ['stash'] = vector3(102.93, -1959.77, 20.82), -- Stash location
            ['vehicles'] = vector3(116.92, -1949.23, 20.72), -- Garage
            ['heading'] = 56.69 -- Heading direction for spawns
        },
        ['blips'] = {
            [1] = { name = 'Ballas Zone', sprite = 84, color = 27, size = 0.6, coords = vector3(108.13, -1941.08, 20.78) }
        },
        ['vehicles'] = {
            { ['model'] = 'avarus', ['label'] = 'Avarus', ['icon'] = 'fas fa-motorcycle' },
            { ['model'] = 'buccaneer2', ['label'] = 'Buccaneer', ['icon'] = 'fas fa-car-alt' }
        }
    },
}
```

***

## Configurable Locations

To configure interactive locations like stash, boss menu, and vehicles, use the `Config.Locations` table. These settings define the help texts and events triggered at each point:

```lua
Config.Locations = {
    ['stash'] = {
        ['help'] = '[E] Open stash',
        ['event'] = 'gangs:openStash'
    },
    ['boss'] = {
        ['help'] = '[E] Open boss menu',
        ['event'] = 'gangs:requestOpenBoss'
    },
    ['vehicles'] = {
        ['help'] = '[E] Open garage',
        ['event'] = 'gangs:vehiclesMenu'
    },
}
```

By fully customizing `config.lua`, you can create a robust gang system with personalized zones, making each gang feel unique and immersive.
