# GiveKeys

The `GiveKeys` export allows you to assign vehicle keys to a player for a specified vehicle. This is particularly useful for third-party assets, such as vehicle shops, to grant ownership access.

***

## **Obtain the Plate Natively**

To use the `GiveKeys` export effectively, you need the vehicle's plate and model. Here is a simple code snippet to obtain these values natively:

```lua
local model = GetDisplayNameFromVehicleModel(GetEntityModel(veh))
local plate = GetVehicleNumberPlateText(veh)
```

With these values, you can seamlessly integrate the export into your script.

***

## **How to Use**

To give keys to a player, use the following code:

```lua
exports['qs-vehiclekeys']:GiveKeys(plate, model, true)
```

* **plate**: The license plate of the vehicle.
* **model**: The model of the vehicle.
* **bypassKeyCheck**: _(optional)_ A boolean value that, if set to `true`, bypasses the key validation check. By default, it is set to `false`.

***

## **Example**

Here is an example of how to use the `GiveKeys` export in a vehicle shop script:

```lua
ESX.TriggerServerCallback('esx_vehicleshop:buyVehicle', function(success)
    if success then
        -- Retrieve the model and plate of the purchased vehicle
        local model = GetDisplayNameFromVehicleModel(GetEntityModel(vehicleData))
        local plate = GetVehicleNumberPlateText(vehicleData)

        -- Give keys to the player
        exports['qs-vehiclekeys']:GiveKeys(plate, model, true)
    else
        ESX.ShowNotification("You don't have enough money to purchase this vehicle.")
    end
end, vehicleData.model, generatedPlate)
```

***

This export simplifies the process of assigning keys to players, making it ideal for use in scenarios like vehicle purchases, rentals, or administrative commands. Integrate it with the plate and model retrieval logic to ensure a smooth experience.
