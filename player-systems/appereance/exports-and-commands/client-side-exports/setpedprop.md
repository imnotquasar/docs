# setPedProp

The `setPedProp` export allows you to apply or remove an individual accessory (prop) to a ped, such as hats, glasses, or watches. It intelligently clears props when an invalid drawable index is provided, ensuring clean application.

***

## How to Use

To apply a prop to a ped, use the following code:

```lua
local ped = PlayerPedId()
local prop = {
    prop_id = 0,       -- Hat slot
    drawable = 5,      -- Hat model index
    texture = 0        -- Texture variation
}

exports['qs-appearance']:setPedProp(ped, prop)
```

To remove a prop, pass a `drawable` value of `-1` or `6363`:

```lua
local prop = {
    prop_id = 1,       -- Glasses slot
    drawable = -1      -- Will trigger prop removal
}

exports['qs-appearance']:setPedProp(ped, prop)
```

This export takes:

* `ped`: The ped entity to modify
* `prop`: A table including:
  * `prop_id`: The accessory slot ID
  * `drawable`: The prop variation index (`-1` or `6363` clears the slot)
  * `texture`: The texture variation (optional if clearing)

It uses `SetPedPropIndex` to apply the prop or `ClearPedProp` when removal is needed, making it useful for both equipping and unequipping individual accessories dynamically.
