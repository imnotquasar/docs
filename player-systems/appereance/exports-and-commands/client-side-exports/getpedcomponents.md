# getPedComponents

The `getPedComponents` export allows you to retrieve a complete list of clothing components applied to a given ped. This includes data such as drawable variations and textures for each component slot (e.g., torso, pants, arms, gloves). It's ideal for saving appearances or debugging character customization.

***

## How to Use

To get the clothing components of a ped, use the following code:

```lua
local ped = PlayerPedId()
local components = exports['qs-appearance']:getPedComponents(ped)

for i, comp in pairs(components) do
    print("Component ID:", comp.component_id)
    print("Drawable:", comp.drawable)
    print("Texture:", comp.texture)
end
```

This will return a table indexed by component slot, where each entry contains:

* `component_id`: The slot ID
* `drawable`: The drawable index (or combined index for gloves)
* `texture`: The texture variation

Special cases like arms (`component_id == 3`) and gloves (`component_id == 99`) are handled separately for accuracy.
