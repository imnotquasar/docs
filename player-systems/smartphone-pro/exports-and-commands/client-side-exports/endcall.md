# endCall

The `endCall` export allows you to end an active call manually. This is useful for scripted interruptions, admin tools, or timeout features.

***

## How to Use

```lua
-- Example: End the current call manually
-- No parameters required

exports['qs-smartphone-pro']:endCall()
print('[DEBUG] Call ended manually.')
```

No parameters are needed. It immediately stops the current call and resets all related states.
