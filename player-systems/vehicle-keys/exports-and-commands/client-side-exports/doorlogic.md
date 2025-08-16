# DoorLogic

The `DoorLogic` export provides advanced control over vehicle door locking and unlocking mechanics. This system includes various optional parameters to customize animations, notifications, sounds, and other effects.

***

## How to Use

To apply door logic to a vehicle, use the following code:

```lua
local closestVehicle = GetClosestVehicle() -- Retrieve the nearest vehicle
if closestVehicle ~= 0 then
    exports["qs-vehiclekeys"]:DoorLogic(closestVehicle, false, 1, false, false, false)
    print("Door logic applied successfully.")
else
    print("No vehicle found.")
end
```

### **Example Parameters:**

* `vehicle`: The targeted vehicle entity.
* `skipAnimation`: (Optional, default `false`) Skips the lock/unlock animation if `true`.
* `forcedDoorStatus`: (Optional) Forces the door status (`0` for None, `1` for Unlocked, `2` for Locked).
* `skipNotification`: (Optional, default `false`) Prevents notifications from being displayed.
* `skipSound`: (Optional, default `false`) Prevents the default vehicle door sounds.
* `skipFlickerLights`: (Optional, default `false`) Prevents lights from flickering when toggling the lock state.

***

## **Example Usage**

This example demonstrates applying `DoorLogic` to the closest vehicle:

```lua
function GetClosestVehicle()
    local playerPed = GetPlayerPed(-1)
    local pos = GetEntityCoords(playerPed)
    local vehicles = GetGamePool('CVehicle')
    local closestVehicle = 0
    local minDistance = -1

    for _, vehicle in ipairs(vehicles) do
        local distance = #(pos - GetEntityCoords(vehicle))

        if minDistance == -1 or distance < minDistance then
            minDistance = distance
            closestVehicle = vehicle
        end
    end

    return closestVehicle
end

local closestVehicle = GetClosestVehicle()
if closestVehicle ~= 0 then
    exports["qs-vehiclekeys"]:DoorLogic(closestVehicle, false, 2, true, false, true)
    print("DoorLogic applied: Doors locked, notifications displayed.")
else
    print("No vehicle found.")
end
```

This export allows flexible control over vehicle door states, enabling customized interaction within your scripts.
