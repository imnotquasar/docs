# GetGang

The GetGang export allows you to retrieve the gang information of a player. This is particularly useful for implementing custom gang-related logic or features within your scripts.

***

## How to Use

To get a player's gang information, use the following code:

```lua
local gang = exports['qs-gangs']:GetGang()
if gang and gang.name ~= 'none' then
    print("The player belongs to a gang: " .. gang.name)
else
    print("The player is not in any gang.")
end
```

This export returns a table containing the gang's `name` and `grade`. You can use this data to check the player's gang affiliation or grade level and apply specific gameplay mechanics or restrictions accordingly.
