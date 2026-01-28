# CreateDispatchCall

This document explains how to create police / emergency dispatch calls from client-side scripts (Lua) using the `qs-police-creator` resource in FiveM.

### What you can do from the client side

* Create a dispatch call with minimal data
* Add a screenshot of the current game view
* Include detailed player/location/vehicle information using `GetPlayerInfo()`
* Put rich player data (street names, vehicle plate, speed, etc.) directly into the **description / message** field

### Main client-side functions

| Export / Function                                           | Description                                                                        | Returns                  |
| ----------------------------------------------------------- | ---------------------------------------------------------------------------------- | ------------------------ |
| `exports['qs-police-creator']:GetScreenshotUrl()`           | Captures current screen and returns temporary image URL                            | `string` or `nil`        |
| `exports['qs-police-creator']:CreateDispatchCall(callData)` | Sends the dispatch to the specified jobs                                           | `result` (boolean/table) |
| `exports['qs-dispatch']:GetPlayerInfo()`                    | Returns detailed info about the local player (ped, coords, streets, vehicle, etc.) | `table` or `nil`         |

### Full callData structure

```lua
local callData = {
    title       = string,               -- required
    description = string,               -- required – can include data from GetPlayerInfo()
    location    = {                     -- required
        coords = { x = number, y = number, z = number }
    },
    jobNames    = { "police", "sheriff" },   -- required
    priority    = number,               -- optional (1 = high, 2 = medium, 3 = low)
    image       = string,               -- optional – screenshot URL
    caller      = {                     -- optional – basic reporter info
        playerId = number,
        name     = string,
        phone    = string,
    },
    blip        = {                     -- optional but recommended
        sprite = number,
        color  = number,
        scale  = number,
        label  = string
    }
}
```

### GetPlayerInfo() – Returned fields

```lua
{
    ped             = ped handle,
    coords          = vector3,
    street_1        = string,           -- main street
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

### 1. Minimal Dispatch (no screenshot, no extra info)

```lua
local callData = {
    title       = 'Suspicious Activity',
    description = 'Unknown person loitering',
    location    = { coords = { x = 123.4, y = 567.8, z = 21.0 } },
    jobNames    = { 'police' },
    priority    = 2,
    blip        = { sprite = 280, color = 1, scale = 1.0, label = 'Suspicious' },
}

exports['qs-police-creator']:CreateDispatchCall(callData)
```

### 2. Dispatch with Screenshot

```lua
local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl()

local callData = {
    title       = 'Robbery in Progress',
    description = 'Armed suspects inside store',
    location    = { coords = { x = 123.4, y = 567.8, z = 21.0 } },
    jobNames    = { 'police', 'sheriff' },
    image       = screenshotUrl,
    priority    = 1,
    blip        = { sprite = 280, color = 49, scale = 1.0, label = 'Robbery' },
}

exports['qs-police-creator']:CreateDispatchCall(callData)
```

### 3. Dispatch with basic caller info

```lua
local callData = {
    title       = 'Shots Fired',
    description = 'Gunshots heard near alley',
    location    = { coords = { x = 123.4, y = 567.8, z = 21.0 } },
    jobNames    = { 'police' },
    caller      = {
        playerId = GetPlayerServerId(PlayerId()),
        name     = GetPlayerName(PlayerId()) or 'Unknown',
        phone    = '555-UNKNOWN',
    },
    priority    = 1,
    blip        = { sprite = 280, color = 1, scale = 1.0, label = 'Shots Fired' },
}

exports['qs-police-creator']:CreateDispatchCall(callData)
```

### 4. Dispatch using GetPlayerInfo() in description

```lua
local playerInfo = exports['qs-dispatch']:GetPlayerInfo() or {}

local street = playerInfo.street_1 or 'Unknown'
if playerInfo.street_2 and playerInfo.street_2 ~= '' then
    street = street .. ' / ' .. playerInfo.street_2
end

local description = ('Gunshots reported at %s.'):format(street)

if playerInfo.vehicle_label then
    description = description .. (' Suspect possibly in %s [%s] going %d km/h.'):format(
        playerInfo.vehicle_label,
        playerInfo.vehicle_plate or '???',
        playerInfo.speed or 0
    )
end

local callData = {
    title       = 'Shots Fired',
    description = description,
    location    = { coords = playerInfo.coords and { x = playerInfo.coords.x, y = playerInfo.coords.y, z = playerInfo.coords.z } or { x = 123.4, y = 567.8, z = 21.0 } },
    jobNames    = { 'police' },
    caller      = {
        playerId = GetPlayerServerId(PlayerId()),
        name     = GetPlayerName(PlayerId()) or 'Unknown',
        phone    = '555-UNKNOWN',
    },
    priority    = 1,
    blip        = { sprite = 280, color = 1, scale = 1.0, label = 'Shots Fired' },
}

exports['qs-police-creator']:CreateDispatchCall(callData)
```

### 5. Full example – Screenshot + GetPlayerInfo() in message

```lua
local playerInfo = exports['qs-dispatch']:GetPlayerInfo() or {}

local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl()

local street = playerInfo.street_1 or 'Unknown location'
if playerInfo.street_2 and playerInfo.street_2 ~= '' then
    street = street .. ' / ' .. playerInfo.street_2
end

local desc = ('Two-vehicle collision reported at %s.'):format(street)

if playerInfo.vehicle_label then
    desc = desc .. (' Involved vehicle: %s [%s] - %d km/h'):format(
        playerInfo.vehicle_label,
        playerInfo.vehicle_plate or '???',
        playerInfo.speed or 0
    )
end

if playerInfo.sex then
    desc = desc .. (' Reporter: ' .. playerInfo.sex)
end

local callData = {
    title       = 'Traffic Accident',
    description = desc,
    location    = { coords = playerInfo.coords and { x = playerInfo.coords.x, y = playerInfo.coords.y, z = playerInfo.coords.z } or { x = 123.4, y = 567.8, z = 21.0 } },
    jobNames    = { 'police', 'ems' },
    caller      = {
        playerId = GetPlayerServerId(PlayerId()),
        name     = GetPlayerName(PlayerId()) or 'Unknown',
        phone    = '555-UNKNOWN',
    },
    image       = screenshotUrl,
    priority    = 1,
    blip        = { sprite = 280, color = 3, scale = 1.2, label = 'Accident' },
}

exports['qs-police-creator']:CreateDispatchCall(callData)
```

### 6. Using current player position when GetPlayerInfo fails

```lua
local playerInfo = exports['qs-dispatch']:GetPlayerInfo()

local coords = playerInfo and playerInfo.coords or GetEntityCoords(PlayerPedId())

local callData = {
    title       = 'Emergency Assistance',
    description = 'Player requesting help - check location',
    location    = { coords = { x = coords.x, y = coords.y, z = coords.z } },
    jobNames    = { 'police', 'ambulance' },
    priority    = 1,
    blip        = { sprite = 280, color = 1, scale = 1.2, label = 'Emergency' },
}

exports['qs-police-creator']:CreateDispatchCall(callData)
```

### Quick tips

* Use `playerInfo.coords` instead of `GetEntityCoords()` when available
* Put street names, vehicle plate, speed, etc. directly in `description` – police see it immediately
* `caller` is usually kept simple (id, name, phone)
* Always handle the case where `GetPlayerInfo()` returns `nil`
* Add screenshot whenever possible – visual evidence helps a lot
