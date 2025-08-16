# setPedAppearance

The `setPedAppearance` export allows you to apply a full appearance configuration to any ped entity. It handles everything from clothing and props to facial features, head overlays, tattoos, hair, and eye color. This export is ideal for restoring saved character data to an NPC or the player ped.

***

## How to Use

To apply a full appearance to a ped, use the following code:

```lua
local ped = PlayerPedId()
local appearance = exports['qs-appearance']:getPedAppearance(ped)

-- Later, restore the same appearance:
exports['qs-appearance']:setPedAppearance(ped, appearance)
```

This export takes:

* `ped`: The ped entity to apply the appearance to
* `appearance`: A table structured like the result of `getPedAppearance`, containing:
  * `components`: Outfit components (e.g., jacket, pants)
  * `props`: Accessories (e.g., hat, glasses)
  * `headBlend`: Facial and skin blending
  * `faceFeatures`: Facial morphs
  * `headOverlays`: Beards, makeup, blemishes, etc.
  * `hair`: Hair style and color
  * `eyeColor`: Eye color index
  * `tattoos`: Tattoo list (optional)

**Behavior:**

* Applies components and props unconditionally
* Applies other features conditionally (only if they exist)
* Includes logic to verify freemode models before applying `headBlend`

This export is perfect for synchronizing or restoring detailed ped appearances, both for players and AI characters.
