# setPedFaceFeatures

The `setPedFaceFeatures` export allows you to apply detailed morph targets to a freemode ped's face. These values control features like nose width, jawline, cheekbone shape, and other customizable facial characteristics.

***

## How to Use

To apply a set of face features to a ped, use the following code:

```lua
local ped = PlayerPedId()
local features = {
    nose_width = 0.2,
    jawline = -0.4,
    cheekbone_height = 0.1,
    -- Add the rest based on constants.FACE_FEATURES
}

exports['qs-appearance']:setPedFaceFeatures(ped, features)
```

This export takes:

* `ped`: The ped entity to modify
* `faceFeatures`: A table where each key corresponds to an entry in `constants.FACE_FEATURES` and each value is a float between `-1.0` and `1.0`

The function loops through all predefined facial features and applies them with `SetPedFaceFeature`, converting each to a float for proper interpolation. It is ideal for restoring saved faces or generating new randomized ones.
