# GenPlate

The GenPlate export from qs-vehicleshop allows you to generate a random vehicle license plate programmatically. This is useful for ensuring unique and consistent plates when adding vehicles to your server.

***

## **How to Use**

To generate a new plate, use the following code:

```lua
local plate = exports['qs-vehicleshop']:GenPlate()
print("Generated Plate: " .. plate)
```

The export returns a string containing the generated plate (e.g., `TZU58C`). Use this string to assign plates to vehicles or manage vehicle-related logic seamlessly in your scripts.
