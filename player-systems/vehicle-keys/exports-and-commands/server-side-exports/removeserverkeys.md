# RemoveServerKeys

The `RemoveServerKeys` export is used to remove a player's access to a specific vehicle's keys from the server side. This export is helpful when you need to revoke key ownership, for example, after vehicle repossession or in administrative actions.

***

## **How to Use**

To remove keys from a player for a specific vehicle, use the following parameters:

* **source**: The player's server ID whose keys you want to remove.
* **plate**: The license plate of the vehicle.
* **model**: The vehicle model.

Here’s an example of how to use this export:

```lua
local playerSource = 1 -- Replace with the player's server ID
local vehiclePlate = "XYZ123"
local vehicleModel = "Adder"

exports['qs-vehiclekeys']:RemoveServerKeys(playerSource, vehiclePlate, vehicleModel)
print("Keys removed from player " .. playerSource .. " for vehicle plate: " .. vehiclePlate)
```

***

## **Example Usage**

This example demonstrates removing a player's vehicle keys after a vehicle has been impounded:

```lua
RegisterNetEvent('impoundVehicle', function(playerId, vehicleData)
    local plate = vehicleData.plate
    local model = vehicleData.model

    -- Remove the player's keys for the impounded vehicle
    exports['qs-vehiclekeys']:RemoveServerKeys(playerId, plate, model)

    print("Keys revoked for player ID: " .. playerId .. " for vehicle plate: " .. plate)
end)
```

In this example, the export ensures that the player no longer has access to the impounded vehicle by removing their keys server-side.
