# Add custom weapons

Adding custom weapons works almost the same way in **ESX** and **QB-Core**.\
The only difference is where you add the items:

* In **ESX** → `qs-inventory/shared/items.lua` and `qs-inventory/shared/weapons.lua`
* In **QB-Core** → `qb-core/shared/items.lua` and `qb-core/shared/weapons.lua`

Everything else (config, components, images) is the same.&#x20;

As an example, we used [https://github.com/NoobySloth/Custom-Weapons](https://github.com/NoobySloth/Custom-Weapons).

{% embed url="https://youtu.be/1IEDBf9Kj0w?list=PLU9c-BCMnvA7LlzYnmxRAoKmYg0bhprRO" %}

***

## Define the weapon in your inventory config <a href="#modifications-to-esx_identify" id="modifications-to-esx_identify"></a>

Add your weapon and its attachments to `Config.CustomWeapons`:

```lua
-- Example source: https://github.com/NoobySloth/Custom-Weapons/tree/main
-- Also add the weapon to items.lua and weapons.lua (next steps)

Config.CustomWeapons = {
    ['weapon_ak47'] = {
        attachments = {
            defaultclip  = { component = 'COMPONENT_AK47_CLIP_01', item = 'rifle_defaultclip' },
            extendedclip = { component = 'COMPONENT_AK47_CLIP_02', item = 'rifle_extendedclip' },
            suppressor   = { component = 'COMPONENT_AT_AR_SUPP_02', item = 'rifle_suppressor' },
        },
        durability = 0.15
    },
    -- add more weapons here
}
```

***

## Register the weapon as an item (`shared/items.lua`)

Example for `weapon_ak47`:

```lua
['weapon_ak47'] = {
    ['name'] = 'weapon_ak47',
    ['label'] = 'AK-47',
    ['weight'] = 1000,
    ['type'] = 'weapon',
    ['ammotype'] = 'AMMO_RIFLE',
    ['image'] = 'weapon_ak47.png',
    ['unique'] = true,
    ['useable'] = false,
    ['rare'] = 'epic', -- epic, legendary, common
    ['description'] = 'Robust, reliable assault rifle'
},

-- Attachments (if used as items)
['rifle_defaultclip'] = {
    ['name'] = 'rifle_defaultclip',
    ['label'] = 'Rifle Mag (Std)',
    ['weight'] = 200,
    ['type'] = 'item',
    ['image'] = 'rifle_defaultclip.png',
    ['unique'] = false,
    ['useable'] = false,
    ['rare'] = 'common',
    ['description'] = 'Standard rifle magazine'
},
['rifle_extendedclip'] = {
    ['name'] = 'rifle_extendedclip',
    ['label'] = 'Rifle Mag (Ext)',
    ['weight'] = 250,
    ['type'] = 'item',
    ['image'] = 'rifle_extendedclip.png',
    ['unique'] = false,
    ['useable'] = false,
    ['rare'] = 'epic',
    ['description'] = 'Extended rifle magazine'
},
['rifle_suppressor'] = {
    ['name'] = 'rifle_suppressor',
    ['label'] = 'Rifle Suppressor',
    ['weight'] = 150,
    ['type'] = 'item',
    ['image'] = 'rifle_suppressor.png',
    ['unique'] = false,
    ['useable'] = false,
    ['rare'] = 'epic',
    ['description'] = 'Sound suppressor for rifles'
},
```

***

## Provide icons/images

Add these to your inventory UI images folder:

* `weapon_ak47.png`
* `rifle_defaultclip.png`
* `rifle_extendedclip.png`
* `rifle_suppressor.png`

***

## Quick checklist

* ✅ Names match across config, items, and weapons
* ✅ Components exist in your weapon pack
* ✅ Items for attachments (if used) are defined
* ✅ Images are added correctly

That’s it — your custom weapon is ready.
