# getHouseList

The `getHouseList` export allows you to retrieve the full list of houses defined in the configuration file (`Config.Houses`). This is particularly useful if you need to access or manipulate the house data programmatically within your scripts.

***

## How to Use

To get the complete list of houses, you can use the following code:

```lua
local houseList = exports['qs-housing']:getHouseList()
for houseId, houseData in pairs(houseList) do
    print("House ID: " .. houseId)
    print("House Details: " .. json.encode(houseData, { indent = true }))
end
```

This export will return a table containing all the houses configured in your asset. Each house entry will include details such as its ID, location, and any other custom configurations defined in `Config.Houses`. You can use this data for tasks like listing available houses, debugging, or creating custom features.
