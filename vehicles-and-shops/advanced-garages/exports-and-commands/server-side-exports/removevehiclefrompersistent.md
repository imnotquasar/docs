# removeVehicleFromPersistent

The `removeVehicleFromPersistent` export is used to remove the persistence of one or more vehicles. This is particularly helpful when vehicles need to be removed from the map after specific native events or when they no longer need to be tracked by the garage system.

***

## How to Use <a href="#how-to-use" id="how-to-use"></a>

To remove persistence, use the following code:

```lua
-- Example: Removing persistence for a single vehicle
exports['qs-advancedgarages']:removeVehicleFromPersistent("ABC123")

-- Example: Removing persistence for multiple vehicles
exports['qs-advancedgarages']:removeVehicleFromPersistent("ABC123", "XYZ789", "LMN456")

print("Vehicles removed from persistence.")
```

This export requires one or more license plate strings as arguments. Once called, the specified vehicles will no longer be managed by the persistence system and can be removed from the map without returning automatically. This is useful for administrative purposes or specific gameplay scenarios.
