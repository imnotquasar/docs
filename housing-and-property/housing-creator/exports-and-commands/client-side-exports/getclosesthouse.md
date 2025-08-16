# GetClosestHouse

The `GetClosestHouse` export allows you to determine whether the player is near a house. This can be useful for triggering house-related interactions or verifying proximity for specific actions.

***

## How to Use

To check if a player is near a house, use the following code:

```lua
local closestHouse = exports['qs-housing']:GetClosestHouse()
if closestHouse then
    print("Closest house identifier: " .. closestHouse)
else
    print("No house nearby.")
end
```

This will return the identifier of the closest house if one is nearby or `nil` if no house is detected. You can use this information to execute house-specific logic or display relevant information to the player.
