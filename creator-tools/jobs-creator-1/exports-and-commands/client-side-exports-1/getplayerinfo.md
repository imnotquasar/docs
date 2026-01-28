---
description: >-
  This document explains how to retrieve detailed player, vehicle, and location
  information from the server side using GetPlayerInfo(source) provided by
  qs-police-creator in FiveM.
---

# GetPlayerInfo

### What GetPlayerInfo(source) does

`GetPlayerInfo(source)` is a **server-side helper function** that gathers contextual information about a connected player using their **server ID (`source`)**.

It is mainly used to:

* Enrich server-generated police / EMS alerts
* Build detailed dispatch descriptions
* Retrieve street and vehicle data without client logic
* Centralize player context in server logic (commands, events, detections)

***

### How to call GetPlayerInfo(source)

```lua
local playerInfo = GetPlayerInfo(source)
```

⚠️ **Important**

* This function **can return `nil`**
* Always implement fallback logic
* `source` must be a valid connected player

Recommended usage:

```lua
local playerInfo = GetPlayerInfo(source) or {}
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

| Field      | Description                     |
| ---------- | ------------------------------- |
| `coords`   | Player coordinates              |
| `street_1` | Main street name                |
| `street_2` | Secondary street / intersection |

***

#### Vehicle (only if player is in a vehicle)

| Field             | Description          |
| ----------------- | -------------------- |
| `vehicle`         | Vehicle entity       |
| `vehicle_label`   | Vehicle display name |
| `vehicle_colour`  | Vehicle color        |
| `vehicle_plate`   | Vehicle plate        |
| `speed`           | Speed in km/h        |
| `doorCount`       | Door count           |
| `networkEntityId` | Network entity ID    |

***

### Example 1 – Basic safe usage

```lua
local info = GetPlayerInfo(source)

if not info then
    print('GetPlayerInfo failed for source:', source)
    return
end

print('Player coords:', info.coords)
```

***

### Example 2 – Reading street names correctly

```lua
local info = GetPlayerInfo(source) or {}

local street = info.street_1 or 'Unknown location'

if info.street_2 and info.street_2 ~= '' then
    street = street .. ' / ' .. info.street_2
end
```

***

### Example 3 – Detecting vehicle state

```lua
local info = GetPlayerInfo(source) or {}

if info.vehicle then
    print('Vehicle:', info.vehicle_label)
    print('Plate:', info.vehicle_plate)
    print('Speed:', info.speed, 'km/h')
else
    print('Player is on foot')
end
```

***

### Example 4 – Building a compact server-side summary

```lua
local info = GetPlayerInfo(source) or {}

local summary = 'Caller on foot'

if info.vehicle_label then
    summary = ('In %s [%s] at %d km/h'):format(
        info.vehicle_label,
        info.vehicle_plate or '???',
        info.speed or 0
    )
end
```

***

### Example 5 – Defensive pattern (recommended)

```lua
local info = GetPlayerInfo(source)

local coords = info and info.coords
    or GetEntityCoords(GetPlayerPed(source))

local street = info and info.street_1 or 'Unknown'

local vehicleText = ''
if info and info.vehicle_label then
    vehicleText = (' Vehicle: %s [%s] (%d km/h)'):format(
        info.vehicle_label,
        info.vehicle_plate or '???',
        info.speed or 0
    )
end

local description = ('Incident at %s.%s'):format(street, vehicleText)
```

***

### Common pitfalls

* ❌ Assuming `GetPlayerInfo()` always returns data
* ❌ Accessing vehicle fields without checking `info.vehicle`
* ❌ Trusting coords without validating player existence
* ❌ Forgetting intersections (`street_2`)

***

### Quick tips

* Always validate `source`
* Treat `GetPlayerInfo(source)` as **optional context**
* Prefer this function over manual native chains
* Combine `street_1` + `street_2` for accuracy
* Ideal for server-side dispatch, logs, and detections
