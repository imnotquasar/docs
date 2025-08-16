# RepairSpecificVehicle

The RepairSpecificVehicle export allows you to repair a specific vehicle by specifying its plate. This is useful for targeted vehicle repairs, ensuring that only the intended vehicle is fixed.

***

## How to Use

To repair a specific vehicle, use the following code:

```lua
local plate = "ABC123" -- Replace with the actual plate of the vehicle you want to repair
exports['qs-advancedgarages']:RepairSpecificVehicle(plate)
print("Vehicle with plate " .. plate .. " has been repaired.")
```

This export takes the plate of the vehicle as an argument. Use it in your scripts to repair vehicles based on their unique plate identifiers, ensuring accurate maintenance and gameplay logic.
