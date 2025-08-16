# getGangs

The `getGangs` export allows you to retrieve a list of all gang IDs currently available in the system. This is particularly useful for syncing gang data with external systems or custom scripts.

***

## How to Use

To fetch and process the list of gangs, use the following example:

```lua
function SyncGangSystem()
    local gangs = exports['qs-gangs']:getGangs()
    local data = {}
    for name in pairs(gangs) do
        table.insert(data, name)
    end
    initCustomGangs(data)
end
```

This export provides all gang IDs, which you can use to initialize custom systems, synchronize data, or apply custom logic in your scripts. The flexibility of this function allows you to adapt it to various use cases involving gang management.
