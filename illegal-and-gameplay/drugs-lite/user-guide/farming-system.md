# Farming System

Quasar Drugs provides a comprehensive farming system allowing players to collect different types of drugs at various configurable locations. The farming spots, props, and item details can be customized in the config/farm.lua file. Before advancing to selling or laundering, players must first collect the raw materials required for drug production.

{% stepper %}
{% step %}
### Police Requirement

You can set a minimum number of police officers required to be online for drug farming to be possible.
{% endstep %}

{% step %}
### Custom Props

Each drug type uses specific props to represent collectable plants or materials. These props must be placed in the world and tied to corresponding items.
{% endstep %}

{% step %}
### Circle Zones

Use Config.CircleZones to define the farming areas with spawn coordinates for the collectable props.
{% endstep %}
{% endstepper %}

***

## Drug Collection Settings

Customize the farming behavior, including the item name, progress bar time, police requirements, and the quantity of drugs collectable per interaction.

```lua
Config.CollectItems = {
    ['weed'] = {
        prop = 'prop_weed_01',          -- Prop model for weed
        name = 'Weed',                 -- Display name
        item = 'weed',                 -- Item name
        time = 4000,                   -- Collection time in milliseconds
        quantityMin = 1,               -- Minimum amount collected
        quantityMax = 5,               -- Maximum amount collected
        requiredCops = true,           -- Police required to farm
        requiredCopsQuantity = 1       -- Minimum police count
    },
    ['meth'] = {
        prop = 'prop_barrel_exp_01a',  -- Prop model for chemicals
        name = 'Chemicals',            -- Display name
        item = 'chemicals',            -- Item name
        time = 4000,
        quantityMin = 1,
        quantityMax = 5,
        requiredCops = false,
        requiredCopsQuantity = 0
    },
    ['cocaine'] = {
        prop = 'prop_plant_cane_02b',  -- Prop model for cocaine
        name = 'Cocaine',
        item = 'cocaine',
        time = 4000,
        quantityMin = 1,
        quantityMax = 5,
        requiredCops = false,
        requiredCopsQuantity = 0
    }
}
```

***

## Farming Zones

Define farming locations and spawn points for props. These coordinates determine where the plants or resources will appear.

```lua
Config.CircleZones = {
    ['WeedField'] = {
        coords = vector3(1320.04, 1870.26, 90.83), -- Center of the weed field
        SpawnCoords = {                          -- Specific spawn locations for props
            vector3(1320.215, 1870.333, 90.85452),
            vector3(1327.837, 1868.747, 92.27645),
            vector3(1308.948, 1866.706, 88.88728)
            -- Add more coordinates as needed
        }
    },
    ['ChemicalsField'] = {
        coords = vector3(817.46, -3192.84, 5.9),
        SpawnCoords = {
            vector3(814.7153, -3195.444, 5.900818),
            vector3(817.7902, -3200.771, 5.900818)
        }
    },
    ['CocainaField'] = {
        coords = vector3(16.34, 6875.94, 12.64),
        SpawnCoords = {
            vector3(16.33991, 6875.94, 12.63982),
            vector3(20.36974, 6871.238, 13.07422)
        }
    }
}
```

***

## How It Works

This system provides a dynamic and interactive way to introduce drug farming, enabling server owners to control the flow of illegal activities while ensuring balance and immersion.

{% stepper %}
{% step %}
### Spot Detection

Players enter a predefined zone, and props spawn at the specified coordinates.
{% endstep %}

{% step %}
### Collection

Interact with the props to gather items using progress bars and animations.
{% endstep %}

{% step %}
### Police Checks

If enabled, the system verifies the number of police officers online before allowing collection.
{% endstep %}
{% endstepper %}
