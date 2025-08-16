# setVehicleToPersistent

The `setVehicleToPersistent` export allows you to assign persistence to a vehicle spawned externally from your server's vehicle shops or other spawning systems. This ensures that the vehicle remains active within the advanced garage system.

***

## How to Use

To set a vehicle as persistent, use the following code:

```lua
-- Example: Assigning persistence to a vehicle
local vehicleNetId = NetworkGetNetworkIdFromEntity(vehicleEntity) -- Get the netId of the vehicle entity

-- Make the vehicle persistent
exports['qs-advancedgarages']:setVehicleToPersistent(vehicleNetId)

print("Vehicle with netId " .. vehicleNetId .. " is now persistent.")
```

This export is particularly useful for integrating third-party vehicle shops or custom spawn systems into the Quasar Advanced Garages persistence framework. It ensures that any externally spawned vehicle behaves as if it were managed directly by the garage system, including saving and tracking its state.
