# GetFuel

The **GetFuel** export allows you to retrieve the current fuel level of a specified vehicle. This is useful for monitoring fuel levels, implementing fuel consumption mechanics, or integrating fuel data into custom scripts.

***

## **How to Use**

To obtain the fuel level of a vehicle, use the following code:

```lua
local fuelLevel = exports['qs-fuelstations']:GetFuel(vehicle)
print("Current fuel level: " .. fuelLevel)
```

***

## Example:

```lua
local vehicle = GetVehiclePedIsIn(PlayerPedId(), false) -- Get the current vehicle
local fuelLevel = exports['qs-fuelstations']:GetFuel(vehicle)
if fuelLevel then
    print("The vehicle's fuel level is: " .. fuelLevel .. "%")
else
    print("Failed to retrieve fuel level.")
end
```

This export takes the following parameter:

* `vehicle`: The entity ID of the vehicle whose fuel level is to be retrieved.

The function returns the fuel level as a percentage (e.g., `50` for 50%). Use this export to integrate fuel data seamlessly into gameplay mechanics or debugging processes.
