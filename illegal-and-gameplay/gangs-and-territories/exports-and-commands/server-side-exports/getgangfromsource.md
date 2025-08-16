# GetGangFromSource

The `GetGangFromSource` export allows you to retrieve the gang information of a player based on their source. This is useful for server-side scripts where you need to check or utilize gang-related data for a specific player.

***

## How to Use

To get the gang information of a player by their source, use the following code:

```lua
local gangData = exports['qs-gangs']:GetGangFromSource(playerSource)
if gangData and gangData.name ~= 'none' then
    print("The player is in the gang: " .. gangData.name)
else
    print("The player is not part of any gang.")
end
```

This export returns an object containing the player's gang details, such as the gang name and grade. Use it in scripts where you need to manage or reference gang affiliations based on a specific player's source.
