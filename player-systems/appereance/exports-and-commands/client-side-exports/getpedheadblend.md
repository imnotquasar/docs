# getPedHeadBlend

The `getPedHeadBlend` export allows you to retrieve detailed information about a ped’s genetic face and skin blending data. This includes the heritage-based head structure used by the freemode characters, which combines parental facial features and skin tones. It's essential for accurately storing or replicating character appearance in custom servers.

***

## How to Use

To retrieve the head blend data of a ped, use the following code:

```lua
local ped = PlayerPedId()
local blendData = exports['qs-appearance']:getPedHeadBlend(ped)

print("Father Shape ID:", blendData.shapeFirst)
print("Mother Shape ID:", blendData.shapeSecond)
print("Shape Mix:", blendData.shapeMix)
print("Skin Mix:", blendData.skinMix)
```

This export returns a table with the following fields:

* `shapeFirst`, `shapeSecond`, `shapeThird`: Parental shape IDs
* `skinFirst`, `skinSecond`, `skinThird`: Parental skin tone IDs
* `shapeMix`, `skinMix`, `thirdMix`: Blend percentages (0.0 to 1.0)
* `shape`: A string like `"21_0"` combining the first and second shape IDs
* `skin`: A string like `"4_1"` combining the first and second skin tone IDs

This data is crucial for reproducing the exact facial structure and skin tone of any freemode ped using the GTA V character creator system.
