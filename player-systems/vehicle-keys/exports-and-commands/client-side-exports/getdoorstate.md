# GetDoorState

The `GetDoorState` export retrieves the current door state of a specified vehicle, providing essential information for vehicle-related interactions or logic. The export returns an integer that corresponds to various door states.

***

## **Door State Values**

The door state values and their meanings are as follows:

* **0**: None
* **1**: Unlocked
* **2**: Locked
* **3**: LockedForPlayer
* **4**: StickPlayerInside
* **7**: CanBeBrokenInto
* **8**: CanBeBrokenIntoPersist
* **10**: CannotBeTriedToEnter
* **Other values**: Unknown Status

***

## **How to Use**

To retrieve the door state of a vehicle, use the following code:

```lua
local vehicle = GetVehiclePedIsIn(PlayerPedId(), false) -- Get the current vehicle the player is in
if vehicle and vehicle ~= 0 then
    local doorState = exports["qs-vehiclekeys"]:GetDoorState(vehicle)
    print("Door State: " .. doorState)
else
    print("No vehicle found.")
end
```

This export takes the vehicle entity as a parameter and returns its door state.

***

## **Example Usage**

This example checks the door state of the nearest vehicle and performs logic based on the state:

```lua
function CheckVehicleDoorState(veh)
    local doorState = exports["qs-vehiclekeys"]:GetDoorState(veh)

    if doorState == 1 then
        print("The vehicle is unlocked.")
    elseif doorState == 2 then
        print("The vehicle is locked.")
    elseif doorState == 7 then
        print("The vehicle can be broken into.")
    else
        print("Vehicle door state: " .. doorState)
    end
end

-- Example of using the function
local playerVehicle = GetVehiclePedIsIn(PlayerPedId(), false)
if playerVehicle and playerVehicle ~= 0 then
    CheckVehicleDoorState(playerVehicle)
else
    print("Player is not in a vehicle.")
end
```

This export is highly useful for managing vehicle interactions, security, and gameplay logic tied to door states.
