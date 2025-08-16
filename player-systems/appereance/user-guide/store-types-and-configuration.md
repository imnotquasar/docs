# Store Types & Configuration

This section explains how to create and customize different types of appearance-related stores in your server, such as clothing shops, barber shops, tattoo parlors, and surgeon clinics. These stores can be placed anywhere in the world and fully configured through simple editable files.

***

## Creating Stores in config/stores.lua <a href="#integration-as-an-example-in-legacyfuel" id="integration-as-an-example-in-legacyfuel"></a>

To add a new store, simply insert a new table inside `config/stores.lua`. Here's an example:

```lua
{
    id = 'store-1',                                   -- Unique store identifier
    type = 'clothing',                                -- Store type: clothing, barber, tattoo, etc.
    coords = vector4(1693.2, 4828.11, 42.07, 188.66), -- Center position of the store
    size = vector3(4, 4, 4),                          -- Size of the box zone (ignored if usePoly is true)
    rotation = 45,                                    -- Box zone rotation
    usePoly = false,                                  -- Set to true to use custom polygon shape
    showBlip = true,                                  -- Whether to show a blip on the map
    -- targetModel = "s_m_m_doctor_01",              -- (Optional) Ped model override
    -- targetScenario = ""                           -- (Optional) Scenario animation override

    points = { -- Used only if usePoly = true
        vector3(1686.90, 4829.83, 42.07),
        vector3(1698.85, 4831.46, 42.07),
        vector3(1700.24, 4817.77, 42.07),
        vector3(1688.36, 4816.29, 42.07)
    }
}

```

Each store must include a unique `id`, a store `type`, coordinates, and size or polygon points depending on how the zone is defined. The `showBlip` flag allows you to control if the store appears on the map.

***

## Adjusting Store Parameters in config/main.lua <a href="#file-with-the-integration-applied" id="file-with-the-integration-applied"></a>

In `config/main.lua`, you can customize pricing and blip settings for each store type:

```lua
Config.ClothingCost = 100    -- Cost to open the clothing shop menu
Config.BarberCost = 100      -- Cost to change hairstyle
Config.SurgeonCost = 100     -- Cost to modify facial structure
Config.TattooCost = 100      -- Cost to apply tattoos
```

You can also control how each store appears on the map through `Config.Blips`:

```lua
Config.Blips = {
    ['clothing'] = {
        Show = true,
        Sprite = 366,
        Color = 47,
        Scale = 0.7,
        Name = 'Clothing Store'
    },
    ['barber'] = {
        Show = true,
        Sprite = 71,
        Color = 0,
        Scale = 0.7,
        Name = 'Barber'
    },
    ['tattoo'] = {
        Show = true,
        Sprite = 75,
        Color = 4,
        Scale = 0.7,
        Name = 'Tattoo Shop'
    },
    ['surgeon'] = {
        Show = true,
        Sprite = 102,
        Color = 4,
        Scale = 0.7,
        Name = 'Plastic Surgeon'
    }
}
```

***

## Ped Models and Target Interaction

In `Config.TargetConfig`, you can define how each type of store looks and behaves in the world, including the ped model, animation scenario, label, icon, and interaction distance:

```lua
Config.TargetConfig = {
    ['clothing'] = {
        label = 'Clothing Store',
        model = 's_f_m_shop_high',
        scenario = 'WORLD_HUMAN_STAND_MOBILE',
        icon = 'fas fa-tshirt',
        distance = 3
    },
    ['barber'] = {
        label = 'Barber Shop',
        model = 's_m_m_hairdress_01',
        scenario = 'WORLD_HUMAN_STAND_MOBILE',
        icon = 'fas fa-scissors',
        distance = 3
    },
    ['tattoo'] = {
        label = 'Tattoo Shop',
        model = 'u_m_y_tattoo_01',
        scenario = 'WORLD_HUMAN_STAND_MOBILE',
        icon = 'fas fa-pen',
        distance = 3
    },
    ['surgeon'] = {
        label = 'Plastic Surgeon',
        model = 's_m_m_doctor_01',
        scenario = 'WORLD_HUMAN_STAND_MOBILE',
        icon = 'fas fa-scalpel',
        distance = 3
    },
    ['clothingroom'] = {
        label = 'Clothing Room',
        model = 'mp_g_m_pros_01',
        scenario = 'WORLD_HUMAN_STAND_MOBILE',
        icon = 'fas fa-sign-in-alt',
        distance = 3
    }
}
```

This flexible system allows you to place interactive stores anywhere in the world, fully themed and customized to your server’s needs.
