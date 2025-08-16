# GetCurrentVanPlate

The `GetCurrentVanPlate` export from `qs-motorhome` allows you to retrieve the license plate of the currently assigned motorhome. This is useful for tracking or validating the motorhome associated with a player.

***

## **How to Use**

To get the current van's license plate, use the following code:

```lua
local vanPlate = exports['qs-motorhome']:GetCurrentVanPlate()
if vanPlate then
    print("The current van's plate is: " .. vanPlate)
else
    print("No van is currently assigned.")
end
```

This export returns the `CurrentVanPlate` as a string (e.g., "ABC123"). Use it to verify ownership, trigger specific actions, or link van-related features in your scripts. If no van is assigned, it will return nil.
