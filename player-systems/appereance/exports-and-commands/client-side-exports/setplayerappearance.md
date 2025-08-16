# setPlayerAppearance

The `setPlayerAppearance` export allows you to completely apply a saved player appearance, including model, facial features, clothing, hair, props, overlays, tattoos, and more. It combines both model loading and full appearance restoration in a single call.

***

## How to Use

To fully load a saved appearance on a player, use the following code:

```lua
local savedAppearance = {
    model = "mp_m_freemode_01",
    headBlend = { shapeFirst = 21, shapeSecond = 0, shapeThird = 0, skinFirst = 4, skinSecond = 1, skinThird = 0, shapeMix = 0.5, skinMix = 0.5, thirdMix = 0 },
    faceFeatures = { nose_width = 0.1, jawline = -0.2, cheekbone_height = 0.3 },
    headOverlays = { beard = { style = 2, opacity = 0.7, color = 1, secondColor = 1 } },
    components = { { component_id = 11, drawable = 15, texture = 2 } },
    props = { { prop_id = 0, drawable = 5, texture = 1 } },
    hair = { style = 5, texture = 1, color = 2, highlight = 3 },
    tattoos = {}, -- if any
    eyeColor = 3
}

exports['qs-appearance']:setPlayerAppearance(savedAppearance)
```

This export takes:

* `appearance`: A table structured exactly like the output of `getPedAppearance`, containing all relevant appearance data.

Internally, this function:

1. Sets the ped model using `setPlayerModel`
2. Applies the rest of the appearance (blend, features, overlays, clothing, etc.) using `setPedAppearance`

This export is essential for restoring full character appearances, especially after character selection, respawn, or loading from a database.
