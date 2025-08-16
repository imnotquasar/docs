# External Garage Integration

Want to create garages from external scripts without modifying the core? With `qs-advancedgarages`, you can register your own garages easily and dynamically.

***

## Creating a Garage

To register a new garage, use the `CreateGarage` export. You can call it from any script using `CreateThread`.

```lua
CreateThread(function()
    exports['qs-advancedgarages']:CreateGarage('qs-1', {
        owner = true,      -- true: private garage; false: public garage
        available = false, -- true: available by default if public
        type = 'vehicle',  -- Garage type: 'vehicle', 'boat', or 'plane'
        coords = {
            menuCoords = vector3(832.22, -1264.15, 26.29),         -- Garage menu location
            spawnCoords = vector4(832.22, -1264.15, 26.29, 180.0)  -- Vehicle spawn point
        },
        shell = {
            shell = 1 -- Shell/interior ID (if applicable)
        },
        price = 10000 -- Purchase price if required
    })
end)
```

***

## Opening a Garage Menu

You can open the garage menu using its ID with the following export:

```lua
RegisterCommand('opengarage', function()
    exports['qs-advancedgarages']:OpenGarageMenu('qs-1')
end)
```

{% hint style="success" %}
Tip: You can replace this command with any interaction method (like `ox_target`, `qb-target`, or keybinds).
{% endhint %}

