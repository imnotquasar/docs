# setPedTattoos

The `setPedTattoos` export allows you to apply a list of tattoos to a ped and store them internally for later use. This is essential for preserving character identity, especially for freemode peds using custom tattoo layers.

***

## How to Use

To apply tattoos to a ped, use the following code:

```lua
local ped = PlayerPedId()
local tattoos = {
    { collection = "mpbusiness_overlays", name = "MP_Buis_Face_01_M" },
    { collection = "mpchristmas2_overlays", name = "MP_Xmas2_M_Tat_005" }
}

exports['qs-appearance']:setPedTattoos(ped, tattoos)
```

This export takes:

* `ped`: The ped entity to apply tattoos to
* `tattoos`: A table of tattoo entries, where each tattoo contains:
  * `collection`: The overlay dictionary name
  * `name`: The specific overlay name

Internally, this function saves the tattoos in `PED_TATTOOS` for reuse (e.g., when switching hair or models) and applies them using the internal `setTattoos` logic. It is designed to maintain visual consistency across customization changes.
