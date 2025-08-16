# updatePersistentVehicleProps

The `updatePersistentVehicleProps` export allows you to dynamically update the stored properties of a persisted vehicle in your garage system. This is especially useful when applying changes such as model, modifications, or metadata without needing to respawn the vehicle or edit the database manually.

***

## How to Use

To update a persisted vehicle’s properties, use the following syntax:

```lua
local success = exports['qs-advancedgarages']:updatePersistentVehicleProps('PLATE', {
    model = 't20',
})
```

This will search for the vehicle with plate `"PLATE"` and update its stored model to `"t20"`.

***

### Example Usage

Here is an example of how you might implement this functionality with a command:

```lua
RegisterCommand('changemodel', function(source)
    local playerPed = GetPlayerPed(source)
    local vehicle = GetVehiclePedIsIn(playerPed, false)

    if not DoesEntityExist(vehicle) then
        print("Player is not in a vehicle.")
        return
    end

    local plate = GetVehicleNumberPlateText(vehicle)
    local success = exports['qs-advancedgarages']:updatePersistentVehicleProps(plate, {
        model = 't20',
    })

    if success then
        print("Vehicle model updated successfully in database.")
    else
        print("Failed to update vehicle model.")
    end
end, false)
```

### Explanation

* `plate` (string): The current plate of the vehicle to be updated.
* `props` (table): A table of properties to be updated (e.g., `model`, `engineHealth`, `mods`, etc.).
