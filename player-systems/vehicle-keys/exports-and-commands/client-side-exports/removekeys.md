# RemoveKeys

The `RemoveKeys` export allows you to revoke a player's access to a specified vehicle by removing its keys. This is useful for scenarios such as repossessions, administrative actions, or vehicle ownership changes.

***

## **Obtain the Plate Natively**

To use the `RemoveKeys` export, you need the vehicle's plate and model. Use the following code snippet to retrieve these values:

```lua
local model = GetDisplayNameFromVehicleModel(GetEntityModel(veh))
local plate = GetVehicleNumberPlateText(veh)
```

With these values, you can accurately identify the vehicle for which the keys should be removed.

***

## **How to Use**

To remove keys from a player, use the following code:

```lua
exports['qs-vehiclekeys']:RemoveKeys(plate, model)
```

* **plate**: The license plate of the vehicle.
* **model**: The model of the vehicle.

***

## **Example**

Here’s an example of how to use the `RemoveKeys` export in a script:

```lua
RegisterCommand('removekeys', function(source)
    local vehicle = GetVehiclePedIsIn(GetPlayerPed(source), false)
    if not DoesEntityExist(vehicle) then
        print("No vehicle found.")
        return
    end

    -- Retrieve the model and plate of the vehicle
    local model = GetDisplayNameFromVehicleModel(GetEntityModel(vehicle))
    local plate = GetVehicleNumberPlateText(vehicle)

    -- Remove the keys
    exports['qs-vehiclekeys']:RemoveKeys(plate, model)
    print("Keys removed for vehicle with plate: " .. plate)
end, false)
```

***

This export provides an efficient way to manage vehicle access dynamically. Use it in scenarios such as player penalties, vehicle ownership adjustments, or administrative commands to maintain control over vehicle keys.
