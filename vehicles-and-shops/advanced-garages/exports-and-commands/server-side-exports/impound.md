# impound

The impound export allows you to impound a specific vehicle by providing its license plate. This is particularly useful for server-side scripts or administrative actions that require targeting a particular vehicle.

***

## How to Use

To impound a vehicle by its plate, use the following code:

```lua
local plate = "ABC123" -- Replace with the specific license plate
exports['qs-advancedgarages']:impound(plate)
print("The vehicle with plate " .. plate .. " has been impounded.")
```

This export requires the vehicle's license plate as an argument and will send the targeted vehicle to the impound. Use this feature for precise vehicle management and enforcement.
