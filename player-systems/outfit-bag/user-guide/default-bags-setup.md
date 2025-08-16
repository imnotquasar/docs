# Default Bags Setup

Set up permanent outfit bags at specific world locations with pre-configured clothing. Perfect for jobs, factions, or public areas that require default outfits without using menus.

***

## Configuration

Add this structure inside `Config.DefaultBags` to define each custom bag:

```lua
Config.DefaultBags = {
    {
        pos = vector3(441.2, -981.9, 29.7), -- Bag world position

        pedpos = { -- Player position when using the bag
            x = 441.1165,
            y = -981.3917,
            z = 29.6896,
            heading = 180.9981
        },

        outfits = {
            {
                name = "Police Uniform", -- Outfit name shown in menu
                data = {
                    ['arms'] = {item = 30, texture = 0, palette = 0},
                    ['t-shirt'] = {item = 15, texture = 0, palette = 0},
                    ['torso2'] = {item = 55, texture = 0, palette = 0},
                    ['pants'] = {item = 35, texture = 0, palette = 0},
                    ['shoes'] = {item = 25, texture = 0, palette = 0},
                    ['hat'] = {item = 46, texture = 0},
                    ['glass'] = {item = 5, texture = 0},
                    -- Add any additional components if needed
                }
            }
        },

        jobs = { "police" }, -- Allowed jobs (optional)
        public = false -- Set to true to make it accessible for everyone
    }
}
```

***

## Clothing Data Structure

Each outfit contains complete clothing information organized by component.

### 🧍‍♂️ Main Components

* `arms`, `t-shirt`, `torso2`, `pants`, `shoes`
* `mask`, `bag`, `accessory`, `vest`, `decals`
* `face`, `hair`

### 🎩 Accessories

* `hat`, `glass`, `ear`, `watch`, `bracelet`, `chain`

### 🧬 Component Format

```lua
['component'] = {
    item = number,       -- Model ID
    texture = number,    -- Texture variation
    palette = number     -- Color palette (optional)
}
```

***

## Useful Tips

* Use `/saveoutfit` or external tools to extract a full outfit structure from your character.
* You can place multiple bags in the world, each with its own outfits and job restrictions.
* If `jobs` is undefined or empty and `public = false`, the bag won't be usable by anyone unless specifically allowed.
