# setPedProps

The `setPedProps` export allows you to apply a full set of accessories (props) to a ped at once. This includes items such as hats, glasses, earrings, and watches. It uses the internal `setPedProp` function to handle each accessory safely and consistently.

***

## How to Use

To apply multiple props to a ped, use the following code:

```lua
local ped = PlayerPedId()
local props = {
    { prop_id = 0, drawable = 5, texture = 1 },  -- Hat
    { prop_id = 1, drawable = 3, texture = 0 },  -- Glasses
    { prop_id = 2, drawable = -1 }              -- Remove earrings
}

exports['qs-appearance']:setPedProps(ped, props)
```

This export takes:

* `ped`: The ped entity to modify
* `props`: A table of prop definitions, where each entry includes:
  * `prop_id`: Accessory slot ID (e.g., `0` for hats)
  * `drawable`: Variation index (`-1` or `6363` removes the prop)
  * `texture`: Texture variation (optional if removing)

It loops through each entry and applies or removes the prop as needed, making it ideal for restoring full accessory sets during character load or outfit switching.
