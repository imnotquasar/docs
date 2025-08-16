# isInCall

The `isInCall` export checks whether the player is currently in a call. This is useful for conditionally blocking actions or controlling UI.

***

## How to Use

```lua
-- Example: Check if player is in an active call
-- Returns true or false

local inCall = exports['qs-smartphone-pro']:isInCall()

if inCall then
    print('[DEBUG] You are currently on a call.')
else
    print('[DEBUG] No call in progress.')
end
```

This returns `true` if the player is in a call, `false` otherwise. Useful for preventing multiple simultaneous calls or managing interaction logic.
