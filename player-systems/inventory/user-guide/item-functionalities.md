# Item functionalities

{% hint style="warning" %}
If you need assistance, please reach out to a developer, as the setup for "Basic Item Declaration" is designed to be straightforward. However, if any difficulties arise, it’s best to consult a trusted developer to ensure a smooth integration.
{% endhint %}

To correctly set up items in qs-inventory, follow these instructions and examples. Note that this file is compatible with **ESX**. If using **QBCore**, move this file to `qb-core/shared` and rename the main function accordingly.

The items will be added in different locations depending on whether you are using **QBCore** or **ESX**. Please navigate to the recommended directory for your framework and then follow the guidelines provided below.

{% stepper %}
{% step %}
### Items for ESX

Items are located in **qs-inventory/shared/items.lua**.
{% endstep %}

{% step %}
### Items for QBCore

Items should be added in **qb-core/shared/items.lua**.
{% endstep %}
{% endstepper %}

***

## Basic Item Declaration <a href="#basic-item-declaration" id="basic-item-declaration"></a>

Each item has essential properties that determine its behavior. Here are the primary fields for setup:

* **name**: Unique ID for the item.
* **label**: Display name in the inventory.
* **weight**: Weight of the item in kg.
* **type**: Item type (`item` or `weapon`).
* **image**: Name of the image file in `html/images/`.
* **unique**: `true` if the item is non-stackable; `false` if it can stack.
* **useable**: `true` if the item can be used.
* **shouldClose**: `true` if the inventory should close when the item is used.
* **description**: Short description of the item.

Example:

```lua
['water_bottle'] = {
    name = 'water_bottle',
    label = 'Water Bottle',
    weight = 500,
    type = 'item',
    image = 'water_bottle.png',
    unique = false,
    useable = true,
    shouldClose = true,
    description = 'A refreshing bottle of water.'
}
```

***

## Decay (Wear and Tear) <a href="#decay-wear-and-tear" id="decay-wear-and-tear"></a>

Certain items degrade with use.

* **decay**: Sets the rate of wear. The higher the value, the faster it wears out.
* **delete**: `true` to remove the item when it breaks.

Wear and Tear Example:

```lua
['lockpick'] = {
    name = 'lockpick',
    label = 'Lockpick',
    weight = 150,
    type = 'item',
    image = 'lockpick.png',
    unique = true,
    useable = true,
    decay = 10,
    delete = true,
    description = 'A lockpick used for opening locked doors or vehicles.'
}
```

***

## Visible Object <a href="#visible-object" id="visible-object"></a>

If you don't have an item set, it will show a simple bag.

This will set a specific prop, when giving the item, throwing it or doing throw, this item will be seen in the game. You can configure an item to be thrown as an object.

* **object**: Model of the object that will be thrown.

Throwable Object Example:

```lua
['snowball'] = {
    name = 'snowball',
    label = 'Snowball',
    weight = 100,
    type = 'item',
    image = 'snowball.png',
    unique = false,
    useable = true,
    object = 'prop_snowball_01',
    description = 'A snowball to throw at your friends!'
}
```

***

## Item Rarity <a href="#item-rarity" id="item-rarity"></a>

The rarity of an item changes the color of the item in the inventory.

* **rare**: Sets the item rarity (`common`, `epic`, `legendary`), which only affects the color of the item in the inventory.

Rarity Example:

```lua
['gold_chain'] = {
    name = 'gold_chain',
    label = 'Gold Chain',
    weight = 300,
    type = 'item',
    image = 'gold_chain.png',
    unique = true,
    useable = false,
    rare = 'epic',
    description = 'A valuable gold chain.'
}
```

***

## Job Restricted Item

If you set a job, only players with that job will be able to use or receive this item. You can define one or multiple jobs.

* `job`: A table containing the job names allowed to use the item.

**Job Restricted Object Example:**

```lua
['radar_gun'] = {
    name = 'radar_gun',
    label = 'Radar Gun',
    weight = 1000,
    type = 'item',
    image = 'radar_gun.png',
    unique = true,
    useable = true,
    object = 'prop_radar_gun_01',
    job = { 'police' },
    description = 'A device used by police to measure vehicle speed.'
}
```

***

## Object with export <a href="#object-with-export" id="object-with-export"></a>

We can add a client export as follows.

* **export:** Sets an export as usability.

Export Example:

```lua
['security_card_02'] = {
    name = 'security_card_02',
    label = 'Security Card B',
    weight = 5,
    type = 'item',
    image = 'security_card_02.png',
    unique = true,
    useable = true,
    description = 'A security card... I wonder what it goes to',
    client = {
        export = 'qs-inventory.test'
    },
}
```

Internal Export Example:

```lua
exports('test', function(item, meta)
    print('item', json.encode(item))
    print('meta', json.encode(meta))
end)
```

***

## Consumables <a href="#consumables" id="consumables"></a>

Please if you are not an experienced programmer, just skip this step and continue adding your consumable items in esx\_basicneeds or qb-smallresources.

For this to work in esx we must have esx\_status and esx\_basicneeds.

Consumable items can affect thirst or hunger and may include animations, visible objects, and movement restrictions.

