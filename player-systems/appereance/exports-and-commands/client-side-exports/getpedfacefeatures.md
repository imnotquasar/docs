# getPedFaceFeatures

The `getPedFaceFeatures` export allows you to retrieve all facial customization values of a ped, including nose width, jawline, cheekbone height, and more. These are the detailed morph values used in the GTA V character creator to fine-tune a freemode ped's face.

***

## How to Use

To get the facial features of a ped, use the following code:

```lua
local ped = PlayerPedId()
local faceFeatures = exports['qs-appearance']:getPedFaceFeatures(ped)

for feature, value in pairs(faceFeatures) do
    print("Feature:", feature, "Value:", value)
end
```

This export returns a table where:

* The **keys** are face feature names (as defined in `constants.FACE_FEATURES`)
* The **values** are normalized floats (rounded to one decimal) representing each morph target, usually between `-1.0` and `1.0`

This data is essential for saving and restoring highly customized characters, enabling full reconstruction of facial structures across sessions or between servers.
