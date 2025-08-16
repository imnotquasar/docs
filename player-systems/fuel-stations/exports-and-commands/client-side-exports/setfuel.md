# SetFuel

The SetFuel export allows you to set the fuel level of a specific vehicle programmatically. This is useful for customizing fuel levels during gameplay scenarios such as refueling, debugging, or initializing vehicles with specific fuel values.

***

## **How to Use**

To set the fuel level of a vehicle, use the following code:

```lua
-- Set the fuel level for a specific vehicle
exports['qs-fuelstations']:SetFuel(vehicle, fuelLevel)
```

***

## Example:

```lua
local vehicle = GetVehiclePedIsIn(PlayerPedId(), false) -- Get the current vehicle
local fuelLevel = 50 -- Set the fuel level to 50%
exports['qs-fuelstations']:SetFuel(vehicle, fuelLevel)
print("Fuel level set to: " .. fuelLevel)
```

This export takes two parameters:

* `vehicle`: The entity ID of the vehicle whose fuel level is to be set.
* `fuelLevel`: The desired fuel percentage (e.g., 50 for 50%).

This function ensures that fuel levels can be adjusted seamlessly, enhancing gameplay customization and debugging options.
