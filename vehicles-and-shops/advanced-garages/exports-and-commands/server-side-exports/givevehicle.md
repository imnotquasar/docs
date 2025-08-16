# GiveVehicle

The `GiveVehicle` export is used to **manually spawn and assign a vehicle to a player**, either with a **custom license plate** or a **randomly generated one**. This export is typically used in administrative tools, staff menus, or scripted rewards that provide vehicles to players directly.

***

## How to Use

To give a vehicle to a player, use the following code:

```lua
lexports['qs-advancedgarages']:GiveVehicle(source, {'playerId', 'vehicleModel', 'plate'}, 'vehicle')
```

* To use a **random plate**, just omit the plate:

```lua
exports['qs-advancedgarages']:GiveVehicle(source, {'playerId', 'vehicleModel'}, 'vehicle')
```

***

#### Parameters

* `'playerId'`: The target player's server ID.
* `'vehicleModel'`: The spawn name of the vehicle (e.g., `"sultan"`).
* `'plate'` _(optional)_: Custom license plate (can include multiple parts).
* `'vehicle'`: Type of entity — must be `"vehicle"`, `"plane"` or `"boat"`.

***

This export is ideal for **admin tools, vehicle rewards, or staff menus**.
