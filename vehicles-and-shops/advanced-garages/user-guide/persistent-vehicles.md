# Persistent Vehicles

Quasar Advanced Garages introduces an advanced persistence system that enhances realism by keeping vehicles active in the world until properly impounded. This feature also includes a police impound system for managing abandoned or misplaced vehicles, ensuring they do not remain obstructive on the streets.

***

## **Removing Vehicles from the Map**

Unlike traditional systems, this garage does not support removing vehicles using the standard `/dv` command. Since vehicles are persistent, they will return to the map even after deletion. To address this, two specialized administrative commands are provided:

<table><thead><tr><th width="219">Command</th><th>Description</th></tr></thead><tbody><tr><td>/mdv</td><td>Removes the closest vehicle and sends it to the impound.</td></tr><tr><td>/mdvall</td><td>Sends all currently deployed vehicles to impound.</td></tr></tbody></table>

Both commands ensure proper management of vehicles, redirecting them to impounds instead of merely deleting them, enhancing server realism.

***

## **Police Impound System**

When vehicles are removed using these commands, they are sent directly to a random impound on the map, based on their type. This integration prevents vehicles from cluttering streets or interfering with gameplay.

***

## **Integrating Persistence Into Other Assets**

To ensure vehicles spawned outside the garage (e.g., from a vehicleshop or other vehicle spawn systems) are also persistent, you can use the following export:

```lua
exports['qs-advancedgarages']:setVehicleToPersistent(vehicle)
```

* **Parameter**: `vehicle` – The `netId` of the vehicle to make persistent.
* **Use Case**: Add this export to your vehicleshop or vehicle spawn assets to apply persistence automatically to all newly spawned vehicles.
