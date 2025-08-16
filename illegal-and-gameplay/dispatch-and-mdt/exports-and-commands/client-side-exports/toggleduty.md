# ToggleDuty

The job duty system allows you to manage whether a player has access to the dispatch and MDT systems. This is particularly useful for controlling access based on duty status, ensuring only active personnel can use these features.

***

## How to Use

To toggle a player's duty status, use the following export:

```lua
-- Enable or disable dispatch and MDT access
exports['qs-dispatch']:ToggleDuty(true)  -- Set duty on
exports['qs-dispatch']:ToggleDuty(false) -- Set duty off
```

To check a player's current duty status, use:

```lua
-- Returns true if the player is on duty, false if off duty
local isOnDuty = exports['qs-dispatch']:GetIsOnDuty()

if isOnDuty then
    print("Player is on duty.")
else
    print("Player is off duty.")
end
```

These exports help manage permissions dynamically, ensuring that dispatch and MDT functionalities are only available to those on active duty.
