# qb-inventory

This guide outlines how to fully integrate a custom throwable weapon — in this case, a newspaper object called `weapon_acidpackage` — into the QBCore ecosystem using `qb-core`, `qb-inventory`, `qb-weapons`, and related modules.

{% stepper %}
{% step %}
## Register The Item

**File:** `qb-core/shared/items.lua`

Add the following entry:

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

> 🧠 Ensure the `image` file matches the item name and is placed in the appropriate image directory (`html/images/items/` or equivalent).
{% endstep %}

{% step %}
## Register The Weapon

**File:** `qb-core/shared/weapons.lua`

Add the following entry:

```lua
[`weapon_acidpackage`] = {
    ['name'] = 'weapon_acidpackage',
    ['label'] = 'Newspaper',
    ['weapontype'] = 'Throwable',
    ['ammotype'] = nil,
    ['damagereason'] = 'Died'
}
```
{% endstep %}

{% step %}
## Enable Weapon HUD Display

**File:** `qb-hud/config.lua`

Add the following line under the weapon list (if not already present):

```lua
[`weapon_acidpackage`] = true
```

> 🎯 This ensures the weapon is visible on the HUD when equipped.
{% endstep %}

{% step %}
## Mark It As Throwable



**File:** `qb-weapons/config.lua`

Add `"acidpackage"` to the `Config.Throwables` array (without the `weapon_` prefix):

```lua
Config.Throwables = {
    "ball",
    "bzgas",
    "flare",
    "grenade",
    "molotov",
    "pipebomb",
    "proxmine",
    "smokegrenade",
    "snowball",
    "stickybomb",
    "acidpackage" -- << Add this
}
```

> 🪃 This flag ensures the weapon is handled as a throwable in weapon logic.
{% endstep %}
{% endstepper %}
