# getPedAppearance

The `getPedAppearance` export allows you to retrieve the complete visual configuration of a ped, including model, facial structure, clothing, props, overlays, tattoos, hair, and eye color. It is designed for full appearance saving, cloning, or syncing across sessions or servers.

***

## How to Use

To get the full appearance data of a ped, use the following code:

```lua
local ped = PlayerPedId()
local appearance = exports['qs-appearance']:getPedAppearance(ped)

print("Model:", appearance.model)
print("Eye Color:", appearance.eyeColor)
print("Total components:", #appearance.components)
```

This export returns a comprehensive table including:

* `model`: The ped model string (e.g., `mp_m_freemode_01`)
* `headBlend`: Facial and skin blend data from parents
* `faceFeatures`: Morph values for facial structure
* `headOverlays`: Makeup, beards, blemishes, etc.
* `components`: Clothing items (torso, pants, shoes, etc.)
* `props`: Accessories (glasses, hats, etc.)
* `hair`: Hair style, texture, color, and highlight
* `tattoos`: A list of all active tattoos (client-side retrieved)
* `eyeColor`: Eye color index (normalized and validated)

This export is the most complete representation of a ped’s visual state and is ideal for any save/load appearance system, identity cloning, or advanced character design workflows.
