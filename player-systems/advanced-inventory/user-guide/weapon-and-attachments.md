# Weapon and Attachments

{% hint style="danger" %}
For this section, if you do not have the minimum knowledge, or an experienced developer, avoid modifying or integrating custom weapons to your server to avoid errors, or problems with the advancedinventory resource, with this we make clear that a support will not help you to configure a section like this to your server.
{% endhint %}

{% hint style="info" %}
Both esx and qbcore will use config/weapons.lua, since this advancedinventory is not compatible with external weapon assets such as qb-weapons or other similar ones.
{% endhint %}

This guide will help you set up new weapons, specifying the characteristics of each and adding attachments or tints in a standardized manner.

<figure><img src="../../../.gitbook/assets/ezgif-4-7b3ec8e912 (1).gif" alt=""><figcaption></figcaption></figure>

***

## Basic Weapon Configuration <a href="#basic-weapon-configuration" id="basic-weapon-configuration"></a>

To add a weapon, define it in two main files:

* **`items.lua`**: Defines the general properties of the weapon.
* **`weapons.lua`**: Defines additional details such as ammo type and in-game name.

**Example Configuration in items.lua:**

```lua
['weapon_pistol'] = {
    name = 'weapon_pistol',
    label = 'Pistol',
    weight = 1000,
    type = 'weapon',
    ammotype = 'AMMO_PISTOL',
    image = 'weapon_pistol.png',
    unique = true,
    useable = false,
    rare = 'common', -- Options: common, epic, legendary
    description = 'A basic handgun for self-defense.'
},
```

* **`name`**: Internal name of the weapon.
* **`label`**: Display name in the game.
* **`weight`**: Weight in the inventory.
* **`type`**: Defines it as a weapon.
* **`ammotype`**: Type of ammunition.
* **`image`**: Image file name.
* **`unique`**: Determines if the weapon is unique.
* **`rare`**: Rarity level.
* **`description`**: Brief description of the weapon.

**Example Configuration in weapons.lua:**

```lua
[`weapon_pistol`] = {
    name = 'weapon_pistol',
    label = 'Pistol',
    weapontype = 'Pistol',
    ammotype = 'AMMO_PISTOL',
    damagereason = 'Shot'
},
```

* **`name`** and **`label`** as in `items.lua`.
* **`weapontype`**: Specific weapon type.
* **`ammotype`**: Type of ammunition.
* **`damagereason`**: Description of the damage caused.

***

## Attachment Configuration <a href="#attachment-and-tint-configuration" id="attachment-and-tint-configuration"></a>

**Naming Conventions to maintain consistency:**

* **Attachments** should follow the format `weapon_attachment`. Example: `pistol_suppressor`.
* **Tints** (colors) should follow the format `color_weapontint`. Example: `black_weapontint`.

**Example Attachment Configuration for WEAPON\_PISTOL:**

```lua
Config.WeaponAttachments = {
    ["WEAPON_PISTOL"] = {
        defaultclip = { component = 'COMPONENT_PISTOL_CLIP_01', item = 'pistol_defaultclip' },
        extendedclip = { component = 'COMPONENT_PISTOL_CLIP_02', item = 'pistol_extendedclip' },
        flashlight = { component = 'COMPONENT_AT_PI_FLSH', item = 'pistol_flashlight' },
        suppressor = { component = 'COMPONENT_AT_PI_SUPP_02', item = 'pistol_suppressor' }
    }
}
```

Each attachment has:

* **`component`**: In-game identifier.
* **`item`**: Attachment name in the inventory, following the format `weapon_attachment`.

**Example Attachments:**

* **defaultclip**: Standard weapon clip.
* **extendedclip**: Extended clip.
* **flashlight**: Flashlight for illumination.
* **suppressor**: Silencer to reduce noise.

**You must add these attachments in Config.WeaponAttachmentItems as this example shows:**

```lua
Config.WeaponAttachmentItems = {
    -- Rifles
    {
        item = 'rifle_suppressor',
        attachment = 'suppressor',
        type = 'suppressor'
    },
    {
        item = 'rifle_smallscope',
        attachment = 'smallscope',
        type = 'scope'
    },
}
```

***

## Weapon Durability Configuration <a href="#weapon-durability-configuration" id="weapon-durability-configuration"></a>

To customize durability, use `Config.DurabilityMultiplier` where higher values represent faster degradation.

**Example Durability Configuration:**

```lua
Config.DurabilityMultiplier = {
    weapon_pistol = 0.15, -- Durability for pistols
    weapon_smg = 0.15,    -- Durability for SMGs
    weapon_rifle = 0.10,  -- Durability for rifles
}
```

***

## Weapon Repair Configuration <a href="#weapon-repair-configuration" id="weapon-repair-configuration"></a>

You can set repair points where players repair weapons for a fee.

**Example Repair Point Configuration:**

```lua
Config.WeaponRepairPoints = {
    [1] = { coords = vector3(964.02, -1267.41, 34.97), IsRepairing = false, RepairingData = {} }
}

Config.WeaponRepairCosts = {
    pistol = 1000, -- Repair cost for pistols
    rifle = 5000,  -- Repair cost for rifles
    shotgun = 3000 -- Repair cost for shotguns
}
```
