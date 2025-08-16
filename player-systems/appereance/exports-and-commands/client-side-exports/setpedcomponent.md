# setPedComponent

The `setPedComponent` export allows you to apply a single clothing component to a ped, such as a shirt, pants, or jacket. It includes automatic handling for special cases like torso adjustments based on jackets, and skips invalid combinations for freemode peds.

***

## How to Use

To apply a clothing component to a ped, use the following code:

```lua
local ped = PlayerPedId()
local component = {
    component_id = 11, -- Jacket
    drawable = 15,
    texture = 2
}

exports['qs-appearance']:setPedComponent(ped, component)
```

This export takes:

* `ped`: The ped entity to modify
* `component`: A table with:
  * `component_id`: The slot ID (e.g., `11` for jacket)
  * `drawable`: The model variation index
  * `texture`: The texture index

**Behavior:**

* Skips application of component `0` (face) and `2` (hair) for freemode peds, as they are typically handled elsewhere.
* If the component is a jacket (`component_id == 11`), it attempts to adjust the **arms (component 3)** using internal torso-hand mapping (`GetUpperBodyData()`), ensuring visual compatibility.
* Applies the variation using `SetPedComponentVariation`. If the component ID is `99` (used internally for gloves), it remaps to component `3` (arms).

This function is ideal for granular updates to specific clothing slots while maintaining compatibility with freemode models.
