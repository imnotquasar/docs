# GiveKeysAuto

The `GiveKeysAuto` export provides an automatic way to give the player keys for the vehicle they are currently inside. This is ideal for scenarios where the player is interacting with a vehicle directly, such as after purchasing or entering it.

***

## How to Use

To grant keys for the vehicle the player is currently inside, use the following code:

```lua
exports['qs-vehiclekeys']:GiveKeysAuto()
print("Keys have been granted for the vehicle you are in.")
```

This export does not require specifying the vehicle's plate or model, as it automatically detects the vehicle the player is seated in. Use this export to streamline key assignment in your scripts for intuitive and efficient vehicle interactions.
