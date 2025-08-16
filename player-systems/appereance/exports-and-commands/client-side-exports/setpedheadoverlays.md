# setPedHeadOverlays

The `setPedHeadOverlays` export allows you to apply facial detail overlays to a ped, such as beards, makeup, blemishes, and more. These overlays add depth and realism to freemode characters and are commonly used in character customization systems.

***

## How to Use

To apply head overlays to a ped, use the following code:

```lua
local ped = PlayerPedId()
local overlays = {
    beard = { style = 2, opacity = 0.8, color = 1, secondColor = 1 },
    lipstick = { style = 5, opacity = 0.6, color = 2, secondColor = 0 },
    -- Add other overlays as needed
}

exports['qs-appearance']:setPedHeadOverlays(ped, overlays)
```

This export takes:

* `ped`: The ped entity to apply overlays to
* `headOverlays`: A table where keys are overlay names (e.g., `"beard"`, `"makeUp"`) and values include:
  * `style`: Overlay style index
  * `opacity`: Blend amount (0.0–1.0)
  * `color`: Primary color ID (optional)
  * `secondColor`: Secondary color ID (optional)

The function automatically sets the appropriate `colorType` based on the overlay (e.g., `2` for lipstick or makeup). It ensures visual consistency by updating both the style and color layers, making it ideal for restoring or customizing detailed character appearances.
