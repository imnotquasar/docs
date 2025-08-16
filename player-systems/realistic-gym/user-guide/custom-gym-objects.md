# Custom Gym Objects

This feature allows you to place custom gym props (such as treadmills, machines, or decorative equipment) within your fitness area. It is currently **disabled by default** but fully supported in structure.

All objects are defined in:

```lua
Config.GymObjects
```

***

## Example Configuration

```lua
Config.GymObjects = {
    -- Example: Custom Treadmill (currently disabled)
    -- ["treadmill"] = {
    --     enabled = true, -- Toggle object visibility
    --     model = "add_custom_model_treadmill", -- Model name (must be streamed or native)
    --     coords = vector3(-1199.6661, -1563.3497, 3.6195), -- Placement coordinates
    --     heading = 125.4344 -- Object rotation
    -- }
}
```

***

## Object Properties

<table><thead><tr><th width="160.66668701171875">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>enabled</code></td><td>Enables or disables the object. Set to <code>true</code> to make it appear in-game.</td></tr><tr><td><code>model</code></td><td>The object model to spawn (e.g., treadmill, weight machine). Must be a valid GTA object or a custom streamed prop.</td></tr><tr><td><code>coords</code></td><td>The world position where the object will be placed.</td></tr><tr><td><code>heading</code></td><td>The rotation of the object to align it correctly in the gym layout.</td></tr></tbody></table>

***

## Important Notes

* No objects are enabled by default — this section is **optional and customizable**.
* If using custom models, ensure they are properly streamed through your resource pack.
* Use this section to improve immersion or to expand your gym visually with RP machines, lockers, benches, and more.
