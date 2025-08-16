# GetServerKey

The `GetServerKey` export checks if a specific player (identified by their server ID) has access to the keys for a particular vehicle. This is useful for validating ownership or permissions for server-side logic, such as locking or unlocking a vehicle.

***

## **How to Use**

To check if a player has the key for a specific vehicle, use the following parameters:

* **source**: The server ID of the player whose key access you want to verify.
* **plate**: The license plate of the vehicle.

#### This export returns a boolean value:

* **`true`**: The player has access to the vehicle's keys.
* **`false`**: The player does not have access.

#### Example usage:

```lua
local playerSource = 1 -- Replace with the player's server ID
local vehiclePlate = "XYZ123"

local hasKey = exports['qs-vehiclekeys']:GetServerKey(playerSource, vehiclePlate)
if hasKey then
    print("Player " .. playerSource .. " has keys for vehicle plate: " .. vehiclePlate)
else
    print("Player " .. playerSource .. " does NOT have keys for vehicle plate: " .. vehiclePlate)
end
```

***

## **Example Use Case**

This example demonstrates checking if a player has the keys before allowing them to lock or unlock a vehicle:

```lua
RegisterNetEvent('vehicle:lockUnlock', function(playerId, plate)
    local hasKey = exports['qs-vehiclekeys']:GetServerKey(playerId, plate)

    if hasKey then
        print("Player ID: " .. playerId .. " is authorized to lock/unlock vehicle: " .. plate)
        -- Proceed with locking or unlocking the vehicle
        TriggerClientEvent('vehicle:toggleLock', playerId, plate)
    else
        print("Player ID: " .. playerId .. " is NOT authorized to lock/unlock vehicle: " .. plate)
        -- Notify the player that they do not have the keys
        TriggerClientEvent('QBCore:Notify', playerId, "You don't have the keys to this vehicle!", "error")
    end
end)
```

In this case, the export checks the player's key ownership before performing any vehicle-related actions.
