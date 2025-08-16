# setPedComponents

The `setPedComponents` export allows you to apply a full set of clothing components to a ped in a single operation. It loops through all provided components and applies them individually using the internal logic of `setPedComponent`.

***

## How to Use

To apply a full outfit to a ped, use the following code:

```lua
local ped = PlayerPedId()
local components = {
    { component_id = 11, drawable = 15, texture = 2 }, -- Jacket
    { component_id = 4, drawable = 6, texture = 1 },   -- Pants
    { component_id = 6, drawable = 2, texture = 0 }    -- Shoes
}

exports['qs-appearance']:setPedComponents(ped, components)
```

This export takes:

* `ped`: The ped entity to modify
* `components`: A table of component tables, where each entry includes:
  * `component_id`: Slot ID (e.g., torso, pants)
  * `drawable`: Variation index
  * `texture`: Texture index

Each component is passed through the `setPedComponent` function, ensuring proper handling of special cases (like torso adjustments) and freemode model validation. This export is ideal for applying full outfits or restoring saved appearances efficiently.
