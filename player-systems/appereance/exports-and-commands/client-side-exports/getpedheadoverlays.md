# getPedHeadOverlays

The `getPedHeadOverlays` export allows you to retrieve all head overlay data applied to a ped, such as blemishes, beards, makeup, lipstick, and more. These overlays are part of GTA V’s freemode character customization and define additional facial details.

***

## How to Use

To get the head overlays of a ped, use the following code:

```lua
local ped = PlayerPedId()
local overlays = exports['qs-appearance']:getPedHeadOverlays(ped)

for name, data in pairs(overlays) do
    print("Overlay:", name)
    print("Style:", data.style)
    print("Opacity:", data.opacity)
    print("Color:", data.color)
    print("Second Color:", data.secondColor)
end
```

This export returns a table where:

* Each **key** is a named overlay (e.g., `beard`, `makeup`, `blush`) from `constants.HEAD_OVERLAYS`
* Each **value** is a table containing:
  * `style`: The index of the selected overlay style
  * `opacity`: The blend opacity of the overlay (0.0–1.0)
  * `color`: The primary color ID
  * `secondColor`: The secondary color ID (used by some overlays)

If an overlay is not applied (`value == 255`), the function normalizes it by setting `style` and `opacity` to `0`. This makes it safe and consistent to save, apply, or replicate overlays across characters.
