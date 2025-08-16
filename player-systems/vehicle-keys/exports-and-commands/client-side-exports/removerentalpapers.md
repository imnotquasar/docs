# RemoveRentalPapers

The `RemoveRentalPapers` export enables removing rental papers from the player's inventory for a specified vehicle. This is ideal for scenarios where a rental period ends or the vehicle is returned.

***

## **How to Use**

To remove rental papers from the player's inventory, use the following code:

```lua
local plate = "ABC123" -- The plate of the rented vehicle
local model = "Sultan" -- The model of the rented vehicle

exports["qs-vehiclekeys"]:RemoveRentalPapers(plate, model)
print("Rental papers removed for vehicle: " .. plate .. " (" .. model .. ")")
```

This export requires two parameters:

* `plate`: The license plate of the vehicle.
* `model`: The model of the vehicle.

***

## **Example Usage**

This example demonstrates how to remove rental papers when the rental period ends:

```lua
function ReturnVehicle(veh)
    local plate = GetVehicleNumberPlateText(veh) -- Get the plate of the vehicle
    local model = GetDisplayNameFromVehicleModel(GetEntityModel(veh)) -- Get the model of the vehicle
    
    -- Remove rental papers for the vehicle
    exports["qs-vehiclekeys"]:RemoveRentalPapers(plate, model)
    
    print("Rental papers removed for: " .. plate .. " (" .. model .. ")")
end

-- Example of using the function
local rentedVehicle = GetVehiclePedIsIn(PlayerPedId(), false) -- Example vehicle
if rentedVehicle then
    ReturnVehicle(rentedVehicle)
else
    print("No rented vehicle to return.")
end
```

This export integrates seamlessly into vehicle return workflows, ensuring rental papers are properly managed and removed when a rental concludes.
