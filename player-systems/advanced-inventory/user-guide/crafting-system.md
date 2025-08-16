# Crafting system

The Quasar Advanced Inventory crafting system is very complete, it includes multiple functions to make it extremely customizable.

***

## Basic use of crafting <a href="#basic-use-of-crafting" id="basic-use-of-crafting"></a>

Enter the config folder to see the crafting.lua file, where you will find multiple crafting examples and general explanations about this system.

This is a basic example taken from config/crafting.lua as an example of use:

```lua
[1] = {
    name = "weapon_pistol", -- Item you craft
    amount = 50, -- Quantity available, place what you want
    info = {}, -- Ignore this if you don't know the qb info
    costs = {
        ["iron"] = 80, -- These are the dependency items for the craft
        ["metalscrap"] = 120,
        ["rubber"] = 8,
        ["steel"] = 133,
        ["lockpick"] = 5,
    },
    type = "weapon", -- Put if it is 'item' or 'weapon'
    slot = 1, -- This is the slot inside crafting, keep order
    rep = 'attachmentcraftingrep', -- Type of reputation, read above its configuration (qb only)
    points = 1,
    threshold = 0, -- Points that you will receive when crafting, is reputation (qb only)
    time = 5500, -- Progress bar time
    chance = 100 -- Chance of breaking, 1-100 (100 imposible breaking)
},
```

***

## Integration into external assets <a href="#integration-into-external-assets" id="integration-into-external-assets"></a>

This integration requires basic programming knowledge, do not proceed if you do not have it or a trusted developer to help you.

With this event we give an example of how to add custom crafting to your other assets, you can modify everything to make it perfect for your other asset.

```lua
function OpenCrafting()
    local CustomCrafting = {
        [1] = {
            name = 'weapon_pistol',
            amount = 50,
            info = {},
            costs = {
                ['tosti'] = 1,
            },
            type = 'weapon',
            slot = 1,
            rep = 'attachmentcraftingrep',
            points = 1,
            threshold = 0,
            time = 5500,
            chance = 100
        },
        [2] = {
            name = 'water_bottle',
            amount = 1,
            info = {},
            costs = {
                ['tosti'] = 1,
            },
            type = 'item',
            slot = 2,
            rep = 'attachmentcraftingrep',
            points = 1,
            threshold = 0,
            time = 8500,
            chance = 100
        },
    }

    local crafting = {
        label = 'Craft',
        items = exports['qs-inventory']:SetUpCrafing(CustomCrafting)
    }
    TriggerServerEvent('inventory:server:SetInventoryItems', CustomCrafting)
    TriggerServerEvent('inventory:server:OpenInventory', 'customcrafting', crafting.label, crafting)
end
```
