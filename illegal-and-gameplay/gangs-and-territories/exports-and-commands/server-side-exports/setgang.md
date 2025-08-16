# setGang

The `setGang` export allows you to assign or remove a gang from a player by their ID. This is useful for dynamically managing gang membership within your server's systems.

***

## How to Use

To assign a gang to a player:

```lua
function AddGangSystemMember(id, gangID)
    local foundGang
    for _, v in ipairs(Gangs) do
        if v.id == gangID then
            foundGang = v
            break
        end
    end
    if not foundGang then return end
    local success, errorMessage = exports['qs-gangs']:setGang(id, foundGang.gangName)
    if not success then
        print('^1[^3ERROR^1] Failed to add gang to player: ' .. errorMessage)
    end
end
```

To remove a gang from a player:

```lua
function RemoveGangSystemMember(id)
    local success, errorMessage = exports['qs-gangs']:setGang(id, 'none')
    if not success then
        print('^1[^3ERROR^1] Failed to remove gang from player: ' .. errorMessage)
    end
end
```

This export returns `success` and `errorMessage` to confirm whether the operation was successful or if there were issues, making it easy to debug or log actions when managing gang memberships.
