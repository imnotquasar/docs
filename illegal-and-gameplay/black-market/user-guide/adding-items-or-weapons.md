# Adding Items or Weapons

Quasar Black Market allows you to add new items or weapons for players to purchase from the truck. Follow this simple guide to configure and expand the list of available items or weapons:

{% stepper %}
{% step %}
### Locate the Configuration File

Navigate to the configuration file where the BlackMarket table is defined, usually in config/blackmarket.lua.
{% endstep %}

{% step %}
### Add New Items or Weapons

Within the BlackMarket table, locate the Weapon or Item section. Each section contains the configuration for weapons and items, respectively.
{% endstep %}

{% step %}
### Save and Test

* Save your changes to the file.
* Restart your server or use the command to reload the script.
* Check the Black Market truck in-game to confirm the new items or weapons are correctly displayed and functional.
{% endstep %}
{% endstepper %}

***

## Weapon Configuration

To add a new weapon, copy and modify an existing weapon entry.

```lua
{
    coord = {1.0, -0.64, 0.0, 0.0, 0.0, -90.0}, -- Position in the truck
    prop = "w_ar_assaultrifle", -- Prop model for visual display
    name = "weapon_assaultrifle", -- Weapon spawn name
    label = "ASSAULT RIFLE", -- Display name
    price = 1500, -- Price of the weapon
    maxquantity = 1 -- Maximum quantity allowed in inventory
},

```

***

## Item Configuration

To add a new item, copy and modify an existing item entry.

```lua
{
    coord = {0.8, 0.0, 2.0, 0.0, 0.0, 0.0}, -- Position in the truck
    prop = "prop_c4_final", -- Prop model for visual display
    name = "c4", -- Item name
    label = "C4", -- Display name
    price = 1200, -- Price of the item
    maxquantity = 1, -- Maximum quantity allowed in inventory
    desc = "High-powered adhesive explosive, ideal for sabotage and ambushes. Remote detonation for maximum precision and destruction." -- Description
},

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
