# Spawn Selector

This version includes a fully integrated **spawn selector system**, which works out of the box with the basic installation of Multicharacter.&#x20;

Players can easily select their desired spawn location from the menu.

{% stepper %}
{% step %}
### Disable the Spawn Selector

You can disable the system by setting Config.EnableDefaultSpawnSelector to false in the configuration file.
{% endstep %}

{% step %}
### Compatibility with qb-apartments

The spawn selector is compatible with **qb-apartments** by default, provided the corresponding line in the fxmanifest.lua file is uncommented. Adjust this line as necessary for your server setup.
{% endstep %}
{% endstepper %}

***

## Configure, Edit, or Add More Locations

Quasar Multicharacter includes a spawn selector system that allows players to choose their spawn location dynamically. You can edit, add, or remove spawn locations using the configuration provided. If something goes wrong, revert your changes or consult a trusted developer for assistance.

Here’s an example of the default configuration for spawn locations:

```lua
Config.Spawns = {
    [1] = {
        camCoords = vector3(1151.57, -627.64, 65.27),
        spawnCoords = vector4(1127.14, -645.29, 55.79, 281.89),
        label = 'Mirror Park',
        address = 'Mirror Park Blvd',
    },
    [2] = {
        camCoords = vector3(-1011.8, -2714.38, 23.61),
        spawnCoords = vector4(-1037.8, -2737.82, 19.17, 325.98),
        label = 'Airport',
        address = 'New Empire Way',
    },
    [3] = {
        camCoords = vector3(-1249.22, -1469.2, 10.6),
        spawnCoords = vector4(-1265.34, -1481.28, 3.33, 286.73),
        label = 'Beach',
        address = 'Aguja St.',
    },
    [4] = {
        camCoords = vector3(1113.8, 2680.31, 46.42),
        spawnCoords = vector4(1138.84, 2672.44, 37.13, 89.32),
        label = 'Sandy Shores',
        address = 'Route 68',
    },
    [5] = {
        camCoords = vector3(176.68, 6555.92, 43.24),
        spawnCoords = vector4(159.59, 6587.62, 31.12, 187.2),
        label = 'Paleto Bay',
        address = 'Great Ocean Hwy',
    }
}
```
