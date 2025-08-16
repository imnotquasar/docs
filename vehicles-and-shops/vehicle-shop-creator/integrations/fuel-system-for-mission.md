# Fuel System for Mission

The fuel system for missions ensures that vehicles used during missions consume fuel faster. This encourages players to use specific transport vehicles, such as the flatbed, for towing or transporting. The configuration supports integration with popular fuel systems like qs-fuelstations or LegacyFuel, and includes fallback mechanisms for custom setups.

***

## How to Use

To activate this feature, enable the fuel system in the configuration and set the time for the fuel to empty. The script will handle fuel levels using supported fuel systems or your custom fuel logic.

```lua
Config.MissionFuel = true -- Mission vehicles lose fuel quickly to enforce transport vehicle usage
Config.TimeToEmpty = .40  -- Time (in minutes) to empty the fuel. 0.4 = 40 seconds, 1 = 1 minute

Config.SetVehicleFuel = function(vehicle, fuelLevel)
    if GetResourceState('qs-fuelstations') == 'started' then
        exports['qs-fuelstations']:SetFuel(vehicle, fuelLevel)
    elseif GetResourceState('LegacyFuel') == 'started' then
        exports["LegacyFuel"]:SetFuel(vehicle, fuelLevel)
    else
        ErrorPrint("Fuel System not found, please add qs-fuelstations or LegacyFuel to your resources or configure custom functions")
        SetVehicleFuelLevel(vehicle, fuelLevel)
    end
end

Config.GetVehicleFuel = function(vehicle)
    local fuelLevel = 100

    if GetResourceState('qs-fuelstations') == 'started' then
        fuelLevel = exports['qs-fuelstations']:GetFuel(vehicle)
    elseif GetResourceState('LegacyFuel') == 'started' then
        fuelLevel = exports["LegacyFuel"]:GetFuel(vehicle)
    else
        fuelLevel = GetVehicleFuelLevel(vehicle)
    end

    return fuelLevel
end
```
