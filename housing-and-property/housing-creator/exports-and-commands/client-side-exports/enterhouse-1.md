# GetHouseData

The **GetHouseData** export lets you fetch the configuration data of a house when you already know its identifier.

***

## How to Use

```lua
local houseId = exports['qs-housing']:GetClosestHouse()

if houseId then
    local houseData = exports['qs-housing']:getHouseData(houseId)
    if houseData then
        print("House locked: " .. tostring(houseData.locked))
    end
else
    print("No house nearby.")
end
```

This returns the configuration table of the specified house, or `nil` if no data is available.

