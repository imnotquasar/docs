# setPedHeadBlend

The `setPedHeadBlend` export allows you to apply facial and skin blend data to a freemode ped. This function is essential for replicating custom character genetics, such as parent-based facial structure and skin tone blending.

***

## How to Use

To apply a head blend to a ped, use the following code:

```lua
local ped = PlayerPedId()
local blendData = {
    shapeFirst = 21,
    shapeSecond = 0,
    shapeThird = 0,
    skinFirst = 4,
    skinSecond = 1,
    skinThird = 0,
    shapeMix = 0.6,
    skinMix = 0.4,
    thirdMix = 0.0
}

exports['qs-appearance']:setPedHeadBlend(ped, blendData)
```

This export takes two arguments:

* `ped`: The ped entity to apply the blend to
* `headBlend`: A table containing the shape and skin parent IDs and mix ratios

The function only executes if the ped model is a freemode ped (`mp_m_freemode_01` or `mp_f_freemode_01`), ensuring compatibility. It applies the blend using `SetPedHeadBlendData`, allowing precise control over character genetics and appearance.
