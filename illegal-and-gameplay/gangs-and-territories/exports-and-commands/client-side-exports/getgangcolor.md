# GetGangColor

The GetGangColor export allows you to retrieve the RGB color values associated with the player's gang. This is useful for customizing visuals, such as UI elements or in-game markers, to match the gang's color scheme.

***

## How to Use

To get the RGB color of the player's gang, use the following code:

```lua
local gangColor = exports['qs-gangs']:GetGangColor()
if gangColor then
    print("The gang color is: R:" .. gangColor.r .. " G:" .. gangColor.g .. " B:" .. gangColor.b)
else
    print("The player is not in a gang.")
end
```

This export returns a table containing the RGB values (`r`, `g`, and `b`) of the gang's color. If the player is not part of a gang, it will return `nil`. Use this information to dynamically style elements related to the player's gang.
