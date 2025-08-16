# GetPlayerInfo

The `GetPlayerInfo` export retrieves detailed information about the player. This can be used for various server-side or client-side implementations where player data is needed.

***

## How to Use

To get the player's information, use the following code:

```lua
local playerInfo = exports['qs-dispatch']:GetPlayerInfo()

if playerInfo then
    print("Player coordinates: " .. tostring(playerInfo.coords))
    print("Nearby street: " .. playerInfo.street_1)
    print("Player vehicle: " .. (playerInfo.vehicle_label or "None"))
else
    print("Failed to retrieve player info.")
end
```

***

## Return Data

The export returns an object containing the following details:

* **`ped`**: The player's character identifier.
* **`coords`**: Player's current map coordinates.
* **`street_1`**: Name of the closest street.
* **`street_2`**: Name of the second nearest street (if applicable).
* **`sex`**: Player character's gender.
* **`vehicle`**: Vehicle identifier if the player is inside a vehicle.
* **`vehicle_label`**: The vehicle's label or description.
* **`vehicle_colour`**: The vehicle's color.
* **`vehicle_plate`**: The vehicle's registration plate.
* **`speed`**: Current speed of the vehicle in km/h (if applicable).

***

## Example Output

Use this export to dynamically retrieve and use player-related data in your scripts.

```lua
{
    ped = 123,
    coords = vector3(200.12, -150.34, 50.08),
    street_1 = "Great Ocean Hwy",
    street_2 = "Joshua Rd",
    sex = "Male",
    vehicle = "vehicle_01",
    vehicle_label = "Sultan RS",
    vehicle_colour = "Red",
    vehicle_plate = "AB123CD",
    speed = 120
}

```