* **thirst/hunger**: Defines whether it affects thirst or hunger.
* **usetime**: Duration of use in ms.
* **anim**: Animation dictionary and clip.
* **prop**: Model and coordinates of the object during the animation.
* **disable**: Disables events (movement, combat, etc.).
* **removeAfterUse**: `true` deletes the item after use.

Consumable Example:

```lua
['tosti'] = {
        ['name'] = 'tosti',
        ['label'] = 'Grilled Cheese Sandwich',
        ['weight'] = 200,
        ['type'] = 'item',
        ['image'] = 'tosti.png',
        ['unique'] = false,
        ['useable'] = true,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'Nice to eat',
        ['created'] = nil,
        ['decay'] = 0.07,
        ['delete'] = false,
        ['object'] = 'prop_sandwich_01',
        ['useableIn'] = 'wallet',
        ['client'] = {
            status = {
                hunger = 200000,
            },
            usetime = 2500,
            anim = {
                dict = 'mp_player_inteat@burger',
                clip = 'mp_player_int_eat_burger_fp'
            },
            prop = {
                model = 'prop_cs_burger_01',
                pos = vec3(0.02, 0.02, -0.02),
                rot = vec3(0.0, 0.0, 0.0),
                bone = 60309 -- Bone here
            },
            -- multiple prop
            -- prop = {
            --     {
            --         model = 'prop_cs_burger_01',
            --         pos = vec3(0.02, 0.02, -0.02),
            --         rot = vec3(0.0, 0.0, 0.0)
            --     },
            --     {
            --         model = 'prop_cs_burger_01',
            --         pos = vec3(0.1, 0.02, -0.02),
            --         rot = vec3(0.0, 0.0, 0.0)
            --     }
            -- },
            disable = {
                move = true,
                car = true,
                mouse = false,
                combat = true,
            },
            removeAfterUse = true
        }
    },
```

***

## Using Multiple Props

You can also attach **more than one prop** to an item during its usage animation. This is useful for complex or layered items (e.g., a sandwich and a drink, or two utensils).

To use multiple props, define them in a table under the `client.prop` field. Each entry must include a `model`, `pos`, and `rot`.

Example with Multiple Props:

```lua
luaCopiarEditar['tosti'] = {
    name = 'tosti',
    label = 'Grilled Cheese Sandwich',
    weight = 200,
    type = 'item',
    image = 'tosti.png',
    unique = false,
    useable = true,
    shouldClose = true,
    combinable = nil,
    description = 'Nice to eat',
    decay = 0.07,
    delete = false,
    object = 'prop_sandwich_01',
    useableIn = 'wallet',
    client = {
        status = {
            hunger = 200000,
        },
        usetime = 2500,
        anim = {
            dict = 'mp_player_inteat@burger',
            clip = 'mp_player_int_eat_burger_fp'
        },
        prop = {
            {
                model = 'prop_cs_burger_01',
                pos = vec3(0.02, 0.02, -0.02),
                rot = vec3(0.0, 0.0, 0.0)
            },
            { -- New prop added here
                model = 'prop_cs_burger_01',
                pos = vec3(0.1, 0.02, -0.02),
                rot = vec3(0.0, 0.0, 0.0)
            }
        },
        disable = {
            move = true,
            car = true,
            mouse = false,
            combat = true,
        },
        removeAfterUse = true
    }
}
```

This setup allows both props to appear during the animation, giving a more immersive and detailed experience.

***

## Disable Throw

If you want to prevent a specific item from being thrown, you can use the `disableThrow` property.

When set to `true`, this will disable the throw action for that item, even if it has a visible object assigned. This is useful for heavy or dangerous items that shouldn't be throwable.

* `disableThrow`: Set to `true` to prevent the item from being thrown.

Non-Throwable Object Example:

```lua
['brick'] = {
    name = 'brick',
    label = 'Brick',
    weight = 500,
    type = 'item',
    image = 'brick.png',
    unique = false,
    useable = true,
    object = 'prop_brick_01',
    disableThrow = true, -- Here you can add or remove throw!
    description = 'A heavy brick. Probably not safe to throw.'
}
```

If `disableThrow` is not set or is set to `false`, the item will behave normally and can be thrown if a prop is assigned. By default, all items are throwable unless you prevent it.

***

## Object Drop Rotation

The `objectRotation` property is used to define how a dropped object appears in the game world by adjusting its rotation. This ensures that items are visually aligned correctly when placed on the ground, avoiding awkward angles or unnatural positioning.

* **objectRotation**: Accepts a `vec3(x, y, z)` value representing the rotation in degrees on each axis:
  * **X**: Tilts the object forward or backward.
  * **Y**: Rotates the object side to side.
  * **Z**: Spins the object horizontally (like turning a coin on a table).

This is especially useful for props that look odd when dropped with default rotation, such as flat or elongated objects.

```lua
['brick'] = {
    name = 'brick',
    label = 'Brick',
    weight = 500,
    type = 'item',
    image = 'brick.png',
    unique = false,
    useable = true,
    object = 'prop_brick_01',
    objectRotation = vec3(80.0, 60.0, 0.0),
    description = 'A heavy brick. Probably not safe to throw.'
}
```

If `objectRotation` is not defined, the item will use a default rotation, which may cause it to appear misaligned or float awkwardly.
