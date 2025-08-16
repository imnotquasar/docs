# updateVehiclePlate

The `updateVehiclePlate` export is designed to change the license plate of a vehicle dynamically. This is particularly useful for integrating with custom assets or systems that allow players to modify vehicle plates.

***

## How to Use

To update a vehicle's license plate, use the following code:

```lua
local currentPlate = "ABC123" -- Current vehicle plate
local newPlate = "NEWPLT"    -- New plate to assign
exports['qs-advancedgarages']:updateVehiclePlate(currentPlate, newPlate)

print("Plate updated from " .. currentPlate .. " to " .. newPlate)
```

### Example

Here is an example of how you might implement this functionality with a command:

```lua
RegisterCommand('changeplate', function(source)
    local playerPed = GetPlayerPed(source)
    local vehicle = GetVehiclePedIsIn(playerPed, false)
    
    if not DoesEntityExist(vehicle) then
        print("Player is not in a vehicle.")
        return
    end
    
    local currentPlate = GetVehicleNumberPlateText(vehicle)
    local newPlate = "PEPERONI" -- Example new plate
    
    exports['qs-advancedgarages']:updateVehiclePlate(currentPlate, newPlate)
    print("Plate successfully updated to " .. newPlate)
end, false)
```

### Explanation

The export requires two parameters:

* **plate**: The current license plate of the vehicle (string).
* **newPlate**: The new license plate to assign to the vehicle (string).

Once executed, the garage system will instantly recognize the new plate, ensuring seamless integration with persistence systems and preventing conflicts with other assets.
