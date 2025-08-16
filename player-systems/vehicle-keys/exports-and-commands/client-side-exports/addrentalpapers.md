# AddRentalPapers

The `AddRentalPapers` export enables adding rental papers to the player's inventory for a specific vehicle. This is useful for implementing rental systems or verifying vehicle ownership during rentals.

***

## **How to Use**

To add rental papers to the player's inventory, use the following code:

```lua
local plate = "ABC123" -- The plate of the rented vehicle
local model = "Sultan" -- The model of the rented vehicle

exports["qs-vehiclekeys"]:AddRentalPapers(plate, model)
print("Rental papers added for vehicle: " .. plate .. " (" .. model .. ")")
```

This export requires two parameters:

* `plate`: The license plate of the vehicle.
* `model`: The model of the vehicle.

***

### **Example Usage**

This example demonstrates how to add rental papers dynamically when renting a vehicle:

```lua
function RentVehicle(veh)
    local plate = GetVehicleNumberPlateText(veh) -- Get the plate of the vehicle
    local model = GetDisplayNameFromVehicleModel(GetEntityModel(veh)) -- Get the model of the vehicle
    
    -- Add rental papers for the vehicle
    exports["qs-vehiclekeys"]:AddRentalPapers(plate, model)
    
    print("Rental papers issued for: " .. plate .. " (" .. model .. ")")
end

-- Example of using the function
local rentedVehicle = GetVehiclePedIsIn(PlayerPedId(), false) -- Example vehicle
if rentedVehicle then
    RentVehicle(rentedVehicle)
else
    print("No vehicle to rent.")
end
```

This export integrates seamlessly into rental systems, enabling efficient tracking and management of rented vehicles.
