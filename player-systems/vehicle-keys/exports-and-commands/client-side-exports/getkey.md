# GetKey

The `GetKey` export allows you to check if a player has access to the keys of a specified vehicle. This is useful for verifying ownership or permissions before allowing certain vehicle-related actions.

***

## How to Use

To check if the player has keys for a specific vehicle, use the following code:

```lua
local hasKey = exports['qs-vehiclekeys']:GetKey(plate)
if hasKey then
    print("The player has keys for the vehicle with plate: " .. plate)
else
    print("The player does not have keys for the vehicle with plate: " .. plate)
end
```

This example retrieves the key status for the given plate and determines if the player has the required access. Use this export to enhance vehicle security and player permissions in your scripts seamlessly.
