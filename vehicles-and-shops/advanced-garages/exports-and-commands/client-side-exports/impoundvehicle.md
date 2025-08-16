# ImpoundVehicle

The ImpoundVehicle export allows you to send the nearest vehicle to an impound directly from the client side. This is useful for managing abandoned or illegally parked vehicles in a streamlined way.

***

## How to Use

To impound the nearest vehicle, use the following code:

```lua
exports['qs-advancedgarages']:ImpoundVehicle()
print("The nearest vehicle has been impounded.")
```

This export requires no additional parameters. It identifies the closest vehicle to the player and moves it to the impound, ensuring efficient handling of vehicles in the game environment.
