# RemoveKeysAuto

The `RemoveKeysAuto` export allows you to automatically remove the keys for the vehicle the player is currently inside. This is particularly useful in scenarios where key access needs to be revoked after certain events or interactions.

***

## How to Use

To remove keys for the vehicle the player is currently in, use the following code:

```lua
exports['qs-vehiclekeys']:RemoveKeysAuto()
print("Keys have been removed for the vehicle you are in.")
```

This export automatically detects the vehicle the player is seated in and removes the keys without requiring additional parameters. Use this export to efficiently manage key removal in real-time gameplay situations.
