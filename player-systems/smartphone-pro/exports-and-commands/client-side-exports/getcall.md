# getCall

The `getCall` export lets you retrieve information about the current call. It can be used to show call details in custom HUDs or logs.

***

## How to Use

```lua
-- Example: Get current call data
-- Returns the current call object (contains type, target info, etc.)

local callData = exports['qs-smartphone-pro']:getCall()

if callData and callData.InCall then
    print('[DEBUG] You are in a call with:', callData.TargetData.name)
else
    print('[DEBUG] No active call.')
end
```

This returns a table with current call data, including call type, target contact, and call time. Use it to track or manipulate call states.
