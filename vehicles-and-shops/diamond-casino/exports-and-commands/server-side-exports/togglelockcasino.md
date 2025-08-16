# ToggleLockCasino

The `ToggleLockCasino` export enables or disables the lock state of all casino doors based on the provided boolean value. When called, the function iterates through all the doors defined in `Config.CasinoDoors`, updating their locked status. It then notifies all clients about the change by triggering the `casino:toggleLock` event, and logs the action for debugging purposes.

***

## How to Use

To use it, pass a boolean value (`true` to lock, `false` to unlock) as shown in the example below:

```lua
local lockStatus = true -- Replace with false to unlock the casino doors
exports['qs-diamondcasino']:ToggleLockCasino(lockStatus)
print("Casino doors have been " .. (lockStatus and "locked" or "unlocked") .. ".")
```

This export is ideal for scenarios where you need to quickly secure or open access to the casino environment, ensuring that all associated doors are updated simultaneously.
