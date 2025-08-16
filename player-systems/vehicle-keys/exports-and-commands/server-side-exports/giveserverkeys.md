# GiveServerKeys

The `GiveServerKeys` export is used to grant vehicle keys to a player server-side. This export is especially useful when you want to manage keys through server-side scripts, ensuring more secure and controlled key assignment.

***

## **How to Use**

To give keys to a player for a specific vehicle, use the following parameters:

* **source**: The player's server ID who will receive the keys.
* **plate**: The license plate of the vehicle.
* **model**: The vehicle model.
* **bypassKeyCheck**: (Optional, default: `false`) If `true`, bypasses the key validation before granting the keys.

Here is an example of how to use this export:

```lua
local playerSource = 1 -- Replace with the player's server ID
local vehiclePlate = "XYZ123"
local vehicleModel = "Adder"
local bypassCheck = false -- Set to true if you want to skip the key validation

exports['qs-vehiclekeys']:GiveServerKeys(playerSource, vehiclePlate, vehicleModel, bypassCheck)
print("Keys given to player " .. playerSource .. " for vehicle plate: " .. vehiclePlate)
```

***

## **Example Usage**

This example assigns vehicle keys to a player when they purchase a vehicle from a server-side shop:

```lua
RegisterNetEvent('vehiclePurchase', function(playerId, vehicleData)
    local plate = vehicleData.plate
    local model = vehicleData.model
    local bypassKeyCheck = false -- Prevent bypass unless explicitly allowed

    -- Assign keys to the player for the purchased vehicle
    exports['qs-vehiclekeys']:GiveServerKeys(playerId, plate, model, bypassKeyCheck)

    print("Vehicle keys assigned to player ID: " .. playerId)
end)
```

In this case, the export is used to securely grant keys to the player after they buy a vehicle. This ensures proper synchronization and ownership within the server.
