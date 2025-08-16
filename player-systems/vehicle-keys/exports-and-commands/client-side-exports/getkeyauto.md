# GetKeyAuto

The `GetKeyAuto` export allows you to check if the player has keys for the vehicle they are currently inside. This is useful for determining access permissions in real-time gameplay scenarios.

***

## How to Use

To check if the player has keys for the vehicle they are in, use the following code:

```lua
local hasKey = exports['qs-vehiclekeys']:GetKeyAuto()
if hasKey then
    print("Player has keys for the current vehicle.")
else
    print("Player does not have keys for the current vehicle.")
end
```

This export automatically identifies the vehicle the player is seated in and returns a boolean value (`true` or `false`) indicating whether the player has keys for it. Use this export to implement custom logic based on key ownership.
