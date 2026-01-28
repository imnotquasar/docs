# GetPlayerInfo

This document explains how to retrieve **detailed real-time player, location, and vehicle information** from client-side scripts (Lua) using the `GetPlayerInfo()` export provided by **qs-police-creator** in FiveM.

***

### What GetPlayerInfo() does

`GetPlayerInfo()` is a **client-side utility function** that collects contextual data about the current player and returns it in a single structured table.

It is commonly used to:

* Enrich police / EMS dispatch calls
* Build detailed incident descriptions
* Provide vehicle and location context to officers
* Reduce repetitive native calls on the client

***

### How to call GetPlayerInfo()

```lua
local playerInfo = exports['qs-police-creator']:GetPlayerInfo()
```

⚠️ **Important**

* This function may return `nil`
* Always handle fallback logic

Recommended pattern:

```lua
local playerInfo = exports['qs-police-creator']:GetPlayerInfo() or {}
```

***

### Returned data structure

```lua
{
    ped             = ped handle,
    coords          = vector3,
    street_1        = string,           -- main street name
    street_2        = string,           -- crossing / intersection
    sex             = string,           -- "male" / "female"
    vehicle         = entity or nil,
    vehicle_label   = string or 'VehLabel Unknown',
    vehicle_colour  = string or 'VehColor Unknown',
    vehicle_plate   = string or 'VehPlate Unknown',
    speed           = number,           -- km/h
    doorCount       = number,
    networkEntityId = number or 0
}
```

***

### Field breakdown

#### Player

| Field | Description       |
| ----- | ----------------- |
| `ped` | Player ped handle |
| `sex` | Player gender     |

***

#### Location

| Field      | Description                 |
| ---------- | --------------------------- |
| `coords`   | Player coordinates          |
| `street_1` | Main street                 |
| `street_2` | Cross street / intersection |

***

#### Vehicle (only if player is in a vehicle)

| Field             | Description          |
| ----------------- | -------------------- |
| `vehicle`         | Vehicle entity       |
| `vehicle_label`   | Vehicle display name |
| `vehicle_colour`  | Vehicle color        |
| `vehicle_plate`   | Plate text           |
| `speed`           | Speed in km/h        |
| `doorCount`       | Door count           |
| `networkEntityId` | Network ID           |

***

### Example 1 – Safe basic usage

```lua
local info = exports['qs-police-creator']:GetPlayerInfo()

local coords = info and info.coords or GetEntityCoords(PlayerPedId())
```

***

### Example 2 – Building a readable street string

```lua
local info = exports['qs-police-creator']:GetPlayerInfo() or {}

local street = info.street_1 or 'Unknown location'

if info.street_2 and info.street_2 ~= '' then
    street = street .. ' / ' .. info.street_2
end
```

***

### Example 3 – Checking vehicle status

```lua
local info = exports['qs-police-creator']:GetPlayerInfo() or {}

if info.vehicle then
    print('Vehicle:', info.vehicle_label)
    print('Plate:', info.vehicle_plate)
    print('Speed:', info.speed, 'km/h')
else
    print('Player on foot')
end
```

***

### Example 4 – Using GetPlayerInfo() inside a dispatch description

```lua
local info = exports['qs-police-creator']:GetPlayerInfo() or {}

local description = 'Incident reported.'

if info.street_1 then
    description = description .. (' Location: %s.'):format(info.street_1)
end

if info.vehicle_label then
    description = description .. (' Suspect in %s [%s] at %d km/h.'):format(
        info.vehicle_label,
        info.vehicle_plate or '???',
        info.speed or 0
    )
end
```

***

### Example 5 – Full defensive pattern (recommended)

```lua
local info = exports['qs-police-creator']:GetPlayerInfo()

local coords = info and info.coords or GetEntityCoords(PlayerPedId())
local street = info and info.street_1 or 'Unknown'

local vehicleText = ''
if info and info.vehicle_label then
    vehicleText = (' Vehicle: %s [%s] (%d km/h)'):format(
        info.vehicle_label,
        info.vehicle_plate or '???',
        info.speed or 0
    )
end

local finalMessage = ('Call at %s.%s'):format(street, vehicleText)
```

***

### Quick tips

* Always assume `GetPlayerInfo()` **can fail**
* Never trust vehicle data without checking `info.vehicle`
* Prefer `playerInfo.coords` over `GetEntityCoords()`
* Combine street fields manually for intersections
* Ideal for dispatches, reports, and evidence systems

