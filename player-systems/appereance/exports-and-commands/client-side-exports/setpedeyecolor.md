# setPedEyeColor

The `setPedEyeColor` export allows you to set the eye color of a ped by specifying a valid eye color ID. It’s typically used in character customization systems to apply cosmetic changes to freemode characters.

***

## How to Use

To set the eye color of a ped, use the following code:

```lua
local ped = PlayerPedId()
exports['qs-appearance']:setPedEyeColor(ped, 3) -- 3 = light blue (example)
```

This export takes:

* `ped`: The ped entity to modify
* `eyeColor`: A number representing the eye color index

The valid range for `eyeColor` depends on the game (typically `0–31`). It uses `SetPedEyeColor` internally and is a simple but essential part of complete character appearance customization.
