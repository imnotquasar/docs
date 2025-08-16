# qs-inventory

This guide explains how to add a new throwable weapon to your inventory system — in this case, a fictional item called **Newspaper**, represented as `weapon_acidpackage`.

{% stepper %}
{% step %}
## Register The Item

**File:** `shared/items.lua`

Add the following entry to register the item in your inventory:

```lua
['weapon_acidpackage'] = {
    ['name'] = 'weapon_acidpackage',
    ['label'] = 'Newspaper',
    ['weight'] = 1000,
    ['type'] = 'weapon',
    ['ammotype'] = nil,
    ['image'] = 'weapon_acidpackage.png',
    ['unique'] = true,
    ['useable'] = false,
    ['description'] = 'A printed or digital publication with news and articles'
}
```
{% endstep %}

{% step %}
## Define The Weapon

**File:** `shared/weapons.lua`

Add the weapon configuration under your weapon list:

```lua
[`weapon_acidpackage`] = {
    name = 'weapon_acidpackage',
    label = 'Newspaper',
    weapontype = 'Throwable',
    ammotype = nil,
    damagereason = 'Died'
}
```
{% endstep %}

{% step %}
## Add To Throwable Config List

**File:** `config.lua`

Add the item name (without the `weapon_` prefix) to the `Config.Throwables` array:

```lua
Config.Throwables = {
    'ball',
    'bzgas',
    'flare',
    'grenade',
    'molotov',
    'pipebomb',
    'proxmine',
    'smokegrenade',
    'snowball',
    'stickybomb',
    'acidpackage' -- << Add this line
}
```
{% endstep %}

{% step %}
## Set Durability Multiplier

**File:** `config.lua`

Define a durability value for the weapon:

```lua
Config.DurabilityMultiplier = {
    weapon_acidpackage = 0.15
}
```
{% endstep %}

{% step %}
## Update Weapon Use Handler

**File:** `client/custom/misc/UseWeapon.lua`

Locate the condition that handles throwable weapons and append the new weapon name to the check:

```lua
elseif weaponName == 'weapon_stickybomb' or weaponName == 'weapon_pipebomb' or weaponName == 'weapon_smokegrenade' or weaponName == 'weapon_flare' or weaponName == 'weapon_proxmine' or weaponName == 'weapon_ball' or weaponName == 'weapon_molotov' or weaponName == 'weapon_grenade' or weaponName == 'weapon_bzgas' or weaponName == 'weapon_acidpackage' then
```

> 🔧 This ensures the weapon is properly detected and handled as a throwable item in gameplay.
{% endstep %}

{% step %}
## Add The Item Icon

Make sure you place the corresponding image file:

```
html/images/items/weapon_acidpackage.png
```

This will allow the icon to display correctly in the inventory UI.
{% endstep %}
{% endstepper %}
