# GetGangLabel

The GetGangLabel export allows you to retrieve the label (display name) of the player's gang. This can be used to display the gang's name in UI elements, notifications, or custom scripts.

***

## How to Use

To get the gang label, use the following code:

```lua
local gangLabel = exports['qs-gangs']:GetGangLabel()
if gangLabel then
    print("The player's gang label is: " .. gangLabel)
else
    print("The player is not in a gang.")
end
```

This export returns a string representing the label of the player's gang (e.g., "Ballas"). If the player is not part of a gang, it will return `nil`. Use this to dynamically adjust gang-related features or visuals in your scripts.
