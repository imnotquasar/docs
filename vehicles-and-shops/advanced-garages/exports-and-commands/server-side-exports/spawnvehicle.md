# SpawnVehicle

The `SpawnVehicle` export allows you to spawn a vehicle programmatically with persistence while ensuring it matches the server's vehicle data. This is useful for scenarios where vehicles need to be spawned externally but still retain their database-linked attributes.

***

## How to Use

To spawn a vehicle with persistence, use the following code:

```lua
-- Example values for required parameters
local vehicleId = 1                 -- ID from the player_vehicles or owned_vehicles table
local ownerIdentifier = "steam:xyz" -- Player's unique identifier
local vehicleType = "car"           -- Type of vehicle: 'vehicle', 'boat', or 'plane'
local spawnCoords = vector4(215.2, -810.2, 30.7, 90.0) -- Coordinates to spawn the vehicle
local vehicleProps = {color1 = 0, color2 = 1}          -- Custom vehicle properties (mods)
local playerSource = 1              -- Player's server-side source ID
local warpIntoVehicle = true        -- Whether the player should spawn inside the vehicle

-- Spawn the vehicle
exports['qs-advancedgarages']:SpawnVehicle(vehicleId, ownerIdentifier, vehicleType, spawnCoords, vehicleProps, playerSource, warpIntoVehicle)

print("Vehicle spawned with persistence for player " .. ownerIdentifier)
```

### Explanation of Parameters

* **`id`**: Unique ID of the vehicle from the database (e.g., `player_vehicle > column id`).
* **`owner`**: The player's identifier (Steam, Discord, etc.).
* **`vType`**: Type of vehicle, such as `vehicle`, `boat`, or `plane`.
* **`coords`**: Coordinates and heading where the vehicle will spawn.
* **`props`**: Vehicle modifications or properties retrieved from the database.
* **`source`**: Player's server source ID.
* **`warp`**: Boolean to decide if the player spawns directly inside the vehicle.

This export ensures that the spawned vehicle integrates seamlessly with the persistence system and retains all database-defined characteristics.
