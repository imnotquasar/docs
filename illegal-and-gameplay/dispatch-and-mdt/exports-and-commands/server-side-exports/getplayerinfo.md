# GetPlayerInfo

The **GetPlayerInfo** export allows you to retrieve detailed information about a specific player by their player ID. This is particularly useful for server-side operations that require dynamic access to player data.

***

## How to Use

To get a player's information, pass their player ID and a callback function to the export:

```lua
exports['qs-dispatch']:GetPlayerInfo(playerID, function(playerData)
    if playerData then
        print("Player coordinates: " .. tostring(playerData.coords))
        print("Nearby street: " .. playerData.street_1)
        print("Player vehicle: " .. (playerData.vehicle_label or "None"))
    else
        print("Failed to retrieve player info.")
    end
end)
```

***

## Return Data

The export returns a structured object containing the following player details:

* **ped**: Player's character identifier.
* **coords**: Current map coordinates of the player.
* **street\_1**: Name of the nearest street.
* **street\_2**: Name of the second nearest street (if applicable).
* **sex**: Player character's gender.
* **vehicle**: Identifier of the vehicle the player is in (if any).
* **vehicle\_label**: Vehicle's label or description.
* **vehicle\_colour**: Color of the player's vehicle.
* **vehicle\_plate**: Vehicle's registration plate.
* **speed**: Current speed of the vehicle in km/h (if applicable).

***

## Example Output

Here’s an example of the returned data structure:

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

Use this export to integrate real-time player data into your scripts efficiently.
