# GetData

The **GetData** export allows you to retrieve the internal `PBData` table. This is useful for accessing the current state of the system (such as configuration, counters, players, etc.) without directly interacting with local variables inside the resource.

***

## How to Use

To get the data, use the following code:

```lua
local data = exports['qs-deathmatch']:GetData()
```

This will return a **Lua table** containing the current `PBData` information. You can use this data to implement custom logic, read flags, query statistics, or display information in the NUI.

> Note: **GetData** provides a **reference** to `PBData`. If you only need to read the data, avoid modifying it. If you need to make changes, use the appropriate events or callbacks provided by the resource to maintain state integrity.
