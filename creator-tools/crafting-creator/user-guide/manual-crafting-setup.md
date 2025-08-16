# Manual Crafting Setup

{% hint style="success" %}
If you're looking for the automatic placement system, please refer to the next section of the documentation.
{% endhint %}

This guide explains how to manually create crafting tables in **Quasar Crafting Creator** using code. This method is ideal for developers who prefer full control over placement, job restrictions, and recipe management directly from the configuration files.

***

## Configuration Example

All crafting tables are defined inside the `Config.CraftingTables` array. Each table can have its own location, object model, job requirements, access levels, and crafting recipes.

This method gives you full customization over:

* The crafting bench object used in the world.
* The area where players can interact with it.
* Job and grade-based access.
* Items available to craft and their required materials.
* Crafting time, level requirements, and experience earned.

```lua
Config.CraftingTables = {
    {
        id = 'craft-1',                                -- Unique identifier (must be different for each table)
        label = 'Item Crafting Bench',                 -- UI label
        coords = vec4(209.40, -753.70, 46.07, 252.28), -- Table position and heading
        size = 5.0,                                    -- Interaction radius
        object = 'gr_prop_gr_bench_02b',               -- Prop model
        job = 'police',                                -- Required job (nil = public)
        grades = {1, 2, 3},                            -- Allowed grades (nil = all grades)
        recipes = {
            {
                name = 'weapon_pistol',                -- Item to craft
                duration = 700,                        -- Crafting time (ms)
                price = 0,                             -- Price (optional)
                level = 15,                            -- Required crafting level
                earn = 0,                              -- XP gained after crafting
                ingredients = {
                    steel = 80,
                    aluminum = 60,
                    rubber = 20
                }
            },
            -- Add more recipes here
        }
    },
    {
        id = 'craft-2',
        label = 'Attachment Crafting Bench',
        coords = vec4(217.83, -731.64, 46.07, 249.44),
        size = 5.0,
        object = 'gr_prop_gr_bench_01b',
        job = nil,               -- Public access
        grades = nil,
        recipes = {
            {
                name = 'pistol_extendedclip',
                duration = 450,
                price = 0,
                level = 4,
                earn = 10,
                ingredients = {
                    metalscrap = 165,
                    steel = 285,
                    rubber = 75
                }
            }
            -- More recipes...
        }
    }
}
```

***

## Object & Camera Offsets

Each crafting object may require adjustments for correct positioning and camera perspective. These offsets are configured using `Config.ObjectOffsets`.

```lua
Config.ObjectOffsets = {
    ['gr_prop_gr_bench_02b'] = {
        camera = vec3(-1.5, 0.0, 1.5),       -- Camera angle during crafting
        object = vec3(0.0, 0.0, 1.4)         -- Object elevation offset
    },
    ['gr_prop_gr_bench_01b'] = {
        camera = vec3(-1.5, 0.0, 1.5),
        object = vec3(0.0, 0.0, 1.4)
    }
}
```

If you use a custom object, simply add it to this table with the proper offsets.
