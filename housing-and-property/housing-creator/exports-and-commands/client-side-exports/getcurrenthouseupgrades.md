# GetCurrentHouseUpgrades

The `GetCurrentHouseUpgrades` export allows you to retrieve the list of upgrades for the house you are currently inside. This is useful for accessing and managing the specific upgrades applied to a house.

***

## How to Use

To get the list of upgrades for the current house, you can use the following code:

```lua
local upgrades = exports['qs-housing']:GetCurrentHouseUpgrades()

if upgrades and next(upgrades) then
    print("Upgrades for the current house:")
    for upgrade, details in pairs(upgrades) do
        print(upgrade, json.encode(details, { indent = true }))
    end
else
    print("No upgrades found for the current house or you are not inside a house.")
end
```

This export will return a table containing the upgrades for the current house. If no upgrades exist or you are not inside a house, it will return an empty table. You can use this data to display, modify, or manage house upgrades programmatically.
