# enterHouse

The `enterHouse` export allows you to programmatically force the local player to enter a specific house. This can be used in scripts to trigger entry into properties either as a regular access or as a visitor.

***

## How to Use

To make the player enter a specific house, use the following code:

```lua
exports['qs-housing']:enterHouse('house-1', true)
```

* **`houseId`** (_string_): The unique identifier of the house you want the player to enter. This must match an existing house defined in your `Config.Houses`.
* **`isVisit`** (_boolean_): Set to `true` if the entry should be treated as a **visit** (guest mode), or `false` for a **normal entry** (owner or authorized access).

